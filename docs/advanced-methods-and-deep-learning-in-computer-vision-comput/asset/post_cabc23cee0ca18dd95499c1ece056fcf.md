
contrastive learning is employed to cluster features according to their semantics while tearing apart those of different classes.

## 8.3.3.4 New directions

Other novel ideas have been proposed in the continual learning literature both for dense and sparse tasks. Here, we present and discuss some of the most promising research directions.

### Weights Initialization
Has been employed in Cermelli et al. (2020) to deal with the atypical behavior of the background class in the *disjoint* and *overlapped* scenarios. The authors initialize the classifier’s parameters for the novel classes in such a way that the probability of the background is uniformly spread among the novel classes, preventing the model to be biased toward the background class when dealing with unseen classes.

### Generative Replay
Methods train generative models on the current data distribution; afterwards, it is possible to sample data from past experience when learning on new data. By learning on actual data mixed with artificially generated past data, they try to preserve past knowledge while learning the new task. The generative model is generally a GAN (Goodfellow et al., 2014) as in Wu et al. (2018) and Shin et al. (2017) or an auto-encoder as in Draelos et al. (2017) and Kamra et al. (2017). Notice that only the weak classification labeling is available for generated data and some pseudo-labels need to be estimated for segmentation.

### Webly-based Learning
Models (Hou et al., 2018; Modolo and Ferrari, 2017), *i.e.*, models that learn from samples acquired via web searches, could be an extremely powerful tool to retrieve faithful past examples using as queries the label names of the old classes to preserve. Also in this case, only weak classification labels are available and some pseudo-labeling scheme need to be introduced.

## 8.4 Conclusion

Semantic image segmentation is an active research field aiming at detailed and accurate scene understanding. Being a dense labeling task, it brings additional complexity with respect to classical image classification problems. To solve this task many deep learning models have been proposed, however such architectures require large labeled training datasets and show bad adaptation capabilities to unseen domains or unseen tasks. To tackle these two aspects, a large research activity has been conducted on both domain adaptation and continual learning in the past few years. In this chapter, we discuss domain adaptation in its unsupervised form (*i.e.*, when no labeled data of the target domain is used for training) applied to the dense semantic segmentation task. Then, we showed that continual learning can be achieved in this task in various possible ways.

The algorithms developed so far are able to greatly alleviate the degradation even if they still need to acquire greater maturity before being applied in delicate real-world scenarios (such as in autonomous driving). Indeed, there still remain many challenges to address as regards both the adaptation of complex deep learning architectures across different tasks and domains and their ability to learn new concepts over time without forgetting previous knowledge.

In addition, many ancillary closely related problems are emerging in response to the practical application to real-world use cases. Future directions should include, for instance, the generalization from or to multiple data distributions, open-set UDA (i.e., recognizing in the target domain classes never seen in the source one), and continual UDA (i.e., the continual adaptation process to unseen domains and unseen tasks).

## Acknowledgment

Our work was in part supported by the Italian Minister for Education (MIUR) under the “Departments of Excellence” initiative (Law 232/2016).

## References

- Achille, A., Eccles, T., Matthey, L., Burgess, C., Watters, N., Lerchner, A., Higgins, I., 2018. Life-long disentangled representation learning with cross-domain latent homologies. In: Neural Information Processing Systems (NeurIPS).
- Barbato, F., Toldo, M., Michieli, U., Zanuttigh, P., 2021. Latent space regularization for unsupervised domain adaptation in semantic segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition Workshops (CVPRW).
- Bengio, Y., Courville, A., Vincent, P., 2013. Representation learning: a review and new perspectives. In: IEEE Transactions on Pattern Analysis and Machine Intelligence (TPAMI). IEEE, pp. 1798–1828.
- Biasetton, M., Michieli, U., Agresti, G., Zanuttigh, P., 2019. Unsupervised domain adaptation for semantic segmentation of urban scenes. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition Workshops (CVPRW).
- Bucher, M., Vu, T.H., Cord, M., Pérez, P., 2020. Buda: boundless unsupervised domain adaptation in semantic segmentation. arXiv preprint. arXiv:2004.01130.
- Buciluă, C., Caruana, R., Niculescu-Mizil, A., 2006. Model compression. In: Proc. of the 12th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pp. 535–541.
- Busto, P.P., Gall, J., 2017. Open set domain adaptation. In: Proceedings of the International Conference on Computer Vision (ICCV), pp. 754–763.
- Castro, F.M., Marin-Jiménez, M.J., Guil, N., Schmid, C., Alahari, K., 2018. End-to-end incremental learning. In: Proceedings of the European Conference on Computer Vision (ECCV), pp. 233–248.
- Cermelli, F., Mancini, M., Bulò, S.R., Ricci, E., Caputo, B., 2020. Modeling the background for incremental learning in semantic segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR).
- Chang, W., Wang, H., Peng, W., Chiu, W., 2019. All about structure: adapting structural information across domains for boosting semantic segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 1900–1909.
- Chen, Y., Li, W., Chen, X., Van Gool, L., 2018. Learning semantic segmentation from synthetic data: a geometrically guided input-output adaptation approach. arXiv preprint. arXiv:1812.05040.
- Chen, M., Xue, H., Cai, D., 2019a. Domain adaptation for semantic segmentation with maximum squares loss. In: Proceedings of the International Conference on Computer Vision (ICCV).
- Chen, Y., Li, W., Chen, X., Gool, L.V., 2019b. Learning semantic segmentation from synthetic data: a geometrically guided input-output adaptation approach. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 1841–1850.
- Chen, Y.C., Lin, Y.Y., Yang, M.H., Huang, J.B., 2019c. CRDoCo: pixel-level domain transfer with cross-domain consistency. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR).
- Chen, Y.H., Chen, W.Y., Chen, Y.T., Tsai, B.C., Frank Wang, Y.C., Sun, M., 2017. No more discrimination: cross city adaptation of road scene segmenters. In: Proceedings of the International Conference on Computer Vision (ICCV), pp. 1992–2001.
- Choi, J., Kim, T., Kim, C., 2019. Self-ensembling with gan-based data augmentation for domain adaptation in semantic segmentation. In: Proceedings of the International Conference on Computer Vision (ICCV), pp. 6830–6840.
- De Lange, M., Aljundi, R., Masana, M., Parisot, S., Jia, X., Leonardis, A., Slabaugh, G., Tuytelaars, T., 2019. Continual learning: a comparative study on how to defy forgetting in classification tasks. arXiv preprint. arXiv:1909.08383.
- Deng, J., Dong, W., Socher, R., Li, L., Li, K., Li, F., 2009. Imagenet: a large-scale hierarchical image database. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 248–255.
- Dhar, P., Singh, R.V., Peng, K.C., Wu, Z., Chellappa, R., 2019. Learning without memorizing. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 5138–5146.
- Ditzler, G., Roveri, M., Alippi, C., Polikar, R., 2015. Learning in nonstationary environments: a survey. IEEE Computational Intelligence Magazine 10, 12–25.
- Douillard, A., Chen, Y., Dapogny, A., Cord, M., 2021. Plop: learning without forgetting for continual semantic segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR).
- Draelos, T.J., Miner, N.E., Lamb, C.C., Cox, J.A., Vineyard, C.M., Carlson, K.D., Severa, W.M., James, C.D., Aimone, J.B., 2017. Neurogenesis deep learning: extending deep networks to accommodate new classes. In: 2017 International Joint Conference on Neural Networks (IJCNN). IEEE, pp. 526–533.
- Du, L., Tan, J., Yang, H., Feng, J., Xue, X., Zheng, Q., Ye, X., Zhang, X., 2019. SSF-DAN: separated semantic feature based domain adaptation network for semantic segmentation. In: Proceedings of the International Conference on Computer Vision (ICCV).
- Dundar, A., Liu, M., Wang, T., Zedlewski, J., Kautz, J., 2018. Domain stylization: a strong, simple baseline for synthetic to real image domain adaptation. arXiv preprint. arXiv:1807.09384.
- Everingham, M., Van Gool, L., Williams, C.K., Winn, J., Zisserman, A., 2010. The Pascal visual object classes (VOC) challenge. International Journal of Computer Vision 88, 303–338.
- French, R.M., 1999. Catastrophic forgetting in connectionist networks. Trends in Cognitive Sciences 3, 128–135.
- Ganin, Y., Lempitsky, V., 2015. Unsupervised domain adaptation by backpropagation. In: Proceedings of the International Conference on Machine Learning (ICML), pp. 1180–1189.
- Ganin, Y., Ustinova, E., Ajakan, H., Germain, P., Larochelle, H., Laviolette, F., Marchand, M., Lempitsky, V., 2016. Domain-adversarial training of neural networks. Journal of Machine Learning Research 17, 2096–2130.
- Girshick, R., Donahue, J., Darrell, T., Malik, J., 2014. Rich feature hierarchies for accurate object detection and semantic segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 580–587.
- Gong, R., Li, W., Chen, Y., Gool, L.V., 2019. DLOW: domain flow for adaptation and generalization. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 2477–2486.
- Goodfellow, I., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A., Bengio, Y., 2014. Generative adversarial nets. In: Neural Information Processing Systems (NeurIPS), pp. 2672–2680.
- Grandvalet, Y., Bengio, Y., 2005. Semi-supervised learning by entropy minimization. In: Actes de CAP 05, Conférence francophone sur l'apprentissage automatique, pp. 281–296.
- Grossberg, S., 2013. Adaptive resonance theory: how a brain learns to consciously attend, learn, and recognize a changing world. Neural Networks 37, 1–47.
- Hinton, G., Vinyals, O., Dean, J., 2015. Distilling the knowledge in a neural network. arXiv preprint. arXiv:1503.02531.
- Hoffman, J., Tzeng, E., Park, T., Zhu, J.Y., Isola, P., Saenko, K., Efros, A., Darrell, T., 2018. CyCADA: cycle-consistent adversarial domain adaptation. In: Proceedings of the International Conference on Machine Learning (ICML).
- Hoffman, J., Wang, D., Yu, F., Darrell, T., 2016. FCNs in the wild: Pixel-level adversarial and constraint-based adaptation. arXiv preprint. arXiv:1612.02649.
- Hou, Q., Cheng, M.M., Liu, J., Torr, P.H., 2018. WebSeg: learning semantic segmentation from web searches. arXiv preprint. arXiv:1803.09859.
- Hsu, Y.C., Liu, Y.C., Ramasamy, A., Kira, Z., 2018. Re-evaluating continual learning scenarios: a categorization and case for strong baselines. arXiv preprint. arXiv:1810.12488.
- Javed, K., White, M., 2019. Meta-learning representations for continual learning. In: Neural Information Processing Systems (NeurIPS).
- Jung, H., Ju, J., Jung, M., Kim, J., 2016. Less-forgetting learning in deep neural networks. arXiv preprint. arXiv:1607.00122.
- Kamra, N., Gupta, U., Liu, Y., 2017. Deep generative dual memory network for continual learning. arXiv preprint. arXiv:1710.10368.
- Kemker, R., McClure, M., Abitino, A., Hayes, T.L., Kanan, C., 2018. Measuring catastrophic forgetting in neural networks. In: Thirty-Second AAAI Conference on Artificial Intelligence.
