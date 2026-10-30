
A CT scan and MRI image. The fused image is then concealed with the MAC address of the sender’s system and image mark using a combination of DWT, Fisher-Yates permutation, firefly optimization, and dual tree complex wavelet transform (DTCWT)-SVD. Also, the patient’s report is hidden in the marked image for better embedding payload, maintaining high visual quality. Finally, the marked image is secured using a low-cost encryption method. Compared with other schemes [11–13], this framework provides a better solution to ensure higher security for privacy preservation.

Singh et al. developed a secure watermarking model for copyright protection of digital images [14]. Initially, a series of transforms including lifting wavelet transform (LWT), Hessenberg decomposition (HD), and randomized SVD (RSVD) is applied on the carrier image. Further, the mark is concealed inside the singular values of the carrier image using a suitable embedding factor. Finally, the marked image is encrypted and then compressed for secure transmission with reduced bandwidth demand. During extraction, a convolutional neural network (CNN)-based denoising model is applied on the extracted mark for improved robustness. Anand et al. proposed a secure watermarking method to authenticate the digital healthcare records [15]. The proposed work implemented wavelet-based watermarking to generate a dual watermark by hiding the encoded MAC address into the mark image. The generated mark is hidden in the IWT-Schur-RSVD coefficients of the carrier image using an optimized scaling factor. Fuzzy inference system is used to maintain a balance between robustness and visual quality by computing the optimal value of the scaling factor. In the final stage, chaotic encryption is used to cipher the marked image to improve security while transmitting over the open network. A blind watermarking method based on Diffie-Hellman and Number Theoretic Transform (NTT) is proposed by Soualmi et al. for protection of medical records [16]. Initially, the mark is encrypted using Diffie-Hellman for better security of this scheme. In the embedding phase, the host image is transformed using NTT, and the resultant coefficients are altered to embed the encrypted mark. The performance of this scheme offers better computational complexity and visual quality in comparison to many existing methods.

Yan et al. developed a multiple watermarking technique to verify the integrity and authenticity of the digital medical content [17]. The proposed work blended watermarking with encryption and compression for better security and compression performance. An encrypted image mark is hidden in the ROI of the carrier image using fragile watermarking. Further, a compressed text mark is placed in the RONI using DWT-SVD and brain storm optimization (BSO) to improve invisibility and robustness. The robustness analysis of this work inferred better results when compared with similar techniques [15, 18, 19]. A blind and robust watermarking method for medical applications is presented by Nguyen-Thanh and Le-Tien [20]. The authors transformed the cover image using Scale Invariant Feature Transform (SIFT) and applied even-odd quantization to conceal the secret information. Further, the security is improved by using a key-based embedding and extraction process. Another robust watermarking-encryption-based framework for e-health applications is presented by Soualmi et al. [21]. In the pre-processing stage, both the cover and image mark are ciphered by XORing with chaotic sequence. Further, the cyphered mark is hidden in the Schur coefficient of the encrypted host image. At the receiver end, the mark is blindly extracted from the received image. The proposed work focused on high security; however, the embedding capacity can be further improved.

Vaidya proposed a robust watermarking solution for healthcare records in wavelet domain [22]. Initially, two-level decomposition using LWT and DWT is applied on the host image. Further, the high frequency coefficient of the host image is altered using adaptive scaling factors to conceal the fingerprint image. The adaptive scaling factors are computed using Local Binary Pattern, which ensures high robustness with minimum visual distortion. The author also enhanced the security by encrypting the marked image using Arnold transform.

## 1.3 PRELIMINARY CONCEPTS

### 1.3.1 Non-Subsampled Contourlet Transform (NSCT)

Although wavelet transforms offer multiresolution and spatio-frequency properties, these transforms suffer from the issues of poor directionality, shift variance, and poor capturing of edge information [23]. To overcome these issues, contourlet transform (CT) is used, having multiresolution and multidirectional properties. However, it uses up- and down-sampling processes, which cause a shift variant problem [23].

Based on CT, NSCT is capable of efficient representation of any image with better directionality, with edge and smooth contour information. It holds shift invariant property, along with all the advantages of CT. The construction of NSCT includes the use of non-subsampled pyramid filter bank (NSPFB) and non-subsampled directional filter bank (NSDFB). NSPFB ensures multi-scalability, and NSDFB provides better directional information. Both filter banks eliminate the operation of up- and down-sampling, confirming shift invariant property [23].

Initially, the input image is decomposed with NSPFB, which results in high- and low-pass sub-bands, with the same size of the input image. Further, NSPFB is applied on a low-pass coefficient to achieve multi-scalability. The result has ‘l+1’ count of sub-images, where ‘l’ represents the decomposition level. Here, ‘l’ is the count of high-pass coefficients, and the rest is the low-pass coefficient. The condition for perfect reconstruction is given as [24],

Z_L(l)×R_L(l)+Z_H(l)×R_H(l)=1 (1.1)

![](img/6e4271af21d9a195003ab8711aa79d27_17_0.png)

Figure 1.1 Non-subsampled contourlet transform.

Here, Z_L(l) and R_L(l) denote the decomposed and reconstructed low-pass filters, respectively. Also, decomposed and reconstructed high-pass filters are denoted by Z_H(l) and R_H(l).

In the next stage, NSDFB is implemented on a high-pass sub-band with ‘d’ level directionality. It results in total 2^d directional sub-bands whose size is the same as that of the input image; it provides more precise directional information. The procedure of NSCT decomposition of an input image is shown in Figure 1.1 [23].

### 1.3.2 Hessenberg Decomposition (HD)

In linear algebra, the matrix decompositions of square matrix are done with the help of HD [25]. It decomposes the square matrix, ‘A’ of size ‘m × m’ into the product of three matrices, which is mentioned in Eq. (1.2).

PHP^T = HD(A)
(1.2)

Where, ‘P’ is indicated as orthogonal matrix and ‘H’ is an upper Hessenberg matrix, and h_{i,j}=0, where i > j + 1.
The mathematical computation of HD is obtained with the help of Householder matrices. The mathematical equation of Householder matrix, ‘Q’ is described below.
Q = (I_n - 2 μ μ^T) / μ^T μ
(1.3)
Where, ‘I_n’ is denoted as identity matrix with dimension ‘m × m’, and ‘Q’ is an orthogonal matrix. ‘μ’ is termed as non-zero vector.

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

### 1.3.3 Multiresolution Singular Value Decomposition (MSVD)

MSVD is a linear complexity transform that uses SVD in place of low- and high-pass filters in wavelet transform [26]. The procedure of calculating MSVD coefficients of the input image, ‘E’ of size p × q, as discussed in Figure 1.2, includes the following processes [26]:

- a. Initially, the input image, E, is segmented into non-overlapping blocks. Size of each block is m × n.
- b. Rearrange each block into separate vector of size mn × 1. Further, the resultant vectors are stacked as new columns to generate a matrix, Ē, of size mn × pq.
- c. Furthermore, corresponding centered matrix, Ē₁, is calculated.
- d. In the next step, the scatter matrix, S, is computed using the following equation:

```
S = Ē₁ × Ē₁ᵀ (1.7)
```
