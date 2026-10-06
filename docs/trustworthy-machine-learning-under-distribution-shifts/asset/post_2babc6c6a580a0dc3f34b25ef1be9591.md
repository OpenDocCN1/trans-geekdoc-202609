
# 4 EXPLORING VARIANT PARAMETERS FOR INVARIANT LEARNING

![](img/1aedbd555ac8a0e63b6116db31c6c2f8_81_0.png)

FIGURE 4.2. Learning flow of EVIL: The blocks in the middle are the dataset where different levels of shades denote different classes, and different types of color indicate different data distributions. The blue arrows ($\rightarrow$) and gray arrows ($\rightarrow$) stand for the information related to label and distribution, respectively. Moreover, the blue solid lines ($—$) and gray dashed lines ($\cdots$) that connect neurons are the invariant parameters and pruned ones, respectively.

Parameter Exploration. In this step, we mainly have two optimization targets:

```
$$\min_{\theta_{inv} \otimes \theta} \mathcal{L}_{inv}(h(f_{\theta_{inv}}(\mathbf{x})), y), \quad (4.3)$$
$$\min_{\theta_{var} \oplus \theta} \mathcal{L}_{var}(g(f_{\theta_{var}}(\mathbf{x})), d), \quad (4.4)$$
```

where $\theta_{inv} = m \circ \theta$ and $\theta_{var} = (1 - m) \circ \theta$ denote the corresponding invariant parameters and variant ones divided by the mask $m$, $h$ and $g$ are two fully-connected layers that map the extracted features into class label space $\mathbb{R}^c$ and distribution index space $\mathbb{R}^m$, respectively. Intuitively, the objective $\mathcal{L}_{inv}$ is the classification task, which is to make predictions based on the label information, and $\mathcal{L}_{var}$ to discriminate each distribution based on the distribution information, which is spurious and unwanted.

By minimizing $\mathcal{L}_{inv}$ in Equation (4.3), the gradient magnitude $\nabla_{\theta_{inv}} \mathcal{L}_{inv}$ [199] can be used to find the most relevant parameters to our loss function (Note that other aforementioned sparse training criteria can be used). Similarly, by minimizing $\mathcal{L}_{var}$ in Equation (4.4), those parameters with large $\nabla_{\theta_{var}} \mathcal{L}_{var}$ are sensitive to the spurious information, which cannot help produce invariant features. Thus, we can sort the parameters based on the gradient magnitude to show how much they are activated by their corresponding objective.

## 4.4 METHODOLOGY

### Algorithm 3 EVIL

**Require:** Multiple training sets $\mathcal{E} = \{e_1, \dots, e_m\}$; Learning model $f_\theta$; Cosine annealing function $S(t, \alpha, T)$, mask $\mathbf{m}$ initialized based on weight value, iteration number of training $T_{pre}$.

```
1: **for** $t = 0, 1, \dots, T$ **do**
2:   Optimize mask via Equation (4.3); (*Invariant learning*)
3:   **if** $t > T_{pre}$ and $t%\Delta T == 0$ **then**
4:     Obtain gradients of $\mathbf{m}_{inv}$ and $\mathbf{m}_{var}$ via Equation (4.3) and Equation (4.4), respectively;
5:     *Parameter exploration*
6:     Update the mask $\mathbf{m}$ via Equation (4.5);
7: **end if**
8: **end for**
```

Further, to dynamically improve our sparsification. We propose to update the mask $\mathbf{m}$ for every $\Delta T$ iterations by rejecting the least activated invariant parameters, meanwhile calling the least activated variant parameters as invariant variants. Specifically, we process this

```
$\mathbf{m} [ArgTopK(-\|\nabla_{\mathbf{m}_{inv}}\|| \cdot |\mathbf{m}||_0 S(t, \alpha, T))] = 0$,
$\mathbf{m} [ArgTopK(-\|\nabla_{\mathbf{m}_{var}}\|| \cdot |\mathbf{m}||_0 S(t, \alpha, T))] = 1,$ (4.5)
```

where $ArgTopK(v, k)$ returns the indices of top-k elements representing value $v$, $\mathbf{m} [\cdot]$ denotes indexing $\mathbf{m}$. Moreover, to decide how many parameters are changed, we follow Dettmers & Zettlemoyer [203] to use cosine annealing function $S(t, \alpha, T) = \frac{\alpha}{2}(1+\cos(\frac{\pi t}{T}))$, where $t$ and $T$ are the current iteration and total iterations, respectively, and hyper-parameter $\alpha$ denotes the largest value. Intuitively, such cosine annealing function gradually changes from $\alpha < 1$ to 0. Through Equation (4.5), the obtained mask finds the parameters that are less affected by the distribution and more related to our learning task than the previous one, further improving the invariant learning performance.

**Invariant Learning.** After obtaining the updated mask $\mathbf{m}$, we then use the invariant parameters as a subnet to learn invariant learning, which is generally formed as:

```
$\mathcal{L}_{inv}(h(f_{\theta_{inv}}(\mathbf{x})), y) = \mathcal{L}_{cee} + \lambda \mathcal{L}_{reg},$ (4.6)
```

where the first term is the empirical risk computed through cross-entropy loss, and the second term is the invariant learning regularization with penalty weight $\lambda$, which can be realized by many popular methods. For instance, to use IRM, the regularization is

```
$\mathcal{L}_{reg} = \frac{1}{n} \sum_{x \in \mathcal{X}} \|\nabla_{\theta} \mathcal{L}_{cee}(h(f_{\theta}(\mathbf{x})), y)\|^2,$ (4.7)
```

To use REx, the regularization is

```
$\mathcal{L}_{reg} = \frac{1}{n} \sum_{x \in \mathcal{X}} \|\nabla_{\theta} \mathcal{L}_{var}(g(f_{\theta}(\mathbf{x})), d)\|^2,$ (4.8)
```

Moreover, to use DRO, we focus on the regularization:

```
$\mathcal{L}_{reg} = \frac{1}{n} \sum_{x \in \mathcal{X}} \|\nabla_{\theta} \mathcal{L}_{cee}(h(f_{\theta}(\mathbf{x})), y)\|^2,$ (4.9)
```

By combining with existing methods, we report the results under different sparsity (20%, 40%, 60%, 80%).

## 4.5 EXPERIMENT

All experiments are conducted on a single NVIDIA 3090 using PyTorch. To implement our framework, we first pre-train models using ERM for 1,000 iterations. Then, a mask is initialized by the weight value. Specifically, by setting sparsity ratio R, we select $\theta$-largest weights by setting their corresponding mask as 1. During parameter exploration, we use the gradient of invariant loss $\mathcal{L}_{inv}$ which we sort the invariant parameters from largest to smallest. Then, we reject the $S(t, \alpha, T)$-invariant parameters by setting their corresponding mask to 0. Similarly, we use the gradient of $\mathcal{L}_{var}$ to sort the variant parameters and collect top-$S(t, \alpha, T)$. During invariant learning, we apply the mask to parameter values as well as their gradients to conduct sparse training.

![](img/1aedbd555ac8a0e63b6116db31c6c2f8_84_0.png)

FIGURE 4.3. Illustration of our optimizers.

To optimize our model, we use Adam [209] optimizer with an initial learning rate $1e-3$ without decay. Moreover, to avoid the conflict between optimizing invariant parameters and variant parameters, we adopt two Adam optimizers, denoted as $Adam_1$ and $Adam_2$, to correspondingly include the invariant and variant parameters. Moreover, $Adam_1$ would include the class prediction $h$ and $Adam_2$ would include the distribution prediction $g$, as illustrated in Figure 4.3. During the training, $Adam_1$ is mainly used to optimize the invariant parameters, but $Adam_2$ is just employed to optimize the variant ones.

For implementing baseline methods, we mainly follow [176] to set the hyperparameters. Specifically, for DRO, we set $\eta = le-2$ to update the group importance. For ERM, we set $\lambda = 1e^2$ to trade off the invariant regularizer. The similar $\lambda$ for penalization from REx is set to $1e$. For CORAL and MMD, set the trade-off weight $\gamma$ as 1. For implementing SagNet, we set the weight for adversarial loss as 0.1. For SAM, we do not use Adaptive SAM [210] and set the perturbation magnitude $\rho$ as 0.05.

### 4.5.1 Practical Implementation
