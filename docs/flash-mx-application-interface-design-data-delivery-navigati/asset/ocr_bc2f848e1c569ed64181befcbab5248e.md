# Gooey connections

In the render method above, we called the drawConnectors method, which we will use to connect each of the nodes with its parent. This is my favorite part of this project as it adds a real organic feel to the system as well as taking advantage of dynamic gradient fills. (I just love that new drawing API – so many new toys!) To achieve this effect, we will need to add some variables in other parts of the code to help us out.

Go to the code layer and add these lines following the declaration of the pi variable:

```
connectorSin1 = Math.sin(-pi/3);
connectorCos1 = Math.cos(-pi/3);
connectorSin2 = Math.sin(-pi*2/3);
connectorCos2 = Math.cos(-pi*2/3);
```

Each of the nodes will use these values to find the x and y position of the corners of the connectors (which we will use the drawing API to create). Instead of having to calculate these values for each node, we place them in variables that we can access later. These hold the sine and cosine of angles -60 and -120 degrees, which is where we will place each corner of the connector in relation to the center of the node graphic.

With these values determined, we need to find the x and y points for each particular node. We will do this inside the init method for the NodeClass. Add the following lines to the end of the init method, but before the render call:

```
this.createEmptyMovieClip("connector", 1);
this.connX1 = connectorCos1 * this.radius;
this.connY1 = connectorSin1 * this.radius;
this.connX2 = connectorCos2 * this.radius;
this.connY2 = connectorSin2 * this.radius;
this.render();
```

You can see that first we add an empty movie clip named connector that will hold our drawing. Next we calculate the x and y positions of our connector's corners, based on our sine and cosine values multiplied by the radius of our graphic.

![](bbox=[0.49, 0.21, 0.9, 0.4])

Now it's time to create the drawConnector method, which will take care of the drawing of our gooey connectors. Place the beginning of this new method after the checkVisibility method of our NodeClass:

```
NodeClass.prototype.drawConnector =
function() {
var x = this._x - this.parent._x;
var y = this._y - this.parent._y;
this.connector.rotation =
Math.atan2(y, x) * 180/pi - 90;
var distance = Math.sqrt(x*x +
y*y)*100/this._xscale - this.radius*.25;
this.connector.clear();
this.connector.moveTo(this.connX1,
this.connY1);
```

x and y are local variables that hold the distance of our node from its parent node on each axis. Using this, we can determine the angle at which we need to rotate our connector movie clip by sending the values to the Math.atan2 method (which we multiply by 180/pi to convert to degrees, and subtract 90 from since Flash views 0 degrees as east and not north, which is what we need).