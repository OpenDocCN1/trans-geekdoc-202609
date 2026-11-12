# 3. Color Palettes: A color palette further contextualizes the information provided to the diffusion model by providing general information of how the colors were distributed in the image, ensuring accurate color replications. It can be obtained by downsizing an image to a small resolution such as 32 × 32.

# 3.1 Additional Optimizations

In order to increase perceptual similarity in a compression maximizing manner, we propose three further optimizations to the aforementioned conditioning inputs:

Due to edge detection, most pixels in a Canny edge bitmap have the same value, representing negative space between thin, edge outlines, allowing further optimization. We exploit this by using lossless JBIG2, the industry standard compression algorithm for bi-level images, typically used in fax machines and black-and-white PDFs. JBIG2 outperforms other algorithms by reducing bi-level images by a factor of 2-5 [17]. Testing on 490 images scraped from the Web (Sect. 4), we see that JBIG2 provides significant lossless compression, allowing the canny edges to be up to 99.95% and on average 90% smaller than the original image. The results are presented in Fig. 2.

![](bbox=[0.205, 0.45, 0.765, 0.57])

Fig. 2. Using JBIG2 on canny edges provides significant lossless compression.

The color map is encoded via WebP, which provides significantly reduced compression artifacting compared to JPEG [11], ensuring that the colors extracted from the original image are provided to the diffusion model accurately.

Lastly, we propose using segmentation masks to preserve finer perceptual details across compression and reconstruction. Stable Diffusion Inpainting allows using a black and white mask to indicate which sections of an image should be recreated, and which sections should be left untouched, thus allowing for the preservation of critical, salient features, such as faces, small text and small logos [42]. The cropped salient features are stored unmodified as part of the compressed form, hence the total compression becomes indirectly proportional to the area of salient features in the original image. However, since only small, important details are at risk of being distorted and thus marked as salient [22,33], compression is expected to still be significant. Salient features can be masked very quickly and automatically by leveraging Meta's Segment Anything Model