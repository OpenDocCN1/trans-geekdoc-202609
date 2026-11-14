![](bbox=[0.18, 0.09, 0.82, 0.29])

Figure 19.27: (a) When the input dimension n is large and the decision boundary is locally linear, even a small error rate in random noise will imply the existence of small adversarial perturbations. Here, $d(x_0, E)$ denotes the distance from a clean input $x_0$ to an adversarial example (A) while the distance to a random sample $N(0; \sigma^2 I) (B)$ will be approximately $\sigma \sqrt{n}$. As $n \to \infty$ the ratio of $d(x_0, A)$ to $d(x_0, B)$ goes to 0. (b) A 2d slice of the InceptionV3 decision boundary through three points: a clean image (black), an adversarial example (red), and an error in random noise (blue). The adversarial example and the error in noise lie in the same region of the error set which is misclassified as “miniature poodle”, which closely resembles a halfspace as in a. Used with kind permission of Justin Gilmer.

these two quantities is determined by

```
$$d(x_0, E) = -\sigma \Phi^{-1}(\mu)$$ (19.52)
```

where $\Phi^{-1}$ denotes the inverse cdf of the gaussian distribution. When the input dimension is large, this distance will be significantly smaller than the distance to a randomly sampled noisy image $x_0 + \delta$ for $\delta \sim N(0, \sigma I)$, as the noise term will with high probablility have norm $||\delta||_2 \approx \sigma \sqrt{d}$. As a concrete example consider the ImageNet dataset, where $d = 224 \times 224 \times 3$ and suppose we set $\sigma = .2$. Then if the error rate in noise is just $\mu = .01$, equation 19.52 will imply that $d(x_0, E) = .5$. Thus the distance to an adversarial example will be more than 100 times closer than the distance to a typical noisy images, which will be $\sigma \sqrt{d} \approx 77.6$. This phenomenon of small volume error sets being close to most points in a data distribution $p(x)$ is called **concentration of measure**, and is a property common among many high dimensional data distributions [MDM19; Gil+18b].

In summary, although the existence of adversarial examples is often discussed as an unexpected phenomenon, there is nothing special about the existence of worst-case errors for ML classifiers — they will always exist as long as errors exist.