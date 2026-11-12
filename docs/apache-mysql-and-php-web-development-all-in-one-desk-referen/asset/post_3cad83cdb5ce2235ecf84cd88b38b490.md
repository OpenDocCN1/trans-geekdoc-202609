
Think of the event name as having multiple parts separated by hyphens. The event Double-1 has two parts. The first part, Double, in this case refers to the number of clicks. The second part, 1, refers to button 1, which is the left button (or the right if the system is configured for left-handed use).

Want to instead respond to a double-click while the Control key is held down? Then instead of Double-1 use Control-Double-1. That's easy. Or you can require the Shift key using Shift-Double-1. Want both keys? Then it's Control-Shift-Double-1 or Shift-Control-Double-1; either works with the same effect. Want just a single click while holding down Shift and Control? Then just use Control-Shift-1. You can also use Alt for the Alt key in all these combinations. (If you're on a Mac, just test out different combinations of these to see which corresponds to the Apple key, and so on.)

## Creating a Second Window

Tk lets you create additional windows besides the main window. But remember: These additional windows are still owned by the main window. Thus, their names still start with a dot. And further, if you close the main window, the additional windows will close as well, and your program will end.

Try out this example:

```
wm title . "First Window"
button .mybutton -text Hello
pack .mybutton
toplevel .win2 -width 300 -height 300
wm title .win2 "Second Window"
button .win2.button2 -text "Click"
pack .win2.button2
```

The key here is the toplevel command, which creates a new window. In this case, the new window is called .win2, and it has a width and a height of 300. I then give the new window a title using the wm title command. Notice that in the wm title command I provide the name of my window (.win2), and then I put the title in double quotes. Thus, the new window will include the words Second Window in the title bar.

And then you can see how I add a button (or any widget, for that matter) to the new window: I create the button as usual, and I give it a name that starts with the name of my new window. In this case, my button's name is .win2.button2. Because that name starts with .win2, the button will automatically show up on the .win2 window (the second window, that is) when I add the button using the pack command.

## Adding a Menu Bar to a Window

Over the years, I've used lots of GUI systems for lots of different languages, and I have to say that creating a menu bar is usually the most cumbersome task in any system. Tk is no different. The problem is not that menus are inherently complex; the problem is that you typically have lots of menus, and they're arranged hierarchically.

The following example creates a window and adds a menu bar to the window. The menu bar consists of two menus, a File menu and an Edit menu.

```
wm title . "Menu demo"

# Declare the main menu bar
menu .mymenu

# Declare the file menu item
menu .mymenu.filemenu
.mymenu add cascade -label "File" -menu .mymenu.filemenu
.mymenu.filemenu add command -label "Exit" -command { exit }

# Declare the edit menu item
menu .mymenu.editmenu
.mymenu add cascade -label "Edit" -menu .mymenu.editmenu
.mymenu.editmenu add command -label "Stuff" -command \
{ exit }

# Add the menu to the window
. configure -menu .mymenu
```

Look carefully at this code because it contains some gotchas. First, I declare the menu widget, and I call it .mymenu. That's not a problem. But next, I must declare another menu widget for each of the menus on the menu bar.

> However, I don't create a menu widget for each menu item; just the menus themselves. That's confusing and an important point to remember. Also, notice that the widgets for the menus are children of the main menu widget; thus in my example, I named them .mymenu.filemenu and .mymenu.editmenu.

After declaring the .mymenu.filemenu widget, I call the add cascade command for .mymenu, which creates the menu. I provide the text that appears at the top of the menu, in this case File, using the -label option. Then comes another gotcha: I have to specify which widget I'm adding this menu for. Yes, I know, that's not particularly sensible, but it's the way Tk does it. So I include the -menu option with the .mymenu.filemenu widget.

I want to add some menu items that go under this File menu. In this case, I want an Exit menu item underneath the File menu. To do that, I put the menu name and use the add command command. I provide a label for the menu item ("Exit"), and then, just like I did when I created a button, I use a -command option to specify the Tcl commands to run. For this example, I'm just using the exit command, which closes the program.

Then I repeat all this for the Edit menu (and any more menus I may want to add). Yes, it's a lot of work, but that's just because programs tend to have a lot of menus. But it works! And finally, when I've created all the menus I need, I need to attach the whole menu bar to the window. I don't use the pack command for this. Instead, I put the window's name (in this case a dot) followed by the configure command, then -menu, and the name of my main menu.

(What you're really doing is reconfiguring the window's options. The option you want to reconfigure is the menu option; to do this, you add -menu followed by the name of your main menu widget.)

When you run the program, your window will have a menu bar like the one shown in Figure 7-3.

![](img/3f967ab8a8fddc723173059f56621648_331_0.png)

## Attaching a Menu to a Button

Tk includes some interesting widgets that you may or may not have seen before. If you use X Windows or KDE (the Linux or Unix windowing systems), then you've likely seen buttons that you can click that result in a menu opening up. Microsoft Windows doesn't include a control like that, but Tk does. Here's a sample program that does just that:

```
wm title . "Menu button demo"

# Create the menu button, specifying the menu
menubutton .menubtn -text "Click me" \
-menu .menubtn.mymenu -relief raised

# Declare the menu itself; it must be a child of the menu button.
menu .menubtn.mymenus

# Declare the file menu item
menu .menubtn.mymenus.menu1
.menubtn.mymenus add cascade -label "File" \
-menu .menubtn.mymenus.menu1
.menubtn.mymenus.menu1 add command -label "Exit" \
-command { exit }

# Declare the edit menu item
menu .menubtn.mymenus.editmenu
.menubtn.mymenus add cascade -label "Edit" -menu \
.menubtn.mymenus.editmenu
.menubtn.mymenus.editmenu add command -label "Stuff" \
-command { exit }

pack .menubtn
```

If you read the previous section, “Adding a Menu Bar to a Window,” this code may seem a bit familiar. The process of creating a set of menus is the same for both menu buttons and window menu bars. But, when you create a menu button, instead of starting with a menu widget, you start with a menubutton widget. Further, the -relief option is available; this option describes how the button looks — that is, whether the button is a regular raised button, an inset button, or any of several types. Here are the types you can try out; their names are rather self-explanatory. Feel free to try them out to see what they look like:

- raised
- sunken
- flat
- ridge
- solid
- groove

When you run the preceding program, you see a window similar to Figure 7-4.

![](img/3f967ab8a8fddc723173059f56621648_333_0.png)

## Sliding Across the Numbers with a Scale

A slider control is found on most operating systems; Tk includes an interesting-looking slider control that you can use. This slider control doesn’t make use of any native slider controls, but that’s okay; it looks cool. (And isn’t that all that matters anyway?)

Here’s a sample program; you’ll notice the slider control is called a scale widget.

```
set curx 0
set cury 0

proc drawH {x} {
    global curx
    global cury
    .mycanvas create line $curx $cury $x $cury
    set curx $x
}

proc drawV {y} {
    global curx
    global cury
    .mycanvas create line $curx $cury $curx $y
    set cury $y
}

scale .myHscale -orient horizontal -length 284 \
    -from 0 -to 250 \
    -command "drawH" -tickinterval 50
grid .myHscale -row 1 -column 0
scale .myVscale -orient vertical -length 300 \
