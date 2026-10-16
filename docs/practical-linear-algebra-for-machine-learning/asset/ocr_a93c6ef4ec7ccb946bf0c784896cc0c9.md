# Chapter 4

# Matrix Operations

This chapter is dedicated to describe how we work with matrices and vectors. The discussion about vectors is straightforward and most of the content of this chapter is dedicated to matrix operations.

# 4.1. Introduction

Have you ever wondered why you need to know matrix operations? The answer is very simple: To work with matrices! Above all, the assumption is that you are familiar with the basic definitions (chapter 2). In this chapter, the most important matrix and vector operations that we need and frequently encounter in Machine Learning are are described.

# 4.2. Matrix Transpose

The transpose of a matrix is an operator which switches the row and column indices of the matrix. As a result, after transposing a matrix, we have a new matrix and is denoted as A^T. Therefore, the i^th row, j^th column elements of A are the j^th row and i^th column elements of A^T, respectively. Assume we show A^T with matrix B, then we have the following:

**B**_{j,i} = **A**_{i,j}

We can have the following example to clarify better:

$$\begin{bmatrix}2 & 3 & 1 \\ 3 & -4 & 2.2\end{bmatrix}^T = \begin{bmatrix}2 & 3 \\ 3 & -4 \\ 1 & -2.2\end{bmatrix}$$

Calculation of a matrix transpose is very easy with Python. For instance, you can try the following code:

```
# Use Numpy package
import numpy as np
```