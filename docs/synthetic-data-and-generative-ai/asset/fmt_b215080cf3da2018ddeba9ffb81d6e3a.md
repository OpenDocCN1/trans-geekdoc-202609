
## 1.3.3 Curve Fitting Issues

Unfortunately, `curve_fitting` fails or performs very poorly in most cases. [Fig. 1.4](#Chp001_1-34_B9780443218576000059.xhtml#f0030) shows one of the relatively rare cases where it works well in the presence of noise. This Python function is still very useful in many contexts, but not in our example. The default setting (`method='lm'`, to be avoided) uses a supposedly robust version of the Levenberg–Marquardt algorithm, dating back to 1977, see [here](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.least_squares.xhtml). Essentially, it gets stuck in local minima or fails to converge, and may even reject a manually chosen initial condition close to an optimum as “not feasible”. Surprisingly, increasing the amount of noise in the data can provide improvements.

To fix the numerical instability problem, one can use a more modern technique, such as `swarm optimization` [[Wiki](https://en.wikipedia.org/wiki/Particle_swarm_optimization)]. The `PySwarms` library documented [here](https://pyswarms.readthedocs.io/en/latest/) is the Python solution. For a tutorial, see [here](https://machinelearningmastery.com/a-gentle-introduction-to-particle-swarm-optimization/). A simpler home-made solution taking advantage of the fact that the fitting curve `f[θ](x)`![Image](images/B9780443218576000059/si146.png) (called regression function by statisticians) is linear both in `θ[1]`![Image](images/B9780443218576000059/si161.png) and `θ[4]`![Image](images/B9780443218576000059/si162.png), consists in splitting the problem as follows:

*   **Step 1:** Sample `θ[2], θ[5]`![Image](images/B9780443218576000059/si163.png) over a region large enough to encompass the optimum values.
*   **Step 2:** Given `θ[2], θ[5]`![Image](images/B9780443218576000059/si164.png), find `θ[1], θ[4]`![Image](images/B9780443218576000059/si165.png) that minimizes `$E(\theta) = \sum_{k = 1}^{n}g^{2}(Y_{k},X_{k};\theta)`![Image](images/B9780443218576000059/si166.png).

Here `(Y[k], X[k])`![Image](images/B9780443218576000059/si167.png) is the `k`th observation in the training set, and `θ = (θ[1], θ[2], θ[4], θ[5])`![Image](images/B9780443218576000059/si168.png). Both steps are straightforward. You repeat them until you reach a point where the minimum `E(θ)`![Image](images/B9780443218576000059/si169.png) computed over the past iterations almost never decreases anymore. Step 2 is just a simple standard two-dimensional linear regression with no intercept, with an exact solution. One of the benefits is that if there are multiple minima, you are bound to find them all, without facing convergence issues. It also reduces a 4D Monte Carlo simulation to a 2D one.

### 1.3.3.2 Python code

Despite the issues previously described, I decided to include the Python code. It shows how the `curve_fitting` function works, beyond using the default settings. It is still a good optimization technique for many problems such as polynomial regression. Unfortunately, not for our problem. If you decrease the amount of noise from `a7=0.2` to `a7=0.1` in the code below, there is a dramatic drop in performance. Likewise, if you change the initial `θ[5]`![Image](images/B9780443218576000059/si170.png) (the last component in `fx011.jpg_start`) from 1.8 to 1.7, the performance collapses. The exact value in this example is `θ[5]=2`![Image](images/B9780443218576000059/si171.png) by construction; the estimated (final) value produced by the Python code is about 1.995.

[Table 1.2](#Chp001_1-34_B9780443218576000059.xhtml#t0015) shows the quality of the estimation, for the parameter vector `θ = (θ[1], θ[2], θ[4], θ[5])`![Image](images/B9780443218576000059/si168.png). The procedure `curve_fitting` starts with an initial guess `fx011.jpg_start` labeled “Start” in the table, and ends with the entry marked as “End” in the table: supposedly, close to an optimum `θ^*`![Image](images/B9780443218576000059/si10.png). Because of the way the synthetic data is generated (within the Python code), the row marked “Model” and consisting of the value `a[1], a[2], a[4], a[5]`![Image](images/B9780443218576000059/si173.png) is always close to an optimum `θ^*`![Image](images/B9780443218576000059/si10.png), unless the amount of noise introduced in the training set is too large. The “End” solution (the output of `curve_fitting`) is based exclusively on the training set points (the red dots in [Fig. 1.4](#Chp001_1-34_B9780443218576000059.xhtml#f0030)), not on the validation set (the orange dots). Yet the approximation is unusually good, given the amount of noise.

[Table 1.2](#Chp001_1-34_B9780443218576000059.xhtml#cf0215)

First and last step of `curve_fitting`, approaching the model.

| | `θ[1]`![Image](images/B9780443218576000059/si161.png) | `θ[2]`![Image](images/B9780443218576000059/si172.png) | `θ[4]`![Image](images/B9780443218576000059/si162.png) | `θ[5]`![Image](images/B9780443218576000059/si170.png) |
|---|---|---|---|---|
| Start | 0.00000 | 1.00000 | 0.00000 | 1.80000 |
| End | 0.52939 | 1.42184 | −0.67571 | 1.99526 |
| Model | 0.50000 | 1.41421 | −0.70000 | 2.00000 |

![Image](images/B9780443218576000059/t0015.png)

By noise, I do not mean a random or Gaussian noise. Here the noise is deterministic: the purpose of this test is to check how well we can predict a phenomena modeled by a superimposition of multiple cosine terms of arbitrary periods, phases, and amplitudes – for instance, ocean tides over time – if we only use a sum of two cosine terms as an approximation. This model (its generalization with more terms) is particular useful in situations where the error is not a `white noise` [[Wiki](https://en.wikipedia.org/wiki/White_noise)], but instead smooth and continuous everywhere: for instance, in granular temperature forecast.

The curve fitting code, also producing [Fig. 1.4](#Chp001_1-34_B9780443218576000059.xhtml#f0030), is on my GitHub repository, [here](https://github.com/VincentGranville/Machine-Learning/blob/main/Source%20Code/fittingCurve.py), under the name `fittingCurve.py`, and also listed below. I use Greek letters in the code to represent the `θ` vector and its components, for consistency reasons. Python digests them with no problem.

![](images/B9780443218576000059/gr012.jpg)

## 1.3.4 Fitting a line in 3D, unsupervised clustering, and other generalizations

In three dimensions, a line is the intersection of two planes `A` and `B`, respectively with equations `g1(w, θ[A]) = 0`![Image](images/B9780443218576000059/si174.png) and `g1(w, θ[B]) = 0`![Image](images/B9780443218576000059/si175.png). For instance, `g1(w, θ[A]) = θ[0]w[0] + θ[1]w[1] + θ[2]w[2] − θ[3]`![Image](images/B9780443218576000059/si176.png). To fit the line,

*   let `θ[A] = (θ[0], θ[1], θ[2], θ[3])^T`![Image](images/B9780443218576000059/si177.png) and `θ[B] = (θ[4], θ[5], θ[6], θ[7])^T`![Image](images/B9780443218576000059/si178.png),
*   use `θ = (θ[A], θ[B])`![Image](images/B9780443218576000059/si179.png) and `g(w, θ) = g1²(w, θ[A]) + g1²(w, θ[B])`![Image](images/B9780443218576000059/si180.png) in formula [(1.1)](#Chp001_1-34_B9780443218576000059.xhtml#deq1),
*   use the constraints `θ[A]^T θ[A] + θ[B]^T θ[B] = 1`![Image](images/B9780443218576000059/si181.png), or two constraints: `θ[A]^T θ[A] = 1`![Image](images/B9780443218576000059/si182.png) and `θ[B]^T θ[B] = 1`![Image](images/B9780443218576000059/si183.png).

With two constraints, we have two Lagrange multipliers `λ[A]`![Image](images/B9780443218576000059/si184.png) and `λ[B]`![Image](images/B9780443218576000059/si185.png) in formula [(1.2)](#Chp001_1-34_B9780443218576000059.xhtml#deq2).
