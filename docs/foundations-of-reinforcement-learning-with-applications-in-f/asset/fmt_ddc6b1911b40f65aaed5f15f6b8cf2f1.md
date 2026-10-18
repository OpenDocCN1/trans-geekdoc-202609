
Finally, we run the `LSTD` algorithm on 10,000 transitions. Note that the Value Function of `RandomWalkMRP`, for `p` ≠ 0.5, is non-linear as a function of the integer states. So we use non-linear features that can approximate arbitrary non-linear shapes—a good choice is the set of (orthogonal) Laguerre Polynomials. In the code below, we use the first 5 Laguerre Polynomials (i.e., upto degree 4 polynomial) as the feature functions for the linear function approximation of the Value Function. Then we invoke the `LSTD` algorithm we wrote above to calculate the `LinearFunctionApprox` based on this batch of 10,000 transitions.

![](images/comp13_8.jpg)

[Figure 13.1](#chapter13.xhtml#fig13_1) depicts how the LSTD Value Function estimate (for 10,000 transitions) `lstd_vf` compares against Incremental Tabular TD Value Function estimate (for 10,000 transitions) `td_vf` and against the true value function `true_vf` (obtained using the linear-algebra-solver-based calculation of the MRP Value Function). We encourage you to modify the parameters used in the code above to see how it alters the results—specifically play around with `this_barrier`, `this_p`, `gamma`, `num_transitions`, the learning rate trajectory for Incremental Tabular TD, the number of Laguerre polynomials, and `epsilon`. The above code is in the file `rl/chapter12/random_walk_lstd.py`.

![Figure 13.1 LSTD and Tabular TD Value Functions](images/fig13_1.jpg)

[Figure 13.1](#chapter13.xhtml#b13fig13_1) LSTD and Tabular TD Value Functions

### 13.3.3 LSTD(λ)

Likewise, we can do `LSTD(λ)` using Eligibility Traces. Here we are given a fixed, finite number of trace experiences

$$
\begin{array}{r}
{\mathcal{D} = \lbrack(S_{i,0},R_{i,1},S_{i,1},R_{i,2},S_{i,2},\ldots,R_{i,T_{i}},S_{i,T_{i}})|1 \leq i \leq n\rbrack} \\
\end{array}
$$

Denote the Eligibility Traces of trace experience `i` at time `t` as **E**`[i, t]`. Note that the eligibility traces accumulate ∇[**w**]*V*(*s*; **w**) = *ϕ*(*s*) in each trace experience. When accumulating, the previous time step's eligibility traces is discounted by `λγ`. By setting the right-hand-side of Equation (13.1) to 0 (i.e., setting the update to **w** over all atomic experiences data to 0), we get:

$$
\begin{array}{r}
{{\sum\limits_{i = 1}^{n}\frac{1}{T_{i}}} \cdot {\sum\limits_{t = 0}^{T_{i} - 1}\mathbf{\mathbf{E}}_{i,t}} \cdot (\phi{(S_{i,t})}^{T} \cdot \mathbf{\mathbf{w}}^{\*} - (R_{i,t + 1} + \gamma \cdot \phi{(S_{i,t + 1})}^{T} \cdot \mathbf{\mathbf{w}}^{\*})) = 0} \\
\end{array}
$$

We can calculate the solution **w**^(\*) as **A**^(−1) ⋅ **b**, where the *m* × *m* Matrix **A** is accumulated at each atomic experience (*S*[*i*, *t*], *R*[*i*, *t* + 1], *S*[*i*, *t* + 1]) as:

$$
\begin{array}{r}
\left. \mathbf{\mathbf{A}}\leftarrow\mathbf{\mathbf{A}} + \frac{1}{T_{i}} \cdot \mathbf{\mathbf{E}}_{i,t} \cdot {(\phi(S_{i,t}) - \gamma \cdot \phi(S_{i,t + 1}))}^{T}\text{~(note~the~Outer-Product)} \right. \\
\end{array}
$$

and the *m*-Vector **b** is accumulated at each atomic experience (*S*[*i*, *t*], *R*[*i*, *t* + 1], *S*[*i*, *t* + 1]) as:

$$
\begin{array}{r}
\left. \mathbf{\mathbf{b}}\leftarrow\mathbf{\mathbf{b}} + \frac{1}{T_{i}} \cdot \mathbf{\mathbf{E}}_{i,t} \cdot R_{i,t + 1} \right. \\
\end{array}
$$

With Sherman-Morrison incremental inverse, we can reduce the computational complexity from *O*(*m*³) to *O*(*m*²).

### 13.3.4 Convergence of Least-Squares Prediction

Before we move on to Least-Squares for the Control problem, we want to point out that the convergence behavior of Least-Squares Prediction algorithms are identical to their counterpart Incremental RL Prediction algorithms, with the exception that Off-Policy LSMC does not have convergence guarantees. [Figure 13.2](#chapter13.xhtml#fig13_2) shows the updated summary table for convergence of RL Prediction algorithms (that we had displayed at the end of [Chapter 12](#chapter12.xhtml)) to now also include Least-Squares Prediction algorithms.

![Figure 13.2 Convergence of RL Prediction Algorithms](images/fig13_2.jpg)

[Figure 13.2](#chapter13.xhtml#b13fig13_2) Convergence of RL Prediction Algorithms

This ends our coverage of Least-Squares Prediction. Before we move on to Least-Squares Control, we need to cover Incremental RL Control with Experience-Replay as it serves as a stepping stone towards Least-Squares Control.

## 13.4 Q-LEARNING WITH EXPERIENCE-REPLAY

In this section, we cover Off-Policy Incremental TD Control with Experience-Replay. Specifically, we revisit the Q-Learning algorithm we covered in [Chapter 12](#chapter12.xhtml), but we tweak that algorithm such that the transitions used to make the Q-Learning updates are sourced from an experience-replay memory, rather than from a behavior policy derived from the current Q-Value estimate. While investigating the challenges with Off-Policy TD methods with deep learning function approximation, researchers identified two challenges:

1. The sequences of states made available to deep learning through trace experiences are highly correlated, whereas deep learning algorithms are premised on data samples being independent.
2. The data distribution changes as the RL algorithm learns new behaviors, whereas deep learning algorithms are premised on a fixed underlying distribution (i.e., stationary).

Experience-Replay serves to smooth the training data distribution over many past behaviors, effectively resolving the correlation issue as well as the non-stationary issue. Hence, Experience-Replay is a powerful idea for Off-Policy TD Control. The idea of using Experience-Replay for Off-Policy TD Control is due to the Ph.D. thesis of Long Lin ([Lin 1993](#bib01.xhtml#refbib_42)).

To make this idea of Q-Learning with Experience-Replay clear, we make a few changes to the `q_learning` function we had written in [Chapter 12](#chapter12.xhtml) with the following function `q_learning_experience_replay`.

![](images/comp13_9.jpg)

The key difference between the `q_learning` algorithm we wrote in [Chapter 12](#chapter12.xhtml) and this `q_learning_experience_replay` algorithm is that here we have an experience-replay memory (using the `ExperienceReplayMemory` class we had implemented earlier). In the `q_learning` algorithm, the (state, action, next_state, reward) 4-tuple comprising `TransitionStep` (that is used to perform the Q-Learning update) was the result of action being sampled from the behavior policy (derived from the current estimate of the Q-Value Function, e.g., `ϵ`-greedy), and then the `next_state` and `reward` being generated from the (state, action) pair using the `step` method of `mdp`. Here in `q_learning_experience_replay`, we don't use this 4-tuple `TransitionStep` to perform the update—rather, we append this 4-tuple to the `ExperienceReplayMemory` (using the `add_data` method), then we sample `mini_batch_sized` `TransitionSteps` from the `ExperienceReplayMemory` (giving more sampling weightage to the more recently added `TransitionSteps`), and use those 4-tuple `TransitionSteps` to perform the Q-Learning update. Note that these sampled `TransitionSteps` might be from old behavior policies (derived from old estimates of the Q-Value estimate). The key is that this algorithm re-uses atomic experiences that were previously prepared by the algorithm, which also means that it re-uses behavior policies that were previously constructed by the algorithm.

The argument `mini_batch_size` refers to the number of `TransitionSteps` to be drawn from the `ExperienceReplayMemory` at each step. The argument `weights_decay_half_life` refers to the half life of an exponential decay function for the weights used in the sampling of the `TransitionSteps` (the most recently added `TransitionStep` has the highest weight). With this understanding, the code should be self-explanatory.

The above code is in the file `rl/td.py`.

### 13.4.1 Deep Q-Networks (DQN) Algorithm
