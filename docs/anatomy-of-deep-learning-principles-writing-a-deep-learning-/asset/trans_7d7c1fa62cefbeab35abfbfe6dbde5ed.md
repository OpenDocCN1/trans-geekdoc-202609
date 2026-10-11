

## 6.4 Fast Convolution Based on Coordinate Indexing

Replacing nested loops with matrix operations can accelerate convolution computation, but multiple loops are still required to copy data during flattening and reshaping. This section introduces fast convolution based on indexing: by rapidly constructing index arrays and then building flattened or reshaped tensors, convolution efficiency can be further improved.

The convolution operation moves the kernel with the stride as the step size, in a "top-to-bottom, left-to-right" order. At each position, the weighted sum of corresponding elements is computed between the kernel and the corresponding data tensor window (multi-channel data block) to obtain each element of the output feature map.

Previously, the original data tensor was flattened into a matrix by sequentially flattening the multi-channel data blocks of the original tensor into row vectors, following the "top-to-bottom, left-to-right" order of the convolution weighted sum.

If the stride is inconsistent with the kernel size (height and width), the data blocks computed sequentially with the kernel for the weighted sum will overlap. Arranging these data blocks sorted by computation order yields a new tensor with non-overlapping data blocks.

For example, for the following 4×4 tensor with 1 sample and 1 channel:

$$
\begin{bmatrix}
x_{00} & x_{01} & x_{02} & x_{03} \\
x_{10} & x_{11} & x_{12} & x_{13} \\
x_{20} & x_{21} & x_{22} & x_{23} \\
x_{30} & x_{31} & x_{32} & x_{33}
\end{bmatrix}
$$

If the kernel is 2×2, the convolution operation essentially performs a weighted sum between the kernel and the data blocks arranged as follows:

$$
\begin{bmatrix}
\begin{bmatrix} x_{00} & x_{01} \\ x_{10} & x_{11} \end{bmatrix} &
\begin{bmatrix} x_{01} & x_{02} \\ x_{11} & x_{12} \end{bmatrix} &
\begin{bmatrix} x_{02} & x_{03} \\ x_{13} & x_{13} \end{bmatrix} \\
& & \\
\begin{bmatrix} x_{10} & x_{11} \\ x_{20} & x_{21} \end{bmatrix} &
\begin{bmatrix} x_{11} & x_{12} \\ x_{21} & x_{22} \end{bmatrix} &
\begin{bmatrix} x_{12} & x_{13} \\ x_{23} & x_{23} \end{bmatrix} \\
& & \\
\begin{bmatrix} x_{20} & x_{21} \\ x_{30} & x_{31} \end{bmatrix} &
\begin{bmatrix} x_{21} & x_{22} \\ x_{31} & x_{32} \end{bmatrix} &
\begin{bmatrix} x_{22} & x_{23} \\ x_{33} & x_{33} \end{bmatrix}
\end{bmatrix}
$$

Flattening each data block (identical in size to the kernel) into a row vector yields the following row vector matrix:

$$
\begin{bmatrix}
x_{00} & x_{01} & x_{10} & x_{11} \\
x_{01} & x_{02} & x_{11} & x_{12} \\
x_{02} & x_{03} & x_{13} & x_{13} \\
& & & \\
x_{10} & x_{11} & x_{20} & x_{21} \\
x_{11} & x_{12} & x_{21} & x_{22} \\
x_{12} & x_{13} & x_{23} & x_{23} \\
& & & \\
x_{20} & x_{21} & x_{30} & x_{31} \\
x_{21} & x_{22} & x_{31} & x_{32} \\
x_{22} & x_{23} & x_{33} & x_{33}
\end{bmatrix}
$$

If there are multiple channels, each data block is a 3D tensor (cuboid), and the process is similar. For example, a 2-channel tensor:

$$
\begin{bmatrix}
x_{000} & x_{001} & x_{002} & x_{003} \\
x_{010} & x_{011} & x_{012} & x_{013} \\
x_{020} & x_{021} & x_{022} & x_{023} \\
x_{030} & x_{031} & x_{032} & x_{033}
\end{bmatrix}
$$

and

$$
\begin{bmatrix}
x_{100} & x_{101} & x_{102} & x_{103} \\
x_{110} & x_{111} & x_{112} & x_{113} \\
x_{120} & x_{121} & x_{122} & x_{123} \\
x_{130} & x_{131} & x_{132} & x_{133}
\end{bmatrix}
$$

According to the convolution computation process, these data blocks are arranged in order as:

**Figure 6-47 Each data block in the convolution computation is a 3D data block of shape 2×2×2 composed of 2×2 2-channel matrices**

That is, the matrix blocks at corresponding positions of the following two matrices constitute a data block:

$$
\begin{bmatrix}
\begin{bmatrix} x_{000} & x_{001} \\ x_{010} & x_{011} \end{bmatrix} &
\begin{bmatrix} x_{001} & x_{002} \\ x_{011} & x_{012} \end{bmatrix} &
\begin{bmatrix} x_{002} & x_{003} \\ x_{013} & x_{013} \end{bmatrix} \\
& & \\
\begin{bmatrix} x_{010} & x_{011} \\ x_{020} & x_{021} \end{bmatrix} &
\begin{bmatrix} x_{011} & x_{012} \\ x_{021} & x_{022} \end{bmatrix} &
\begin{bmatrix} x_{012} & x_{013} \\ x_{023} & x_{023} \end{bmatrix} \\
& & \\
\begin{bmatrix} x_{020} & x_{021} \\ x_{030} & x_{031} \end{bmatrix} &
\begin{bmatrix} x_{021} & x_{022} \\ x_{031} & x_{032} \end{bmatrix} &
\begin{bmatrix} x_{022} & x_{023} \\ x_{033} & x_{033} \end{bmatrix}
\end{bmatrix}
$$

and

$$
\begin{bmatrix}
\begin{bmatrix} x_{100} & x_{101} \\ x_{110} & x_{111} \end{bmatrix} &
\begin{bmatrix} x_{101} & x_{102} \\ x_{111} & x_{112} \end{bmatrix} &
\begin{bmatrix} x_{102} & x_{103} \\ x_{113} & x_{113} \end{bmatrix} \\
& & \\
\begin{bmatrix} x_{110} & x_{111} \\ x_{120} & x_{121} \end{bmatrix} &
\begin{bmatrix} x_{111} & x_{112} \\ x_{121} & x_{122} \end{bmatrix} &
\begin{bmatrix} x_{112} & x_{113} \\ x_{123} & x_{123} \end{bmatrix} \\
& & \\
\begin{bmatrix} x_{120} & x_{121} \\ x_{130} & x_{131} \end{bmatrix} &
\begin{bmatrix} x_{121} & x_{122} \\ x_{131} & x_{132} \end{bmatrix} &
\begin{bmatrix} x_{122} & x_{123} \\ x_{133} & x_{133} \end{bmatrix}
\end{bmatrix}
$$

Flattening each data block into a row vector yields:

$$
\begin{bmatrix}
x_{000} & x_{001} & x_{010} & x_{011} & x_{100} & x_{101} & x_{110} & x_{111} \\
x_{001} & x_{002} & x_{011} & x_{012} & x_{101} & x_{102} & x_{111} & x_{112} \\
x_{002} & x_{003} & x_{013} & x_{013} & x_{102} & x_{103} & x_{113} & x_{113} \\
& & & & & & & \\
x_{010} & x_{011} & x_{020} & x_{021} & x_{110} & x_{111} & x_{120} & x_{121} \\
x_{011} & x_{012} & x_{021} & x_{022} & x_{111} & x_{112} & x_{121} & x_{122} \\
x_{012} & x_{013} & x_{023} & x_{023} & x_{112} & x_{113} & x_{123} & x_{123} \\
& & & & & & & \\
x_{020} & x_{021} & x_{030} & x_{031} & x_{120} & x_{121} & x_{130} & x_{131} \\
x_{021} & x_{022} & x_{031} & x_{032} & x_{121} & x_{122} & x_{131} & x_{132} \\
x_{022} & x_{023} & x_{033} & x_{033} & x_{122} & x_{123} & x_{133} & x_{133}
\end{bmatrix}
$$

All these data blocks, identical in size to the kernel, are arranged in the "top-to-bottom, left-to-right" computation order to form an expanded tensor, whose data originates from the original data tensor. From the data subscripts of the expanded tensor shown in Figure 6-47, one can see which subscripts in the original tensor they originate from. In other words, as long as the subscript of each data element in the expanded data tensor within the original data tensor is known, these data can be generated from the original data tensor.

First, look at the single-channel case; removing the letter 'x' clearly reveals the subscripts of the expanded tensor elements in the original tensor:

$$
\begin{bmatrix}
\begin{bmatrix} 00 & 01 \\ 10 & 11 \end{bmatrix} &
\begin{bmatrix} 01 & 02 \\ 11 & 12 \end{bmatrix} &
\begin{bmatrix} 02 & 03 \\ 13 & 13 \end{bmatrix} \\
& & \\
\begin{bmatrix} 10 & 11 \\ 20 & 21 \end{bmatrix} &
\begin{bmatrix} 11 & 12 \\ 21 & 22 \end{bmatrix} &
\begin{bmatrix} 12 & 13 \\ 23 & 23 \end{bmatrix} \\
& & \\
\begin{bmatrix} 20 & 21 \\ 30 & 31 \end{bmatrix} &
\begin{bmatrix} 21 & 22 \\ 31 & 32 \end{bmatrix} &
\begin{bmatrix} 22 & 23 \\ 33 & 33 \end{bmatrix}
\end{bmatrix}
$$

Simply indexing the original data tensor with these subscripts yields the tensor composed of these data blocks.

Observing these subscripts reveals that all subscripts can be obtained by starting from the initial top-left subscript and moving with the stride as the step size in a "top-to-bottom, left-to-right" manner. The top-left subscripts are:

$$
\begin{bmatrix} 00 & 01 \\ 10 & 11 \end{bmatrix}
$$

Moving "left-to-right" by one stride each time (i.e., column subscript +1) yields the three data block subscripts in the first row:

$$
\begin{bmatrix}
\begin{bmatrix} 00 & 01 \\ 10 & 11 \end{bmatrix} &
\begin{bmatrix} 01 & 02 \\ 11 & 12 \end{bmatrix} &
\begin{bmatrix} 02 & 03 \\ 13 & 13 \end{bmatrix}
\end{bmatrix}
$$

Moving the first row "top-to-bottom" by stride (i.e., increasing row subscripts) sequentially yields the subscripts of all data blocks in the subsequent 2 rows.

For the row and column subscripts of the top-left data block:

$$
\begin{bmatrix} 00 & 01 \\ 10 & 11 \end{bmatrix}
$$

The row and column subscripts are `i=0,1` and `j=0,1` respectively. As shown in Figure 6-48:

**Figure 6-48 Row and column subscripts of the top-left data block**

Therefore, the row and column subscript combinations `[(0,0),(0,1),(1,0),(1,1)]` can be obtained from the row subscript vector `[0,0,1,1]` and column subscript vector `[0,1,0,1]` of the 4 elements in the top-left data block. Similarly, for an arbitrary `kH`×`kW` kernel, the row and column subscripts `i0` and `j0` corresponding to the elements of the top-left data block in the original tensor can be obtained using Python code:

```python
# 此处原文缺失代码示例
```

