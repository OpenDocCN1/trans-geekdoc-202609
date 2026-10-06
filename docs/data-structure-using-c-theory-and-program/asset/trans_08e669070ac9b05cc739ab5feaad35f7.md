

# 算法

步骤

- 1. 开始
2. 存储第一个元素的地址
3. 设置 node = start
4. 设置 count = 1
5. 读取 item
6. 当 node ≠ NULL 时，重复步骤 7 到 11
7. 如果 item = info [node] 则
8. 写入“在位置找到元素”，count 并退出
9. 如果是结构体，则结束步骤 7
10. 设置 count = count + 1
11. 设置 node = next [node]
12. 结束步骤 6 循环
13. 写入“未找到元素”
14. 停止

程序：在单单链链表中查找节点

```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int info;
    struct node *next;
};
void create (struct node*);
void search (struct node*);
void display (struct node*);
void main ()
{
    struct node *next;
    char ch='1';
    node=(struct node*)malloc(sizeof(struct node));
    if(node==NULL)
    {
        printf("\n out of memory space");
```

```c
exit(0);
}
create(node);
while (ch!='3')
{
  printf("\n 1. 查找");
  printf("\n 2. 显示");
  printf("\n 3. 退出");
  printf("\n 输入您的选择");
  ch=getchar();
  switch(ch)
  {
    case '1':
      search(node);
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
void create (struct node * next)
{
  char ch;
  int i=1;
  printf("\n 输入第 %d 个节点的值", i);
  scanf("%d",&node->info);
  node->next=NULL;
  i=i+1;
  printf("\n 按 'E' 键退出，按 'Y' 键继续: ");
  ch=getchar (
  while (ch!='N')
```

```c
{
  node->next=(struct node*)malloc(sizeof(struct node));
  if(node->next==NULL) {
    printf("\n 内存空间不足\n\n");
    exit(0);
  }
  node=node->next;
  printf("\n 输入第 %d 个节点的值", i);
  scanf("%d", &node->info);
  node->next=NULL;
  i=i+1;
  printf("\n按 'E' 键退出，按 'Y' 键继续\n\n");
  ch=getchar();
}
}
void search(struct node *next) {
  int x, i=1;
  printf("\n 输入要查找的节点值\n");
  scanf("%d", &x);
  while(node!=NULL) {
    if(node->info==x) {
      printf("\n 找到元素 %d 位于位置:\n", x,i);
      return;
    }
    i=i+1;
  }
  printf("\n 在列表中未找到元素 %d\n", x);
}
void display(struct node *next) {
  printf("\n 列表中节点的值如下:\n");
  while(node!=NULL) {
    printf("%d", node->info);
  }
```

```c
node=node->next;
  }
}
```

# 输出

输入节点值: 10

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 20

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 30

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 40

按 ‘E’ 键退出，按 ‘Y’ 键继续: E

- 1. 查找
2. 显示
3. 退出
输入您的选择: 2

10 20 30 40

- 1. 查找
2. 显示
3. 退出
输入您的选择: 1

输入要查找的节点值: 30
找到元素 30 位于位置: 3

- 1. 查找
2. 显示
3. 退出
输入您的选择: 1

输入要查找的节点值: 15
在列表中未找到元素 15

- 1. 查找
2. 显示
3. 退出
输入您的选择: 3

# f. 对链表节点进行排序

排序是将链表按升序或降序排列。

第 3 章 链表

81

![](img/3d5da05d64722faaa72fdc4daca105f9_95_0.png)

**图** 排序前

![](img/3d5da05d64722faaa72fdc4daca105f9_95_1.png)

**图** 排序后（节点值升序排序）

# 算法

步骤

- 1. 开始
2. 存储第一个节点的地址
3. 设置 node = start
4. 当 next [node] ≠ NULL 时，重复步骤 5 到 14
5. 设置 ptr = next [node]
6. 当 ptr ≠ NULL 时，重复步骤 7 到 12
7. 如果 info [node] > info [ptr] 则
8. 设置 temp = info [node]
9. 设置 info [node] = info [ptr]
10. 设置 info [ptr] = temp
11. 如果是结构体，则结束步骤 7
12. 设置 ptr = next [ptr]
13. 结束步骤 6 循环
14. 设置 node = next [node]
15. 结束步骤 4 循环
16. 停止

**程序：** 单链表值排序

```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int info;
    struct node *next;
};
void create (struct node*);
void sort (struct node*);
void display (struct node*);
void main ()
```

```c
{
  struct node *next;
  node=(struct node*)malloc(sizeof(struct node));
  if(node==NULL)
  {
    printf("\n 内存空间不足");
    exit(0);
  }
  create(node);
  while (ch!='3')
  {
    printf("\n 1. 查找");
    printf("\n 2. 显示");
    printf("\n 3. 退出");

# 第 3 章 链表

```c
void create (struct node * next)
{
  char ch;
  int i=1;
  printf("\n 输入第 %d 个节点的值", i);
  scanf("%d",&node->info);
  node->next=NULL;
  i=i+1;
  printf("\n 按 'E' 键退出，按 'Y' 键继续: ");
  ch=getchar (
  while (ch!='N')
  {
    node->next=(struct node*)malloc(sizeof(struct node));
    if(node->next==NULL) {
      printf("\n 内存空间不足\n\n");
      exit(0);
    }
    node=node->next;
    printf("\n 输入第 %d 个节点的值", i);
    scanf("%d", &node->info);
    node->next=NULL;
    i=i+1;
    printf("\n按 'E' 键退出，按 'Y' 键继续\n\n");
    ch=getchar();
  }
}
void search(struct node *next) {
  int x, i=1;
  printf("\n 输入要查找的节点值\n");
  scanf("%d", &x);
  while(node!=NULL) {
    if(node->info==x) {
      printf("\n 找到元素 %d 位于位置:\n", x,i);
      return;
    }
    i=i+1;
  }
  printf("\n 在列表中未找到元素 %d\n", x);
}
void display(struct node *next) {
  printf("\n 列表中节点的值如下:\n");
  while(node!=NULL) {
    printf("%d", node->info);
  }
}
```

# 输出

输入节点值: 10

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 20

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 30

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 40

按 ‘E’ 键退出，按 ‘Y’ 键继续: E

- 1. 查找
2. 显示
3. 退出
输入您的选择: 2

10 20 30 40

- 1. 查找
2. 显示
3. 退出
输入您的选择: 1

输入要查找的节点值: 30
找到元素 30 位于位置: 3

- 1. 查找
2. 显示
3. 退出
输入您的选择: 1

输入要查找的节点值: 15
在列表中未找到元素 15

- 1. 查找
2. 显示
3. 退出
输入您的选择: 3

# f. 对链表节点进行排序

排序是将链表按升序或降序排列。

第 3 章 链表

81

![](img/3d5da05d64722faaa72fdc4daca105f9_95_0.png)

**图** 排序前

![](img/3d5da05d64722faaa72fdc4daca105f9_95_1.png)

**图** 排序后（节点值升序排序）

# 算法

步骤

- 1. 开始
2. 存储第一个节点的地址
3. 设置 node = start
4. 当 next [node] ≠ NULL 时，重复步骤 5 到 14
5. 设置 ptr = next [node]
6. 当 ptr ≠ NULL 时，重复步骤 7 到 12
7. 如果 info [node] > info [ptr] 则
8. 设置 temp = info [node]
9. 设置 info [node] = info [ptr]
10. 设置 info [ptr] = temp
11. 如果是结构体，则结束步骤 7
12. 设置 ptr = next [ptr]
13. 结束步骤 6 循环
14. 设置 node = next [node]
15. 结束步骤 4 循环
16. 停止

**程序：** 单链表值排序

```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int info;
    struct node *next;
};
void create (struct node*);
void sort (struct node*);
void display (struct node*);
void main ()
```

```c
{
  struct node *next;
  node=(struct node*)malloc(sizeof(struct node));
  if(node==NULL)
  {
    printf("\n 内存空间不足");
    exit(0);
  }
  create(node);
  while (ch!='3')
  {
    printf("\n 1. 查找");
    printf("\n 2. 显示");
    printf("\n 3. 退出");

# 数据结构

# 输出

输入节点值: 10

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 20

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 30

按 ‘E’ 键退出，按 ‘Y’ 键继续: Y

输入节点值: 40

按 ‘E’ 键退出，按 ‘Y’ 键继续: E

# 反转链表

# 算法

步骤

- 1. 开始
2. 存储第一个节点的地址
3. 设置 node = start
4. 当 next [node] ≠ NULL 时，重复步骤 5 到 14
5. 设置 ptr = next [node]
6. 当 ptr ≠ NULL 时，重复步骤 7 到 12
7. 如果 info [node] > info [ptr] 则
8. 设置 temp = info [node]
9. 设置 info [node] = info [ptr]
10. 设置 info [ptr] = temp
11. 如果是结构体，则结束步骤 7
12. 设置 ptr = next [ptr]
13. 结束步骤 6 循环
14. 设置 node = next [node]
15. 结束步骤 4 循环
16. 停止

**程序：** 单链表值排序

```c
#include<stdio.h>
#include<stdlib.h>
struct node {
    int info;
    struct node *next;
}head;

# 反转链表

# 数据结构

# 反

链:

# 反转链表

First node will become the last node.
.. node will become the first node.
3. Each node will to the the node.

# 算法

步骤

Each node will point to the previous node.

# of the will the the





# List

#

: 反转链表

```c
#include<stdio.h>
#include<stdlib.h>
struct node {
    int info;
    struct node *next;
}head;
void insert_data(int value) {
    struct node *var,*temp;
temp=head;
var=(struct node *)malloc(sizeof(struct node));
var->data=value;
if(head==NULL) {
        head=var;
        head->next=NULL;
    }
    else {
        while(temp->next!=NULL) {
            temp=temp->next;
        }
        var->next=NULL;
        temp->next=var;
    }
}
void reverse_list() {
  struct node *temp,*temp1,*var;
  temp=head;
  while(temp!=NULL) {
    temp1=var;
    var=temp;
    temp=temp->next;
    var->next=temp1;
  }
  head=var;
}
void display() {
  struct node *var;
  var=head;
  printf("\nlist of elements \n");
  while(var!=NULL) {
    printf("%d-> %s", var->data);
    var=var->next;
  }
  printf("NULL");
}
int main() {
  int i,value;
  char ch='y';
head=NULL;
  printf("\n 1.) Insert node");
  printf("\n 2.) display the list");
  printf("\n 3.) reverse the nodes");
  printf("\n 4.) exit");
  while(ch=='y') {
    printf("\n Enter your choice: ");
    ch=getchar();
    switch(ch) {
      case '1':
        printf("\n Enter the value: ");
        scanf("%d", &value);
        insert_data(value);
        break;
      case '2':
        display();
        break;
      case '3':
        reverse_list();
        break;
      case '4':
        break;
      default:
        printf("\n Wrong Choice");
    }
  }
}
}
```

