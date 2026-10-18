
# Value Functions and Bellman Equations

Perhaps the most important concept we want to highlight in this entire book is the idea of a `Value Function` and how we can compute it in an efficient manner with either `Planning` or `Learning` algorithms. The Value Function `V^π:𝒮→ℝ` for a given (fixed) policy `π` is defined as:

$$
\begin{array}{r} {V^{\pi}(s) = \mathbb{E}_{\pi,p}\lbrack G_{t}|S_{t} = s\rbrack\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

The intuitive way to understand Value Function is that it tells us how much “accumulated future reward” (i.e., `Return`) we expect to obtain from a given state. The randomness under the expectation comes from the uncertain future states and rewards the Agent is going to see (based on the function `p`), upon taking future actions prescribed by the policy `π`. The key in evaluating the Value Function for a given policy is that it can be expressed recursively, in terms of the Value Function for the next time step's states. In other words,

$$
\begin{array}{r} {V^{\pi}(s) = {\sum\limits_{r,s^{\prime}}p}(r,s^{\prime}|s,\pi(s)) \cdot (r + \gamma \cdot V^{\pi}(s^{\prime}))\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

This equation says that when the Agent follows a deterministic policy `π`, in a given state `s`, it takes an action `a = π(s)`, then sees a random next state `s'` and a random reward `r`, so `V^π(s)` can be broken into the expectation of `r` (immediate next step's expected reward) and the remainder of the future expected accumulated rewards (which can be written in terms of the expectation of `V^π(s')`). We won't get into the details of how to solve this recursive formulation in this chapter (will cover this in great detail in future chapters), but it's important for you to recognize for now that this recursive formulation is the key to evaluating the Value Function for a given policy.

However, evaluating the Value Function for a given policy is not the end goal—it is simply a means to the end goal of evaluating the `Optimal Value Function` (from which we obtain the `Optimal Policy`). The Optimal Value Function `V*:𝒮→ℝ` is defined as:

$$
\begin{array}{r} {V^{*}(s) = \max_{\pi}V^{\pi}(s)\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

The good news is that even the Optimal Value Function can be expressed recursively, as follows:

$$
\begin{array}{r} {V^{*}(s) = \max_{a}{\sum\limits_{r,s^{\prime}}p}(r,s^{\prime}|s,a) \cdot (r + \gamma \cdot V^{*}(s^{\prime}))\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

Furthermore, we can prove that there exists an Optimal Policy `π*` achieving `V*(s)` for all `s ∈ 𝒮` (the proof is constructive, which gives a simple method to obtain the function `π*` from the function `V*`). Specifically, this means that the Value Function obtained by following the optimal policy `π*` is the same as the Optimal Value Function `V*`, i.e.,

$$
\begin{array}{r} {V^{\pi^{*}}(s) = V^{*}(s)\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

There is a bit of terminology here to get familiar with. The problem of calculating `V^π(s)` (Value Function for a give policy) is known as the `Prediction` problem (since this amounts to statistical estimation of the expected returns from any given state when following a policy `π`). The problem of calculating the Optimal Value Function `V*` (and hence, Optimal Policy `π*`), is known as the `Control` problem (since this requires steering of the policy such that we obtain the maximum expected return from any state). Solving the Prediction problem is typically a stepping stone toward solving the (harder) problem of Control. These recursive equations for `V^π` and `V*` are known as the (famous) Bellman Equations (which you will hear a lot about in future chapters). In a continuous-time formulation, the Bellman Equation is referred to as the famous `Hamilton-Jacobi-Bellman (HJB)` equation.

The algorithms to solve the prediction and control problems based on Bellman equations are broadly classified as:

*   Dynamic Programming, a class of (in the language of A.I.) `Planning` algorithms.

*   Reinforcement Learning, a class of (in the language of A.I.) `Learning` algorithms.

Now let's talk a bit about the difference between Dynamic Programming and Reinforcement Learning algorithms. Dynamic Programming algorithms (which we cover a lot of in this book) assume that the agent knows of the transition probabilities `p` and the algorithm takes advantage of the knowledge of those probabilities (leveraging the Bellman Equation to efficiently calculate the Value Function). Dynamic Programming algorithms are considered to be `Planning` and not `Learning` (in the language of A.I.) because the algorithm doesn't need to interact with the Environment and doesn't need to learn from the (states, rewards) data stream coming from the Environment. Rather, armed with the transition probabilities, the algorithm can reason about future probabilistic outcomes and perform the requisite optimization calculation to infer the Optimal Policy. So it `plans` its path to success, rather than `learning` about how to succeed.

However, in typical real-world situations, one doesn't really know the transition probabilities `p`. This is the realm of Reinforcement Learning (RL). RL algorithms interact with the Environment, learn with each new (state, reward) pair received from the Environment, and incrementally figure out the Optimal Value Function (with the “trial and error” approach that we outlined earlier). However, note that the Environment interaction could be `real` interaction or `simulated` interaction. In the latter case, we do have a model of the transitions but the structure of the model is so complex that we only have access to samples of the next state and reward (rather than an explicit representation of the probabilities). This is known as a `Sampling Model` of the Environment. With access to such a sampling model of the environment (e.g., a robot learning on a simulated terrain), we can employ the same RL algorithm that we would have used when interacting with a real environment (e.g., a robot learning on an actual terrain). In fact, most RL algorithms in practice learn from sampling models of the environment. As we explained earlier, RL is essentially a “trial and error” learning approach and hence, is quite laborious and fundamentally inefficient. The recent progress in RL is coming from more efficient ways of learning the Optimal Value Function, and better ways of approximating the Optimal Value Function. One of the key challenges for RL in the future is to identify better ways of finding the balance between “exploration” and “exploitation” of actions. In any case, one of the key reasons RL has started doing well lately is due to the assistance it has obtained from Deep Learning (typically Deep Neural Networks are used to approximate the Value Function and/or to approximate the Policy Function). RL with such deep learning approximations is known by the catchy modern term `Deep RL`.

We believe the current promise of A.I. is dependent on the success of Deep RL. The next decade will be exciting as RL research will likely yield improved algorithms, and its pairing with Deep Learning will hopefully enable us to solve fairly complex real-world stochastic control problems.

# 1.9 OUTLINE OF CHAPTERS

The chapters in this book are organized into 4 modules as follows:

*   Module I: Processes and Planning Algorithms ([Chapters 3](#chapter3.xhtml) – [6](#chapter6.xhtml))

*   Module II: Modeling Financial Applications ([Chapters 7](#chapter7.xhtml) – [10](#chapter10.xhtml))

*   Module III: Reinforcement Learning Algorithms ([Chapters 11](#chapter11.xhtml) – [14](#chapter14.xhtml))

*   Module IV: Finishing Touches ([Chapters 15](#chapter15.xhtml) – [17](#chapter17.xhtml))
