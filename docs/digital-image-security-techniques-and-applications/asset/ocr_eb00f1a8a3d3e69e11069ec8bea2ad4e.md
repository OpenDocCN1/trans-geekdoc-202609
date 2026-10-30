![](bbox=[0.13, 0.1, 0.38, 0.35])

![](bbox=[0.55, 0.1, 0.82, 0.35])

Figure 5.5 Encrypted watermarked image.

# 5.3 WATERMARKING PROCEDURE

The watermark embedding and extraction procedure is mentioned in sections 3.1 and 3.2. In the embedding procedure, the cover image is first divided into sub-bands (LL1, HL1, LH1, HH1) using one LWT. Apply QR decomposition to HL1 and LH1, and then extract the diagonal component of both the sub-bands of the input host image. Take the first watermark image as the cameraman and the second as details of the patient and apply LWT to both watermark images and apply Hénon scrambling to low-high sub-band of details of patient, and then extract the diagonal components of both watermark images. Add the diagonal components of both the watermark images and the cover image by taking suitable scaling factor. Apply inverse QR and LWT to get the watermarked image, then apply chaotic logistic map to scramble the image and send it to another end. In the extraction procedure, first receive the scrambled watermarked image and apply the decryption process to get the watermarked image. Apply LWT to get the watermarked sub-bands and get the watermarked diagonal components after applying QR decomposition. Apply inverse embedding, inverse QR decomposition, Hénon decryption, and inverse LWT to get both the watermark images back.

# 5.3.1 Embedding process

Step 1: To divide the input cover image into sub-bands as shown in Eq. (5.5), apply one level LWT.

[LL1,HL1,LH1,HH1] = lwt2(host image) (5.5)

Step 2: Apply QR decomposition to HL1 and LH1 and then extract the diagonal component of both the sub-bands of the input host image. In Eq. (5.6), R1 is the upper triangular matrix for HL1 sub-band.