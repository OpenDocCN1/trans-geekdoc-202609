
![](img/47f81eeb5093bf67426e3b948e0d8952_72_0.png)

Figure 4.13 Decrypted images for all encryption algorithms in the presence of noise with an SNR of 50 dB: (a) the RC6 algorithm; (b) the homomorphic cryptosystem with the RC6 algorithm; (c) the chaotic Baker map algorithm; and (d) the homomorphic cryptosystem with the chaotic Baker map scrambling algorithm.

![](img/47f81eeb5093bf67426e3b948e0d8952_72_1.png)

Figure 4.14 The variation of the PSNR of the decrypted image with the SNR of the encrypted image for all encryption algorithms.

comes at the expense of losses in the decrypted image due to the LSB watermark.

2. All other parameters, like encryption quality, noise immunity, and key sensitivity, depend mainly on the encryption algorithm. For the diffusion ciphers, like RC6, the encryption quality and the key sensitivity are better than those of the permutation ciphers, like chaotic Baker map. But, if the transmission medium is noisy, the permutation ciphers are preferred.

## CHAOTIC IMAGE ENCRYPTION WITH DIFFERENT MODES OF OPERATION

### 5.1 Overview

Chaos theory consistently plays an active role in modern cryptography. The attractiveness of using chaos as the basis for developing a cryptosystem is mainly its random behavior and sensitivity to initial conditions and parameter settings that fulfill the classic Shannon requirements of confusion and diffusion [89]. Chaos-based algorithms have shown some exceptionally good properties in many concerned aspects regarding security, complexity, speed, computational overhead, and so on. Some chaotic cryptosystems based on ergodicity have been proposed [90,91]. A number of chaos-based image [91,92] and random number generation algorithms [67,93–95] based on discrete chaos have been proposed, but security is generally not high enough [96,97].

This chapter discusses implementing chaotic Baker map scrambling of image pixels using three different modes of operation: CBC, CFB, and OFB. This implementation depends on the block size S, where S = N × N pixels, and an IV that works as the main key. The bits of the IV must be random and uncorrelated as much as possible to yield a powerful encryption mechanism. In the chapter experiments, the image encrypted is Lena, which is a 512 × 512 grayscale image, and parts of an encrypted version of the Cameraman image are used in the IV (Figure 5.1).

### 5.2 Chaotic Encryption with Modes of Operation

The main objective of chaotic encryption with different modes of operation is to increase the security of chaotic encryption with moderate computation time and adjust it to encrypt images with arbitrary dimensions. We investigated chaotic encryption with three modes of operation: CBC, CFB, and OFB [16–18]. The three modes were tested to decide which one would increase the data-hiding ability of the cryptosystem. Chaotic encryption with modes of operation can be simply summarized in the following three steps:

- 1. Scan the image row by row.
- 2. Convert the scanned rows to w blocks, each with N × N pixels.
- 3. Encrypt these blocks using the 2D chaotic Baker map in the CBC, CFB, or OFB mode as explained in the following sections.

The block diagram of chaotic encryption with modes of operation is shown in Figure 5.2.

![](img/47f81eeb5093bf67426e3b948e0d8952_75_0.png)

Figure 5.1 Encrypted version of Cameraman image.

![](img/47f81eeb5093bf67426e3b948e0d8952_76_0.png)

Figure 5.2 Chaotic encryption implemented in (a) CBC mode, (b) CFB mode, (c) OFB mode.

### 5.3 Implementation Issues

As stated in the previous section, chaotic encryption can be implemented in three different modes of operation. It is based on the 2D chaotic Baker map as the main encryption algorithm. It is known that the permutations induced by the Baker map behave as typical random permutations. An IV is used as the main key. This IV must be random to resist the brute-force attack. The XOR operations between the bits of the IV and the bits of the data blocks change the values of the pixels, which makes the encryption algorithm behave like a 3D Baker map. The algorithm also uses a secondary key, which is the key used by the Baker map to scramble the pixels.

Chaotic encryption with modes of operation is based on the segmentation of the image to be encrypted into blocks. The block size is an important factor that affects the performance of the cryptosystem. The effect of the block size on the encryption quality is studied in detail in the simulation examples section. Because the IV has similar size to the plaintext blocks, the increase in the block size increases the security. In addition, the chaotic encryption algorithm with modes of operation will be able to encrypt images with arbitrary dimensions after segmentation into small blocks.

### 5.4 Simulation Examples and Discussion

Simulation experiments have been carried out to encrypt the Lena image with the chaotic encryption system using the different modes of operation and comparing the obtained results with the results of the 2D chaotic Baker map encryption algorithm and the RC6 algorithm. The IV has been taken as part of the encrypted Cameraman image shown in Figure 5.1, equal in size to the selected block size. Several block sizes have been tested:

- 1. S₁ = 128 × 128 pixels. The IV is a 128 × 128 pixel section of the encrypted Cameraman image.
- 2. S₂ = 64 × 64 pixels.
- 3. S₃ = 32 × 32 pixels.
- 4. S₄ = 16 × 16 pixels.
- 5. S₅ = 8 × 8 pixels.

The encrypted versions of the Lena image are shown using the chaotic Baker map cryptosystem and the RC6 cryptosystem (Figure 5.3) and the chaotic encryption with different modes of operation and different block sizes (Figure 5.4). It is clear from Figure 5.4 that the performance of the chaotic encryption with different modes of operation is good except for its implementation in the OFB mode with large block sizes.

To check the noise immunity of each of the cryptosystems mentioned in this chapter, additive white Gaussian noise (AWGN) with

![](img/47f81eeb5093bf67426e3b948e0d8952_77_0.png)

Figure 5.3 Encrypted images using traditional cryptosystems: (a) encrypted image using the chaotic Baker map cryptosystem; (b) encrypted image using the RC6 cryptosystem.

a signal-to-noise ratio (SNR) of 5 dB was added to the encrypted images, and then the decryption was performed. The decryption results of the chaotic Baker map cryptosystem and the RC6 cryptosystem (Figure 5.5) and the chaotic encryption with different modes of operation (Figure 5.6) are shown. From visual inspection, it is clear that the chaotic Baker map cryptosystem has the highest noise immunity. It is also clear that the chaotic encryption with different modes of operation is more immune to noise than the RC6 cryptosystem.

![](img/47f81eeb5093bf67426e3b948e0d8952_78_0.png)

Figure 5.4 Encrypted images using chaotic encryption with different modes of operation and different block sizes.

Table 5.1 shows the values of the evaluation metrics for all cryptosystems mentioned in this chapter; $r_{cc}$ represents the correlation

![](img/47f81eeb5093bf67426e3b948e0d8952_79_0.png)

Figure 5.5 Decrypted images using the traditional cryptosystems at SNR = 5 dB. (a) decrypted image using the chaotic Baker map cryptosystem; (b) decrypted image using the RC6 cryptosystem.

![](img/47f81eeb5093bf67426e3b948e0d8952_79_1.png)

Figure 5.6 Decrypted images using the chaotic algorithm with different modes of operation and different block sizes at SNR = 5 dB.

| Table 5.1 Numerical Evaluation Metrics for All Cryptosystems | | | | | | | | | | | | | | | | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CHAOTIC ENCRYPTION WITH MODES OF OPERATION | | | | | | | | | | | | | | | | | | | | | | | | | |
| | CBC | | | | | | | | | | CFB | | | | | | | | | | OFB | | | | ENCRYPTION | | RC6 |
| | $S_1$ | $S_2$ | $S_3$ | $S_4$ | $S_5$ | $S_6$ | $S_7$ | $S_8$ | $S_9$ | $S_{10}$ | $S_1$ | $S_2$ | $S_3$ | $S_4$ | $S_5$ | $S_6$ | $S_7$ | $S_8$ | $S_9$ | $S_{10}$ | $S_1$ | $S_2$ | $S_3$ | $S_4$ | $S_5$ | | | | | | | |
| TEST | | | | | | | | | | | | | | | | | | | | | | | | | | | | | | |
| $D$ | 0.71 | 0.72 | 0.71 | 0.71 | 0.72 | 0.71 | 0.71 | 0.71 | 0.71 | 0.71 | 0.7 | 0.67 | 0.66 | | | | | | | | | | | | | | | | |
| $I_{eye}$ | $1.4 \times 10^{-3}$ | $4.7 \times 10^{-6}$ | $1.3 \times 10^{-3}$ | $1.7 \times 10^{-3}$ | $-2 \times 10^{-3}$ | $15 \times 10^{-3}$ | $3.7 \times 10^{-3}$ | $-7.1 \times 10^{-3}$ | $2.5 \times 10^{-4}$ | $-65 \times 10^{-3}$ | $2 \times 10^{-3}$ | $2.3 \times 10^{-3}$ | $41.8 \times 10^{-3}$ | $0$ | $10^{-4}$ | | | | | | | | | | | | | | |
| $D_t$ | 0.71 | 0.7 | 0.71 | 0.71 | 0.7 | 0.71 | 0.71 | 0.71 | 0.7 | 0.7 | 0.73 | 0.74 | 0.95 | 0.98 | 0.87 | | | | | | | | | | | | | | |
| $I_{eye}^t$ | 0.57 | 0.57 | 0.57 | 0.57 | 0.57 | 0.57 | 0.57 | 0.57 | 0.7 | 0.57 | 0.7 | 0.7 | 0.69 | 0.71 | $2.5 \times 10^{-3}$ | | | | | | | | | | | | | | |
| *Note: Decryption was performed in the presence of an AWGN with $SNR=5 \, dB$. | | | | | | | | | | | | | | | | | | | | | | | | | | | | | | | |
