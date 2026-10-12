
The key is found during the 2nd pass when you examine `a[0]`. Thus a key of `3` is not a worst case situation. The discrepancy is due to the asymmetry of the div operation, which gives values of `mid` that are closer to the left endpoint than the right.

![](images/sq1.jpg)

If the key is `1` or `20`, say (outside the range of array values and not in the array), the algorithm will need 3 passes through the search loop to determine that the key is not in the array, a worst case.

![](images/sq1.jpg)

If the key is `8`, say (not in the array but inside the range of array values), the algorithm will need just 2 passes through the search loop to determine that the key is not in the array. So this is not a worst case.

![](images/sq1.jpg)

If the key is `10`, say (not in the array but between `a[2]` and `a[3]` in this example), the algorithm will need 3 passes through the search loop to determine that the key is not in the array, a worst case! Here is how it works:

1st pass: `low` = `0 high` = `3 mid` = `1`

2nd pass: `low` = `2 high` = `3 mid` = `2`

3rd pass: `low` = `3 high` = `3 mid` = `3`

When `a[3]` is found to be greater than `key`, the value of `low` becomes `4`, while `high` is still `3`, which means that the test `if (low > high)` becomes true and is a base case that terminates the algorithm. There are no further comparisons with `key`.

Here is another example, where *n* is not a power of 2.

Suppose the array is `1`, `3`, `5`, `7`, `9`. Here *n* is 5. To find the number of passes in the worst case, round up to the nearest power of 2, which is 8 or 2³. In the worst case, the number of passes through the search loop will be 3:

![](images/sq1.jpg)

If the key is `1`, there will be 2 passes to find it, which is not a worst case.

![](images/sq1.jpg)

If the key is `9`, there will be 3 passes to find it, which is a worst case.

![](images/sq1.jpg)

If the key is `8`, there will be 3 passes to find it, which is a worst case.

![](images/sq1.jpg)

If the key is `4`, there will be 2 passes to find it, which is not a worst case.

![](images/sq1.jpg)

If the key is any value outside the range of `1` – `9`, there will be 3 passes to find it, which is a worst case.

The lessons from these examples is that not every key that is not in the array represents a worst case.

Here are some general rules for calculating the maximum number of loop passes in different binary search situations. In each case it’s assumed that the algorithm given in this book is used.

![](images/sq1.jpg)

If *n*, the number of elements, is not a power of 2, round *n* up to the nearest power of 2. The number of passes in the worst case equals the exponent.

![](images/sq1.jpg)

If *n* is a power of 2, the number of passes in the worst case equals the exponent plus one.

![](images/sq1.jpg)

Irrespective of *n*, the worst case will always involve a key that is either at the right endpoint or not in the array.

![](images/sq1.jpg)

Irrespective of *n*, any key that is not in the array and is less than `a[0]` or greater than `a[n-1]` will be a worst case situation.

![](images/sq1.jpg)

Irrespective of *n*, any key that is between `a[0]` and `a[n-1]` but is not in the array may or may not be a worst case situation.

### Chapter Summary

You should not memorize any sorting code. You must, however, be familiar with the mechanism used in each of the sorting algorithms. For example, you should be able to explain how the merge method of merge sort works, or how many elements are in their final sorted position after a certain number of passes through the selection sort loop. You should know the best and worst case situations for each of the sorting algorithms.

Be familiar with the sequential and binary search algorithms. You should know that a binary search is more efficient than a sequential search, and that a binary search can only be used for an array that is sorted on the search key.

### Multiple-Choice Questions on Sorting and Searching

[1](#54_Chapter46.xhtml#qans3_1). The decision to choose a particular sorting algorithm should be made based on which of the following?

I. Run-time efficiency of the sort

II. Size of the array

III. Space efficiency of the algorithm

(A) I only

(B) II only

(C) III only

(D) I and II only

(E) I, II, and III

[2](#54_Chapter46.xhtml#qans3_2). The following code fragment does a sequential search to determine whether a given integer, `value`, is stored in an array `a[0]` ... `a[n-1]`.

![images](images/f315-01.jpg)

Which of the following should replace `/* boolean expression */` so that the algorithm works as intended?

(A) `value != a[i]`

(B) `i < n && value == a[i]`

(C) `value != a[i] && i < n`

(D) `i < n && value != a[i]`

(E) `i < n || value != a[i]`

[3](#54_Chapter46.xhtml#qans3_3). A feature of data that is used for a binary search but not necessarily used for a sequential search is

(A) length of list.

(B) type of data.

(C) order of data.

(D) smallest value in the list.

(E) median value of the data.

[4](#54_Chapter46.xhtml#qans3_4). Array `unsortedArr` contains an unsorted list of integers. Array `sortedArr` contains a list of integers sorted in increasing order. Which of the following operations is more efficient for `sortedArr` than `unsortedArr`? Assume the most efficient algorithms are used.

I. Inserting a new element

II. Searching for a given element

III. Computing the mean of the elements

(A) I only

(B) II only

(C) III only

(D) I and II only

(E) I, II, and III

[5](#54_Chapter46.xhtml#qans3_5). An algorithm for searching a large sorted array for a specific value *x* compares every third item in the array to *x* until it finds one that is greater than or equal to *x*. When a larger value is found, the algorithm compares *x* to the previous two items. If the array is sorted in increasing order, which of the following describes all cases when this algorithm uses fewer comparisons to find *x* than would a binary search?

(A) It will never use fewer comparisons.

(B) When *x* is in the middle position of the array

(C) When *x* is very close to the beginning of the array

(D) When *x* is very close to the end of the array

(E) When *x* is not in the array

[6](#54_Chapter46.xhtml#qans3_6). Assume that `a[0]` ... `a[N-1]` is an array of *N* positive integers and that the following assertion is true.

![images](images/f315-03.jpg)

Which of the following *must* be true?

(A) The array is sorted in ascending order.

(B) The array is sorted in descending order.

(C) All values in the array are different.

(D) `a[0]` holds the smallest value in the array.

(E) `a[0]` holds the largest value in the array.

[7](#54_Chapter46.xhtml#qans3_7). The following code is designed to set `index` to the location of the first occurrence of `key` in array `a` and to set `index` to −1 if `key` is not in `a`.

![images](images/f316-01.jpg)

In which case will this program *definitely* fail to perform the task described?

(A) When `key` is the first element of the array

(B) When `key` is the last element of the array

(C) When `key` is not in the array

(D) When `key` equals 0

(E) When `key` equals `a[key]`

[8](#54_Chapter46.xhtml#qans3_8). Refer to method `search`.

![images](images/f316-02.jpg)

Assuming that the method works as intended, which of the following should be added to the precondition of `search`?

(A) `v` is sorted smallest to largest.

(B) `v` is sorted largest to smallest.

(C) `v` is unsorted.

(D) There is at least one occurrence of `key` in `v`.

(E) `key` occurs no more than once in `v`.

[9](#54_Chapter46.xhtml#qans3_9). Consider the following class.

![images](images/f317-01.jpg)

If an array of `Integer` contains the following elements, what would the array look like after the third pass of `selectionSort`, sorting from high to low?

89 42 −3 13 109 70 2

![images](images/f317-02.jpg)

Questions 10–14 are based on the `binSearch` method and the private instance variable `a` for some class.

![images](images/f318-01.jpg)
