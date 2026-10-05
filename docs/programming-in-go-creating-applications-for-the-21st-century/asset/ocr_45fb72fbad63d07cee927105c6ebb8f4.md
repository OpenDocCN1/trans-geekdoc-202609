# 6.5. Examples

Although not, we can use the ordered map Delete(), Find(), and Len() methods on the distancePoint map in exactly the same way as we did for the wordFor map, but using *Point keys for the first two (since the less than function works in terms of *Points, not Points).

Now that we have seen the ordered map in we will review its implementation. We won't cover the Delete()'s helper method and functions, because some of them are really tricky and covering them won't add to our knowledge of Go programming. (All these functions are in the book's source code, of course, in the file qrac.eu/emap/emap.go). We will start looking at the two types we used to implement the ordered map (Map and node), and then the construction functions. Then we will look at the Map's methods and some of them short with more complicated processing passed on to helper functions. As common in Go programming, most methods are quite

```
type Map struct {
  *node
  less func(interface{}, interface{}) bool
  length int
}

type node struct {
  key, value interface{}
  red bool
  left, right *node
}
```

The ordered map is implemented in two custom struct types. The first struct type is the Map struct which holds the root of the left-leaning red-black tree, a less than function that is used to compare keys, and a length which holds the number of items in the map. This's fields are all exported and the less function's zero value is nil, so creating a variable will produce an invalid Map. The Map type's documentation explains this and directs users to use one of the emap package's construction functions to create valid Maps.

The second struct type is the node struct which represents a single key-value item. In addition to its key and value fields, the node struct has three additional fields needed to implement the tree. The red field of type bool is used to identify whether a node is "red" (true) or "black" (false)—this is used when portions of the tree are rotated to maintain its balance. The left and right fields of type *node hold pointers to a node's left and right subtrees (which can be nil).