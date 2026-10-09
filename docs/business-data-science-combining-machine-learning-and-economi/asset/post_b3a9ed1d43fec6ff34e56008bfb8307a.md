
## 10.3 Stochastic Gradient Descent

these early layers is then processed through a series of classical neural network nodes, as in Equation 10.1. These later network layers work like a traditional nonparametric regression: they expand the output of early layers to approximate arbitrary functional forms in the response of interest. Thus, the DNNs combine restrictive dimension reduction with flexible function approximation. The key is that both components are learned jointly.

![](img/315929ad4bddd26368466d02e06e2385_406_0.png)

FIGURE 10.7: A cartoon of a DNN, taking as input images, structured data $x_1 \ldots x_{big}$, and raw document text.

We’ve covered only a tiny part of the area of deep learning. There is a ton of exciting new material coming out of both industry and academia. For a glimpse of what is happening in the field, browse the latest proceedings of neural information processing systems (NeurIPS), the premier ML conference, at https://NeurIPS.cc. You’ll see quickly the massive breadth of research. One currently hot topic is on uncertainty quantification for deep neural networks. Another is on understanding how imbalance in training data leads to potentially biased predictions. Topics of this type are gaining prominence as DNNs are moving away from academic competitions and into real-world applications. As the field grows and DNN model construction moves from a scientific to an engineering discipline, we’ll see more need for this type of research that tells us when and how much we can trust the DNNs.

To give a complete view of deep learning, we need to describe the one algorithm that is relied upon for training all of the models: stochastic gradient descent. SGD optimization is a twist on gradient descent (GD), the previously dominant method for minimizing any function that you can differentiate. Given a minimization objective $\mathcal{L}(\Omega)$, where $\Omega$ is the full set of model parameters, each iteration of a gradient descent routine updates from current parameters $\Omega_t$ as follows:

$$\Omega_{t+1} = \Omega_{t} - C_{t} \nabla\mathcal{L}|_{\Omega_{t}}.$$
(10.2)

Here, $\nabla\mathcal{L}|_{\Omega_{t}}$ is the gradient of $\mathcal{L}$ evaluated at the current parameters, and $C_{t}$ is a projection matrix that determines the size of the steps taken in the direction implied by $\nabla\mathcal{L}$. We have the subscript $t$ on $C_{t}$ because this projection can be allowed to update during the optimization. For example, Newton's algorithm uses $C_{t}$ equal to the matrix of objective second derivatives, $\nabla^2\mathcal{L}|_{\Omega_{t}}.$

It is often stated that neural networks are trained through “backpropagation,” which is not quite correct. Rather, they are trained through variants of gradient descent. Back-propagation, or backprop for short, is a method for calculating gradients on the parameters of a network. In particular, backprop is just an algorithmic implementation of the chain rule from calculus. In the context of the simple neuron from Equation 10.1, the gradient calculation for a single weight $\omega_{hj}$ is

$$\frac{\partial\mathcal{L}}{\partial\omega_{hj}} = \sum_{i=1}^{n}\frac{\partial\mathcal{L}}{\partial z_{ij}^{h}} \frac{\partial z_{ij}^{h}}{\partial\omega_{hj}} = \sum_{i=1}^{n}\frac{\partial\mathcal{L}}{\partial z_{ij}^{h}} z_{ij}^{h-1}[0<\Sigma_{j}\omega_{nj}^{h-1}] .$
(10.3)

Another application of the chain rule can be used to expand $\partial\mathcal{L}/\partial z_{ij}^{h}$ as $\partial\mathcal{L}/\partial z_{ij}^{h+1} \times \partial z_{ij}^{h+1}/\partial z_{ij}^{h}$, and so on, until you have written the full gradient as a product of layer-specific operations. The directed structure of the network lets you efficiently calculate all of the gradients by working backward layer by layer, from the response down to the inputs. This recursive application of the chain rule and the associated computation recipes make up the general backprop algorithm.

In statistical estimation and ML model-training, $\mathcal{L}$ typically involves a loss function that sums across data observations. For example, assuming an l2 (ridge) regularization penalty on the parameters, the minimization objective corresponding to regularized likelihood maximization over $n$ independent observations $z_i$ (e.g., $z_i = [x_i, y_i]$ for regression) can be written as

$$\mathcal{L}(\Omega) \equiv \mathcal{L}(\Omega;\{z_i\}_{i=1}^n) = \sum_{i=1}^n \big[ -\log \mathrm{p}(z_i \mid \Omega) + \lambda \| \Omega \|_2^2 \big]. \tag{10.4}$$

Here, $\| \Omega \|_2^2$ is the sum of all squared parameters in $\Omega$. More generally, $\mathcal{L}(\Omega;\{z_i\}_{i=1}^n)$ can consist of any loss function that involves summation over observations. For example, to model predictive uncertainty, we often work with quantile loss. Define $\tau_q(x; \Omega)$ as the *quantile function*, parametrized by $\Omega$, that maps from covariates $x$ to the $q$th quantile of the response $y$:

$$\mathrm{p}\left(y < \tau_q(\boldsymbol{x}; \Omega) \mid \boldsymbol{x}\right) = q. \tag{10.5}$$

You fit $\tau_q$ to minimize the regularized quantile loss function (again assuming a ridge penalty):

$$\mathcal{L}(\Omega;\{z_i\}_{i=1}^n) = \sum_{i=1}^n \left[\big(y_i - \tau_q(\boldsymbol{x}_i; \Omega)\big) \left(q - \mathbb{1}_{[y_i < \tau_q(x_i; \Omega)]}\right) + \lambda \| \Omega \|_2^2 \right]. \tag{10.6}$$

The common “sum of squared errors” criterion, possibly regularized, is another loss function that fits this pattern of summation over observations.

In all of these cases, the gradient calculations required for the updates in Equation 10.2 involve sums over all $n$ observations. That is, each calculation of $\nabla \mathcal{L}$ requires an order of $n$ calculations. For example, in a ridge-penalized linear regression where $\Omega = \beta$, a vector of regression coefficients, the $j$th gradient component is

$$\frac{\partial \mathcal{L}}{\partial \beta_j} = \sum_{i=1}^n \big[ (y_i - \boldsymbol{x}_i^t \beta) x_{ij} + \lambda \beta_j \big]. \tag{10.7}$$

The problem for massive datasets is that when $n$ is really big, these calculations become prohibitively expensive. The issue is aggravated when, as it is for DNNs, $\Omega$ is high dimensional and there are complex calculations required in each gradient summand. GD is the best optimization tool that we have, but it becomes computationally infeasible for massive datasets.

The solution is to replace the actual gradients in Equation 10.2 with estimates of those gradients based upon a subset of the data. This is the SGD algorithm. It has a long history, dating back to the Robbins-Munro algorithm proposed by a couple of statisticians in 1951. In the most common versions of SGD, the full-sample gradient is simply replaced by the gradient on a smaller subsample. Instead of calculating gradients on the full-sample loss, $\mathcal{L}(\mathbf{\Omega};\{z_i\}_{i=1}^n)$, we descend according to subsample calculations,

\begin{equation} \mathbf{\Omega}_{t+1} = \mathbf{\Omega}_t - C_t \nabla \mathcal{L}(\mathbf{\Omega}; \{z_{i_b}\}_{b=1}^B)\big|_{\mathbf{\Omega}_t} \tag{10.8}\end{equation}

Here, $\{z_{i_b}\}_{b=1}^B$ is a *mini-batch* of observations with $B \ll n$. The key mathematical result behind SGD is that, so long as the sequence of $C_t$ matrices satisfy some basic requirements, the SGD algorithm will converge to a local optimum whenever $\nabla \mathcal{L}(\mathbf{\Omega}; \{z_{i_b}\}_{b=1}^B)$ is an *unbiased* estimate of the full sample gradient. That is, SGD convergence relies upon the following:

\begin{equation} \mathbb{E}\left[\frac{1}{B}\nabla \mathcal{L}\left(\mathbf{\Omega}; \{z_{i_b}\}_{b=1}^B\right)\right] = \mathbb{E}\left[\frac{1}{n}\nabla \mathcal{L}(\mathbf{\Omega}; \{z_i\}_{i=1}^n)\right] = \mathbb{E}\nabla \mathcal{L}(\mathbf{\Omega}; z). \tag{10.9}\end{equation}

Here, the last term refers to *the population* expected gradient—that is, the average gradient for observation $z$ drawn from the true data-generating process.

To understand why SGD is so preferable to GD for machine learning, it helps to discuss how computer scientists think about the *constraints* on estimation. Statisticians and economists tend to view sample size (i.e., lack of data) as the binding constraint on their estimators. In contrast, in many ML applications the data is practically unlimited and continues to grow during system deployment. Despite this abundance, there is a fixed computational budget (or the need to update in near-real-time for streaming data), such that you can execute only a limited number of operations when crunching through the data. Thus, in ML, the binding constraint is the amount of computation rather than the amount of data.

SGD trades faster updates for a slower per-update convergence rate. As explained in a 2008 paper by Bousquet and Bousquet, this trade is worthwhile when the faster updates allows you to expose your model to more data than would otherwise be possible. To see this, note that the mini-batch gradient $B^{-1}\nabla \mathcal{L}(\mathbf{\Omega};\{z_{i_b}\}_{b=1}^B)$ has a much higher variance than the full-
