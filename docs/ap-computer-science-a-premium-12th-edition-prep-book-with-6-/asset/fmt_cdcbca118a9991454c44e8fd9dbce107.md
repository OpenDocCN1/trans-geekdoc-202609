
## 2. Merge Sort Characteristics

Merge sort is not affected by the initial ordering of the elements. Thus, best, worst, and average cases have similar run times.

## Optional Topic

### Quicksort

For large *n*, quicksort is, on average, the fastest known sorting algorithm. Here is a recursive description of how quicksort works:

If there are at least two elements in the array,

1. Partition the array.
2. Quicksort the left subarray.
3. Quicksort the right subarray.

The `partition` method splits the array into two subarrays as follows: a *pivot* element is chosen at random from the array (often just the first element) and placed so that all items to the left of the pivot are less than or equal to the pivot, whereas those to the right are greater than or equal to it.

For example, if the array is `4, 1, 2, 7, 5, −1, 8, 0, 6`, and `a[0] = 4` is the pivot, the `partition` method produces:

![images](images/f310-01.jpg)

Here’s how the partitioning works: Let `a[0]`, 4 in this case, be the pivot. Markers `up` and `down` are initialized to index values 0 and *n* − 1, as shown. Move the `up` marker until a value less than the pivot is found, or `down` equals `up`. Move the `down` marker until a value greater than the pivot is found, or `down` equals `up`. Swap `a[up]` and `a[down]`. Continue the process until `down` equals `up`. This is the pivot position. Swap `a[0]` and `a[pivotPosition]`.

![images](images/f310-02.jpg)

Notice that the pivot element, 4, is in its final sorted position.

#### Analysis of Quicksort

1. For the fastest run time, the array should be partitioned into two parts of roughly the same size.
2. If the pivot happens to be the smallest or largest element in the array, the split is not much of a split—one of the subarrays is empty! If this happens repeatedly, quicksort degenerates into a slow, recursive version of selection sort and is very inefficient.
3. The worst case for quicksort occurs when the partitioning algorithm repeatedly divides the array into pieces of size 1 and *n* − 1. An example is when the array is initially sorted in either order and the first or last element is chosen as the pivot. Some algorithms avoid this situation by initially shuffling up the given array (!) or selecting the pivot by examining several elements of the array (such as first, middle, and last) and then taking the median.

The main disadvantage of quicksort is that its worst case behavior is very inefficient.

### Note

For both quicksort and merge sort, when a subarray gets down to some small size *m*, it becomes faster to sort by straight insertion. The optimal value of *m* is machine-dependent, but it’s approximately equal to 7.

### Sorting Algorithms in Java

Unlike the container classes like `ArrayList`, whose elements must be objects, arrays can hold either objects or primitive types like `int` or `double`.

A common way of organizing code for sorting arrays is to create a sorter class with an array private instance variable. The class holds all the methods for a given type of sorting algorithm, and the constructor assigns the user’s array to the private array variable.

#### Example: Selection Sort for an Array of `int`

![images](images/f311-01.jpg)

### Sequential Search

Assume that you are searching for a key in a list of *n* elements. A sequential search starts at the first element and compares the key to each element in turn until the key is found or there are no more elements to examine in the list. For example, if the list is sorted in ascending order, stop searching as soon as the key is less than the current element. (If the key is less than the current element, it will be less than all subsequent elements.)

#### Analysis

1. The best case has the key in the first slot.
2. The worst case occurs if the key is in the last slot or not in the list. In the worst case, all *n* elements must be examined.
3. On average, there will be *n*/2 comparisons.

### Binary Search

If the elements are in a *sorted* array, a divide-and-conquer approach provides a much more efficient searching algorithm. The following recursive pseudocode algorithm shows how the *binary search* works.

Binary search works only if the array is sorted on the search key.

Assume that `a[low]` ... `a[high]` is sorted in ascending order and that a method `binSearch` returns the index of `key`. If `key` is not in the array, it returns −1.

![images](images/f312-01.jpg)

Note that this algorithm can also be described iteratively. There are no recursive calls, just an adjustment of `mid` so that the algorithm searches to the left or the right.

Again, assume that `a[low]...a[high]` is sorted in ascending order and that the method will return the index of `key`. If `key` is not in the array, the method will return −1.

![images](images/f312-02.jpg)

### Note

1. After just one comparison, the binary search algorithm ignores one half of the array elements. This is true for both the iterative and recursive versions.
2. When `low` and `high` cross, there are no more elements to examine, and `key` is not in the array.

For example, suppose 5 is the key to be found in the following array:

![images](images/f313-01.jpg)

### Analysis of Binary Search

1. In the best case, the key is found on the first try (i.e., `(low + high)/2` is the index of `key`).
2. In the worst case, the key is not in the array or is at an endpoint of the array. Here, the *n* elements must be divided by 2 until there is just one element, and then that last element must be compared with the key. An easy way to find the number of comparisons in the worst case is to round *n* up to the next power of 2 and take the exponent. For example, in the array above, *n* is 9. Suppose 21 were the key. Round 9 up to 16, which is 2⁴. Thus you would need 4 comparisons with the key to find it. If *n* is an exact power of 2, the number of comparisons in the worst case equals the exponent plus one. For example, if the number of elements *n* = 32 = 2⁵, then the number of comparisons in the worst case is 5 + 1 = 6. Note that in this discussion, the number of comparisons refers to the number of passes through the search loop of the above algorithm—namely, the outer `else` piece of code.

The number of comparisons for binary search in the worst case depends on whether *n* is a power of 2 or not.

3. There’s an interesting wrinkle when discussing the worst case of a binary search that uses the above algorithm. The worst case (i.e., the maximum number of comparisons) will either have the key at an endpoint of the array, or be equal to a value that’s not in the array. The opposite, however, is not necessarily true: If the key is at an endpoint, or a value not in the array, it is not necessarily a worst case situation.

As a simple example, consider the array `3`, `7`, `9`, `11`, where `a[0]` is `3` and `a[3]` is `11`. The number of elements *n* equals 4, which is 2², an exact power of 2. The worst case for searching for a given key will be 3 comparisons, the exponent plus one.

![images](images/sq1.jpg)

**If the key is `11` (an endpoint of the array)**, the algorithm will need 3 passes through the search loop to find the key. This is a worst case. Here’s how it works:

1. 1st pass: `low = 0`, `high = 3`, `mid = 1`
2. 2nd pass: `low = 2`, `high = 3`, `mid = 2`
3. 3rd pass: `low = 3`, `high = 3`, `mid = 3`

The key is found during the 3rd pass when you examine `a[3]`. Thus a key of `11` represents a worst case.

![images](images/sq1.jpg)

**If the key is `3` (the other endpoint of the array)**, the algorithm will need 2 passes through the search loop to find the key. Here’s how it works:

1. 1st pass: `low = 0`, `high = 3`, `mid = 1`
2. 2nd pass: `low = 0`, `high = 0`, `mid = 0`
