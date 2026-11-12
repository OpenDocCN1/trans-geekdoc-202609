```
}
}
pack .mybtn -side top
```

Here's how it works:

+   1. The button's command calls the tk_dialog function, passing first a name for the dialog box (why, I don't know, but it's required, even though you don't use it again).
+   2. Next you pass a string that will appear in the title bar of the dialog box.
+   3. Then you pass the name of an icon bitmap. (Feel free to use one of the pre packaged bitmaps. See the sidebar "Displaying the standard bitmaps" in this chapter for more information on the pre packaged bitmaps.)
+   4. Next you add a number that's the default value returned by the dialog box in case the user closes the dialog box without choosing one of the buttons.
+   5. And finally, you include all the strings you want to display on the different buttons. Just list them one after the other.

You can see how this all looks in Figure 9-3.

![](bbox=[0.13, 0.55, 0.55, 0.64])