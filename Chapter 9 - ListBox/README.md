here's a full example of how to create and use a Listbox widget in Tkinter:
```
import tkinter as tk

root = tk.Tk()

# Adjust Size
root.geometry("300x200")

# create a list of items
items = ["Samsung", "Apple", "Cooler Master", "Asus", "HP"]

# create a Listbox widget and add the items
listbox = tk.Listbox(root)
for item in items:
    listbox.insert(tk.END, item)

# add a scrollbar to the listbox
scrollbar = tk.Scrollbar(root)
scrollbar.pack(side=tk.RIGHT, fill=tk.Y)
listbox.config(yscrollcommand=scrollbar.set)
scrollbar.config(command=listbox.yview)

# create a button to show the selected item
def show_selected():
    selection = listbox.curselection()
    if selection:
        index = selection[0]
        item = listbox.get(index)
        print(item)

btn = tk.Button(root, text="Show selected", command=show_selected)
btn.pack()

# add the listbox to the window
listbox.pack()

root.mainloop()
```

In this example, we create a Listbox widget and add five items to it using a for loop and the insert() method. We also create a Scrollbar widget and configure it to work with the Listbox using the yscrollcommand and config() methods.

We then create a show_selected() function that gets the selected item from the Listbox when the user clicks the button. We use the curselection() method to get the index of the selected item, then use the get() method to retrieve the item text. Finally, we print the selected item to the console.

You can customize this example by changing the items in the Listbox, modifying the show_selected() function to do something else with the selected item, or adding additional functionality to the Listbox such as selecting multiple items or deleting items.
