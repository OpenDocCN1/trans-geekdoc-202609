CI and encrypted WM computed singular values were used alongside a multiplicative factor called the embedding strength in determining the watermarking bits to be embedded into the CI. Embedded strength plays a vital part in deciding the watermarked image’s imperceptibility. Embedding strength is chosen in such a way to maintain a balance between the imperceptibility and PSNR. The LL band of the CI is rebuilt with the modified SVD bits consisting of CI and WM SVD bits. When inverse DWT was applied, it results in watermarking the encrypted image in the main CI. WM is preprocessed to possess singular values that match with those of the cover or the target image. For the removal or extraction of the watermark from the CI, again DWT and SVD is employed, as discussed within the algorithms above (Priya & Vijaya, 2021) (Figures 3.12 and 3.13).

![](bbox=[0.12, 0.4, 0.88, 0.57])

FIGURE 3.12 Embedded cover image with encrypted watermark image; extracted watermark image that is encrypted; and final watermark image after decryption.

![](bbox=[0.1, 0.64, 0.9, 0.82])

FIGURE 3.13 Histogram of actual cover image and embedded cover image with encrypted watermark image.

Variation of embedding strength gives the amount of imperceptibility associated with the watermarked CI as depicted in Table 3.3. Smaller the embedding strength, higher the PSNR value. As the embedding strength