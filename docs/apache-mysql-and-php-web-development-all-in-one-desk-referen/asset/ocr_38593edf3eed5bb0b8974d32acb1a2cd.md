```
wm title . "Save file dialog demo"
label .mylabel -text .
pack .mylabel -side top
set filetypes {
{"some files" {"*.txt" "*.abc"} }
{"other files" ("*.def" "*.123") }
}
button .mybtn -text "File..." -command {
set result [tk_getSaveFile \\
-filetypes $filetypes \\
-defaultextension ".txt" -initialdir "/"]
if {$result != ""} {
.mylabel configure -text $result
}
}
pack .mybtn -side top
```

This dialog box works the same way as the Open File dialog box; if you haven't done so already, take a look at the previous section, “Choosing a File to Open,” to see how the different options work.

![](bbox=[0.115, 0.485, 0.215, 0.565])

The tk_getSaveFile command doesn't actually save a file; it simply lets the user pick a filename. It's up to your program to then save the file. You can save a file using the open command and the puts command.

# Grabbing a Color

A color chooser is a handy dialog box. Those of us who used the early Macintosh computers remember how this dialog box was by far the coolest dialog box on the Mac, because it showed a gazillion colors at once on the old color screens. That dialog box alone probably sold 10,000 Macintosh computers. And now other operating systems feature a similar dialog box as well. Not to be left behind, the designers of Tk have given you access to this dialog box. Here’s an example:

```
wm title . "Color box demo"
canvas .mycanvas -width 300 -height 300
pack .mycanvas -side bottom
label .mylabel -text Color
pack .mylabel -side top
```