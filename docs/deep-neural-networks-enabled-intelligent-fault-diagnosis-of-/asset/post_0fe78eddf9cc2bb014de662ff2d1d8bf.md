
## Convolutional Neural Networks for Intelligent Fault Diagnosis 71

![](img/f29bba55de4872c43f26af4667e705f2_81_0.png)

FIGURE 4.8 Feature visualization based on t-SNE.

in a high dimensional space nonlinearly, every overlap among different classes in visualization is still consistent with the high accuracies in Table 4.2. The above visualization is able to qualitatively illustrate the effectiveness of the CDFL for fault diagnosis.

## CONCLUSION

The CDFL approach has been presented for induction motor fault diagnosis in this chapter. This approach can learn features directly from raw data to characterize different working conditions of the induction motors. When the local filters' weights are learned by BPNN, the fast convolutional pooling architecture can be built to extract the discriminative and invariant features from the raw vibration data. Then the SVM has classified the features successfully for induction motor fault diagnosis. Experimental studies have verified the CDFL's capability of extracting the discriminative and effective features from the fault signals. As compared to other state-of-the-art methods, the approach proposed in this chapter is more effective and robust for induction motor fault diagnosis. Further research is being conducted to verify the applicability of the presented approach for fault diagnosis of other types of machines.

## REFERENCES

- Chang, Chih-Chung, and Chih-Jen Lin. 2011. LIBSVM A Library for Support Vector Machines. ACM Transactions on Intelligent Systems and Technology (TIST) 2 (3): 1-27. https://doi.org/10.1145/1961189.1961199.
- Ganz, Zeke, Ricardo Eanao, David Carlos, and Lawrence Carin. 2015. “Learning Deep Sigmoid Networks With Data Augmentation.” Artificial Intelligence and Data Science, PMLR: 38:268-276. http://proceedings.ml/v3/gan15.
- Nce, Serkan Kayilar, Levant Eren, Murat Akar, and Moncef Gabbou. 2016, “Real-Time Motor Fault Detection by 1-D Convolutional Neural Networks.” IEEE Transactions on Industrial Electronics 63 (1): 7067-7075. https://doi.org/10.1109/TIE.2016.258279
- Le Cun, Y., Boser, J. S. Denker, D. R. Edward, W. Hubbard, and L. D. Jackson. 1990. “Handwritten Digit Recognition With a Back-Propagation Network.” Advances in Information Processing Systems 2:396–404.
- Jing, Luyang, Ming Zhao, Pin Li, and Xiaoqiang Xu. 2017. “A Convolutional Neural Network Based Feature Learning and Fault Diagnosis Method for the Condition Monitoring of Gearbox.” Measurement 111: 1–10. https://doi.org/10.1016/j.measurement.2017.07.017.

## 72 Deep Neural Networks-Intelligent Fault Diagnosis of Mechanical Systems

- Krizhevsky, Alex, Ilya Sutskever, and Geoffrey E. Hinton. 2012. "ImageNet Classification With Deep Convolutional Networks." Advances in Information Processing Systems 25: 1097–1105.
- LeCun, Yann, and Yoshua Bengio. 1995. "Convolutional Networks for Images, Speech, and Time- The Handbook of Brain Theory and Neural Networks 36(161)(10).
- Liao, Bin, Jingjun Xu, Jiantu, and Shilong Zhou. 2015. "An Image Retrieval Method for Binary Images Based on DNN and softmax Classifier." IEEE Technical Review 32 (4):294–303. https://doi.org/10.1109/0254602.2015.101633
- Lu, Chen, Zhenya Wang, and Bo Zhou. 2017. "Intelligent Fault Diagnosis of Rolling Bearing Using Hierarchical Convolutional Network Base Health State Classification." Advanced Engineering Informatics 32: 139–151. https://doi.org/10.1016/j.aei.2017.02.005
- Osama, Ahmed-Habil, abdel-rahman Mohamed. 2014. "Convolutional Networks for Speech." IEEE Transactions on Audio, Speech, and Language Processing 22 (10): 1533–1545.
- Saxe, Andrew M., Pang Wei, and Andrew Y. 2011. "On random weights." In NIPS.
- Shao, Shiyun, Ruqiang Wang, and Robert. 2017. "A Deep Learning Approach." Chinese Journal of Mechanical Engineering 30:1347–1356.
- Wen, Shijun, and Chen. 2016. "A Sparse Auto-Encoder." Measurement 89: 171–178.
- Sun, Ruqiun, Ruqiang Wang, and Robert. 2017. "Discriminative Features." IEEE Transactions on Industrial 13 (3): 1350–1359.
- van Maaten, Lars, and Geoffrey Hinton. 2008. "Visualizing Data Using t-SNE." Journal of Machine Learning 9:2575–2605.
- Wang, Peng, Ruqiang Wang, and Robert. 2017. "Virtual Deep Learning." Journal of Manufacturing Systems 44: 310–316.
- Yang, Tan, and Liang. 2015. "Estimating Parameters." Monthly Notices of the Royal Astronomical Society 452: 158–168.
- Y, Gary, and C. 2000. "Wavelet Packet Extraction." IEEE Transactions on Industrial 47 (3): 650–667.
- Yin, Zuyuan, Jin Kruger, and Hu. 2015. "Introduction of SVM." 13th International Conference: 550–555.
- Zeiler, David D, and Rob Fergus. 2014. "Visualizing and Understanding Convolutional Networks." Computer Vision–2014: Zurich, Switzerland, September 6–12, Part 1 (pp. 818–833). Springer International Publishing.
- Zhao, Xiaodong, Xinliang Tang, and Yibin Zhao. 2010. "Fault Diagnosis of Asynchronous Induction Motor Based on BP Network." 2010 International Conference on Measuring Technology and Mechatronics 236–239. Changsha, China.

## II
### Advanced Topics of Deep Learning-Enabled Intelligent Fault Diagnosis

![](img/f29bba55de4872c43f26af4667e705f2_84_0.png)

## Data Augmentation for Intelligent Fault Diagnosis

### INTRODUCTION

For deep learning-based fault diagnosis methods, training data is an important factor that affects the performance of prediction model. Generally, a deep neural network contains multiple hidden layers, and the number of free parameters that need to be trained is enormous. In order to achieve accurate predictions, the deep architecture need to be well-trained, and fully training a large balanced data. However, in practice, training samples across different machine states often exhibit an imbalance. For example, for a mechanical system under operation, it is working under normal circumstance most of the time and the collected sensor data that represent positive samples are sufficient, while machine operating in fault is infrequent and corresponding samples are limited compared to positive samples. Therefore, there is an imbalance between positive training samples and fault samples.

Generative adversarial networks (GANs) offer an alternative when facing the issue of unbalanced data classification by generating data for minor classes. GANs have shown prominent capability in producing realistic looking data and have been successfully applied in image generation. It can be used for data augmentation by generating artificial data that are similar to original data and enriching training dataset. Moreover, the generative architecture models data generation process and thereby helps to understand the original data distribution.

GAN was first introduced as a framework for generation of artificial images (Goodfellow et al. 2014) and has the capability to produce convincing image samples. However, the original GAN faced challenges with training instability, requiring
