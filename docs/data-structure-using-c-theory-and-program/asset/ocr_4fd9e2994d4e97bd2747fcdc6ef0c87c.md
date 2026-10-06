# Chapter 6 Trees

+   1. Node holds the address of the root node of the tree.
2. Preorder (node)
3. if node ≠ NULL
4. process (node)
5. preorder ( left node)
6. preorder (right node)
7. stop

+   2. In-order Traversal.
Steps:
A binary tree is in memory.
1. node hold the address of the root node of the tree.
2. inorder (node)
3. if node ≠ NULL
4. inorder (left node)
5. process (node)
6. inorder (right node)
7. stop

+   3. Post-order Traversal.
Steps:
A binary tree is in memory.
1. node hold the address of the root node of the tree.
2. postorder (node)
3. if node ≠ NULL
4. postorder (left node)
5. postorder (right node)
6. process (node)
7. stop

Function for Pre-order traversal.

```
preorder(struct tree *ptr)
{
  if (ptr!=NULL)
    {
      printf("%d",ptr->head);
      preorder(ptr->l);
      preorder(ptr->r);
    }
}
```