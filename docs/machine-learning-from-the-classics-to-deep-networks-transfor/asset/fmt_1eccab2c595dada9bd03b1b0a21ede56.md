
## 3.6 The Cramér–Rao lower bound

In the previous sections, we saw how one can improve the performance of the MVU estimator, provided that this exists and it is known. However, how can one know that an unbiased estimator that has been obtained is also of minimum variance? The goal of this section is to introduce a criterion that can provide such information.

The *Cramér–Rao lower bound* [9,31] is an elegant theorem and one of the most well-known techniques used in statistics. It provides a lower bound on the variance of *any* unbiased estimator. This is very important because (a) it offers the means to assert whether an unbiased estimator has minimum variance, which, of course, in this case coincides with the corresponding MSE in Eq. [(3.22)](#Chp003_65-117_B9780443292385000093.xhtml#deq37), (b) if this is not the case, it can be used to indicate how far away the performance of an unbiased estimator is from the optimal one, and finally (c) it provides the designer with a tool to know the best possible performance that can be achieved by an unbiased estimator. Because our main purpose here is to focus on the insight and physical interpretation of the method, we will deal with the simple case where our unknown parameter is a real number. The general form of the theorem, involving vectors, is given in Appendix B.

We are looking for a bound of the variance of an unbiased estimator, whose randomness is due to the randomness of the training data, as we change from one set to another. Thus, it does not come as a surprise that the bound involves the joint PDF of the data, parameterized in terms of the unknown parameter `θ`. Let `𝒳 = {x[1], x[2], …, x[N]}` denote the set of `N` observations, corresponding to a random vector^([^(10)](#fn10)).

### Theorem 3.1

*It is assumed that the joint PDF satisfies the following* regularity *condition:*

```
E[ ∂ln p(𝒳;θ) / ∂θ ] = 0, ∀θ.
```

*This regularity condition is a weak one and holds for most of the cases in practice (Problem* [3.7](#Chp003_65-117_B9780443292385000093.xhtml#o0040)*). Then, the variance of any unbiased estimator,* `θ̂`*, must satisfy the following inequality:*

![Equation](images/B9780443292385000093/fx002.jpg)(3.29)

*where*
