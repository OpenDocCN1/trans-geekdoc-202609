![](bbox=[0.15, 0.09, 0.67, 0.2])

$$P(A|B)=\frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^{c})P(A^{c})}.\quad (3.25)$$

![](bbox=[0.26, 0.23, 0.74, 0.25])

# **SOL-38** CH.SOL- 3.9.

Given $X$ as a discrete randomly distributed variable and given $\gamma$ as the parameter of interest, the likelihood and the log-likelihood of $X$ given $\gamma$ follows respectively:

$$\mathcal{L}_{\gamma}(X=x)=p(X=x|\gamma)\quad (3.26)$$

$$\ell_{\gamma}(X=x)=\ln\left(p(X=x|\gamma)\right)\quad (3.27)$$

The term likelihood can be intuitively understood from this definition; it deduces how likely is to obtain a value $x$ when a prior information is given regarding its distribution, namely the parameter $\gamma$. For example, let us consider a biased coin toss with $p_{h}=\gamma$. Then:

$$\mathcal{L}_{\gamma}(X="H"]=p(X="H"|\gamma)=\gamma.\quad (3.28)$$

$$\ell_{\gamma}(X="H")=\ln\left(p(X="H"|\gamma)\right)=\ln\left(\gamma\right).\quad (3.29)$$

Note: The likelihood function may also follow continuous distributions such as the normal distribution. In the latter, it is recommended and often obligatory to employ the log-likelihood. Why? We encourage the reader to modify the above to the continuous case of normal distribution and derive the answer.

# **SOL-39** CH.SOL- 3.10.

The continuous prior distribution, $f(\Gamma=\gamma)$ represents what is known about the probability of the value $\gamma$ before the experiment has commenced. It is termed as being subjective, and therefore may vary considerably between researchers. By proceeding the previous example, $f(\Gamma=0.8)$ holds the probability of randomly flipping a coin that yields “heads” with chance of 80% of times.