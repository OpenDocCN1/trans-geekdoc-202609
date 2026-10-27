```
22 for k = 1:K
23     X = [X x.^k];
24     testX = [testX testx.^k];
25 end
26
27
28 w_hat = inv(X'*X)*X'*t;
29 ss_hat = mean((t - X*w_hat).^2);
30 pred_va = ss_hat*diag(testX*inv(X'*X)*testX');
31 % Make a plot
32 figure(1);hold off
33 plot(x,t,'b.');
34 hold on
35 errorbar(testx,testX*w_hat,pred.va,'r');
```

EX 2.13. The Bernoulli distribution for a binary random variable $x$ is:

$$p(x|\theta)=\theta^{x}(1-\theta)^{1-x}$$

The Fisher information is defined as the negative expected value of the second derivative of the log density evaluated at some paramater value:

$$\mathcal{F}= -\mathbf{E}_{p(x|\theta)}\left\{\left.\frac{\partial^{2}\log p(x|\theta)}{\partial\theta^{2}}\right|_{\theta}\right\}$$

Differentiating $\log p(x|\theta)$ twice gives:

$$\frac{\partial\log p(x|\theta)}{\partial\theta}=\frac{x}{\theta}-\frac{1-x}{1-\theta}$$ $$\frac{\partial^{2}\log p(x|\theta)}{\partial\theta^{2}}=-\frac{x}{\theta^{2}}-\frac{1-x}{(1-\theta)^{2}}.$$

The Fisher information is therefore:

$$\mathcal{F}=\frac{1}{\theta^{2}}\mathbf{E}_{p(x|\theta)}\{x\}+\frac{1}{(1-\theta)^{2}}\mathbf{E}_{p(x|\theta)}\{1-x\}.$$

Substituting in the expectations ($\theta$ and $1-\theta$ respectively gives:

$$\mathcal{F}=\frac{\theta}{\theta^{2}}+\frac{1-\theta}{(1-\theta)^{2}}=\frac{1}{\theta(1-\theta)}$$

EX 2.14. The multivariate Gaussian pdf is given by:

$$p(\mathbf{x}|\boldsymbol{\mu},\boldsymbol{\Sigma})=\frac{1}{(2\pi)^{D/2}|\boldsymbol{\Sigma}|^{1/2}}\exp\left\{-\frac{1}{2}(\mathbf{x}-\boldsymbol{\mu})^{\top}\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu})\right\}.$$

Logging and removing terms not including $\boldsymbol{\mu}$:

$$\log p(\mathbf{x}|\boldsymbol{\mu},\boldsymbol{\Sigma})\propto\boldsymbol{\mu}^{\top}\boldsymbol{\Sigma}^{-1}\mathbf{x}-\frac{1}{2}\boldsymbol{\mu}^{\top}\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}.$$