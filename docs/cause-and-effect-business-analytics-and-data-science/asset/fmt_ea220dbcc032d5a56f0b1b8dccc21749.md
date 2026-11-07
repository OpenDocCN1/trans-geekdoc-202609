
Even though holdout sample data are used, [Algorithm 8.4](#chapter8.xhtml#box8_4) is still based on statistical estimation, and as a result, the estimates are not known with complete certainty. While it is quite common to use statistical estimates as an input to *deterministic* optimization with the assumption that the estimates are completely correct, there are mathematically advanced yet practical ways to handle uncertainty in optimization. The degree of uncertainty can be assessed using the bootstrapping method described in [Algorithm 8.5](#chapter8.xhtml#box8_5). [Section 8.5](#chapter8.xhtml#sec8_5) describes multiple methods to address optimization under uncertainty, including `MVO`, a simple version of `RO`, and `SP` – the latter is achieved by addressing uncertainty directly through probabilities using specific algorithms such as `Simulation Optimization`. These methods for optimization under uncertainty are practical to employ, especially with relatively small problems. Whether or not the analyst chooses to use them depends on how important he/she thinks it is to handle uncertainty due to statistical estimation. More sophisticated methods are introduced in [Lo et al. (2017)](#chapter8.xhtml#ref8_23).

Last but not least, the methods introduced in this chapter may serve only as starting points to consider, and there can be other issues that arise in practice to make things a little different (and more interesting), such as additional constraints and sensitivity analysis of controllable parameters (e.g., budget).

## Appendix 8.1: A Few Words on Convexity

The optimization problems in this chapter cannot guarantee global optima unless they belong to a class of “convex minimization” problems (or, equivalently, “concave maximization” problems). The convexity concept applies to problems with continuous decision variables only and thus does not apply to problems with binary decision variables. A convex minimization problem requires that the objective function is a convex function (e.g., U-shaped) and the constraints are convex inequalities. For linear constraints, they are always convex (and also concave). We now focus on the objective function.

Page 247 The simplest case of optimization is from single-variable calculus, where we want to minimize a (smooth) nonlinear function of a single variable, `f(x)`, without any constraints. To solve this problem, we take the first derivative and set it to zero: `f′(x)` = 0 and then determine the root, `x*`. Then we determine if `x*` is a local minimum by checking whether the second derivative evaluated at `x*`, `f″(x*)` ≥ 0 (one may imagine a U-shaped curve). If the latter inequality is satisfied, we know this `x*` is a local minimum. And if `f′′(x)` ≥ 0 for all `x`, which means `f(x)` is a *convex function*, then `x*` is also a *global* minimum of `f(x)`.

The conditions for multiple variables are similar. Again, if our goal is to find the values of a vector (`x[1]`,…,`x[m]`)′ such that `f(x[1],…,x[m])` is minimized (assuming again it is a smooth function), from standard calculus or operations research textbooks (e.g., [Ravindran et al. 1987](#chapter8.xhtml#ref8_29)), we equate the first partial derivative vector to zero, $\\nabla\\mathbf{f}\\left( \\mathbf{x} \\right) = \\left( \\frac{\\partial f}{\\partial x\_{1}} \\right.$,…,$\\left. ~\\frac{\\partial f}{\\partial x\_{m}} \\right)' = 0,~$ in order to determine the root, `x*` = (`x*[1]`,…,`x*[m]`)′. To check whether `x*` is a local minimum, we would check whether the second partial derivative (also known as the Hessian matrix) evaluated at `x*` is positive definite (matrix version of “greater than zero”): ∇²`f`(`x*`) ≥ 0, where the $\\left. i,jth~element~of~\\nabla^{2}\\mathbf{f}\\left( \\mathbf{x}^{\*} \\right) = \\frac{\\partial^{2}\\mathbf{f}}{\\partial\\mathbf{x}\_{\\mathbf{i}}\\mathbf{x}\_{\\mathbf{j}}} \\right|\_{\\mathbf{x}~ = ~\\mathbf{x}\*}$. To guarantee it is also the global minimum, one would check whether `f(x)` is a convex function, that is, ∇²`f`(`x`) ≥ 0 (positive semi-definite) for all values of `x`, that is, `u′ ∇²f(x) u` ≥ 0 for any values of `u` (one may imagine a bowl-shaped surface in a three-dimensional space with `m = 2`).

Let's get back to our context of uplift treatment optimization; suppose we would like to minimize the overall variance as in `model (8.10)`. It can be proved that the objective function, which is a quadratic function of decision variables, is positive semi-definite, and hence it is guaranteed that `model (8.10)` has a global minimum.

## Appendix 8.2: A Brief Introduction to Simulation Optimization

Stochastic Programming (`SP`) has a wide range of applications in any field that requires optimization under uncertainty. One of the key existing algorithms available is `Simulation Optimization`, a computationally intensive method that combines Monte Carlo simulation and optimization, as the name suggests.

Page 248 `Simulation Optimization` iterates between two steps:

1. **The Optimization Step:** It suggests a possibly improved solution given the results of previous iterations. It is typically based on a heuristic search algorithm as the optimizer, taking outputs from the Simulation step. In `CB`, the user has to indicate the number of simulations for this step under “`Optimization Control`.”

2. **The Simulation Step:** It evaluates a given solution using Monte Carlo Simulation. The strength of simulation allows this algorithm to evaluate almost any situation with a given solution suggested by the optimization step (in [Example 8.3c](#chapter8.xhtml#sec8_5_3_1), bootstrapping is employed for simulation). In `CB`, the user has to specify the number of random trials for this step.

The above two steps feed each other until a certain termination criterion is satisfied. For further information, see [Better et al. (2008)](#chapter8.xhtml#ref8_3) or [EPM Information Development Team (2009)](#chapter8.xhtml#ref8_13).

## Notes

1. Formally, `△ p[i]` = `E(△ p[i])` + uncertainty (noise) with mean zero. [⏎](#chapter8.xhtml#en8_18b)

2. Technically, the single treatment case includes a control group, so some literature refers to this simplest situation as a “two-treatment” case. [⏎](#chapter8.xhtml#en8_28b)

3. NP-completeness and its related terms are key concepts in Computer Science and Operations Research for measuring the complexity of algorithms. They are beyond the scope of this book; see [Cook (2012)](#chapter8.xhtml#ref8_5), [Cormen (2013)](#chapter8.xhtml#ref8_6), or [Fortnow (2013)](#chapter8.xhtml#ref8_15) for an introduction or Bertsimas and Tsitsiklis (1997), Papadimitriou and Steiglitz (1998), or [Dasgupta et al. (2006)](#chapter8.xhtml#ref8_10) for a formal discussion. [⏎](#chapter8.xhtml#en8_38b)

4. Specifically, in this approach, if the cluster-level solution from [Algorithm 8.4](#chapter8.xhtml#box8_4) recommends only a *single* treatment for a given cluster, we can prioritize targets using [Algorithm 8.1](#chapter8.xhtml#box8_1) or [8.2](#chapter8.xhtml#box8_2) at the cluster level. However, if the cluster-level solution involves more than one treatment for a given cluster, one may solve a binary integer program similar to `model (8.4)`, except that the problem size is much smaller as we are solving for each cluster as opposed to the entire population. [⏎](#chapter8.xhtml#en8_48b)

5. Additionally, the Four Quadrant Method described in Section 9.2 of Chapter 9 can also be used for multiple treatments, as outlined in Section 8.2.1. [⏎](#chapter8.xhtml#en8_58b)

6. While standard deviations can be estimated using the usual parametric formula (see `Eqn. (8.12a)`), estimating covariances will require methods such as bootstrapping. [⏎](#chapter8.xhtml#en8_68b)
