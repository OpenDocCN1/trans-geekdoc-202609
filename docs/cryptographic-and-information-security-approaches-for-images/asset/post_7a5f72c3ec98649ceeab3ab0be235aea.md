
![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_0.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_1.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_2.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_3.png)

(a)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_4.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_5.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_6.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_254_7.png)

(b)

Figure 8.7 Results of CS based encryption and decryption processes using DCT basis matrix. (From Nagesh, P. and Li, B., Int. Conf. Acoust. Speech Signal Process., 1261–1264, 2009; Singh, T. and Singh, M., US Patent No. 8,761,525, US Patent and Trademark Office, Washington, DC, 2014.) (a) Encrypted color image using different secret keys (A) Secret key k = 88320 (B) Secret key k = 118272 (C) Secret key k = 147456 (D) Secret key k = 177408 (b) Decrypted image using different secret keys (A) Secret key k = 88320 (B) Secret key k = 118272 (C) Secret key k = 147456 (D) Secret key k = 177408.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_0.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_1.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_2.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_3.png)

(a)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_4.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_5.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_6.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_255_7.png)

(b)

Figure 8.8 Results of CS based encryption and decryption processes using DFT basis matrix (a) Encrypted color image using different secret keys (A) Secret key k = 88320 (B) Secret key k = 118272 (C) Secret key k = 147456 (D) Secret key k = 177408 (b) Decrypted image using different secret keys (A) Secret key k = 88320 (B) Secret key k = 118272 (C) Secret key k = 147456 (D) Secret key k = 177408.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_0.png)

(A)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_1.png)

(B)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_2.png)

(C)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_3.png)

(D)

(a)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_4.png)

(A)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_5.png)

(B)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_6.png)

(C)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_256_7.png)

(D)

(b)

Figure 8.9 Results of CS based encryption and decryption processes using DWT basis matrix (a) Encrypted color image using different secret keys (A) Secret key k = 88320 (B) Secret key k = 118272 (C) Secret key k = 147456 (D) Secret key k = 177408 (b) Decrypted image using different secret keys (A) Secret key k = 88320 (B) Secret key k = 118272 (C) Secret key k = 147456 (D) Secret key k = 177408.

## Table 8.4 Quality Measures Value for CS Based Encryption and Decryption Processes for Goldhill Images

| Secret Key k (M×N×C) | Using DCT Basis Matrix [8] [52] PSNR (dB) | SSIM | Using DFT Basis Matrix PSNR (dB) | SSIM | Using DWT Basis Matrix PSNR (dB) | SSIM | Compression Ratio (CR) |
|---|---|---|---|---|---|---|---|
| 88320 (115×256×3) | 36.12 | 0.7756 | 37.05 | 0.8005 | 36.81 | 0.8011 | 2.22 |
| 118272 (154×256×3) | 36.73 | 0.8233 | 37.95 | 0.8728 | 37.56 | 0.8522 | 1.66 |
| 147456 (192×256×3) | 37.27 | 0.8639 | 38.40 | 0.8969 | 38.38 | 0.8937 | 1.33 |
| 177408 (231×256×3) | 37.75 | 0.8919 | 38.90 | 0.9218 | 39.18 | 0.9260 | 1.11 |

After obtaining results of CS based encryption and decryption processes for the Goldhill image, below observations are made:

- 1. The experiment results show that CS based encryption and decryption processes equally performed well for standard images using DCT basis matrix, DFT basis matrix, and DWT basis matrix.
- 2. The results of DFT and DWT basis matrices are better than results of the DCT basis matrix. This indicates that the performance of the CS encryption and decryption processes using DFT and DWT are better than the existing process using DCT [8,52].
- 3. The quality of decrypted image increases with size of secret key k.
- 4. The visual quality of decrypted images shows that some loss has taken place (based on the histogram of decrypted images). This indicates that this approach is lossy.
- 5. The compression ratio up to 2.22 is achieved using this CS based approach.

## 8.4.4 Performance Analysis of CS Based Encryption and Decryption Processes for Landsat Satellite Images

In this section, different sizes of encrypted Landsat satellite images are generated using different sizes of measurement matrix as secret keys. The decryption of these images is performed using the same measurement matrix which is used in encryption and CS recovery OMP algorithm. Figures 8.10 through 8.12 shows the encrypted images, decrypted images, and histograms of decrypted images when DCT, DFT and DWT coefficients are used. The quality measures obtained for the Landsat satellite image using CS based encryption and decryption processes are tabulated in Table 8.5.

After obtaining the results of CS based encryption and decryption processes for the Landsat satellite image, the below observation on results are made.

- 1. The experiment results show that CS based encryption and decryption processes using DCT and DWT basis matrices have not performed well for Landsat satellite images, and hence are not applicable for these kinds of images.
- 2. The visual quality of decrypted images using DCT basis matrix, DWT basis matrix are not good compared to the visual quality of decrypted images resulting from the DFT basis matrix. This indicates that the results of DFT basis matrix are better than the results of DCT and DWT basis matrices.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_0.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_1.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_2.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_3.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_4.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_5.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_6.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_259_7.png)

Figure 8.10 Results of CS based encryption and decryption processes using DCT basis matrix. (From Nagesh, P. and Li, B., Int. Conf. Acoust. Speech Signal Process., 1261–1264, 2009; Singh, T. and Singh, M., US Patent No. 8,761,525, US Patent and Trademark Office, Washington, DC, 2014.) (a) Encrypted color image using different secret keys (A) Secret key k = 216000 (B) Secret key k = 288000 (C) Secret key k = 360000 (D) Secret key k = 432000 (b) Decrypted image using different secret keys (A) Secret key k = 216000 (B) Secret key k = 288000 (C) Secret key k = 360000 (D) Secret key k = 432000.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_0.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_1.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_2.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_3.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_4.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_5.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_6.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_260_7.png)

Figure 8.11 Results of CS based encryption and decryption processes using DFT basis matrix (a) Encrypted color image using different secret keys (A) Secret key k = 216000 (B) Secret key k = 288000 (C) Secret key k = 360000 (D) Secret key k = 432000 (b) Decrypted image using different secret keys (A) Secret key k = 216000 (B) Secret key k = 288000 (C) Secret key k = 360000 (D) Secret key k = 432000.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_0.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_1.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_2.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_3.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_4.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_5.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_6.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_261_7.png)

Figure 8.12 Results of CS based encryption and decryption processes using DWT basis matrix (a) Encrypted color image using different secret keys (A) Secret key k = 216000 (B) Secret key k = 288000 (C) Secret key k = 360000 (D) Secret key k = 432000 (b) Decrypted image using different secret keys (A) Secret key k = 216000 (B) Secret key k = 288000 (C) Secret key k = 360000 (D) Secret key k = 432000.
