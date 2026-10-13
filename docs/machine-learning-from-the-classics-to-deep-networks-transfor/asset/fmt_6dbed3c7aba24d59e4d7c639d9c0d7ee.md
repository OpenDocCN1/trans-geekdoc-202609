
Also, we have already commented in Section [14.5](#Chp014_717-754_B9780443292385000202.xhtml) that a major drawback of importance sampling is the large variance of the weights, which becomes more severe in high-dimensional spaces, where our interest will be from now on. Let us elaborate on the variance problem a bit more and seek ways to bypass/reduce this undesired behavior.

It can be shown (e.g., [35] and Problem [17.1](#Chp017_855-884_B9780443292385000238.xhtml#o0030)) that the variance of the corresponding estimator, `μ̂`, in Eq. [(17.1)](#Chp017_855-884_B9780443292385000238.xhtml#deq1) is given by

```
var[μ̂] = (1/N) ( ∫ f²(x)p²(x)/q(x) dx - μ_f² )
```

Observe that if the numerator `f²(x)p²(x)` tends to zero slower than `q(x)` does, then for fixed `N`, the variance `var[μ̂] → ∞`. This demonstrates the significance of selecting `q` very carefully. It is not difficult to see, by minimizing Eq. [(17.4)](#Chp017_855-884_B9780443292385000238.xhtml#deq4), that the optimal choice for `q(x)`, leading to the minimum (zero) variance, is proportional to the product `f(x)p(x)` (try it!). We will make use of this result later on. Note, of course, that the proportionality constant should be `1/μ[f]`, which is not known. Thus, this result can only be considered as a benchmark.

Concerning the variance issue, let us turn our attention to the unbiased estimator `Ẑ` of `Z` in Eq. [(17.2)](#Chp017_855-884_B9780443292385000238.xhtml#deq2). It can be shown (Problem [17.2](#Chp017_855-884_B9780443292385000238.xhtml#o0035)) that

```
var[Ẑ] = (Z²/N) ( ∫ p²(x)/q(x) dx - 1 )
```

By its definition, the variance of `Ẑ` is directly related to the variance of the weights. It turns out that, in practice, the variance in Eq. [(17.5)](#Chp017_855-884_B9780443292385000238.xhtml#deq5) exhibits an exponential dependence on the dimensionality (e.g., [12,16] and Problem [17.5](#Chp017_855-884_B9780443292385000238.xhtml#o0050)). In such cases, the number of samples, `N`, has to be excessively large in order to keep the variance relatively small. One way to *partially* cope with the variance-related problem is the *resampling* technique.

### 17.2.2 Resampling
