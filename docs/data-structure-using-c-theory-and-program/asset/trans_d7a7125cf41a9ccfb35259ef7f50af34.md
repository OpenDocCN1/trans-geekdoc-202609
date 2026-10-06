

输入元素 4

+ 1. 创建树
2. 中序遍历
3. 前序遍历
4. 后序遍历
5. 退出

输入选择 1

+ 1. 左元素
2. 右元素
3. 退出

输入选择 1

输入元素 2

+ 1. 创建树
2. 中序遍历
3. 前序遍历
4. 后序遍历
5. 退出

输入选择 1

+ 1. 左元素
2. 右元素
3. 退出

输入选择 2

输入元素 2

+ 1. 创建树
2. 中序遍历
3. 前序遍历
4. 后序遍历
5. 退出

输入选择 1

+ 1. 左元素
2. 右元素
3. 退出

输入选择 12
选择错误

+ 1. 创建树
2. 中序遍历

# 第 6 章 树

+ 3. 前序遍历
4. 后序遍历
5. 退出

输入选择 1
1. 左元素
2. 右元素
3. 退出

输入选择 2
1. 左元素
2. 右元素
3. 退出

输入元素 4
1. 创建树
2. 中序遍历
3. 前序遍历
4. 后序遍历
5. 退出

输入选择 2
左、根、右 2424
1. 创建树
2. 中序遍历
3. 前序遍历
4. 后序遍历
5. 退出

输入选择 3
根、左、右 4224
1. 创建树
2. 中序遍历
3. 前序遍历
4. 后序遍历
5. 退出

输入选择 4
左、右、根 2424
1. 创建树
2. 中序遍历

+ 3. 前序遍历
4. 后序遍历
5. 退出

输入选择 5

# 遍历的非递归函数

非递归的树遍历程序将通过使用栈来实现。

# 1. 使用栈进行前序遍历

非递归地以前序遍历树的步骤如下：
步骤：

+ (i) 初始指针 (ptr) 包含根节点的地址。
(ii) 将根节点的地址 PUSH 到栈中。
(iii) 从栈中 POP 一个地址。
(iv) 如果 POP 的地址不为 NULL
(a) 遍历该节点
(v) 将节点的右子节点 PUSH 到栈中
(vi) 将节点的左子节点 PUSH 到栈中
(vii) 重复上述步骤，直到栈为空。

# 前序遍历的非递归函数如下为：

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

# 示例：考虑一个二叉树。

![](img/3d5da05d64722faaa72fdc4daca105f9_257_0.png)

初始设置 ptr = A，树的根节点。将其 PUSH 并从栈中 POP 出。由于 ptr != NULL

**遍历节点 A**，并将它的右子节点 C 和左子节点 B PUSH 到栈中。现在从栈中 POP 顶元素 B。

| 栈: |
| :--- |
| B |
| C |

从栈中 POP 顶元素 B。B != NULL

**遍历节点 B**，并将它的右子节点（无右节点）和左子节点 D PUSH 到栈中。

| 栈: |
| :--- |
| D |
| C |

从栈中 POP 顶元素 D。D != NULL

**遍历节点 D**，并将它的右子节点 H 和左子节点 G PUSH 到栈中。

| 栈: |
| :--- |
| H |
| C |

从栈中 POP 顶元素 G。G != NULL

**遍历节点 G**，并将它的右子节点和左子节点（无左右节点）

| 栈: |
| :--- |
| H |
| C |

从栈中 POP 顶元素 H。H != NULL

# 遍历节点 H 并将其右子节点 I PUSH 到栈中，以及左子节点（无左子节点）

| I |
| :--- |
| C |

从栈中 POP 顶元素 I。I != NULL
遍历节点 I 并将其右子节点和左子节点（无左右节点）

| C |
| :--- |

栈:
从栈中 POP 顶元素 C。C != NULL
遍历节点 C 并将它的子节点 F 和左子节点 E PUSH 到栈中。

| E |
| :--- |
| F |

栈:
从栈中 POP 顶元素 E。

| F |
| :--- |

遍历节点 E 并将其右子节点和左子节点（无子节点）
从栈中 POP 顶元素 F
遍历节点 F 并将其右子节点和左子节点（无子节点）
现在，栈中元素，栈为空。
最终的前序遍历为：A B D G H I C F

# 2. 使用栈进行中序遍历

+ 非递归地以中序遍历树的步骤如下：
步骤：
(i) 当栈不为空或指针 (ptr) 不为 NULL 时重复步骤
(ii) 如果 ptr != NULL
(a) 将 ptr PUSH 到栈中
(b) ptr=left
(iii) 如果 ptr = NULL
(a) 从栈中 POP 元素
(b) 遍历节点
(c) ptr=right

# 第 6 章 树

# 中序遍历的非递归函数：

```
nonrec_inorder(struct node *ptr)
{
    while(top!=-1 || ptr!=NULL)
    {
        if(ptr!=NULL)
        {
            stack[++top]=ptr;
            ptr=left;
        }
        else
        {
            ptr=stack[top--];
            printf("%d", ptr->info);
            ptr=right;
        }
    }
}
```

示例：考虑一个二叉树。

![](img/3d5da05d64722faaa72fdc4daca105f9_259_0.png)初始 ptr=根节点
现在将 A PUSH 到栈。
现在节点 (A) 的左侧元素为 B。
将 B PUSH 到栈，指针移动到 (B) 的左侧，存储在左侧的元素是 D。
将 D PUSH 到栈，指针移动到 (D) 的左侧，存储在该处的元素是 G。
将 G PUSH 到栈，指针移动到 (G) 的左侧，G 没有元素，因此 G 为 NULL。
在这些操作后；栈的形式如下：

| G |
| :--- |
| D |
| B |
| A |

从栈中 POP 顶元素 G，即：元素 G。
**遍历节点 G** 并移动到 ptr=right (G)，即：ptr=NULL。
再次从栈中 POP 顶元素，是 D，现在指针指向 ptr=right (D)，即：ptr=H。
**遍历节点 D** 将 H PUSH 到栈，且 ptr(H)=NULL。

| H |
| :--- |
| B |
| A |

栈:
从栈中 POP 顶元素 H
**遍历节点 H** 并 ptr=right (H)=I
将 I PUSH 到栈，且 ptr(I)=NULL。

| I |
| :--- |
| B |
| A |

栈:
从栈中 POP 顶元素 I
**遍历节点 I** 并 ptr=right (I) = NULL
再次从栈中 POP 元素 B

**遍历节点 B** 并 ptr=right (B)=NULL

| A |
| :--- |

从栈中 POP 顶元素 A
**遍历节点 A** 并 ptr=right(A)=C
ptr ≠ NULL，所以将节点 C PUSH 到栈
现在 ptr=left(C)=E
ptr ≠ NULL，所以将节点 E PUSH 到栈，且 ptr(E)=NULL

| E |
| :--- |
| C |

从栈中 POP 顶元素 E
**遍历节点 E**，再次从栈中 POP 元素 C
**遍历节点 C** 并 ptr=right(C)=F
将节点 F PUSH 到栈，且 ptr(F)=NULL

| F |
| :--- |

从栈中 POP 顶元素 F
**遍历节点 F**，ptr=right(F)=NULL。
栈为空
**因此，最终的中序遍历为：** G D I B A E C F

# 3. 使用栈进行后序遍历

非递归地以后序遍历树的步骤如下：
步骤：

(i) 初始指针 ptr 有根节点的地址
(ii) 当 ptr!=NULL 时重复步骤
(iii) top=top+1
(iv) stack[top]=ptr
(v) 如果right(ptr)!=NULL
(vi) {
(vii) top=top+1
(viii) stack[top]=right(ptr)
(ix) }
(x) ptr=left(ptr)
(xi) 从栈中 POP
(xii) 当 (ptr > 0) 时
(xiii) {
(xiv) 遍历 ptr
(xv) ptr=stack[top]
(xvi) top=top-1
(xvii) }
(xviii) 如果 ptr < 0 则
(xix) {
(xx) ptr=right(ptr)
(xxi) }
(xxii) 停止

# 后序遍历的非递归函数为：

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

if(ptr<0)
}
ptr=ptr->right;
}
}
}
```

