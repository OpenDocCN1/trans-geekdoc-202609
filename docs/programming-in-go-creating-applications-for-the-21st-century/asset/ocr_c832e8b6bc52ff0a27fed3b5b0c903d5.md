# 308 Chapter 6. Object-Oriented Programming

We don't have to explicitly initialize the new node's left and right fields (i.e., its leaves) since Go will automatically set them to their zero values (i.e., nil), so we use the struct's key: value syntax to initialize those fields that have nonzero values.

If the new key is the same as an existing key we reuse the existing key's node, and replace its value with the new value. (This is the same behavior as the built-in map type.) A consequence of this is that every item in an ordered map has a unique key.

```
func isRed(root *node) bool { return root != nil && root.red }
```

This tiny helper function returns whether the given node is red; it treats nil nodes as black.

```
func colorFlip(root *node) {
    root.red = !root.red
    if root.left != nil {
        root.left = !root.left.red
    }
    if root.right != nil {
        root.right = !root.right.red
    }
}
```

This helper function flips the colors of the given node and all of its non-nil leaves.

```
func rotateLeft(root *node) *node {
    x := root.right
    root.right = x.left
    x.left = root
    x.red = root.red
    root.red = true
    return x
}
func rotateRight(root *node) *node {
    x := root.left
    root.left = x.right
    x.right = root
    x.red = root.red
    root.red = true
    return x
}
```

These functions rotate the root's subtree to maintain the subtree's balance.

```
func (m *Map) Find(key interface{}) (value interface{}, found bool) {
    root := m.root
    for root != nil {
        if m.less(key, root.key) {
            root = root.left
        } else if m.less(root.key, key) {
            root = root.right
        } else {
            return root.key, true
        }
    }
    return nil, false
}
```