![](bbox=[0.1, 0.14, 0.88, 0.38])

Figure 14.15 The illustration of hiding using difference.

Figure 14.15 shows the example which hides information bits 110 into a hiding unit (p_i, p_{i+1}) = (67,78), then the resulting hiding unit becomes (65,79).

There are many methods to design a hiding unit. The basic idea is to get one difference by predictive methods in image or video coding.

# 14.3.2 Hiding in Non-compressed Media

Hiding in non-compressed media usually uses mathematic transform, such as discrete Fourier transform (DFT), DCT [19], discrete wavelet transform (DWT) [20,21], singular value decomposition (SVD), to transform the cover signal into transformed domain [22], and then modify features to hide information bits. These mathematic transforms usually have their integer version, namely integer DCT, integer DWT and so on. Integer transform is more suitable for high-capacity data hiding, and float transform is more suitable for high-robustness data hiding.

# 14.3.3 Hiding in Compressed Media

Multimedia has a large amount size compared with text; hence, most media are compressed media. Hiding in compressed media is more useful but more difficult [23–25]. The compression has removed redundant space in cover signal so the representation is more compact and formatted. Moreover, compressed media requires the hiding scheme is format-compatible. There are two types of hiding strategies: one is first decompressing the media into spatial domain, and then information bits are hidden by methods like equation (14.8) and (14.10) 14.3.1 and 14.3.2. But it is time-consuming, another is first to decompress partially the cover signal and then modify the syntax elements to hide information bits [26] just like those methods in 3.1 and 3.2.