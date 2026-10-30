
is done using the permutation-based scrambling technique for providing better security. Simultaneously, the authors used optimization-based encryption technique for authenticating the watermarked image. However, the time complexity of the developed method can be reduced.

In [18], chaotic encryption-based watermarking is reported. In this method, text and image watermarks are embedded into the desired sub-bands of the host image using DWT-SVD. It seems that values of the peak signal-to-noise ratio (PSNR) are quite low, which accounts for poor perceptual invisibility. HT-RDWT-SVD-based watermarking is described in [5]. In this methodology, a cover image is transformed using HT-RDWT-SVD, while a watermark image is transformed using RDWT-SVD. Results clearly show that this scheme provides better security and authenticity to the watermarked image by encryption. Using fuzzy logic, authors in [19] have utilized NSCT-RDWT-SVD combination to embed watermark images into the cover image. Fuzzy logic is used to determine the optimal scaling factor in this method. This scheme depicts poor robustness toward filtering attacks.

De-noising convolutional neural network (DnCNN)-based watermarking technique is developed in [20] where lifting wavelet transform (LWT), along with Hessenberg decomposition and redundant singular value decomposition (RSVD), is employed for embedding the watermark. DnCNN is applied to strengthen robustness against attacks, whereas encryption succeeded by compression is also done on the watermarked image to achieve better results. However, robustness against geometric attacks is not reported. Curvelet transform, along with RDWT, is used in [21] to embed the watermark. In this methodology the scrambled watermark is embedded along with Pseudo Noise (PN) sequences in subbands of the host image. Robustness against filtering and scaling attacks is the main shortcoming of the developed method.

Error correction codes (ECC) and DWT are used for watermark embedding [22]. Dual embedding of the watermark is performed to protect sensitive medical information, while a comparative analysis among various ECC is also conducted. Embedding of the watermark using Walsh Hadamard transform (WHT) is investigated in [23]. In this approach, WHT is applied over a segmented block cover image, while shuffling of bit information is done to achieve security. However, robustness is weak against median filter attack.

The concept of deep learning is utilized in [24], where robustness is significantly improved. The concatenation principle is used for the embedding process, while the block-level transposed convolution technique is employed in the extraction process. However, the imperceptibility attained is lesser in this technique. Fusion-based image watermarking using NSCT is briefed in [25], where two medical images are fused. A fused cover image is used for the embedding process in which image and text watermarks are concurrently embedded for smart healthcare applications.

A similar technique that uses principal component analysis (PCA) and RDWT is reported in [26], where principal components are used for embedding and extraction processes. A review of various image watermarking techniques for smart healthcare system is discussed in [27]. In this article, open issues and challenges are elaborated on telemedicine applications. The presented review regarding different techniques inspires us to contribute a new watermarking technique that meets research gaps. There are numerous potential research issues that need to be focused, such as better robustness and perceptual invisibility, capacity, etc. Thus, by developing this novel technique, digital image copyright protection can be attained effectively with better attributes.

## 6.3 PROPOSED WATERMARKING TECHNIQUE

Watermark embedding and extraction techniques are presented in this section. Initially, HT decomposes a cover image into reflectance and illumination components. Further multiresolution analysis is attained by decomposing the reflectance component using RDWT. Low high (LH) subband is chosen to maintain an adequate balance between robustness and perceptual invisibility. MSVD is applied to this LH subband to attain better imperceptibility. Similarly, RDWT-MSVD transforms are applied over the watermark image. The selection of the optimal scaling factor yields the watermarked image. Embedding and extraction watermark procedures are depicted in Figure 6.1(a, b).

![](img/6e4271af21d9a195003ab8711aa79d27_131_0.png)

(a)

Figure 6.1 Watermarking technique procedure (a) embedding.

![](img/6e4271af21d9a195003ab8711aa79d27_132_0.png)

(b)

Figure 6.1 (Continued) Watermarking technique procedure (b) extraction.

### 6.3.1 Embedding technique

- HT of the cover image ‘C’ is computed, yielding ‘C_R’ as the reflectance component whereas ‘C_I’ as an illumination component.
- ‘C_R’ is decomposed using RDWT resulting in four subbands.
  C_R --RDWT--> [C_RLL, C_RHL, C_RLH, C_RHH] (6.1)
- MSVD of ‘C_RLH’ subband is computed as:
  C_RLH --MSVD--> [X1, U1] (6.2)
- RDWT is performed over the watermark image ‘W_mk’.
  W_mk --RDWT--> [W_mkLL, W_mkHL, W_mkLH, W_mkHH] (6.3)
- MSVD for ‘W_mkLH’ is computed, which results in [X2, U2].
  W_mkLH --MSVD--> [X2, U2] (6.4)
- Watermark is embedded in accordance with Eq. (6.5):
  X3 = X1 + β° X2 (6.5)
  where ‘β’ is the scaling factor.
- Inverse MSVD, RDWT, HT transformation results in watermarked image ‘W_I’.

### 6.3.2 Extraction technique

- HT of ‘W_I’ watermarked image is evaluated, which results in ‘W_IR’ as the reflectance component, whereas ‘W_II’ as an illumination component.
- RDWT is applied over ‘W_IR’ as:
  $$W_{IR} \xrightarrow{RDWT} [W_{IRLL}, W_{IRHL}, W_{IRLH}, W_{IRHH}] \tag{6.6}$$
- MSVD coefficients of ‘W_IRLH’ are evaluated according to Eq. (6.7):
  $$W_{IRLH} \xrightarrow{MSVD} [X_4, U_4] \tag{6.7}$$
- Extraction process is done in accordance with Eq. (6.8):
  $$X_5 = (X_4 - X_1)/\beta \tag{6.8}$$
- Inverse MSVD and RDWT of ‘X_5’ is computed to retrieve the watermark image ‘W_mk’.

## 6.4 SIMULATION RESULTS

The proposed watermarking technique in this chapter is implemented using ‘MATLAB’. Several cover images, which comprise standard and medical images [28, 29] of size 512 × 512, are taken, while a watermark image of size 512 × 512 is chosen. Cover images are represented in Figure 6.2(a), and a watermark image in Figure 6.2(b). The value of ‘β’ is selected as 0.1 for experimental analysis. Weighted peak signal-to-noise ratio (WPSNR) [30, 31], PSNR, structural similarity index (SSIM), and normalized correlation (NC) [31] metrics are evaluated for analyzing the proposed technique imperceptibility and robustness. The values of these metrics are tabulated in Table 6.1, which clearly emphasizes performance of the proposed technique under no attacks. 53.22179 dB and 66.17175 dB are the mean values of PSNR and WPSNR, respectively, while NC and SSIM values are near to unity.

Proposed technique robustness is analyzed under several attacks such as sharpening, affine, compression, etc. Figure 6.3 illustrates the ‘Airplane’ watermarked image subjected to different attacks and corresponding retrieved watermark images. Proposed technique is robust toward attacks, as the visual quality of extracted watermark images is better. In Tables 6.2, 6.3, 6.4, and 6.5 NC values are computed for the proposed technique under different attacks.

![](img/6e4271af21d9a195003ab8711aa79d27_134_0.png)

![](img/6e4271af21d9a195003ab8711aa79d27_134_1.png)

Figure 6.2 (a) Several cover images (b) Watermark image.

Table 6.1 Performance metric values for the proposed scheme

| Image | SSIM | PSNR (dB) | WPSNR (dB) | NC |
|---|---|---|---|---|
| Lena | 0.9986 | 55.5431 | 64.9250 | 0.9996 |
| Cameraman | 0.9943 | 50.6895 | 66.5252 | 0.9989 |
| Peppers | 0.9961 | 51.6619 | 67.1621 | 0.9994 |
| Boat | 0.9961 | 51.4885 | 66.9485 | 0.9994 |
| Man | 0.9972 | 52.5542 | 67.9080 | 0.9994 |
| Airplane | 0.9980 | 54.7573 | 63.5201 | 0.9996 |
| Lung | 0.9924 | 50.1003 | 66.9217 | 0.9958 |
| Knee | 0.9959 | 52.9325 | 66.0630 | 0.9991 |
| Elbow | 0.9987 | 57.2672 | 66.0620 | 0.9996 |
| Brain | 0.9980 | 55.2234 | 65.6819 | 0.9985 |
