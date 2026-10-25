```
fn main() {
    let list = Cons(1, Box::new(Cons(2, Box::new(Cons(3, Box::new(Nil))))));
    println!("Created a simple linked list!");
}
```

+   - enum List: Defines a recursive data structure for the linked list.
+   - Box<List>: Allocates memory on the heap, allowing Rust to manage the recursive nature of the list.

# Binary Trees

Binary trees are essential for many algorithms and data structures, such as binary search trees and heaps. They provide fast lookup, insertion, and deletion operations.

# Implementing a Simple Binary Tree:

```
'''rust enum BinaryTree { Node(i32, Box, Box), Empty, }
use BinaryTree::::{Node, Empty};
fn main() {
    let tree = Node(10, Box::new(Node(5, Box::new(Empty), Box::new(Empty))),
    Box::new(Node(15, Box::new(Empty), Box::new(Empty))));
    println!("Created a simple binary tree!");
}
'''
```

+   - enum BinaryTree: Defines a recursive structure for the binary tree.
+   - Box<BinaryTree>: Uses heap allocation to manage the recursive structure.