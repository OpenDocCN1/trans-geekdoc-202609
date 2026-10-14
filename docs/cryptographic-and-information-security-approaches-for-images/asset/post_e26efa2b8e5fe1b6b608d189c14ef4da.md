
Solving and finding the slope:

$s = \begin{cases} \dfrac{y_2 - y_1}{x_2 - x_1} \mod p & \text{if } P \neq Q & \text{Addition} \\ \dfrac{3x_1^2 + a}{2y_1} \mod p & \text{if } P = Q & \text{Doubling} \end{cases} \tag{6.21}$

**Note:** This is one of the most important properties that ECC follows, this result will be used in finding the keys.

## WORKING OF ECC

### Phase 1: Setup

- 1. Both Alice and Bob agree common ECC equation, let's say:
- $E: y^2 = x^3 + a x + b,$
- And prime elements on this curve $(x_p, y_p)$

### Phase 2: Protocol

- 1. Alice generates its private key: $a = K_{pr A} \in \{2,3,\dots,\#E -1\}$ where $E$ is cardinality of group.
- 2. Bob generates its private key: $b = K_{pr B} \in \{2,3,\dots,\#E -1\}$ where $E$ is cardinality of group.
- 3. Alice and Bob generate their public keys using:
- $A = K_{\text{pub }A} = a.P = (x_A, y_A) \tag{6.22}$
- $B = K_{\text{pub }B} = b.P = (x_B, y_B) \tag{6.23}$
- 4. Now both Alice and Bob will generate:
- $a.B = (X_{AB}, Y_{AB}) \tag{6.24}$
- $b.A = (X_{AB}, Y_{AB}) \tag{6.25}$
- 5. Message m let's say a video can be encrypted through AES using $X_{AB}$ as a key.
- $$C = AES_{X_{AB}}(m) \tag{6.26}$$
- 6. Decryption will be done using the same $X_{AB}$
- $$m = AES^{-1}_{X_{AB}}(C) \tag{6.27}$$

**Note:** For calculating $a.P$, $b.P$, $a.B$, and $b.A$ we will use Equation 6.21.

## 6.3.1 Advantages of ECC Over RSA

The following are the advantages of ECC over RSA.

### 6.3.1.1 Security

The sub-exponential attack is identified in RSA because of its fast computation of the addition operation. It will not be easy to carry sub-exponential attacks in ECC because of point addition, which is computationally expensive. Therefore, the number of bits required to make RSA key pairs safe is increasing exponentially with respect to the bit required to make key pairing safe in ECC. Jurisic and Menezes [46] studied that to make RSA secure, 1024-bit modulus is required as compared to 160-bit modulus required for ECC (Table 6.6).

Table 6.6 Keys Size Comparison vs. Cracking Time for RSA and ECC

| RSA Key Size in Bits | ECC Key Size in Bits | Time to Crack in MIPS-year |
|---|---|---|
| 512 | 106 | $10^4$ |
| 768 | 132 | $10^8$ |
| 1024 | 160 | $10^{11}$ |
| 2048 | 210 | $10^{20}$ |
| 21000 | 600 | $10^{78}$ |

### Table 6.7 Comparison of RSA and ECC

| Function | ECC-163-bit (in ms) | RSA-1024bit (in ms) |
|---|---|---|
| Key generation | 3.8 | 4708.3 |
| Sign | 2.1(ECNRA) | 228.4 |
|  | 3.0(ECDSA) |  |
| Verify | 9.9(ECNRA) | 12.7 |
|  | 10.7(ECDSA) |  |

### 6.3.1.2 Space

Since ECC guarantees to give RSA-like security with low key size, the number of transistors over chip is also less as compared to an RSA encrypted system on chip. However, the bandwidth consumption for both the SoCs (system on chip) will be the same but for a shorter message; ECC SoC performs better because it is fast.

### 6.3.1.3 Efficiency

ECC and RSA can be modified to run fast by using a smaller exponential in RSA, which can directly impact its security, or by storing the result beforehand in ECC, which directly impacts the space requirement. Certicom, the company behind the ECC, studied the impact of fast ECC and modified RSA (Table 6.7).

## Exercise

Exercise 6.1: Hill Cipher—A polygraphic substitution cipher, which uses m × m invertible matrix in Z₂₆ as a secret key. Hill cipher comprises two steps:
Step 1: Encode the message into sequence block of m Z₂₆ integers.
Step 2: Separately encrypt each block by using the product with secret matrix.

Recover m and secret key for the following message using known plain text attack.
Message: conversation
Encrypted message: HIARRTNUYTUS

Exercise 6.2: Vigenère cipher—A polyalphabetic substitution cipher, which uses an alphabetic key to encrypt a message. Using vigenère cipher, encrypt the word “knowledge” using the key “books.”

Exercise 6.3: Data Encryption Algorithm (DES)—A symmetric key algorithm for encryption of electronic data. DES has several modes of operations like ECB, CFB, CBC, OFB, these modes differ in generating ciphertext block from plain text block. Explain all the modes in detail and also sketch the block diagrams for encryption and decryption for each mode.

Exercise 6.4: Show that decryption of b_i and b_{i+1} remains unchanged, if opponent can replace one cipher text block while the decryption of the rest of the block is changed.
Exercise 6.5: Not all DES keys are strong. Weak keys exist if DES_k is an involution where k is a key. Show four weak keys for DES.
Exercise 6.6: Image segmentation uses different kinds of operators for identifying the edges in an image. Write the advantages and disadvantages for each operator and also mention the condition in which the particular operator is used.
Exercise 6.7: Write the advantages and disadvantages for both block selection and pixel selection techniques in images.
Exercise 6.8: Write the conditions in which spatial domain image encryption techniques and frequency domain techniques are used. Give some real-life examples which support your answer.
Exercise 6.9: Write the steps required for surveillance video transfer among two points. Include the steps for encryption, transferring, and decryption of video. Give proper justification for techniques used for the below two scenarios:
Scenario 1: Surveillance video is first stored completely then transferred (non-real-time).
Scenario 2: Surveillance video is encrypted and transferred in real-time with no intermediate data storage unit.
Exercise 6.10: ECC has various advantages over RSA which includes robustness of small key size, faster generation of keys, etc. Discuss the disadvantages of ECC over RSA and give some examples which support your answer.

## References

- 1. Ibn Wahshiyya's translation of the Ancient Egyptian hieroglyph alphabet. [online]. Available: https://en.wikipedia.org/wiki/Egyptian_hieroglyphs#/media/File:Ibn_Wahshiyya%27s_985_CE_translation_of_the_Ancient_Egyptian_hieroglyph_alphabet.jpg (accessed October 30, 2017).
- 2. A. A. Soofi, I. Riaz, and U. Rasheed, An enhanced vigenere cipher for data security, Int. J. Sci. Technol. Res., 5(3), 141–145, 2016.
- 3. B. A. Mohammed Haris, A survey paper on different modification of playfair cipher, Int. J. Adv. Res. Comput. Sci., 8(5).
- 4. M. Rahman, A. Nordin, A. F. A. Abidin, and M. K. Yusof, Cryptography: A new approach of classical hill cipher, Int. J. Secur. Appl., 7(2), 179–190, 2013.
- 5. V. Laforet, The hobbit. [online]. Available: https://gizmodo.com/5969817/the-hobbit-an-unexpected-masterclass-in-why-48-fps-fails.
- 6. K. Jalesh and S. Nirmala, A hybrid approach for enhancing the security of information content of an image, in Multimedia Processing, Communication and Computing Applications: Proceedings of the First International Conference, ICMCCA, December 13–15, 2012. P. P. Swamy and D. S. Guru, Eds. New Delhi, India: Springer, 2013, pp. 169–180.
- 7. N. A. Flayh, R. Parveen, and S. I. Ahson, Wavelet based partial image encryption, in 2009 IEEE International Multimedia, Signal Processing and Communication Technologies, Aligarh, India, 2009, pp. 32–35.
- 8. A. K. Yekkala, N. Udupa, N. Bussa, and C. E. V. Madhavan, Lightweight encryption for images, in 2007 Digest of Technical Papers International Conference on Consumer Electronics, 2007, pp. 1–2.
- 9. R. Munir, Robustness analysis of selective image encryption algorithm based on arnold cat map permutation, Proc. 3rd Makassar Int. Conf. Electr. Eng. Informatics, pp. 1–5, 2012.
- 10. R. Krishnamoorthi and P. D. S. K. Malarchveli, Selective combinational encryption of gray scale images using orthogonal polynomials based transformation, Int. J. Comput. Sci. Netw. Secur., 8(5), 195–204, 2008.
- 11. Y. V Subba Rao, A. Mitra, and S. R. Mahadeva Prasanna, A partial image encryption method with pseudo random sequences, in Information Systems Security: Second International Conference, ICISS 2006, Kolkata, India, December 19–21. A. Bagchi and V. Atluri, Eds. Berlin, Germany: Springer, 2006, pp. 315–325.
- 12. M. A. A. Steffi and D. Sharma, Comparative study of partial encryption of images and video, Int. J. Mod. Eng. Res., 1(1), 179–185, 2011.
- 13. Y. Ou, C. Sur, and K. H. Rhee, Region-based selective encryption for medical imaging, in Frontiers in Algorithmics: First Annual International Workshop, FAW 2007, Lanzhou, China, August 1–3.
- 14. W. Zhang, K. Wong, H. Yu, and Z. Zhu, A symmetric color image encryption algorithm using the intrinsic features of bit distributions, Commun. Nonlinear Sci. Numer. Simul., 18(3), 584–600, 2013.
- 15. H. T. Panduranga and S. K. NaveenKumar, Selective image encryption for medical and satellite images, Int. J. Eng. Technol., 5(1), 115–121, 2013.
- 16. S. Bahrami and M. Naderi, Image encryption using a lightweight stream encryption algorithm, Adv. Multimed., 2012, 1–8, 2012.
- 17. J.-Y. Oh, D.-I. Yang, and K.-H. Chon, A selective encryption algorithm based on AES for medical information, Healthc. Inform. Res., 16(1), 22, 2010.
- 18. A. Wong and W. Bishop, Backwards compatible, multi-level Region-of-Interest (ROI) image encryption architecture with biometric authentication, Int. Conf. Signal Process. Multimed. Appl., 324–329, 2007.
- 19. F. Dufaux, S. J. Wee, J. G. Apostolopoulos, and T. Ebrahimi, JPSEC for secure imaging in JPEG 2000, in Applications of Digital Image Processing XXVII, A. G. Tescher, Ed. SPIE, November 2004.
- 20. P. Kumar and P. K. Pateriya, RC4 enrichment algorithm approach for selective image encryption, Int. J. Comput. Sci. Commun. Networks, 2(2), 181–189, 2012.
- 21. Z. Brahimi, H. Bessalah, A. Tarabet, and M. K. Kholladi, A new selective encryption technique of JPEG2000 codestream for medical images transmission, in 2008 5th International Multi-Conference on Systems, Signals and Devices, 2008, pp. 1–4.
- 22. H. A. Younis, T. Y. Abdalla, and A. Y. Abdalla, Vector quantization techniques for partial encryption of wavelet-based compressed digital images, Iraqi J. Electr. Electron. Eng., 5(1), 74–89, 2009.
- 23. K. Kuppusamy and K. Thamodaran, Optimized partial image encryption scheme using PSO, in International Conference on Pattern Recognition, Informatics and Medical Engineering (PRIME-2012), 2012, pp. 236–241.
- 24. R. E. L. Metzler and S. S. Agaian, Selective region encryption using a fast shape adaptive transform, in 2010 IEEE International Conference on Systems, Man and Cybernetics, 2010, pp. 1763–1770.
- 25. S. Sasidharan and D. S. Philip, A fast partial encryption scheme with wavelet transform and RC4, Int. J. Adv. Eng. Technol., 1(4), pp. 322–331, 2011.
- 26. N. Taneja, B. Raman, and I. Gupta, Combinational domain encryption for still visual data, Multimed. Tools Appl., 59(3), 775–793, 2012.
