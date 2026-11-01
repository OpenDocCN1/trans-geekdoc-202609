
# Contraction and Value Iteration Convergence

The basic concept used in showing that value iteration converges is the notion of a contraction. Roughly speaking, a contraction is a function of one argument that, when applied to two different inputs in turn, produces two output values that are “closer together,” by at least some constant factor, than the original inputs. For example, the function `divide by two` is a contraction, because, after we divide any two numbers by two, their difference is halved. Notice that the `divide by two` function has a fixed point, namely `zero`, that is unchanged by the application of the function. From this example, we can discern two important properties of contractions:

### Contraction
- A contraction has only one fixed point; if there were two fixed points they would not get closer together when the function was applied, so it would not be a contraction.
- When the function is applied to any argument, the value must get closer to the fixed point (because the fixed point does not move), so repeated application of a contraction always reaches the fixed point in the limit.

Now, suppose we view the Bellman update ([Equation (16.10)](#Chapter16-02.xhtml#eq16-10)) as an operator `B` that is applied simultaneously to update the utility of every state. Then the Bellman equation becomes `U = B U` and the Bellman update equation can be written as

`U[i + 1] ← B U[i]`.

Next, we need a way to measure distances between utility vectors. We will use the max norm, which measures the “length” of a vector by the absolute value of its biggest component:

### Max norm
$\\left. \\text{∥}U \\parallel \\,\\,\\, = \\max\\limits\_{s} \\middle| U(s) \\middle| . \\right.$

With this definition, the “distance” between two vectors, `||U — U'||`, is the maximum difference between any two corresponding elements. The main result of this section is the following: Let `Ui` and `U'i` be any two utility vectors. Then we have

$\\begin{matrix} {\\parallel BU\_{i} - B{U^{\\prime}}\_{i} \\parallel \\,\\, \\leq \\,\\,\\gamma \\parallel U\_{i} - {U^{\\prime}}\_{i} \\parallel .} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(16.11)} \\\\ \\end{matrix}$

That is, the Bellman update is a contraction by a factor of `γ` on the space of utility vectors. (Exercise 16.VICT provides some guidance on proving this claim.) Hence, from the properties of contractions in general, it follows that value iteration always converges to a unique solution of the Bellman equations whenever `γ < 1`.

We can also use the contraction property to analyze the rate of convergence to a solution. In particular, we can replace `U'i` in [Equation (16.11)](#Chapter16-02.xhtml#eq16-11) with the true utilities `U`, for which `B U = U`. Then we obtain the inequality

`|| B U[i] - U || ≤ γ || U[i] - U ||`.

If we view `||Ui — U||` as the error in the estimate `Ui`, we see that the error is reduced by a factor of at least `γ` on each iteration. Thus, value iteration converges exponentially fast. We can calculate the number of iterations required as follows: First, recall from [Equation (16.1)](#Chapter16-01.xhtml#eq16-1) that the utilities of all states are bounded by `±Rmax/(1 – γ)`. This means that the maximum initial error `||U[0] – U|| ≤ 2 Rmax/(1 – γ)`. Suppose we run for `N` iterations to reach an error of at most `ϵ`. Then, because the error is reduced by at least `γ` each time, we require `γ^N · 2 Rmax/(1 – γ) ≤ ϵ`. Taking logs, we find that

`N = [log(2 Rmax / ϵ (1 - γ))/log(1/γ)]`

iterations suffice. [Figure 16.7(b)](#Chapter16-02.xhtml#fig16-7) shows how `N` varies with `γ`, for different values of the ratio `ϵ/Rmax`. The good news is that, because of the exponentially fast convergence, `N` does not depend much on the ratio `ϵ/Rmax`. The bad news is that `N` grows rapidly as `γ` becomes close to 1. We can get fast convergence if we make `γ` small, but this effectively gives the agent a short horizon and could miss the long-term effects of the agent’s actions.

The error bound in the preceding paragraph gives some idea of the factors influencing the run time of the algorithm, but is sometimes overly conservative as a method of deciding when to stop the iteration. For the latter purpose, we can use a bound relating the error to the size of the Bellman update on any given iteration. From the contraction property ([Equation (16.11)](#Chapter16-02.xhtml#eq16-11)), it can be shown that if the update is small (i.e., no state’s utility changes by much), then the error, compared with the true utility function, also is small. More precisely,

$\\begin{matrix} {\\text{if}\\,\\,\\,\\,\\,\\,\\,\\, \\parallel U\_{i + 1} - U\_{i} \\parallel < \\epsilon(1 - \\gamma)/\\gamma\\,\\,\\,\\,\\,\\,\\text{then}\\,\\,\\,\\,\\,\\, \\parallel U\_{i + 1} - U \\parallel < \\epsilon.} & {\\,\\,\\,\\,\\,\\,\\,(16.12)} \\\\ \\end{matrix}$

This is the termination condition used in the `VALUE–ITERATION` algorithm of [Figure 16.6](#Chapter16-02.xhtml#fig16-6).

So far, we have analyzed the error in the utility function returned by the value iteration algorithm. What the agent really cares about, however, is how well it will do if it makes its decisions on the basis of this utility function. Suppose that after `i` iterations of value iteration, the agent has an estimate `U[i]` of the true utility `U` and obtains the maximum expected utility (`MEU`) policy `πi` based on one-step look-ahead using `Ui` (as in [Equation (16.4)](#Chapter16-01.xhtml#eq16-4)). Will the resulting behavior be nearly as good as the optimal behavior? This is a crucial question for any real agent, and it turns out that the answer is yes. `U^{π[i]}(s)` is the utility obtained if `πi` is executed starting in `s`, and the policy loss `|| U^{π[i]} - U ||` is the most the agent can lose by executing `πi` instead of the optimal policy `π*`. The policy loss of `πi` is connected to the error in `Ui` by the following inequality:

### Policy loss
$\\begin{matrix} {\\text{if}\\,\\,\\,\\,\\,\\,\\,\\, \\parallel U\_{i} - U \\parallel < \\varepsilon\\,\\,\\,\\,\\,\\,\\text{then}\\,\\,\\,\\,\\,\\,\\, \\parallel U^{\\pi\_{i}} - U \\parallel < 2\\varepsilon\\text{.}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(16.13)} \\\\ \\end{matrix}$

In practice, it often occurs that `πi` becomes optimal long before `Ui` has converged. [Figure 16.8](#Chapter16-02.xhtml#fig16-8) shows how the maximum error in `Ui` and the policy loss approach zero as the value iteration process proceeds for the 4 × 3 environment with `γ = 0.9`. The policy `πi` is optimal when `i = 5`, even though the maximum error in `Ui` is still 0.51.

Description

In all three graphs, The vertical axis is labeled P (U vertical bar E subscript j) and the horizontal axis is labeled U. The horizontal axis is marked at U subscript 1 and U subscript 2 from the right, respectively. Each graph has two color-coded bell-shaped curves. The blue curve has its peak at U subscript 1 and the red curve has its peak at U subscript 2. Part (“a”): The two bell-shaped curves have the same width and the peaks are at the same height. Part (b): The blue curve is narrower than the red curve and the peak height of the blue curve is taller than the red curve. Part (c): The two bell-shaped curves have the same width. The peak height of the blue curve is shorter than the red curve.

×![](images/Fig-230.jpg)

Figure 16.8 The maximum error `|| Ui – U ||` of the utility estimates and the policy loss `||Uπi – U ||`, as a function of the number of iterations of value iteration on the 4 × 3 world.
