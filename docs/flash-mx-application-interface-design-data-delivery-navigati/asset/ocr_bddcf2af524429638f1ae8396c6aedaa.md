The subsequent three lines set some properties of the text field to be switched on or off. The `background` is switched on, giving us a default white rectangle in which to contain our text. The `selectable` property is set to `false` and this prevents the cursor from changing from pointer to text-selectable if it inadvertently rolls over the floating label. (Try commenting this line out and you will see that it causes all sorts of problems if we leave the default setting as on.) Next up is the `autosize` property, and we've set this to be on by giving it the Boolean value of `true`. This essentially fits the text field snugly around the text it contains – it resizes our white rectangular text container depending on the number of characters the text field displays.

Following on, we see that the next line defines an `onEnterFrame` function that is used to animate the floating label and update its contents as buttons are rolled over. The first four lines of code in our callback function provide the sliding inertia movement to the label so that the label floats towards the pointer in the both the x and y axis. The line `_root.label.insidesize.text = _root.select;` populates the text field with the value `root.select`, which as we will see later is updated every time we roll over a button. The last line of code in this block sets the text field to our previously defined Uformat text format.

The last block of code in frame 1 is partly similar to the previous block, dealing specifically with the 'size label' – this time the label is animated around a circular path when a button is clicked, its final position on the path being dependent upon the value it is displaying, `_root.size`:

```
_root.createEmptyMovieClip('sizelabel', 993);
_root.sizelabel.createTextField("insidesize", 0, 0, 40, 30, 18);
_root.sizelabel.insidesize.selectable = false;
_root.sizelabel.onEnterFrame = function() {
    this._x = 470 + Math.cos(degrees / 180 * Math.PI) * 75;
    this._y = 140 + Math.sin(degrees / 180 * Math.PI) * 75;
    if (count*10 < _root.size) degrees+=7;
    count++;
_root.dial.createEmptyMovieClip('indial', -387);
with (_root.dial.indial) {
lineStyle(1, 0xFFFFFF, 60);
moveTo(486, 191);
lineto(this._x+20, this._y+50);
}
_root.sizelabel.insidesize.text = _root.size;
_root.sizelabel.insidesize.setTextFormat(Tformat);
}
```

![](bbox=[0.67, 0.098, 0.958, 0.265])

![](bbox=[0.67, 0.27, 0.958, 0.435])

![](bbox=[0.67, 0.44, 0.958, 0.61])

![](bbox=[0.67, 0.615, 0.958, 0.755])

![](bbox=[0.67, 0.76, 0.958, 0.925])