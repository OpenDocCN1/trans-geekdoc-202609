# Chapter 8 Searching and Sorting

```
printf("%d\t", array[c]);
}
return 0;
}
```

# ## Output

Enter number of elements

7

Enter 7 integers

30 20 35 14 90 25 32

Sorted list in ascending order:

14 20 25 30 32 35 90

# ## 8.8 SELECTION SORT

The idea of selection sort is rather simple: we repeatedly find the next largest (or smallest) element in the array and move it to its final position in the sorted array. Assume we wish to sort the array in increasing order, i.e., the smallest element at the beginning of the array and the largest element at the end. We begin by selecting the largest element and moving it to the highest index and the largest element. We can do this by swapping the element at the highest index and the largest element. We reduce the effective size of the array by one element and repeat the process on the smaller sub-array.

Let us use an array of elements. First you will search the position of smallest element from array[0] ...... array[n-1]. Then you will interchange that smallest element with array[0]. Now you will search the position of the second smallest element from array[1] ...... array[n-1], then interchange that smallest element with array[1], and so on......

# ## Algorithm

Selection sort (A)

+   1. start
2. n=length[A]
3. for j=1 to n-1
4. smallest=j
5. for i=j+1 to n
6. if A[i] < A[smallest]
7. then smallest=i
8. exchange (A[j], A[smallest])