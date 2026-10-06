# Chapter 2 Introduction to Array

29

# Row-Major Implementation

Row major ordering assigns successive elements moving across the rows and then down the columns to successive memory locations. The mapping is best described by the diagram.

Row major ordering is the method employed by most high level programming languages including Pascal, C, Ada Modula-2 it very easy to implement and easy to use in machine language (especially with a debugger as CodeView). The conversion from a two-dimensional structure to a linear array is very intuitive.

A:array[0..3,3] of char,

| | 0 | 1 | 2 | 3 |
|---|---|---|---||
| 0 | 15 | 14 | 13 | 12 |
| 1 | 10 | 9 | 8 | 7 |
| 2 | 6 | 5 | 4 | 3 |
| 3 | 12 | 13 | 14 | 15 |

+   1. Address of element in Row-Major Implementation
Address of element a[i][j]=B+W (n (i-L1)+(j-L2))

Where B=base address
W=size of each array element
n=number of column (i.e., U2 - L2 + 1)
L1=lower bound of row
L2=lower bound of column
U2=upper bound of column

Q1. A-2D array defined as A[4....6, 1....4] required 4 bytes of storage for each element. If the array is stored in row major, then calculate the address of element at location A [5, 2]. Base address is 100.

Solution: Apply the formula
Address of element a[i][j]=B+ W (n (i- L1) + (j- L2))
B=100, W=4, i=5, j=2, L1=4, L2=1, U2=4
Calculate n=U2 - L2 + 1
=4-1+1

=4
Address of A[5,2]=100 + 4 (4 (5 - 4) + (2 - 1))
=100 + 4 (4 * 1 + 1)
=120

Q2. Calculate the address of Y [4,3] in a 2-D array Y[1....6, 1....5] stored in row major order in the main memory. Suppose the base address to be 200 and that each element required 4 bytes of storage.