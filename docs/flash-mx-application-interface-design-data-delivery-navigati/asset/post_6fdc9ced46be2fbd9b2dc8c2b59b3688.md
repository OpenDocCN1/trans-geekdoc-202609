
Go to the code layer where we wrote the tree.translate method and place this method beneath it:

```
tree.startRotate = function(amount) {
    this.rot = this._rotation;
    this.degrees = amount*180/Math.PI;
    while (this.degrees < -180) {
        this.degrees += 360 };
    while (this.degrees > 180) {
        this.degrees -= 360 };
    if (Math.abs(this.degrees - this.rot) > 180) {
        if (this.rot > 0) {
            this.degrees += 360
        } else {
            this.degrees -= 360
        }
    }
    rotateInt = setInterval(this, "rotate",
        intervalTime);
}
```

This code looks more confusing than it actually is. Basically, I store the tree's current rotation in rot since we will be adjusting this number during our animation and it needs to remain separate from the actual property. This is because the value might need to go beyond 180 or -180, which _rotation is never allowed to do (for instance, -190 will automatically be converted to 170). I store the degrees to rotate to in the variable degrees (which I convert from radians). If the degrees value is outside the range of -180 to 180, I adjust it. Once both degrees and rot are within the same range, I find the shortest rotation amount between the two and adjust degrees again if necessary. The adjustment is required in order to spin in the right direction. For instance, if degrees is 170 and rot is -170, 20 degrees would be the shortest distance to spin to reach the proper angle, not 340 degrees. In this case, 360 would be subtracted from degrees, leaving an amount of -190, which would allow us to spin the 20 degrees from -170 to -190. With rot and degrees set to be in the form we need them, I set an interval to call tree's rotate method, which we will write now.

Place this method right after the previous code:

```
tree.rotate = function(amount) {
    this.rot -= (this.rot -
        this.degrees)/intervals;
    this._rotation = this.rot;
    if (Math.abs(this.rot - this.degrees) < 1) {
        clearInterval(rotateInt);
    }
}
```

Another easing, motion-tweened animation. We just adjust the rotation of our tree a little each interval call. Once we're close enough, we clear the interval. Test your movie now to see the result.

![](img/50202c17d5022233f3e3ec60560e35aa_107_0.png)

See the problem? By rotating the tree we are also rotating each node, which in turn causes the text to rotate into unreadable positions. What we need to do is rotate the node graphic in the opposite direction as the tree. We'll create one final method inside NodeClass to take care of this.

Add this method after NodeClass's drawConnector method on the NodeClass layer:

```
NodeClass.prototype.rotateGraphics = \
    function(degrees) {
        this.nodeGraphic._rotation = degrees;
    }
```

Here we simply rotate the graphic of the node. Easy. Now to call this method, we could simply place a loop in the tree's rotate method that would run through its nodes. This would be the easy thing to do. What I want to do, however, is show you a new way of handling situations like this that perhaps is unnecessary in the current system, but you might find invaluable later. We are going to create a custom event.

There is an undocumented feature in Flash MX that will allow us to create our own custom events in our movies (events like onEnterFrame or onMouseMove), and then register objects to receive these custom events. For instance, you know that every instance of a movie clip automatically receives notification every time a frame is entered, and you can write a handler to run a function when that event occurs:

```
mcInstance.onEnterFrame = function() {};
```

In this case, the event is already defined and the movie clip is already set up to receive notification of the event. Now imagine if you could define your own events and decide which objects should receive notification when these events are fired. This is now possible, and it only takes a few lines of code. So let's give it a try!

Add this new line to the code immediately following the creation of our tree movie clip, on the code layer:

```
this.createEmptyMovieClip("tree", 0);
tree._x = windowWidth*.5;
tree._y = windowHeight*.5;
tree.depth = 15000;
tree.setMask(mask);

ASBroadcaster.initialize(tree);
```

ASBroadcaster is an undocumented object that allows us to enable new objects to broadcast events, which is what we would like tree to be able to do. The initialize method gives this ability to tree. Now tree can define new events to broadcast to the Flash movie.

Now we need to actually broadcast our custom event, which we will do every time we rotate our tree. Place these new lines in our tree.rotate method:

```
tree.rotate = function(amount) {
    this.rot -= (this.rot -
        this.degrees)/intervals;
    this._rotation = this.rot;
    if (Math.abs(this.rot - this.degrees) < 1) {
        clearInterval(rotateInt);
    }
    this.broadcastMessage("onRotate", -this._rotation);
}
```

Since we have initialized this object with ASBroadcaster, we can use broadcastMessage to fire a custom event. Now every time the tree.rotate function is called, it will send out the custom event onRotate to any object registered to receive it. In addition, we send an additional parameter, this._rotation, that can be used by the objects receiving the event.

Two more lines will do everything we need for our new event to work. First, we need to have objects that will receive this new event, and will hopefully act upon it.

Go to the NodeClass layer and add the following lines to the NodeClass's init method:

```
this._parent.addListener(this);
this.onRotate = this.rotateGraphics;

if (this._name == "rootNode") {
    this.render();
    return;
}
```

addListener adds this object (this node) as a listener for any event that tree (this._parent) will broadcast. On the next line, we assign a function for this custom event, in this case the rotateGraphics method we wrote just a few moments ago. Now, in addition to receiving notification of all of the standard movie clip events (enterFrame, mouseMove, load, and so on), our NodeClass instances will receive notification when the tree rotates as well, and they will use the onRotate handler when this event occurs.

Test your movie now to see how the nodes know when to rotate their graphics. This ability to assign custom events can come in extremely handy – and is pretty fun to play around with, too!

![](img/50202c17d5022233f3e3ec60560e35aa_109_0.png)

## Taking it further

What I've shown you in this chapter is how to build, manipulate and animate a branching structure. The finished file as was presented in this tutorial can be found in the download files as gods_tree_book.fla if you want to look at the code in its entirety. As you saw in the initial gods_tree.swf, I went on to build another level of functionality for this system by allowing the user to click on nodes to access additional information (plus I added spouse nodes to the system). All the code is commented, and I encourage you to open it up and take a look at how certain things were accomplished.

In addition, imagine where you could take this concept and this file further. Although it works well to display branching information, and indeed that is what it was built for, I couldn't help but think of some great games that could be built from this system, from a more sophisticated Whack-a-Mole to a Choose Your Own Adventure type interactive story. Instead of loading a single interface full of information, perhaps you could set the system up as a gallery where selecting a low-res image on a node loaded the higher-res full screen version. How about making the gallery system respond to the types of images that a user has previously chosen, loading similar or complementary images in the next generation? Maybe you could remove the user entirely and use some random generation and funky math to animate the nodes and the colors of the system to create some surrealistic Web-art. Or maybe I should stop giving my ideas away and beat you to the punch!
