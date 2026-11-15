
of predicting label $y_0$:

$\ell_{\text{CE}}(f(\boldsymbol{x}_0), y_0) := -\log P(y_0 \mid \boldsymbol{x}_0), \quad \text{where } P(y_0 \mid \boldsymbol{x}_0) := \frac{e^{f_{y_0}(\boldsymbol{x}_0)}}{\sum_{j=1}^K e^{f_j(\boldsymbol{x}_0)}}. \quad (2.2)$

Here \(f_j(\boldsymbol{x}_0)\) is the class prediction score of class \(j\), and the prediction probability of class \(j\) is computed using a softmax operation for normalization. We can define the \(g(\boldsymbol{x})\) for adversarial attacks by slightly changing this loss function. For untargeted attack, the goal of “making model predicts another label” can be formulated as “minimizing the probability of predicting class \(y_0\)”. This can be naturally achieved by setting

Untargeted CE loss: \(g(\boldsymbol{x}) := \ell_{\text{CE}}(f(\boldsymbol{x}), y_0). \quad (2.3)\)

Since here we want to maximize \(g(\boldsymbol{x})\) instead of minimizing it, the perturbation will try to maximally increase the cross-entropy loss to achieve the worst prediction.

For targeted attack, we aim to maximize the predicted probability of the target class \(t\). The attack successfulness can thus be defined as

Targeted CE loss: \(g(\boldsymbol{x}) := -\ell_{\text{CE}}(f(\boldsymbol{x}), t), \quad (2.4)\)

which is the log-likelihood of the target class probability.

The constraint set \(B(\boldsymbol{x}_0)\) is usually defined as a small region around \(\boldsymbol{x}_0\). If the \(\ell_p\) norm is used for measuring distance, then we can define

\(B(\boldsymbol{x}_0) = \{\boldsymbol{x} : \|\boldsymbol{x} - \boldsymbol{x}_0\|_p \le \epsilon\},\)

where \(\epsilon\) is a predefined small constant, known as the perturbation threshold or budget. For example, on the CIFAR-10 image classification dataset (which is a standard benchmarking dataset for evaluating adversarial attacks), the \(\epsilon\) is often set as 8/255 (for \(\ell_\infty\) norm) when each pixel is in the range of [0, 255]. Note that for computer vision applications, we usually need to enforce an additional elementwise lower and upper bounds to ensure that the adversarial example \(\boldsymbol{x}\) is still a valid image, so the constraint set will become the intersection of \(\ell_p\) ball and \(\boldsymbol{x} \in [0, 255]^d\). For simplicity, we will omit this constraint in our derivations since they can often easily done by a simple elementwise projection to the feasible data space.

Once we formulate an adversarial attack as a constraint optimization problem, any existing optimization algorithm can be used for solving this problem to generate an adversarial example. For example, a projected gradient descent method can be applied: at each iteration, we update the current solution \(\boldsymbol{x}_t\) by

\(\boldsymbol{x}_{t+1} \leftarrow \Pi(\boldsymbol{x}_t + \alpha \nabla g(\boldsymbol{x})), \quad (2.5)\)

where \(\alpha\) is the learning rate of gradient descent, and \(\Pi(\cdot)\) projects the vector to \(B(\boldsymbol{x}_0)\). However, in practice, we may find that this plain projected gradient descent update is not very effective in solving the attack problem, especially when we use \(\ell_\infty\) norm constraint, which is the most common choice in the computer vision community. In the \(\ell_\infty\) norm case the constraint set \(B(\boldsymbol{x})\) is a hyperrectangle (high-dimensional rectangle), and the successful attacks are often (but not always) lying on the corner of this rectangle, i.e., most of the elements of a successful adversarial example \(\boldsymbol{x}_i^*\) should be close to \((\boldsymbol{x}_0)_i \pm \epsilon\). If the plain projected gradient descent update (2.5) is used, then some coordinates will require many iterations to reach \(\pm \epsilon\), leading to slow convergence. Therefore it is a common practice to use the *steepest descent algorithm* for conducting an attack, as detailed below.

## 2.3 Steepest descent, FGSM and PGD attack

In this section, we will first consider the \(\ell_\infty\) norm attack (i.e., \(B(\boldsymbol{x}) = \{\boldsymbol{x} : \|\boldsymbol{x} - \boldsymbol{x}_0\|_\infty \le \epsilon\}\)). Let us consider the problem of conducting only *one update* to approximately solve (2.1). The idea of steepest descent update is forming a linear approximation of the objective function and finding the best update to maximize this linear approximation. Concretely, we can conduct the first-order Taylor expansion of \(g(\boldsymbol{x})\) on the initial solution \(\boldsymbol{x}_0\) (assuming that we start from the original natural example):

\(g(\boldsymbol{x}) \approx g(\boldsymbol{x}_0) + \nabla g(\boldsymbol{x}_0)^T (\boldsymbol{x} - \boldsymbol{x}_0).\)

We can then solve the following constraint optimization problem, which is an approximation of (2.1):

\(\underset{\boldsymbol{x}}{\text{argmax}} \nabla g(\boldsymbol{x}_0)^T (\boldsymbol{x} - \boldsymbol{x}_0) \quad \text{s.t.} \quad \boldsymbol{x} \in \|\boldsymbol{x} - \boldsymbol{x}_0\|_\infty \le \epsilon. \quad (2.6)\)

Note that we drop the \(g(\boldsymbol{x}_0)\) term in the Taylor expansion since it is a constant irrelevant to \(\boldsymbol{x}\). Now we can easily see that (2.6) has a closed-form solution

\(\boldsymbol{x}_1 = \boldsymbol{x}_0 + \epsilon \text{sign}(\nabla g(\boldsymbol{x}_0)). \quad (2.7)\)

Here $\text{sign}(\cdot) \in \{+1, -1\}$ denotes elementwise sign values. This is the one-step steepest descent update, and surprisingly, it has been found that even this simple step is very effective for constructing adversarial examples. This rule in (2.7) is known as the fast gradient sign method (FGSM), first proposed by Goodfellow et al. (2015).

A straightforward extension of FGSM is to run steepest descent for multiple iterations. In this case, we need to choose a step size $\alpha$ for each iteration, that is, from the current iteration \(\boldsymbol{x}_t\) we allow the update in \(\{\boldsymbol{x}_{t+1} : \|\boldsymbol{x}_{t+1} - \boldsymbol{x}_t\|_\infty \le \alpha\}\) and minimize the linear approximation within this region. This will lead to the same subproblem with (2.6) with $\epsilon$ being replaced by $\alpha$, so the optimal update is \(\boldsymbol{x}_t + \alpha \text{sign}(\nabla g(\boldsymbol{x}_t))\). Another issue when running multiple iterations is that the variables may go outside the constraint set \(B(\boldsymbol{x}_0)\) after few iterations. Therefore we have to further project the update back to the constraint set, leading to the following iterative steepest descent update:

\(\boldsymbol{x}_{t+1} = \Pi(\boldsymbol{x}_t + \alpha \text{sign}(\nabla g(\boldsymbol{x}_t))) \quad \forall t=0, \dots, T-1.\) (2.8)

If we run this update for $T$ iterations, then the final solution $\boldsymbol{x}_T$ is supposed to be better than FGSM. This is called the iterative FGSM (I-FGSM) attack by Kurakin et al. (2016), also called the (basic) PGD attack by Madry et al. (2018). This PGD attack is one of the most effective first-order (gradient-based) algorithms for constructing adversarial examples. Furthermore, it is very easy to incorporate in the adversarial training algorithm to train a robust model, which will be discussed in Chapter 11.

One issue for running PGD attack is to choose a suitable step size $\alpha$. If $\alpha < \frac{\epsilon}{T}$, then the solution $\boldsymbol{x}_T$ will not reach the boundary of $B(\boldsymbol{x}_0)$, and so the attack will not be very effective. In practice, $\alpha$ is usually set as a number slightly larger than $\frac{\epsilon}{T}$. Its value can also vary per attack iteration. Also, one can randomly initialize $\boldsymbol{x}_0$ inside $B(\boldsymbol{x}_0)$ and possibly repeat this process multiple times for finding adversarial examples.

## 2.4 Transforming to an unconstrained optimization problem

Instead of solving the constrained optimization problem in (2.1), we can actually transform it into an unconstrained optimization problem and apply standard gradient descent or other first-order methods (without projection) to solve the problem. This is done by solving the following "soft-constrained" form, where we remove the constraint and add a penalty in
