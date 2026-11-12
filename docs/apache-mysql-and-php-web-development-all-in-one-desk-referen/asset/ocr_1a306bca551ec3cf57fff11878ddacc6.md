Here I make use of a special syntax that gives you the end of the located text. The search command returned the found position, and I stored that in the res variable. For the end position, I use this line:

```
"$res + $foundsize chars"
```

This is a special way of specifying text later in the text widget. Don't worry too much about the mechanics here, because it only makes a little bit of sense; the chars word is a built-in keyword that you must use here. The key here is that $res is the start position and $foundsize is the length of the selection.

And finally, I call the focus command, which is a special command that moves the focus to the requested widget, in this case the text box. (Otherwise focus stays on the button that you clicked.)

# Loading and saving a file

In this final section of this chapter, I want to show you how to load a file into a text widget and save the contents of a text widget to a file. Here's one way:

```
proc LoadFile {atextbox filename} {
if {[file exists $filename]} {
set myfile [open $filename "r"]
while {[eof $myfile]} {
set buf [read $myfile 10000]
$atextbox insert end $buf
}
close $myfile
} else {
tk_messageBox -icon info -message \
"Sorry, I couldn't find the file."
}
}
```

```
proc SaveFile {atextbox filename} {
set myfile [open $filename "w"]
puts -nonewline $myfile [$atextbox get 1.0 end]
close $myfile
}
```

```
text .textbox -width 40 -height 15
pack .textbox
LoadFile .textbox "address.txt"
SaveFile .textbox "address2.txt"
```

This loads a file called address.txt (containing our favorite, The Gettysburg Address) that I created earlier, and then resaves text to a new file called