
First rule is to permute the cover signal or hiding units by key before hiding. For example, 2D Arnold Transform Mapping. Thus, the non-intent receiver does not know the key and does not extract the hidden bits. Of course, it looks like permuting the information bits. However, there is a distinct difference that the permutation of cover signal affects the capacity of hiding.

Second rule is that the hiding should keep the statistical characteristic unchanged as much as possible. Most of modern steganalysis detects the existence of data hiding by analyzing the statistical characteristics [45]. Thus, most data hiding schemes by padding reserved fields with information bits are not secure in abnormal attributes detection. This rule is particularly important in hiding bits in compressed images, audios and videos because these formats have explicit characteristics, such as the distribution of predictive mode, transform coefficients, motion vectors.

Third rule is that the hiding should hide firstly bits into hiding units with less distortion and then hide bits into hiding units with more distortion. At this time, the total distortion caused by hiding will be less than ones caused by other hiding strategies. The small distortion means usually more secure.

These days, AI (artificial intelligence) is a hot research topic. It is worth thinking that how to develop data hiding in this era of AI. Most research of AI includes huge data and needs a cloud computing platform. Thus data hiding can be used to provide some privacy protection mechanism for data in cloud platform. Take deep learning as an example, there are many models which are obtained by many experts efforts in deep learning. It is very helpful for encouraging technology innovation if inventors of each model can be traced by technical measures. Actually, data hiding provides the potential technical measures to verify, authenticate and protect these models.

Social service platforms have been popular. Many media files are exchanged and processed, the authentication of media files can be achieved by robust data hiding schemes. Thus designing robust data hiding scheme is a potential research topic.

Another potential direction is to design data hiding schemes for the latest new media standards, such as HEVC, JPEG-X, 3D video codec and so on.

## 14.7 Conclusions

This chapter introduces the data hiding in compressed image and video. First, it gives the JPEG compression standard and the basic hybrid coding framework of video coding standards, such as MPEG1, MPEG2, MPEG4, H.264 and HEVC and so on. Then it reviews the potential hiding space and methods in compression domain. Following it gives the basic reversible data hiding strategies in images and videos. It also gives the further research directions and potential applications.

## References
- 1. F. A. P. Petitcolas, Anderson R. J., Kuhn M. G. Information hiding–A survey. Proceedings of the IEEE 87 (1999) 1062–1078.
- 2. H. Cheng, Li X. B. Partial encryption of compressed images and videos. IEEE Transactions on Signal Processing 48 (8) (2000) 2439–2451.
- 3. A. Z. Tirkel, Rankin G. A., Schyndel R. M. V. Electronic watermark. Proceedings of International Conference Digital Image Computing, Technology and Applications (1993) 666–672.
- 4. R. G. V. Schyndel, Tirkel A. Z., Osborne C. F. A digital watermark. Proceedings of IEEE International Conference Image Processing 2 (1994) 86–90.
- 5. R. G. V. Schyndel, Tirkel A. Z., Osborne C. F. A two dimensional watermark. Proceedings International Conference Digital Image Computing, Technology and Applications (1995) 378–383.
- 6. W. Bender, Gruhl D., Morimoto N., Lu A. Techniques for data hiding. IBM Systems Journal 35 (3–4) (1996) 313–336.
- 7. N. Nikolaidis, Pitas I. Copyright protection of images using robust digital signatures. Proceedings of IEEE International Conference on Acoustics Speech and Signal Processing (1996) 2168–2171.
- 8. R. Z. Wang, Lin C. F., Lin J. C. Hiding data in images by optimal moderately-significant-bit replacement. IEE Electronics Letters 36 (25) (2000) 2069–2070.
- 9. C. K. Chan, Cheng L. M. Hiding data in images by simple LSB substitution. Pattern Recognition 37 (3) (2004) 469–474.
- 10. J. Mielikainen. LSB matching revisited. IEEE Signal Processing Letters 13 (5) (2006) 285–287.
- 11. R. Z. Wang, Lin C. F., Lin J. C. Image hiding by optimal LSB substitution and genetic algorithm. Pattern Recognition 34 (3) (2001) 671–683.
- 12. C. C. Chang, Hsiao J. Y., Chan C. S. Finding optimal least-significant-bit substitution in image hiding by dynamic programming strategy. Pattern Recognition 36 (7) (2003) 1583–1595.
- 13. C. K. Chan, Cheng L. M. Improved hiding data in images by optimal moderately-significant-bit replacement. IEE Electronics Letters 37 (16) (2001) 1017–1018.
- 14. C. C. Thien, Lin J. C. A simple and high-hiding capacity method for hiding digit-by-digit data in images based on modulus function. Pattern Recognition 36 (12) (2006) 2875–2881.
- 15. S. J. Wang. Steganography of capacity required using modulo operator for embedding secret image. Applied Mathematics and Computation 164 (1) (2006): 99–116.
- 16. C. C. Chang, Chan C. S., Fan Y. H. Image hiding scheme with modulus function and dynamic programming strategy on partitioned pixels. Pattern Recognition 39 (6) (2006) 1155–1167.
- 17. X. L. Li, Yang B., Cheng D. F., Zeng T. Y. A generalization of LSB matching. IEEE Signal Processing Letters 16 (2) (2009) 69–72.
- 18. S. Liu, Yao H., Zhang S., Gao W. A progressive quality hiding strategy based on equivalence partitions of hiding units. LNCS Transaction on Data Hiding and Multimedia Security 6 (2011) 58–82.
- 19. H. T. Hu, Hsu L. Y. Robust, transparent and high-capacity audio watermarking in DCT domain. Signal Processing 109 (2015) 226–235.
- 20. M. Ali, Ahn C. W., Pant M., Siarry P. An image watermarking scheme in wavelet domain with optimized compensation of singular value decomposition via artificial bee colony. *Information Sciences* 301 (2015) 44–60.
- 21. C. Li, Zhang Z., Wang Y., Ma B., Huang D. Dither modulation of significant amplitude difference for wavelet based robust watermarking. *Neurocomputing* 166 (2015) 404–415.
- 22. Z. Shao, Duan Y., Coatrieux G., Wu J., Meng J., Shu H. Combining double random phase encoding for color image watermarking in quaternion gyrator domain. *Optics Communications* 343 (2015) 56–65.
- 23. Y. X. Liu, Liu S. Y., Zhao H. G. et al. A data hiding method for H.265 without intra-frame distortion drift. *Intelligent Computing Methodologies* (2017) 642–650. Cham, Switzerland, Springer.
- 24. J. Wang, Wang R., Xu D., Li W. An information hiding algorithm for HEVC based on angle differences of intra prediction mode. *JSW* 10 (2) (2015) 213–221.
- 25. L. P. Van, De Praeter J., Van Wallendael G., De Cock J., Van de Walle R. Out-of-the-loop information hiding for HEVC video. *ICIP* (2015) 3610–3614.
- 26. S. D. Lin, Shie S.-C., Guo J. Y. Improving the robustness of DCT-based image watermarking against JPEG compression. *Computer Standards & Interfaces* 32 (2010) 54–60.
- 27. W. Liu, Zeng W., Dong L., Yao Q. Efficient compression of encrypted grayscale images. *IEEE Transactions on Image Processing* 19 (4) (2010) 1097–1102.
- 28. X. G. Kang, X. Y. Xu, Peng A. J., Zeng W. J. Scalable lossy compression for pixel-value encrypted images. *IEEE Data Compression Conference 2012* Snowbird, Utah (2012).
- 29. X. G. Kang, Peng A. J., Xu X. Y., Cao X. C. Performing scalable lossy compression on pixel encrypted images. *EURASIP Journal on Image and Video Processing* 32 (2013) 1–6.
- 30. G. C. Zhang, Liu S. H., Jiang F., Zhao D. B., Gao W. An improved image compression scheme with an adaptive parameters set in encrypted domain. *Visual Communications and Image Processing* (2013) 1–6.
- 31. Q. Su, Niu Y., Zhao Y., Pang S., Liu X. A dual color images watermarking scheme based on the optimized compensation of singular value decomposition. *AEU-International Journal of Electronics and Communications* 67 (2013) 652–664.
- 32. S. A. Parah, Sheikh J. A., Hafiz A. M., Bhat G. M. Data hiding in scrambled images: A new double layer security data hiding technique. *Computers & Electrical Engineering* 40 (2014) 70–82.
- 33. S. Liu, Paul A., Zhang G., Jeon G. A game theory-based block image compression method in encryption domain. *Journal of Supercomputing* (2015). doi:10.1007/s11227-015-1413-0.
- 34. S. Liu, Rho S., Jifara W., Jiang F., Liu C. A hybrid framework of data hiding and encryption in H.264/SVC. *Discrete Applied Mathematics* (2016). doi:10.1016/j.dam.2016.06.028.
- 35. A. M. Alattar. Reversible watermark using the difference expansion of a generalized integer transform. *IEEE Transactions on Image Processing* 13 (2004) 1147–1156.
- 36. F. Huang, Qu X., Kim H. J., Huang J. Reversible data hiding in JPEG images. *IEEE Transactions on Circuits and Systems for Video Technology* 26 (9) (2016) 1610–1621.
- 37. Y. Zhang, Liu F. L., Yang C. F. et al. Steganalysis of content-adaptive JPEG steganography based on Gauss partial derivative filter bank. *Journal of Electronic Imaging* 26 (1) (2017) 013011.
