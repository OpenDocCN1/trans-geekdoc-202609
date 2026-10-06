# Machine Learning for Social and Behavioral Research

| 7 1 4 1 |
| 8 1 5 1 |
| 9 2 6 2 |
| 10 3 6 1 |
| 11 5 6 1 |
| 12 2 7 1 |
| 13 3 7 1 |
| 14 3 8 1 |
| 15 5 8 1 |
| 16 2 9 1 |
| 17 5 9 1 |
| 18 2 10 1 |
| 19 3 10 3 |
| 20 4 10 1 |

Another way to store a sparse matrix is called sparse column (CSC) format, which also represents a matrix by three vectors. One vector contains all the nonzero values. The second vector contains the row index of the nonzero elements in the original matrix. The third vector is of the length of the number of columns +1. The first element is 0. Each subsequent value is equal to the previous values plus the number of nonzero values on that column. For the above example, the CSC representation is shown below. Different from the above method, the three vectors have different lengths.

```
i: 2 4 0 1 2 3 0 0 1 2 4 1 2 2 4 1 4 1 2 3
j: 0 2 3 6 7 8 11 13 15 17 20
v: 1 1 1 1 1 1 2 1 1 1 1 1 1 1 1 3 1
```

The advantage of using a sparse matrix becomes more obvious when a matrix is large. For example, for the teaching evaluation data, if we tokenize the comments, we have 27,939 (comments) by 18,216 (tokens/words) matrix. Less than 0.2% of the elements are not zero. If we store all the values using a matrix in R, it takes about 3.8 Gb of computer memory. However, using the CSC format to store the nonzero values only, it just takes about 18.1 Mb of memory, saving more than 95% of the computer memory.

# 11.5 Basic Analysis of the Teaching Comment Data

We now discuss how we can conduct some basic analysis of the teaching comment data. We first tokenize the comments into individual words (unigrams) as tokens. Overall, the 27,939 comments used a total of 1,223,454