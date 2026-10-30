techniques for smart healthcare system is discussed in [27]. In this article, open issues and challenges are elaborated on telemedicine applications. The presented review regarding different techniques inspires us to contribute a new watermarking technique that meets research gaps. There are numerous potential research issues that need to be focused, such as better robustness and perceptual invisibility, capacity, etc. Thus, by developing this novel technique, digital image copyright protection can be attained effectively with better attributes.

# 6.3 PROPOSED WATERMARKING TECHNIQUE

Watermark embedding and extraction techniques are presented in this section. Initially, HT decomposes a cover image into reflectance and illumination components. Further multiresolution analysis is attained by decomposing the reflectance component using RDWT. Low high (LH) subband is chosen to maintain an adequate balance between robustness and perceptual invisibility. MSVD is applied to this LH subband to attain better imperceptibility. Similarly, RDWT-MSVD transforms are applied over the watermark image. The selection of the optimal scaling factor yields the watermarked image. Embedding and extraction watermark procedures are depicted in Figure 6.1(a, b).

![](bbox=[0.12, 0.6, 0.92, 0.88])

(a)

Figure 6.1 Watermarking technique procedure (a) embedding.