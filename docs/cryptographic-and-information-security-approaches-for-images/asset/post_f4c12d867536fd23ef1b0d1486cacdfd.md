
distance is less than the threshold, this matching point is accurately matched; otherwise, the matched point is deleted, and the tolerance error is empirically determined.

**Fourth stage:** In each iteration, the number of points that have been matched accurately is calculated. If the number of points that are accurately matched is more than the desired value, or reaches the predetermined maximum number of iterations, the algorithm stops. At the end, all the matching points, based on the transformation model that has the largest number of accurate matchings, are again calculated.

## 26.8 Experiment and Results

In this section, the functions of the proposed methods are evaluated by the MICC-F220 dataset (Amerini et al. 2011). The MICC-F220 dataset consists of 220 images where 110 are tampered and 110 are original. To investigate the effectiveness of the proposed methods, they are also compared with the method presented in Fridrich et al. (2003), Popescu and Farid (2004) and Amerini et al. (2011). In the following, evaluation criteria and simulation results are presented.

### 26.8.1 Evaluation Criteria

In order to evaluate the proposed method, three common evaluation criteria, i.e. the True Positive Rate (TPR) according to Equation 26.17, False Positive Rate (FPR) according to Equation 26.18 and precision according to Equation 26.19 are used. As the TPR and precision are higher and FPR is lower, those two are more suitable.

TPR = T_p / N  (26.17)

FPR = F_p / M  (26.18)

Precision = T_p / (T_p + F_p)  (26.19)

where:
- T_p is the number of forgery images that are correctly identified as forgery
- N is the number of forgery images
- F_p is the number of original images that are detected as forgery
- M is the number of original images.

### 26.8.2 Examining the Performance of the Proposed Method by the MICC-F220 Database

In this section, using images from the MICC-F220 database, we investigate the performance of the proposed method on CMFD images, the result of which can be seen in Figure 26.11 and Table 26.1.

As Figure 26.11 shows, by the removal of the redundant keypoints, the proposed method reduces mismatches and ultimately increases the accuracy of CMFD. According to Table 26.1, it is seen that method (Fridrich et al. 2003) based on DCT and method (Popescu and Farid 2004) based on PCA have acceptable TPR but not acceptable FPR. The low performance of these two methods comes from the forging areas in this database. Scale and translation changes render these methods inappropriate for identifying forgery areas with geometric distortions. The proposed method has better performance compared to that of (Amerini et al. 2011) as it reduces mismatches, which ultimately reduces FPR. The proposed method has more precision compared to other methods, showing its better performance in detecting the areas of copy-move forgery.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_817_0.png)

Figure 26.11 Copy-move image forgery detection. (a) forgery detection by Amerini method [36], (b) forgery detection by the proposed method, (c) forgery detection by Amerini method [36], (d) forgery detection by the proposed method.

## Table 26.1 Copy-Move Forgery Detection Results of Different Methods by Classic Criteria

| Method | TPR (%) | FPR (%) | Precision |
|---|---|---|---|
| Fridrich et al. (2003) | 89 | 84 | 0.514 |
| Popescu and Farid (2004) | 87 | 86 | 0.494 |
| Amerini et al. (2011) | 100 | 8 | 0.925 |
| Proposed method | 100 | 3 | 0.970 |

## 26.9 Conclusion

In this chapter, while introducing forgery detection methods, we dealt with a more precise examination of the problem of copy-move forgery as one of the most important and common types of forgery. For this purpose, two general classifications, including keypoint-based and block-based methods were examined. By examining these methods, it was concluded that keypoint-based methods have better performance. Hence, in this section, a keypoint-based method is used. In this chapter, a keypoint-based method based on redundant keypoint removal in the SIFT algorithm was used to identify forged areas. The experiments were carried out by MICC-F220 database (Amerini et al. 2011). The results of the experiments were evaluated using standard evaluation criteria and compared with classical methods. The results thereof proved the better efficiency and capability of the proposed method in detecting forged areas.

## Exercises

- Examine the types of areas that can be tampered with in copy-move forgery.
- Examine which type of copy-move forgery each of the methods (keypoint-based and block-based) is used more.
- Check the performance of the proposed method by adding Gaussian noise with the standard deviations 3, 4, and 5 on MICC-F220 images.
- Check the performance of the proposed method by adding different JPEG transforms to MICC-F220 images.

## References

Amerini, I., Ballan, L., Caldelli, R., Del Bimbo, A., Del Tongo, L., Serra, G. 2013. Copy-move forgery detection and localization by means of robust clustering with J-Linkage. Signal Processing: Image Communication 28 (6): 659–669.

Amerini, I., Ballan, L., Caldelli, R., Del Bimbo, A., Serra, G. 2011. A SIFT-based forensic method for copy-move attack detection and transformation recovery. IEEE Transactions on Information Forensics and Security 6 (3): 1099–1110.

Ansari, M. D., Ghrera, S., Tyagi, V. 2014. Pixel-based image forgery detection: A review. IETE Journal of Education 55 (1): 40–46.

Bay, H., Tuytelaars, T., Van Gool, L. 2006. Surf: Speeded up robust features. 9th European Conference on Computer Vision–ECCV, Austria. pp. 404–417.

Bayram, S., Sencar, H. T., Memon, N. 2009. An efficient and robust method for detecting copy-move forgery in Acoustics, Speech and Signal Processing. IEEE 12th International Conference on Computer Vision, pp. 1053–1056.

Bin, Y., Xingming, S., Xianyi, C., Zhang, J., Xu, L. 2013. An efficient forensic method for copy-Move forgery detection based on DWT-FWHT. Radioengineering 22 (4).

Birajdar G. K., Mankar, V. H. 2013. Digital image forgery detection using passive. Digital Investigation 10 (3): 226–245.

Dixit A., Gupta, R. 2016. Copy-move image forgery detection: a review. International Journal of Image, Graphics and Signal Processing 8 (6): 29.

Fan, Y., Zhu, Y.-S., Liu, Z. 2016. An improved SIFT-based copy-move forgery detection method using T-linkage and multi-scale analysis. Journal of Information Hiding and Multimedia Signal Processing 7 (2): 399–408.

Fischler, M. A., Bolles, R. C. 1981. Random sample consensus: A paradigm for model fitting with applications to image analysis and automated cartography. Communications of the ACM 24 (6): 81–395.

Fridrich, A. J., Soukal, B. D., Lukáš, A. J. 2003. Detection of copy-move forgery in digital images. In Proceedings of Digital Forensic Research Workshop, August 2003, Cleveland, OH, USA.

Gan, Y., Zhong, J. 2014. Image copy-move tamper blind detection algorithm based on integrated feature vectors. Journal of Chemical and Pharmaceutical Research 6 (6): 1584–1590.

Guo, X., Cao, X., Zhang, J., Li, X. 2009. Mift: A mirror reflection invariant feature descriptor. In Asian Conference on Computer Vision pp. 536–545.

Huang, H., Guo, W. and Zhang, Y. 2008. Detection of copy-move forgery in digital images using in Computational Intelligence and Industrial Application. IEEE 2: 272–276.

Han, Q., Yu, L., Niu, X. 2016. Feature point-based copy-move forgery detection: Covering the non-textured areas. Multimedia Tools and Applications 75 (2): 1159–1176.

Harris, C., Stephens, M. 1988. A combined corner and edge detector. In Alvey Vision Manchester, UK 10 (50): 10–5244.

Hossein-Nejad, Z., Nasri, M. 2017. RKEM: Redundant keypoint elimination method in image registration. IET Image Processing 11 (5): 273–284.

Junhong, Z. 2010. Detection of copy-move forgery based on one improved LLE method in advanced computer control (ICACC). 2nd International Conference on IEEE pp. 547–550.

Lee, J.-C., Chang, C.-P., Chen, W.-K. 2015. Detection of copy-move image forgery using histogram of orientated gradients. Information Sciences 321: 250–262.

Li, L., Li, S., Zhu, H., Wu, X. 2014. Detecting copy-move forgery under affine transforms for image forensics. Computers & Electrical Engineering 40 (2): 1951–1962.

Lin, H.-J., Wang, C.-W., Kao, Y.-T. 2009. Fast copy-move forgery detection, WSEAS Transactions on Signal Processing 5 (5): 188–197.
