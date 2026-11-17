If you run the code like that, you'll see that it draws the main node in the center, surrounded by five child nodes. We've plotted the nodes around the edge by using basic trigonometry. Each point is positioned on the edge of a circle with the radius clusterRadius at the angle this.segment * i. So on the x-axis we take the cosine of the angle and multiply it by the radius, and on the y-axis we do the same using the sine of the angle. The new movie clips are attached within the original node, so all of the co-ordinates are relative to the center point of the original node.

While this does get the job done, it's not very visually appealing. What we want instead is to create the nodes one at a time and have them move to their target position around the edge of the original node. We're going to need to write some more methods to do this.

+   addKids – triggers the addition and initializes counter variables. Informs its parent node that it has opened. Sets the onEnterFrame handler to addNextKid.

+   addNextKid – if it has not already created all of its children it calls createChild to create the next child.

+   createChild – creates a new clusterNode object, passing it all the relevant data. Calls the moveToPosition method for this new node, passing the target radius to moveto.

+   moveToPosition – stores the target radius. Sets the onEnterFrame handler to rotateMe.

+   rotateMe – calls moveToTarget each frame. If moveToTarget returns true clears the onEnterFrame handler.

+   moveToTarget – gradually shifts the node's radian and radius properties until they equal the target values, at the same time shifting the node's position on stage. Returns true when it has reached the target.

That looks like quite a lot of methods, but each one is a necessary part of the mechanism. Generally we have one method to initiate an action, and then another method that is called every frame to carry out that action over time and create the motion, the animation.

First of all we have the addKids method, new and improved to replace the one we wrote before:

```
clusterNode.prototype.addKids = function() {
    this.kidCount = 0
    this._parent.kidOpen = this
    this.opening = true
    this.onEnterFrame = this.addNextKid
}
```