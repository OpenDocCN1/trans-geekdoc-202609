
Figure 8-13: You can embed widgets right inside a text control.

![](img/3f967ab8a8fddc723173059f56621648_358_0.png)

## Searching

An important feature of any good text control is searching. The following example shows you how easy it is to search for text. When you run this example, type a string inside the entry box (which is just a scaled-down single-line text box) and click the Find button, and you'll see the next instance of the found text highlighted. Very easy indeed. (You don't have to type in the whole Gettysburg Address as I do here; you can enter whatever you want in the text box.)

```
wm title . "Text Search"

text .textbox -width 40 -height 15 -font {Helvetica 12} \
-wrap word
pack .textbox -side bottom
entry .word -textvariable whattofind
pack .word -side left
button .findbtn -text "Find" -command "FindText"
pack .findbtn -side left

proc FindText {} {
global whattofind
set res [.textbox search -count foundsize \
whattofind insert]
if {$res != ""} {
.textbox tag delete sel 0.0 end
# See the text for an explanation of
# the following strange lines!
.textbox mark set insert "$res + $foundsize chars"
.textbox tag add sel $res "$res + $foundsize chars"
focus .textbox
}
}

.textbox insert 1.0 \
{
Four score and seven years ago our fathers brought \
forth on this continent a new nation, conceived in \
liberty and dedicated to the proposition that all men \
are created equal. Now we are engaged in a \
great civil war, testing whether that nation or any \
nation so conceived and so dedicated can long endure. \
We are met on a great battlefield of that war. We have \
come to dedicate a portion of that field as a final \
resting place for those who here gave their lives that \
that nation might live. It is altogether fitting and \
proper that we should do this. But in a larger sense, \
we cannot dedicate, we cannot consecrate, we cannot \
hallow this ground. The brave men, living and dead who \
struggled here have consecrated it far above our poor \
power to add or detract. The world will little note nor \
long remember what we say here, but it can never forget \
what they did here. It is for us the living rather to be \
dedicated here to the unfinished work which they who \
fought here have thus far so nobly advanced. It is rather \
for us to be here dedicated to the great task remaining \
before us--that from these honored dead we take increased \
devotion to that cause for which they gave the last full \
measure of devotion--that we here highly resolve that \
these dead shall not have died in vain, that this nation \
under God shall have a new birth of freedom, and that \
government of the people, by the people, for the people \
shall not perish from the earth.}
```

The key to all this is in the FindText procedure, which runs in response to
the button. This procedure calls .textbox search, which performs the
search. This command returns the position of the search, which I store in
the res variable; the command starts looking at the current insertion location.
Further, in this command you can optionally include the name of a variable
that will receive the length of the found text; I chose to call this variable
foundsize.

After the search, I move the insertion point to the start of the found text. To
do so, I use the following line:

```
.textbox mark set insert "$res + $foundsize chars"
```

This line and the next have a strange syntax in them, which I describe
shortly. The next line is where I select the text. To select text, simply use the
tag called sel. You don't need to create this tag; it exists automatically,
unlike other tags. But notice how I highlight the text:

```
.textbox tag add sel $res "$res + $foundsize chars"
```

Here I make use of a special syntax that gives you the end of the located text. The search command returned the found position, and I stored that in the res variable. For the end position, I use this line:

```
"$res + $foundsize chars"
```

This is a special way of specifying text later in the text widget. Don't worry too much about the mechanics here, because it only makes a little bit of sense; the chars word is a built-in keyword that you must use here. The key here is that $res is the start position and $foundsize is the length of the selection.

And finally, I call the focus command, which is a special command that moves the focus to the requested widget, in this case the text box. (Otherwise focus stays on the button that you clicked.)

## Loading and saving a file

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

This loads a file called address.txt (containing our favorite, The Gettysburg Address) that I created earlier, and then resaves text to a new file called address2.txt. The LoadFile procedure that I have included here checks if the file exists, and if so, opens the file and begins reading in it. I don't read the file in line by line, however, using the gets command. That's because I want to copy the exact contents and paste it byte-for-byte into the text widget. (When I tried this with the gets command, the newlines got lost.) So instead I use the read command, which reads text into a buffer. I keep reading more and more text, adding it to the end of the text widget, until I reach the end of the file.

The save is even easier. In my SaveFile procedure, I open a file, grab the whole text from the widget, and write it all out in one swoop using the puts command. (Notice that I included an option in puts called nonewline, which makes sure not to add an extra newline at the end that wasn't already there.) Then I close the file. Easy!

## Chapter 9: Displaying Standard Dialog Boxes in Tk

### In This Chapter

- Getting input from a message box
- Selecting a directory
- Choosing a file to open
- Picking a filename to save
- Grabbing a color
- Creating a generic dialog box

Some time back, designers of the various operating systems figured out that certain tasks required certain dialog boxes that came up again and again. And rather than force programmers to reinvent the wheel every time they wanted to create these dialog boxes, the designers decided to give them some standard dialog boxes instead.

You're probably very familiar with the standard dialog boxes on your operating system of choice. These include, among others, a dialog box for File Open, and a dialog box for File Save. Tk lets you access these standard dialog boxes. In addition, Tk has a special generic dialog box that you can use for special situations where you want the user to select from a set of buttons. In the following sections, I give you the whole scoop and nothing but the scoop on these dialog boxes.

### Getting Input from a Message Box

The simplest type of stock dialog box is the message box. Here's a sample program that you can try out:

```
wm title . "Message box demo"
tk_messageBox -icon info -message \
"Greetings from a message box!"

set res [tk_messageBox -icon warning -message \
"Now go away, please." -type yesno]
```

```
if {$res == "no"} {
tk_messageBox -icon info -message \
"Okay, I guess you can stay. We're having a party."
}
```

This program opens a message box using the tk_messageBox function. The message box that opens has a message (Greetings from a message box!) and an OK button. After the user clicks OK, the program opens a second message box, but this one requires the user to click either Yes or No. The user makes a choice, and the program saves the result in the res variable.

If the user clicks the No button (that is, if res equals "No"), the program opens up another dialog box (just for fun). Figure 9-1 shows the sequence of message boxes that I just described.

![](img/3f967ab8a8fddc723173059f56621648_363_0.png)

The main differences in the message boxes in the preceding program are in the choice of buttons and the choice of an icon. I selected the buttons using the -type option, and I selected the icon using the -icon option. Here are the choices for the -type option:

- abortretryignore: Please don't use this one. It's outdated, and users cringe when they see it. (At least this user does.)
- ok: This is the default, so if you leave off the -type option, you'll just get an OK button.
- okcancel: This gives you an OK and a Cancel button.
- retrycancel: If you want your program to try an action again and again at the user's request, you can use this type.
- yesno: Hopefully your users will be able to make up their minds between yes and no.
- yesnocancel: But, if they can't choose between yes and no, you can also include a Cancel button. Yes no?
