The curveTo command accepts four parameters. The final two parameters are the actual coordinates we are drawing to, which you can see we have already determined with our connX1, connX2, connY2 and y variables. The first two parameters are the coordinates that the line curves toward. In our case, we pick a y position halfway up our connector and an x position on the opposite side of center from the curve, giving us a nice concave shape.

![](bbox=[0.05, 0.26, 0.46, 0.72])

Test your movie to see what we have made. Fun!

You might notice an unwanted connector sticking out from our rootNode Chaos. Problem is, it doesn't have a node to connect to (poor Chaos!), so we need to make sure it doesn't try. We can fix it very quickly in our init method.

Add the following lines to our NodeClass's init method:

```
if (this._name == "rootNode") {
    this.render();
    return;
}

this.createEmptyMovieClip("connector", 1);
this.connX1 = connectorCos1 * this.radius;
this.connY1 = connectorSin1 * this.radius;
this.connX2 = connectorCos2 * this.radius;
this.connY2 = connectorSin2 * this.radius;
```

Here we have just done a quick check before we even add the connector movie clip. If the node is the rootNode, it renders itself and exits the method.

The rootNode will still run the drawConnector code unnecessarily, though, even if it has no connector movie clip, so let's add one more line to our drawConnector method:

```
NodeClass.prototype.drawConnector =
    ->function() {
    if (this._name == "rootNode") { return
    ->false };
    var x = this._x - this.parent._x;
    var y = this._y - this.parent._y;
```

Now the rootNode will immediately leave this function and not run the code. Test your movie to see everything in effect.

![](bbox=[0.49, 0.715, 0.91, 0.99])