
The above code is in the file `rl/chapter2/simple_inventory_mrp.py`). We encourage you to play with the inputs to `SimpleInventoryMRPFinite` in `__main__` and view the transition probabilities and rewards of the constructed Finite Markov Reward Process.

## 3.12 VALUE FUNCTION OF A MARKOV REWARD PROCESS

Now we are ready to formally define the main problem involving Markov Reward Processes. As we've said earlier, we'd like to compute the “expected accumulated rewards” from any non-terminal state. However, if we simply add up the rewards in a sampling trace following time step `t` as ${\sum\limits_{i = t + 1}^{\infty}R_{i}} = R_{t + 1} + R_{t + 2} + \ldots$, the sum would often diverge to infinity. So we allow for rewards accumulation to be done with a discount factor `γ` ∈ [0, 1]: We define the (random) `Return G[t]` as the “discounted accumulation of future rewards” following time step `t`. Formally,

$$
\begin{array}{r}
{G_{t} = {\sum\limits_{i = t + 1}^{\infty}\gamma^{i - t - 1}} \cdot R_{i} = R_{t + 1} + \gamma \cdot R_{t + 2} + \gamma^{2} \cdot R_{t + 3} + \ldots}
\\
\end{array}
$$

We use the above definition of `Return` even for a terminating sequence (say terminating at `t` = `T`, i.e., `S[T]` ∈ 𝒯), by treating `R[i]` = 0 for all `i` > `T`.

Note that `γ` can range from a value of 0 on one extreme (called “myopic”) to a value of 1 on another extreme (called “far-sighted”). “Myopic” means the Return is the same as Reward (no accumulation of future Rewards in the Return). With “far-sighted” (`γ` = 1), the Return calculation can diverge for continuing (non-terminating) Markov Reward Processes but “far-sighted” is indeed applicable for episodic Markov Reward Processes (where all random sequences of the process terminate). Apart from the Return divergence consideration, `γ` < 1 helps algorithms become more tractable (as we shall see later when we get to Reinforcement Learning). We should also point out that the reason to have `γ` < 1 is not just for mathematical convenience or computational tractability—there are valid modeling reasons to discount Rewards when accumulating to a Return. When Reward is modeled as a financial quantity (revenues, costs, profits etc.), as will be the case in most financial applications, it makes sense to incorporate time-value-of-money which is a fundamental concept in Economics/Finance that says there is greater benefit in receiving a dollar now versus later (which is the economic reason why interest is paid or earned). So it is common to set `γ` to be the discounting based on the prevailing interest rate ($\\gamma = \\frac{1}{1 + r}$, where `r` is the interest rate over a single time step). Another technical reason for setting `γ` < 1 is that our models often don't fully capture future uncertainty and so, discounting with `γ` acts to undermine future rewards that might not be accurate (due to future uncertainty modeling limitations). Lastly, from an AI perspective, if we want to build machines that acts like humans, psychologists have indeed demonstrated that human/animal behavior prefers immediate reward over future reward.

Note that we are (as usual) assuming the fact that the Markov Reward Process is time-homogeneous (time-invariant probabilities of state transitions and rewards).

As you might imagine now, we'd want to identify non-terminal states with large expected returns and those with small expected returns. This, in fact, is the main problem involving a Markov Reward Process—to compute the “Expected Return” associated with each non-terminal state in the Markov Reward Process. Formally, we are interested in computing the `Value Function`

$$
\begin{array}{r}
\left. V:\\mathcal{N}\\rightarrow{\mathbb{R}} \right.
\\
\end{array}
$$

defined as:

$$
\begin{array}{r}
{V(s) = \mathbb{E}\lbrack G_{t}|S_{t} = s\rbrack\text{~for~all~}s \\in \\mathcal{N},\text{~for~all~}t = 0,1,2,\ldots}
\\
\end{array}
$$

For the rest of the book, we will assume that whenever we are talking about a Value Function, the discount factor `γ` is appropriate to ensure that the Expected Return from each state is finite.

Now we show a creative piece of mathematics due to Richard Bellman. Bellman noted ([Bellman 1957b](#bib01.xhtml#refbib_9)) that the Value Function has a recursive structure. Specifically,

$$
\begin{aligned}
{V(s)} & {= \mathbb{E}\lbrack R_{t + 1}|S_{t} = s\rbrack + \gamma \cdot \mathbb{E}\lbrack R_{t + 2}|S_{t} = s\rbrack + \gamma^{2} \cdot \mathbb{E}\lbrack R_{t + 3}|S_{t} = s\rbrack + \ldots}
\\
& {= \mathcal{R}(s) + \gamma \cdot {\sum\limits_{s^{\prime} \in \mathcal{N}}{\mathbb{P}}}\lbrack S_{t + 1} = s^{\prime}|S_{t} = s\rbrack \cdot \mathbb{E}\lbrack R_{t + 2}|S_{t + 1} = s^{\prime}\rbrack}
\\
& {\,\,\, + \gamma^{2} \cdot {\sum\limits_{s^{\prime} \in \mathcal{N}}{\mathbb{P}}}\lbrack S_{t + 1} = s^{\prime}|S_{t} = s\rbrack{\sum\limits_{s^{\prime\prime} \in \mathcal{N}}{\mathbb{P}}}\lbrack S_{t + 2} = s^{\prime\prime}|S_{t + 1} = s^{\prime}\rbrack \cdot \mathbb{E}\lbrack R_{t + 3}|S_{t + 2} = s^{\prime\prime}\rbrack}
\\
& {\,\,\, + \ldots}
\\
& {= \mathcal{R}(s) + \gamma \cdot {\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,s^{\prime}) \cdot \mathcal{R}(s^{\prime}) + \gamma^{2} \cdot {\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,s^{\prime}){\sum\limits_{s^{\prime\prime} \in \mathcal{N}}\mathcal{P}}(s^{\prime},s^{\prime\prime}) \cdot \mathcal{R}(s^{\prime\prime}) + \ldots}
\\
& {= \mathcal{R}(s) + \gamma \cdot {\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,s^{\prime}) \cdot (\mathcal{R}(s^{\prime}) + \gamma \cdot {\sum\limits_{s^{\prime\prime} \in \mathcal{N}}\mathcal{P}}(s^{\prime},s^{\prime\prime}) \cdot \mathcal{R}(s^{\prime\prime}) + \ldots)}
\\
& {= \mathcal{R}(s) + \gamma \cdot {\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,s^{\prime}) \cdot V(s^{\prime})\text{~for~all~}s \in \mathcal{N}}
\\
\end{aligned}
$$

(3.1)

Note that although the transitions to random states `s′`, `s″`, … are in the state space of 𝒮 rather than 𝒩, the right-hand-side above sums over states `s′`, `s″`, … only in 𝒩 because transitions to terminal states (in 𝒯 = 𝒮 − 𝒩) don't contribute any reward beyond the rewards produced *before reaching* the terminal state.

We refer to this recursive equation (3.1) for the Value Function as the Bellman Equation for Markov Reward Processes. [Figure 3.7](#chapter3.xhtml#fig3_7) is a convenient visualization aid of this important equation. In the rest of the book, we will depict quite a few of these type of state-transition visualizations to aid with creating mental models of key concepts.

![Figure 3.7 Visualization of MRP Bellman Equation](images/fig3_7.jpg)

[Figure 3.7](#chapter3.xhtml#b3fig3_7) Visualization of MRP Bellman Equation

For the case of Finite Markov Reward Processes, assume 𝒮 = {`s[1]`,`s[2]`,…`s[n]`} and assume 𝒩 has `m` ≤ `n` states. Below we use bold-face notation to represent functions as column vectors and matrices since we have finite states/transitions. So, `V` is a column vector of length `m`, 𝒫 is an `m` × `m` matrix, and ℛ is a column vector of length `m` (rows/columns corresponding to states in 𝒩), so we can express the above equation in vector and matrix notation as follows:

$$
\begin{array}{r}
{\mathbf{V} = \mathcal{R} + \gamma\mathcal{P} \cdot \mathbf{V}}
\\
\end{array}
$$

Therefore,

$$
\begin{array}{r}
\left. \Rightarrow\mathbf{V} = {(\mathbf{I}_{m} - \gamma\mathcal{P})}^{- 1} \cdot \mathcal{R} \right.
\\
\end{array}
$$

(3.2)

where `I[m]` is the `m` × `m` identity matrix.
