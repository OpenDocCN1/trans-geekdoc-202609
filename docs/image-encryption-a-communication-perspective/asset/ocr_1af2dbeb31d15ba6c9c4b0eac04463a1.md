The UACI is defined as

$$UACI = \frac{1}{M \times N} \left[ \sum_{i,j} \frac{C_1(i,j)-C_2(i,j)}{255} \right] \times 100\% \quad (3.11)$$

It measures the average intensity of differences between the two images. The higher the values of NPCR and UACI are, the better the encryption will be.

# 3.3 Other Tests

# 3.3.1 Noise Immunity

The noise immunity reflects the ability of the image cryptosystem to tolerate noise. To test the noise immunity, noise with different signal-to-noise ratios (SNRs) is added to the encrypted image, and then the decryption algorithm is performed. If the decrypted image is close to the original image, we can say that the cryptosystem at hand is immune to noise. This closeness can be verified visually or numerically with the value of $r_{xy,d}$ which represents the correlation coefficient between the original image and the decrypted image, and the peak signal-to-noise ratio (PSNR) of the decrypted image, which is defined as follows [60,66]:

$$PSNR = 10 \times \log_{10} \left( \frac{M \times N \times 255^2}{\sum_{m=1}^{M} \sum_{n=1}^{N} \left[ f(m,n) - f_d(m,n) \right]^2 } \right) \quad (3.12)$$

where $f(m,n)$ is the original image, and $f_d(m,n)$ is the decrypted image.

# 3.3.2 The Processing Time

The processing time is the time required to encrypt and decrypt an image. The smaller value the processing time has, the better the encryption efficiency will be.

# 3.4 Testing the Evaluation Metrics

We have tested these metrics by evaluating three encrypted images with well-known encryption quality. The first one is obtained by flipping the Cameraman image using the Caesar cipher, which is a straightforward