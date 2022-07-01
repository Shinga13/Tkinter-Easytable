# Tkinter-Easytable
This python class serves as table display module for the GUI-Interface Tkinter. Tkinter itself does not contain such a module; possibly the closest module functionality-wise is 
the tkk.Treeview module. This on the other side is bulky and user-unfriendly not mentioning that it's purpose is not to display tables but hierachical structures such as
directories. At the same time those issues are the goals this project tries to archieve: An easy to use module that provides a method of displaying tables specifically.

## Features
- horizontally and vertically scrollable, the heading is always visible
- a variety of styling functions capable of styling individual cells, rows, columns

## How-to-use
### Installation
To use this module simply download the Easytable.py file and import it into your own python project. I recommend using one of the following ways:
- paste the Easytable.py file into the same folder as your own .py file. Use <br>`from Easytable import Easytable` or <br>`from Easytable import Easytable as X` <br>as import statement, with X being your preferred name
- paste easytable in a subfolder together with an empty python file named `__init__.py`. Use <br>`from [SUBFOLDERNAME].Easytable import Easytable` as import statement
### First table
Easytable inherits from tkinter.Frame, so it supports all methods of this class, but some of those may not show any effect. To create a table use the constructor with at least 
two parameters: The master frame and secondly a list of headings. The table will have as many columns as there are elements in the heading list. To add content to the table 
use the `add_content` function on the created table. Pass a list to add its elements to the table. Pass multiple lists inside a list to add multiple lines. 
### Styling
Each table cell is represented by a tkinter Label, and those can be styled as well with built-in methods. `style_configure` for example styles the labels itself while 
`border_configure` configures the borders of each cell (See examples below). You can use all style attributes for the table that a standard tkinter Label supports.
### Example

```
from tkinter import Tk, BOTH
from local.Easytable import Easytable

# list containing the headings for the table
headings = ['Name', 'Population', 'Area [sqkm]', 'Continent', 'Language', 'Currency']

# 1-Dimensional list with data for one row
data_1 = ['England', '56,489,800', '130,279', 'Europe', 'English', 'Pound Sterling']

# 2-Dimensional list with data for 5 rows
data_2 = [
    ['germany', '83,190,556', '357,022', 'europe', 'german', 'euro'],
    ['france', '67,413,000', '643,801', 'europe', 'french', 'euro'],
    ['mexico', '126,014,024', '1,972,550', 'north america', 'spanish', 'mexican peso'],
    ['Peru', '34,294,231', '1,285,216', 'south america', 'spanish', 'sol'],
    ['vietnam', '96,208,984', '331,699', 'asia', 'vietnamese', 'dong']
]

# the style options, may also be inserted directly as dictionaries into the function calls
style = {
            'heading':{'font':('Helvetica',17,'normal'), 'fg':'#b3b3b3', 'bg':'#3a3a3a'},
            'content':{'bg':'#424242', 'fg':'#eeeeee', 'font':('Helvetica',14,'bold'), 'anchor':'w', 'padx':5},
            'bordercolor': '#222222',
            'borderwidth':{'top_border':0, 'bottom_border':1, 'left_border':0, 'right_border':1},
            'scroll':{
                'trough':{'troughcolor':'#424242','troughrelief':'flat','borderwidth':0},
                'arrow':{'background':'#888888', 'relief':'flat', 'borderwidth':0, 'arrowcolor':'#3a3a3a'},
                'thumb':{'relief':'flat', 'background':'#888888', 'borderwidth':0}
            }
        }

# function running on every inserted element; optional see (*)
def caps(text):
    return str(text).title()

# creating a basic window
root = Tk()
root.geometry('450x400')
root.title('Easytable Demo')

# constructing the table and filling it into the window
table = Easytable(root, columns=headings, heading_style=style['heading'], default_cell_style=style['content'], scrollbar_style=style['scroll'], border_color=style['bordercolor'])
table.pack(fill=BOTH)

# add a single row
table.add_content(data_1)

# add multiple rows
table.add_content(data_2, caps) # (*) the function caps is called for each inserted string, capitalizing the content of each cell

# configure the borders
table.border_configure('heading content', **style['borderwidth'])
table.border_configure('content column0', right_border=4)

# style examples
table.style_configure('pattern[evencolumns]', {'bg':'#303042'})
table.style_configure('cell[0,3]', {'fg':'#5555dd'})
table.style_configure('content column0', {'anchor':'e'})

# set the table height
table.table_configure(height=6)


root.protocol("WM_DELETE_WINDOW", lambda:quit())
root.mainloop()
```
