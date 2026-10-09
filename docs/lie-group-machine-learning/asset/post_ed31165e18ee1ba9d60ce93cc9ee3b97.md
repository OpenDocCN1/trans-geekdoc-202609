
### A. Feature extraction is performed using the concentration of the eigenvalue distribution of the feature matrix.

For each image $A_j^i$, we project it into a 2n-dimensional vector, i.e.,

$$X_j^i = A_j^i v .$$

We call $v$ and $X_j^i$ as projection vectors and projection feature vectors, respectively. After the two images are transformed by the symplectic singular matrix, two new symplectic matrices are obtained. The original images are reconstructed by the two symplectic orthogonal matrices, and the original images are projected onto the two symplectic orthogonal matrices. In this projection space, the symplectic classifier is used for image classification. For different face images, some images are selected as training examples. In this process, the image is extracted by features and then expressed as a symplectic matrix. Using the simplification method of the symplectic matrix, we can simplify the matrix of the image, and the feature subspace of the image can be obtained. Then, the image is used as a training example, and other images in the image library are used as examples to be recognised.

For the image in the image library to be recognised, the image is composed with the same feature combination, the image is represented by the symplectic matrix, and the matrix is then singularly decomposed to obtain the corresponding symplectic representation method. Then, we use the symplectic group classifier algorithm in the face recognition process to deal with the image.

### 3.4.2 Instance validation

To verify the performance of the symplectic group classifier algorithm, we used ORL and YALE, two types of face image libraries, to test the algorithm performance. The ORL library is described in Section 3.3.2. The YALE database consists of 15 people (11 images per person) with greater lighting and facial changes. The hardware environment of the test system is *Pentium* (*R*) 4 *CPU* (2.80 *GHz*) with 512 *MB* memory. The software platform is *MATLAB* 6.5. For an image in the image library, we first calculate its symplectic matrix and use the symplectic algorithm for training. Then, in the database, to find another expression of the same person, according to the correct rate of finding the image, the algorithm recognition efficiency is obtained. As shown in Figure 3.8, the performances of several algorithms are compared.

Figure 3.9 shows the recognition rate of the two classification algorithms in the ORL library. For each class of images in the ORL library, we use the samples 2, 3, ..., 9 as the training samples, and the others as the test samples. Compared with the recognition algorithm, the recognition rate of the image is higher when the training group is larger.

Figure 3.10 shows the recognition rate of the two classification algorithms in the YALE library. For each type of image in the YALE library, 2, 3, ..., 10 images are selected as the classification samples and the others as the test samples. Compared with PCA recognition algorithm, the recognition efficiency of symplectic group classification algorithm is high.

![](img/456a7a56403cbb2b5f1a261793529a51_134_0.png)

Fig. 3.8: Face recognition effect diagram of symplectic group classification algorithm.

![](img/456a7a56403cbb2b5f1a261793529a51_134_1.png)

Fig. 3.9: Face recognition rate in the ORL library.

![](img/456a7a56403cbb2b5f1a261793529a51_135_0.png)

**Fig. 3.10:** Recognition rate in the YALE library.

In the process of recognising the image, we use the symplectic group classification algorithm to use multiple images as the training samples. Here, we give the recognition rate of the symplectic group classification algorithm using only one image as the training sample and other images as the test sample. Through the recognition process, we find that, even with only one image as a training example, the symplectic group classifier algorithm has a higher recognition accuracy. This is because, for an image, the image processed by the symplectic classification algorithm obtains the feature vector of the image, and the feature vector is stable for different images of the same face. Tables 3.3 and 3.4 give the performance comparison of several classification algorithms on the ORL and YALE libraries in the case of only one training sample [36, 37].

**Tab. 3.3:** Performance comparison of several algorithms on ORL Library.

| Classification algorithm | Number of training samples | Average recognition accuracy (%) |
| :--- | :--- | :--- |
| Symplectic group | 1 | 92.6 |
| Spectroface | 1 | 90.8 |
| Linear subspace | 1 | 84.2 |

**Tab. 3.4:** Performance comparison of several algorithms on YALE Library.

| Classification algorithm | Number of training samples | Average recognition accuracy (%) |
|---|---|---|
| Symplectic group | 1 | 92.6 |
| Spectroface | 1 | 95.7 |
| Linear subspace | 1 | 84.4 |

The results show that the accuracy rate of the average recognition is at a high level even when there is only one training classification sample, and the correctness rate of the symplectic group is relatively high compared with the linear subspace method.

# 3.5 Summary

As a new method of machine learning, Lie group machine learning has attracted considerable attention from researchers. At present, Lie group machine learning theory has been applied to many fields, e.g., there have been some successful examples in the field of classification. In this chapter, we discussed the design method of the symplectic group classifier in Lie group machine learning, studied the symplectic group classifier algorithm in the framework of Lie group machine learning, and used the classifier for image recognition and data set classification. Thus, this method was shown to be advantageous.

# Bibliography

- [1] Feng K, Qin MZ. Symplectic Algebraic Algorithm of Hamiltonian System. Zhejiang: Zhejiang University Press, 2006.
- [2] Shaw WT. Symplectic Geometry of null Infinity and Two-surface Twistors. Mathematical Institute, Oxford UK.
- [3] Gao L, Li YM, Chen XR, Yang KQ. An Attempt to Seismic Ray Tracing with Symplectic Algorithm. Chinese Journal of Geophysics, 2000, 5(3), 402–410.
- [4] Wu Y, Hu JY, Yin XG. Symplectic Integrators of the Equations of Multibody System Dynamics on Manifolds. Advantages in Mechanics, 2002, 2(32), 189–195.
- [5] Wang SX, Liu YW, Wu HT. Study on Computational Accuracy of Robot Dynamics. Chinese Journal of Mechanical Engineering, 1998, 34(1), 14–20.
- [6] Han XS, Wang SX, Yu SY. Investigation of Nanomanufacturing Process by Molecular Dynamics Simulation Based on Symplectic Algorithm. Chinese Journal of Mechanical Engineering, 2005, 41(4), 17–22.
- [7] Zhang K. The study on PML-FDTD and Boundary Connecting Conditions of Total-scattering Fields in 3-D Cylindrical Coordinates. Journal of Chongqing University of Posts and Telecommunications, 2003, 3, 21–26.
- [8] Xu ZX, Zhou DY, Deng ZC. Numerical Method Based on Hamilton System and Symplectic Algorithm to Differential Games. Applied Mathematics and Mechanics, 2006, 27(3), 305–310.
- [9] Sun Y, Xie J. Hamiltonian Symplectic Semi-analytical method and its application in anisoTropic electromagnetic waveguide. Chinese Journal of Computational Mechanics, 2005, 22(6), 690–693.
- [10] Zhang PG. A Post-processing Algorithm for the Dynamic Analysis of DNA Elastic Slender Structure. Journal of Qingdao University, 2006, 21(3), 71–74.
- [11] Ritter G, Gallegos MT. A Bayesian approach to object identification in pattern recognition. Proceedings of the International Conference on Pattern Recognition, 2000, IEEE: 1082–1086.
- [12] Lovell BC, Bradley AP. The Multiscale Classifier. IEEE Transactions on Pattern Analysis And Machine Intelligence, 1996, 2(18), 124–137.
- [13] Dawi AHM, Chong TS, Fong SF. The Effects of Different Three–Dimensional Animated Visual Displays in Computer–Based Multimedia on Learners with Different Spatial Abilities. Proceedings of the Fifth IEEE International Conference on Advanced Learning Technologies. IEEE, 2005, ICALT’05, 798–801.
- [14] Tuzel O, Subbarao R, Meer P. Simultaneous Multiple 3D Motion Estimation via Mode Finding on Lie Groups. Proceedings of the Tenth IEEE–International Conference on Computer Vision. Pattern Anal. Machine Intelligence, 2005, 1, 18–25.
- [15] Fletcher PT, Lu CL, Joshi S. Statistics of Shape via Principal Geodesic Analysis on Lie Groups. Proceedings of the 2003 IEEE Computer Society Conference on Computer Vision and Pattern Recognition. Transaction on Medical Imaging, 2003, 1, 95–99.
- [16] Miasnikov AD, Haralick RM. Regression analysis and automorphic orbits in free groups of Rank2. Proceedings of the 17th International Conference on Pattern Recognition. IEEE, 2004, ICPR’04, 180–183.
- [17] Bonmassar G, Schwartz EL. Lie Group, Space–Variant Fourier Analysis and the Exponential Chirp Transform. Proceedings of the 1996 Conference on Computer Vision and Pattern Recognition. IEEE, 1996, CVPR’96, 492–496.
- [18] Yang L, Qin Z, Zhang XP. Classifier Simulation Algorithm and Its Applications. Journal of Xi’an Jiaotong University, 2005, 39(12), 1311–1314.
- [19] Mitchell TM. Machine Learning. Beijing: Machinery Industry Press, 2003.
- [20] He YH, Zhao L, Zou CR. Kernel Nearest Features Classifier for Face Recognition. Journal of Applied Sciences, 2006,24(3), 227–231.
- [21] Squire DM, Caelli TM. Invariance Signatures. Characterizing Contours by Their Departures from Invariance. Computer Vision and Image Understanding, 2000, 77(3), 284–316.
- [22] Zhong WX, Ouyang HJ. Hamiltonian System and Symplectic Geometry in Mechanics of Composite Materials –Plane Stress Problem. Applied Mathematics and Mechanics, 1992, 13(12), 1031–1035.
- [23] Ma ZJ. Group Theory in Physics. Science Press, 2006.
- [24] Lai JH, Yan XH, Deng DG. Finishing the Classifier Design of Spectroface Human Face Recognition. Journal of Image and Graphics, 2002, 7(5), 466–471.
- [25] Yu HB. Detection and Tracking of Human Body Based on Head Feature Extraction and Its Application. Hangzhou: Zhejiang University, 2007.
- [26] Wang P. Research on Classification Algorithm on Data Stream. Shanghai: Fudan University, 2007.
- [27] Xie YH. Research on Some Problems of Face Feature Extraction and Classifier Design. Nanjing: Nanjing University of Science and Technology, 2006.
- [28] Li L. Using Symplectic Geometry to Construct Authentication Codes With Arbitration. Journal of Jilin Architectural and Civil Engineering Institute, 2006, 23(4), 63–67.
- [29] Zhao Lih, Sun XH. Skin Color–Based Face Detection. Journal of Engineering Graphics, 2005, 3, 84–88.
