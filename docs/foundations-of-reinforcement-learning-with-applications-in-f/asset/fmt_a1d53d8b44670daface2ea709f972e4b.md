
The code in the class `AssetAllocDiscrete` below is fairly self-explanatory. We use the function `back_opt_qvf` covered in [Section 6.9](#chapter6.xhtml#sec6_9) of [Chapter 6](#chapter6.xhtml) to perform backward induction on the optimal Q-Value Function. Since the state space is continuous, the optimal Q-Value Function is represented as a `QValueFunctionApprox` (specifically, as a `DNNApprox`). Moreover, since we are working with a generic distribution of returns that govern the state transitions of this MDP, we need to work with the methods of the abstract class `MarkovDecisionProcess` (and not the class `FiniteMarkovDecisionProcess`). The method `backward_induction_qvf` below makes the call to `back_opt_qvf`. Since the risky returns distribution is arbitrary and since the utility function is arbitrary, we don't have prior knowledge of the functional form of the Q-Value function. Hence, the user of the class `AssetAllocDiscrete` also needs to provide the set of feature functions (`feature_functions` in the code below) and the specification of a deep neural network to represent the Q-Value function (`dnn_spec` in the code below). The rest of the code below is mainly about preparing the input `mdp_f0_mu_triples` to be passed to `back_opt_qvf`. As was explained in [Section 6.9](#chapter6.xhtml#sec6_9) of [Chapter 6](#chapter6.xhtml), `mdp_f0_mu_triples` is a sequence (for each time step) of the following triples:

*   A `MarkovDecisionProcess[float, float]` object, which in the code below is prepared by the method `get_mdp`. `State` is the portfolio wealth (float type) and `Action` is the quantity of investment in the risky asset (also of float type). `get_mdp` creates a class `AssetAllocMDP` that implements the abstract class `MarkovDecisionProcess`. To do so, we need to implement the `step` method and the `actions` method. The `step` method returns an instance of `SampledDistribution`, which is based on the `sr_sampler_func` that returns a sample of the pair of next state (next time step's wealth) and reward, given the current state (current wealth) and action (current time step's quantity of investment in the risky asset).

*   A `QValueFunctionApprox[float, float]` object, prepared by `get_qvf_func_approx`. This method sets up a `DNNApprox[Tuple[NonTerminal[float], float]]` object that represents a neural-network function approximation for the optimal Q-Value Function. So the input to this neural network would be a `Tuple[NonTerminal[float], float]` representing a (state, action) pair.

*   An `NTStateDistribution[float]` object prepared by `get_states_distribution`, which returns a `SampledDistribution[NonTerminal[float]]` representing the distribution of non-terminal states (distribution of portfolio wealth) at each time step.

The `SampledDistribution[NonTerminal[float]]` is prepared by `states_sampler_func` that generates a sampling trace by sampling the state-transitions (portfolio wealth transitions) from time 0 to the given time step in a time-incremental manner (invoking the `sample` method of the risky asset's return `Distributions` and the `sample` method of a uniform distribution over the action choices specified by `risky_alloc_choices`).

![](images/comp08_2.jpg)![](images/comp08_2_2.jpg)

The above code is in the file `rl/chapter7/asset_alloc_discrete.py`. We encourage you to create a few different instances of `AssetAllocDiscrete` by varying its inputs (try different return distributions, different utility functions, different action spaces). But how do we know the code above is correct? We need a way to test it. A good test is to specialize the inputs to fit the setting of [Section 8.4](#chapter8.xhtml#sec8_4) for which we have a closed-form solution to compare against. So let us write some code to specialize the inputs to fit this setting. Since the above code has been written with an educational motivation rather than an efficient-computation motivation, the convergence of the backward induction ADP algorithm is going to be slow. So we shall test it on a small number of time steps and provide some assistance for fast convergence (using limited knowledge from the closed-form solution in specifying the function approximation). We write code below to create an instance of `AssetAllocDiscrete` with time steps `T = 4`, `μ = 13%`, `σ = 20%`, `r = 7%`, coefficient of CARA `a = 1.0`. We set up `risky_return_distributions` as a sequence of identical Gaussian distributions, `riskless_returns` as a sequence of identical riskless rate of returns, and `utility_func` as a lambda parameterized by the coefficient of CARA `a`. We know from the closed-form solution that the optimal allocation to the risky asset for each of time steps `t = 0, 1, 2, 3` is given by:

$$
\begin{array}{r}
{x_{t}^{*} = \frac{1.5}{1.07^{4 - t}}}
\\
\end{array}
$$

Therefore, we set `risky_alloc_choices` (action choices) in the range `[1.0, 2.0]` in increments of 0.1 to see if our code can hit the correct values within the 0.1 granularity of action choices.

To specify `feature_functions` and `dnn_spec`, we need to leverage the functional form of the closed-form solution for the Action-Value function (i.e., Equation (8.27)). We observe that we can write this as:

$$
\begin{array}{r}
{Q_{t}^{*}(W_{t},x_{t}) = - sign(a) \cdot e^{- (\alpha_{0} + \alpha_{1} \cdot W_{t} + \alpha_{2} \cdot x_{t} + \alpha_{3} \cdot x_{t}^{2})}}
\\
\end{array}
$$

where

$$
\begin{array}{r}
{\alpha_{0} = \frac{{(\mu - r)}^{2}(T - t - 1)}{2\sigma^{2}} + \log(|a|)}
\\
\end{array}
$$

$$
\begin{array}{r}
{\alpha_{1} = a{(1 + r)}^{T - t}}
\\
\end{array}
$$

$$
\begin{array}{r}
{\alpha_{2} = a(\mu - r){(1 + r)}^{T - t - 1}}
\\
\end{array}
$$

$$
\begin{array}{r}
{\alpha_{3} = - \frac{{(a\sigma{(1 + r)}^{T - t - 1})}^{2}}{2}}
\\
\end{array}
$$

This means, the function approximation for `Q[t]^(*)` can be set up with a neural network with no hidden layers, with the output layer activation function as `g(S) = -sign(a) * e^(-S)`, and with the feature functions as:

$$
\begin{array}{r}
{\phi_{1}((W_{t},x_{t})) = 1}
\\
\end{array}
$$

$$
\begin{array}{r}
{\phi_{2}((W_{t},x_{t})) = W_{t}}
\\
\end{array}
$$

$$
\begin{array}{r}
{\phi_{3}((W_{t},x_{t})) = x_{t}}
\\
\end{array}
$$

$$
\begin{array}{r}
{\phi_{4}((W_{t},x_{t})) = x_{t}^{2}}
\\
\end{array}
$$

We set `initial_wealth_distribution` to be a normal distribution with a mean of `init_wealth` (set equal to 1.0 below) and a standard distribution of `init_wealth_stdev` (set equal to a small value of 0.1 below).

![](images/comp08_3.jpg)

Next, we perform the Q-Value backward induction, step through the returned iterator (fetching the Q-Value function for each time step from `t = 0` to `t = T - 1`), and evaluate the Q-values at the `init_wealth` (for each time step) for all `alloc_choices`. Performing a `max` and `argmax` over the `alloc_choices` at the `init_wealth` gives us the Optimal Value function and the Optimal Policy for each time step for wealth equal to `init_wealth`.

![](images/comp08_4.jpg)

This prints the following:

![](images/comp08_5.jpg)

Now let's compare these results against the closed-form solution.

![](images/comp08_6.jpg)

This prints the following:

![](images/comp08_7.jpg)

As mentioned previously, this serves as a good test for the correctness of the implementation of `AssetAllocDiscrete`.
