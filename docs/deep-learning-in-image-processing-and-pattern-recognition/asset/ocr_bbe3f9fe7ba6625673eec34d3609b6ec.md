![](bbox=[0.1, 0.1, 0.9, 0.36])

**Figure 7.** Classification accuracy of each class in the furniture dataset.

# 5. Conclusions

This paper proposes a furniture classification algorithm based on VGG16 network combined with depthwise group over-parameterized convolution. In VGG16 model, depthwise group over-parameterized convolution is introduced to reduce the number of parameters of the overall model while extracting more sufficient semantic features, which reduces the risk of model overfitting and improves the furniture image classification accuracy of the model, especially in complex backgrounds situation. In addition, in the selection of activation function, this paper used ReLU activation function in the former part of the neural network, reduced the correlation between parameters, accelerated the weight update speed of the former part of the model, and applied Leaky ReLU activation function in the last layer to avoid the problem that some neurons do not update.

This paper conducts experiments on the furniture public data set and compares DGOVGG16 with other six popular classification network methods. The AA of the proposed DGOVGG16 in this paper reaches 95.51%, which is superior to other classical methods, which fully shows that our model can accurately classify furniture images under complex backgrounds with stronger competitiveness. In future work, we intend to mine and fuse the global and local features of furniture at different scales improve the proposed DGOVGG16 model, so that the classification accuracy between similar furniture images can be further improved.

**Author Contributions:** Conceptionalization, H.Y. and X.Z.; methodology, H.Y., X.Z. and A.W.; software, H.Y., C.L. and L.Y.; validation, X.Z., H.Y., C.L. and L.Y.; writing—review and editing, X.Z. and A.W. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research is funded by “Belt and Road Initiative” Innovative Talent Exchange Foreign Experts Project (G202201010).

**Data Availability Statement:** https://www.kaggle.com/datasets/akkhtetechie/furniture-detector/download?datasetVersionNumber=1 (accessed on 2 November 2022).

**Conflicts of Interest:** The authors declare no conflict of interest.

# References

+   1. Ren, S.; He, K.; Girshick, R.; Sun, J. Faster R-CNN: Towards real-time object detection with region proposal networks. *IEEE Trans. Pattern Anal. Mach. Intell.* **2017**, *39*, 1137–1149. [CrossRef] [PubMed]

+   2. Mo, K.; Zhu, S.; Chang, A.X.; Yi, L.; Tripathi, S.; Guibas, L.J.; Su, H. Partner: A large-scale benchmark for fine-grained and hierarchical part-level 3D object understanding. In *Proceedings of the International Conference on Computer Vision and Pattern Recognition (CVPR), Long Beach, CA, USA, 16–20 June 2019*.