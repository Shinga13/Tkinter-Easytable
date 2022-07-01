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

