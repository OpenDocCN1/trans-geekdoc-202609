
- 7. Y. Zhou, K. Panetta, S. Agaian, and C. L. P. Chen. Image encryption using p-fibonacci transform and decomposition. Optics Communications, 285(5):594–608, 2012.
- 8. S. K. Abd-El-Hafiz, S. H. AbdElHaleem, and A. G. Radwan. Novel permutation measures for image encryption algorithms. Optics and Lasers in Engineering, 85:72–83, 2016.
- 9. B. Mondal and T. Mandal. A multilevel security scheme using chaos based encryption and steganography for secure audio communication. International Journal of Research in Engineering and Technology, 2(10):399–403, 2013.
- 10. W. Yanling. Image scrambling method based on chaotic sequences and mapping. In Education Technology and Computer Science, 2009. ETCS'09. First International Workshop on, Vol. 3, pp. 453–457, March 2009.
- 11. S. M. H. Alwahbani and E. B. M. Bashier. Speech scrambling based on chaotic maps and one time pad. In Computing, Electrical and Electronics Engineering (ICCEEE), 2013 International Conference on, pp. 128–133, August 2013.
- 12. W. Liu, K. Sun, and C. Zhu. A fast image encryption algorithm based on chaotic map. Optics and Lasers in Engineering, 84:26–36, 2016.
- 13. B. Mondal and T. Mandal. A light weight secure image encryption scheme based on chaos dna computing. Journal of King Saud University-Computer and Information Sciences, 29(4):499–504, 2017.
- 14. B. Mondal, T. Mandal, N. Biswas, and P. Kumar. A secure partial encryption scheme based on bit plane manipulation. In 7th International Symposium on Embedded Computing and System Design 2017 (ISED), pp. 1–5, 2017.
- 15. Z. Parvin, H. Seyedarabi, and M. Shamsi. A new secure and sensitive image encryption scheme based on new substitution with chaotic function. Multimedia Tools and Applications, 75(17):10631–10648, 2014.
- 16. J. Chen, Z. Zhu, C. Fu, H. Yu, and L. Zhang. An efficient image encryption scheme using gray code based permutation approach. Optics and Lasers in Engineering, 67:191–204, 2015.
- 17. Y. Zhou, K. Panetta, S. Agaian, and C. L. P. Chen. (n, k, p)-gray code for image systems. IEEE Transactions on Cybernetics, 43(2):515–529, 2013.
- 18. C. Fu, B. Lin, Y. Miao, X. Liu, and J. Chen. A novel chaos-based bit-level permutation scheme for digital image encryption. Optics Communications, 284(23):5415–5423, 2011.
- 19. A. Jolfai, X. W. Wu, and V. Muthukkumarasamy. On the security of permutation-only image encryption schemes. IEEE Transactions on Information Forensics and Security, 11(2):235–246, 2016.
- 20. Y. Li, C. Wang, and H. Chen. A hyper-chaos-based image encryption algorithm using pixel-level permutation and bit-level permutation. Optics and Lasers in Engineering, 90:238–246, 2017.
- 21. X. Li. A generalized matrix-based scrambling transformation and its properties. In Young Computer Scientists, 2008. ICYCS 2008. The 9th International Conference for, pp. 1429–1434, November 2008.
- 22. P. Premaratne and M. Premaratne. Key-based scrambling for secure image communication. In D.-S. Huang, P. Gupta, X. Zhang, and P. Premaratne, editors, Emerging Intelligent Computing Technology and Applications, Vol. 304 of Communications in Computer and Information Science, pp. 259–263. Springer, Berlin, Germany, 2012.
- 23. R.-G. Zhou, Y.-J. Sun, and P. Fan. Quantum image gray-code and bit-plane scrambling. Quantum Information Processing, 14(5):1717–1734, 2015.
- 24. Y. Zhang, K. Lu, Y. Gao, and M. Wang. Neqr: A novel enhanced quantum representation of digital images. *Quantum Information Processing*, 12(8):2833–2860, 2013.
- 25. Y. Dodis and A. Smith. Entropic security and the encryption of high entropy messages. Cryptology ePrint Archive, Report 2004/219, 2004. http://eprint.iacr.org/2004/219.
- 26. C. E. Shannon. Communication theory of secrecy systems. *Bell System Technical Journal*, 28:656–715, 1949.
- 27. T. Siegenthaler. Correlation-immunity of nonlinear combining functions for cryptographic applications (corresp.). *IEEE Transactions on Information Theory*, 30(5):776–780, 1984.
- 28. H. M. Elkhamchouchi and M. A. Makar. Measuring encryption quality for bitmap images encrypted with rijndael and kamkar block ciphers. In *Proceedings of the Twenty-Second National Radio Science Conference*, 2005. NRSC 2005, pp. 277–284, March 2005.
- 29. M. A. Sutton, J. J. Orteu, and H. Schreier. *Image Correlation for Shape, Motion and Deformation Measurements: Basic Concepts, Theory and Applications*. Springer, New York, 2009.

## Chapter 3

## Chaos-Based Image Cryptography

Charles Z. Liu, Linda Y. Dong and Raymond P. Shaw

## Contents

- 3.1 Introduction........................................................68
- 3.1.1 Background........................................................68
- 3.1.2 Chaotic Encryption...............................................69
- 3.1.3 Organization of the Chapter......................................70
- 3.2 Relevant Methods...................................................70
- 3.2.1 Logistic Mapping.................................................71
- 3.2.2 Tent Mapping.....................................................71
- 3.2.3 Sine Map..........................................................72
- 3.2.4 Sawtooth-Bernoulli Map...........................................72
- 3.2.5 Gaussian Map.....................................................72
- 3.2.6 Multidimensional Maps............................................73
- 3.3 Compounded Chaotic Cryptography....................................73
- 3.4 Case Study: Cryptography for Biometrics.............................74
- 3.4.1 Biometrics........................................................74
- 3.4.2 Security of Biometric............................................75
- 3.4.3 Materials.........................................................76
- 3.4.4 Tests and Results...............................................77
- 3.5 Analysis............................................................80
- 3.5.1 Key Space Analysis..............................................81
- 3.5.2 Sensitivity Analysis............................................81
- 3.5.3 Performance Analysis........................................82
- 3.5.3.1 Correlation Analysis.....................................83
- 3.5.3.2 Uniform Analysis.........................................83
- 3.5.3.3 Analysis Results.........................................84
- 3.6 Discussion....................................................89
- 3.6.1 Effectiveness..............................................89
- 3.6.2 Implementation.............................................90
- 3.6.3 Anti-attack................................................90
- 3.6.3.1 Brute Force Attack.......................................90
- 3.6.3.2 Hill Climbing Attack.....................................91
- 3.7 Conclusion....................................................92
- References.......................................................92

## 3.1 Introduction

### 3.1.1 Background

Information security gains increasing weight in modern information exchanging and system networking, and cryptography serves as an important foundation for guaranteeing the trustworthy data communication. With the access of diverse multimedia content in an information system, data such as image, speech, and video, it brings many new properties to communication as well as challenges in security. Image cryptography is a technique to cipher an original image by encoding its elements (usually pixels) with an algorithm to convert the plaintext information into an encrypted form that's hard to read its meaning. Usually, the ciphered information can be recovered by a corresponding decryption processing to decode the encrypted information back to its original meaning. To build a bridge between encryption and decryption for the plaintext, a key, usually a set of characters, is required as a clue for the algorithm to encode and decode the information correspondingly.

Conventional ciphering strategies, such as Data Encryption Standard (DES), International Data Encryption Algorithm (IDEA), Rivest–Shamir–Adleman (RSA) serve sufficiently for data like words and characters, but are not suitable for information in complex forms like image or voice, thus rendering its weakness on applications. This is especially true for online communication or of data that is complicated and large [4]. Even though conventional methods can be embedded into the encoded part of the system for encrypting the information with transforming the original data like image or voice into a coded form, the efficiency and effectiveness may not be stable. Besides time-consumption, in some cases directly applying traditional methods may cause inferior performance on scrambling. What is more, inappropriate encryption would result in the risk of data loss caused by residual transcoding errors and improper decryption, thus failing to restore the original data since distortion caused losing partial information.
