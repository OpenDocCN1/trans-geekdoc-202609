
| 1 | 2 | 5 | 4 | 3 | 6 |

# 第 8 章 搜索与排序

(c) 比较第 3 个和第 4 个元素，5>4，交换。

| 1 | 2 | 4 | 5 | 3 | 6 |

现在元素如下：

| 1 | 2 | 4 | 5 | 3 | 6 |

(d) 比较第 4 个和第 5 个元素，5>3，交换。

现在元素如下：

| 1 | 2 | 4 | 3 | 5 | 6 |

第二轮结束后，元素如下：

| 1 | 2 | 4 | 3 | 5 | 6 |

第三轮：

(a) 比较第 1 个和第 2 个元素，1<2，不交换。

(b) 比较第 2 个和第 3 个元素，2<4，不交换。

(c) 比较第 3 个和第 4 个元素，4>3，交换。

| 1 | 2 | 4 | 3 | 5 | 6 |

现在元素如下：

| 1 | 2 | 3 | 4 | 5 | 6 |

所以，最终排序后的元素为

| 1 | 2 | 3 | 4 | 5 | 6 |

## 程序：编写一个程序使用数组实现冒泡排序

```c
#include <stdio.h>
int main(){
{
    int array[100], n, c, d, swap;
    printf("Enter number of elements\n");
    scanf("%d", &n);
    printf("Enter %d integers\n", n);
    for (c = 0; c < n; c++)
        scanf("%d", &array[c]);
    for (c = 0; c < (n - 1); c++)
    {
        for (d = 0; d < n - c - 1; d++)
        {
          if (array[d] > array[d+1]) {
            swap = array[d];
            array[d] = array[d+1];
            array[d+1] = swap;
          }
        }
    }
    printf("Sorted list in ascending order:\n");
    for (c = 0; c < n; c++) {
      printf("%d\t", array[c]);
    }
    return 0;
}
```

### 输出

Enter number of elements

8

Enter 8 integers

44

55

33

88

77

22

11

66

Sorted list in ascending order:

11 22 33 44 55 66 77 88

# 8.7 插入排序

这是一种简单的排序算法，通过移动元素一位对数组进行排序。以下是插入排序的一些重要特性。

- 1. 它具有最简单的实现方式之一。
- 2. 它对于较小的数据集有效，但对于较大的列表效率非常低。
- 3. 插入排序是自适应的，这意味着如果给出一个部分排序的列表，它会减少总步数，从而提高效率。

# 第 8 章 搜索与排序

- 4. 它比选择排序和冒泡排序算法更好。
- 5. 它的空间复杂度类似于冒泡排序，插入排序也需要单个额外的内存空间。
- 6. 它是**稳定**的，因为它不会改变相等元素的相对顺序。

### 算法

插入排序 (A)

1. 开始
2. 从 j=2 到长度 [A]
3. 执行 key = A[j]
4. i = j-1
5. 当 i > 0 且 A[i] > key
6. 执行 A[i+1]=A[i]
7. i = i+1
8. A[i+1]= key

**步骤 1**：由于有一个元素，array [0] 已经排序。

**步骤 2**：将 array [1] 插入到 array [0] 之前或之后，array [0], array [1] 已排序。

**步骤 3**：将 array [2] 插入到 array [0] 之前或 array [0] 和 array [1] 之间或 array [1] 之后，array [0], array [1], array [2] 已排序。

**步骤 4**：将 array [3] 插入到其正确位置，array [0], array [1], array [2], array [3] 已排序以此类推……最后，array [n-1] 被插入到其正确位置，array [0], array [1], array [2]... array [n-1] 已排序。

**示例**：让我们取出元素并应用插入排序。

| 30 | 20 | 35 | 14 | 25 | 32 |

解决方案：

**步骤 1**：20<30，交换元素，我们得到

| 20 | 30 | 35 | 14 | 25 | 32 |

**步骤 2**：30<35，不需要交换元素

| 20 | 30 | 35 | 14 | 25 | 32 |

**步骤 3**：14 小于 35，所以将 14 插入到 20 之前，我们得到

| 14 | 20 | 30 | 35 | 25 | 32 |

**步骤 4**：90>35，不需要交换元素

| 14 | 20 | 30 | 35 | 25 | 32 |

**步骤 5**：25 小于 90，所以将 25 插入到 30 之前

| 14 | 20 | 25 | 30 | 35 | 32 |

**步骤 6**：32 小于 90，因此将 32 插入到 35 之前，我们得到

| 14 | 20 | 25 | 30 | 32 | 35 |

因此数组已排序。

**程序**：编写一个程序使用数组实现插入排序

```c
#include <stdio.h>
int main() {
    int n, array[100], c, d, t;
    printf("Enter number of elements\n");
    scanf("%d", &n);
    printf("Enter %d integers\t", n);
    for (c = 0; c < n; c++) {
        scanf("%d", &array[c]);
    }
    for (c = 1; c <= n - 1; c++) {
        d = c;
        t = array[d];
        while (d > 0 && array[d-1] > t) {
            array[d] = array[d-1];
            d--;
        }
        array[d] = t;
    }
    printf("Sorted list in ascending order:\n");
    for (c = 0; c < n; c++) {
        printf("%d\t", array[c]);
    }
    return 0;
}
```

### 输出

Enter number of elements

7

Enter 7 integers

30 20 35 14 90 25 32

Sorted list in ascending order:

14 20 25 30 32 35 90

# 8.8 选择排序

选择排序的思想是：我们重复在数组中找到下一个最大（或最小）元素并将其移动到最终位置。假设我们希望按升序排列数组，即最小元素在数组开头，最大元素在末尾。我们从选择最大元素并移动到最高索引开始。我们可以通过交换最高索引元素和最大元素来实现。我们将数组的有效大小缩小一个，并在较小的子数组上重复该过程。

让我们使用元素数组。首先，你从 array[0]... array[n-1] 中搜索最小元素的位置。然后你将该最小元素与 array[0] 交换。现在你从 array[1]... array[n-1] 中搜索第二个最小元素的位置，然后将该元素与 array[1] 交换，以此类推……

### 算法

选择排序 (A)

1. 开始
2. n=length[A]
3. 从 j=1 到 n-1
4. smallest=j
5. 从 i=j+1 到 n
6. 如果 A[i] < A[smallest]
7. 则 smallest=i
8. 交换 (A[j], A[smallest])

### 步骤

1. 从 array [0]... array[n-1] 中搜索最小元素
2. 将 array [0] 与最小元素交换。
3. 结果：array [0] 已排序。
4. 再次从 array [1]... array[n-1] 第二个最小元素
5. 将 array [1] 与第二个最小元素交换。
6. 结果：array [0], array [1] 已排序。
7. 重复这些步骤直到我们得到有序的数组。

### 选择排序如何工作

| 原始数组 | 第一轮 | 第二轮 | 第三轮 | 第四轮 | 第五轮 |
| --- | --- | --- | --- | --- | --- |
| 3 | 1 | 1 | 1 | 1 | 1 |
| 6 | 6 | 3 | 3 | 3 | 3 |
| (1) | (3) | 6 | 4 | 4 | 4 |
| 8 | 8 | 8 | 8 | 5 | 5 |
| 4 | 4 | 4 | 6 | 6 | 6 |
| 5 | 5 | 5 | 5 | 8 | 8 |

在第一轮中，找到的最小元素是 1，所以它被放在第一个位置，然后留下第一个元素，在剩余元素中搜索最小元素，3 是最小的，所以它被放在第二个位置。然后我们留下 1 和 3，在剩余元素中搜索最小元素并将其放在第三个位置，继续这样做，直到数组排序。

```c
for ( d = c + 1; d < n; d++)
{
    if ( array[position] > array[d])
        position = d;
}
if ( position != c )
{
    swap = array[c];
    array[c] = array[position];
    array[position] = swap;
}
```

```c
printf("Sorted list in ascending order:\n");
for ( c = 0; c < n; c++ )
printf("%d\t", array[c]);
return 0;
```

### 输出

输入元素个数

6

输入5个整数

3 6 1 8 4 5

升序排列的列表：

1 3 4 5 6 8

# 8.9 合并排序 (MERGE SORT)

合并排序是一种使用了分治法思想的排序算法。MERGE (A, p, r) 过程对子数组 A[p...r] 中的元素进行排序。如果 p ≤ r，则子数组最多有一个元素，因此已经是排序的。否则，划分步骤只需计算一个索引 q，将 A[p...r] 划分为两个子数组：A[p...q] 和 A[q+1...r]，它们包含 [n/2] 个元素。为了对整个序列 A=A[1],A[2],...A[n]，我们调用 MERGE-(A,1,length[A])，其中 A[n]=n。如果我们在 n 是 2 的幂时观察该过程底部的操作，该算法将长度为 1 的序列对合并为长度为 2 的有序序列，将长度为 2 的序列对合并为长度为 4 的有序序列，以此此类推，直到两个长度为 n/2 的序列合并成最终长度为 n 的有序序列。

### 算法

MERGE-SORT (A, p, r)

+   1. 开始
2. 如果 p < r
3. 则 q = (p + r) / 2
4. MERGE-SORT(A, p, q)
5. MERGE-SORT(A, q+1, r)
6. MERGE(A, p, q, r)

MERGE (A, p, q, r)

+   1. N1 = q - p + 1
2. N2 = r - q
3. 创建数组 L[1.......n1+1] 和 R[1.......n2+1]
4. 对于 i=1 到 n1
5. 执行 L[i] = A[p + i - 1]
6. 对于 j =1 到 n2
7. 执行 R[j] = A[q + j]
8. L[n1+1] = ∞
9. R[n2+1] = ∞
10. i = 1
11. j = 1
12. 对于 k = p 到 r
13. 执行 如果 L[i] ≤ R[j]
14. 则 A[k] = L[i]
15. i = i + 1
16. 否则 A[k] = R[j]
17. j = j + 1

示例：让我们取元素列表并应用合并排序技术

194 34 12 756 54 1 88 55 897 23 96 33

解决方案：

第 1 步：将两个无序对合并为一个有序对。初始我们有大小为 1 的对。合并为大小为 2 的对。

有序对

![](img/3d5da05d64722faaa72fdc4daca105f9_386_0.png)

# 第8章查找与排序

# 第 2 步：同样将大小为 2 的对合并为大小为 4 的对

34 194 12 756 1 54 55 88 23 897 33 96

# 有序对

12 34 194 756 1 54 55 88 23 33 96 897

# 第 3 步：以排序方式将大小为 4 的对合并为大小为 8 的对

1 12 33 54 55 88 194 756 23 897 33 96

# 第 4 步：将两个对合并为一个对

1 12 23 33 34 54 55 88 96 194 756 897

现在有序列表为：

1 12 23 33 34 54 55 88 96 194 756 897

### 程序：写一个程序使用数组实现合并排序

```c
#include<stdio.h>
#define MAX 50
void mergeSort(int arr[], int low, int mid, int high);
void partition(int arr[], int low, int high);
void main()
{
    int merge[MAX],i,n;
    printf("Enter the total number of elements: \n");
    scanf("%d",&n);
    printf("Enter the elements which be to sort: \n");
    for(i=0;i<n;i++)
    {
        scanf("%d",&merge[i]);
    }
    partition(merge,0,n-1);
    printf("After merge elements: \n");
    for(i=0;i<n;i++)
    {
        printf("%d",merge[i]);
    }
}
```

```c
void partition(int arr[], int low, int high)
{
  int mid;
  if(low<high)
  {
    mid=(low+high)/2;
    partition(arr,low,mid);
    partition(arr,mid+1,high);
    mergeSort(arr,low,high);
  }
}
```

```c
void mergeSort(int arr[], int low, int mid, int high)
{
  int i,m,k,l,temp[MAX];
  l=low;
  i=low;
  m=mid+1;
  while(l<=mid&&m<=high)
  {
    if(arr[l]<=arr[m])
    {
      temp[i]=arr[l];
      l++;
    }
    else
    {
      temp[i]=arr[m];
      m++;
    }
    i++;
  }
  while(l<=mid)
  {
    temp[i]=arr[l];
    l++;
    i++;
  }
  while(m<=high)
  {
    temp[i]=arr[m];
    m++;
    i++;
  }
  for(k=low;k<=high;k++)
  {
    arr[k]=temp[k];
  }
}
```

### 输出

输入元素个数：

12

输入要排序的元素：

194 34 12 756 54 1 88 55 897 23 96 33

合并后的元素：

1 12 23 33 34 55 88 96 194 756 897

# 8.10 堆排序 (HEAP SORT)

堆排序由 John Williams 发明，其方法与选择排序相反。选择排序找到 n 个元素中的最小值，然后是在 n-1 个元素中找到最小值，以此类推直到数组末尾；堆排序找到最大元素并将其放在数组末尾，此过程对其他元素重复。在讨论堆排序之前，我们先定义一个新结构：堆。**最大堆（或最小堆）**是一个完全二叉树，其中每个节点的值大于（或小于）它的子节点的值（如果存在）。这被称为堆属性。堆是每个节点都满足堆属性的完全二叉树。最大堆的定义意味着根是堆中最大元素之一。如果元素是唯一的，那么根包含最大元素。

我们按照以下步骤进行堆排序：

+   1. 用堆的最后一个节点替换根
+   2. 将最后一个节点（现在的根）放在正确的位置，这意味着堆中的删除操作，但这里被删除的节点是根。

# 示例：让我们取一个堆并应用堆排序

![](img/3d5da05d64722faaa72fdc4daca105f9_390_0.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 72 | 64 | 65 | 56 | 32 | 46 | 54 | 29 | |

### 解决方案：

# 第 1 步：

![](img/3d5da05d64722faaa72fdc4daca105f9_390_1.png)
