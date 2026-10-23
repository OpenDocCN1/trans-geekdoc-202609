(uncentered) second-order moment; however, it lacks the correction factor. Thus, unlike in Adam, the RMSProp second-order moment estimate may have high bias early in training. Adam is generally regarded as being fairly robust to the choice of hyperparameters, though the learning rate sometimes needs to be changed from the suggested default.

# 8.5.4 Choosing the Right Optimization Algorithm

We have discussed a series of related algorithms that each seek to address the challenge of optimizing deep models by adapting the learning rate for each model parameter. At this point, a natural question is: which algorithm should one choose?

Unfortunately, there is currently no consensus on this point. Schaul et al. (2014) presented a valuable comparison of a large number of optimization algorithms across a wide range of learning tasks. While the results suggest that the family of algorithms with adaptive learning rates (represented by RMSProp and AdaDelta)

```
Algorithm 8.7 The Adam algorithm
Require: Step size ε (Suggested default: 0.001)
Require: Exponential decay rates for moment estimates, ρ1 and ρ2 in [0,1). (Suggested defaults: 0.9 and 0.999 respectively)
Require: Small constant δ used for numerical stabilization (Suggested default: 10^{-8})
Require: Initial parameters θ
Initialize 1st and 2nd moment variables s = 0, r = 0
Initialize time step t = 0
while stopping criterion not met do
Sample a minibatch of m examples from the training set {x^{(1)},...,x^{(m)}} with corresponding targets y^{(i)}.
Compute gradient: g ← (1/m) ∇θ ∑i L(f(x^{(i)};θ), y^{(i)})
t ← t + 1
Update biased first moment estimate: s ← ρ1 s + (1 - ρ1) g
Update biased second moment estimate: r ← ρ2 r + (1 - ρ2) g ⊙ g
Correct bias in first moment: ŝ ← s / (1 - ρ1^t)
Correct bias in second moment: r̂ ← r / (1 - ρ2^t)
Compute update: Δθ = -ε ŝ / sqrt(r̂ + δ)  (operations applied element-wise)
Apply update: θ ← θ + Δθ
end while
```