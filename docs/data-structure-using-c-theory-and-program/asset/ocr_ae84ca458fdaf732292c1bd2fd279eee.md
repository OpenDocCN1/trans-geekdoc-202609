```
{
  printf("\n\n\a\n\aSorted array : \n");
  for(i=0;i<n;i++)
    printf(" %d",a[i]);
}
```

# Output

Enter size of array : 8
Enter element in array : 72
64
65
56
32
46
54
29
48
Heap array : 72 64 65 56 32 46 54 56 65 29 48
Sorted array : 29 32 46 48 54 56 64 65 72

# 8.11 QUICK SORT

C.A.R. Hoare implements quick sort by divide and conquer method. That means divide the problem into two small problems and those two small problems into small ones and so on. To Quick sort, we divide the original list into two sub lists. We choose the item from list called key or pivot from which all the left side of elements are smaller and all the right side of elements are greater than that element. So we can create lists, one on the left side of pivot element and the second list is on light side of the pivot. Thus, quick sort works by partitioning a given A[p......r] into two non-empty sub-arrays A[p......q] and A[q+1......r] such that every key in A[p......q] is less than or equal to every key in A[q+1......r]. Then the two sub-arrays are stored by recursive calls to quick sort. The exact position of the partition depends on the given array and index q is computed as a part of the partitioning procedure.

# Algorithm

QUICK SORT (A, p, r)

+   1. if p < r then
2. q = PARTITION (A, p, r)