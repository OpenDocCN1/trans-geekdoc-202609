Another fun thing in Repton was drawing pictures in the map designer. You could do a self-portrait out of boulders and diamonds, and watch the whole thing fall apart in real-time when you played the level. Great days.

For those of you who don't fancy clearing the cobwebs of the attic, here is a modern Flash interpretation (with nearing resolution and all -- see SpecDraw.fla):

The beeb was used for much more than gaming though. It also had some pretty sophisticated graphics commands, and image-programming abilities that are still better than what Flash has only just achieved. PLOT, MOVE, and GCOL, were my first experiences with the world of vectors, but to be perfectly honest, I don't think I ever called them vectors back then. To me they were just lines. I actually made a pretty complicated (for me) drawing program with both line and pixel capabilities – admittedly it started off as an example program that came with a mouse, but I altered it enough to make it my own. Unfortunately, I can't get a screenshot of this in the book because my beeb only works nowadays if I open it up and hold down the BASIC ROM when I turn it on, and even then it sometimes decides to just sit and beep at me instead of booting up. If anyone out there has a beeb in good working order that they want to get rid of, then I'll be more than happy to give it a good home.

# My drawing app (Spectrum ZX+)

The affectionately titled Specy was superb for graphics. In essence, it is the lo-fi graphic lover's dream, with it's clashing colors and limited color palette.

To say I pushed these graphic capabilities to their limit is talking rubbish. The best I could come up with (besides dodgy moiré patterns) was a drawing application, minus an interface. The drawing program resembled the classic etch-a-sketch tool: pen down... and still down. It was impossible to take the pen off the paper, but it had a groovy feel all the same, because sometimes limitations are good.

It also tests your memory, guesswork and keypressing, when you try to calculate where you are going over a previously drawn line.

```
// speccy draw by ken jokol / pinderkaos.com
// movieclip inits
_root.createEmptyMovieClip("root", 1);
lines.lineStyle(1, 0x000000, 100);
inc = 10;
rightBound = 250;
downBound = 190;
currentX = 130;
currentY = 80;
lines.moveTo(currentX, currentY);
// keys code
checkDir = new Object();
checkDir.onKeyDown = function() {
if (Key.isDown(Key.LEFT)) {
yAdd = 0;
xAdd = -inc;
}
if (Key.isDown(Key.RIGHT)) {
yAdd = 0;
xAdd = inc;
}
if (Key.isDown(Key.DOWN)) {
yAdd = inc;
xAdd = 0;
}
if (Key.isDown(Key.UP)) {
yAdd = -inc;
xAdd = 0;
}
currentX += xAdd;
currentY += yAdd;
if (currentX>rightBound) {
currentX = rightBound;
}
if (currentX<0) {
currentX = 0;
}
if (currentY>downBound) {
currentY = downBound;
}
if (currentY<0) {
currentY = 0;
}
lines.lineTo(currentX, currentY);
};
Key.addListener(checkDir);
```