
based methods obtain linear upper and lower bounds for output neurons with respect to inputs, when plugging-in the function into \(\underline{m}\), the whole loss function will be differentiable. Surprisingly, although those bounds are much tighter than IBP, when conducting certified training, it leads to much worse performance than IBP. Zhang et al. (2020a) observed that linear relaxation-based training usually leads to small norms of the model parameters, thus forcing many neurons to be inactive. A conjecture is that since linear relaxation-based methods have much tighter bounds when neurons are either inactive or active, they tend to over-regularize the network to enforce most of neurons to be inactive. However, it remains to be an open question on why this phenomenon happens more common in linear relaxation-based training than in IBP training.

However, linear relaxation-based training is still useful for certified defense. In particular, Zhang et al. (2020a) developed a Crown-IBP training method that combines the linear relaxation-based method with IBP. As mentioned before, the problem of IBP training is that the bounds tend to be very bad near initialization, which makes training extremely unstable. Crown-IBP uses CROWN training (a linear relaxation-based method) at the initial phase and then gradually switches the training objective to IBP. More specifically, Crown-IBP considers the following training objective:

\(\min_\theta E_{(x,y)}[\kappa L(x; y; \theta) + (1 - \kappa)L(-((1 - \beta)\underline{m}_{\text{IBP}}(x, \epsilon) + \beta \underline{m}_{\text{CROWN-IBP}}(x, \epsilon)); y; \theta)].\)

where \(\underline{m}\) is a combination of two bounds such that \(\underline{m}_{\text{CROWN-IBP}}\) conducts IBP in the forward bounding pass and CROWN bound propagation in a backward bounding pass. By setting \(\beta\) to be close to 1 in the beginning and gradually reduced to 0, the Crown-IBP training methods take the advantage of CROWN (linear relaxation-based methods) in the initial training phase but do not over-regularize the neurons. More details can be found in (Zhang et al., 2020a).

## 14.3 Empirical comparison

We present the comparison of existing certified training approaches on MNIST and CIFAR-10 datasets. For simplicity, we focus on the \(\ell_\infty\) certified robust training with several commonly used settings of \(\epsilon\). Experimental results are presented in Table 14.1.

Table 14.1 A comparison of IBP, Crown-IBP, and Improved IBP on MNIST and CIFAR-10 datasets.

| Dataset | \(\epsilon\) | Training Method | Standard error | Certified error |
|---|---|---|---|---|
| MNIST | 0.4 | IBP | 1.66 | 15.01 |
| MNIST | 0.4 | Crown-IBP | 2.17 | 12.06 |
| MNIST | 0.4 | Improved IBP | 2.2 | 10.82 |
| CIFAR-10 | 8/255 | IBP | 58.72 | 69.88 |
| CIFAR-10 | 8/255 | Crown-IBP | 53.73 | 66.62 |
| CIFAR-10 | 8/255 | Improved IBP | 51.06 | 65.05 |

Note that for IBP training, we mainly refer to the training recipe proposed in (Gowal et al., 2018); for Crown-IBP, we used the results from (Zhang et al., 2020a) and (Xu et al., 2020b), and for improved IBP, we consider IBP with the tricks proposed by Shi et al. (2021). For both datasets, we use the seven-layer CNN model used commonly in those papers. We can observe that current methods already achieve reasonably good performance on MNIST datasets; since each pixel value is normalized to be [0, 1], a perturbation of \(\epsilon = 0.4\) is already very large, and certified training can obtain models with almost 10% data correctly and robustly classified on MNIST. However, the performance of CIFAR-10 is still not ideal, so many recent works still try to improve the certified robustness accuracy on CIFAR-10 and larger-scale datasets.

## 14.4 Extended reading

- Fast certified robustness training: (Boopathy et al., 2021).

## Adversary detection

Another type of defense methods against evasion attacks, which we call _adversary detection_, aims to detect the existence of adversarial examples, rather than trying to classify them into the correct classes. The main assumption behind these methods is that the adversarial examples came from a different distribution compared with natural samples, so they could be detected with carefully designed detectors. In addition to evasion attacks, similar methodology can be applied to detect other types of adversary attacks. In this section, we first discuss adversarial detection to testing time adversarial attacks. We then discuss detection methods against other attack scenarios.

### 15.1 Detecting adversarial inputs

A straightforward way toward adversarial example detection is to build a simple binary classifier separating the adversarial examples apart from the clean data. However, these methods usually suffer from lack of generalization to unforeseen attacks. Therefore an effective detection method is usually based on some characteristics of adversarial attacks instead of purely classifying an existing attack. In the following, we will introduce several popular detection methods.

_Density estimation._ A common observation is that adversarial examples often lie outside the natural image manifold, and many detection methods are based on these characteristics. In particular, Feinman et al. (2017) proposed to use kernel density estimation to measure how far a sample is from the provided data manifold. Letting \(X = \{x_1, \dots, x_n\}\) be training samples stored in the database, we can assume that the training data distribution is a mixture of Gaussians centered at those points, denoted as \(p_X(x)\). Therefore, for a testing instance \(x\), the density can be estimated as \(p_X(x) = \frac{1}{n} \sum_{i=1}^n K_\sigma (x_i, x),\), where \(K_\sigma(\cdot, \cdot)\) is a kernel function. A commonly used kernel function is the Gaussian kernel, where \(K_\sigma (x_i, x) = e^{-\frac{||x_i - x||^2}{2\sigma^2}}\). The KD-detection method proposed in (Feinman et al., 2017) fits the density function on each label. If an incoming example x is predicted as label y, we use the density estimation based on the samples from class y. Once \(p_X(x)\) is computed, we can then get the statistics of KD estimation of natural examples versus adversarial examples to determine the threshold for detecting adversarial examples.

Many other algorithms also fall into this kernel density estimation framework. For example, Ma et al. (2018) observed that the local intrinsic dimension (LID) of hidden layer outputs differ between adversarial examples and natural examples, so they conduct density estimations on hidden layer features (instead of input layers) to detect adversarial examples. It is also observed in many works that an ensemble of several different layers can significantly boost the performance of adversarial detection in computer vision tasks, so most of the existing detectors are based on not only one, but on several hidden layer features. In another work, Lee et al. (2018) generated the class of conditional Gaussian distributions with respect to hidden layer output of the DNN under Gaussian discriminant analysis, which results in a confidence score based on the Mahalanobis distance (MAHA), followed by a logistic regression model on the confidence scores to detect adversarial examples. A joint statistical test pooling information from multiple layers is proposed by Raghuram et al. (2020) to detect adversarial examples.

Feature attribution methods for adversarial detection. In addition to density estimation based on hidden layer features, many works identify some other important features that can distinguish adversarial examples from natural examples. Here we will discuss an interesting finding that adversarial examples can be detected by feature attribution methods (Yang et al., 2020d).

Assume that the model is a function \(f : \mathbb{R}^d \to [0, 1]^K\) and a feature attribution method \(\phi\) maps an input image \(x \in \mathbb{R}^d\) to a \(d\)-dimensional vector \(\phi(x) \in \mathbb{R}^d\), where each element in \(\phi(x)\) corresponds to how important the feature contributes to the model prediction. There are many feature attribution methods developed in the literature. For instance, the widely used leave-one-out (LOO) feature attribution method (Zeiler and Fergus, 2014; Li et al., 2016) measures the importance of each feature by the change of model output when removing the feature (e.g., setting it as 0). Mathematically, the LOO method designs \(\phi\) as \(\phi(x)_i = f(x)_c - f(x_{(i)})_c,\), where c is the target class we are interested in, and \(x_{(i)}\) means x with feature i removed.
