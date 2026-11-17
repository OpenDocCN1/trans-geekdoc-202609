Continue with the drawLaser method by adding the following lines of code:

```
```
for (var i in logo) {
    if (typeof logo[i] == "movieclip") {
        if (logo[i].hitTest(this.contactPoint.x,
            this.contactPoint.y, 1)) {
            var logoColor = new Color(logo[i]);
            var laserColor = logoColor.getRGB();
            break;
        }
    }
}
```
```

To understand this code, you will need to understand how I have set up the logo. Enter symbol editing mode. You will find that the logo is separated into layers, and each layer contains an element of a different color. If you select any of the elements, you will find that each layer contains its own movie clip, and that the movie clip has been colored in the Properties panel. It is set up in this way so that we can use the Color object's built-in getRGB method to determine each clip's color when a laser is over it. For this reason we not only need to separate each color into its own movie clip, but we need to then tint that movie clip 100% of its base color (look down to the Properties panel again to see evidence of this). Currently, there is no way for Flash to determine a clip or pixel's color, so we must create this workaround to accomplish our task.

![](bbox=[0.08, 0.66, 0.32, 0.97])

As to the code, the for in loop above runs through each property inside of logo. If a property (which can be an object) is a movie clip, then it tests to see if the point of contact for the laser (stored in this.contactPoint, which is set in the getContactX function that we will write next) hits that logo movie clip. If it does, then it creates a temporary Color object and uses it to find the color of that element using the getRGB method. It stores that color in the variable laserColor. Having found one color, we need no longer search and so we break out of the loop.

If you are wondering about the difference between the x and y values stored in this.contactPoint and the values stored in beamX and beamY, you will see when we set up the values for contactPoint that they are relative to the main timeline, whereas beamX and beamY are relative to the laser movie clip. We need the contactPoint values in order to call hitTest, but we will need the beamX and beamY values to draw the laser graphic correctly inside of the laser movie clip.

The last bit of this function is a piece of cake. Finish it off by adding these lines:

```
```
this.clear();
this.lineStyle(2, laserColor, 100);
this.lineTo(this.beamX, this.beamY);
}
```
```

Pretty easy. We clear the previously drawn beam graphic and reset the lineStyle (thickness, color and alpha for the laser), which is cleared every time the clear method is called. We then draw our line from the laser's origin (0,0) to whatever values we assigned to beamX and beamY.

The next, and final, method is a bit of a bear, and the most complicated of this project. Let's walk through it slowly.

![](bbox=[0.35, 0.87, 0.93, 0.97])