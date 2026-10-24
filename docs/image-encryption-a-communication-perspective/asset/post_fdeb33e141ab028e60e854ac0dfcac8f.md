
![](img/47f81eeb5093bf67426e3b948e0d8952_49_0.png)

(a)

![](img/47f81eeb5093bf67426e3b948e0d8952_49_1.png)

(b)

Figure 2.17 (a) The 8 × 8 matrix divided into rectangles. (b) The matrix after applying the 2D Baker map.

Figure 2.17 shows an example for the chaotic map of an (8 × 8) square image (i.e., N = 8). The secret key, S_key = [n1, n2, n3] = [2, 4, 2]. The cipher resulting from the chaotic Baker map encryption is a permutation cipher, which does not change the histogram of the original image. Although this cryptosystem is simple and fast to be used for video encryption, it lacks the high degree of security, and its computation time grows as the image size increases [51,52,61].

## 3 Encryption Evaluation Metrics

### 3.1 Introduction

With the application of an encryption algorithm to an image, its pixel values change when compared with the original image. A good encryption algorithm must make these changes in an irregular manner and maximize the difference in pixel values between the original and the encrypted images. Also, to obtain a good encrypted image, it must be composed of totally random patterns that do not reveal any of the features of the original image. The encrypted image has to be independent of the original image. It should have a low correlation with the original image [62–66].

One of the important metrics in examining an encrypted image is the visual inspection: The more hidden the features of the image are, the better the encryption algorithm is. Unfortunately, visual inspection only is not enough to judge the complete hiding of the contents of the image, so other metrics are considered to evaluate the degree of encryption quantitatively [67,68].

Diffusion is an important parameter that must be measured to judge the encryption algorithm randomization. If an algorithm has a good diffusion characteristic, the relation between the encrypted image and the original image is too complex, and it cannot be predicted easily. To measure the diffusion of any algorithm, a bit is changed in the plain image, and the difference between the encrypted image obtained from the original plain image and the encrypted image obtained from the modified one is obtained [69].

Other tests can be used to determine some specific characteristics of the encryption algorithms, such as the noise immunity and the processing time.

### 3.2 Encryption Evaluation Metrics

This section discusses, in detail, two families of encryption metrics; the first family evaluates the ability of the encryption algorithm to substitute the original image with an uncorrelated encrypted image. In this family, five metrics are studied: the histogram deviation D_H, the correlation coefficient r_xy, the irregular deviation D_I, the histogram uniformity, and the deviation from ideality. The second family evaluates the diffusion characteristics of the encryption algorithm. In this family, three metrics are studied: the Avalanche effect, number of pixel change rate (NPCR), and unified average changing intensity (UACI).

### 3.2.1 Histogram Deviation

The histogram deviation measures the quality of encryption in terms of how it maximizes the deviation between the original and the encrypted images [70]. The steps for calculating this metric are as follows:

- 1. Estimate the histogram of both the original and the encrypted images.
- 2. Estimate the absolute difference between both histograms.
- 3. Estimate the area under the absolute difference curve divided by the total area of the image as follows:

```
$$D_H = \frac{\left(\frac{d_0 + d_{255}}{2} + \sum_{i=1}^{254} d_i\right)}{M \times N}\tag{3.1}$$
```

where d_i is the amplitude of the absolute difference at the gray level i. M and N are the dimensions of the image to be encrypted. The higher the value of D_H is, the better the quality of the encrypted image will be [70].

Although this metric gives good results about how the encrypted image deviates from the original image, it cannot be used alone to measure the quality of encryption as it has some limitations, explained further in this chapter.

### 3.2.2 Correlation Coefficient

A useful metric to assess the encryption quality of any image cryptosystem is the correlation coefficient between pixels at the same indices in the plain- and the cipher images [70]. This metric can be calculated as follows:

$r_{xy} = \frac{\text{cov}(x, y)}{\sqrt{D(x)}\sqrt{D(y)}}$ (3.2)

where x and y are the plain- and cipherimages. In numerical computations, the following discrete formulas can be used:

$E(x) = \frac{1}{L} \sum_{i=1}^{L} x_i$ (3.3)

$D(x) = \frac{1}{L} \sum_{i=1}^{L} (x_i - E(x))^2$ (3.4)

$\text{cov}(x, y) = \frac{1}{L} \sum_{i=1}^{L} (x_i - E(x))(y_i - E(y))$ (3.5)

where L is the number of pixels involved in the calculations. The closer the value of r_xy to zero, the better the quality of the encryption algorithm will be.

### 3.2.3 Irregular Deviation

The irregular deviation measures the quality of encryption in terms of how much the deviation caused by encryption (on the encrypted image) is irregular [71]. The steps for calculating this metric are as follows:

- 1. Calculate the absolute difference between the encrypted image and the original image.
- 2. Estimate the histogram H of this absolute difference matrix.
- 3. Estimate the mean value M_H of this histogram.
- 4. Estimate the absolute of the histogram deviations from this mean value as follows:

$$H_D(i) = |H(i) - M_H| \tag{3.6}$$

The irregular deviation $D_I$ is calculated as follows:

$$D_I = \frac{\sum_{i=0}^{255} H_D(i)}{M \times N} \tag{3.7}$$

The lower the value of $D_I$, the better the encryption quality will be.

### 3.2.4 Histogram Uniformity

A histogram uses a bar graph to profile the occurrence of each gray level of the image. The horizontal axis represents the gray-level value. It begins at zero and goes to the number of gray levels. Each vertical bar represents the number of occurrences of the corresponding gray level in the image [72].

For image encryption algorithms, the histogram of the encrypted image should have two properties:

- 1. It must be totally different from the histogram of the original image.
- 2. It must have a uniform distribution, which means that the probability of occurrence of any grayscale value is the same.

### 3.2.5 Deviation from Ideality

The deviation from ideality measures the quality of encryption in terms of how the encryption algorithm minimizes the deviation of the encrypted image from an assumed ideal encryption case. An ideally encrypted image $C_I$ must have a completely uniform histogram distribution, which means that the probability of existence of any gray level is constant. From this definition of the ideal encrypted image histogram, it can be formulated as

$$H(C_i) = \begin{cases} \frac{M \times N}{256} & 0 \le C_i \le 255 \\ 0 & \text{elsewhere} \end{cases} \tag{3.8}$$

The deviation from ideality can be represented as follows:

$$ D = \frac{\sum_{C_i=0}^{255} |H(C_i)-H(C)|}{M \times N} \tag{3.9} $$

where $H(C)$ is the histogram of encrypted image. Of course, the lower the value of $D$, the better the encryption quality will be.

### 3.2.6 Avalanche Effect

We can use the Avalanche effect metric [73,74] to test the efficiency of the diffusion mechanism. A single bit change can be made in the image $P$ to give a modified image $P'$. Both $P$ and $P'$ are encrypted to give $C$ and $C'$. The Avalanche effect metric is the percentage of different bits between $C$ and $C'$. If $C$ and $C'$ differ from each other in half of their bits, we can say that the encryption algorithm possesses good diffusion characteristics.

### 3.2.7 NPCR and UACI

To test the influence of a one-pixel change on the whole image encrypted by any encryption algorithm, two common metrics may be used: NPCR and UACI [75]. Let the two ciphered images, whose corresponding plain images have only one pixel difference, be denoted by $C_1$ and $C_2$. Label the grayscale values of the pixels at grid $(i,j)$ in $C_1$ and $C_2$ by $C_1(i,j)$ and $C_2(i,j)$, respectively. Define a binary matrix $D$ with the same size as the images $C_1$ and $C_2$. Then, $D(i,j)$ is determined from $C_1(i,j)$ and $C_2(i,j)$. If $C_1(i,j)=C_2(i,j)$, then $D(i,j)=0$; otherwise, $D(i,j)=1$.

The NPCR is defined as

$$ \text{NPCR}=\frac{\sum_{i,j} D(i,j)}{M \times N}\times100\% \tag{3.10} $$

The $NPCR$ measures the percentage of different pixels in the two images.
