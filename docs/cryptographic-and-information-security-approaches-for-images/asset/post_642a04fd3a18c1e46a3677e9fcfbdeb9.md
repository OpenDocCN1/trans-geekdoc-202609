
![](img/f4c3bcc9f5332d57a8ec85a75075f8da_383_0.png)

Figure 13.2 Frequency distribution of 8 × 8 sub block. (From Lam, E.Y. and Goodman, J.W., IEEE Trans. Image Process., 9, 1661–1666, 2000.)

In the case of a frame of the video (or still image), there exists an intra correlation between the neighboring values of the pixel. Each frame is divided into chunks of blocks with size 3 × 3, where every block contains an 8 × 8 sub block (total 64 pixels). This process generates total of nine blocks as shown in Figure 13.2. The value of AC coefficient of the central block (5th block) is predicted using the value of adjacent block DC coefficient. The watermark is embedded in low frequency values to have greater robustness. The common signal processing attacks and low pass filter tend to change the low frequency components much lesser than middle or high frequency components. In a sub block of 8 × 8 DCT, the leftmost corner coefficients are the low frequency values that carry a DC component and 5 AC components as shown in Figure 13.2.

The DC component is not used while applying a watermark because it would introduce visual distortion. Five topmost AC values AC(0,1), AC(0,2), AC(1,1), AC(2,0), and AC(1,0) of low frequencies are considered for watermarking.

### 13.4.1 Steps for Embedding of the Watermark

The input is uncompressed video and original watermark is an image. After completion of process, the watermarked video is generated. The watermark unit is part of the HEVC encoder.

- Step 1: The detection of scene change from video is determined using histogram difference as follows in Equation 13.1:

H = Σ_{k=1}^{N} Σ_{i=0,j=0}^{N} (P₁(i,j,k) − P₂(i,j,k+1))²   (13.1)

P₁ and P₂ are consecutive frames of a particular video. N is the total number of pixels in a frame.

- Step 2: An 8 bit original watermark is divided into various planes which are LSB to MSB (least significant to most significant bit) (total 8 planes) using bit plane slice method. Each plane is considered as a watermark.

- Step 3: These bit planes (which are known as watermark) are inserted in various frames for a particular scene. It has an edge that if any distortion happens then it would not hamper the whole watermark, but the other parts of the watermark are still able to be extracted from remaining frames.

- Step 4: Every frame from a scene is again further divided into blocks of size 8 × 8. For every block, Integer 2D DCT is computed which resulted in one DC and other 63 AC values.

- Step 5: The prediction of AC values for a middle block (5th block) is performed with surrounding blocks DC value as shown in Figure 13.3. The prediction process uses Equations 13.2 through 13.6 as follows:

AC_(0,1) = p1 * (DC4 − DC6)  (13.2)

AC_(1,0) = p1 * (DC2 − DC8)  (13.3)

AC_(0,2) = p2 * (DC4 − DC6 − 2 * DC5)  (13.4)

AC_(2,0) = p2 * (DC2 + DC8 − 2 * DC5)  (13.5)

AC_(1,1) = p3 * (DC1 + DC9 − DC3 − DC7)  (13.6)

where, p1 = 9/64, p2 = 1/32, p3 = 3/128.

The prediction process involves constants p1, p2, and p3 which carry the denominator value in terms of 2^N here N is a natural number. This has an advantage as it requires only shift operation, thereby avoiding the division requirement. The hardware implementation of shifter is simpler in comparison to divisor. The developed watermarking is based on integer arithmetic that is adapted to integer DCT. The algorithm outperforms the others in terms of computational complexity.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_384_0.png)

Figure 13.3 Prediction of central block with adjacent blocks. (From Küçük tunç, O. et al., Comput. Vis. Image Underst., 114, 125–134, 2010.)

Existing algorithms have floating point structure, which degrades the performance in real-time system.

- Step 6: The watermark in terms of Δ value is inserted in predicted AC values to generate new AC values as in Equation (13.7). The value of Δ ranges from 1 to 5. The particular value of Δ has to be chosen as per requirement of robustness against the quality of the frame.

If watermark bit = 1 then, set

$AC_i \ge AC_i' + \Delta$

else

$AC_i < AC_i' - \Delta$ (13.7)

- Step 7: Once the watermark is embedded, then Int IDCT (Integer Inverse DCT) of each block is executed to have watermark. Again all frames are accumulated to have secure embedded video.

### 13.4.2 Watermark Extraction Process

The retrieval of the algorithm is blind. The generated secure watermarked video is used in the extraction process. The output of the retrieving process is an extracted watermark.

- Step 1: The secure watermarked video uses scene change detection method again, the various frames are gathered from a particular scene.

- Step 2: Every frame which is extracted from a scene is separated into 8 × 8 blocks to calculate the Integer DCT for a block.

- Step 3: AC value of 5th block is predicted once again with DC values of the adjacent blocks as per Equations (13.2) through (13.6) which were used earlier in the embedding process.

- Step 4: The watermark bit is found by comparing the original AC value and estimated AC value as shown in (13.8).

If

$AC_i \ge AC_i'$

Watermark bit = 1

Else

Watermark bit = 0; (13.8)

- Step 5: Each watermark bit helps to have the bit planes.
- Step 6: The bit planes are combined to obtain the extracted watermark image.

## 13.5 Implementation of Proposed Secure HEVC

Our secure system uses Integer DCT based watermarking to be used in HEVC. Therefore, the hardware implementation of Integer DCT and watermarking process are discussed in this section.

### 13.5.1 Implementation of Integer DCT Algorithm

In HEVC standard, 2-D integer transform is computed with the help of separable property where a 1-D horizontal transform (row wise) is calculated first, followed by a 1-D vertical (column wise) transform calculation. The process flow is shown in Figure 13.4.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_386_0.png)

Figure 13.4 Implementation of 2-D DCT with separable property. (From Chen, Z. et al., J. Vis. Commun. Image Represent., 17, 264–290, 2006.)

1-D 8 × 8 Integer DCT matrix is defined as $C_f$ in Equation (13.9).

$C_f = \frac{1}{8} \begin{bmatrix} 8 & 8 & 8 & 8 & 8 & 8 & 8 & 8 \\ 12 & 10 & 6 & 3 & -3 & -6 & -10 & -12 \\ 8 & 4 & -4 & -8 & -8 & -4 & 4 & 8 \\ 10 & -3 & -12 & -6 & 6 & 12 & 3 & -10 \\ 8 & -8 & -8 & 8 & 8 & -8 & -8 & 8 \\ 6 & -12 & 3 & 10 & -10 & -3 & 12 & -6 \\ 4 & -8 & 8 & -4 & -4 & 8 & -8 & 4 \\ 3 & -6 & 10 & -12 & 12 & -10 & 6 & -3 \end{bmatrix}$ (13.9)

The above matrix is used for integer DCT calculation in our proposed system.

### 13.5.2 Butterfly Structure of 8 Point 1-D Forward DCT

1-D transform is evaluated via fast butterfly structure and is implemented with three different stages. Three-stage data flow diagram of 1-D DCT algorithm is shown in Figure 13.5 (where $X$ is input vector and $Y$ denotes the output vector with transformed values).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_387_0.png)

Figure 13.5 1-D Integer DCT module using butterfly diagram. (From Krishnan, T. and Oraintara, S., Fast and lossless implementation of the forward and inverse MDCT computation in MPEG audio coding. In Circuits and Systems, IEEE International Symposium on (ISCAS 2002), Vol. 2, 2002.)

The butterfly method is multiplier-less and can be implemented with integer arithmetic only. The different stages of structure are shown in Table 13.1. With the help of this stage-wise process, 8 × 8 block transform is implemented with simple operations such as additions/subtractions and shifts only. Here >>1 stands for right shift operation by one bit and >>2 stands for similarly right shift by 2 bits.

**Table 13.1 Butterfly Structure of Forward DCT**

| Stage 1 | Stage 2 | Stage 3 |
|---|---|---|
| a0 = X0 + X7 | b0 = a0 + a3 | Y0 = b0 + b1 |
| a1 = X1 + X6 | b1 = a1 + a2 | Y2 = b2 + (b3 >> 1) |
| a2 = X2 + X5 | b2 = a0 - a3 | Y4 = b0 - b1 |
| a3 = X3 + X4 | b3 = a1 - a2 | Y6 = (b2 >> 1) - b3 |
| a4 = X0 - X7 | b4 = a5 + a6 + ((a4 >> 1) + a4) | Y1 = b4 + (b7 >> 2) |
| a5 = X1 - X6 | b5 = a4 - a7 - ((a6 >> 1) + a6) | Y3 = b5 + (b6 >> 2) |
| a6 = X2 - X5 | b6 = a4 + a7 - ((a5 >> 1) + a5) | Y5 = b6 - (b5 >> 2) |
| a7 = X3 - X4 | b7 = a5 - a6 + ((a7 >> 1) + a7) | Y7 = -b7 + (b4 >> 2) |

Source: Liang, J. and Tran, T.D., IEEE Transactions on Signal Processing, 49, 3032–3044, 2001.
