The required expectation is given by:

$$\begin{aligned}
\mathbb{E}_{p(y)}\{\sin(y)\} &= \int \sin(y)p(y)\,dy \\
&= \int_{y=a}^{b} \sin(y)\frac{1}{b-a}\,dy \\
&= \frac{1}{b-a}[-\cos(y)]_a^b \\
&= \frac{\cos(a)-\cos(b)}{b-a}.
\end{aligned}$$

When $a=0$, $b=1$, this is equal to

$$\mathbb{E}_{p(y)}\{\sin(y)\}=\frac{\cos(0)-\cos(1)}{1}=0.45970.$$

Code to compute a sample-based approximation below (`sampleexpect.m`):

```
```matlab
clear all;
close all;
% Compute a sample based approximation to the required expectation
u = rand(10000,1); % Take 10000 samples
su = sin(u);
% Plot how the approximation changes as more samples are used
ns = 10:100:10000;
stages = zeros(size(ns));
for i = 1:length(ns)
    stages(i) = mean(su(1:ns(i)));
end
plot(ns,stages)
% Plot the true value
hold on
plot([0 ns(end)],[0.4597 0.4597],'k--')
```
```

# EX 2.5. The multivariate Gaussian pdf is given by:

$$p(\mathbf{w})=\frac{1}{(2\pi)^{D/2}|\boldsymbol{\Sigma}|^{1/2}}\exp\left\{-\frac{1}{2}(\mathbf{w}-\boldsymbol{\mu})^\mathsf{T}\boldsymbol{\Sigma}^{-1}(\mathbf{w}-\boldsymbol{\mu})\right\}.$$

Setting $\boldsymbol{\Sigma}=\sigma^2\mathbf{I}$ gives:

$$p(\mathbf{w})=\frac{1}{(2\pi)^{D/2}|\sigma^2\mathbf{I}|^{1/2}}\exp\left\{-\frac{1}{2\sigma^2}(\mathbf{w}-\boldsymbol{\mu})^\mathsf{T}\mathbf{I}^{-1}(\mathbf{w}-\boldsymbol{\mu})\right\}.$$

Because it only has elements on the diagonal, the determinant of $\sigma^2\mathbf{I}$ is given by the product of these diagonal elements. As they are all the same, $|\sigma^2\mathbf{I}|^{1/2}=\left(\prod_{d=1}^{D}\sigma^2\right)^{1/2}=(\sigma^2)^{D/2}$. $\mathbf{I}^{-1}=\mathbf{I}$ and multiplying a vector/matrix by $\mathbf{I}$ leaves the matrix/vector unchanged. Therefore, the argument within the expectation can be written as $-\frac{1}{2\sigma^2}(\mathbf{w}-\boldsymbol{\mu})^\mathsf{T}(\mathbf{w}-\boldsymbol{\mu})$ and recalling that $\mathbf{b}^{\mathsf{T}}\mathbf{b}=\sum_i b_i^2$, we can rewrite the pdf as:

$$p(\mathbf{w})=\frac{1}{(2\pi)^{D/2}(\sigma^2)^{D/2}}\exp\left\{-\frac{1}{2\sigma^2}\sum_{d=1}^{D}(w_d-\mu_d)^2\right\}.$$