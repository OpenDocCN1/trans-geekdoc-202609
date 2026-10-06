
Enter the element 4

+ 1. Create tree
2. Traverse In-Order
3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 1

+ 1. Left Element
2. Right Element
3. Exit

Enter choice 1

Enter the element 2

+ 1. Create tree
2. Traverse In-Order
3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 1

+ 1. Left Element
2. Right Element
3. Exit

Enter choice 2

Enter the element 2

+ 1. Create tree
2. Traverse In-Order
3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 1

+ 1. Left Element
2. Right Element
3. Exit

Enter choice 12
Choice is wrong

+ 1. Create tree
2. Traverse In-Order

# Chapter 6 Trees

+ 3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 1
1. Left Element
2. Right Element
3. Exit

Enter choice 2
1. Left Element
2. Right Element
3. Exit

Enter the element 4
1. Create tree
2. Traverse In-Order
3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 2
Left, Root, Right 2424
1. Create tree
2. Traverse In-Order
3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 3
Root, Left, Right 4224
1. Create tree
2. Traverse In-Order
3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 4
Left, Right, Root 2424
1. Create tree
2. Traverse In-Order

+ 3. Traverse Pre-Order
4. Traverse Post-Order
5. Exit

Enter choice 5

# Non-Recursive Function for Traversal

Non-recursive procedures for tree traversal will be implemented by using stack.

# 1. Pre order Traversal using stack

The procedure for traversing a tree in pre-order non-recursively is as:
Steps:

+ (i) Initially pointer (ptr) contains the address of root.
(ii) PUSH the address of root node on the stack.
(iii) POP an address from the stack.
(iv) If the POP address is not NULL
(a) Traverse the node
(v) PUSH right child of node on stack
(vi) PUSH left child of node on stack
(vii) Repeat steps until the stack is empty.

# Non-recursive function for preorder traversal is:

```
nonrec_preorder(struct node *ptr)
{
  stack[++top]=ptr;
  while(top!=-1)
  {
    ptr=stack[top--]
    if(ptr!=NULL)
      {
        printf("%d", ptr->info);
        stack[++top]=ptr->right;
        stack[++top]=ptr->left;
      }
  }
}
```

# Example: Consider a binary tree.

![](img/3d5da05d64722faaa72fdc4daca105f9_257_0.png)

Initially set ptr = A, the root of tree. PUSH it and POP it from the stack. Since ptr != NULL

**Traverse the node A**, and PUSH its right child C and left child B node on the stack. Now POP the top element B from the stack.

| Stack: |
| :--- |
| B |
| C |

POP the top element B from the stack. B != NULL

**Traverse the node B**, and PUSH its right child (no right child) and left child D on the stack.

| Stack: |
| :--- |
| D |
| C |

POP the top element D from the stack. D != NULL

**Traverse the node D**, and PUSH its right child H and left child G on the stack.

| Stack: |
| :--- |
| H |
| C |

POP the top element G from the stack. G != NULL

**Traverse the node G**, and PUSH its right child and left child (no right and left child)

| Stack: |
| :--- |
| H |
| C |

POP the top element H from the stack. H != NULL

# Traverse the node H and PUSH its right child I on the stack and its left child (no left child)

| I |
| :--- |
| C |

POP the top element I from the stack. I != NULL
Traverse the node I and PUSH its right child and left child (no right and left child)

| C |
| :--- |

Stack:
POP the top element C from the stack. C != NULL
Traverse the node C and PUSH its child F and left child E on the stack.

| E |
| :--- |
| F |

Stack:
POP the top element E from the stack.

| F |
| :--- |

Traverse the node E and PUSH its right child and left child (no child)
POP the top element from the stack F
Traverse the node F and PUSH its right child and left child (no child)
Now, element in stack, stack is empty.
The Final Pre-order traversal is: A B D G H I C F

# 2. Inorder Traversal using stack

+ The procedure for traversing a tree in in-order non-recursively is as:
Steps:
(i) repeat step while stack is not empty or pointer (ptr) ≠ NULL
(ii) if ptr ≠ NULL
(a) PUSH ptr on the stack
(b) ptr=left (ptr)
(iii) If ptr = NULL
(a) POP the element from the stack
(b) traverse the node
(c) ptr=right (ptr)

# Chapter 6 Trees

# Non-recursive function for in-order:

```
nonrec_inorder(struct node *ptr)
{
    while(top!=-1 || ptr!=NULL)
    {
        if(ptr!=NULL)
        {
            stack[++top]=ptr;
            ptr=ptr->left;
        }
        else
        {
            ptr=stack[top--];
            printf("%d", ptr->info);
            ptr=ptr->right;
        }
    }
}
```

Example: Consider a Binary Tree.

![](img/3d5da05d64722faaa72fdc4daca105f9_259_0.png)

Initially ptr=root node
Now PUSH A on stack.
Now ptr=left of node (A) makes element B.
PUSH B on stack and ptr moves to left (B) the element stored at left of B is D
PUSH D on stack and ptr moves to left (D) the element stored at this location is G
PUSH G on the stack and ptr moves to left (G), G't have any element hence G is NULL.

After these operations of push; stack would be in the following form:

| G |
| :--- |
| D |
| B |
| A |

POP the top element from the stack i.e.; the element G.
**Traverse the node G** and ptr=right (G), i.e.; ptr=NULL. Again POP the top element from the stack that is D now pointer points to ptr=right (D) i.e.; ptr=H. **Traverse the node D** PUSH H on stack, and ptr=left(H)=NULL.

| H |
| :--- |
| B |
| A |

Stack:
POP the top element from the stack H
**Traverse the node H** and ptr=right (H)=I
PUSH I on the stack and ptr=left (I)=NULL.

| I |
| :--- |
| B |
| A |

Stack:
POP the top element from the stack I
**Traverse the node I** and ptr=right (I) = NULL
Again POP the element from the stack B

# Traverse the node B and ptr=right (B)=NULL

| A |
| :--- |

POP the top element from the stack A
**Traverse the node A** and ptr=right(A)=C
Ptr ≠ NULL, so PUSH the node C on the stack
Now ptr=left(C)=E
Ptr ≠ NULL, so PUSH the node E on the stack and ptr=left(E)=NULL

| E |
| :--- |
| C |

POP the top element from the stack
**Traverse the node E**, again POP the element C from the stack
**Traverse the node C** and ptr=right(C)=F
PUSH the node F on the stack and ptr=left(F)=NULL

| F |
| :--- |

POP the top element from the stack
**Traverse the node F**, ptr=right(F)=NULL.
Stack is empty
**Thus, the final in-order traversal is: G D H I B A E C F

# 3. Postorder traversal using stack

The procedure for traversing a tree in post-order non-recursively is as follows:
Steps:

(i) initially pointer ptr has the address of root
(ii) repeat step while ptr!=NULL
(iii) top=top+1
(iv) stack[top]=ptr
(v) if(right(ptr)!=NULL
(vi) {
(vii) top=top+1
(viii) stack[top]=right(ptr)
(ix) }
(x) ptr=left(ptr)
(xi) POP from the stack
(xii) while (ptr > 0)
(xiii) {
(xiv) traverse ptr
(xv) ptr=stack[top]
(xvi) top=top-1
(xvii) }
(xviii) if ptr < 0 then
(xix) {
(xx) ptr=right(ptr)
(xxi) }
(xxii) stop

# Non-recursive function for post-order traversal is:

```
nonrec_postorder(struct node *ptr)
{
struct node *stack[30];
int top=-1;
int visited,i, visit[10];
do
{
while(ptr!=NULL)
{
printf("%d", ptr->info);
stack[++top]=ptr;
ptr=ptr->left;
}
if(top!=-1)
{
nptr=stack[top--];
visited=0;
for(i=0;i<top;i++)
if(visit[i]==nptr)
{
printf("%d", nptr->info);
stack[++top]=nptr;
ptr=nptr->right;
}
if(ptr!=NULL)
{
visit[top]=nptr;
ptr=ptr->right;
}
else
{
ptr=stack[top--];
}

if(ptr<
)
}
ptr=ptr->right;
}
}
}
```

# 6. CREATION OF BINARY TREE WITH THE HELP OF TRAVERSAL

There are two ways of creating binary tree:

- 1. Non-recursive function for preorder traversal
- 2. Non-recursive function for inorder traversal
- 3. Postorder traversal stack

Non-recursive procedures for tree traversal will be implemented by using stack.
