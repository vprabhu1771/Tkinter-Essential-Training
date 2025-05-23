here's a full example of how to create and use a menu bar in Tkinter:
```
import tkinter as tk

root = tk.Tk()
root.geometry("300x200")

# create a function to handle menu item selections
def select_file():
    print("File selected")

def select_edit():
    print("Edit selected")

# create a menu bar
menu_bar = tk.Menu(root)

# create a File menu and add items
file_menu = tk.Menu(menu_bar, tearoff=0)
file_menu.add_command(label="New", command=select_file)
file_menu.add_command(label="Open", command=select_file)
file_menu.add_separator()
file_menu.add_command(label="Exit", command=root.quit)

# create an Edit menu and add items
edit_menu = tk.Menu(menu_bar, tearoff=0)
edit_menu.add_command(label="Cut", command=select_edit)
edit_menu.add_command(label="Copy", command=select_edit)
edit_menu.add_command(label="Paste", command=select_edit)

# add the File and Edit menus to the menu bar
menu_bar.add_cascade(label="File", menu=file_menu)
menu_bar.add_cascade(label="Edit", menu=edit_menu)

# set the menu bar for the window
root.config(menu=menu_bar)

root.mainloop()
```

In this example, we create a menu bar using the Menu() method, and then create two menus - File and Edit - using the Menu() method again. We add items to each menu using the add_command() method, and add a separator between items in the File menu using add_separator().

We then add the File and Edit menus to the menu bar using the add_cascade() method, and set the menu bar for the window using the config() method.

When the user selects a menu item, the corresponding function (select_file() or select_edit()) is called, which simply prints a message to the console. You can customize this example by adding additional menus and items, and modifying the functions to perform different actions when a menu item is selected.
