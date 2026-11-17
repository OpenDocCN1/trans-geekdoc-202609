The setWait method just stores the arguments that it has been passed for later use:

```
clusterNode.prototype.setWait =
➤ function(obj,method,args) {
    this.waitObj = obj
    this.waitMethod = method
    this.waitArgs = args
}
```

To go with this we also create a checkWait method. When a node closes, it will call this method in its parent. It basically checks if it has a method waiting to be executed, a waitMethod, calls it and then deletes the method, along with its corresponding object and argument:

```
clusterNode.prototype.checkWait =
➤ function() {
    this.waitObj[this.waitMethod]
    (this.waitArgs)
    delete this.waitObj
    delete this.waitMethod
    delete this.waitArgs
}
```

The procedure for closing a node's children will work in a similar way to the addKids method we created earlier, in that it is one method that calls a series of other methods:

+   closeKids – initiates the closing. Checks if any of its children have sprouted their own children. If so, it calls closeKids for that node. If not, it checks that it has kids and then sets onEnterFrame to closeNextKid.

+   closeNextKid – this method decrements a counter and calls closeMe for the next child node.

+   closeMe – sets new targets for the radius and radians so that it will move back to its parent. Sets onEnterFrame to goClose.

+   goClose – decrements alpha. Moves node towards its parent. Calls the parent's removeChild method when it is close enough.

+   removeChild – this method is passed a number and the node removes the child corresponding to that entry in the array. It decrements its kidCount. When kidCount reaches zero, all the nodes have been closed and it calls allClosed.

+   allClosed – deletes kidOpen in the node's parent. Calls the parent's checkWait method.