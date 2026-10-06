
5. Ding, C. and Peng, H., Minimum redundancy feature selection from microarray gene expression data. *J. Bioinf. Comput. Biol*., 3, 02, 185–205, 2005.

6. Hua, J., Tembe, W.D., Dougherty, E.R., Performance of feature-selection methods in the classification of high-dimension data. *Pattern Recognit*., 42, 3, 409–424, 2009.

7. Yang, C.-S., Chuang, L.-Y., Ke, C.-H., Yang, C.-H., A hybrid feature selection method for microarray classification. *IAENG Int. J. Comput. Sci*., 35, 3, 2008.

8. Wang, S.-L, Li, X.-L, Fang, J, Finding minimum gene subsets with heuristic breadth-first search algorithm for robust tumor classification. *BMC Bioinf*., 13, 1, 178, 2012.

9. Nagpal, A and Singh, V, A feature selection algorithm based on qualitative mutual information for cancer microarray data. *Proc. Comput. Sci*., 132, 244–252, 2018.

10. Chinnaswamy, A, Srinivasan, R, Poolakkaparambil, S.M, Rough set based variable tolerance attribute selection on high dimensional microarray imbalanced data, in: *Data-Enabled Discovery and Applications*, vol. 2(1), p. 7, 2018.

11. Prasad, Y, Biswas, K.K, Hanmandlu, M, A recursive pso scheme for gene selection in microarray data. *Appl. Soft Comput*., 71, 213–225, 2018.

12. Tang, J and Zhou, S, A new approach for feature selection from microarray data based on mutual information. *IEEE/ACM Trans. Comput. Biol. Bioinform*., 13, 6, 1004–1015, 2016.

13. Banerjee, M, Mitra, S, Banka, H, Evolutionary rough feature selection in gene expression data. *IEEE Trans. Syst. Man Cybern., Part C (Appl. Rev.)*, 37, 4, 622–632, 2007.

14. Li, F and Yang, Y, Analysis of recursive gene selection approaches from microarray data. *Bioinformatics*, 21, 19, 3741–3747, 2005.

15. Peng, H, Long, F, Ding, C, Feature selection based on mutual information criteria of max-dependency, max-relevance, and min-redundancy. *IEEE Trans. Pattern Anal. Mach. Intell*., 27, 8, 1226–1238, 2005.

16. Xing, E.P, Jordan, M, II, Karp, R.M. *et al*., Feature selection for highdimensional genomic microarray data, in: *ICML*, vol. 1, Citeseer, pp. 601–608, 2001.

17. Guyon, I and Elissee, A, An introduction to variable and feature selection. *J. Mach. Learn. Res*., 3, Mar, 1157–1182, 2003.

18. Yu, L and Liu, H, Feature selection for high-dimensional data: A fast correlation-based filter solution, in: *Proceedings of the 20th international conference on machine learning (ICML-03)*, pp. 856–863, 2003.

19. Zhu, Z, Ong, Y.-S, Dash, M, Markov blanket-embedded genetic algorithm for gene selection. *Pattern Recognit*., 40, 11, 3236–3248, 2007.

20. Shen, Q, Shi, W.-M, Kong, W, Hybrid particle swarm optimization and tabu search approach for selecting genes for tumor classification using gene expression data. *Comput. Biol. Chem*., 32, 1, 53–60, 2008.

21. Niknam, T and Amiri, B, An efficient hybrid approach based on PSO, ACO and k-means for cluster analysis. *Appl. Soft Comput*., 10, 1, 183–197, 2010.

22. Rashedi, E, Nezamabadi-Pour, H, Saryazdi, S, GSA: a gravitational search algorithm. *Inf. Sci*., 179, 13, 2232–2248, 2009.

1. *Corresponding author: `rampintu570@gmail.com`

2. †Corresponding author: `pratyay_kuila@yahoo.com`

# Part 3: MACHINE LEARNING FOR SECURITY SYSTEMS

## 10: On Fusion of NIR and VW Information for Cross-Spectral Iris Matching

**Ritesh Vyas¹*, Tirupathiraju Kanumuri², Gyanendra Sheoran² and Pawan Dubey²**

*¹Bennett University, Greater Noida, India*

*²NIT Delhi, Delhi, India*

> **Abstract**
>
> Iris has been the most promising biometric trait when it comes to personal authentication. But there are certain situations where iris images captured in one spectrum or wavelength must be matched against the templates of feature vectors created from iris images from another spectrum or wavelength. Representation of iris texture using different spectrum is significantly different. Therefore, this paper investigates the application of different fusion strategies in combining the information from near infrared and visible wavelength images to enhance the recognition performance. Two benchmark cross-spectral iris databases are used in the experimentation, namely, PolyU cross spectral database and Cross-Eyed database. Fusion schemes at two different levels, feature level and score level, are adopted to validate the hypothesis of performance improvement through combination of information from different spectrum. Results show that fusion helps in improvement of cross-spectral iris matching.
>
> **Keywords:** Iris recognition, cross-spectral, near infrared (NIR), visible wavelength (VW), information fusion

### 10.1 Introduction

Since its inception [1, 2], iris recognition has been the choice of researchers working in the field of biometric authentication. Reasons behind such popularity of iris biometric are the uniqueness, randomness, and stability of iris features. The core steps of any iris recognition system comprise of segmentation (i.e., localizing the iris boundaries), normalization (i.e., transforming the nearly circular iris into rectangular templates for achieving the scale invariance), feature extraction (i.e., representing the iris texture in most distinctive manner), and matching (i.e., measuring the similarity between two different feature templates) [3].

Traditionally, iris-dependent biometric applications employ iris images obtained in the near infrared (NIR) wavelength band, as this band is good at revealing the pigmentation of the iris and offers more physical comfort to the user as compared to other illuminations. Moreover, it also works for dark irides, where intensity difference between that of pupil and iris is not much. However, there have been studies like refs. [4, 5] which have explored the potentials of iris recognition in multiple spectra other than traditional NIR spectrum. In recent past, researchers have turned their attention toward efficient iris recognition in visible wavelength (VW; 400–700 nm). Despite various noise factors being added to the iris images due to VW imaging, there exists a firm rationale that endorses its use in iris recognition. First is that VW cameras are cost-effective in providing higher resolution images. Besides, large-scale surveillance/monitoring often incorporates visible range cameras [6]. Extensive application of hand-held devices like smartphones has also drawn the attention of research community toward enhanced iris recognition through VW-based imaging.

Therefore, due to the transfer of iris recognition technology from NIR to VW spectrum, there arise some situations where iris samples captured in one wavelength (NIR/VW) need to be matched against those of acquired in the other (VW/NIR). The most suitable example of such situations is the application of surveillance, where live stream of people is acquired through advanced VW cameras and images from this stream are matched against the stored databases which have NIR-based images. This sort of cross-spectral matching causes decadence in the overall recognition performance, reason behind which is the uncorrelated information present in different wavelengths' images.

#### 10.1.1 Related Works

There have been many efforts in the literature, which have dealt with the challenging issue of cross-spectral iris matchings. Boyce *et al*. [7] reported a phenomenal explication of the iris structure at different wavelengths. Additionally, it was suggested in [7, 8] that the system performance varies inversely with the relative wavelength between two channels being compared. Feature-level fusion using augmentation and ordered weighted average (OWA) was used in [9] to combine the features of NIR and VW images.
