
depend on layer prediction relationship of SVC in order to construct hashing chain or embed watermarking. HAU is independent of SVC structure since HAU only considers the authentication of base layer's codestream and content-based features of SVC, hence HAU is transparent to users.

The last column illustrates the communication overhead. In our SVC experiments, GOP size is 8 and encoded SVC sequences have three layers (one base layer and two enhancement layers). The cryptographic authentication [46] appends 960 bytes overhead per GOP (i.e., each frame has 120 bytes overhead). Hence, the average overheads of the scheme [46] are 2.19% and 2.62% of the original codestream for quality and spatial scalability, respectively. In general, HAU produces the smallest communication overhead as shown at the last column of Table 7.4, except the similar communication overhead on quality scalability as that of cryptographic authentication. In addition, HAU's communication overhead is constant, but the overhead of cryptographic authentication [46] and watermarking-based authentication [50] increase with the number of enhancement layers. For example, with GOP size being 8, each frame will carry 40 bytes more overhead [46] when an SVC sequence contains one more enhancement layer.

## 7.4.1.4 Conclusions

A hybrid authentication scheme was introduced for SVC, named HAU, which processes the base layer and enhancement layers using cryptographic authentication and content-based authentication, respectively. Cryptographic authentication ensures the integrity of the base layer while content-based authentication verifies enhancement layers using extracted features. HAU is secure, SVC format-transparent, light-weight in communication overhead and low computational complexity. The analysis and experiments indicated that HAU is robust to content-preserving manipulations but sensitive to content-changing manipulations.

## 7.5 Conclusion

This Chapter emphasized the security of scalable video coding. Firstly, it introduced the characteristic of scalable video coding, which consists of temporal, quality, and spatial scalabilities. Then, security requirements were described, i.e., security and integrity. Secondly, it analyzed and evaluated existing encryption and authentication schemes of scalable video and images, and figured out that existing partial encryption and existing content-based authentication algorithms cannot satisfy reality security requirements. Additionally, two encryption schemes were proposed for different scenarios, i.e., bitstream encryption and transparent encryption. Furthermore, a hybrid authentication scheme was designed based on the structure of scalable video coding.

## References

- 1. D. L. Goeckel, Adaptive coding for time-varying channels using outdated fading estimates. *IEEE Transactions on Communications*, 47(6): 844–855, 1999.
- 2. V. K. Goyal, Multiple description coding: Compression meets the network. *IEEE Signal Processing Magazine*, 18(5): 74–93, 2001.
- 3. H. Schwarz, D. Marpe, and T. Wiegand, Overview of the scalable video coding extension of the h.264/avc standard. *IEEE Transactions on Circuits and Systems for Video Technology*, 17(9): 1103–1120, 2007.
- 4. M. Wien, H. Schwarz, and T. Oelbaum, Performance analysis of svc. *IEEE Transactions on Circuits and Systems for Video Technology*, 17(9): 1194–1203, 2007.
- 5. ITU-T, I. J. 1, Advanced video coding for generic audiovisual services, ITU-T and ISO/IEC JTC 1 Recommendation H.264 and ISO/IEC 14496-10 (MPEG-4) AVC, 2005.
- 6. W. Li. Overview of fine granularity scalability in MPEG-4 video standard. *IEEE Transactions on Circuits and Systems for Video Technology*, 11(3): 301–317, 2001.
- 7. H. Sohn, W. De Neve, and Y. M. Ro. Region-of-interest scrambling for scalable surveillance video using JPEG XR. *ACM Multimedia*, pp. 861–864, 2009.
- 8. H. Sohn, W. De Neve, and Y. M. Ro. Privacy protection in video surveillance systems: Analysis of subband-adaptive scrambling in JPEG XR. *IEEE Transactions on Circuits and Systems for Video Technology*, 21(2): 170–177, 2011.
- 9. C. Yuan, B. B. Zhu, Y. Wang, S. Li, and Y. Zhong. Efficient and fully scalable encryption for MPEG-4 FGS. *ISCAS (2)*, pp. 620–623, 2003.
- 10. B. B. Zhu, C. Yuan, Y. Wang, and S. Li. Scalable protection for MPEG-4 fine granularity scalability. *IEEE Transactions on Multimedia*, 7(2): 222–233, 2005.
- 11. Z. Shahid, M. Chaumont, and W. Puech. Selective and scalable encryption of enhancement layers for dyadic scalable H.264/AVC by scrambling of scan patterns. *ICIP*, pp. 1273–1276, 2009.
- 12. G. Algin and E. Tunali. Scalable video encryption of H.264 SVC codec. *Journal of Visual Communication and Image Representation (JVCIR)*, 22(4): 353–364, 2011.
- 13. A. Tosun and W. Feng. Efficient multi-layer coding and encryption of MPEG video streams. *IEEE International Conference on Multimedia and Expo (I)*, pp. 119–122, 2000.
- 14. C. Li, X. Zhou, and Y. Zhong. NAL level encryption for scalable video coding. *PCM*, pp. 496–505, 2008.
- 15. C. Li, C. Yuan, and Y. Zhong. Layered encryption for scalable video coding. *2nd International Congress on Image and Signal Processing*, pp. 1–4, 2009.
- 16. W. Zeng and S. Lei. Efficient frequency domain selective scrambling of digital video. *IEEE Transactions on Multimedia*, 5(1): 118–129, 2003.
- 17. F. Liu and H. Koenig. A survey of video encryption algorithms. *Computers & Security*, 29(1): 3–15, 2010.
- 18. B. Zhu, M. Swanson, and S. Li. Encryption and authentication for scalable multimedia: Current state of the art and challenges. *Internet Multimedia Management Systems V*, 5601: 157–170, 2004.
- 19. X. Liu and A. Eskicioglu. Selective encryption of multimedia content in distribution network: Challenges and new directions. In *2nd IASTED International Conference on Communication, Internet, and Information Technology*, pp. 527–533, 2003.
- 20. H. Yu. An overview on scalable encryption for wireless multimedia access. *Internet Quality of Service*, 5245: 24–34, 2003.
- 21. S. Lian. *Multimedia Content Encryption: Techniques and Applications*. Boca Raton, FL: CRC Press, pp. 121–130, 2008.
- 22. T. Kunkelmann and U. Horn. Video encryption based on data partitioning and scalable coding - A comparison. *IDMS*, pp. 95–106, 1998.
- 23. T. Stutz and A. Uhl. A survey of H.264 AVC/SVC encryption, *IEEE Transactions on Circuits and Systems for Video Technology*, 22(3): 325–339, 2012.
- 24. R. L. Rivest. The RC4 encryption algorithm. RSA Data Security, Inc., March 12, 1992.
- 25. S.-W. Park and S.-U. Shin. Combined scheme of encryption and watermarking in H.264/Scalable Video Coding (SVC). In *New Directions in Intelligent Interactive Multimedia*. Springer, Berlin, Germany, pp. 351–361, 2008.
- 26. Joint scalable video model software, http://ip.hhi.de/imagecomg1/savce/downloads/svc-reference-software.htm.
- 27. A. Skodras, C. Christopoulos, and T. Ebrahimi. The JPEG 2000 still image compression standard. *IEEE Signal Processing Magazine*, 18(5): 36–58, 2001.
- 28. Z. Zhao and P. Liang. A statistical analysis of H.264/AVC FME mode reduction. *IEEE Transactions on Circuits and Systems for Video Technology*, 21(1): 53–61, 2011.
- 29. S. Ma, W. Gao, D. Zhao, and Y. Lu. A study on the quantization scheme in H.264/AVC and its application to rate control. In *Advances in Multimedia Information Processing, PCM*, pp. 192–199, 2004.
- 30. T. Ebrahimi and C. Horne. MPEG-4 natural video coding - An overview. *Signal Processing: Image Communication*, 15(4–5): 365–385, 2000.
- 31. I. E. Richardson. *The H.264 Advanced Video Compression Standard*, 2nd ed. Chichester, UK: Wiley, 2010.
- 32. A. Mansouri, A. M. Aznaveh, F. Torkamani-Azar, and F. Kurugollu. A low complexity video watermarking in H.264 compressed domain. *IEEE Transactions on Information Forensics and Security*, 5(4): 649–657, 2010.
- 33. J. S. Park and H. J. Song. Selective intra prediction mode decision for H.264/AVC encoders. *World Academy of Science, Engineering and Technology*, 13: 51–55, 2006.
- 34. Arizona State University: Video trace library. http://trace.eas.asu.edu/index.html.
- 35. The CAVIAR team: EC funded CAVIAR project/IST 2001 37540. http://homepages.inf.ed.ac.uk/rbf/CAVIAR/.
- 36. C. Y. Lin and S. F. Chang. Issues and solutions for authenticating MPEG video. In *SPIE International Conference on Security and Watermarking of Multimedia Contents*, Vol. 3657, pp. 54–56, 1999.
- 37. S. Shahabuddin, R. Iqbal, S. Shirmohammadi, and J. Zhao. Compressed-domain temporal adaptation-resilient watermarking for H.264 video authentication. In *IEEE International Conference on Multimedia and Expo (ICME)*, pp. 1752–1755, 2009.
- 38. P. Yin and H. H. Yu. A semi-fragile watermarking system for MPEG video authentication. In *IEEE International Conference on Acoustics, Speech, and Signal Processing (ICASSP)*, Vol. 4, pp. IV-3461–IV-3464, 2002.
- 39. J. G. Apostolopoulos and S. J. Wee. Secure scalable streaming enabling transcoding without decryption. In *Proceedings of the IEEE International Conference on Image Processing*, pp. 437–440, 2001.
