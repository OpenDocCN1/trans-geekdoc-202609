
随后，使用带标签的训练数据集训练了 NB、LDA 和 QDA 算法。对于 LDA 训练，SVD 求解器被设置为训练求解器，并调整了 QDA 的正则化参数以正则化协方差估计。NB、LDA 和 QDA 模型的性能如[图 10](#979-8-3693-1642-9.ch011.xhtml#f10)所示。这些分类器模型在 F1 分数和精确率方面也表现良好。从[图 8](#979-8-3693-1642-9.ch011.xhtml#f08)可以看出，NB 和 QDA 表现良好，表明模型在精确分类类别方面具有优势。最后，对所有分类器进行了性能比较，并呈现在[图 11](#979-8-3693-1642-9.ch011.xhtml#f11)中。对于比较，考虑了所有获得性能指标的分类器。对于 kNN 和 SVM，采纳了能提供最佳结果的条件。即当邻居数量=4 时 kNN 提供了更好的性能，而 SVM 在 rbf 核以及 Gamma 值为 0.1 和 0.3 时效果更好。性能比较表明带有 rbf 核的 SVM 分类器表现卓越。

## 5. 结论

本章有效地将一种加密方案与模式识别框架相结合，用于生物特征认证。此处的认证与给定生物特征数据的类别标签的真实预测相关联。因此，识别模型在正确预测类别方面的优劣非常重要。本工作采用得克萨斯 3D 人脸识别数据集中的面部图像作为生物特征数据。数据库中的图像包含多种族群，且具有不同的光照和表情。

| 图 11. 所有分类器的性能比较 |
| --- |
| ![Figure979-8-3693-1642-9.ch011.f11](i/ch011.f11.png) |

实验涉及使用 RSA 算法对图像进行加密，使用 Debauchees 小波融合实际图像和加密图像，从加密图像和融合图像中提取 GLCM 和 LBP 纹理，拼接特征并进行特征选择，将选定的特征输入 kNN、SVM、NB、LDA 和 QDA 机器学习算法以创建分类器模型，最后对模型进行评估。模型使用准确率、精确率、召回率、MCC、Kappa 和 F1 分数等性能指标进行评估。与所有指标相比，所有模型的精确率均较高，其中带有 rbf 核的 SVM 表现最为突出。这表明，将图像加密纳入模式识别框架对于提供更好的生物特征认证以获取系统访问权限具有重要意义。

## 参考文献

Abusham, E., Ibrahim, B., Zia, K., & Rehman, M. (2023). Facial image encryption for secure face recognition system. Electronics (Basel), 12(3), 774. doi:[10.3390/electronics12030774](https://doi.org/10.3390/electronics12030774)

Agarwal, S., & Jung, K. H. (2023). Forensic analysis and detection using polycolor model binary pattern for colorized images. Multimedia Tools and Applications, 1–20. doi:[10.1007/s11042-023-16675-1](https://doi.org/10.1007/s11042-023-16675-1)

Aggarwal, A. K. (2022). Learning texture features from glcm for classification of brain tumor mri images using random forest classifier. Transactions on Signal Processing, 18, 60–63. doi:[10.37394/232014.2022.18.8](https://doi.org/10.37394/232014.2022.18.8)

Al Alkeem, E., Kim, S. K., Yeun, C. Y., Zemerly, M. J., Poon, K. F., Gianini, G., & Yoo, P. D. (2019). An enhanced electrocardiogram biometric authentication system using machine learning. IEEE Access : Practical Innovations, Open Solutions, 7, 123069–123075. doi:[10.1109/ACCESS.2019.2937357](https://doi.org/10.1109/ACCESS.2019.2937357)

Ali, S. S., Baghel, V. S., Ganapathi, I. I., & Prakash, S. (2020). Robust biometric authentication system with a secure user template. Image and Vision Computing, 104, 104004. doi:[10.1016/j.imavis.2020.104004](https://doi.org/10.1016/j.imavis.2020.104004)

Ashwanth, B., & Swamy, K. V. (2020, March). Medical image fusion using transform techniques. In 2020 5th International conference on devices, circuits and systems (ICDCS) (pp. 303-306). IEEE. doi:[10.1109/ICDCS48716.2020.243604](https://doi.org/10.1109/ICDCS48716.2020.243604)

Barburiceanu, S., Terebes, R., & Meza, S. (2021). 3D texture feature extraction and classification using GLCM and LBP-based descriptors. Applied Sciences (Basel, Switzerland), 11(5), 2332. doi:[10.3390/app11052332](https://doi.org/10.3390/app11052332)

Bishop, C. M., & Nasrabadi, N. M. (2006). Pattern recognition and machine learning (Vol. 4). New York: Springer.

Chang, H. B., & Schroeter, K. G. (2010, January). Creating safe and trusted social networks with biometric user authentication. In International Conference on Ethics and Policy of Biometrics (pp. 89-95). Springer Berlin Heidelberg. doi:[10.1007/978-3-642-12595-9_12](https://doi.org/10.1007/978-3-642-12595-9_12)

DavidB. (2023, April). An Analytical Survey on Multi-Biometric Authentication System for Enhancing the Security Levels in Cloud Computing. In 2023 Eighth International Conference on Science Technology Engineering and Mathematics (ICONSTEM) (pp. 1-6). IEEE.

Gong, L., Qiu, K., Deng, C., & Zhou, N. (2019). An optical image compression and encryption scheme based on compressive sensing and RSA algorithm. Optics and Lasers in Engineering, 121, 169–180. doi:[10.1016/j.optlaseng.2019.03.006](https://doi.org/10.1016/j.optlaseng.2019.03.006)

Gupta, S., Castleman, K. R., Markey, M. K., & Bovik, A. C. (2010). Texas 3D Face Recognition Database. 2010 IEEE Southwest Symposium on Image Analysis & Interpretation (SSIAI), 97–100. [http://live.ece.utexas.edu/research/texas3dfr/index.htm](http://live.ece.utexas.edu/research/texas3dfr/index.htm)

Gustian, D. A., Rohmah, N. L., Shidik, G. F., Fanani, A. Z., & Pramunendar, R. A. (2019, September). Classification of troso fabric using SVM-RBF multi-class method with GLCM and PCA feature extraction. In 2019 International Seminar on Application for Technology of Information and Communication (iSemantic) (pp. 7-11). IEEE. doi:[10.1109/ISEMANTIC.2019.8884329](https://doi.org/10.1109/ISEMANTIC.2019.8884329)

Hadid, A. (2008). The Local Binary Pattern Approach and its Applications to Face Analysis. 2008 First Workshops on Image Processing Theory. Tools and Applications. doi:[10.1109/IPTA.2008.4743795](https://doi.org/10.1109/IPTA.2008.4743795)

Hamidi, H. (2019). An approach to develop the smart health using Internet of Things and authentication based on biometric technology. Future Generation Computer Systems, 91, 434–449. doi:[10.1016/j.future.2018.09.024](https://doi.org/10.1016/j.future.2018.09.024)

Haralick, R. M., Dinstein, I., & Shanmugam, K. (1973). Textural features for image classification. Trans. Syst. Man Cybern. doi:[10.1109/TSMC.1973.4309314](https://doi.org/10.1109/TSMC.1973.4309314)

Heikkilä, M., Pietikäinen, M., & Schmid, C. (2009). Description of interest regions with local binary patterns. Pattern Recognition, 42(3), 425–436. doi:[10.1016/j.patcog.2008.08.014](https://doi.org/10.1016/j.patcog.2008.08.014)

Hemalatha, S. (2020, February). A systematic review on Fingerprint based Biometric Authentication System. In 2020 International Conference on Emerging Trends in Information Technology and Engineering (ic-ETITE) (pp. 1-4). IEEE. doi:[10.1109/ic-ETITE47903.2020.342](https://doi.org/10.1109/ic-ETITE47903.2020.342)

Hussain, L., Malibari, A. A., Alzahrani, J. S., Alamgeer, M., Obayya, M., Al-Wesabi, F. N., Mohsen, H., & Hamza, M. A. (2022). Bayesian dynamic profiling and optimization of important ranked energy from gray level co-occurrence (GLCM) features for empirical analysis of brain MRI. Scientific Reports, 12(1), 15389. doi:[10.1038/s41598-022-19563-0](https://doi.org/10.1038/s41598-022-19563-0)
