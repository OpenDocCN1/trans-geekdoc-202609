# Learning sparse deep neural networks with a spike-and-slab prior

Yan Sun, Qifan Song, Faming Liang *

Department of Statistics, Purdue University, West Lafayette, IN 47907, USA

# ARTICLE INFO

Article history:
Received 6 February 2021
Received in revised form 27 June 2021
Accepted 11 September 2021
Available online 24 September 2021

Keywords:
Bayesian neural network
Sparse deep learning
Posterior consistency
High-dimensional nonlinear variable selection
Model calibration

# ABSTRACT

Deep learning has achieved great successes in many machine learning tasks. However, the deep neural networks (DNNs) are often severely over-parameterized, making them computationally expensive, memory intensive, less interpretable and mis-calibrated. We study sparse DNNs under the Bayesian framework: we establish posterior consistency and structure selection consistency for Bayesian DNNs with a spike-and-slab prior, and illustrate their performance using examples on high-dimensional nonlinear variable selection, large network compression and model calibration. Our numerical results indicate that sparsity is essential for improving the prediction accuracy and calibration of the DNN.

© 2021 Elsevier B.V. All rights reserved.

# 1. Introduction

During the past decade, deep neural networks (DNNs) have achieved great successes in solving many complex machine learning tasks such as pattern recognition and natural language processing. A key factor to these successes is their universal approximation power, while heavily relying on a large number of parameters. The DNNs used in these tasks may consist of hundreds of layers and billions of parameters, see e.g. He et al. (2016) on image classification. Many DNNs are severely over-parameterized; for some networks only 5% of parameters are enough to achieve acceptable models (Denil et al., 2013). Moreover, these over-parameterized networks are no longer well calibrated (Guo et al., 2017).

To reduce the complexity of the DNN and improve its calibration, sparse deep learning has been considered by some researchers, see e.g. Schmidt-Hieber (2020), Bauer and Kohler (2019), Polson and Ročková (2018) and Sun et al. (2021). The approximation power of the sparse DNN has been studied from both frequentist and Bayesian perspectives. From the frequentist perspective, Schmidt-Hieber (2020) and Bauer and Kohler (2019) quantify the approximation error of the sparse DNN in approximating Hölder smooth functions. From the Bayesian perspective, Polson and Ročková (2018) established posterior consistency for the Bayesian DNN with a spike-and-slab prior, and Sun et al. (2021) established posterior consistency for the Bayesian DNN with a mixture Gaussian prior. Quite recently, the theory of sparse deep learning has also been developed under the framework of variational inference, see e.g. Chérief-Abdellatif (2020), Bai et al. (2020b) and Bai et al. (2020a). However, due to the approximation nature of the variational posterior distribution, the resulting statistical inference is often sub-optimal.

This paper studies theoretical properties of the Bayesian sparse DNN with a spike-and-slab prior. It is closely related to Polson and Ročková (2018), which both employ a spike-and-slab prior, but our theory is more general. In particular, our theory is developed under the assumption that the input dimension and the upper bound of the connection weights

* Corresponding author.
E-mail address: fliang@purdue.edu (F. Liang).