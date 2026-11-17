We're almost there, but you can see we have a few problems that have cropped up. First, the content is seen before the window is fully open, and second, the content is not removed immediately when a new section is selected. Let's take care of the first problem by adding a mask to reveal the content. We will do this in our addContent code.

Place these lines at the end of the addContent function, immediately after the formatting of tb:

```
this.createEmptyMovieClip("contentMask", 50);
content.setMask(this.contentMask);
```

That's easy enough, but all we actually have is an empty clip. We need to draw something inside it to serve as our masked region. We will take care of this in the extendBottomSide function, which is appropriate since this is where we want the mask to slowly reveal the content.

Place these lines before the final if statement in the extendBottomSide function:

```
this.contentMask.clear();
this.contentMask.beginFill(0, 0);
drawBox(this.contentMask, -mc.leftSide, -buttonHeight, -branchDown,
-> mc.bottom);
this.contentMask.endFill();
```

Now we have something! The box inside contentMask can be drawn with the drawBox function since we want a rectangular mask for our content. As mc.bottom is adjusted a little each function call, the mask will extend with the drawn borders to reveal more content.

One last thing to take care of, and that's the removal of previous content. This can be accomplished with just a few extra lines within the selectMe function, which is the point where we need previous content removed.

Add the following line to the beginning of selectMe (still on the sections code layer). It can be added anywhere before the first for loop.

```
this._parent.content.removeMovieClip();
```

So the content is removed. To take care of the mask as well, add the following new line to the second for loop:

```
for (var i in sectionButtons) {
    if (sectionButtons[i].selected) {
    sectionButtons[i].onEnterFrame = retractLeftSide;
    sectionButtons[i].contentMask.removeMovieClip();
    sectionButtons[i].btn.enabled = 1;
    delete sectionButtons[i].selected;
    }
```

With these additions, test your movie and see what we've accomplished!

![](bbox=[0.702, 0.102, 0.952, 0.222])

![](bbox=[0.702, 0.232, 0.952, 0.352])

![](bbox=[0.702, 0.362, 0.952, 0.482])

![](bbox=[0.702, 0.492, 0.952, 0.602])

![](bbox=[0.702, 0.612, 0.952, 0.732])

![](bbox=[0.702, 0.742, 0.952, 0.852])

![](bbox=[0.702, 0.862, 0.952, 0.982])