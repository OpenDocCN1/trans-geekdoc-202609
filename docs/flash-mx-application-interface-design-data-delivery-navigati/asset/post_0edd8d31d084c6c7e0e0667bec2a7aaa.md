
We can add a little extra code to make the sub-node open once it has reached its target. All we need to do to achieve this is add a few extra lines to the rotateMe method that controls the motion. Basically we just add a conditional which, when the node reaches its target, checks whether its target radius is equivalent to separator which indicates that it has been opened. If so, we call the node's addKids method. We could add a separate property to indicate that the clip is sprouting, but it's probably sufficient just to use the radius value for now:

```
clusterNode.prototype.rotateMe = function() {
if(this.moveToTarget(1)) {
delete this.onEnterFrame
if(this.radiusTarg==this.separator){
this.addKids()
}
}
}
```

If you run the code here, or check out spinner006.fla, you'll see that once each node has sprouted to the right it then opens its own children. You can navigate all the way down the tree doing this, but at the moment it's impossible to go back up. This is because the kidOpen property is set in the parent as soon as one of its child nodes opens its own children. Next we'll work on making the tree close as well as open.

![](img/50202c17d5022233f3e3ec60560e35aa_136_0.png)

## Queuing actions

The next stage in building this interface is to allow the user to move back up the tree to take an alternate path, to open a different set of branches. This complicates matters somewhat. So far we have been able to call open and have that branch open. What we need to implement here is a mechanism whereby one clicks a node and it then checks if any of its siblings are open. If they are open, then they must first be closed, and only when they are closed can the selected node open. This is complicated further by the fact that if the user has traversed far down the tree and then clicks to open a different top-level category, the interface might have to close two or three clusters before it can open the new top-level category.

To circumvent this situation we have to build in a series of checks. When the user clicks to open a category that already has one of its siblings open, we will have to first call a method closeKids that will close the open node. We will also queue an action in the parent node. When the child node has removed all of its children it will then call this method that's waiting in the parent. The same thing will apply when calling the closeKids method. If the child that is open has one of its own children open then that will have to be closed first, and so on until you reach a node with no open children.

First of all then, we need to make modifications to the openChild method:

```
clusterNode.prototype.openChild=function(mc) {
 if(this.kidOpen) {
 this.setWait(this,"openChild",mc)
 this.kidOpen.closeKids()
 }else{
 this.redoRadians(mc)
 for(var i in this.kidMCs) {
 if(this.kidMCs[i]==mc) {
 this.kidMCs[i].moveToPosition(this.separator)
 }else{
 this.kidMCs[i].moveToPosition(this.clusterRadius)
 }
 }
 }
}
```

Now when a node is told to open one of its children and it already has a child open, it will do two things. First of all it calls a setWait method, passing it three arguments. These correspond to an object, a method name and a parameter to pass. We'll write this method in a moment. After it has stored these, we then call the closeKids method in the child that is already open.

![](img/50202c17d5022233f3e3ec60560e35aa_137_0.png)

The setWait method just stores the arguments that it has been passed for later use:

```
clusterNode.prototype.setWait = function(obj,method,args) {
    this.waitObj = obj
    this.waitMethod = method
    this.waitArgs = args
}
```

To go with this we also create a checkWait method. When a node closes, it will call this method in its parent. It basically checks if it has a method waiting to be executed, a waitMethod, calls it and then deletes the method, along with its corresponding object and argument:

```
clusterNode.prototype.checkWait = function() {
    this.waitObj[this.waitMethod](this.waitArgs)
    delete this.waitObj
    delete this.waitMethod
    delete this.waitArgs
}
```

The procedure for closing a node's children will work in a similar way to the addKids method we created earlier, in that it is one method that calls a series of other methods:

- closeKids – initiates the closing. Checks if any of its children have sprouted their own children. If so, it calls closeKids for that node. If not, it checks that it has kids and then sets onEnterFrame to closeNextKid.
- closeNextKid – this method decrements a counter and calls closeMe for the next child node.
- closeMe – sets new targets for the radius and radians so that it will move back to its parent. Sets onEnterFrame to goClose.
- goClose – decrements alpha. Moves node towards its parent. Calls the parent's removeChild method when it is close enough.
- removeChild – this method is passed a number and the node removes the child corresponding to that entry in the array. It decrements its kidCount. When kidCount reaches zero, all the nodes have been closed and it calls allClosed.
- allClosed – deletes kidOpen in the node's parent. Calls the parent's checkWait method.

## So to start with, we write the closeKids method:

```
clusterNode.prototype.closeKids =
  function() {
    if(this.kidOpen) {
      this.setWait(this,"closeKids")
      this.kidOpen.closeKids()
    }else{
      if(this.kidCount == 0) {
        this.allClosed()
      }else{
        this.removeCount = this.kidCount
        this.onEnterFrame =
          this.closeNextKid
      }
    }
  }
```

As you can see, the first conditional checks if any of its children has children open. If so, it calls closeKids for that child and stores closeKids as its own wait function. When its child has closed and removed its child nodes, it will then close and remove its own child nodes.

If none of its children has children open, we first check that the current node has children open, in case we click in the gap between a node starting to open and actually creating the movie clips. If it doesn't, we call allClosed straight away.

If the node does have children open, and none of its children has children open, then we can go ahead and close it, setting the remove counter to the value of kidCount and assigning closeNextKid to the enterFrame handler.

The closeNextKid method is quite simple. It just decrements removeCount and then calls the closeMe method for the next node in its kidsArray. When removeCount is less than zero, it removes the method from the enterFrame handler:

```
clusterNode.prototype.closeNextKid =
  function() {
    this.removeCount--
    this.kidMCs[this.removeCount].closeMe()
    if(this.removeCount < 0) {
      delete this.onEnterFrame
    }
  }
```

The closeMe method will be called for each node to be closed. It basically sets new targets for the node's radian and radius values.

```
clusterNode.prototype.closeMe =
  function() {
    this.radianTarg += 3
    this.radiusTarg = 0
    this.onEnterFrame = this.goClose
  }
```

![](img/50202c17d5022233f3e3ec60560e35aa_139_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_139_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_139_2.png)

Setting `radiusTarg` is self-explanatory, while we add three to the node's `radianTarg` (roughly equivalent to 180 degrees) so that it rotates as it closes – purely an aesthetic consideration.

Once we've set the new targets, we set the `onEnterFrame` handler to `goClose` which will handle the actual closing:

```
clusterNode.prototype.goClose = function() {
    this._alpha-=10
    if(this.moveToTarget(5)||
    this._alpha<=10)
    this._parent.removeChild(this.kidNum)
}
```

As we close each node we also reduce the alpha, making the effect slightly smoother. Next we call `moveToTarget` which handles the actual motion as earlier. Note that now we're passing it a value of 5 for tolerance, which means that it will be judged to have reached its target when it is within 5 pixels of it on the x and y axes. Once the node is either within 5 pixels of its parent node or its alpha is below 10, we call the `removeChild` method in the parent node, passing the current node's `kidNum`.

The `removeChild` method is straightforward. We remove the child node's movie clip and delete the corresponding entry in the `kidMCs` array. After that, we decrement the parent's `kidCount` value. When this value has reached zero all of its children will have been removed, and so we then call the node's `allClosed` method.

```
clusterNode.prototype.removeChild =
    function(num) {
        this.kidMCs[num].removeMovieClip()
        delete this.kidMCs[num]
        this.kidCount--
        if (this.kidCount==0) {
            this.allClosed()
        }
    }
```

Once all of the node's children have been closed, we then want to let the node's parent know that it can execute any queued actions. This is what is accomplished in the `allClosed` method:

```
clusterNode.prototype.allClosed =
    function() {
        delete this._parent.kidOpen
        this._parent.checkWait()
    }
```

So here we've done two things. Firstly we have removed the parent's `kidOpen` property, and secondly, we have called the parent's `checkWait` method, which executes any queued actions, either opening a different child or closing itself.

If you test the movie at this point, or `spinner007.fla`, you'll see that it's generally functioning correctly. The user can now click on any node, whether or not its parent already has open children, and the interface will go through the correct series of events to open the node.

![](img/50202c17d5022233f3e3ec60560e35aa_140_0.png)
