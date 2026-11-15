One interesting sort method is the *bubble sort*. This sort processes elements by comparing adjacent pairs, swapping them as required for a certain order. To sort in ascending order, a swap takes place only when the first value of a pair is greater than the second value. After the first pass of the search, the largest element will be the last in the ordered sequence. After the second pass, the second largest element will be in the second-to-last place of the ordered sequence. Because each element must be compared to all the other elements, there are potentially n – 1 passes required for a sequence to be completely sorted.

The following is a trace of the steps required for a bubble sort to put the sequence “5, 4, 6, 3, 7” in ascending order. Each pass is denoted by the iteration i.

| i = 1 | i = 2 | i = 3 | i = 4 |
| :--- | :--- | :--- | :--- |
| 5, 4, 6, 3, 7 <br> swap | 4, 5, 3, 6, | 7 <br> keep | 4, 3, 5, | 6, 7 <br> swap | 3, 4, | 5, 6, 7 <br> keep |
| 4, 5, 6, 3, 7 <br> keep | 4, 5, 3, 6, | 7 <br> swap | 3, 4, 5, | 6, 7 <br> keep | |
| 4, 5, 6, 3, 7 <br> swap | 4, 3, 5, 6, | 7 <br> keep | | |
| 4, 5, 3, 6, 7 <br> keep | | | |

Another interesting sorting routine is the *selection sort*, which builds a sorted list by partitioning the original list