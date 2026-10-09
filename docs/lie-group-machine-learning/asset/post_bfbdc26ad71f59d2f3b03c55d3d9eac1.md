
![](img/456a7a56403cbb2b5f1a261793529a51_331_0.png)

**Fig. 9.14:** Classification accuracy map using the (9.75) after 100 times to calculate. Abscissa represents the calculation times and vertical coordinates represents the classification accuracy.

![](img/456a7a56403cbb2b5f1a261793529a51_331_1.png)

**Fig. 9.15:** Shows incorrect test examples of algorithm 9.4.

This is probably because the covariance manifold structure is generally close to linear but locally uneven after adding the operator; hence, Algorithm 9.5 uses log-Euclidean, but the standard Lie group distance $d(X_1, X_2) = \|\log(X_1^{-1}X_2)\|$ is used in the calculation of (9.44), rather than the affine invariant distance (9.23). Thus, the errors generated during the calculation are amplified in the case of when multiple mappings between Lie group and Lie algebra.

In addition, Figure 9.13(a) shows the effect of only using a 5-dimensional vector on $z_i$, with faster calculation. With the configuration of Intel i5 dual-core CPU (1.6 GHz), 4 GB memory, and MATLAB 2011b, for Algorithm 9.4, the total training and classification time of 200 training samples and 200 test samples is less than 1 second, and the classification accuracy is basically maintained at around 98%, as shown in Figure 9.14. Therefore, Algorithm 9.4 is suitable for applications where the speed requirements are relatively high, such as target tracking and rapid detection. Figure 9.15 shows incorrect test examples of Algorithm 9.4.

## 9.7 Summary

In this chapter, we started with the geometrical structure of the Lie group and Lie algebra, and tried to find a geodesic line on the Lie group manifold and project Lie group samples to the geodesic line, and maximised the ratio of divergence between classes and divergence within the classes after projection, so as to realise class discrimination of the nonlinear Lie group space. Then, through the study of matrix theory and the kernel method, combined with Lie group geodesic theory, the kernel function based on the matrix Lie group was designed and realised. Thus, we extended Lie group machine learning to the classification and dimension reduction algorithm based on the kernel method. The Lie-group-based Lie–Fisher and KlieDA algorithms were shown to have high classification accuracy compared with the traditional method. The Lie–Fisher algorithm solves the problem of geodesic classification in Lie group manifold space. KlieDA solves the problem of high-dimensional spatial mapping and classification of nonlinear matrix Lie group samples.

## Bibliography

- [1] Kondor R. **Group Theoretical Methods in Machine Learning**. 2008.
- [2] Fletcher T, Lu C, Joshi S. Statistics of Shape via Principal Geodesic Analysis on Lie Groups. IEEE Conference on Computer Vision and Pattern Recognition, **2003**, 1, **95**–**101**.
- [3] Fletcher PT, Lu C, Pizer SM, Joshi S. Principal geodesic analysis for the study of nonlinear statistics of shape. **IEEE Transactions on Medical Imaging**, **2004**, **23**(8), **995**–**1005**.
- [4] Bayro CE, Ortegon AJ. Template Tracking with Lie Algebras. **IEEE International Conference on Robotics and Automation**, **2004**, 5, **5183**–**5188**.
- [5] Bayro CE, Ortegon AJ. Lie Algebra Template Tracking. International Conference on Pattern Recognition, **2004**, 2, **56**–**59**.
- [6] Fiori S. Unsupervised Neural Learning on Lie Group. **International Journal of Neural Systems**, **2002**, **12**(3–4), **219**–**246**.
- [7] Tournier M, Wu X, Courty N, Arnaud E, Reveret L. Motion Compression using Principal Geodesics Analysis. **ACM Conference on Computer and Communications Security**, **2008**, **28**(2), **355**–**364**.
- [8] Li G, Liu Y, Yin J, Shi ZL. Projective Tracking Based on Second-order Optimization on Lie Manifolds. **Chinese Conference on Pattern Recognition**, **2008**, 1–6.
- [9] Fletcher PT, Joshi S, Lu C, Pizer S. Gaussian Distributions on Lie Groups and Their Application to Statistical Shape Analysis. **International Conference on Information Processing and Medical Imaging, LNCS** **2732**, **2003**, **450**–**462**.
- [10] Yarlagadda P, Ozcanli O, Mundy J. Lie Group distance based generic 3-d vehicle Classification. **International Conference on Pattern Recognition**, **2008**, 1–4.
- [11] Li G, Liu Y, Shi ZL, Yin J. Optimization on Lie Manifolds and Projective Tracking. **CSSE**, **2008**, 1, **768**–**771**.
- [12] Maher M. Means and Averaging in the Group of Rotations. **SIAM Journal on Matrix Analysis and Applications**, **2002**, **24**(1), 1–16.
- [13] Fiori S, Tanaka T. An Algorithm to Compute Averages on Matrix Lie Groups. **IEEE Transactions on Signal Processing**, **2009**, **57**(12), **4734**–**4743**.
- [14] Fiori S, Tanaka T. Learning Averages over the Lie Group of Symmetric Positive-Definite Matrices. **International Joint Conference on Neural Networks**, **2009**, **828**–**832**.
- [15] Lin DH, Grimson E, Fisher J. Learning visual flows: A Lie algebraic approach. **IEEE Conference on Computer Vision and Pattern Recognition**, **2009**, **747**–**754**.
- [16] Poriikli F, Tuzel O, Meer P. Covariance Tracking using Model Update Based on Lie Algebra. **IEEE Conference on Computer Vision and Pattern Recognition**, **2006**, **728**–**735**.
- [17] Chen DQ, Han JQ, Yu Z. Visual Tracking Using Region Covariance and Geometric Particle Filtering. International Congress on Image and Signal Processing (CISP), 2010, 1, 381–386.
- [18] Doretto G, Yao Y. Region Moments: Fast invariant descriptors for detecting small image structures. IEEE Conference on Computer Vision and Pattern Recognition, 2010, 3019–3026.
- [19] Tuzel O, Porikli F, Meer P. Learning on Lie Groups for Invariant Detection and Tracking. IEEE Conference on Computer Vision and Pattern Recognition, 2008, 1–8.
- [20] Tuzel O, Porikli F, Meer P. Region Covariance: A Fast Descriptor for Detection and Classification. European Conference on Computer Vision, 2006, 589–600.
- [21] Ando R, Ohki H, Fujita Y. A Comparison with Covariance with Covariance Features on Player Uniform Number Recognition. Korea–Japan Joint Workshop on Frontiers of Computer Vision, 2011, 1–4.
- [22] Penner X, Fillard P, Ayache N. A Riemannian Framework for Tensor Computing. International Journal of Computer Vision, 2006, 66(1), 41–66.
- [23] Tuzel O, Porikli F, Meer P. Human Detection via Classification on Riemannian Manifold. IEEE Conference on Computer Vision and Pattern Recognition, 2007, 1–8.
- [24] Wang CM, Jascha SD, Ivana T, Bruno AO. Lie Group Transformation Models for Predictive Video Coding. Data Compression Conference, 2011, 83–92.
- [25] Arsigny V, Fillard P, Penner X, Ayache N. Geometric means in a novel vector space structure on symmetric positive-definite matrices. SIAM Journal on Matrix Analysis and Applications, 2007, 29(1), 328–347.
- [26] Xu M, Rajesh PNR. Learning the Lie Groups of Visual Invariance. Neural Computation, 2007, 19(10), 2665–2693.
- [27] Plebe A. Learning Visual Invariance. The European Symposium on Artificial Neural Networks, 2006, 73–76.
- [28] Cadieu CF, Olshausen BA. Learning Transformational invariants from Natural Movies. Neural Information Processing Systems, 2008, 209–216.
- [29] Wang Z, Chen SC, Liu J, Zhang DQ. Pattern Representation in Feature Extraction and Classifier Design: Matrix Versus Vector. IEEE Transactions on Neural Networks, 2008, 19(5), 758–769.
- [30] Chen SC, Zhu YL, Zhang DQ, Yang JY. Feature extraction approaches based on matrix pattern: MatPCA and MatPLDA. Pattern Recognition Letters, 2005, 26(8), 1157–1167.
- [31] Mika S, Rätsch G, Weston J, Schölkopf B, Müller KR. Fisher discriminant analysis with kernels. Neural Networks for Signal Processing IX, 1999, 41–48.
- [32] Brun A, Westin CF, Herterhson M, Knutsson H. Intrinsically and Extrinsic Means on the Circle – A Maximum Likelihood Interpretation. International Conference on Acoustics, Speech, and Signal Processing, 2007, 3, 1053–1056.
- [33] Drummond T, Ciplolla R. Real–Time Visual Tracking of Complex Structures. IEEE Transactions on Pattern Analysis and Machine Intelligence, 2002, 24(7), 932–946.
- [34] Dalal N, Triggs B. Histograms of Oriented Gradients for Human Detection. IEEE Conference on Computer Vision and Pattern Recognition, 2005, 1, 886–893.
- [35] Wang QJ, Zhang RB. LPP-HOG: A New Local Image Descriptor for Fast Human Detection. KAMW, 2008, 640–643.
- [36] Dalal N. Finding People in Images and Videos. 2006.
- [37] Stringer SM, Perry R, Rolls ET, Proksche JH. Learning invariant object recognition in the visual system with continuous transformations. Biological Cybernetics, 2006, 94(2), 128–142.
- [38] Charles FC, Bruno AO. Learning Transformational Invariants from Time–Varying Natural Images. Neural Information Processing Systems, 2008.
- [39] Hu MK. Visual pattern recognition by moment invariants. IRE Transactions on Information Theory, 1962, 8, 179–187.
