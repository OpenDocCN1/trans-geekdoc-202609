
That is, it is equal to the probability of the feature vector to belong to class `ω₁` (`ω₂`) and to lie in the "wrong" region `ℛ₂` (`ℛ₁`) in the feature space.

Eq. [(7.5)](#Chp007_293-342_B9780443292385000135.xhtml#deq6) can be written as

```
(7.6)
```

It turns out that the Bayesian classifier, as defined in [(7.3)](#Chp007_293-342_B9780443292385000135.xhtml#deq3), minimizes `Pₑ` with respect to `ℛ₁` and `ℛ₂` [11,38]. This is also true for the general case of `M` classes (Problem [7.1](#Chp007_293-342_B9780443292385000135.xhtml#o0010)).

[Fig. 7.1](#Chp007_293-342_B9780443292385000135.xhtml#f0010)A demonstrates geometrically the optimality of the Bayesian classifier for the two-class one-dimensional case and assuming equiprobable classes (`P(ω₁) = P(ω₂) = 1/2`). The region `ℛ₁`, to the left of the threshold value `x₀`, corresponds to `p(x|ω₁) > p(x|ω₂)`, and the opposite is true for region `ℛ₂`. The probability of error is equal to the area of the shaded region, which is equal to the sum of the two integrals in Eq. [(7.6)](#Chp007_293-342_B9780443292385000135.xhtml#deq7). In [Fig. 7.1](#Chp007_293-342_B9780443292385000135.xhtml#f0010)B, the threshold has been moved away from the optimal Bayesian value, and as a result the probability of error, given by the total area of the corresponding shaded region, increases.

![Figure 7.1 (A) The classification error probability for partitioning the feature space, according to the Bayesian optimal classifier, is equal to the area of the shaded region. (B) Moving the threshold value away from the value corresponding to the optimal Bayes rule increases the probability of error, as is indicated by the increase of the area of the corresponding shaded region.](images/B9780443292385000135/gr001.jpg)

**Figure 7.1** (A) The classification error probability for partitioning the feature space, according to the Bayesian optimal classifier, is equal to the area of the shaded region. (B) Moving the threshold value away from the value corresponding to the optimal Bayes rule increases the probability of error, as is indicated by the increase of the area of the corresponding shaded region.

### 7.2.1 Average risk

Because in classification the dependent variable (label), `y`, is of a discrete nature, the classification error probability may seem like the most natural cost function to be optimized. However, this is not always true. In certain applications, not all errors are of the same importance. For example, in a medical diagnosis system, committing an error by predicting the class of a finding in an X-ray image as being "malignant" while its true class is "normal" is less significant than an error the other way around. In the former case, the wrong diagnosis will be revealed in the next set of medical tests. However, the opposite may have unwanted consequences. For such cases, one uses an alternative to the probability of error cost function that puts relative weights on the errors according to their importance. This cost function is known as the *average risk* and it results in a rule that resembles that of the Bayesian classifier, yet it is slightly modified due to the presence of the weights.

Let us start from the simpler two-class case. The *risk* or *loss* associated with each one of the two classes is defined as
