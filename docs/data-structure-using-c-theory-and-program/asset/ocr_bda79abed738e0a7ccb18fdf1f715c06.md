```
{
  if(ptr!=NULL)
  {
    inode(ptr->l);
    printf("%%d",ptr->head);
    inode(ptr->r);
  } // if close
  return(0);
} //fun closed
preorder(struct tree *ptr)
{
  if (ptr!=NULL)
  {
    printf("%%d",ptr->head);
    preorder(ptr->l);
    preorder(ptr->r);
  } // if close
  return(0);
} //fun closed
postorder(struct tree *ptr)
{
  if (ptr!=NULL)
  {
    postorder(ptr->l);
    postorder(ptr->r);
    printf("%%d",ptr->head);
  } // if close
  return(0);
} //fun closed
```

# Output

+   1. Create tree
2. Traverse In-Order
3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit
Enter choice 1