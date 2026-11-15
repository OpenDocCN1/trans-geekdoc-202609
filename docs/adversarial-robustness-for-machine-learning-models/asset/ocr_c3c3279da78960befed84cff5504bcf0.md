+   1. Although neural networks are good at extracting informative features from images/audio/text, there are many other applications where neural networks may not outperform other classical machine learning models. In particular, the gradient boosting decision tree (GBDT) model is more widely used than neural networks in many data mining tasks. Many Kaggle data mining competitions are won by GBDT models, and GBDT is still widely used in ranking systems in industry. Hence it is important to understand how to measure and improve the robustness of these discrete models.

+   2. Discrete structures may be more robust than neural networks since the discrete operations are less sensitive to small perturbations. Several practical defense approaches have combined nearest-neighbor classifier with neural networks (Papernot and McDaniel, 2018; Dubey et al., 2019; Sitawarin and Wagner, 2019). Studying the robustness of discrete models is thus essential for understanding whether they can provide improved robustness.

# ## 16.1 Evaluating the robustness of K-nearest-neighbor models

Nearest-neighbor (NN) classifiers predict the label of a testing instance by one or _K_ closest samples in the database. Assume that there are _C_ labels in total. We use \(\{(\mathbf{x}_1, y_1), \dots, (\mathbf{x}_n, y_n)\}\) to denote the database where each \(\mathbf{x}_i\) is a _d_-dimensional vector, and \(y_i \in \{1, \dots, C\}\) is the corresponding label. A _K_-NN classifier \(f : \mathbb{R}^d \rightarrow \{1, \dots, C\}\) maps a test instance to a predicted label. Given a test instance \(\mathbf{z} \in \mathbb{R}^d\), the classifier first identifies the _K_-nearest neighbors \(\{\mathbf{x}_{\pi(1)}, \dots, \mathbf{x}_{\pi(K)}\}\) based on the Euclidean distance \(\|\mathbf{x}_i - \mathbf{z}\|\) and then predicts the final label by majority voting among \(\{y_{\pi(1)}, \dots, y_{\pi(K)}\}\).

Given a test sample **_z_**, assume that it is correctly classified as class-1 by the NN model. An adversarial perturbation is defined as \(\boldsymbol{\delta} \in \mathbb{R}^d\) such that \(f(\mathbf{z} + \boldsymbol{\delta}) \neq 1\). Robustness evaluation aims to find the minimum-norm adversarial perturbation

```
\(\boldsymbol{\delta}^* = \arg \min_{\boldsymbol{\delta}} \|\boldsymbol{\delta}\| \text{ s.t. } f(\mathbf{z} + \boldsymbol{\delta}) \neq 1, \quad \text{(16.1)}\)
```

and we define \(\epsilon^* = \|\boldsymbol{\delta}^*\|\) as the norm of this perturbation. In many cases it is challenging to obtain the optimal solution of (16.1), so we will discuss algorithms for attack and verification. Attack algorithms aim to find a feasible (but may be subpotimal) solution \(\boldsymbol{\delta}\) for (16.1), which serves as an