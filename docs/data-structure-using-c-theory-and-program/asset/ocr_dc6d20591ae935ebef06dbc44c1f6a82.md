return(0);

# Function for Inorder traversal.

```
inorder(struct tree *ptr)
{
    If (ptr!=NULL)
    {
        inorder(ptr->l);
        printf("%d",ptr->head);
        inorder(ptr->r);
    }
    return(0);
}
```

# Function for Postorder traversal.

```
postorder(struct tree *ptr)
{
    if (ptr!=NULL)
    {
        postorder(ptr->l);
        postorder(ptr->r);
        printf("%d",ptr->head);
    }
    return(0);
}
```

# Program: write a program to Implement Binary Tree and apply Traversalnlike - Preorder, Inorder, Postorder.

```
#include<stdio.h>
#include<stdlib.h>
struct tree
{
    int head;
    struct tree *l, *r;
}
struct tree *r,*t;
int ch1,n,flag=0,in;
```