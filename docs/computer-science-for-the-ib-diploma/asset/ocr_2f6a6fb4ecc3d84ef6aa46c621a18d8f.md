![](bbox=[0.11, 0.08, 0.49, 0.3])

# Two-dimensional arrays / lists

A two-dimensional array can be seen as a table, with rows and columns. To manipulate and traverse a 2D array, two indices are used: one for the rows and one for the columns. When writing code, rows are always first and columns second.

Look at the figure for storing numbers from 1 to 9 in a table with three rows and three columns. You will create a 2D array or a 2D list for this purpose.

Each element in a 2D array (Java) or 2D list (Python) can be directly accessed by specifying its indices (row index and column index).

# Declaration

```
```java
int numbers[ ] [ ] = new int [3] [3];
```
```

```
```python
numbers = [[0 for i in range(3)] for j in range(3)]
```
```

The first value of 3 indicates the number of rows, and the second one the number of columns. The value of 0 in the Python example refers to the initial value this list will be set to.

In Python, the 2D list will appear as a table with three rows and three columns, all filled with zeros, as shown in the diagram below: In Java, the 2D array will only include the structure of the table, as there are no initial values provided:

![](bbox=[0.28, 0.6, 0.75, 0.73])

Manipulating 2D arrays or lists requires the use of two loops: the first one for the rows and the second one for the columns. When addressing one specific item in the array or list, this is done by using the name of the array or list followed by square brackets that include the row and column indices.

numbers [0] [2] refers to the element in the array numbers, located at the intersection of the first row with the third column.