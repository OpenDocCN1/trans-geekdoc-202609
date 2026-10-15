
*   [Chiang\* P.-y., Ni\* R., Abdelkader A., Zhu C., Studor C., Goldstein T.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0470)  Certified defenses for adversarial patches. In: 2020:. *International Conference on Learning Representations.*. [https://openreview.net/forum?id=HyeaSkrYPH](https://openreview.net/forum?id=HyeaSkrYPH).

*   [Zhang H., Wang J.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0475)  Towards adversarially robust object detection. In: 2019:421–430. *Proceedings of the IEEE/CVF International Conference on Computer Vision.*.

*   [Zhang R., Isola P., Efros A.A., Shechtman E., Wang O.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0480)  The unreasonable effectiveness of deep features as a perceptual metric. In: 2018:586–595. *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition.*.

*   [Zhang Y., Xiang T., Hospedales T.M., Lu H.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0485)  Deep mutual learning. In: 2018:4320–4328. *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition.*.

*   [Zhang H., Yu Y., Jiao J., Xing E., El Ghaoui L., Jordan M.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0490)  Theoretically principled trade-off between robustness and accuracy. In: 2019:7472–7482. *International Conference on Machine Learning.*.

*   [Zhang H., Yu Y., Jiao J., Xing E.P., Ghaoui L.E., Jordan M.I.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0495)  Theoretically principled trade-off between robustness and accuracy. In: 2019:. *Advances in Neural Information Processing Systems.*.

*   [Zhao H., Shi J., Qi X., Wang X., Jia J.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0500)  Pyramid scene parsing network. In: 2017:2881–2890. *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition.*.

*   [Zhao Y., Yan H., Wei X.](#Ch003_29-58_S0169716123000019.xhtml#B-bb0505)  Object hider: adversarial patch attack against object detectors. *arXiv preprint:2010.14974.* 2020.

*   [Wu et al., 2017](#Ch003_29-58_S0169716123000019.xhtml#B-bb0435) Wu, J., Zhang, Q., Xu, G., 2017. Tiny ImageNet challenge.

* * *

Section II 

Advanced Methods

# Chapter 4: Deep metric learning for computer vision: A brief overview

Deen Dayal Mohan; Bhavin Jawade; Srirangaraj Setlur; Venu Govindaraju[∗](#Ch004_59-79_S0169716123000032.xhtml#cr0010)    ^()University at Buffalo, Buffalo, NY, United States  

^∗ Corresponding author: email address: [govind@buffalo.edu](mailto:govind@buffalo.edu)

## Abstract

Objective functions that optimize deep neural networks play a vital role in creating an enhanced feature representation of the input data. Although cross-entropy-based loss formulations have been extensively used in a variety of supervised deep-learning applications, these methods tend to be less adequate when there is large intraclass variance and low interclass variance in input data distribution. Deep metric learning seeks to develop methods that aim to measure the similarity between data samples by learning a representation function that maps these data samples into a representative embedding space. It leverages carefully designed sampling strategies and loss functions that aid in optimizing the generation of a discriminative embedding space even for distributions having low interclass and high intraclass variances. In this chapter, we will provide an overview of recent progress in this area and discuss state-of-the-art deep metric learning approaches.

### Keywords

Deep metric learning; Triplet loss; Image retrieval; Face verification; Person re-identification

##  1: Introduction

The field of metric learning is currently an active area of research. Traditionally, metric learning had been used as a method to create an optimal distance measure that accounts for the specific properties and distribution of the data points (for example, Mahalanobis distance). Subsequently, the methods evolved to focus on creating representations from data that are optimized for given specific distance measures such as Euclidean or cosine distance. Following the advent of Deep Learning, these feature representations have been learned end to end using complex nonlinear transformations. This has led to the primary research in the area of deep metric learning (DML) to be focused on creating loss/objective functions that are used to train deep neural networks.

One of the key areas that extensively uses DML approaches is Computer Vision. This is due to the fact that most computer vision applications deal with scenarios where there is a large variance in visual features of data samples belonging to the same class. Additionally, multiple samples belonging to different classes might have many similarities in visual features.

Recent advances in convolution neural networks (CNNs) have helped in creating good feature representations from images. While using CNNs as feature extractors under a supervised learning setting, often Softmax-based objective functions are used. Although these loss formulations tend to work well in many applications, they tend to suffer when modeling input data that has high interclass and low intraclass variances. These properties of data are present in a variety of real-world applications such as Face Recognition ([Sankaran et al., 2019](#Ch004_59-79_S0169716123000032.xhtml#bb0070)), Fingerprint Recognition [(Jawade et al., 2021](#Ch004_59-79_S0169716123000032.xhtml#bb0020), [2022)](#Ch004_59-79_S0169716123000032.xhtml#bb0025), Image Retrieval ([Mohan et al., 2020](#Ch004_59-79_S0169716123000032.xhtml#bb0050)), Person Re-Identification ([Lee et al., 2022](#Ch004_59-79_S0169716123000032.xhtml#bb0040)), and Cross-Modal Retrieval ([Wei et al., 2020](#Ch004_59-79_S0169716123000032.xhtml#bb0095)), ([Jawade et al., 2023](#Ch004_59-79_S0169716123000032.xhtml#bb0030)). In such a scenario, DML-based loss formulations are used to create highly discriminable embedding spaces. These embedding spaces are designed so as to have a feature representation of samples belonging to the same class to be clustered together and well separated from clusters of other classes in the manifold.

In this chapter, we discuss popular DML formulations which are part of the literature. We will restrict our discussion to methods that have found applications in different computer vision tasks. We have organized the different loss formulations into three categories based on the type of overall objective formulations as shown in [Fig. 1](#Ch004_59-79_S0169716123000032.xhtml#f0010). The first category consists of pair-based formulations, which formulate the overall objectives based on direct pair-based interactions between samples in the dataset. The second is a group of methods that use a pseudo class representative known as a proxy to formulate the final optimization. Finally, we also discuss regularization methods that try to incorporate auxiliary information that aids in creating more optimal feature representations.

![Fig. 1 An illustration describing various types of deep metric learning losses.](images/S0169716123000032/f04-01-9780443184307.jpg)

[Fig. 1](#Ch004_59-79_S0169716123000032.xhtml#B-f0010) An illustration describing various types of deep metric learning losses.

##  2: Background

In this section, we will introduce the mathematical notations and assumptions that are commonly used in DML literature.

Consider a dataset *X* = {(*x*[1], *y*[1]), (*x*[2], *y*[2])…(*x*[*n*], *y*[*n*])}![si1\_e](images/S0169716123000032/si1_e.png), consisting of a set of images and their corresponding class labels. Let *ϕ* be a function parameterized by *θ* that maps each image *x*[*i*] into an embedding space of *d* dimensions, i.e.,

$\\begin{array}{r} {f\_{i} = \\Phi(x\_{i};\\theta\_{\\phi});\\forall i \\in n} \\\\ \\end{array}$

![si2\_e](images/S0169716123000032/si2_e.png)  (1)
