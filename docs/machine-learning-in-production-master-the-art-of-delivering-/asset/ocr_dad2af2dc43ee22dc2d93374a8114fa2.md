Note: A cedilla is a symbol that is written under the letter 'ç' in French, Portuguese, and some other languages to show that you pronounce it like a letter 's'.

# # Hello World app using Tkinter

Let’s create a basic Tkinter app to give you a glimpse of Tkinter functionality. The following code creates a simple app displaying the Hello World text with the Exit button to close the app.

```
1. from tkinter import *
2. win = Tk()
3.
4. a = Label(win, text = "Hello World")
5. a.pack()
6.
7. b=Button(win, text='Exit', command=tk.destroy)
8. b.pack()
9.
10. win.mainloop()
```

In the preceding code, first, the tkinter package is imported to create the main window for the app using the Tk(), where the win is the name of the main window object that has been created using Tk(). A Label() widget is used to display text or images, and the win parameter is used to denote the parent window of the app.

The pack() organizes the widgets in blocks (such as buttons and labels). If you do not organize the widget, your app will still run, but that widget will be invisible. A Button() widget is used to add buttons, and here it is used to close the Tkinter app. When the user clicks on the Exit button, the Tkinter app window will close. Finally, the mainloop() is to keep the application running and execute user commands.

The following figure shows the output of the preceding code. It is a simple Tkinter app with a label and a button.

![](bbox=[0.375, 0.78, 0.625, 0.905])

Figure 8.2: Hello World app using Tkinter