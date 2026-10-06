

```c
a[i+1]=a[i];
}
a[pos]=data;
printf("The Final Array is\n");
for(i=0;i<4;i++)
{
  printf("%d\t",a[i]);
}
```

# 输出

输入数字 5
3
5
输入位置2
输入数据12
最终数组是：

5 3 12 5 

# 编写一个删除一维数组中元素的程序

```c
#include<stdio.h>
void main()
{
  int a[5],i,pos,data;
  printf("Enter the number");
  for(i=0;i<4;i++)
  {
    scanf("%d",&a[i]);
  }
  printf("Enter the position");
  scanf("%d",&pos);
  for(i=pos;i<4;i++)
  {
    a[i]=a[i+1];
  }
  printf("The Final Array is\n");
  for(i=0;i<3;i++)
  {
    printf("%d\t",a[i]);
  }
}
```

# 输出

输入数字6
3
12
4

输入位置2
最终数组是：
6 3 4

# 编写一个查找单维数组中最大值和最小值的程序

```c
#include<stdio.h>
void main()
{
int a[10]
```

# 第2章 数组绪论

```c
if(a[i]<min)
{
min=a[i];
}
printf("\n The Maximum Value is:- %d", max);
printf("\n The Minimum Value is:- %d", min);
}
```

# 输出

输入数组长度

12
3
21
33
40
-10
5
8
2
45

数组元素:-

12 3 21 33 40 -10 5 8 2 45
最大值是:- 45
最小值是:- -10

## 2.3 数组操作

可以在数组上执行的各种操作有：

- 1. 遍历。
- 2. 排序。
- 3. 搜索。
- 4. 插入。
- 5. 删除。
- 6. 合并。

## 遍历

遍历是指从第一个元素开始到最后一个元素，恰好访问数组中每个元素的过程。下面是一个简单的算法。

# 算法

步骤：

- 1. i = L
2. while i ≤ U do
3. process (A[i])
4. i = i + 1
5. end while
6. stop

# 排序

该操作按照指定的顺序（升序或降序）对数组进行处理。给定的算法用于将整数数组的元素按升序存储。

# 算法

步骤：

- 1. i = U
2. while i ≥ L do
3. j = L
4. while j > i do
5. if (A[j], A[j+1]) = FALSE
6. swap (A[j], A[j+1])
7. end if
8. j = j + 1
9. end while
10. i = i - 1
11. end while
12. stop

# 搜索

该操作用于在数组中搜索元素。一个简单的算法如下。

# 算法 

步骤：

- 1. i = L, found = 0, location = 0 // found=0 意味着列表中未找到数据
2. while (i ≤ U) and (found = 0) do
3. if Compare (A[i], Key) = TRUE then
- 4. found = 1
5. location = i
6. else
7. i = i + 1
8. end if
9. end while
10. if found = 0 then
11. print "search is unsuccessful"
12. else
13. print "Search is successful"
14. end if
15. Return
16. stop

# 插入

该操作用于向数组的特定位置插入元素。一个简单的算法如下。

# 算法

步骤：

- 1. if A[U] != NULL then
2. print "array is full"
3. exit
4. else
5. i = U
6. while i > location
7. A[i] = A[i - 1]
8. i = i - 1
9. End while
10. A[location] = Key
11. End if
12. Stop

# 删除

该操作用于从数组中删除特定元素。通过覆盖其后续元素来实现删除。一个简单的算法如下。

# 算法 

步骤：

- 1. if n=0 then array is underflow and stop
2. read data as element to be deleted
3. read location at deletion will be made
4. k=LB
5. repeat step 6 while a(k) != data
6. k=k+1
7. repeat step 8 while k < UB
8. a(k)=a(k+1)
9. k=k+1
10. a(UB)=NULL
11. UB-1
12. stop

# 合并

该操作用于合并两个排序的数组并创建一个第三个数组。这是一个简单的算法。

注意：

- LBA: 数组1的下界
- UBA: 数组1的上界
- LBB: 数组2的下界
- UBB: 数组2的上界

# 算法 

步骤：

- 1. i=LBA, j=LBB, k=0
2. repeat step 3 to 4 where i ≤ UBA and j ≤ UBB
3. if A(i) < B(j)
4. c(k)=A(i)
5. i=i+1
6. else
7. c(k)=B(j)
8. j=j+1
9. k=k+1
10. repeat step 11 while i ≤ UBA
11. c(k)=A(i)
12. i=i+1
13. k=k+1
14. repeat step 15 while j ≤ UBB
15. c(k)=B(j)
16. j=j+1
17. k=k+1
18. stop

## 2.4 内存中的一维表示

![](img/3d5da05d64722aa72fd4daca105f9_41_0.png)

| 内存中的实际地址 | 1100 | 1104 | 1108 | 1102 | 1106 |
|---|---|---|---|---|
| 元素 | 15 | 7 | 44 | 9 | 20 |
| 相对于数组的下标 | 0 | 1 | 2 | 4 | 5 |

![](img/3d5da05d64722aa41_1.png)

# 一维数组的计算

设 A 为具有 n 个元素的一维数组。由于数组存储在连续的内存位置，系统不需要跟踪 A 的每个元素，只需要跟踪第一个元素，表示为：基地址 (A)。一维数组中特定元素的地址给如下：
元素 a[k]=B+W*K

其中 B=数组中每个元素的大小
K=元素的地址

Q1. 假设数组第一个元素的基地址为 5000，且一维数组的第5个元素在内存中占用 2 字节，则地址如下：

解：使用公式
元素 a[k] = B + W * K
基地址=5000
W=2
K=5
A [5] = 5000 + 2 * 5
=5000 + 10
=5010

Q2. 假设数组第一个元素的基地址为 200，且数组的每个元素在内存中占用 4 字节，则一维数组中第6个元素 a[6] 的地址为：

解：使用公式
元素 a[k] = B + W * K
基地址=200
W=4
K=6
A [6] = 200 + 4 * 6
=200 + 24
=224

## 2.5 二维数组

在内存中存储二维数组的元素时，它们被分配在连续的内存位置上。因此，必须对二维数组进行线性化以以便存储。实现线性化有两种两种替代方案：行主优先和列主优先。

二维数组的通用语法为 `<Data_type> array_name[size1][size2];`

![](img/3d5da05d64722aa72fd4daca105f9_42_0.png)

## 2.6 内存中二维（维度）数组的实现

在内存中存储二维数组元素时，它们是按连续内存位置分配的。因此，二维数组必须被线性化以实现其存储。在编程语言中实现二维数组存储的两种方式：

- 1. 行主优先实现
- 2. 列主优先实现

# 行主优先实现

行主排序按行再按列将元素分配到连续的内存位置。这种映射通过图表描述最好。行主排序在 Pascal、C 等高级编程语言中非常直观。A:array[0..3,3] 的 char，

| | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| 0 | 15 | 14 | 13 | 12 |
| 1 | 10 | 9 | 8 | 7 |
| 2 | 6 | 5 | 4 | 3 |
| 3 | 12 | 13 | 14 | 15 |

+ 1. 行主优先实现中的元素地址
元素 a[i][j]=B+W (n (i-L1)+(j-L2))

其中 B=基地址
W=每个元素的大小
n=列数（即 U2 - L2 + 1）
L1=行的下界
L2=列的下界
U2=列的上界

Q1. 定义为 A[4....6, 1....4] 的二维数组每个元素需要 4 字节存储空间。如果数组按行主优先顺序存储，则计算位置 A [5, 2] 的元素地址。基地址为 100。

解：使用公式
元素 a[i][j] = B + W (n (i- L1) + (j- L2))
B=100, W=4, i=5, j=2, L1=4, L2=1, U2=4
计算 n=U2 - L2 + 1
=4-1+1
=4
A[5,2]=100 + 4 (4 (5 - 4) + (2 - 1))
=100 + 4 (4 * 1 + 1)
=120

Q2. 计算在主内存中按行主优先存储的二维数组 Y[1....6, 1....5] 中 Y [4,3] 的地址。假设基地址为 200，且每个元素需要 4 字节存储空间。

