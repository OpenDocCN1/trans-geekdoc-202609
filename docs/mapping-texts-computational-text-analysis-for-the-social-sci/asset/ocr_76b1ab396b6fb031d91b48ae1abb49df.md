# OUR DEAR FRIEND, THE MATRIX

We'll end this primer with the **matrix**,22 which is a collection of vectors stacked on top of each other or side by side. What's handy about a matrix is that we can work on several vectors simultaneously.

First, let's create an example matrix by building vectors and then “binding” them as rows.

```
vec1 <- c(1, 2, 4, 2)
vec2 <- c(3, 3, 3, 1)
vec3 <- c(4, 4, 4, 1)
mat <- rbind(vec1, vec2, vec3)
mat
```

```
       [,1] [,2] [,3] [,4]
vec1    1    2    4    2
vec2    3    3    3    1
vec3    4    4    4    1
```

We'll often need to **transpose** a matrix, which tips-and-flips it, so the rows become the columns and vice versa:

```
t(mat)
```

```
      vec1 vec2 vec3
[1,]    1    3    4
[2,]    2    3    4
[3,]    4    3    4
[4,]    2    1    1
```

A matrix is a mathematical object like any other, which means we can also do arithmetic with them, but again we’ll need to work with _all the numbers_ and keep track of their positions in our matrix. Let’s create two small matrices and add them.

```
mat1 <- matrix(c(1:4), ncol = 2)
mat2 <- matrix(c(5:8), ncol = 2)
mat1 + mat2
```

```
      [,1] [,2]        [,1] [,2]        [,1] [,2]
[1,]    1    3   +   [1,]    5    7   =   [1,]    6   10
[2,]    2    4       [2,]    6    8       [2,]    8   12
```

We added the numbers in the corresponding row-column position (i.e., cell) in each matrix. What happens if we add a scalar to our matrix? Every cell increases by the amount of that single number.

This gets more complicated when the matrices are not the same shape. We cannot add or subtract them, but we can multiply matrices of differing shapes. **Matrix multiplication** is a little different than regular multiplication, and instead of using * in R , it requires a particular

> 22 Matrix comes from Latin for womb or mother: “I have ... defined a ‘Matrix’ as a rectangular array of terms, out of which different systems of determinants may be engendered as from the womb of a common parent” (Sylvester 1851:247).