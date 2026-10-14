σ_i and σ_ID is the corresponding variance value of original and compressed image, respectively; σ_IDI is the covariance of I and DI, C1 and C2 are positive constant values.

The compression ratio (CR) is found using below equation:

$CR = \frac{Size_f}{Size_{cf}}$ (8.12)

where f is the original image and Cf is the compressed image.

In this chapter, the compression ratio is found between the encrypted image and the original image.

$CR = \frac{Size_f}{Size_{Ef}}$ (8.13)

where f is the original image and Ef is the encrypted image.

In this process, the measurement matrix is used as a secret key for generating encrypted and decrypted images. This measurement matrix can be of different types: Fourier, Gaussian, and binary. In this chapter, the Gaussian type measurement matrix is used; it is also responsible for compression in the compressive sensing method. The size of this matrix also decides the compression of image.

The selection of the measurement matrix as a secret key can be done using below equation:

$k = M \times N \times C$ (8.14)

where k is the secret key, M×N is the size of measurement matrix, C is the no. of color channel (here C = 3)

# 8.4.3 Performance Analysis of CS Based Encryption and Decryption Processes for Goldhill Images

In this section, different sizes of encrypted Goldhill images are generated using different sizes of measurement matrices as secret keys. The decryption of these images is performed using the same measurement matrices which are used in encryption and CS recovery OMP algorithm. Figure 8.7 shows the encrypted images and decrypted images using CS based encryption and decryption processes based on DCT coefficients of a Goldhill image. Figure 8.8 shows the results after using DFT coefficients of a Goldhill image instead of DCT. Similarly, Figure 8.9 shows the corresponding images when DWT coefficients of the Goldhill image are used. The quality measure values for Goldhill images using CS based encryption and decryption processes are tabulated in Table 8.4.