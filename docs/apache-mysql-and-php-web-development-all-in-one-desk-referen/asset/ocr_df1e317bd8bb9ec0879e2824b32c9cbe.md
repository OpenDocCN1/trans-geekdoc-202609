delete command takes two indexes, which represent the start and end of
a range that I want to delete. In this case, I'm deleting the items that have
index 1, 2, and 3. (The first item in the listbox gets index 0.)

But you might notice something bizarre: If you read the program from top to
bottom, you'll see that I used .lb as a command before the code where I
created the .lb control. But that's okay, because the place where I use .lb
as a command (in a button command) runs after I create the .lb control;
the .lb control gets created when the program first starts, and the button
command runs only when the user of the program clicks the button.

After the buttons, I make the listbox. Notice the pack command that follows
this listbox command and compare it to the previous pack command, the
one that followed the frame statement. The one for the frame statement
includes the option -side top. The one for the listbox statement includes
the option -side bottom. The pack command positions controls relative to
a side of the window. Thus, the first pack command will position the frame at
the top of the window, and the second pack command will position the list-
box at the bottom. (But positioning items in windows is a bit more complex
than it seems, so be sure to read Book IV, Chapter 8, where it is explained
more fully.)

The final part of the program is probably the most interesting. If you want to
write code that responds to mouse clicks and such, you use the bind com-
mand. Although some widgets have mouse capabilities built right in (like
the button, which has its -command option), other widgets require that you
bind a function to the widget. The listbox is an example of the latter type of
widget.

Although the concept may seem strange, in practice this is quite easy: You
just choose the widget and which type of event you want to respond to; in
this case, I want it to respond to a double-click of the left mouse button. Tk
has a name for each type of event, and the name for a double-click of the left
button is Double-1. (Yes, that's the numeral 1.) You can see, then, the
format of the command; it's much like a proc command, and it starts with
the word bind. Then comes the name of the widget you're binding to (in
this case, the listbox) and the event name inside angled brackets. And
finally, you have a set of curly braces containing the commands to run.

For a really detailed explanation of the different events available, take a look
at www.scriptics.com/man/tcl8.4/TkCmd/bind.htm. Or, for the short
version, read on.