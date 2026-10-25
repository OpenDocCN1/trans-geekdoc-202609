# Chapter 14

# Matrix Decompositions

Many complex matrix operations cannot be solved efficiently or with stability using the limited precision of computers. Matrix decompositions are methods that reduce a matrix into constituent parts that make it easier to calculate more complex matrix operations. Matrix decomposition methods, also called matrix factorization methods, are a foundation of linear algebra in computers, even for basic operations such as solving systems of linear equations, calculating the inverse, and calculating the determinant of a matrix. In this tutorial, you will discover matrix decompositions and how to calculate them in Python. After completing this tutorial, you will know:

+   - What a matrix decomposition is and why these types of operations are important.
+   - How to calculate an LU and QR matrix decompositions in Python.
+   - How to calculate a Cholesky matrix decomposition in Python.

Let's get started.

# 14.1 Tutorial Overview

This tutorial is divided into 3 parts; they are:

+   1. What is a Matrix Decomposition
+   2. LU Decomposition
+   3. QR Decomposition
+   4. Cholesky Decomposition

# 14.2 What is a Matrix Decomposition

A matrix decomposition is a way of reducing a matrix into its constituent parts. It is an approach that can simplify more complex matrix operations that can be performed on the decomposed matrix rather than on the original matrix itself. A common analogy for matrix decomposition is the factoring of numbers, such as the factoring of 10 into 2 × 5. For this reason, matrix decomposition is also called matrix factorization. Like factoring real values, there are