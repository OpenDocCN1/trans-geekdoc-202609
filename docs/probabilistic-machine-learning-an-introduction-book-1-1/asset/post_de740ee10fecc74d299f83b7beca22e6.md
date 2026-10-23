
## 10.6 Bayesian logistic regression

So far we have focused on point estimates of the parameters, either the MLE or the MAP estimate. However, in some cases we want to compute the posterior, $p(\mathbf{w}|\mathcal{D})$, in order to capture our uncertainty. This can be particularly useful in settings where we have little data, and where choosing the wrong decision may be costly; this arises in online advertising, for example (see Sec. 8.3).

Unlike with linear regression, it is not possible to compute the posterior exactly for a logistic regression model. A wide range of approximate algorithms can be used, as we briefly discuss in Sec. 7.7. In this section, we give a few examples of different methods. But before we discuss how to approximate the posterior, we discuss how to use the posterior to make predictions.

### 10.6.1 Approximating the posterior predictive

The posterior $p(\mathbf{w}|\mathcal{D})$ tells us everything we know about the parameters of the model given the data. However, in machine learning applications, the main task of interest is usually to predict an output $y$ given an input $\mathbf{x}$, rather than to try to understand the parameters of our model. Thus we need to compute the posterior predictive distribution

$$
p(y|\mathbf{x}, \mathcal{D}) = \int p(y|\mathbf{x}, \mathbf{w}) p(\mathbf{w}|\mathcal{D}) \, d\mathbf{w} \tag{10.112}
$$

As we discussed in Sec. 2.4.2, a simple approach to this is to first compute a point estimate $\hat{\mathbf{w}}$ of the parameters, such as the MLE or MAP estimate, and then to ignore all posterior uncertainty, by assuming $p(\mathbf{w}|\mathcal{D}) = \delta(\mathbf{w} - \hat{\mathbf{w}})$. In this case, the above integral reduces to the following plug-in approximation:

$$
p(y|\mathbf{x}, \mathcal{D}) \approx \int p(y|\mathbf{x}, \mathbf{w}) \delta(\mathbf{w} - \hat{\mathbf{w}}) \, d\mathbf{w} = p(y|\mathbf{x}, \hat{\mathbf{w}}) \tag{10.113}
$$

However, if we want to compute uncertainty in our predictions, we should use a non-degenerate posterior. It is common to use a Gaussian posterior, as we will see. But we still need to approximate the integral in Eq. (10.112). We discuss some approaches to this below.

#### 10.6.1.1 Monte Carlo approximation

The simplest approach is to use a Monte Carlo approximation to the integral. This means we draw $S$ samples from the posterior, $\mathbf{w}_s \sim p(\mathbf{w}|\mathcal{D})$, and then compute

$$
p(y=1|\mathbf{x}, \mathcal{D}) \approx \frac{1}{S} \sum_{s=1}^{S} \sigma(\mathbf{w}_s^\top \mathbf{x}) \tag{10.114}
$$

#### 10.6.1.2 Probit approximation

Although the Monte Carlo approximation is simple, it can be slow, since we need to draw $S$ samples at test time for each input $\mathbf{x}$. Fortunately, if $p(\mathbf{w}|\mathcal{D}) = \mathcal{N}(\mathbf{w}|\boldsymbol{\mu}, \boldsymbol{\Sigma})$, there is a simple yet accurate deterministic approximation, first suggested in [SL90]. To explain this approximation, we follow the presentation of [Bis06, p219]. The key observation is that the sigmoid function $\sigma(a)$ is similar in shape to the Gaussian cdf (see Sec. 3.3.1) $\Phi(a)$. In particular we have $\sigma(a) \approx \Phi(\lambda a)$, where $\lambda^2 = \pi/8$ ensures the two functions have the same slope at the origin. This is useful since we can integrate a Gaussian cdf wrt a Gaussian pdf exactly:

$$
\int \Phi(\lambda a) \mathcal{N}(a|m, v) \, da = \Phi\left(\frac{m}{(\lambda^{-2}+v)^{1/2}}\right) = \Phi\left(\frac{\lambda m}{(1+\lambda^2v)^{1/2}}\right) \approx \sigma(\kappa(v)m) \tag{10.115}
$$

where we have defined

$$
\kappa(v) \triangleq (1+\pi v/8)^{-1/2} \tag{10.116}
$$

Thus if we define $a = \mathbf{x}^{\mathsf T}\mathbf{w}$, we have

$$
p(y=1|\mathbf{x}, \mathcal{D}) \approx \sigma(\kappa(v)m) \tag{10.117}
$$

$$
m = \mathbb{E}[a] = \mathbf{x}^{\mathsf T}\boldsymbol{\mu} \tag{10.118}
$$

$$
v = \mathbb{V}[a] = \mathbb{V}[\mathbf{x}^{\mathsf T}\mathbf{w}] = \mathbf{x}^{\mathsf T}\boldsymbol{\Sigma}\mathbf{x} \tag{10.119}
$$

where we used Eq. (D.68) in the last line. Since $\Phi^{-1}$ is known as the probit function, we will call this the **probit approximation**.

Using Eq. (10.117) results in predictions that are less extreme (in terms of their confidence) than the plug-in estimate. To see this, note that $0 < \kappa(v) < 1$ and hence $\kappa(v)m < m$, so $\sigma(\kappa(v)m)$ is closer to 0.5 than $\sigma(m)$ is. However, the decision boundary itself will not be affected. To see this, note that the decision boundary is the set of points $\mathbf{x}$ for which $p(y=1|\mathbf{x}, \mathcal{D}) = 0.5$. This implies $\kappa(v)m = 0$, which implies $m = \bar{\mathbf{w}}^{\mathsf T}\mathbf{x} = 0$; but this is the same as the decision boundary from the plug-in estimate. Thus “being Bayesian” doesn’t change the misclassification rate (in this case), but it does change the confidence estimates of the model, which can be important, as we illustrate in Sec. 10.6.2.

In the multiclass case, [Nab01, p353] suggests the following extension of the Spiegelhalter method of Sec. 10.6.1.2:

$$
p(y=c|\mathbf{x}, \mathcal{D}) \approx \frac{\exp(\kappa(v_c)m_c)}{\sum_{c'}\exp(\kappa(v_{c'})m_{c'})} \tag{10.120}
$$

$$
m_c = \mathbf{m}_c^{\mathsf T}\mathbf{x} \tag{10.121}
$$

$$
v_c = \mathbf{x}^{\mathsf T}\mathbf{V}_{c,c}\mathbf{x} \tag{10.122}
$$

where $\kappa$ is defined in Eq. (10.116). Unlike the binary case, taking into account posterior covariance gives different predictions than the plug-in approach (see Exercise 3.10.3 of [RW06]).

### 10.6.2 Laplace approximation

As we discuss in Sec. 7.7.2, the Laplace approximation approximates the posterior using a Gaussian. The mean of the Gaussian is equal to the MAP estimate $\hat{\mathbf{w}}$, and the covariance is equal to the inverse Hessian $\mathbf{H}$ computed at the MAP estimate, i.e., $p(\mathbf{w}|\mathcal{D}) \approx \mathcal{N}(\mathbf{w}|\hat{\mathbf{w}},\mathbf{H}^{-1})$. We can find the mode using a standard optimization method (see Sec. 10.2.7), and we can use the results from Sec. 10.2.3.4 to compute the Hessian at the mode.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_0.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_1.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_2.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_3.png)

Figure 10.14: (a) Illustration of the data. (b) Log-likelihood for a logistic regression model. The line is drawn from the origin in the direction of the MLE (which is at infinity). The numbers correspond to 4 points in parameter space, corresponding to the lines in (a). (c) Unnormalized log posterior (assuming vague spherical prior). (d) Laplace approximation to posterior. Adapted from a figure by Mark Girolami. Generated by logregLaplaceGirolamiDemo.m.

As an example, consider the data illustrated in Fig. 10.14(a). There are many parameter settings that correspond to lines that perfectly separate the training data; we show 4 example lines. The likelihood surface is shown in Fig. 10.14(b). The diagonal line connects the origin to the point in the grid with maximum likelihood, $\hat{\mathbf{w}}_{mle} = (8.0, 3.4)$. (The unconstrained MLE has $\|\mathbf{w}\| = \infty$, as we discussed in Sec. 10.2.7; this point can be obtained by following the diagonal line infinitely far to the right.)

For each decision boundary in Fig. 10.14(a), we plot the corresponding parameter vector in Fig. 10.14(b). These parameter values are $\mathbf{w}_1 = (3, 1)$, $\mathbf{w}_2 = (4, 2)$, $\mathbf{w}_3 = (5, 3)$, and $\mathbf{w}_4 = (7, 3)$. These points all approximately satisfy $\mathbf{w}_i(1)/\mathbf{w}_i(2) \approx \hat{\mathbf{w}}_{mle}(1)/\hat{\mathbf{w}}_{mle}(2)$, and hence are close to the orientation of the maximum likelihood decision boundary. The points are ordered by increasing weight norm (3.16, 4.47, 5.83, and 7.62).

To ensure a unique solution, we use a (spherical) Gaussian prior centered at the origin, $\mathcal{N}(\mathbf{w}|0, \sigma^2 \mathbf{I})$. The value of $\sigma^2$ controls the strength of the prior. If we set $\sigma^2 = \infty$, we force the MAP estimate to be $\mathbf{w} = 0$; this will result in maximally uncertain predictions, since all points $\mathbf{x}$ will produce a predictive distribution of the form $p(y=1|\mathbf{x}) = 0.5$. If we set $\sigma^2 = 0$, the MAP estimate becomes the MLE, resulting in minimally uncertain predictions. (In particular, all positively labeled points will have $p(y = 1|\mathbf{x}) = 1.0$, and all negatively labeled points will have $p(y = 1|\mathbf{x}) = 0.0$, since the data is separable.) As a compromise (to make a nice illustration), we pick the value $\sigma^2 = 100$.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_0.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_1.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_2.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_3.png)

Figure 10.15: Posterior predictive distribution for a logistic regression model in 2d. Top left: contours of $p(y = 1|\mathbf{x}, \mathbf{w}_{map})$. Top right: samples from the posterior predictive distribution. Bottom left: Averaging over these samples. Bottom right: moderated output (probit approximation). Adapted from a figure by Mark Girolami. Generated by logregLaplaceGirolamiDemo.m.

Multiplying this prior by the likelihood results in the unnormalized posterior shown in Fig. 10.14(c). The MAP estimate is shown by the blue dot. The Laplace approximation to this posterior is shown in Fig. 10.14(d). We see that it gets the mode correct (by construction), but the shape of the posterior is somewhat distorted. (The southwest-northeast orientation captures uncertainty about the magnitude of $\mathbf{w}$, and the southeast-northwest orientation captures uncertainty about the orientation of the decision boundary.)

In Fig. 10.15, we show contours of the posterior predictive distribution. Fig. 10.15(a) shows the plugin approximation using the MAP estimate. We see that there is no uncertainty about the decision boundary, even though we are generating probabilistic predictions over the labels. Fig. 10.15(b) shows what happens when we plug in samples from the Gaussian posterior. Now we see that there is considerable uncertainty about the orientation of the “best” decision boundary. Fig. 10.15(c) shows the average of these samples. By averaging over multiple predictions, we see that the uncertainty in the decision boundary “splays out” as we move further from the training data. Fig. 10.15(d) shows that the probit approximation gives very similar results to the Monte Carlo approximation.
