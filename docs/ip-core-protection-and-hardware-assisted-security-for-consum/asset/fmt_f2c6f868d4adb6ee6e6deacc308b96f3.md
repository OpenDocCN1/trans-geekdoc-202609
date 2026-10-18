
In an 8-bit grayscale image, the pixel intensity ranges from \[0–255\], where 0 indicates pure black and 255 indicates pure white. Therefore, each grayscale image is represented using 256 shades of gray. To reduce the dynamic range (required in DCT processing), the midpoint of this range, i.e., 128 is subtracted from each pixel value of the image. Therefore, the modified data range, i.e., \[−128, 127\] is centered on zero. The generic 2D-DCT coefficient matrix (`T`) for a sample of `N`×`N` can be expressed as follows ([DCT matrix, 2018](#Chapter9.html#c09_bib10)):

![image](OEBPS/images/c09_eqn1.gif)

where “`N`” is the size of the DCT matrix, “`i`” and “`j`” is the `i`th row, `j`th column component of the 2D-DCT matrix. In standard JPEG process, “`N`” is equal to 8 and `i` and `j` vary from 0 to 7. The 2D-DCT coefficient matrix for an 8 × 8 block is shown in [Figure 9.3](#Chapter9.html#c09_fig3) (also explained in Chapter 3). According to [Figure 9.3](#Chapter9.html#c09_fig3), all elements of the first row (`i` = 0) are equal to 1/√8 according to ([9.1)](#Chapter9.html#c09_eqn1). As “`T`” is an orthogonal matrix, the inverse of “`T`” (i.e., `T`^(−1)) is equal to the transpose of “`T`” (i.e., `T`^(trans)).

![image](OEBPS/images/PBCS0600-09-f03.jpg)

Figure 9.3. 2D-DCT coefficient matrix

##### 9.2.1.2 Perform DCT on input image

To perform DCT on the input image, the image should be subdivided into multiple nonoverlapping 8 × 8 blocks. Each block can be processed independently, therefore block-wise parallelism is possible for transformation, which is the key feature of 8 × 8 DCT. A generic 8 × 8 block “`M`” of input image matrix is shown in [Figure 9.4](#Chapter9.html#c09_fig4), where `m`[`ij`] express pixel intensity of `i`th row, `j`th column component of the “`M`” block. The DCT on the “`M`” block can be performed through following matrix multiplications:

![image](OEBPS/images/c09_eqn2.gif)

![image](OEBPS/images/PBCS0600-09-f04.jpg)

Figure 9.4. Generic 8×8 block of input image

In the above expression, `D` is calculated as follows:

![image](OEBPS/images/c09_eqn3.gif)

The “`D`” matrix (`d`[11], `d`[12], …, `d`[88]) transforms the rows of the “`M`” block. Further, “`X`” matrix (`X`[11], `X`[12], …, `X`[88]) transforms the columns of the “`D`” matrix. Thus, transforms both rows and columns of the “`M`” block. Therefore, “`X`” is the DCT block of “`M`” block.

##### 9.2.1.3 Perform quantization

The transformed block “`X`” is now ready to compress through quantization. As human eye is not good in distinguishing the high-frequency brightness deviation in an image, a large amount of information reduction is possible from the high-frequency components of an image. This is achieved by dividing each element of transformed block “`X`” by the corresponding element of the quantization matrix (`Q`) and then rounding to the nearest integer. As a result, most of the high-frequency components are rounded to zero, which indicates discarding less important high-frequency components. Additionally, many of the remaining components become small positive or negative numbers, which take fewer bits to represent. The quantization matrix is designed in such a way that it provides more resolution to higher perceivable frequency components over lower perceivable frequency components. The designing process of standard quantization matrix (`Q`[`50`]) involves subjective experiment of human visual system. In the range of 1 to 100, standard quantization matrix provides quality level as 50. It thus provides a balance between image compression ratio and image quality. The standard quantization matrix is shown in [Figure 9.5](#Chapter9.html#c09_fig5). However, image quality and compression ratio can vary by changing the quantization matrix. To obtain a quantization matrix with quality level greater than `Q`[`50`], each element of `Q`[`50`] should be multiplied with (100−quality level)/50 and then rounding to the nearest integer. Similarly, to obtain a quantization matrix with quality level lower than `Q`[`50`], each element of `Q`[`50`] should be multiplied with 50/quality level and then rounding to the nearest integer.

![image](OEBPS/images/PBCS0600-09-f05.jpg)

Figure 9.5. Standard quantization matrix (`Q`[`50`])

##### 9.2.1.4 Data encoding

The 2D quantized 8 × 8 block (`X′`) is now ready to be compressed through encoding. The block is converted to a 1D array through “zigzag” scanning. Thereafter, employing `run-length encoding (RLE)` enables grouping similar frequencies together. The encoded data is then converted into binary to generate a bitstream. Finally, the bitstream data of the compressed image is stored into a storage device.

#### 9.2.2 DCT-based JPEG image decompression process

##### 9.2.2.1 Data decoding

Image reconstruction process starts with data decoding. The stored data is first fetched from the storage device and decoded through RLE. The quantized 2D 8 × 8 block (`X′`) is reconstructed through “inverse zigzag” scanning from the 1D array.

##### 9.2.2.2 Perform inverse quantization

The reconstructed `X′` is now ready to be decompressed through inverse quantization. Decompression is achieved by multiplying each element of reconstructed block by the corresponding element of quantization matrix, to obtain block (`X″`).

##### 9.2.2.3 Perform IDCT on decompressed image

Similar to applying DCT on the input block in the JPEG compression process, IDCT is applied on the decompressed block (`X″`). The IDCT on the `X″` block can be performed through following matrix multiplications:

![image](OEBPS/images/c09_eqn4.gif)

In the above expression, `E` is calculated as follows:

![image](OEBPS/images/c09_eqn5.gif)

The “`E`” matrix (`e`[11], `e`[12], …, `e`[88]) transforms the rows of the `X″` block. Further, “`O`” matrix (`o`[11], `o`[12], …, `o`[88]) transforms the columns of the “`E`” matrix. Thus the above transformations, transform both the rows and columns of the `X″` block. Therefore, “`O`” is the IDCT block of `X″` block. After applying IDCT on the decompressed block, each element is rounded to the nearest integer.

##### 9.2.2.4 Reconstruct the decompressed image

To reconstruct the decompressed image from the inversely transformed decompressed block, 128 is added to each of the element of the decompressed block to keep the range of output image pixel between \[0, 255\] instead of \[−128, 127\].

### 9.3 Design process of structurally obfuscated JPEG IP core

#### 9.3.1 Threat model, problem formulation, and optimization framework

##### 9.3.1.1 Threat model

To protect a JPEG CODEC IP core from RE and Trojan insertion through structural obfuscation. In order to maximize protection ability, impede the correct functionality of the application by generating a functionally equivalent but structurally nonobvious architecture of JPEG CODEC IP Core. (Note: Motivation of using structural obfuscation to guard against RE was thoroughly explained in Chapter 7).

##### 9.3.1.2 Problem formulation

In order to protect a JPEG CODEC IP core from RE threat, design a structurally obfuscated, low-cost hardware. The hardware design cost is evaluated by calculating the total hardware area and total design latency. The hardware design cost adopted from Sengupta `et al.` ([2018b](#Chapter9.html#c09_bib32)) is formulated as:

![image](OEBPS/images/c09_eqn6.gif)

where `Cf`(`X`[`i`]) is the hardware design cost for design solution `Xi`; `L`[total]^(JPEG) and `A`[total]^(JPEG) represent the total design latency and total hardware area of the obfuscated JPEG IP core, respectively; `L`[max]^(JPEG) and `A`[max]^(JPEG) indicate the maximum possible design latency and hardware area, respectively, using the specified module library; weightage factor of two design parameters (latency-area) is controlled via `w`[1] and `w`[2].

##### 9.3.1.3 Optimization framework
