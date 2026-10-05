# Fundamentals of the q Programming Language

Here we have elided the very top index of a matrix: a[:1] retrieves the items with index 1 from each item of the nonsingular list a.
The @ verb can also be used to index rows of the matrix:

```
@[a; 1]
5.7 -8.9 -3.2
```

Matrices of compatible shapes can be multiplied using the matrix multiplication verb mmu. Thus to multiply a by a transpose of b

```
d: a mmu flip b;
d
```

```
(73.92 23.54;-90.76 -23.31)
The inverse of a nonsingular matrix can be computed using inv:
inv d
```

```
(-0.05638399 -0.05694034;0.2195372 0.1788033)
```

Note for mmu and inv to work the matrix must have floating point entries. Thus the following will work:

```
(3 5 7f; 6 4 7f) mmu (3 2f; 12 2f; 5 2f)
whereas
(3 5 7; 6 4 7) mmu (3 2; 12 2; 5 2)


```

will fail with error 'length.
Dot product is supported through the $ operator:

```
a[@]$b[@]
51.24
```

We have demonstrated that we can implement basic linear algebra calculations within q in a very straightforward way. The provided commands can be extended by readers into more complex functions and solve more advanced problems.

# 1.7 LAUNCHING THE SESSION: ADDITIONAL OPTIONS

Let us consider this section with an overview of useful startup flags we can use starting our q session:

+   > q <additional options>

where a number of useful <additional options> is specified below.

Block writing

The option–b prevents the user, or the client launched by the user, to write into memory. If we launch a session with this option, any client which connects to this session cannot