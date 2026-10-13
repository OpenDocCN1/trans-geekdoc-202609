
*p*(**y**|ℳ[*i*]) ≈ *p*(**y**|ℳ[*i*], *θ̂*[*MAP*])*p*(*θ̂*[*MAP*]|ℳ[*i*])*Δ**θ*[*θ*|*y*].

![Equation](images/B9780443292385000184/si122.png) (12.32)

To get a better feeling for each one of the factors involved in Eq. [(12.32)](#Chp012_583-634_B9780443292385000184.xhtml#deq42), let us also assume that the prior PDF is (almost) uniform with a width equal to Δ*θ*. Then Eq. [(12.32)](#Chp012_583-634_B9780443292385000184.xhtml#deq42) is rewritten as

```
$p(\mathbf{y}|\mathcal{M}_{i}) \approx p(\mathbf{y}|\mathcal{M}_{i},{\widehat{\theta}}_{MAP})\frac{\Delta\theta_{\theta|y}}{\Delta\theta}.$
```

![Equation](images/B9780443292385000184/si123.png) (12.33)

The first factor in the product on the right-hand side in Eq. [(12.33)](#Chp012_583-634_B9780443292385000184.xhtml#deq43) coincides with the likelihood function at its optimal value, because for this case of uniform prior, *θ̂*[MAP] = *θ̂*[ML]. In other words, this factor provides us with the best fit that model ℳ[*i*] can achieve on the given set of observations. However, now, in contrast to the ML method, the evidence function also depends on the second factor, $\frac{\Delta\theta_{\theta|y}}{\Delta\theta}$. As it has been pointed out in the insightful papers [13,27,28], this term accounts for the complexity of the model, and it is named the Occam factor for obvious reasons. Let us elaborate on this a bit more by following the reasoning given in [28].

![Figure 12.3 The posterior peaks around the value {\widehat{\theta}}_{MAP} Equation and the posterior PDF can be approximated by p({\widehat{\theta}}_{MAP}|\mathbf{y};\mathcal{M}_{i}) Equation over an interval of values equal to Δθθ|y.](images/B9780443292385000184/gr003.jpg)

[Figure 12.3](#Chp012_583-634_B9780443292385000184.xhtml#cf0430) The posterior peaks around the value *θ̂*[*MAP*] and the posterior PDF can be approximated by *p*(*θ̂*[*MAP*]|**y**; ℳ[*i*]) over an interval of values equal to Δ*θ*[*θ*|*y*].
