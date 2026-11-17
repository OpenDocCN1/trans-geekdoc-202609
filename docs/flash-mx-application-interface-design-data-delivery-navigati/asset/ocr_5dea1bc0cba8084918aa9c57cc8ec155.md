We're then setting the scroll position to be 0 (so the scrollbar is scrolled to its absolute top). Then finally, we're setting two things in the title bar; the number of files visible (items) and the path of that particular folder, like in the top of this image:

![](bbox=[0.043, 0.209, 0.455, 0.336])

That's the end of the loader2.onLoad function.

When the Navigate up button is pressed, to take us back up a level, the following code, attached to the Navigate up button, is run:

```
```
_root.matchDir = _root.parentdir[
    _root.dirlevel];
_root.loader2.load (_root.baseURL add
"dirstuff.php?matchExt=" add
_root.matchExt add "&matchDir=" add
_root.matchDir);
```
```

This code moves back in the parentdir array, to the previous directory, and then reissues the loader2.load function.

Now, back to the scrolling. In order to facilitate this – to bring it to life – we use the following code:

```
```
filescroll.setChangeHandler ("scrolling");
scrolling = function()
{
    _root.anchor._y = -
    filescroll.getScrollPosition();
}
```
```

It's very simple, thanks to the use of anchor. We're telling the scrollbar to call the function scrolling, whenever the thumb is moved, or 'scrolled'. By taking the current scroll position (the value returned by the scrollbar) and applying it to the _y parameter of the anchor, all our files will move up or down, as the scrollbar is moved.

# ## The rest

The remaining interface items consist of the JPG viewer, the text file viewer and the MP3 player. As cool as they are, however, they're not the focus of this chapter, which is supposed to illustrate the cool file interface, and not get into players and viewers as well. Feel free to explore and learn the code – it's all very simple. The most complicated code is the MP3 player, which handles streaming and time display in order to play properly. The other two – JPG and text file – are actually controlled, for the most part, by the handleFile function in the FileInfoComponent itself.

One of the nice things about this interface is that it's really quite easy to change the graphics as we see fit. As we saw earlier, each frame of this movie clip corresponds to a different file type icon.

Changing the images is as simple as editing the fileInfoIcon movie clip within the FileInfoComponent assets folder in the library.

![](bbox=[0.61, 0.642, 0.798, 0.845])

![](bbox=[0.043, 0.922, 0.893, 0.989])