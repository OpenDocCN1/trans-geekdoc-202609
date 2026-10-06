
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

# Output

Enter number of elements
6
Enter 5 integers
3 6 1 8 4 5
Sorted list in ascending order:
1 3 4 5 6 8

# 8.9 MERGE SORT

Merge sort is a sorting algorithm that uses the idea of divide and conquer approach. The procedure MERGE (A, p, r) sorts the elements in the sub array A[p...r]. If p ≤ r the sub array has at most one element and is therefore already sorted. Otherwise, the divide step simply computes an index q that partitions A[p...r] into two subarrays: A[p...q], and A[q+1...r] containing [n/2] elements. To sort the entire sequence A=A[1],A[2],...A[n] we call MERGE-(A,1,length[A]) where once again A[n]=n. If we look at the operation of the procedure bottom when n is a power of two, the algorithm of merging pairs of 1 item sequence to sorted sequences of length 2, merging pairs of sequences of length 2 to form sorted sequences of length 4, and so on, until two sequences of length n/2 are merged to form the final sorted sequence of length n.

# Algorithm

MERGE-SORT (A, p, r)

+   1. start
2. if p < r
3. then q = (p + r) / 2
4. MERGE-SORT(A, p, q)
5. MERGE-SORT(A, q+1, r)
6. MERGE(A, p, q, r)

MERGE (A, p, q, r)

+   1. N1 = q - p + 1
2. N2 = r - q
3. create arrays L[1.......n1+1] and R[1.......n2+1]
4. for i=1 to n1
5. do L[i] = A[p + i - 1]
6. for j =1 to n2
7. do R[j] = A[q + j]
8. L[n1+1] = ∞
9. R[n2+1] = ∞
10. i = 1
11. j = 1
12. for k = p to r
13. do if L[i] ≤ R[j]
14. then A[k] = L[i]
15. i = i + 1
16. else A[k] = R[j]
17. j = j + 1

Example: let us take a list of element and apply merge sort technique
194 34 12 756 54 1 88 55 897 23 96 33

Solution:

Step 1: merge the two unsorted pairs in a single sorted pair. Initially we have pair size 1. into pairs of size 2.

Sorted pair

![](img/3d5da05d64722faaa72fdc4daca105f9_386_0.png)

# Chapter 8 Searching and Sorting

# Step 2: similarly merge the pairs of size 2 into pair of size 4

34 194 12 756 1 54 55 88 23 897 33 96

# Sorted pair

12 34 194 756 1 54 55 88 23 33 96 897

# Step 3: merge the pairs of size 4 into a pair of 8 in sorted fashion

1 12 33 54 55 88 194 756 23 897 33 96

# Step 4: merge two pairs into a single pair

1 12 23 33 34 54 55 88 96 194 756 897

Now the sorted list is:

1 12 23 33 34 54 55 88 96 194 756 897

# Program: Write a program to implement a merge sort using array

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
    printf("After merge sorting elements: \n");
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

# Output

Enter the total number of elements:
12
Enter the elements which be sort:
194 34 12 756 54 1 88 55 897 23 96 33
After merge sorting elements are:
1 12 23 33 34 55 88 96 194 756 897

# 8.10 HEAP SORT

Heap sort was invented by John Williams and uses the approach opposite to selection sort. The selection sorts the smallest element among n elements, then the smallest element among n-1 elements and on on, until the end of the array where heap sort finds the largest element and puts it at the end of the array, the second largest item is found and this process is repeated for all other elements. Before discussing heap sort, we will begin by defining a new structure, the heap. We can define minimum heap and maximum heap. A **max (or min) heap** is a complete binary tree with the property that the value at each node is at least large as (or small as) the values of its children (if they exist). This is called Heap property. A heap is complete binary tree in which each node satisfies the heap property and every leaf is of depth d-1. The definition of a max heap implies that one of the largest elements at the root of the heap. If the elements are distinct, then the root contains the largest element.

We do following steps for heap sorting

+   1. Replace the root with last node of heap tree
+   2. Keep the last node (now root) at the proper position, it means the delete operation in heap tree but here deleted node is root.

# Example: Let us take a heap tree and apply tree sorting

![](img/3d5da05d64722faaa72fdc4daca105f9_390_0.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 72 | 64 | 65 | 56 | 32 | 46 | 54 | 29 | |

# Solution:

# Step 1:

![](img/3d5da05d64722faaa72fdc4daca105f9_390_1.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 48 | 64 | 65 | 56 | 32 | 46 | 54 | 29 | 72 |

Now the root is at the position of last node and last node at the position of root. Here left and right child of 48 is 64 and 65.

![](img/3d5da05d64722faaa72fdc4daca105f9_390_2.png)

Here right child of 48 is 54, which is greater than 48, hence replace it with 54.

![](img/3d5da05d64722faaa72fdc4daca105f9_391_0.png)

Now the elements of heap tree in array are:

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 65 | 64 | 54 | 56 | 32 | 46 | 48 | 29 | 72 |

Now 29 is the last node. So replace it with root 65 and do the same.

# Step 2:

![](img/3d5da05d64722faaa72fdc4daca105f9_391_1.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 64 | 56 | 54 | 65 | 32 | 46 | 48 | 29 | 72 |

# Step 3: same as step 1 and step 2

![](img/3d5da05d64722faaa72fdc4daca105f9_391_2.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 64 | 56 | 54 | 65 | 32 | 46 | 48 | 29 | 72 |

# Step 4:

![](img/3d5da05d64722faaa72fdc4daca105f9_391_3.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 54 | 48 | 54 | 65 | 32 | 46 | 64 | 29 | 72 |

# Step 5:

![](img/3d5da05d64722faaa72fdc4daca105f9_392_0.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 48 | 32 | 54 | 65 | 56 | 46 | 64 | 29 | 72 |

# Step 6:

![](img/3d5da05d64722faaa72fdc4daca105f9_392_1.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 46 | 32 | 54 | 65 | 56 | 48 | 64 | 29 | 72 |

# Step 7:

![](img/3d5da05d64722faaa72fdc4daca105f9_392_2.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 32 | 29 | 54 | 65 | 56 | 48 | 64 | 46 | 72 |

# Step 8:

![](img/3d5da05d64722faaa72fdc4daca105f9_392_3.png)

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 29 | 32 | 54 | 65 | 56 | 48 | 64 | 46 | 72 |

Program: Write a program Implement heap sort

```c
#include<stdio.h>
void main()
{
    int a[20],i,j,temp,n,root,c;
    printf("Enter size of array : ");
    scanf("%d",&n);
    printf("Enter element in array : ");
    for(i=0;i<n;i++)
    scanf("%d",&a[i]);
    for(i=1;i<n;i++)
    {
      c=i;
      do
    {
        root=(c-1)/2;
        if(a[root]<a[c])
        {
          temp=a[root];
          a[root]=a[c];
          a[c]=temp;
        }
        c=root;
      }while(c!=0);
    }
    printf("Heap array : ");
    for(i=0;i<n;i++)
    printf(" %d",a[i]);
    for(j=n-1;j>=0;j--)
    {
      temp=a[0];
      a[0]=a[j];
      a[j]=temp;
      root=0;
      do
    {
        c=2*root+1;
        if(a[c]<a[c+1] && c<j)
        c++;
        if(a[root]<a[c] && c<j)
        {
          temp=a[root];
          a[root]=a[c];
          a[c]=temp;
        }
        root=c;
      }while(c<j);
    }
}
```
