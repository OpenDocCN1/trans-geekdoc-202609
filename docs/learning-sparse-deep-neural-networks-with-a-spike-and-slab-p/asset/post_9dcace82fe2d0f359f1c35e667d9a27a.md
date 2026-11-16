
## Learning sparse deep neural networks with a spike-and-slab prior

Yan Sun, Qifan Song, Faming Liang *

Department of Statistics, Purdue University, West Lafayette, IN 47907, USA

## ARTICLE INFO

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

## ABSTRACT

Deep learning has achieved great successes in many machine learning tasks. However, the deep neural networks (DNNs) are often severely over-parameterized, making them computationally expensive, memory intensive, less interpretable and mis-calibrated. We study sparse DNNs under the Bayesian framework: we establish posterior consistency and structure selection consistency for Bayesian DNNs with a spike-and-slab prior, and illustrate their performance using examples on high-dimensional nonlinear variable selection, large network compression and model calibration. Our numerical results indicate that sparsity is essential for improving the prediction accuracy and calibration of the DNN.

© 2021 Elsevier B.V. All rights reserved.

## 1. Introduction

During the past decade, deep neural networks (DNNs) have achieved great successes in solving many complex machine learning tasks such as pattern recognition and natural language processing. A key factor to these successes is their universal approximation power, while heavily relying on a large number of parameters. The DNNs used in these tasks may consist of hundreds of layers and billions of parameters, see e.g. He et al. (2016) on image classification. Many DNNs are severely over-parameterized; for some networks only 5% of parameters are enough to achieve acceptable models (Denil et al., 2013). Moreover, these over-parameterized networks are no longer well calibrated (Guo et al., 2017).

To reduce the complexity of the DNN and improve its calibration, sparse deep learning has been considered by some researchers, see e.g. Schmidt-Hieber (2020), Bauer and Kohler (2019), Polson and Ročková (2018) and Sun et al. (2021). The approximation power of the sparse DNN has been studied from both frequentist and Bayesian perspectives. From the frequentist perspective, Schmidt-Hieber (2020) and Bauer and Kohler (2019) quantify the approximation error of the sparse DNN in approximating Hölder smooth functions. From the Bayesian perspective, Polson and Ročková (2018) established posterior consistency for the Bayesian DNN with a spike-and-slab prior, and Sun et al. (2021) established posterior consistency for the Bayesian DNN with a mixture Gaussian prior. Quite recently, the theory of sparse deep learning has also been developed under the framework of variational inference, see e.g. Chérief-Abdellatif (2020), Bai et al. (2020b) and Bai et al. (2020a). However, due to the approximation nature of the variational posterior distribution, the resulting statistical inference is often sub-optimal.

This paper studies theoretical properties of the Bayesian sparse DNN with a spike-and-slab prior. It is closely related to Polson and Ročková (2018), which both employ a spike-and-slab prior, but our theory is more general. In particular, our theory is developed under the assumption that the input dimension and the upper bound of the connection weights can increase with the training sample size; and the activation function is Lipschitz continuous, which has covered many popular activation functions such as ReLU, tanh, and sigmoid. In contrast, Polson and Ročková (2018) assumes that the input dimension is of the order \(O(1)\), the connections weights are bounded, and the activation function is ReLU. This paper also provides a scalable algorithm for simulating from the posterior distribution of the Bayesian DNN. The numerical results indicate that sparsity is essential for improving the prediction accuracy and model calibration of the DNN.

The remaining part of this paper is organized as follows. Section 2 presents the theoretical results. Section 3 describes a stochastic gradient Markov chain Monte Carlo (SGMCMC) algorithm for Bayesian DNN simulation. Section 4 presents a network compression example. Section 5 concludes the paper with a brief discussion.

* Corresponding author.
E-mail address: fliang@purdue.edu (F. Liang).

## 2. Theoretical results

Let \(D_n = \{x^{(i)}, y^{(i)}\}_{i=1}^n\) denote a training dataset of \(n\) i.i.d observations, where \(x^{(i)} \in \mathbb{R}^{p_n}\), \(y^{(i)} \in \mathbb{R}\), and \(p_n\) denotes the dimension of the input variable and is assumed to grow with the training sample size \(n\). We assume that the data are generated from a generalized linear model with the pdf/pmf given by

```
\(f(y|\mu^*(x)) = \exp\{A(\mu^*(x))y + B(\mu^*(x)) + C(y)\},\)
```

where \(\mu^*(x)\) denotes an unknown function of \(x\), and \(A(\cdot)\), \(B(\cdot)\) and \(C(\cdot)\) are appropriately defined functions. For example, for logistic regression, we have \(A(\mu^*) = \mu^*\), \(B(\mu^*) = -\log(1+e^{\mu^*})\) and \(C(y) = 1\); and for normal regression, by introducing an extra dispersion parameter \(\sigma^2\), we have \(A(\mu^*) = \mu^*/\sigma^2\), \(B(\mu^*) = -\mu^{*2}/2\sigma^2\) and \(C(y) = -y^2/2\sigma^2 - \log(2\pi\sigma^2)/2\). For simplicity of analysis, \(\sigma^2\) is assumed to be known. To model the data, we propose to approximate \(\mu^*(x)\) by a DNN with \(H_n - 1\) hidden layers. Let \(L_h\) denote the number of hidden units at layer \(h\), with \(L_{H_n} = 1\) for the output layer and \(L_0 = p_n\) for the input layer. Let \(w^h \in \mathbb{R}^{L_h \times L_{h-1}}\) and \(b^h \in \mathbb{R}^{L_h \times 1}\), \(h \in \{1, 2, \dots, H_n\}\) denote the weights and bias of layer \(h\), respectively. Let \(\psi^h: \mathbb{R}^{L_h \times 1} \to \mathbb{R}^{L_h \times 1}\) denote a mapping which applies a piece-wise differentiable activation function \(\psi\) to each entry of the input. In summary, the DNN forms a nonlinear mapping

```
\(\mu(\beta, x) = w^{H_n}\psi^{H_n-1}[\cdots \psi^1[w^1x + b^1]\cdots] + b^{H_n},\) (1)
```

where \(\beta = \{w_{ij}^h, b_k^h : 1 \le h \le H_n, 1 \le i, k \le L_h, 1 \le j \le L_{h-1}\}\) denotes the collection of weights and biases of the DNN. A fully connected DNN consists of \(K_n = |\beta| = \sum_{h=1}^{H_n} (L_{h-1} \times L_h + L_h)\) tuning parameters. To facilitate representation for sparse DNNs, we re-parameterize \(\beta\) by introducing an indicator variable for each element of \(\beta\), which indicates the existence of the corresponding connection. Here the bias is treated as a special connection with a constant input of 1. Let \(w^h = \tilde{w}^h \circ y^{w^h}\) and \(b^h = \tilde{b}^h \circ y^{b^h}\), where \(y^{w^h}\) and \(y^{b^h}\) are the matrices or vectors of indicators, and \(\circ\) denotes element-wise product. Correspondingly, we define \(\tilde{\beta} = \{\tilde{w}_{ij}^h, \tilde{b}_k^h\}\) and \(\gamma = \{y_{ij}^{w^h}, y_k^{b^h}\}\) which represent connection weights and network structure, respectively. For notational simplicity, we rewrite \(\tilde{\beta}\) and \(\gamma\) as \(\tilde{\beta} = (\tilde{\beta}_1, \tilde{\beta}_2, \dots, \tilde{\beta}_{K_n}) \in \mathbb{R}^{K_n}\) and \(\gamma = (\gamma_1, \gamma_2, \dots, \gamma_{K_n}) \in \{0, 1\}^{K_n}\). Correspondingly, we have \(\beta = \tilde{\beta} \circ \gamma\).

### 2.1. Regularity conditions on sparse DNNs

With slight abuse of notation, we will rewrite \(\mu(\beta, x)\) in (1) for the sparse DNN as \(\mu(\beta, \gamma, x)\) by including the network structure information. In what follows, we characterize how well \(\mu^*(x)\) can be approximated by \(\mu(\beta, \gamma, x)\) with a sparse DNN from the Bayesian perspective. For this purpose, we assume the following regularity conditions:

- A.1 The input \(x\) is bounded by 1 entry-wisely, i.e. \(x \in \Omega = [-1, 1]^{p_n}\), and the density of \(x\) is bounded in its support \(\Omega\) uniformly with respect to \(n\).

- A.2 The unknown regression mean function \(\mu^*(x)\) can be well approximated by a sparse DNN model such that \(\mu(\beta^*, \gamma^*, x)\) satisfies

  - A.2.1 \(\|\mu^*(x) - \mu(\beta^*, \gamma^*, x)\|_{l^2(\Omega)}^2 \le \varpi_n\), where the approximation error \(\varpi_n \to 0\) as the sample size \(n \to \infty\).

  - A.2.2 \(H_n \log K_n \ge C \log n\) for some constant \(C > 0\), \(1 < r_n^* H_n \log K_n < n^1\) and \(\|\beta^*\|_\infty < E_n\), where \(E_n\) is a sequence satisfying \(\log E_n = O(\log K_n)\), and \(r_n^*\) is the network size, i.e., \(r_n^* = \sum_{i=1}^{K_n} \gamma_i^*\).

- A.3 The activation function \(\psi\) is Lipschitz continuous with a Lipschitz constant of 1.

Refer to the supplementary material for more discussions on the conditions, where we show how our Bayesian DNN theory is compatible with the existing sparse DNN approximation theory.
