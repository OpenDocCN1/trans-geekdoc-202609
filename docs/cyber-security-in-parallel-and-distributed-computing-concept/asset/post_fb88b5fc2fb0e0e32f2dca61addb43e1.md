
been hidden in the image. However, in reality we do not have the original image, so we have to build an image to make a “landmark,” so that we can estimate the information hidden in any image by the theory of coincidence built from the case having an original image to compare. Based on empirical estimates, the “matched” estimation method can estimate the information on the image equivalent to other estimation approaches such as RS and DI [32], but better in terms of time taken.

## 2.3.2 Constraint Steganalysis

Along with constraint steganalysis, there are some public steganographic programs such as OutGuess [40], Attack F5 [13], Attack HKC [42], Attack RCM [43], Attack MBNS [44].

Contributing to this research, the author has proposed four constraint steganalysis techniques for hidden images using known hiding techniques.

### 2.3.2.1 HKC Hiding Technique

This hiding technique is based on shifting pixel frequency columns. The shifting creates an abnormal signal around the frequency band with the greatest value of the pixel frequency graph, so Wen-Chung Kuo and Yan-Hung Lin provide a method of detection [42] based on the relationship between the maximum frequency column called Peak and the four adjacent frequency bands of Peak to detect hidden images using the HKC technique. However, Kuo and Lin’s detection techniques are not effective in the case of low or hidden bits, so the authors propose Kuo and Lin’s advanced method for higher reliability [39]. The thesis also builds a generally simpler taxonomy than that of Kuo and Lin. Based on this new expression, we can estimate the information hidden in the image using the HKC technique.

### 2.3.2.2 DIH Technique

This technique is based on the coefficient of difference of the image. This technique loses the naturalness of the histogram of different coefficients d_ij, which in an unhidden image that is distributed according to the Gaussian histogram but in a hidden image does not have this distribution. This is the main reason why the author proposes a method for detecting hidden images using the DIH technique [35].

### 2.3.2.3 IWH Hiding Technique

This is a reverse hiding technique based on shifting the frequency columns of the wavelet frequency histogram of LL, LH, HL bands. This is a unique case of the LSB hiding technique, but the amount of hidden message with the highest hiding ability may still be very low compared to the conventional LSB technique. Using blind steganalysis on LSB of wavelet frequency domain (χ²_n [13], “gray scale” of the thesis) usually results in low classification.

However, when analyzing the wavelet frequency histogram, we get the abnormal state of the histogram when we hide the information. Thus, the author gives the corresponding detection method and that can approximate the bit rate of information concealed in the image [35].

### 2.3.2.4 RVH Hiding Technique (Hiding in Two Phases)

This technique uses multiple concealment strategies to improve image quality and hiding capacity. Information to hide M is classified into M₁ and M₂. The hiding process consists of two main phases: a horizontal hiding phase to hide M₁ and a vertical hiding phase to hide M₂. This is a unique case of LSB hiding technique, but this method can be detected with some statistical detection methods such as χ₁², “standard deviation,” LLRT, etc. Because of using two-phases to hide information, it avoids balancing the pairs of value (PoV) that are normally caused by LSB technique.

Therefore, to detect hidden information, the author analyzes the frequency of bit “0” and bit “1” of the LSB on the pixel columns in even positions or on the pixel rows at the odd position of the image vector. With unhidden images, the frequency of bit 0 and bit 1 are approximately equal, but after hiding the message using RVH this rule is broken. The author has built up the expression of calculating the probability of bits 0 and 1 after each concealed phase of RVH so that the above statement can be verified. Then, we provide an algorithm for detecting and estimating the approximate number of bits of information for hidden images using the RVH hiding technique [36].

## 2.4 Conclusion

Steganography is still an urgent problem in the field of information protection in general, and security, politics and defense in particular. Steganography requires a comprehensive study of problems of hidden information in the image. Continuing research in this area is not only scientifically significant; it is also significant in promoting the development of the information security field.

New techniques for steganography are constantly being introduced. Each new technique has many advantages and is more difficult to detect. Analyzing and finding out the distinctive features of the image before and after hiding a message are important for the technique to detect hidden images using this technique. In this direction, in the future, we will continue to study the following issues:

- Improve algorithm to increase the accuracy of existing detection techniques.
- Provide a method of extracting information.
- Find a detection method for the m LSBs domain.
- Study methods of detecting hidden information in other multimedia environment such as video, audio, etc.

## References

1. Jessica Fridrich (2009), Steganography in digital media: principles, algorithms, and applications, Cambridge University Press.
2. C.K. Chan, L.M. Cheng (2001), Improved hiding data in images by optimal moderately-significant-bit replacement, IEEE Electronics Letters, Vol. 37 (16), pp. 1017-1018.
3. C.K. Chan, L.M. Cheng (2004), Hiding data in images by simple LSB substitution, Pattern Recognition 37, pp. 469-474.
4. C.C. Chang, J.Y. Hsiao, C.S. Chan (2003), Finding optimal least-significant-bit substitution in image hiding by dynamic programming strategy, Pattern Recognition 36, pp. 1583-1595.
5. Xiaolong Li, Bin Yang, Daofang Cheng and Tieyong Zeng (2009), A Generalization of LSB Matching, IEEE signal processing letters, Vol. 16 (2), pp. 69-72.
6. W.N. Lie, L.C. Chang (1999), Data hiding in images with adaptive numbers of least significant bits based on the human visual system, in: Proceedings of IEEE International Conference on Image Processing, Taipei, Taiwan, vol. 1, pp. 286-290.
7. Ching-Chiuan Lin, Nien-Lin Hsueh (2008), A lossless data hiding scheme based on three-pixel block differences, Pattern Recognition 41, pp. 1415-1425.
8. S. H. Liu, T. H. Chen, H. X. Yao and W. Gao (2004), A variable depth LSB data hiding technique in images, Machine Learning and Cybernetics 2004, pp. 3990-3994.
9. Z. M. Lu, J. S. Pan, and S. H. Sun (2000), VQ-based digital image watermarking method, Electron. Lett, Vol. 36 (14), pp. 1201-1202.
10. F. A. P. Petitcolas, R. J. Anderson, and M.G. Kuhn (1999), Information hiding - A survey, Proc. IEEE, vol. 87 (7), pp. 1062-1078.
11. C. I. Podilchuk and E. J. Delp (2001), Digital watermarking: Algorithms and applications, IEEE Signal Process. Mag., vol. 18 (4), pp. 33-34.
12. Niels Provos, Peter Honeyman (2003), Hide and seek: An introduction to steganography, Published by The IEEE computer society.
13. Westfeld A. (2001), High Capacity Despite Better Steganalysis (F5A Steganographic Algorithm), In: Moskowitz, I.S. (eds.): Information Hiding. 4th International Workshop. Lecture Notes in Computer Science, Vol.2137. Springer-Verlag, Berlin Heidelberg New York (2001), pp. 289-302.
14. J. K. Cox, J. Kilian, T. Leighton, and T. Shamoon (1997), Secure spread spectrum watermarking for multimedia, IEEE Trans. on Image Processing, 6(12):1673-1687.
15. Ingemar Cox, Jeffrey Bloom, Matthew Miller, Ton Kalker, Jessica Fridrich (2008), Digital Watermarking and Steganography, Second Edition, Morgan Kaufmann Press, USA.
16. Li, Bin; Fang, Yanmei; Huang, Jiwu. (2008), Steganalysis of Multiple-Base Notational System Steganography, IEEE Signal Processing Letters, vol. 15, pp. 493-496.
17. B. Chen and G. Wornell (2001), Quantization index modulation: A class of provably good methods for digital watermarking and information embedding, IEEE Trans. Info. Theory, Vol. 47 (4), pp. 1423-1443.
18. Takayuki Ishida, Kazumi Yamawaki, Hideki Noda, Michiharu (2009), Performance improvement of JPEG2000 steganography using QIM, Journal of Communication and Computer, Volume 6 (1), USA.
19. M.U. Celik, G. Sharma, A.M. Tekalp, and E. Saber (2002), Reversible Data Hiding, In Proc. of International Conference on Image Processing, Rochester, NY, USA, Vol. 2, pp. 157-160
20. Yeh-Shun Chen, Ran-Zan Wang, Yeuan-Kuen Lee, Shih-Yu Huang (2008), Steganalysis of reversible contrast mapping watermarking, Proceedings of the world congress on Engineering 2008, Vol I, WCE2008, London, U.K., pp. 555-557.
21. Fridrich, J., Goljan, M., and Du, R. (2001), Reliable Detection of LSB Steganography in Grayscale and Color Images, Proc. of ACM: Special Session on Multimedia Security and Watermarking, Ottawa, Canada, pp. 27-30.
22. S. P. Hivrale, S. D. Sawarkar, Vijay Bhosale, and Seema Koregaonkar (2008), Statistical Method for Hiding Detection in LSB of Digital Images: An Overview, Proceedings of World Academy of Science, Engineering and Technology, Volume 32, ISSN 2070-3740, pp. 658-661.
23. K. M. Sullivan (2005), Image steganalysis: Hunting and Escaping, Ph. D Thesis in Electrical and computer Engineering, University of California.
24. A. Westfeld and A. Pfitzmann (1999), Attacks on steganographic systems, In Lecture notes in computer science: 3rd International Workshop on Information Hiding.
