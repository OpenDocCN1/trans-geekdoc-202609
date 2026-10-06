# Output

Enter size of the array: 12

Enter 12 elements:
46
27
6
57
70
86
40
63
93
17
80
66

Sorted elements:
6 17 27 40 46 57 63 66 70 80 86 93

# 8.12 RADIX SORT

This sort is based on the values of the actual digits in the positional representations of the numbers being sorted. For example, the number 475 in decimal notation is written with a 4 in the hundred position, a 7 in the tens position, and a 5 in the unit position. The larger of the two integer of equal length can be determined as follows: start at the most significant digit and advance through the least significant digits as long as the corresponding digits in the two numbers match. The number with the larger digit in the first position in which the digits of the two numbers do not match is the larger of the two. Of course, if all the digits of both match, the numbers are equal. To sort decimal numbers, we need ten buckets, since the base or radix is ten. These buckets are numbered 0,1,2,3,4,5,6,7,8,9.

Example: let us take number in unsorted order and sort them by applying radix sort.

235 126 211 347 499 569 330 165

Solution:

Step 1: Take these numbers on the basis of unit digit