Next in our code, we have the onMouseDown function:

```
FileInfoClass.prototype.onMouseDown = function()
{
    if (!root.busy)
    {
        this.offx = _root._xmouse - this._x;
        this.offy = _root._ymouse - this._y;

        if (this.hitTest(root._xmouse,
        _root._ymouse, true))
        {
            this.startDrag();
            this.doSelect();

            root.mousepressed = true;
            root.mousestartx = root._xmouse;
            root.mousestarty = root._ymouse;

            this.g = getTimer();

            if (this.firstclick != true ||
            (this.g > (this.clicktime
            + this.doubleclickspeed)))
            {
                this.firstclick = true;
                this.clicktime = this.g;
            }
            else
            {
                if (this.g < this.clicktime +
                this.doubleclickspeed)
                {
                    this.handleFile();
                }
                this.firstclick = false;
            }
        }
        else
        {
            this.doDeselect();
        }
    }
}
```

This handles the double-clicking that we discussed earlier. There are also a few key differences.

We're making sure that the root.busy flag is not true – otherwise, this click must be ignored. We're checking to see if the file itself is being clicked on, via the hitTest method, and if so, we're calling our doSelect method. We're also making it draggable by calling the startDrag method. When we press the mouse button down, we want to also grab onto the file, and move it around, if we so desire. Finally, if this is a double click, then we call the handleFile method.

If the hitTest was false, then we call doDeselect. This means that only one file will be selected at a time, because unless we're clicking on a file, it'll deselect itself, and since we only have one mouse cursor on screen, we'll only ever be hitTesting with one file (unless they're stacked on top of each other, but then, startDrag will only drag one item at a time, anyway).

We then have one more function:

```
FileInfoClass.prototype.onMouseUp = function()
{
    this.stopDrag();
    root.mousepressed = false;
}
```

When the mouse is released, we want to stop all dragging, and set the mousepressed flag to false.

Lastly, we finish off with:

```
#endinitclip
```

This indicates that this is the end of the class definition.

Now we've seen the code attached to the FileInfoComponent, and how to send the contents of a directory with PHP, let's look at how to tie it all together, and parse the variables to create the directory layout on screen.