For example, pixel value of matrix, ‘A’ with size of 4 × 4 is obtained from input image, is presented below.

```
A = 
[104.6010 42.2519 56.5573 106.6036
100.1120 43.6523 63.5101 141.4542
83.2060 81.4629 45.2070 118.1840
24.4301 56.1044 83.4849 93.2716] (1.4)
```

Where, HD decomposed the matrix, ‘A’ into two matrices such as ‘P’ and ‘H’, which are mentioned below.

```
P = 
[1 0 0 0
0 -0.7559 0.3109 0.5762
0 -0.6282 -0.0964 -0.7720
0 -0.1845 -0.9455 0.2682] (1.5)
```

```
H = 
[104.6010 -89.5251 -91.7719 12.3475
-132.4481 167.6635 164.2178 -36.9402
0 86.3894 43.9222 6.9409
0 0 -23.9644 -27.4539] (1.6)
```

We have observed that 167.6635 is the highest energy element of Hessenberg matrix, ‘H’, which can be used to insert the mark data.

# 1.3.3 Multiresolution Singular Value Decomposition (MSVD)

MSVD is a linear complexity transform that uses SVD in place of low- and high-pass filters in wavelet transform [26]. The procedure of calculating MSVD coefficients of the input image, ‘E’ of size p × q, as discussed in Figure 1.2, includes the following processes [26]:

+   a. Initially, the input image, E, is segmented into non-overlapping blocks. Size of each block is m × n.
+   
+   b. Rearrange each block into separate vector of size mn × 1. Further, the resultant vectors are stacked as new columns to generate a matrix, Ē, of size mn × pq.
+   
+   c. Furthermore, corresponding centered matrix, Ē₁, is calculated.
+   
+   d. In the next step, the scatter matrix, S, is computed using the following equation:

```
S = Ē₁ × Ē₁ᵀ (1.7)
```