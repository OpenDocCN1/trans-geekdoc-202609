There is some additional code here too. This will be required for the final stage of our preliminary Flash movie.

The final elements of this movie are aimed at making it simpler to use. The first is a grid, which we can turn on or off to help make it easier to position the feet in the correct position. This grid will be positioned over the mat.

Create a new movie clip symbol called grid and draw a basic grid on it. The simplest way is to draw a hairline weight line and duplicate it 20 times or so. Drag the last duplicate to a position that will form the outer grid line, at least 400 pixels distance from the first line. Use the Align tools to space them equally. Select all, duplicate once more and rotate this new set of lines through 90 degrees. (Alternatively you could use my grid from the library if you’re feeling lazy.)

![](bbox=[0.106, 0.445, 0.488, 0.772])

Drag this new clip onto the main stage, on a new layer above the mat layer, called, surprisingly, grid. Name the instance grid and then create a new layer above this one and drag an instance of square on to it. Position this instance of square exactly over the mat and then turn the layer into a mask, and the grid layer to a masked layer.

We now need to create a button to both activate and

deactivate this grid. Do this by adding another button to the controller movie clip, with some graphics on the text layer to indicate what it does. Name this button gridBut.

![](bbox=[0.683, 0.195, 0.794, 0.285])

We need another bit of ActionScript to add functionality to this button. As it is associated with a button, I have placed it before the insert and record mode. This just keeps things neater. The code checks to see whether the grid is already visible – if it is it turns it off, and if it isn’t it turns it on:

```
controls.gridBut.onRelease = function() {
if (_root.gridvis == false) {
grid._visible = true;
gridvis = true;
} else {
grid._visible = false;
_root.gridvis = false;
}
};
```

We want it off to begin with which is why we have

```
gridvis = false;
grid._visible = false;
```

in the code that initializes everything at the foot of the ActionScript.