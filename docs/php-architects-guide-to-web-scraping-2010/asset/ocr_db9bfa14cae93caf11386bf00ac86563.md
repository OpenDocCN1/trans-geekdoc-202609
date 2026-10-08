ties include `firstChild` and `lastChild`. **Leaf nodes** are nodes that have no children, which can be checked using the `hasChildNodes` method of `DOMNode`.

All nodes in a tree have a single **parent node**, with one exception: the **root node** from which all other nodes in the tree stem. If two nodes share the same parent, they are appropriately referred to as **sibling nodes**. This relationship is shown in the `previousSibling` and `nextSibling` properties in `DOMNode`.

Lastly, child nodes of a node, child nodes of those child nodes, and so on are collectively known as **descendant nodes**. Likewise, the parent node of a node, that parent node’s parent node, and so on are collectively known as **ancestor nodes**.

An example may help to showcase this terminology.

```
```
<html>
<body>
<ul id="thelist">
<li>Foo</li>
<li>Bar</li>
</ul>
</body>
</html>
```
```

+   • `html` is the root node.

+   • `body` is the first (and only) child of `html`.

+   • `ul` is the first (and only) child of `body`.

+   • The `li` nodes containing **Foo** and **Bar** are the first and last child nodes of `ul` respectively.

+   • The `li` node containing **Bar** node is the next sibling of the `li` node containing **Foo**.

+   • The `li` node containing **Foo** is likewise the previous sibling of the `li` node containing **Bar**.

+   • The `ul` and `li` nodes are descendants of the `body` node.