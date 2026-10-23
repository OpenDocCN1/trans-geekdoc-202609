where **M**_t is a **preconditioning matrix**, or simply the **preconditioner**, typically chosen to be positive-definite. Unfortunately the noise in the gradient estimates make it difficult to reliably estimate the Hessian, which makes it difficult to use the methods from Sec. 5.3. In addition, it is expensive to solve for the update direction with a full preconditioning matrix. Therefore most practitioners use a diagonal preconditioner **M**_t. Such preconditioners do not necessarily use second-order information, but often result in speedups compared to vanilla SGD.

# 5.4.6.1 AdaGrad

The **AdaGrad** (short for “adaptive gradient”) method of [DHS11] was originally designed for optimizing convex objectives where many elements of the gradient vector are zero; these might correspond to features that are rarely present in the input, such as rare words. The update has the following form

$\theta_{t+1,d} = \theta_{t,d} - \eta_t \frac{1}{\sqrt{s_{t,d}+\epsilon}} g_{t,d} \tag{5.70}$

where

$s_{t,d} = \sum_{\tau=1}^{t} g_{\tau,d}^2 \tag{5.71}$

is the sum of the squared gradients and $\epsilon > 0$ is a small term to avoid dividing by zero. Equivalently we can write the update in vector form as follows:

$\Delta \theta_t = -\eta_t \frac{1}{\sqrt{\mathbf{s}_t + \epsilon}} \mathbf{g}_t \tag{5.72}$

where the square root and division is performed elementwise. Viewed as preconditioned SGD, this is equivalent to taking $\mathbf{M}_t = \text{diag}(\mathbf{s}_t + \mathbf{\epsilon})^{1/2}$. This is an example of an **adaptive learning rate**; the overall stepsize $\eta_t$ still needs to be chosen, but the results are less sensitive to it compared to vanilla GD. In particular, we usually fix $\eta_t = \eta_0$.

# 5.4.6.2 RMSProp and AdaDelta

A defining feature of AdaGrad is that the term in the denominator gets larger over time, so the effective learning rate drops. While it is necessary to ensure convergence, it might hurt performance as the denominator gets large too fast.

An alternative is to use an exponentially weighted moving average (EWMA, Sec. 4.6.2) of the past squared gradients, rather than their sum:

$s_{t+1,d} = \beta s_{t,d} + (1 - \beta) g_{t,d}^2 \tag{5.73}$

In practice we usually use $\beta \sim 0.9$, which puts more weight on recent examples. In this case,

$\sqrt{s_{t,d}} \approx \text{RMS}(\mathbf{g}_{1:t,d}) = \sqrt{\frac{1}{t} \sum_{\tau=1}^{t} g_{\tau,d}^2} \tag{5.74}$