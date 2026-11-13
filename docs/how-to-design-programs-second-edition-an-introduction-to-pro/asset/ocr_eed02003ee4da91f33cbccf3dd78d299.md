+   • NONE is always a BST.

+   • (make-node ssn0 name0 L R) is a BST if
+     - L is a BST,
+     - R is a BST,
+     - all ssn fields in L are smaller than ssn0,
+     - all ssn fields in R are larger than ssn0.

In other words, to check whether a BT also belongs to BST, we must inspect all numbers in all subtrees and ensure that they are smaller or larger than some given number. This places an additional burden on the construction of data, but, as the following exercises show, it is well worth it.

**Exercise 324.** Design the function `inorder`. It consumes a binary tree and produces the sequence of all the `ssn` numbers in the tree as they show up from left to right when looking at a tree drawing.

**Hint** Use append, which concatenates lists like thus:

```
```
(append (list 1 2 3) (list 4) (list 5 6 7))
==
(list 1 2 3 4 5 6 7)
```
```

What does `inorder` produce for a binary search tree?

Looking for a node with a given ssn in a BST may exploit the BST invariant. To find out whether a BT contains a node with a specific ssn, a function may have to look at every node of the tree. In contrast, to find out whether a binary search tree contains the same ssn, a function may eliminate one of two subtrees for every node it inspects.

Let’s illustrate the idea with this sample BST:

```
```
(make-node 66 'a L R)
```
```

If we are looking for 66, we have found the node we are looking for. Now, if we are looking for a smaller number, say 63, we can focus the search on `L` because **all** nodes with `ssn` fields smaller than 66 are in `L`. Similarly, if we were to look for 99, we would ignore `L` and focus on `R` because **all** nodes with `ssn`s larger than 66 are in `R`.

**Exercise 325.** Design `search-bst`. The function consumes a number `n` and a