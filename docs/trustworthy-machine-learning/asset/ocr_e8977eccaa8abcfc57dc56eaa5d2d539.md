The likelihood ratio ranges from zero to infinity and the threshold value η = 1 is optimal for equal priors and equal costs. Applying any monotonically increasing function to both the likelihood ratio and the threshold still yields a Bayes optimal decision function with the same risk R*. That is,

ŷ*(·) = {0, g(Λ(x)) ≤ g(η)
1, g(Λ(x)) > g(η)}

Equation 6.19

for any monotonically increasing function g(·) is still optimal.

It is somewhat more natural to think of a score s(x) to be in the range [0,1] because it corresponds to the label values y ∈ {0,1} and could also potentially be interpreted as a probability. The score, a continuous-valued output of the decision function, can then be thought of as a confidence in the prediction and be obtained by applying a suitable g function to the likelihood ratio. In this case, 0.5 is the threshold for equal priors and costs. Intermediate score values are less confident and extreme score values (towards 0 and 1) are more confident. Just as the likelihood ratio may be viewed as a random variable, the score may also be viewed as a random variable S. The Brier score is an appropriate performance metric for the continuous-valued output score of the decision function:

Brier score = E[(S − Y)²].

Equation 6.20

It is the mean-squared error of the score S with respect to the true label Y. For a finite number of samples {(s₁,y₁), ..., (sₙ,yₙ)}, you can compute it as:

Brier score = 1/n Σ_{j=1}^{n} (s_j − y_j)².

Equation 6.21

The Brier score decomposes into the sum of two separable components: calibration and refinement. The concept of calibration is that the predicted score corresponds to the proportion of positive true labels. For example, a bunch of data points all having a calibrated score of s = 0.7 implies that 70% of them have true label y = 1 and 30% of them have true label y = 0. Said another way, perfect calibration implies that the probability of the true label Y being 1 given the predicted score S being s is the value s itself: P(Y = 1 | S = s) = s. Calibration is important for probabilistic risk assessments: a perfectly calibrated score can be interpreted as a probability of predicting one class or the other. It is also an important concept for evaluating causal inference methods, described in Chapter 8, for algorithmic fairness, described in Chapter 10, and for communicating uncertainty, described in Chapter 13.

6 José Hernández-Orallo, Peter Flach, and César Ferri. “A Unified View of Performance Metrics: Translating Threshold Choice into Expected Classification Loss.” In: Journal of Machine Learning Research 13 (Oct. 2012), pp. 2813–2869.