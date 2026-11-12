
To create a new instance of the structure, I type the name of my structure type followed by a name for the instance. Thus, emailinfo_friend creates a new structure called friend of type emailinfo.

Next, I set the members of my new structure called friend. To do so, I type the name of the structure as a command, in this case friend. Then I type the subcommand config. And finally, I type each item name as an option followed by a value, as in -name "Jeff".

To access the members of the structure, I again type my structure name (such as friend) and then use the cget subcommand, followed by the name of the item as an option, as in friend cget -name. Here's the output from this program:

```
Jeff
jeff@me.com
Me, Inc.
Suzy
suzy@me.com
Me, Inc.
```

## Chapter 7: Designing GUIs with Tk

### In This Chapter

- Creating a hierarchy of widget names
- Constructing a simple window
- Adding a button to a window
- Creating a listbox and working with the pack and bind commands
- Creating a second window
- Attaching a menu to a button
- Building a scale slider
- Changing a control's settings

When you install Tcl, you get an additional product called Tk. Tk, which simply stands for Toolkit (how's that for creativity), is a library for creating graphical user interfaces, or GUIs. Originally Tk was built specifically for use with Tcl, but over time, people have written libraries that let you use Tk from nearly any language. Examples of such languages are Python, Perl, and C++.

If you've ever struggled with a complex GUI library such as Microsoft Foundation Classes, Tk will be a welcome addition to your world of programming. It's extremely simple to use. Yes, occasionally some of the code gets a little strange, but nevertheless, Tk is easy.

But Tk has another strong point: It's operating-system-independent! Yes, that's correct. You can develop a program in Tcl/Tk on a Linux computer, and hand the program to somebody with either a Windows PC or a Mac and he or she will be able to run the program. It's true, and you can't say that about many other languages (especially C++). And even better, the windows and controls you create will look "native," meaning the Windows controls will look like Windows controls, and the Mac OS controls will look like Mac OS controls.

In this chapter, I show you how to get up and running with Tk using the Tcl programming language. But first, let me share with you an important lesson I recently learned.

![](img/3f967ab8a8fddc723173059f56621648_321_0.png)

When you save your Tcl/Tk programs to a file, don’t name the file the same as one of the built-in widget commands! For example, don’t name your file `button.tcl` or `canvas.tcl`. If you do, you’ll get some very strange error messages because Tcl will get confused over the names. These errors will be a bit nonsensical, and you could pull your hair out trying to interpret them.

![](img/3f967ab8a8fddc723173059f56621648_321_1.png)

Although a *For Dummies* book is a reference guide and you’re not required to read the thing from cover to cover (especially a huge book like this one), I do ask that you read the following two sections, “A Hierarchy of Widgets and Names” and “Creating a Simple Window,” before proceeding with any other sections or chapters in this book on Tk. In those sections, I provide you with some important information about Tk.

### A Hierarchy of Widgets and Names

When you create a GUI with Tk, everything you create gets built in a hierarchical manner. At the very top of this hierarchy is your main window. Inside the main window, you have controls known in the Tk world as *widgets*. Then inside these various widgets you might have more widgets. And inside some of those widgets you might have even more widgets. (This is starting to sound like a scene from *Alice in Wonderland*.)

In order to keep everything in your wonderland clean and neat, Tk requires that you give a name to your widget that shows the hierarchy. First, remember this rule:

*The main window’s name is simply . (a period or dot).*

That’s hard to spell out in written text without getting lost in a morass of punctuation, but the main window’s name is just a period or dot. Next, every widget owned by the main window has a name that starts with a period, as in these examples:

- .mybutton1
- .greatbiglistbox
- .textentry
- .canvas1

These names reflect not only the name of the widget, but also the name of the widget’s owner — the main window. Why is that necessary? Because some widgets can have other widgets inside of them. For example, one important widget type is called a frame. A frame is simply a holder of other widgets, allowing you to organize your widgets neatly inside a window. You could name a frame that's owned by the main window something like .bigframe. And if another frame is owned by .bigframe, you might call it .bigframe.smallerframe.

Then, inside .bigframe, you may have two buttons and a listbox with the following names, respectively:

- .bigframe.button1
- .bigframe.button2
- .bigframe.listbox1

Notice how each of these names starts with a dot (representing the main window) and is followed by the name of the frame, then a dot, and finally the control's own unique name. But don't be fooled: The name of the first button is not simply button1. The name of the first button is the whole shebang, .bigframe.button1. Never try to abbreviate the name; you need the whole name to make sense.

![](img/3f967ab8a8fddc723173059f56621648_322_0.png)

Sometimes people like to store their widget names in variables, and you can too, if you like. I don't do so in any of the examples in this book so that the names are clearly visible. But suppose you store your .bigframe widget's name in a variable called f, like so:

```
set f .bigframe
```

Then, thanks to the magic of substitution, you're free to refer to the .bigframe.button1 widget like so:

```
$f.button1
```

Because $f gets replaced with .bigframe, the interpreter changes $f.button1 into .bigframe.button1, which is the button's full name.

What if you have more than one window? That doesn't change anything about the names: Your main window is still the head honcho, the owner of all the other widgets including the additional windows. In the section, "Creating a Second Window," later in this chapter, I show you how to make additional windows. There you'll see that you still need to name your additional windows as if they're owned by the main window (because they are!) starting with a dot, as in .secondwindow or .auxiliaryinformation, for example. If you have a button on the second window, then that button may be called, for example, .secondwindow.coolclicker.

## Creating a Simple Window

When you run a Tcl program, you run it under the auspices of the tclsh program, which passes the Tcl commands on to the Tcl interpreter. When you run a Tcl program that contains Tk commands, you don't use tclsh. Instead, you use a program called wish, which stands for *windowing shell*. (The designers of Tcl/Tk are so filled with verbal creativity that I can't stand it.)

This means that if you're using the pound-bang thingy at the beginning of a script in Linux or Unix, you'll want to reference the wish program, not the tclsh program. In other words, I recommend adding the following line at the very beginning of your Tcl/Tk programs if you want them to run as executables:

```
#!/usr/local/bin/wish
```

(This is assuming, of course, that wish is found in the directory called /usr/local/bin. If you installed it elsewhere, adjust the path accordingly, please.)

Or, you can run your programs like so:

```
wish myprogram.tcl
```

![](img/3f967ab8a8fddc723173059f56621648_323_0.png)

In Windows, you can set up a file association so that .tcl programs open with wish.exe. Then you can just run the file like so:

```
myprogram.tcl
```

And wish will launch, running your script.

When you run wish, you automatically get an initial main window. Isn't that great? I'll say it again: You automatically get a main window, which means you don't have to create a main window! Life is good, sometimes.

Instead of creating a main window, all you have to do is provide some information about the main window. Therefore, here's about the simplest Tk program you can imagine:

```
wm title . "Hello"
```

This just sets the title of the main window. Try storing this in a file called basicwindow.tcl and run it directly as follows:

```
wish basicwindow.tcl
```
