
the learning trajectory may pass through many different structures and eventually arrive at a region that is a locally convex bowl. AdaGrad shrinks the learning rate according to the entire history of the squared gradient and may have made the learning rate too small before arriving at such a convex structure. RMSProp uses an exponentially decaying average to discard history from the extreme past so that it can converge rapidly after finding a convex bowl, as if it were an instance of the AdaGrad algorithm initialized within that bowl.

```
**Algorithm 8.4** The AdaGrad algorithm

**Require:** Global learning rate $\epsilon$

**Require:** Initial parameter $\boldsymbol{\theta}$

**Require:** Small constant $\delta$, perhaps $10^{-7}$, for numerical stability

Initialize gradient accumulation variable $\boldsymbol{r} = \mathbf{0}$

**while** stopping criterion not met **do**

&emsp;Sample a minibatch of $m$ examples from the training set $\{\mathbf{x}^{(1)},\ldots,\mathbf{x}^{(m)}\}$ with corresponding targets $\mathbf{y}^{(i)}$.

&emsp;Compute gradient: $\mathbf{g} \leftarrow \frac{1}{m}\nabla_{\theta}\sum_i L(f(\mathbf{x}^{(i)};\boldsymbol{\theta}),\mathbf{y}^{(i)})$.

&emsp;Accumulate squared gradient: $\mathbf{r} \leftarrow \mathbf{r} + \mathbf{g} \odot \mathbf{g}$.

&emsp;Compute update: $\Delta\boldsymbol{\theta} \leftarrow -\frac{\epsilon}{\delta+\sqrt{\mathbf{r}}} \odot \mathbf{g}$. (Division and square root applied element-wise)

&emsp;Apply update: $\boldsymbol{\theta} \leftarrow \boldsymbol{\theta} + \Delta\boldsymbol{\theta}$.

**end while**
```

```
**Algorithm 8.5** The RMSProp algorithm

**Require:** Global learning rate $\epsilon$, decay rate $\rho$

**Require:** Initial parameter $\boldsymbol{\theta}$

**Require:** Small constant $\delta$, usually $10^{-6}$, used to stabilize division by small numbers

Initialize accumulation variables $\mathbf{r} = \mathbf{0}$

**while** stopping criterion not met **do**

&emsp;Sample a minibatch of $m$ examples from the training set $\{\mathbf{x}^{(1)},\ldots,\mathbf{x}^{(m)}\}$ with corresponding targets $\mathbf{y}^{(i)}$.

&emsp;Compute gradient: $\mathbf{g} \leftarrow \frac{1}{m}\nabla_{\theta}\sum_i L(f(\mathbf{x}^{(i)};\boldsymbol{\theta}),\mathbf{y}^{(i)})$.

&emsp;Accumulate squared gradient: $\mathbf{r} \leftarrow \rho\mathbf{r} + (1-\rho)\mathbf{g} \odot \mathbf{g}$.

&emsp;Compute parameter update: $\Delta\boldsymbol{\theta} = -\frac{\epsilon}{\sqrt{\delta+\mathbf{r}}} \odot \mathbf{g}$. ($\frac{1}{\sqrt{\delta+\mathbf{r}}}$ applied element-wise)

&emsp;Apply update: $\boldsymbol{\theta} \leftarrow \boldsymbol{\theta} + \Delta\boldsymbol{\theta}$.

**end while**
```

RMSProp is shown in its standard form in algorithm 8.5 and combined with Nesterov momentum in algorithm 8.6. Compared to AdaGrad, the use of the moving average introduces a new hyperparameter, ρ, that controls the length scale of the moving average.

Empirically, RMSProp has been shown to be an effective and practical optimization algorithm for deep neural networks. It is currently one of the go-to optimization methods being employed routinely by deep learning practitioners.

```
Algorithm 8.6 RMSProp algorithm with Nesterov momentum
Require: Global learning rate ε, decay rate ρ, momentum coefficient α
Require: Initial parameter θ, initial velocity v
Initialize accumulation variable r = 0
while stopping criterion not met do
Sample a minibatch of m examples from the training set {x^(1),...,x^(m)} with corresponding targets y^(i).
Compute interim update: θ~ ← θ + αv.
Compute gradient: g ← 1/m ∇_θ~ Σ_i L(f(x^(i);θ~), y^(i)).
Accumulate gradient: r ← ρr + (1 - ρ)g ⊙ g.
Compute velocity update: v ← αv - ε/√r ⊙ g. (1/√r applied element-wise)
Apply update: θ ← θ + v.
end while
```

## 8.5.3 Adam

Adam (Kingma and Ba, 2014) is yet another adaptive learning rate optimization algorithm and is presented in algorithm 8.7. The name “Adam” derives from the phrase “adaptive moments.” In the context of the earlier algorithms, it is perhaps best seen as a variant on the combination of RMSProp and momentum with a few important distinctions. First, in Adam, momentum is incorporated directly as an estimate of the first-order moment (with exponential weighting) of the gradient. The most straightforward way to add momentum to RMSProp is to apply momentum to the rescaled gradients. The use of momentum in combination with rescaling does not have a clear theoretical motivation. Second, Adam includes bias corrections to the estimates of both the first-order moments (the momentum term) and the (uncentered) second-order moments to account for their initialization at the origin (see algorithm 8.7). RMSProp also incorporates an estimate of the (uncentered) second-order moment; however, it lacks the correction factor. Thus, unlike in Adam, the RMSProp second-order moment estimate may have high bias early in training. Adam is generally regarded as being fairly robust to the choice of hyperparameters, though the learning rate sometimes needs to be changed from the suggested default.

```
Algorithm 8.7 The Adam algorithm
Require: Step size ε (Suggested default: 0.001)
Require: Exponential decay rates for moment estimates, ρ1 and ρ2 in [0,1). (Suggested defaults: 0.9 and 0.999 respectively)
Require: Small constant δ used for numerical stabilization (Suggested default: 10^{-8})
Require: Initial parameters θ
Initialize 1st and 2nd moment variables s = 0, r = 0
Initialize time step t = 0
while stopping criterion not met do
Sample a minibatch of m examples from the training set {x^{(1)},...,x^{(m)}} with corresponding targets y^{(i)}.
Compute gradient: g ← (1/m) ∇θ ∑i L(f(x^{(i)};θ), y^{(i)})
t ← t + 1
Update biased first moment estimate: s ← ρ1 s + (1 - ρ1) g
Update biased second moment estimate: r ← ρ2 r + (1 - ρ2) g ⊙ g
Correct bias in first moment: ŝ ← s / (1 - ρ1^t)
Correct bias in second moment: r̂ ← r / (1 - ρ2^t)
Compute update: Δθ = -ε ŝ / sqrt(r̂ + δ)  (operations applied element-wise)
Apply update: θ ← θ + Δθ
end while
```

## 8.5.4 Choosing the Right Optimization Algorithm

We have discussed a series of related algorithms that each seek to address the challenge of optimizing deep models by adapting the learning rate for each model parameter. At this point, a natural question is: which algorithm should one choose?

Unfortunately, there is currently no consensus on this point. Schaul et al. (2014) presented a valuable comparison of a large number of optimization algorithms across a wide range of learning tasks. While the results suggest that the family of algorithms with adaptive learning rates (represented by RMSProp and AdaDelta)

performed fairly robustly, no single best algorithm has emerged.

Currently, the most popular optimization algorithms actively in use include SGD, SGD with momentum, RMSProp, RMSProp with momentum, AdaDelta, and Adam. The choice of which algorithm to use, at this point, seems to depend largely on the user’s familiarity with the algorithm (for ease of hyperparameter tuning).

## 8.6 Approximate Second-Order Methods

In this section we discuss the application of second-order methods to training deep networks. See LeCun et al. (1998a) for an earlier treatment of this subject. For simplicity of exposition, the only objective function we examine is the empirical risk:

$J(\boldsymbol{\theta}) = \mathbb{E}_{\mathbf{x},y\sim\hat{p}_{\text{data}}(\mathbf{x},y)}[L(f(\mathbf{x};\boldsymbol{\theta}),y)] = \frac{1}{m}\sum_{i=1}^{m} L(f(\mathbf{x}^{(i)};\boldsymbol{\theta}),y^{(i)}). \quad (8.25)$

The methods we discuss here extend readily, however, to more general objective functions, such as those that include parameter regularization terms, as discussed in chapter 7.

### 8.6.1 Newton's Method

In section 4.3, we introduced second-order gradient methods. In contrast to first-order methods, second-order methods make use of second derivatives to improve optimization. The most widely used second-order method is Newton’s method. We now describe Newton’s method in more detail, with emphasis on its application to neural network training.

Newton’s method is an optimization scheme based on using a second-order Taylor series expansion to approximate $J(\boldsymbol{\theta})$ near some point $\boldsymbol{\theta}_0$, ignoring derivatives of higher order:

$J(\boldsymbol{\theta}) \approx J(\boldsymbol{\theta}_0) + (\boldsymbol{\theta} - \boldsymbol{\theta}_0)^\top \nabla_{\boldsymbol{\theta}}J(\boldsymbol{\theta}_0) + \frac{1}{2}(\boldsymbol{\theta} - \boldsymbol{\theta}_0)^\top \boldsymbol{H} (\boldsymbol{\theta} - \boldsymbol{\theta}_0), \quad (8.26)$

where $\boldsymbol{H}$ is the Hessian of $J$ with respect to $\boldsymbol{\theta}$ evaluated at $\boldsymbol{\theta}_0$. If we then solve for the critical point of this function, we obtain the Newton parameter update rule:

$\boldsymbol{\theta}^* = \boldsymbol{\theta}_0 - \boldsymbol{H}^{-1} \nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_0). \quad (8.27)$
