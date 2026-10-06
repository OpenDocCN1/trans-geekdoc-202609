

![](img/3d5da05d64722faaa72fdc4daca105f9_206_0.png)
![](img/3d5da05d64722faaa72fdc4daca105f9_206_1.png)
![](img/3d5da05d64722faaa72fdc4daca105f9_206_2.png)
![](img/3d5da05d64722faaa72fdc4daca105f9_206_3.png)

当 n = 3 时：

+   1. X→Y
2. X→T
3. Y→T
4. X→Y
5. T→X
6. T→Y
7. X→Y

![](img/3d5da05d64722faaa72fdc4daca105f9_206_4.png)

![](img/3d5da05d64722faaa72fdc4daca105f9_207_0.png)

# 找到 n 个盘从 X 移动到 Y 的步数公式为 2^n-1

| 盘的数量 (n) | 移动次数 |
| --- | --- |
| 1 | 2^1-1 = 2-1 = 1 |
| 2 | 2^2-1 = 4-1 = 3 |
| 3 | 2^3-1 = 8-1 = 7 |
| 4 | 2^4-1 = 16-1 = 15 |

# 需要记忆的重点

+   1. 栈是一种线性数据结构，元素仅在某一端进行添加和删除，这一端称为栈顶。因此，栈被称为 LIFO（后进先出）数据结构，因为最后插入的元素是最先取出的。

+   2. 在计算机内存中，栈可以使用链表或单数组来实现。

+   3. 中间表达式、前缀和后缀表示法是编写代数表达式的不同但等价的符号。

+   4. 在后缀表示法中，运算符放在操作数之后，而在前缀表示法中，运算符放在操作数之前。

+   5. 后缀表达式从左到右扫描。如果字符是操作数，则将其推入栈中。否则，如果是运算符，则从栈中弹出两个值并对这些值应用运算符。将结果推入栈中。

+   6. 多个栈意味着在足够大小的同一个数组中拥有多个栈。

# 单选题

+   1. 栈是：
(a) LIFO (b) FIFO
(c) FILO (d) LIFO

+   2. 哪个函数将元素置于栈顶？
(a) Pop() (b) Push()
(c) Peek() (d) Iempty()

# 第4章 栈

+   3. 堆叠在一起的盘代表：
(a) 栈 (b) 队列
(c) 链表 (d) 数组

+   4. 逆波兰表达式是以下的另一个名称：
(a) 中间表达式 (b) 前缀表达式
(c) 后缀表达式 (d) 代数表达式

# 判断题

+   1. Pop () 用于在栈顶添加元素。
2. 后缀运算不允许运算符优先级的规则存在。
3. 递归遵循分治法技术来解决问题。
4. 使用递归函数需要消耗更多的内存和更长的时间来执行。
5. 递归更多是一种自底向上的解决方法。
6. 间接递归函数是指它包含对另一个函数的调用，而该函数最终又调用了它。
7. peeks 操作显示栈顶值并将其从栈中删除。
8. 在栈中，最后插入的元素是第一个被取出的元素。
9. 当 top=max-1 时，发生下溢（Underflow）。
10. 在多栈的情况下永远不会发生上溢（Overflow）。

# 空题

+   1. ________ 用于将中间表达式转换为后缀表达式。
2. ________ 用于算法的非递归实现。
3. 具有 n 个元素的链表栈的存储需求为 ________。
4. 当 ________ 时发生下溢。
5. 后缀表达式的求值顺序是从 ________ 的。
6. 每当有待执行的操作时，该函数变为递归的。
7. 如果一个函数显式地调用自己，则称为 ________ 递归。

# 练习题

+   1. 你如何理解栈溢和下溢？
2. 栈如何使用链表实现？
3. 栈如何使用数组实现？

4. 在空栈上执行以下序列：PUSH ‘S’, PUSH ‘S’, PUSH ‘T’, PUSH ‘U’, POP, PUSH ‘A’, PUSH ‘L’, PUSH ‘G’, POP, PUSH ‘C’, PUSH ‘A’, PUSH ‘B’, POP, POP。显示每次操作后的栈配置型？

5. 将以下中间表达式转换为后缀表达式：

+   (a) A–B + C
(b) A * B + C / D
(c) (A - B) + C * D / E - C
(d) (A * B) + (C / D) - (D + E)
(e) ((A - B) + D / ((E + F) * G))
(f) 14 / 7 * 3 - 4 + 9 / 2

6. 将以下中间表达式转换为前缀表达式：

+   (a) A–B + C
(b) A * B + C / D
(c) (A - B) + C * D / E - C
(d) (A * B) + (C / D) - (D + E)
(e) ((A - B) + D / ((E + F) * G))
(f) 14 / 7 * 3 - 4 + 9 / 2

7. 区分迭代函数和递归函数？

8. 解释汉诺塔问题？

# 参考文献

+   1. Bruno, JL and T. Lassagne, The generation of optimal code for an attack machine, 1975.
+   2. Donald Knuth, The Art of Programming, Vol. 2, 1984.
+   3. Forsythe, A., Computer Science: A Course, John Wiley, 1986.
+   4. Harrison, M., Data Structures, Addison-Wesley, 1985.
+   5. Seth, J., The generation of optimal code for an attack machine, Journal of ACM, 1970.

# 5 队列

## 5.1 引言

队列自然地出现在问题中。队列最常见的情况是在商场、售票处等排队。第一个进入的人是第一个离开的。因此，队列也被称为先进先出（FIFO）。

## 5.2 队列的表示

队列作为线性数据结构，可以使用数组和链表表示。

### 1. 使用数组的队列

数组是存储固定数量元素的数据结构。数组的一个主要限制是它的大小是固定的。因此，如果使用数组实现队列，我们必须确定想要存储的元素的确切数量。

#### 使用数组的队列的操作

(a) 插入（队尾）
(b) 删除（队头）

# 队列插入算法

步骤：
1. 开始
2. 检查上溢条件
if rear=max-1 then
写入“OVERFLOW”并然后
停止
3. 读取数据
4. if front=0 then
5. queue[rear]=data
6. rear=rear+1
7. 停止

# 队列删除算法

步骤：
1. 开始
2. 检查下溢条件
if Front==1 then
写入"UNDERFLOW"并然后
停止
3. if rear=front then
4. queue[front]=-1
5. front=0
6. front=front+1
7. 停止

# 程序：编写一个实现队列数组的程序

```c
#include<stdio.h>
#define MAX 7
void insert(int);
int del();
int queue[MAX], rear=0, front=0;
void display();
void main()
{
int choice, token;
printf("\n1.Insert");
printf("\n2.Delete");
printf("\n3.show or display");
while(1)
{
printf("\nenter your choice for the operation: ");
scanf("%d",&choice);
switch(choice)
```