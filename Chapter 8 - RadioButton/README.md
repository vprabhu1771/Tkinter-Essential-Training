here is a full example of how to create and use Radiobutton widgets in Tkinter:
```
import tkinter as tk

root = tk.Tk()

# Adjust Size
root.geometry("300x200")

# create a variable to store the selected value
var = tk.StringVar()

# create the radio buttons
rb1 = tk.Radiobutton(root, text="Windows", variable=var, value="Windows")
rb2 = tk.Radiobutton(root, text="Mac Os", variable=var, value="Mac Os")
rb3 = tk.Radiobutton(root, text="Linux", variable=var, value="Linux")

# set the default selection
var.set("Mac Os")

# add the radio buttons to the window
rb1.pack()
rb2.pack()
rb3.pack()

def show_selected():
    # get the selected value and display it
    selected = var.get()
    print(selected)

# create a button to show the selected value
btn = tk.Button(root, text="Show selected", command=show_selected)
btn.pack()

root.mainloop()
```

In this example, we create a StringVar to store the selected value, then create three Radiobutton widgets with different text and values. We set the default selection to "Mac Os", and add the radio buttons and a button to the window using pack().

When the user clicks the button, the show_selected() function is called, which gets the selected value using var.get() and prints it to the console.

You can customize this example by changing the text and values of the radio buttons, and modifying the show_selected() function to do something else with the selected value.
