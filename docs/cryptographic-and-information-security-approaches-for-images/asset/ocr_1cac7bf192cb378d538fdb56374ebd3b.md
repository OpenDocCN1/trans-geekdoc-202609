# 13.5 Implementation of Proposed Secure HEVC

Our secure system uses Integer DCT based watermarking to be used in HEVC. Therefore, the hardware implementation of Integer DCT and watermarking process are discussed in this section.

# 13.5.1 Implementation of Integer DCT Algorithm

In HEVC standard, 2-D integer transform is computed with the help of separable property where a 1-D horizontal transform (row wise) is calculated first, followed by a 1-D vertical (column wise) transform calculation. The process flow is shown in Figure 13.4.

1-D 8 × 8 Integer DCT matrix is defined as $C_f$ in Equation (13.9).

$C_f = \frac{1}{8} \begin{bmatrix} 8 & 8 & 8 & 8 & 8 & 8 & 8 & 8 \\ 12 & 10 & 6 & 3 & -3 & -6 & -10 & -12 \\ 8 & 4 & -4 & -8 & -8 & -4 & 4 & 8 \\ 10 & -3 & -12 & -6 & 6 & 12 & 3 & -10 \\ 8 & -8 & -8 & 8 & 8 & -8 & -8 & 8 \\ 6 & -12 & 3 & 10 & -10 & -3 & 12 & -6 \\ 4 & -8 & 8 & -4 & -4 & 8 & -8 & 4 \\ 3 & -6 & 10 & -12 & 12 & -10 & 6 & -3 \end{bmatrix}$ (13.9)

The above matrix is used for integer DCT calculation in our proposed system.

# 13.5.2 Butterfly Structure of 8 Point 1-D Forward DCT

1-D transform is evaluated via fast butterfly structure and is implemented with three different stages. Three stages data flow diagram of 1-D DCT algorithm is shown in Figure 13.5 (where $X$ is input vector and $Y$ denotes the output vector

![](bbox=[0.12, 0.7, 0.9, 0.88])

Figure 13.4 Implementation of 2-D DCT with separable property. (From Chen, Z. et al., J. Vis. Commun. Image Represent., 17, 264–290, 2006.)