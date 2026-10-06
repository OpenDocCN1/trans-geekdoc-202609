```
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

```
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

Merge sort is a sorting algorithm that uses the idea of divide and conquers approach. The procedure MERGE (A, p, r) sorts the elements in the sub array A[p...r]. If p ≤ r the sub array has at most one element and is therefore already sorted. Otherwise, the divide step simply computes an index q that partitions A[p...r] into two subarrays: A[p...q], and A[q+1...r] containing [n/2] elements. To sort the entire sequence A=A[1],A[2],...A[n] we call MERGE-(A,1,length[A]) where once again A[n]=n. If we look at the operation of the procedure bottom when n is a power of two, the algorithm of merging pairs of 1 item sequence to sorted sequences of length 2, merging pairs of sequences of length 2 to form sorted sequences of length 4, and so on, until two sequences of length n/2 are merged to form the final sorted sequence of length n.