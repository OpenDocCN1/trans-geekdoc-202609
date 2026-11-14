
## 5.3 Future Research Opportunities

Although this research has proposed various machine learning methods to develop the classical SAR-aided SHM under the presence of small displacement data and unpredictable EOCs and these methods could present reliable and correct results, we suggest also some ideas for further research studies.

### 5.3.1 Data Augmentation by Generative Adversarial Networks

In this book, the probabilistic algorithms based on the concept of Markov Chain Monte Carlo have been utilized to expand the small displacement points. Due to the recent revolution in deep learning by proposing Generative Adversarial Networks (GANs) by Goodfellow et al. (2014), it is recommended to extend the process of data augmentation via various GANs (Creswell et al. 2018).

### 5.3.2 Data Normalization Under Novel Machine Learning Algorithms

It has been verified in this book that the EOCs are inevitable in real-world long-term SHM projects regardless of the types of data and structure. On this basis, it is critical to implement data normalization to mitigate or remove all influences of the EOCs on the SHM-based features. In this work, it has been attempted to develop various kinds of DNN-based data normalization algorithms with the aid of the deep and shallow DAEs. Although some machine learning algorithms such as unsupervised teacher–student learning, transfer learning, and online learning have been incorporated to propose these algorithms, it is possible to exploit further novel machine learning concepts. Therefore, it is recommended to extend the procedure of data normalization by taking advantage of some advanced machine learning algorithms such as ensemble learning (Dietterich 2000), partially-supervised learning (Schwenker and Trentin 2014), active learning (Settles 2012), dictionary learning (Daneshvar et al. 2023), meta learning (Entezami et al. 2023a), multi-task learning (Entezami et al. 2023b), hybrid learning (Sarmadi et al. 2023), empirical learning (Entezami et al. 2022), and new DAEs based on sparse, denoising, stacking, and variational configurations (Charte et al. 2018; Dong et al. 2018).

On the other hand, the proposed data normalization techniques in this book have required some hyperparameters, which made them parametric algorithms for data normalization. To avoid encountering difficulties and challenges regarding the problem of hyperparameter optimization, it is suggested to develop non-parametric data normalization methods by using some new machine learning concepts such as unsupervised feature selection (Solorio-Fernández et al. 2020) and feature weighting (Niño-Adan et al. 2021).

### 5.3.3 Enhanced Online Learning for Real-Time SHM

Even though the proposed online hybrid learning has opened a new methodology for real-time SHM, the decision depended on a pre-defined value regarding the rate of false positive error for stopping the online learning stage. To enhance this methodology, it is recommended to develop more robust algorithms by using new performance evaluation metrics for stopping conditions of the online learning stage.

### 5.3.4 Damage Localization

Apart from the problem of early damage detection, the other important challenge in SHM is to locate the damaged area of the structure (Entezami et al. 2018; Heravi et al. 2022). In this regard, it would be very appropriate to propose damage localization frameworks. One of the major limitations of unsupervised damage localization via contact-based sensing technology is the limitation of installation of adequate sensors for measuring suitable information (Entezami and Shariatmadar 2019; Entezami et al. 2022). A great merit of the remote sensing technique and InSAR techniques is to provide distributed target points for measuring displacement/deformation data, which these points can serve as virtual contact-based sensors (Behkamal et al. 2023a, b). Therefore, it is recommended to propose unsupervised learning methods for locating damaged areas by using information obtained from the remote sensing technology.

## References

Behkamal B, Entezami A, De Michele C, Arslan AN (2023a) Elimination of thermal effects from limited structural displacements based on remote sensing by machine learning techniques. Remote Sens 15(12):3095. https://doi.org/10.3390/rs15123095

Behkamal B, Entezami A, De Michele C, Arslan AN (2023b) Investigation of temperature effects into long-span bridges via hybrid sensing and supervised regression models. Remote Sens 15(14):3503. https://doi.org/10.3390/rs15143503

Charte D, Charte F, García S, del Jesus MJ, Herrera F (2018) A practical tutorial on autoencoders for nonlinear feature fusion: taxonomy, models, software and guidelines. Inf Fusion 44:78–96. https://doi.org/10.1016/j.inffus.2017.12.007

Creswell A, White T, Dumoulin V, Arulkumaran K, Sengupta B, Bharath AA (2018) Generative adversarial networks: an overview. IEEE Signal Process Mag 35(1):53–65. https://doi.org/10.1109/MSP.2017.2765202

Daneshvar MH, Sarmadi H, Yuen K-V (2023) A locally unsupervised hybrid learning method for removing environmental effects under different measurement periods. Meas 208:112465. https://doi.org/10.1016/j.measurement.2023.112465

Dietterich TG (2000) Ensemble methods in machine learning. In: Multiple Classifier Systems. Springer, Berlin, pp 1–15

Dong G, Liao G, Liu H, Kuang G (2018) A review of the autoencoder and its variants: a comparative perspective from target recognition in synthetic-aperture radar images. IEEE Geosci Remote Sens Mag 6(3):44–68. https://doi.org/10.1109/MGRS.2018.2853555

Entezami A, Shariatmadar H (2019) Damage localization under ambient excitations and non-stationary vibration signals by a new hybrid algorithm for feature extraction and multivariate distance correlation methods. Struct Health Monit 18(2):347–375. https://doi.org/10.1177/14771475217854372

Entezami A, Shariatmadar H, Karamodin A (2018) Data-driven damage diagnosis under environmental and operational variability by novel statistical pattern recognition methods. Struct Health Monit 18(5–6):1416–1443. https://doi.org/10.1177/1475921718800306

Entezami A, Shariatmadar H, Mariani S (2020) Fast unsupervised learning methods for structural health monitoring with large vibration data from dense sensor networks. Struct Health Monit 19(6):1685–1710. https://doi.org/10.1177/1475921719894186

Entezami A, Shariatmadar H, De Michele C (2022) Non-parametric empirical machine learning for short-term and long-term structural health monitoring. Struct Health Monit 21(6):2700–2718. https://doi.org/10.1177/14759217211069842

Entezami A, Sarmadi H, Behkamal B (2023a) Long-term health monitoring of concrete and steel bridges under large and missing data by unsupervised meta learning. Eng Struct 279:115616. https://doi.org/10.1016/j.engstruct.2023.115616

Entezami A, Sarmadi H, Behkamal B, De Michele C (2023b) On continuous health monitoring of bridges under serious environmental variability by an innovative multi-task unsupervised learning method. Struct Infrastruct Eng In Press 1–19. https://doi.org/10.1080/15732479.2023.2166538

Goodfellow I, Pouget-Abadie J, Mirza M, Xu B, Warde-Farley D, Ozair S, Courville A, Bengio Y (2014) Generative adversarial nets. Adv Neural Inf Process Syst 27

Heravi MA, Tavakkoli SM, Entezami A (2022) Structural health monitoring by probability density function of autoregressive-based damage features and fast distance correlation method. J Vib Control 28(19–20):2786–2802. https://doi.org/10.1177/1077546321020198

Niño-Adan I, Manjarres D, Landa-Torres I, Portillo E (2021) Feature weighting methods: a review. Expert Syst Appl 184:115424. https://doi.org/10.1016/j.eswa.2021.115424

Sarmadi H, Entezami A, Magalhães F (2023) Unsupervised data normalization for continuous dynamic monitoring by an innovative hybrid feature weighting–selection algorithm and natural nearest neighbor searching. Struct Health Monit Press. https://doi.org/10.1177/147592172231166116

Schwenker F, Trentin E (2014) Pattern classification and clustering: a review of partially supervised learning approaches. Pattern Recog Lett 37:4–14. https://doi.org/10.1016/j.patrec.2013.10.017

Settles B (2012) Active learning. morgan & claypool, San Rafael, California, United States

Solorio-Fernández S, Carrasco-Ochoa JA, Martínez-Trinidad JF (2020) A review of unsupervised feature selection methods. Artif Intell Rev 53(2):907–948. https://doi.org/10.1007/s10462-019-09682-y
