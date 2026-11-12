: Figure 7-2:
This tiny
window has
a single
button on it.

![](bbox=[0.26, 0.15, 0.38, 0.2])

As you can see, the code for this tiny window is pretty simple. The first line creates a button by calling the button command. The first parameter to the button command (and all widget commands in general, for that matter) is the name of the button.

Remember, you have to name your widgets starting with a dot. From there, you specify whether the widget is contained in another widget. This button isn't, so I just follow the dot with the final part of the name: .mybutton.

Then I specify an option, which in this case is -text. That option is the text that appears on the button. I chose Hello to appear on the button, as you can see in Figure 7-2.

But just because you create a widget doesn't mean Tk automatically plops the widget on the window for you. To add the widget to a window, you need to use the pack command:

```
pack .mybutton
```

The format of the pack command is simple; you simply type pack followed by the name of the widget.

![](bbox=[0.14, 0.64, 0.23, 0.72])

The word pack may seem like a strange choice for a command that adds a widget to a window. However, in reality, pack refers to the way the widgets get positioned in a window. The pack command is a geometry manager that organizes the widgets. Tk offers three different geometry managers called pack, grid, and place. The pack command is a special one that squishes your controls all together as much as possible. You can also include some options in the pack command; these are present in many of the examples in this chapter. If you want to find out more about geometry managers, see Book IV, Chapter 8.

The preceding program is really cool and all, but I must admit it doesn't do much. If you click the button, nothing happens. A good button is one that rolls up his sleeves and actually does something rather than sit around on the couch all day eating potato chips.