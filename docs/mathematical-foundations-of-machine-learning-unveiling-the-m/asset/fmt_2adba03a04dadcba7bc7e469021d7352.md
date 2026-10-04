
# Learnability without Uniform Convergence

A “stochastic convex optimization” or learnability without uniform convergence problem can be considered an exceptional case of the “General Learning Setting” explained above, including additional limitations that “the objective function is Lipschitz-continuous and convex in `h` for every and that `H` is closed, convex and bounded”. The problems where is a subset of a “Hilbert space” will be addressed here.

An exceptional scenario is “the familiar linear prediction setting, where `z = y` is an instance-label pair, each hypothesis `h` belongs to a subset `H` of a Hilbert space, and `f y) = l( , y)` for some feature mapping `φ` and a loss function `l : R × Y →` which is convex with respect to its first argument”.

The scenario has been successfully established where the stochastic dependence on is linear, similar to the previous example, has been established successfully. When the “domain `H`” and the “mapping `φ`” is bounded, there is uniform convergence, meaning that `−` is uniformly bounded overall `∈ H`”. This uniform convergence of to validates selection of the empirical minimizer `=arg` and ensures that the expected value of converges to the optimal value `= inf h`

Although dependency on “`h`” is nonlinear, uniform convergence can still be established with the use of “covering number arguments” provided “`H`” is a finite dimension. Regrettably, uniform convergence may not take place if we go to infinite-dimensional hypothesis and empirical minimization may not make impart the ability to learn to the algorithm.

Remarkably, this does not mean that the problem can be deemed “unlearnable”. It can be shown that with regularization mechanisms, even when uniform convergence doesn’t exist, a learning algorithm can be developed to solve any “stochastic convex optimization” issue. This mechanism directly relates to the principle of stability.

For example, let’s look at the “convex stochastic optimization” problem given by the equation in the picture below, where for this example will be the unit sphere `H = : | ≤1”`, with `α ∈ [0,` and `∈ H”`, and “`u ∗ v`” can be defined as an element-wise product.

![](image-ohfrcb8q.jpg)

Now, considering a series of learning problems, where `=` for any sample size and establishing that a “convergence rate independent of the dimensionality cannot be expected”. This case can be formalized into infinite dimensions. The learning problem in the equation above can be considered as “that of finding the center of an unknown distribution over `x ∈` where stochastic per-coordinate confidence measures are also available”. For now, we will be focusing on the scenario wherein certain coordinates are missing, meaning `=`

By taking into consideration the distribution given below over `α): x =` with probability as 1, and is uniform over That is, are independent and identically distributed uniform “Bernoulli”. For a random sample `)”` if “`d >` then that is a result of probability greater than “`1 − > 0.63”` and a coordinate `∈ 1 . . . d”` is present such that all “confidence vectors in the sample are “0” on the coordinate i.e. `=` for all `=` Assume `∈ H”` is the “standard basis vector corresponding to this coordinate”. Then in the equation shown in the picture below, `(·)”` represents the empirical risk concerning the `(·)”`.

![](image-vzf183bh.jpg)

In another scenario, if `(·)”` denotes the actual risk for the function the equation shown in the picture below is obtained.

![](image-bpem098j.jpg)

In any given sample size ‘`m,`’ it is possible to construct a convex ‘Lipschitz-continuous objective’ in a sufficiently high dimension. This construction ensures that, with a minimum probability of ‘`0.63`’ over the sample, ‘`suph |F(3) (h)−F(3) (h)| ≥ ½.`’ Additionally, as ‘`f (·; ·)`’ is non-negative, ‘`ej`’ can be identified as an ‘empirical minimizer,’ even though its expected value, ‘`F (3) (ej) = ½,`’ is not closely aligned with the optimal expected value ‘`minh F(3) (h) = F(3) (0) = 0.`’”

To elucidate this scenario without relying on sample size, let’s consider “`H`” as the unit sphere in an infinite-dimensional Hilbert space with orthonormal basis where for its coordinates are denoted as with respect to this basis. The “confidences function as a map of each coordinate to the interval `[0,1][0,1]`, signifying an infinite sequence of real numbers in `[0,1][0,1]`. The operation of the product denoted as is defined based on this mapping, and the objective function of the equation (depicted in the first picture of this example) can be straightforwardly defined in this infinite-dimensional space.

Let’s reconsider the distribution over where and `α` is an infinite, independent, and identically distributed sequence of uniform Bernoulli random variables (i.e., a Bernoulli process with each `αi` uniform over `{0,1}{0,1}` and independent of all other It can be inferred that for any finite sample, there is a high likelihood of finding a coordinate `j` with for all and therefore, an empirical minimizer with can be obtained.

As a result, it is evident that the empirical values are not uniform while converging as expected, and empirical minimization does not ensure a solution to the learning problem. Moreover, one could potentially generate a sharper counter-example, wherein the “unique empirical minimizer is nowhere close to the optimal expected value. To achieve this, must be augmented with the use of a small term that ensures its empirical minimizer is unique and not too close to the origin. Considering the equation below where

`=` 

The goal remains convex, and “`1 + ε`” maintains its Lipschitz property. Furthermore, as the added term is strictly convex, “`f(4)(h;z)`” becomes strictly convex concerning “`h,`” explaining the uniqueness of the empirical minimizer.

Under the same distribution for “`z: x = 0`” with “`α[i]`” independently and identically distributed as uniform 0 or 1, the minimizer of “`FS(4)(h)`” is termed the empirical minimizer, subject to the constraints “`|h| ≤ 1.`” The positive aspect is that while solving this constrained optimization problem is intricate, it is not obligatory. It suffices to demonstrate that “the optimum of the unconstrained optimization problem `h∗UC = arg minFS(4)(h)` (with no constraining `h ∈ H).`

has norm `≥`

It’s important to note that in the unconstrained problem, where `αi[j] = 0` for all `i = 1…n`, only the second term of `f (4)` is dependent on `h[j]`, and we have `h∗UC[j] = 1`. For certain coordinate ‘`j`’, the occurrence of this situation leads to the conclusion that the solution to the constrained optimization problem lies on the boundary of `H`, expressed as `|hˆS| = 1`. This condition can be represented by the equation shown in the picture below, while ensuring that `F∗ ≤ F(0) = ε`.

![](image-xlwrspdg.jpg)
