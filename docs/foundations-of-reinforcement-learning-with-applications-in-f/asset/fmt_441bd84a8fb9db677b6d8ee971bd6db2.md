
In this chapter, we cover RL Control algorithms that take a vastly different approach. These Control algorithms are still based on GPI, but the Policy Improvement of their GPI is not based on consulting the Q-Value Function, as has been the case with Control algorithms we covered in the previous two chapters. Rather, the approach in the class of algorithms we cover in this chapter is to directly find the Policy that fetches the “Best Expected Returns”. Specifically, the algorithms of this chapter perform a Gradient Ascent on “Expected Returns” with the gradient defined with respect to the parameters of a Policy function approximation. We shall work with a stochastic policy of the form `π(s, a; θ)`, with `θ` denoting the parameters of the policy function approximation `π`. So we are basically learning this parameterized policy that selects actions without consulting a Value Function. Note that we might still engage a Value Function approximation (call it `Q(s; a; w)`) in our algorithm, but its role is to only help learn the policy parameters `θ` and not to identify the action with the best action-value for each state. So the two function approximations `π(s, a; θ)` and `Q(s, a; w)` collaborate to improve the policy using gradient ascent (based on gradient of “expected returns” with respect to `θ`). `π(s, a; θ)` is the primary worker here (known as *Actor*) and `Q(s, a; w)` is the support worker (known as *Critic*). The Critic parameters `w` are optimized by minimizing a suitable loss function defined in terms of `Q(s, a; w)` while the Actor parameters `θ` are optimized by maximizing a suitable “Expected Returns” function. Note that we still haven't defined what this “Expected Returns” function is (we will do so shortly), but we already see that this idea is appealing for large/continuous action spaces where sweeping through actions is infeasible. We will soon dig into the details of this new approach to RL Control (known as *Policy Gradient*, abbreviated as PG)—for now, it's important to recognize the big picture that PG is basically GPI with Policy Improvement done as a *Policy Gradient Ascent*.

The contrast between the RL Control algorithms covered in the previous two chapters and the algorithms of this chapter actually is part of the following bigger-picture classification of learning algorithms for Control:

*   Value Function-based: Here we learn the Value Function (typically with a function approximation for the Value Function) and the Policy is implicit, readily derived from the Value Function (e.g., `ϵ`-greedy).

*   Policy-based: Here we learn the Policy (with a function approximation for the Policy), and there is no need to learn a Value Function.

*   Actor-Critic: Here we primarily learn the Policy (with a function approximation for the Policy, known as *Actor*), and secondarily learn the Value Function (with a function approximation for the Value Function, known as *Critic*).

PG Algorithms can be Policy-based or Actor-Critic, whereas the Control algorithms we covered in the previous two chapters are Value Function-based.

In this chapter, we start by enumerating the advantages and disadvantages of Policy Gradient Algorithms, state and prove the Policy Gradient Theorem (which provides the fundamental calculation underpinning Policy Gradient Algorithms), then go on to address how to lower the bias and variance in these algorithms, give an overview of special cases of Policy Gradient algorithms that have found success in practical applications, and finish with a description of Evolutionary Strategies that although technically not RL, resemble Policy Gradient algorithms and are quite effective in solving certain Control problems.

## 14.1 Advantages and Disadvantages of Policy Gradient Algorithms

Let us start by enumerating the advantages of PG algorithms. We've already said that PG algorithms are effective in large action spaces, especially high-dimensional or continuous action spaces, because in such spaces selecting an action by deriving an improved policy from an updating Q-Value function is intractable. A key advantage of PG is that it naturally *explores* because the policy function approximation is configured as a stochastic policy. Moreover, PG finds the best Stochastic Policy. This is not a factor for MDPs since we know that there exists an optimal Deterministic Policy for any MDP but we often deal with Partially-Observable MDPs (POMDPs) in the real-world, for which the set of optimal policies might all be stochastic policies. We have an advantage in the case of MDPs as well since PG algorithms naturally converge to the deterministic policy (the variance in the policy distribution will automatically converge to 0) whereas in Value Function-based algorithms, we have to reduce the `ϵ` of the `ϵ`-greedy policy by-hand and the appropriate declining trajectory of `ϵ` is typically hard to figure out by manual tuning. In situations where the policy function is a simpler function compared to the Value Function, we naturally benefit from pursuing Policy-based algorithms than Value Function-based algorithms. Perhaps the biggest advantage of PG algorithms is that prior knowledge of the functional form of the Optimal Policy enables us to structure the known functional form in the function approximation for the policy. Lastly, PG offers numerical benefits as small changes in `θ` yield small changes in `π`, and consequently small changes in the distribution of occurrences of states. This results in stronger convergence guarantees for PG algorithms relative to Value Function-based algorithms.

Now let's understand the disadvantages of PG Algorithms. The main disadvantage of PG Algorithms is that because they are based on gradient ascent, they typically converge to a local optimum whereas Value Function-based algorithms converge to a global optimum. Furthermore, the Policy Evaluation of PG is typically inefficient and can have high variance. Lastly, the Policy Improvements of PG happen in small steps and so, PG algorithms are slow to converge.

## 14.2 Policy Gradient Theorem

In this section, we start by setting up some notation, and then state and prove the Policy Gradient Theorem (abbreviated as PGT). The PGT provides the key calculation for PG Algorithms.

### 14.2.1 Notation and Definitions

Denoting the discount factor as `γ`, we shall assume either episodic sequences with 0 ≤ `γ` ≤ 1 or non-episodic (continuing) sequences with 0 ≤ `γ` < 1. We shall use our usual notation of discrete-time, countable-spaces, time-homogeneous MDPs although we can indeed extend PGT and PG Algorithms to more general settings as well. We lighten `𝒫(s, a, s′)` notation to `𝒫[s, s′]^(a)` and `ℛ(s, a)` notation to `ℛ[s]^(a)` because we want to save some space in the very long equations in the derivation of PGT.

We denote the probability distribution of the starting state as `p[0]:𝒩→[0,1]`. The policy function approximation is denoted as `π(s, a; θ) = ℙ[A[t] = a|S[t] = s; θ]`.

The PG coverage is quite similar for non-discounted, non-episodic MDPs, by considering the average-reward objective, but we won't cover it in this book.

Now we formalize the “Expected Returns” Objective `J(θ)`.

$$
\begin{array}{r}
{J(\theta) = \mathbb{E}_{\pi}\left[\sum_{t = 0}^{\infty}\gamma^{t} \cdot R_{t + 1}\right]}
\\
\end{array}
$$

Value Function `V^(π)(s)` and Action Value function `Q^(π)(s, a)` are defined as:

$$
\begin{array}{r}
{V^{\pi}(s) = \mathbb{E}_{\pi}\left[\sum_{k = t}^{\infty}\gamma^{k - t} \cdot R_{k + 1}|S_{t} = s\right]\text{~for~all~}t = 0,1,2,\ldots}
\\
\end{array}
$$
