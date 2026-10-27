
### EX 3.7.
Assuming that the probability of heads is given by $r$, we observe $y$ heads in $N$ tosses, and $r$ has a Beta prior with parameters $\alpha$ and $\beta$, the posterior density is a Beta density with parameters $\delta=\alpha+y$ and $\gamma=\beta+N-y$. The marginal likelihood is given by:

$$p(y_N\mid\alpha,\beta)=\binom{N}{y_N}\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}\frac{\Gamma(\alpha+y_N)\Gamma(\beta+N-y_N)}{\Gamma(\alpha+\beta+N)}.$$

The probability of winning is given by:

$$\mathbf{E}_{p(r\mid y_N)}\{P(Y_{\mathrm{new}}\leq 6\mid r)\}=1-\sum_{y_{\mathrm{new}}=7}^{y_{\mathrm{new}}=10}\mathbf{E}_{p(r\mid y_N)}\{P(Y_{\mathrm{new}}=y_{\mathrm{new}}\mid r)\}$$

where

$$\mathbf{E}_{p(r\mid y_N)}\{P(Y_{\mathrm{new}}=y_{\mathrm{new}}\mid r)\}=\binom{N_{\mathrm{new}}}{y_{\mathrm{new}}}\frac{\Gamma(\delta+\gamma)}{\Gamma(\delta)\Gamma(\gamma)}\frac{\Gamma(\delta+y_{\mathrm{new}})\Gamma(\gamma+N_{\mathrm{new}}-y_{\mathrm{new}})}{\Gamma(\delta+\gamma+N_{\mathrm{new}})}$$

From the question, $y_N=9$, $N=20$.

Scenario 1: $\alpha=\beta=1$. The posterior density has parameters $\delta=\alpha+y_N=10$, $\gamma=\beta+N-y_N=1+20-9=12$. The marginal likelihood comes out as: 0.0476. The probability of winning as: 0.84812.

Scenario 2: $\alpha=\beta=50$. The posterior density has parameters $\delta=\alpha+y_N=59$, $\gamma=\beta+N-y_N=50+20-9=61$. The marginal likelihood comes out as: 0.1486. The probability of winning as: 0.83162.

Scenario 3: $\alpha=5,\beta=1$. The posterior density has parameters $\delta=\alpha+y_N=14$, $\gamma=\beta+N-y_N=1+20-9=12$. The marginal likelihood comes out as: 0.0135. The probability of winning as: 0.7211.

### EX 3.8.
Code below (`scenarios.m`):

```matlab
clear all;
close all;
% Define an array to hold the three scenarios
% Each row is alpha,beta for one scenario
hypers = [1,1;50,50;5,1];

scenario = 1; % Change this to look at different ones

% Generate the 100 tosses
N = 100;
toss = rand(N,1)<0.7;
Nheads = sum(toss);
Ntails = N - Nheads;

% Compute the posterior
alpha = hypers(scenario,1);
beta = hypers(scenario,2);
postalpha = alpha + Nheads;
postbeta = beta + Ntails;
```

![](img/4c6eb9ed1cdfcf169bfa1a2b6a72e99a_23_0.png)

### EX 3.11.
Code below (marglike.m):

```matlab
clear all;close all;
% Generate the data
N = 100;
x = rand(N,1)*10^-5;
x = sort(x);
ss = 100;
f = 5*x.^3 - x.^2 + x;
t = f + randn(size(f))*sqrt(ss);

% Choose sigma_0^2
ss0 = 0.3; % Try increasing this

% Loop over model orders
order = [1:7];
X = repmat(1,size(x));
for i = 1:length(order)
    mu0 = zeros(order(i)+1,1);
    S0 = ss0*eye(order(i)+1);
    X = [X x.^order(i)];

    mlmean = X*mu0;
    mlcov = ss*eye(N) + X*S0*X';

    logml(i) = -(N/2)*log(2*pi) - (N/2)*log(det(mlcov)) - ...
        0.5*(t-mlmean)'*inv(mlcov)*(t-mlmean);

% Note that the non log value may be numerically instable.
ml(i) = exp(logml(i));
end
```

### EX 3.12.
Assuming **w** is fixed, and the following inverse gamma prior on $\sigma^2$:

$$p(\sigma^2\mid\alpha,\beta)=\frac{\beta^\alpha}{\Gamma(\alpha)}(\sigma^2)^{-\alpha-1}\exp\left\{-\frac{\beta}{\sigma^2}\right\}.$$

The likelihood is the standard Gaussian likelihood:

$$p(\mathbf{t}\mid\mathbf{w},\mathbf{X},\sigma^2)=\frac{1}{(2\pi)^{N/2}(\sigma^2)^{N/2}}\exp\left\{-\frac{1}{2\sigma^2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw})\right\}.$$

The posterior density over $\sigma^2$ is therefore proportional to the product of these two densities. Collecting similar terms:

$$p(\sigma^2\mid\mathbf{w},\mathbf{X},\alpha,\beta)\propto(\sigma^2)^{-\alpha-N/2-1}\exp\left\{-\frac{1}{\sigma^2}\left(\beta+\frac{1}{2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw})\right)\right\}.$$

This is another inverse gamma with parameters $\alpha^*$ and $\beta^*$ given by:

$$\alpha^*=\alpha+\frac{N}{2}$$
$$\beta^*=\beta+\frac{1}{2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw}).$$

This will be the mean of the Gaussian approximation and we can already see that it is equal to $\mu$, the posterior mean.

To find the covariance matrix, we take second derivatives of $g$:

$$\frac{\partial^2 g}{\partial \mathbf{w}\partial \mathbf{w}^\mathsf{T}} = -(\mathbf{I}_D + \mathbf{X}^\mathsf{T}\mathbf{X})$$

The covariance of the Laplace approximation is therefore:

$$(\mathbf{I} + \mathbf{X}^\mathsf{T}\mathbf{X})^{-1}.$$

This is identical to the posterior covariance matrix thus confirming that the approximation is, in this case, exact.

### EX 4.2.
We are interested in the Laplace approximation to the posterior $p(r|N, y, \alpha, \beta)$. The first step is to find the MAP value of $r$. The log posterior is (removing constants):

$$g = (\alpha - 1) \log r + (\beta - 1) \log(1 - r) + y \log r + (N - y) \log(1 - r).$$

Taking partial derivatives with respect to $r$ leaves:

$$\frac{\partial g}{\partial r} = \frac{\alpha + y - 1}{r} - \frac{\beta + N - y - 1}{1 - r}.$$

Re-arranging this expression gives the MAP solution for $r$:

$$\hat{r} = \frac{\alpha + y - 1}{\alpha + \beta + N - 2}.$$

This will be the mean of the Gaussian approximation. The variance is given by:

$$\sigma^2 = - \left( \frac{\partial^2 g}{\partial r^2} \right)^{-1} = - \left( - \frac{\alpha + y - 1}{r^2} - \frac{\beta + N - y - 1}{(1 - r)^2} \right)^{-1}$$

### EX 4.3.
The plot below shows an example where $\alpha = \beta = 2$, $y = 2$, and $N = 10$.

![](img/4c6eb9ed1cdfcf169bfa1a2b6a72e99a_27_0.png)

### EX 4.4.
This is a nice example to illustrate the power of sampling. Imagine sampling pairs of values from uniform distributions between -0.5 and 0.5. These values would be uniformly distributed in the square shown below:

The probability that one of these points lies within the circle must be equal to the ratio of the area of the circle to the area of the square. We can obtain an empirical estimate of this value by say generating N pairs (i.e. points) and then computing the number of pairs that lie within the circle (s). Then:

$$\frac{s}{N} \approx \frac{\pi r^{2}}{1 \times 1} = 0.5^{2}\pi.$$

Re-arranging this expression will give an approximate value of π:

$$\pi \approx \frac{s}{0.5^{2}N}.$$

For example, one random sample of 100 points yields a value of:

$$\pi \approx 3.240.$$

As we would expect, this approximation will, on average, get better as we take more samples. An example after 10000 is:

$$\pi \approx 3.129.$$

### EX 4.5.
Re-arrange as follows:

$$P(T_{\text{new}}=1|\mathbf{x}_{\text{new}},\widehat{\mathbf{w}}) = \frac{1}{1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})}$$
$$0.5 = \frac{1}{2}=\frac{1}{1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})}$$
$$2 = 1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})$$
$$1 = \exp(0)=\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})$$

therefore $\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}}=0.$

### EX 4.6.
Assuming a Gaussian prior:

$$p(\mathbf{w}) = \mathcal{N}(\mathbf{0},\mathbf{I}_{D}),$$

and:

$$v_{n}=\exp\{\mathbf{w}^{\mathsf{T}}\mathbf{x}_{n}\}$$

the log posterior is proportional to:

$$g = -\frac{1}{2}\mathbf{w}^{\mathsf{T}}\mathbf{w} + \sum_{n}(t_{n}\log v_{n} - v_{n}).$$

The gradient is obtained by taking partial derivatives with respect to w:

$$\frac{\partial g}{\partial \mathbf{w}} = -\mathbf{w} + \sum_{n}\frac{t_{n}}{v_{n}}\frac{\partial v_{n}}{\partial \mathbf{w}} - \frac{\partial v_{n}}{\partial \mathbf{w}}.$$

Now,

$$\frac{\partial v_n}{\partial \mathbf{w}}=\mathbf{x}_n v_n$$

and therefore:

$$\frac{\partial g}{\partial \mathbf{w}}=-\mathbf{w}+\sum_n\mathbf{x}_n(t_n-v_n).$$

The Hessian is obtained by differentiating a second time. You might find it worthwhile to work out each element of the matrix individually for (say) $D=2$ if this step appears difficult:

$$\frac{\partial^2 g}{\partial\mathbf{w}\partial\mathbf{w}^{\mathsf T}}=-\mathbf{I}-\sum_n v_n\mathbf{x}_n\mathbf{x}_n^{\mathsf T}$$

Given some initial value of $\mathbf{w}$, the optimisation scheme repeatedly updates $\hat{\mathbf{w}}$ as follows until it converges to a maximum:

$$\mathbf{w}\leftarrow\mathbf{w}-\left(-\mathbf{I}-\sum_n v_n\mathbf{x}_n\mathbf{x}_n^{\mathsf T}\right)^{-1}\left(-\mathbf{w}+\sum_n\mathbf{x}_n(t_n-v_n)\right)$$

### EX 4.7.
Given the result of the previous exercise, this is straightforward. The Laplace approximation is a Gaussian with mean $\boldsymbol{\mu}$ and covariance $\boldsymbol{\Sigma}$ where $\boldsymbol{\mu}=\hat{\mathbf{w}}$, the maximum obtained using the Newton-Raphson scheme derived in the previous exercise and the covariance is:

$$\boldsymbol{\Sigma}=-\left(-\mathbf{I}-\sum_n\hat{v}_n\mathbf{x}_n\mathbf{x}_n^{\mathsf T}\right)^{-1},$$

where:

$$\hat{v}_n=\exp\{\hat{\mathbf{w}}^{\mathsf T}\mathbf{x}_n\}.$$

### EX 4.8.
Example code below (`poisscount.m`):

```matlab
%% Laplace and Metropolis-Hastings for a Poisson Counts model
% Simon Rogers, August 2011
clear all;
close all;

% Generate the 'true' data.
N = 200; % Number of data objects
x = [repmat(1,N,1) randn(N,1)];
w = randn(2,1);

temp = exp(x*w);

t = poissrnd(temp);

truew = w;
%% Newton Raphson
% Initialise w
w = rand(2,1)*5;
wall = [];
```
