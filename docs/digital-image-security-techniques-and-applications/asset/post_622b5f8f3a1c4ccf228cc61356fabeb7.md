
### Table 1.4 Subjective analysis of the proposed watermarking method

| Gain factor | Visual Quality |
|---|---|
| 0.005 | Excellent |
| 0.01 | Excellent |
| 0.05 | Excellent |
| 0.09 | Very Good |
| 0.3 | Very Good |
| 0.5 | Very Good |
| 1 | Above Average |
| 1.5 | Acceptable |
| 1.7 | Less than Acceptable |
| 2 | Weak |

![](img/6e4271af21d9a195003ab8711aa79d27_26_0.png)

### Figure 1.5 Subjective analysis of proposed work using histogram.

The histogram of marked image shows sharp peaks, providing statistical information. On the contrary, the histogram of ciphered image is uniform, which makes it robust against statistical attacks. Table 1.5 shows the impact of attacks on the NC score. The NC score against different considered attacks is usually greater than 0.9409, which shows high resistance. Finally, Figure 1.7 confirms high robustness of the proposed work in comparison to the existing work [13], [32], [33]. The result shows 99% more robustness in best case over the traditional schemes, indicating its potential for secure healthcare applications.

![](img/6e4271af21d9a195003ab8711aa79d27_27_0.png)

Figure 1.6 Security analysis of the encryption technique using histogram comparison.

### Table 1.5 Robustness evaluation of the proposed work

| Attack | NC |
|---|---|
| Salt and pepper noise (0.0001, 0.001, 0.01, 0.1) | 0.9943, 0.9936, 0.9889, 0.9514 |
| Gaussian noise (0.0001, 0.001, 0.01, 0.1) | 0.9942, 0.9929, 0.9853, 0.9409 |
| Rotation (1°, 45°, 90°) | 0.9944, 0.9943, 0.9941 |
| JPEG compression (10, 50, 90) | 0.9932, 0.9937, 0.9948 |
| Gaussian low-pass filter (0.4, 0.6) | 0.9943, 0.9943 |
| Speckle noise (0.001, 0.05, 0.5) | 0.9942, 0.9903, 0.9685 |
| Cropping [20 20 400 480] | 0.9928 |
| Median filter ([3 3], [2 2]) | 0.9946, 0.9945 |
| Sharpening mask (0.01, 0.1) | 0.9905, 0.9906 |
| Histogram equalization | 0.9847 |
| Image scaling (0.5, 2) | 0.9949, 0.9921 |

![](img/6e4271af21d9a195003ab8711aa79d27_27_1.png)

Figure 1.7 Comparative analysis of proposed work with Ref. [13], Ref. [32], and Ref. [33].

(Continued)

![](img/6e4271af21d9a195003ab8711aa79d27_28_0.png)

![](img/6e4271af21d9a195003ab8711aa79d27_28_1.png)

Figure 1.7 (Continued) Comparative analysis of proposed work with Ref. [13], Ref. [32], and Ref. [33].

## 1.6 CONCLUSION

In this chapter, a robust and secure watermarking technique using NSCT-based image fusion is proposed for healthcare applications. Initially, NSCT-based fusion is applied on CT scan and MRI images to generate a fused image, used as watermark. Further, the fused mark is concealed in the NSCT-HDMSVD coefficients of the carrier image. The marked image is encrypted with updated stereo image encryption for better security. Also, average PSNR and
NC scores of 54.3941 dB and 0.9903 confirm high visual quality and ability to extract high quality mark. Better robustness is observed in comparison to traditional work with maximum improvement of 99%. The aforementioned outcomes indicate that the suggested solution is useful for the authenticity and copy-protection of the electronic version of COVID-19 patient data.

## ACKNOWLEDGEMENTS

This work is supported by Thapar Institute of Engineering & Technology, Patiala, India, under SEED Research Grant, and research project order no. IES212111 - International Exchanges 2021 Round 2, dt. 28 February 2022, under Royal Society, UK.

## REFERENCES

- [1] S. Salehi, A. Abedi, S. Balakrishnan, and A. Gholamrezanezhad, “Coronavirus disease 2019 (COVID-19): A systematic review of imaging findings in 919 patients,” Am. J. Roentgenol., vol. 215, no. 1, pp. 87–93, 2020, doi: https://www.ajronline.org/doi/10.2214/AJR.20.23034
- [2] “Digital Health Market Size & Growth Report, 2021–2028,” 2021.
- [3] A. Anand and A. K. Singh, “Watermarking techniques for medical data authentication: A survey,” Multimed. Tools Appl., vol. 80, no. 4, pp. 30165–30197, 2021, doi: 10.1007/s11042-020-08801-0
- [4] A. K. Singh, B. Kumar, G. Singh, and A. Mohan, Medical Image Watermarking: Techniques and Applications. Springer International Publishing USA, 2017.
- [5] E. E-D. Hemdan, “An efficient and robust watermarking approach based on single value decomposition, multi-level DWT, and wavelet fusion with scrambled medical images,” Multimed. Tools Appl., vol. 80, no. 19, pp. 1–29, 2021, doi: 10.1007/s11042-020-09769-7
- [6] A. Anand and A. K. Singh, “SDH: Secure data hiding in fused medical image for smart healthcare,” IEEE Trans. Comput. Soc. Syst., vol. 9, no. 4, pp. 1265–1273, 2022.
- [7] A. Anand and A. K. Singh, “Health record security through multiple watermarking on fused medical images,” IEEE Trans. Comput. Soc. Syst., vol. 9, no. 6, pp. 1594–1603, 2021.
- [8] J.-Y. Li and C.-Z. Zhang, “Blind watermarking scheme based on Schur decomposition and non-subsampled contourlet transform,” Multimed. Tools Appl., vol. 79, pp. 30007–30021, 2020, doi: 10.1007/s11042-020-09389-1
- [9] B. Akhbari and S. Ghaemmaghami, “Watermarking of still images using multi-resolution singular value decomposition,” in Intelligent Signal Processing and Communication Systems, ISPACS, 2005, pp. 325–328.
- [10] S. Kumar and G. Bhatnagar, “SIE: An application to secure stereo images using encryption,” in Handbook of Multimedia Information Security: Techniques and Applications, Springer, Cham, 2019, pp. 37–61.
- [11] C. Kumar, A. K. Singh, and P. Kumar, “Improved wavelet-based image watermarking through SPIHT,” Multimed. Tools Appl., vol. 79, no. 15–16, pp. 11069–11082, 2020, doi: 10.1007/s11042-018-6177-0
- [12] F. N. Thakkar and V. K. Srivastava, “A blind medical image watermarking: DWT-SVD based robust and secure approach for telemedicine applications,” Multimed. Tools Appl., vol. 76, no. 3, pp. 3669–3697, 2017, doi: 10.1007/s11042-016-3928-7
- [13] H. S. Alshanbari, “Medical image watermarking for ownership & tamper detection,” Multimed. Tools Appl., vol. 80, pp. 16549–16564, 2021, doi: 10.1007/s11042-020-08814-9
- [14] O. P. Singh and A. K. Singh, “Data hiding in encryption-compression domain,” Complex Intell. Syst., vol. 9, pp. 2759–2772, 2023, doi: 10.1007/s40747-021-00309-w
- [15] A. Anand and A. K. Singh, “Cloud based secure watermarking using IWT-Schur-RSVD with fuzzy inference system for smart healthcare applications,” Sustain. Cities Soc., vol. 75, no. 1, pp. 103398, 2021, doi: 10.1016/j.scs.2021.103398
- [16] A. Soualmi, A. Alti, and L. Laouamer, “Medical data protection using blind watermarking technique,” in Enabling AI Applications in Data Science, Studies in., A.-E. Hassanien et al. (eds.), Springer Nature Switzerland, 2021, pp. 557–576.
- [17] F. Yan, H. Huang, and X. Yu, “A multiwatermarking scheme for verifying medical image integrity and authenticity in the Internet of Medical Things,” IEEE Trans. Ind. Informatics, vol. 18, no. 12, pp. 8885–8894, 2022, doi: 10.1109/TII.2022.3159863
- [18] A. Anand and A. K. Singh, “Joint watermarking-encryption-ECC for patient record security in wavelet domain,” IEEE Multimed., vol. 27, no. 3, pp. 66–75, 2020, doi: 10.1109/MMUL.2020.2985973
- [19] S. Thakur, A. K. Singh, B. Kumar, and S. P. Ghrera, “Improved DWT-SVD-based medical image watermarking through hamming code and chaotic encryption,” in D. Dutta, H. Kar, C. Kumar, V. Bhadauria (eds.), Advances in VLSI, Communication, and Signal Processing. Lecture Notes in Electrical Engineering, vol. 587, Springer Singapore, 2020, pp. 897–905.
- [20] T. Nguyen-Thanh and T. Le-Tien, “Robust blind medical image watermarking using quantization and SIFT with enhanced security,” J. Adv. Inf. Technol., vol. 13, no. 1, pp. 45–52, 2022, doi: 10.12720/jait.13.1.45-52
- [21] A. Soualmi, A. Alti, and L. Laouamer, “A novel blind medical image watermarking scheme based on Schur triangulation and chaotic sequence,” Concurr. Comput. Pract. Exp., vol. 34, no. 1, pp. 1–21, 2022, doi: 10.1002/cpe.6480
- [22] S. P. Vaidya, “Fingerprint-based robust medical image watermarking in hybrid transform,” Vis. Comput., vol. 39, no. 3, pp. 1–16, 2022, doi: 10.1007/s00371-022-02406-4
- [23] J. Ravi and R. Narmadha, “Image fusion based on nonsubsampled shearlet transform,” Int. J. Eng. Adv. Technol., vol. 9, no. 3, pp. 4177–4180, 2020, doi: 10.35940/ijeat.C5452.029320
- [24] Z. Zhao, “The nonsubsampled contourlet transform for image fusion,” in Proceedings of the 2007 International Conference on Wavelet Analysis and Pattern Recognition, 2007, pp. 305–310.
- [25] J. Liu et al., “An optimized image watermarking method based on HD and SVD in DWT domain,” IEEE Access, vol. 7, pp. 80849–80860, 2019, doi: 10.1109/ACCESS.2019.2915596
- [26] G. Bhatnagar, A. Saha, Q. M. J. Wu, and P. K. Atrey, “Analysis and extension of multiresolution singular value decomposition,” Inf. Sci. (Ny)., vol. 277, pp. 247–262, 2014, doi: 10.1016/j.ins.2014.02.018
