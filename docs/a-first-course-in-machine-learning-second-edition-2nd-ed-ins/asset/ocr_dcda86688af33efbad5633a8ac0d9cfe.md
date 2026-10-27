```
```matlab
% DP sample
basemu = 0;
basess = 1;
alp = 10; % Concentration parameter

N = 100; % Number of samples to draw

samples = [];

for n = 1:N
    if n==1
        samples = randn.*sqrt(basess) + basemu;
    else
        if rand < alp/(alp + n-1)
            % Sample a new value
            samples(end+1) = randn.*sqrt(basess) + basemu;
        else
            % Copy a previous one
            samples(end+1) = samples(randi(length(samples)));
        end
    end
end
```
```

EX 10.9. See script on accompanying webpage.

EX 10.10. We will derive the collapsed sampler. Assume that we observe $m = 1\ldots M$ datasets, each of which has $n = 1\ldots N_m$ observations, $x_n^m$. There are $k = 1\ldots K$ top-level components and the top-level concentration parameter is $\alpha$. The concentration parameter in the $m$th file is $\gamma_m$. In the $m$th file there are $v = 1\ldots V_m$ components, each associated with one of the top-level components. Let $z_{nv}^m = 1$ if the $n$th observation in the $m$th file is associated with the $v$th component in that file. Let $w_{vk}^m = 1$ if the $v$th component in the $m$th file is associated with the $k$th top-level component.

For the collapsed sampler, we require the distributions for re-sampling $z_{nv}^m$. When we re-sample this assignment, there are three possibilities. 1: We put it into a current component in file $m$. 2: We put it into a new component that uses a pre-existing top-level component. 3: We put it into a new component that has a new top-level component. We will consider each of these in turn. Firstly, though we need the posterior density over $\mu_k$ (the mean of the $k$th top-level component). This is Gaussian and given by:

$$\begin{aligned}
p(\mu_k\mid\ldots) &\propto \mathcal{N}(\mu_0,\sigma_0^2)\prod_{m=1}^{M}\prod_{n=1}^{N_m}\prod_{v=1}^{V_m}\mathcal{N}(x_n^m\mid\mu_k,\sigma^2)^{z_{nv}^m w_{vk}^m} \qquad (10.1)\\
&= \mathcal{N}(a,b^2)\\
b^2 &= \left[\frac{1}{\sigma_0^2}+\frac{1}{\sigma^2}\sum_{m,n,v}z_{nv}^m w_{vk}^m\right]^{-1}\\
a &= b^2\left[\frac{\sum_{m,n,v}z_{nv}^m w_{vk}^m x_n^m}{\sigma^2}+\frac{\mu_0}{\sigma_0^2}\right]
\end{aligned}$$