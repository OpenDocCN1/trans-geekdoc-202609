
**Figure 6:** Recognition performance measured by the `fl-score` (in green) obtained in the constrained learning setting and average cardinality of the subsets of data sources (in blue), as a function of `τ[imp]` and `τ[int]`. Confusion matrices corresponding to (a) the model trained on all data sources fused and (b) the best performing model trained on a constrained number of data sources. The model trained on all data sources fused together resulted in 70.86 % recognition performance measured by the `fl-score`. Both models use the following set of hyperparameters: `l[r]` = 0.1, `nf` = 28, ![figure](images/in73-1.png), ![figure](images/in73-2.png), ![figure](images/in73-3.png), ![figure](images/in73-4.png), ![figure](images/in73-5.png), ![figure](images/in73-6.png), ![figure](images/in73-7.png), `s` = 0.6, and `n[u]` = 2048. The best performing model yields a recognition performance of 88.7%, and an improvement of 17.84% over the baseline, using a subset containing solely 12 data sources, hence reducing by one-half the required quantities of data.

For comparison, we also trained a neural network on the whole data sources. This network achieved a performance of 70.86 % measured by the `fl-score`. We used for this neural network the set of hyperparameters that were obtained for the best configuration during the exploration of the neural architecture space. From the rightmost confusion matrix which is embedded in [Fig. 6](#chap3.xhtml#fig6), we notice a more pronounced confusion for still class which is often confused with public transportation-related activities (bus, train and subway with 11%, 10% and 12% confusion, respectively). Analysis of the evolution of the confusion of this class over the BO runs shows an f1-score of approximately 26.28% ± 0.13, with a maximum of 43% recorded at the 59th run. A similar observation can be made for train class which is often confused with subway and reflects a clear link between the two activities.

## 6. Discussion

We proposed, in this chapter, to leverage domain models in order to improve the way neural architectures relate data sources together in a sensor-rich environment. First, we presented a novel approach for deriving subsets of important and interacting data sources, namely, the data generation process that is intended to capture the dynamics of body movements pertaining to each human activity. As deriving such models using human expertise is hard, we framed this task as an exploration of the space of neural architectures. These architectures are composed of sensor fusion and feature extraction components controlled by sets of hyperparameters, which in turn control the impact of the corresponding data sources processed by these components. Derivation of the subsets of important and interacting data sources is based upon this assumption. We confronted the obtained data generation model to empirical results from the literature. In addition to some specific insights, such as the emergence of genuine set of modalities that are found to impact substantially the dynamics of human activities, the obtained model is consistent with those from the literature. These specific insights can be explained by the type of architecture components that we used in the proposed instantiation and which are based on convolutional neural networks. This part opens up perspectives to modeling real-world phenomena like the dynamics of human activities using a large-scale exploration of the space of architectures. Such models could constitute general wisdom, similar to human expertise, that can be leveraged as domain knowledge.

Second, the effectiveness of the obtained domain models is demonstrated via a setting that exploits the subsets of interacting data sources in order to constrain the learning process of a neural network. Indeed, the proposed setting showed substantial improvements over the baseline where all data sources of the sensor-rich environment are used. In particular, we get an improvement of the recognition performances, measured by the `fl-score`, of up to 17.84% over the baseline and this using solely 12 data sources among those available. The experimental results on a fully-featured dataset of human activities prove the effectiveness of the proposed approach and open up perspectives regarding the incorporation of richer domain models in order to relate data sources more efficiently and develop data-efficient learning systems. Another perspective is related to the way these kinds of domain models are incorporated into the actual learning processes. One can derive from these domain models an additional term, `R` : ![figure](images/vf.png) → ![figure](images/vr.png), that can be plugged to the original optimization objective (Eq. (2)), which, then, becomes

![figure](images/p75-1.png)

where `λ` ∈ \[0; 1\] is a weight parameter used to control the impact of the regularization term. This term can be used precisely at the interfaces between data sources and the components that process them. The goal is to impose the learning model to reproduce, in its internals, the insights that are provided as domain knowledge.

## References

[1](#chap3.xhtml#fs1). J. K. Aggarwal and Q. Cai, “Human motion analysis: A review,” *Computer vision and image understanding*, vol. 73, no. 3, pp. 428–440, 1999.

[2](#chap3.xhtml#fs2). V. Radu, C. Tong, S. Bhattacharya, N. D. Lane, C. Mascolo, M. K. Marina, and F. Kawsar, “Multimodal deep learning for activity and context recognition,” *Proc. ACM Interact. Mobile, Wearable Ubiquitous Technol*., vol. 1, no. 4, p. 157, 2018.

[3](#chap3.xhtml#fs3). R. Kurle, S. Günnemann, and P. van der Smagt, “Multi-source neural variational inference,” in *Proc. the AAAI Conf. Artificial Intelligence*, vol. 33, pp. 4114–121, 2019.

[4](#chap3.xhtml#fs4). M. Zeng, H. Gao, T. Yu, O. J. Mengshoel, H. Langseth, I. Lane, and X. Liu, “Understanding and improving recurrent networks for human activity recognition by continuous attention,” in *Proc. 2018 ACM Int. Sympo. on Wearable Computers*, ACM, pp. 56–63, 2018.

[5](#chap3.xhtml#fs5). K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for image recognition,” in *Proc. IEEE Conf. Computer Vision and Pattern Recognition*, pp. 770–778, 2016.

6. C. Szegedy, W. Liu, Y. Jia, P. Sermanet, S. Reed, D. Anguelov, D. Erhan, V. Vanhoucke, and A. Rabinovich, “Going deeper with convolutions,” in *Proc. IEEE Conf. Computer Vision and Pattern Recognition*, pp. 1–9, 2015.

7. T. Plötz, N. Y. Hammerla, and P. Olivier, “Feature learning for activity recognition in ubiquitous computing,” in *Int. Joint Conf. Artificial Intelligence*, p. 1729, 2011.

[8](#chap3.xhtml#fs8). F. J. Ordóñez, and D. Roggen, “Deep convolutional and LSTM recurrent neural networks for multimodal wearable activity recognition,” *Sensors*, vol. 16, no. 1, p. 115, 2016.

[9](#chap3.xhtml#fs9). M. T. Luong, H. Pham, and C. D. Manning, “Effective approaches to attention-based neural machine translation,” arXiv preprint arXiv:1508.04025, 2015.

[10](#chap3.xhtml#fs10). Z. Chen, L. Zhang, Z. Cao and J. Guo, “Distilling the knowledge from handcrafted features for human activity recognition,” *IEEE Trans. Indust. Inform*., vol. 14, no. 10, pp. 4334–4342, 2018.

[11](#chap3.xhtml#fs11). H. Gjoreski, M. Ciliberto, F. J. O. Morales, D. Roggen, S. Mekki, and S. Valentin, “A versatile annotated dataset for multimodal locomotion analytics with mobile devices,” in *Proc. 15th ACM Conf. Embedded Network Sensor Systems*, ACM, 2017, p. 61.

[12](#chap3.xhtml#fs12). P. K. Atrey, M. A. Hossain, A. El Saddik, and M. S. Kankanhalli, “Multimodal fusion for multimedia analysis: a survey,” *Multimedia Syst*., vol. 16, no. (6), pp. 345–379, 2010.

[13](#chap3.xhtml#fs13). T. Elsken, J. H. Metzen, and F. Hutter, “Neural architecture search: A survey,” *J. Mach. Learni. Res*., vol. 20, no. 55, pp. 1–21, 2019.
