
$$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha \\cdot \\gamma^{t} \\cdot (\\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}})) \\cdot G\_{t}} \\\\ \\end{array}$$  

where `α` is the learning rate.

This Policy Gradient algorithm is Monte-Carlo because it is not bootstrapped (complete returns are used as an unbiased sample of `Q`^(*π*), rather than a bootstrapped estimate). In terms of our previously-described classification of RL algorithms as Value Function-based or Policy-based or Actor-Critic, REINFORCE is a Policy-based algorithm since REINFORCE does not involve learning a Value Function.

Now let's write some code to implement the REINFORCE algorithm. In this chapter, we will focus our Python code implementation of Policy Gradient algorithms to continuous action spaces, although it should be clear based on the discussion so far that the Policy Gradient approach applies to arbitrary action spaces (we've already seen an example of the policy function parameterization for discrete action spaces). To keep things simple, the function `reinforce_gaussian` below implements REINFORCE for the simple case of single-dimensional continuous action space (i.e. 𝒜 = ℝ), although this can be easily extended to multi-dimensional continuous action spaces. So in the code below, we work with a generic state space given by `TypeVar('s')` and the action space is specialized to `float` (representing ℝ).

As seen earlier in the canonical example for single-dimensional continuous action space, we assume a Gaussian distribution for the policy. Specifically, the policy is represented by an arbitrary parameterized function approximation using the class `FunctionApprox`. As a reminder, an instance of `FunctionApprox` represents a probability distribution function `f` of the conditional random variable variable `y`|`x` where `x` belongs to an arbitrary domain 𝒳 and `y` ∈ ℝ (probability of `y` conditional on `x` denoted as `f`(`x`; **θ**)(`y`) where **θ** denotes the parameters of the `FunctionApprox`). Note that the `evaluate` method of `FunctionApprox` takes as input an Iterable of `x` values and calculates `g`(`x`; **θ**) = 𝔼[`f`(`x`; **θ**)]\[`y`\] for each of the `x` values. In our case here, `x` represents non-terminal states in 𝒩 and `y` represents actions in ℝ, so `f`(`s`; **θ**) denotes the probability distribution of actions, conditional on state `s` ∈ 𝒩, and `g`(`s`; **θ**) represents the *Expected Value* of (real-numbered) actions, conditional on state `s` ∈ 𝒩. Since we have assumed the policy to be Gaussian,

$$\\begin{array}{r} {\\pi(s,a;\\mathbf{\\mathbf{\\theta}}) = \\frac{1}{\\sqrt{2\\pi\\sigma^{2}}} \\cdot e^{- \\frac{{(a - g(s;\\mathbf{\\mathbf{\\theta}}))}^{2}}{2\\sigma^{2}}}} \\\\ \\end{array}$$  

To be clear, our code below works with the `@abstractclass FunctionApprox` (meaning it is an arbitrary parameterized function approximation) with the assumption that the probability distribution of actions given a state is Gaussian whose variance `σ`² is assumed to be a constant. Assume we have `m` features for our function approximation, denoted as `ϕ`(`s`) = (`ϕ`[1](`s`), …, `ϕ`[*m*](`s`)) for all `s` ∈ 𝒩.

`σ` is specified in the code below as `policy_stdev`. The input `policy_mean_approx0:FunctionApprox[NonTerminal[S]]` specifies the function approximation we initialize the algorithm with (it is up to the user of `reinforce_gaussian` to configure `policy_mean_approx0` with the appropriate functional form for the function approximation, the hyper-parameter values, and the initial values of the parameters **θ** that we want to solve for).

The Gaussian policy (of the type `GaussianPolicyFromApprox`) selects an action `a` (given state `s`) by sampling from the Gaussian distribution defined by mean `g`(`s`; **θ**) and variance `σ`².

The score function is given by:

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(s,a;\\mathbf{\\mathbf{\\theta}}) = \\frac{(a - g(s;\\mathbf{\\mathbf{\\theta}})) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}g(s;\\mathbf{\\mathbf{\\theta}})}{\\sigma^{2}}} \\\\ \\end{array}$$  

The outer loop of `while True:` loops over trace experiences produced by the method `simulate_actions` of the input `mdp` for a given input `start_states_distribution` (specifying the initial states distribution `p`[0]:𝒩→\[0,1\]), and the current policy `π` (that is parameterized by **θ**, which updates after each trace experience). The inner loop loops over an Iterator of `step: ReturnStep[S, float]` objects produced by the `returns` method for each trace experience.

The variable `grad` is assigned the value of the negative score for an encountered (`S`[*t*], `A`[*t*]) in a trace experience, i.e., it is assigned the value:

$$\\begin{array}{r} {- \\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}}) = \\frac{(g(S\_{t};\\mathbf{\\mathbf{\\theta}}) - A\_{t}) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}g(S\_{t};\\mathbf{\\mathbf{\\theta}})}{\\sigma^{2}}} \\\\ \\end{array}$$  

We negate the sign of the score because we are performing Gradient Ascent rather than Gradient Descent (the `FunctionApprox` class has been written for Gradient Descent). The variable `scaled_grad` multiplies the negative of score (`grad`) with `γ`^(*t*) (`gamma_prod`) and return `G`[*t*] (`step.return_`). The rest of the code should be self-explanatory.

`reinforce_gaussian` returns an Iterable of `FunctionApprox` representing the stream of updated policies `π`(`s`, ⋅;**θ**), with each of these `FunctionApprox` being generated (using `yield`) at the end of each trace experience.

![](images/comp14_1.jpg)

The above code is in the file `rl/policy_gradient.py`.

## 14.5 Optimal Asset Allocation (Revisited)

In this chapter, we will test the PG algorithms we implement on the Optimal Asset Allocation problem of [Chapter 8](#chapter8.xhtml), specifically the setting of the class `AssetAllocDiscrete` covered in [Section 8.5](#chapter8.xhtml#sec8_5). As a reminder, in this setting, we have a single risky asset and at each of a fixed finite number of time steps, one has to make a choice of the quantity of current wealth to invest in the risky asset (remainder in the riskless asset) with the goal of maximizing the expected utility of wealth at the end of the finite horizon. Thus, this finite-horizon MDP's state at any time `t` is the pair (`t`, `W`[*t*]) where `W`[*t*] ∈ ℝ denotes the wealth at time `t`, and the action at time `t` is the investment `x`[*t*] ∈ ℝ in the risky asset.

We provided an ADP backward-induction solution to this problem in [Chapter 6](#chapter6.xhtml), implemented with `AssetAllocDiscrete` (code in `rl/chapter7/asset_alloc_discrete.py`). Now we want to solve it with PG algorithms, starting with REINFORCE. So we require a new interface and hence, we implement a new class `AssetAllocPG` with appropriate tweaks to `AssetAllocDiscrete`. The key change in the interface is that we have inputs `policy_feature_funcs`, `policy_mean_dnn_spec` and `policy_stdev` (see code below). `policy_feature_funcs` represents the sequence of feature functions for the `FunctionApprox` representing the mean action for a given state (i.e., `g`(`s`; **θ**) = 𝔼[`f`(`s`; **θ**)]\[`a`\] where `f` represents the policy probability distribution of actions for a given state). `policy_mean_dnn_spec` specifies the architecture of a deep neural network a user would like to use for the `FunctionApprox`. `policy_stdev` represents the fixed standard deviation `σ` of the policy probability distribution of actions for any state. Unlike the backward-induction solution of `AssetAllocDiscrete` where we had to model a separate MDP for each time step in the finite horizon (where the state for each time step's MDP is the wealth), here we model a single MDP across all time steps with the state as the pair of time step index `t` and the wealth `W`[*t*]. `AssetAllocState = Tuple[int, float]` is the data type for the state (`t`, `W`[*t*]).
