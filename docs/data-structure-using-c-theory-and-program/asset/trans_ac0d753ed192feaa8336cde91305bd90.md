

# 第3章 链表

```c
node->next=NULL;
i=i+1;

printf("\n Press 'E' key to exit and Press 'Y' key to continue");
ch=getchar();
}
}
void delete(struct node *next)
{
    struct node *prev;
    if(node->next==NULL)
    {
        free(node);
        start=NULL;
        return;
    }
    while(node->next!=NULL)
    {
        prev=node;
        node=node->next;
    }
    prev->next=NULL;
    free(node);
}
void display (struct node *next)
{
    if(node==NULL)
    {
        printf("\n n List is Empty");
        return;
    }
    printf("\n value of nodes in the list are as follows:\n");
    while(node!=NULL)
    {
        printf("%0d", node->info);
        node=node->next;
    }
}
```

# 输出

输入节点值: 10

按 ‘E’ 键退出并按 ‘Y’ 键继续: Y

输入节点值: 20

按 ‘E’ 键退出并按 ‘Y’ 键继续: Y

输入节点值: 30

按 ‘E’ 键退出并按 ‘Y’ 键继续: Y

输入节点值: 40

按 ‘E’ 键退出并按 ‘Y’ 键继续: E

- 1. 删除尾部
2. 显示
3. 退出

输入你的选择: 2

链表中节点的值如下:
10 20 30 40

- 1. 删除尾部
2. 显示
3. 退出

输入你的选择: 1

- 1. 尾部插入
2. 显示
3. 退出

输入你的选择: 2

链表中节点的值如下:
10 20 30

- 1. 删除尾部
2. 显示
3. 退出

输入你的选择: 3

# c. (iii) 在特定位置删除

![](img/3d5da05d64722faaa72fdc4daca105f9_80_0.png)

![](img/3d5da05d64722faaa72fdc4daca105f9_80_1.png)

# 算法

步骤

- 1. 开始
2. 存储第一个节点的地址。
3. 设置 node = start
4. 设置 temp = start
5. 如果 node = NULL 则
6. 写入 “UNDERFLOW”（上溢）并
7. 退出
8. 设置 i = 1
9. 读取 loc
10. 当 node ≠ NULL 且 i < loc 时，重复步骤 11 到 13
11. 设置 temp = node
12. 设置 node = next [node]
13. 设置 i = i+1
14. 步骤 10 循环结束
15. 如果 node = NULL 则
16. 写入 “未找到位置”
17. 退出
18. 设置 next [temp] = next [node]
19. 释放与 node 相关的空间
20. 停止

# 程序：在特定位置删除节点

```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int info;
    struct node *next;
};
struct node *start;
void delete (struct node);
void create (struct node*);
void count(struct node*);
void display (struct node*);
void main ()
```

```c
{
  char ch='1';
  struct node *next;
  node=(struct node*)malloc(sizeof(struct node));
  if(node==NULL) {
    printf("\n out of memory");
  }
  start=node;
  printf("\n 链表创建\n");
  create (node)
  while (ch=='3') {
    printf("\n 1. 特定位置删除");
    printf("\n 2. 显示");
    printf("\n 3. 退出");
    printf("\n 输入你的选择");
    ch=getchar();
    switch(ch) {
      case '1':
        delete(node);
        node=start;
        break;
      case '2':
        display(node);
        break;
      case '3':
        break;
      default:
        printf("\n 选择错误");
    }
  }
  void create (struct node *next)

```c
{
  char ch;
  int i=1;
  printf("\n 输入第d个节点的值", i);
  scanf("%d", &next->info);
  next->next=NULL;
  i=i+1;
  printf("\n 按 'E' 键退出并按 'Y' 键继续: ");
}
```

```c
return;
}
while (i<loc)
{
    prev=node;
    node=node->next;
    i=i+1;
}
if(loc==1)
    start=node->next;
else
    prev->next=node->next;
free(node);
}
int count(struct node *next)
{
    int i=0;
    while(node!=NULL)
    {
        i=1;
        node=node->next;
    }
    return i;
}
void display (struct node *next)
{
    if(node==NULL)
    {
        printf("\n 链表为空");
        return;
    }
    printf("\n 链表中节点的值如下:\n");
    while(node!=NULL)
    {
        printf("%d", node->info);
        node=node->next;
    }
}
```

# 输出

输入节点值: 10
按 'E' 键退出并按 'Y' 键继续: Y
输入节点值: 20
按 'E' 键退出并按 'Y' 键继续: Y
输入节点值: 30
按 'E' 键退出并按 'Y' 键继续: Y
输入节点值: 40
按 'E' 键退出并按 'Y' 键继续: E

- 1. 特定位置删除
2. 显示
3. 退出

输入你的选择: 2
链表中节点的值如下:
10 20 30 40

- 1. 特定位置删除
2. 显示
3. 退出

输入你的选择: 1
输入要插入节点的位置: 2

- 1. 特定位置删除
2. 显示
3. 退出

输入你的选择: 2
链表中节点的值如下:
10 30 40

- 1. 特定位置删除
2. 显示
3. 退出

输入你的选择: 3

# d. 两个链表合并为单链表

内存中有两个列表，需要将两个链表合并为一个单链表。为了获得合并后的列表，必须将第一个链表的最后一个节点连接到第二个链表的第一个节点。

# 链表_1
![](img/3d5da05d64722faaa72fdc4daca105f9_86_0.png)

# 链表_2
![](img/3d5da05d64722faaa72fdc4daca105f9_86_1.png)
合并前的图

# 链表
![](img/3d5da05d64722faaa72fdc4daca105f9_86_2.png)
合并后的图

# 算法

步骤

- 1. 设置 node_1 = list_1
2. 创建一个新节点 list
3. 如果 list = NULL 则
4. 写入 “内存不足”
5. 退出
6. 设置 info [list] = info [node_1]
7. 设置 next [list] = NULL
8. 设置 node_1 = next [node_1]
9. 设置 node = list
10. 当 node_1 ≠ NULL 时重复步骤 11 到 19
11. 创建一个新节点 curr
12. 如果 curr = NULL 则
13. 写入 “内存不足”
14. 退出
15. 设置 info [curr] = info [node_1]
16. 设置 next [curr] = NULL
17. 设置 node_1 = next [node_1]
18. 设置 next [node] = curr
19. 设置 node = curr
20. 步骤 10 循环结束
21. 设置 node_2 = list_2
22. 当 node_2 ≠ NULL 时重复步骤 23 到 29
23. 如果 curr = NULL 则
24. 写入 “内存不足”
25. 退出
26. 设置 info [curr] = info [node_2]
27. 设置 next_2 = next [node_2]
28. 设置 next [node] = curr
29. 步骤 22 循环结束
30. 停止

# 程序：合并两个为单链表

```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int info;
    struct node *next;
};
struct node *start;
void delete (struct node);
void create (struct node*);
void count(struct node*);
void display (struct node*);
void main ()
{
  char ch;
  struct node *next, *node1, *node2;
  node1=(struct node*)malloc(sizeof(struct node));
  if(node1==NULL) {
    printf("\n out of memory");
  }
  start=node1;
  printf("\n 链表创建\n");
  create (node1)
  while (ch=='3') {
    printf("\n 1. 特定位置删除");
    printf("\n 2. 显示");
    printf("\n 3. 退出");
    printf("\n 输入你的选择");
    ch=getchar();
    switch(ch) {
      case '1':
        delete(node1);
        node1=start;
        break;
      case '2':
        display(node1);
        break;
      case '3':
        break;
      default:
        printf("\n 选择错误");
    }
  }
}
void create (struct node *next)
{
  char ch;
  int i=1;
  printf("\n 输入第%d个节点的值", i);
  scanf("%d", &next->info);
  next->next=NULL;
  i=i+1;
  printf("\n 按 'E' 键退出并按 'Y' 键继续: ");
}
void merge (struct node *node1, struct node *node2)
{
    struct node *temp;
    while(node1->next!=NULL)
    {
        temp=node1;
        node1=node1->next;
    }
    temp->next=node2;
}
```

# e. 在链表中查找元素

查找意味着在给定的列表中找到一个值。假设我们有一个链表，并且想要查找一个值，30。如果该值存在链表中，它将返回位置，否则它将显示消息 “元素不在链表中”。

![](img/3d5da05d64722faaa72fdc4daca105f9_90_0.png)

搜索元素（例如 30）的图

