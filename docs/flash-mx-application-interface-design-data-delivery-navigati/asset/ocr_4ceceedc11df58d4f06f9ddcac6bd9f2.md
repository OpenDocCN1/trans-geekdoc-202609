Place this method directly after the NodeClass's translate method:

```
```javascript
NodeClass.prototype.showChildren = function() {
  var childrenNum = this.node.children.length;
  if (childrenNum < 1) { return false };
  if (this.children != undefined) { return false };
  this.children = [];
}
```
```

showChildren is what we called in our center method, that will – you guessed it – show the node's children. Before we do this, we need to make a few checks to make sure we have anything to show. The first thing we do is place the number of children the node has into a variable, childrenNum. If this number is less than 1, that means there are no children to show, and so we exit out of the function. Second, we check to see if the children are already expanded. You will see that as soon as we attach the children, we will store references to these children in this node's children array. If this array already exists, that means the children are attached and we do not need to continue, so we exit the function. If we have made it this far, we go ahead and create the children array and get ready to add the children.

Finish off the showChildren method with the following:

```
```javascript
var i = 0;
while (i < childrenNum) {
  var angle = pi/(childrenNum+1) * (i+1) + this.angle;
  var distance = this.diameter*childDistance;
  var props = {};
  props.node = this.node.children[i];
  props.parent = this;
  props.angle = angle - pi/2;
  props.x = this.x;
  props.y = this.y;
  props.tX = Math.cos(angle) * distance + this.tX;
  props.tY = Math.sin(angle) * distance + this.tY;
  props.tZ = props.z = this.tZ - childDepth;
  this.children.push(this._parent.attachMovie("nodeSymbol",
      this.node.children[i].name + this._parent.depth,
      this._parent.depth--, props));
  i++;
}
}
```
```