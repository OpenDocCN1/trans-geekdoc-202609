The maximum number of non-zero elements in sparse matrix is defined by constant MAX. The array representation will use [2 * (n + 1) * size of (int) + n * size of (T)] bytes of memory where n is the number of non-zero bytes and T is the data type of elements.

# Linked List Representation of a Sparse Matrix

Representing a sparse matrix as an array of 3-tuples. we need to know the number of non-zero terms in each of the sparse matrices. As a result, it is not possible to predict the size of the resultant matrix before hand. Instead of an array, we can represent the sparse matrix in the form of a linked list. The linked list representation is maintained for each column as well as each row of the matrix, i.e., if the matrix is of size 4 x 4, then there would be 4 lists for 4 columns and 4 lists for 4 rows. A node in a list stores the information about the non-zero element of the sparse matrix. The head node for a column list stores the column number, a pointer to the node which comes first in the column and a pointer to the next column head node. A head node for a row list, a pointer to the node, which comes first in the row list, and a pointer to the next head node.

Example: Show through appropriate data structure representation of the following 4 x 4 sparse matrix.

|0 0 11 0|
|12 0 0 0|
|0 -4 0 0|
|0 0 0 -25|

Solution: The given 4 x 4 sparse matrix can be represented in array is:

| Row | Column | Value |
| 0 | 2 | 11 |
| 1 | 0 | 12 |
| 2 | 1 | -4 |
| 3 | 3 | -25 |

And the linked list representation is:

Example: Let a N x N sparse matrix array. Write algorithm for the following:

+   (i) Find the number NUM of non-zero element in A.
(ii) Find the product PROD of the diagonal elements
(a11, a22, ..., ann)

```
|4 4 4|
|--3 11 X|
|--2 12 X|
|--3 2-4 X|
|--4 25 X|
```