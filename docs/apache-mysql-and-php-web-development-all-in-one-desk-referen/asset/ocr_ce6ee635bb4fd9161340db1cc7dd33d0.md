```
wm title . "Listbox Demo 2"
pack propagate . off

frame .buttonbar
pack .buttonbar -side top

button .buttonbar.bt1 -text "Add" -command {
} .lb insert end grapes kiwi
button .buttonbar.bt2 -text "Del" -command {
} .lb delete 1 3

pack .buttonbar.bt1 .buttonbar.bt2 \
    -side left -padx 5 -pady 5

listbox .lb -width 250 -height 250
pack .lb -side bottom

.lb insert end apple banana orange

# Create a handler to catch double-clicks from the listbox
# Note: This is a digit 1 after the word Double!
bind .lb <Double-1> {
    tk_messageBox -icon info -message [selection get]
}
```

In this program, you'll first notice that I have included more than one button. But these buttons are inside a frame. A frame is nothing more than a holder for other widgets. The pack command requires you to use a great deal of -side parameters for some complex layouts, and I find that if I want a row of buttons across the top of my window, it's easier to just put a frame at the top, and then fill the frame with my buttons. Thus, in this example program I created a frame, and then created some buttons. Notice how I named the buttons by starting with the frame, as in .buttonbar.bt1.

Also notice that I included two extra parameters in the pack command, -padx and -pady. These just specify some blank space to include around the buttons that I'm packing. And you probably also noticed that I was able to include two buttons in a single pack command; that's not a big deal.

The first button's command inserts items into the listbox. Notice how I do this: I treat the listbox's name as a command, and I follow with a subcommand. The subcommand in the first button is insert, and the one in the second button is delete. The insert command takes an index, which can be either a number or the word end, and then several strings that I want to put in the listbox (in this case, it's the strings grapes and kiwi). The