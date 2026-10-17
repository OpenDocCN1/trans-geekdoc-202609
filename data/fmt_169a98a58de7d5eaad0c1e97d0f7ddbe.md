
10-> 20-> 30-> 40-> NULL

选择操作：2

元素列表为

10-> 20-> 30-> 40-> NULL

选择操作：3

元素列表为

40-> 30-> 20-> NULL

选择操作：4

## 3.5 循环链表

循环链表是一种更复杂的链式数据结构。在循环链表中，我们可以在列表的任何位置插入元素，而在数组中，我们无法在列表的任何位置插入元素，因为它是连续内存存储的。在循环链表中，前一个元素存储下一个元素的地址，最后一个元素存储起始元素的地址。元素之间以环形的方式相互指向，形成一个环链。循环链表具有动态大小，这意味着可以在需要时分配内存。循环链表是所有节点都连接成一个圆的链表。末尾没有 `NULL`。循环链表可以是单循环链表，也可以是双向链表。

![](img/3d5da05d64722faaa72fdc4daca105f9_102_0.png)

图 循环链表

## 3.6 循环链表中的操作

循环链表上可以进行各种操作。

- (a) 创建循环链表。
- (b) 插入节点
- (c) 删除节点

### 创建循环链表

创建循环链表的方法与单链表相同。唯一需要点是，这里最后一个节点将始终指向第一个节点，而不是 `NULL`。

![](img/3d5da05d64722faaa72fdc4daca105f9_103_0.png)

#### 算法

步骤

1. 开始
2. `ptr = ptr->start`
3. `start=start->link`
4. 读取信息
5. `first=first->ptr`
6. `ch='Y'`
7. 当 `ch='Y'` 时，重复步骤 8 到 13
8. `curr=curr->link`
9. `start=start->link`
10. 读取信息
11. `ptr=ptr->curr`
12. `ptr=ptr->curr`
13. 按更多节点信息按 Y/N
14. `link=link->first`
15. 停止

```c
void create()
{
struct node *ptr, *curr;
char ch;
ptr=(struct node *) malloc(sizeof(struct node));
printf(" Input First Node Information");
scanf("%d", &ptr->info);
first=ptr;

do {
  curr=(struct node *) malloc(sizeof(struct node));
  printf("Input Second Node Information");
  scanf("%d",&curr->info);
  ptr->link=curr;

  ptr=curr;
  printf("Press <Y/N>for more Node Information");
  ch=getchar();
}
while (ch=='Y');
ptr->link=first;
}
```

### b. (i) 插入节点（在头部）

![](img/3d5da05d64722faaa72fdc4daca105f9_104_0.png)

![](img/3d5da05d64722faaa72fdc4daca105f9_104_1.png)

#### 算法

步骤

1. 开始
2. 如果 `start=NULL` 则
3. 打印“OVERFLOW”然后
4. 停止
5. `ptr=ptr->start`
6. `start=start->link`
7. 读取信息
8. `curr=curr->first`
9. 当 `curr->link!=first` 时，重复步骤 10
10. `curr->curr->link`
11. `ptr->link=first`
12. `first=ptr`
13. `curr->link=first`
14. 停止

```c
void insertatbeg()
{
    struct node *ptr;
ptr=(struct node *) malloc (sizeof(struct node));
    if(ptr==NULL)
    {
    printf("OVERFLOW\n");
    return;
    }
    printf("Input New Node Information");
    scanf("%d",&ptr->info);
    curr=first;
    while(curr->link!=NULL)
    {
        curr=curr->link;
    }
    ptr->link=first;
    first=ptr;
    }
}
```

### b. (ii) 插入节点（在尾部）

![](img/3d5da05d64722faaa72fdc4daca105f9_105_0.png)

![](img/3d5da05d64722faaa72fdc4daca105f9_105_1.png)

#### 算法

步骤

1. 开始
2. 如果 `start=NULL` 则
3. 打印“OVERFLOW”然后
4. 停止
5. `ptr->ptr->start`
6. `start=start->link`
7. 读取信息
8. `curr->curr->link`
9. 当 `curr->link!=first` 时，重复步骤 10
10. `curr->curr->link`
11. `ptr->link=first`
12. `ptr->link=first`
13. 停止

```c
void insertatend()
{
  struct node *ptr, *curr;
  ptr=(struct node *) malloc(sizeof(struct node));
  if(ptr==NULL)
  {
    printf("OVERFLOW\n");
    return;
  }
  printf("Input Node Information");
  scanf("%d", &ptr->info);
  curr=first;
  while(curr->link!=first) {
    curr=curr->link;
  }
}
```

### c. 从循环链表中删除

#### 从循环链表中删除

从单循环链表中删除。

### c. (i) 删除节点（在头部）

![](img/3d5da05d64722faaa72fdc4daca105f9_107_0.png)

删除前

![](img/3d5da05d64722faaa72fdc4daca105f9_107_1.png)

删除后

#### 算法

步骤

1. 开始
2. 如果 `start=NULL` 则
3. 打印“OVERFLOW”然后
4. 停止
5. `ptr=ptr->start`
6. `start=start->link`
7. 读取信息
8. `curr=curr->first`
9. 当 `curr->link!=first` 时，重复步骤 10
10. `curr->curr->link`
11. `ptr->link=first`
12. `first=ptr`
13. `curr->link=first`
14. 停止

```c
void deletebeg()
{
    struct node *ptr;
ptr=(struct node *) malloc (sizeof(struct node));
    if(ptr==NULL)
    {
    printf("OVERFLOW\n");
    return;
    }
    printf("Input New Node Information");
    scanf("%d",&ptr->info);
    curr=first;
    while(curr->link!=NULL)
    {
        curr=curr->link;
    }
    ptr->link=first;
    first=ptr;
    }
}
```

### (ii) 删除节点（在尾部）

#### 从循环链表中删除

从单循环链表中删除。

#### 循环链表

```c
void deleteend()
{
    printf("OVERFLOW\n");
    return;
}
```

*(注：原文此部分逻辑不完整，已根据语意尽可能翻译)*

### c. (ii) 删除节点（在尾部）

#### 循环链表

```c
void deleteatend()
{
    printf("OVERFLOW\n");
    return;
}
```

## 使用 C 语言实现的数据结构

```c
printf("\nEnter the data-");
scanf("%d",&data);
int status = find(start,data);
if(status)
{
    printf("Element Found\n");
}
else
{
    printf("Element Not Found\n");
}
if(query==5)
{
    exit(0);
}
```

### 输出

- 1. 插入
- 2. 删除
- 3. 打印
- 4. 查找
- 5. 退出

1

输入数据:-2

- 1. 插入
- 2. 删除
- 3. 打印
- 4. 查找
- 5. 退出

1

输入数据:-3

- 1. 插入
- 2. 删除

### 第3章 链表

- 3. 打印
- 4. 查找
- 5. 退出

1 输入数据:-4

- 1. 插入
- 2. 删除
- 3. 打印
- 4. 查找
- 5. 退出

1 输入数据:-5

- 1. 插入
- 2. 删除
- 3. 打印
- 4. 查找
- 5. 退出

3 列表为 2-> 3-> 4-> 5->

- 1. 插入
- 2. 删除
- 3. 打印
- 4. 查找
- 5. 退出

2 输入数据:-4

- 1. 插入
- 2. 删除
- 3. 打印
- 4. 查找
- 5. 退出

3 列表为 2-> 3-> 5->

## 3.7 双向链表

在单向链表中，人们可以从第一个节点沿从左到右的一个向移动到任何节点。这就是为什么单向链表也被称为单向链表。相反，双向链表是一种双向链表，因为人们可以在两个方向（从左到右或从右到左）移动。双向链表是数据元素节点的线性集合，每个节点被分为三个部分：

- (a) 一个指针字段 `prev`，包含链表中前一个节点的位置。
- (b) 一个信息字段 `info`，包含数据。
- (c) 一个指针字段 `next`，包含链表中下一个节点的位置。

| 前一个节点 | 信息 | 下一个节点 |
| :--- | :--- | :--- |

图 双向链表

第一个节点的指针 `prev` 和最后一个节点的 `next` 包含值 `NULL`，即它们不存储任何其他节点的地址。这分别表示链表的开始和结束。双向链表优于单向链表的优势是可以沿两个方向进行遍历。这使其成为数据库和文字处理器等应用的理想数据结构，因为这些应用需要在双方向上移动。

## 3.8 双向链表操作

双向链表可以进行各种操作。

- 1. 遍历双向链表。
- 2. 插入节点
    - (a) 在头部插入
    - (b) 在末尾插入
    - (c) 在特定位置插入
- 3. 删除节点
    - (a) 在头部删除
    - (b) 在末尾删除
    - (c) 在特定位置删除

## 1. 遍历双向链表

我们希望遍历列表以恰好处理每个节点一次。我们的目标是从第一个节点开始遍历到列表末尾。考虑一个指针变量 `curr`，它指向当前正在处理的节点，`[curr]` 指向下一个节点。

![](img/3d5da05d64722faaa72fdc4daca105f9_115_0.png)

图 遍历双向链表

#### 算法

步骤

- 1. 开始
- 2. 保存第一个节点的地址
- 3. 设置 `node = start` // 初始化指针变量 `node`
- 4. 当 `node != NULL` 时重复步骤 5 和 6
- 5. 处理 `info [node]` // 对 `info [node]` 应用处理
- 6. 设置 `node = next [node]` // 将指针移动到下一个节点
- 7. 步骤 4 循环结束
- 8. 停止

## 程序：创建双向链表

```c
#include<stdio.h>
#include<stdlib.h>
struct dllnode
{
    int info;
    struct dllnode *prev;
    struct dllnode *next;
};
void create(struct dllnode *);
void display(struct dllnode *);
void main()
{
    struct dllnode*node;
    node=(struct dllnode *)malloc(sizeof(struct dllnode));
    if(node==NULL)
    {
      printf("\n out of memory");
      exit(0);
    }
    create(node);
    display(node);
}
void create (struct dllnode *node) {
  struct dllnode *curr;
  char ch;
  int i=1;
  printf("\nEnter the value of %d node:", i);
  scanf("%d", &node->info);
  node->prev=NULL;
  node->next=NULL;
  i=1;
  printf("\n Press 'E' key to exit and 'Y' to to continue
  ch=getchar();
  while(ch!='N') {
    curr=(struct dllnode *)malloc(sizeof(struct dllnode));
    if(curr==NULL) {
      printf("\n Out of memory");
      exit(0);
    }
    curr->next=node;
    node->prev=curr;
    printf("\nEnter the value of %d node:", i);
    scanf("%d", &curr->info);
    curr->prev=NULL;
    i=1;
    printf("\n Press 'E' key to exit and 'Y' to continue:");
    ch=getchar();
  }
}
void display(struct dllnode *node)
{
  struct dllnode *temp;
  printf("\nThe list is:");
  while(node!=NULL) {
    printf("%d-> ", node->info);
    node=node->next;
  }
  printf("NULL\n");
}
```

```c
printf("%d", node->info);
node=node->prev;
}
```

### 输出

输入节点值: 10

按 'E' 键退出，按 'Y' 键继续: Y

输入节点值: 20

按 'E' 键退出，按 'Y' 键继续: Y

输入节点值: 30

按 'E' 键退出，按 'Y' 键继续: Y

输入节点值: 40

按 'E' 键退出，按 'Y' 键继续: Y

按 'E' 键退出，按 'Y' 键继续: E

- 1. 在头部插入
- 2. 显示
- 3. 退出

输入您的选择: 2

10 20 30 40

链表中节点值的正向方向:

10 20 30 40

链表中节点值的反向方向:

40 30 20 10

- 1. 在头部插入
- 2. 显示
- 3. 退出

### 输入您的选择: 1

50

链表中节点值的正向方向:

50 10 20 30 40

链表中节点值的反向方向:

40 30 20 10 50

输入您的选择: 3

- 1. 在头部插入
- 2. 显示
- 3. 退出

### b. 在尾部插入

![](img/3d5da05d64722faaa72fdc4daca105f9_123_0.png)

插入前的图

![](img/3d5da05d64722faaa72fdc4daca105f9_123_1.png)

插入后的图 (x = 50)

#### 算法

### 步骤

1. 开始
2. 保存第一个节点的地址
3. 创建一个名为 temp/node 的节点
4. 如果 node = NULL 则
5. 写入“内存空间不足”并
6. 退出
7. 设置 info [node] = x //将新数据拷贝到新节点
8. 设置 next [node] = NULL
9. 设置 curr = start
10. 当 curr ≠ NULL 时重复步骤 11 和 12
11. 设置 prev = curr
12. 设置 curr = next [curr]
13. 步骤 10 循环结束
14. 设置 next [prev] = node
15. 设置 prev [node] = prev
16. 停止

程序：在双链表的尾部插入节点
