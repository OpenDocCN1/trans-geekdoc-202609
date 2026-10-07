# Developing the Fundamentals of Hypothesis Testing 83

# 4.4.3 Using Software to identify Rejection Regions

We can use software to identify the rejection region or regions under the null hypothesis. Doing so has several advantages, including the speed of the calculations, as well as a much larger range of possible parameters (Y, n, π) than are summarized in Table C.1. In R, the qbinom function in the [stats] package computes critical values of the binomial distribution. The input parameters are the size of the sample (n), the probability of success (π), and a value related to α. By default, the return function returns values for the lower tail of the distribution. We consider three cases:

+   1. Directional hypothesis with lower critical value (e.g., H₀; π < .5). In this case, qbinom provides the critical value directly. For example, if n = 8 and α = .05, qbinom(.05, size = 8, prob = .5) returns the 2. This means we can reject H₀ when Y < 2, or equivalently, when Y ≤ 1.
2. Directional hypothesis with upper tail critical value (e.g., H₀; π > .5). Here, we use the option lower.tail = FALSE to compute upper-tail probabilities: qbinom(.05, size = 8, prob = .5, lower.tail = 6, meaning we can reject the null when Y > 6, or equivalently, when Y ≥ 7.
3. Two-sided alternative hypothesis (e.g., H₀; π ≠ .5). In this case, we divide half of the probability in each tail. We then apply qbinom, once for the lower and once for the upper rejection region, following the same guidance as the directional tests. For example, with n = 8 and α = .05, we use α/2 to identify the lower critical value: qbinom(.025, size = 8, prob = .5) = 1, meaning we can reject when Y < 1, or equivalently, when Y = 0. For the upper critical value, qbinom(.025, size = 8, prob = .5, lower.tail = FALSE) = 7, meaning that we can reject the null when Y = 7 or equivalently, when Y = 8.

# 4.5 The Power of a Statistical Test

# 4.5.1 Errors in Decision Making

In deciding to reject or not reject a null hypothesis, we can make two types of errors. If the null hypothesis is true, rejecting it is a false positive that we call a Type 1 error. As we have just discussed, the probability of a Type 1 error is α, the significance level. This means that the Type 1 error rate is under the control of the researcher. If the null hypothesis is false, we can make different kind of error by failing to reject it; this is a false negative. Failure to reject a null hypothesis when it is false is called a Type 2 error, and its probability, p(to reject H₀ | H₁ is false), is referred to as β (Greek letter beta). The complementary conditional probability, that is, p(reject H₀ | H₁ is false), is called the power of the test. When H₁ is false, only two decisions are possible: fail to reject it (with probability β) or reject it (with probability 1 - β). Therefore, power = 1 - β.
The following table may help to clarify the meanings of α, β, and power:

| Decision in the Population | Reject H₀ | Fail to reject H₀ |
|--- |--- |--- |
| H₀ True | α = Type 1 error rate | 1 - α |
| H₁ False | power = 1 - β | β = Type 2 error rate |