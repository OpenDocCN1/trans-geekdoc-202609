
# 二分查找与排序算法练习题

## 二分查找

A binary search will be performed on the following list.

![images](images/f318-02.jpg)

**10.** To find the key value 27, the search interval *after* the first pass through the `while` loop will be

- (A) `a[0]` ... `a[7]`
- (B) `a[5]` ... `a[6]`
- (C) `a[4]` ... `a[7]`
- (D) `a[2]` ... `a[6]`
- (E) `a[6]` ... `a[7]`

**11.** How many iterations will be required to determine that 27 is not in the list?

- (A) 1
- (B) 3
- (C) 4
- (D) 8
- (E) 16

**12.** What will be stored in `y` after executing the following?

![images](images/f318-03.jpg)

- (A) `20`
- (B) `7`
- (C) `4`
- (D) `0`
- (E) `−1`

**13.** If the test for the `while` loop is changed to

![images](images/f318-04.jpg)

the `binSearch` method does not work as intended. Which value in the given list will not be found?

- (A) 4
- (B) 7
- (C) 11
- (D) 24
- (E) 30

**14.** For `binSearch`, which of the following assertions will be true following every iteration of the `while` loop?

- (A) `key` = `a[mid]` or `key` is not in `a`.
- (B) `a[low]` ≤ `key` ≤ `a[high]`
- (C) `low` ≤ `mid` ≤ `high`
- (D) `key` = `a[mid]`, or `a[low]` ≤ `key` ≤ `a[high]`
- (E) `key` = `a[mid]`, or `a[low]` ≤ `key` ≤ `a[high]`, or `key` is not in array `a`.

**15.** A large sorted array containing about 30,000 elements is to be searched for a value `key` using an iterative binary search algorithm. Assuming that `key` is in the array, which of the following is closest to the smallest number of iterations that will guarantee that `key` is found? Note: 10³ ≈ 2^(10).

- (A) 15
- (B) 30
- (C) 100
- (D) 300
- (E) 3000

## 插入排序

For Questions 16–19 refer to the `insertionSort` method and the private instance variable `a`, both in a `Sorter` class.

![images](images/f319-01.jpg)

**16.** An array of `Integer` is to be sorted biggest to smallest using the `insertionSort` method. If the array originally contains

1 7 9 5 4 12

what will it look like after the third pass of the `for` loop?

- (A) 9 7 1 5 4 12
- (B) 9 7 5 1 4 12
- (C) 12 9 7 1 5 4
- (D) 12 9 7 5 4 1
- (E) 9 7 12 5 4 1

**17.** When sorted biggest to smallest with `insertionSort`, which list will need the fewest changes of position for individual elements?

- (A) 5, 1, 2, 3, 4, 9
- (B) 9, 5, 1, 4, 3, 2
- (C) 9, 4, 2, 5, 1, 3
- (D) 9, 3, 5, 1, 4, 2
- (E) 3, 2, 1, 9, 5, 4

**18.** When sorted biggest to smallest with `insertionSort`, which list will need the greatest number of changes in position?

- (A) 5, 1, 2, 3, 4, 7, 6, 9
- (B) 9, 5, 1, 4, 3, 2, 1, 0
- (C) 9, 4, 6, 2, 1, 5, 1, 3
- (D) 9, 6, 9, 5, 6, 7, 2, 0
- (E) 3, 2, 1, 0, 9, 6, 5, 4

**19.** While typing the `insertionSort` method, a programmer by mistake enters

![images](images/f319-02.jpg)

Despite this mistake, the method works as intended the first time the programmer enters an array to be sorted in descending order. Which of the following could explain this?

- I. The first element in the array was the largest element in the array.
- II. The array was already sorted in descending order.
- III. The first element was less than or equal to all the other elements in the array.

- (A) I only
- (B) II only
- (C) III only
- (D) I and II only
- (E) II and III only

**20.** The elements in a long list of integers are roughly sorted in decreasing order. No more than 5 percent of the elements are out of order. Which of the following is a valid reason for using an insertion sort rather than a selection sort to sort this list into decreasing order?

- I. There will be fewer comparisons of elements for insertion sort.
- II. There will be fewer changes of position of elements for insertion sort.
- III. There will be less space required for insertion sort.

- (A) I only
- (B) II only
- (C) III only
- (D) I and II only
- (E) I, II, and III

## 归并排序 vs 插入排序

**21.** Which of the following is a valid reason why merge sort is a better sorting algorithm than insertion sort for sorting long, randomly ordered lists?

- I. Merge sort requires less code than insertion sort.
- II. Merge sort requires less storage space than insertion sort.
- III. Merge sort runs faster than insertion sort.

- (A) I only
- (B) II only
- (C) III only
- (D) I and II only
- (E) II and III only

## 模式匹配搜索

**22.** A large array of lowercase characters is to be searched for the pattern “pqrs.” The first step in a very efficient searching algorithm is to look at characters with index

- (A) 0, 1, 2, ... until a “p” is encountered.
- (B) 0, 1, 2, ... until any letter in “p” ... “s” is encountered.
- (C) 3, 7, 11, ... until an “s” is encountered.
- (D) 3, 7, 11, ... until any letter in “p” ... “s” is encountered.
- (E) 3, 7, 11, ... until any letter other than “p” ... “s” is encountered.

## 二分查找前置条件

**23.** The array `names[0]`, `names[1]`, ..., `names[9999]` is a list of 10,000 name strings. The list is to be searched to determine the location of some name `X` in the list. Which of the following preconditions is necessary for a binary search?

- (A) There are no duplicate names in the list.
- (B) The number of names *N* in the list is large.
- (C) The list is in alphabetical order.
- (D) Name `X` is definitely in the list.
- (E) Name `X` occurs near the middle of the list.

## 算法识别

**24.** Consider the following method.

![images](images/f320-01.jpg)

The method shown is an example of

- (A) insertion sort.
- (B) merge sort.
- (C) selection sort.
- (D) binary search.
- (E) sequential search.

## 可选主题：快速排序与归并排序

**25.** The `partition` method for quicksort partitions a list as follows.

(i) A pivot element is selected from the array.
(ii) The elements of the list are rearranged such that all elements to the left of the pivot are less than or equal to it; all elements to the right of the pivot are greater than or equal to it.

Partitioning the array requires which of the following?

- (A) A recursive algorithm
- (B) A temporary array
- (C) An external file for the array
- (D) A swap algorithm for interchanging array elements
- (E) A merge method for merging two sorted lists

**26.** Assume that merge sort will be used to sort an array `arr` of `n` integers into increasing order. What is the purpose of the `merge` method in the merge sort algorithm?

- (A) Partition `arr` into two parts of roughly equal length, then merge these parts.
- (B) Use a recursive algorithm to sort `arr` into increasing order.
- (C) Divide `arr` into `n` subarrays, each with one element.
- (D) Merge two sorted parts of `arr` into a single sorted array.
- (E) Merge two sorted arrays into a temporary array that is sorted.

## 复杂度分析

**27.** A binary search is to be performed on an array with 600 elements. In the *worst* case, which of the following best approximates the number of iterations of the algorithm?

- (A) 6
- (B) 10
- (C) 100
- (D) 300
- (E) 600

**28.** A worst case situation for insertion sort would be

- I. A list in correct sorted order.
- II. A list sorted in reverse order.
- III. A list in random order.

- (A) I only
- (B) II only
- (C) III only
- (D) I and II only
- (E) II and III only

**29.** Consider a binary search algorithm to search an ordered list of numbers. Which of the following choices is closest to the maximum number of times that such an algorithm will execute its main comparison loop when searching a list of 1 million numbers?

- (A) 6
- (B) 20
- (C) 100
- (D) 120
- (E) 1000

**30.** Consider these three tasks.

- I. A sequential search of an array of *n* names
- II. A binary search of an array of *n* names in alphabetical order
- III. An insertion sort into alphabetical order of an array of *n* names that are initially in random order

For large *n*, which of the following lists these tasks in order (from least to greatest) of their average case run times?

![images](images/f321-01.jpg)
