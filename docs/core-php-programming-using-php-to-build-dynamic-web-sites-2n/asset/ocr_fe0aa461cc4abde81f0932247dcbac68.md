# Core PHP Programming

take several forms but always involves comparing two elements with a set of rules for ordering. The result of the comparison determines whether the two items are in order or out of order, therefore needing to be swapped.

There are three classes of sorts: exchange, insert, and select. In an exchange method, two elements are compared and possibly exchanged. This process continues until the list is in order. In an insert method, the elements are removed and placed in another list, one by one. Each time an element is moved, it is inserted into the correct position. When all elements are moved, the list is in order. A selection sort involves building a second list by scanning the first and repeatedly selecting the lowest value. Insertion sorts are two sides of a coin. The former scans the new list; the latter scans the old list.

As I said earlier, a sorting algorithm is essentially comparison and possible movement of elements in a list. On average, moving elements takes the same amount of time, no matter what algorithm you use. Likewise, the comparison is independent of the actual sort. If we take these to constants, the most important question to ask about algorithm is: How many times must the sort be kept in context with the data. Some algorithms perform very well when the data are completely unordered but slow when the data are already in reverse order. Some sorts perform very poorly when there are many elements; others have such as be inappropriate for smaller data sets. Like any technician, the programmer matches the tools to the job.

In the first part of this chapter I will describe the bubble sort and the quicksort. I will guide you through expressing the algorithms in PHP. I will then go on to describe the built-in sorting functions.

# Bubble Sort

Bubble sort's one virtue is simplicity. The list is scanned repeatedly, less than there are elements. Neighboring items are compared and swapped if out of order. Each time through the list you scan one less item because the lightest bubbles (to stick with the metaphor) have risen to the top.

The outermost loop sets the limit for how far to bubbles to rise. The first time through this, is one, the first element of the array is indexed by zero. After going through the inner loop once, we will be certain that the smallest number will be in the first position of the array. This is because the inner loop will compare the smallest to the next element, swap them if they are out of order, and move up a notch. Eventually the smallest element will be reached and swapped upward.

If n is the number of elements in the array, the bubble sort will always make (n - 1) comparisons, then (n - 2) and so on. In Listing 15.1, this means 7 elements require 21 comparisons (6 + 5 + 4 + 3 + 2 + 1) in the first iteration, regardless of whether the array is in or out of order. If the array is already in order, no exchanges will be made. If it is in reverse order, an exchange will be made for every comparison.