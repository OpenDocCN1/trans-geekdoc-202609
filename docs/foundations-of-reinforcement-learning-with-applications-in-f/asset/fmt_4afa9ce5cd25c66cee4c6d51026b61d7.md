
$$\\begin{array}{r} \\left. \\mathbf{\\mathbf{b}}\\leftarrow\\mathbf{\\mathbf{b}} + \\phi(s\_{i},a\_{i}) \\cdot r\_{i} \\right. \\\\ \\end{array}$$  

With Sherman-Morrison incremental inverse, we can reduce the computational complexity from `O(m³)` to `O(m²)`.

This solved `w`^(\*) defines an updated `Q`-Value Function as follows:

$$\\begin{array}{r} {Q(s,a;\\mathbf{\\mathbf{w}}^{\*}) = \\phi{(s,a)}^{T} \\cdot \\mathbf{\\mathbf{w}}^{\*} = {\\sum\\limits\_{j = 1}^{m}\\phi\_{j}}(s,a) \\cdot w\_{j}^{\*}} \\\\ \\end{array}$$  

This defines an updated, improved deterministic policy `π`[*D*]^′ (serving as the `Deterministic Target Policy` for the next iteration of GPI):

$$\\begin{array}{r} {\\pi\_{D}^{\\prime}(s) = \\text{arg}\\,\\text{max}\_{a}Q(s,a;\\mathbf{\\mathbf{w}}^{\*})\\text{~for~all~}s \\in \\mathcal{N}} \\\\ \\end{array}$$  

This least-squares solution of `w`^(\*) (Prediction) is known as Least-Squares Temporal Difference for Q-Value, abbreviated as `LSTDQ`. Thus, LSPI is GPI with LSTDQ and greedy policy improvements. Note how LSTDQ in each iteration re-uses the same data 𝒟, i.e., LSPI does experience-replay.

We should point out here that the LSPI algorithm we described above should be considered as the `standard variant` of LSPI. However, we can design several other variants of LSPI, in terms of how the experiences data is sourced and used. Firstly, we should note that the experiences data 𝒟 essentially provides the behavior policy for Q-Learning (along with the consequent reward and next state transition). In the `standard variant` we described above, since 𝒟 is provided from an external source, the behavior policy that generates this data 𝒟 must come from an external source. It doesn't have to be this way—we could generate the experiences data from a behavior policy derived from the Q-Value estimates produced by LSTDQ (e.g., `ϵ`-greedy policy). This would mean the experiences data used in the algorithm is not a fixed, finite data set, rather a variable, incrementally-produced data set. Even if the behavior policy was external, the data set 𝒟 might not be a fixed finite data set—rather, it could be made available as an on-demand, variable data stream. Furthermore, in each iteration of GPI, we could use a subset of the experiences data made available until that point of time (rather than the approach of the standard variant of LSPI that uses all of the available experiences data). If we choose to sample a subset of the available experiences data, we might give more sampling-weightage to the more recently generated data. This would especially be the case if the experiences data was being generated from a policy derived from the Q-Value estimates produced by LSTDQ. In this case, we would leverage the `ExperienceReplayMemory` class we'd written earlier.

Next, we write code to implement the `standard variant` of LSPI we described above. First, we write a function to implement LSTDQ. As described above, the inputs to LSTDQ are the experiences data 𝒟 (transitions in the code below) and a deterministic target policy `π`[*D*] (`target_policy` in the code below). Since we are doing a linear function approximation, the input also includes a set of features, described as functions of state and action (`feature_functions` in the code below). Lastly, the inputs also include the discount factor `γ` and the numerical control parameter `ϵ`. The code below should be fairly self-explanatory, as it is a straightforward extension of LSTD (implemented in function `least_squares_td` earlier). The key differences are that this is an estimate of the Action-Value (Q-Value) function, rather than the State-Value Function, and the target used in the least-squares calculation is the Q-Learning target (produced by the `target_policy`).

![](images/comp13_10.jpg)

Now we are ready to write the standard variant of LSPI. The code below is a straightforward implementation of our description above, looping through the iterations of GPI, yielding the Q-Value `LinearFunctionApprox` after each iteration of GPI.

![](images/comp13_11.jpg)

The above code is in the file `rl/td.py`.

### 13.5.1 Saving Your Village from a Vampire

Now we consider a Control problem we'd like to test the above LSPI algorithm on. We call it the Vampire problem that can be described as a good old-fashioned bedtime story, as follows:

> *A village is visited by a vampire every morning who uniform-randomly eats 1 villager upon entering the village, then retreats to the hills, planning to come back the next morning. The villagers come up with a plan. They will poison a certain number of villagers each night until the vampire eats a poisoned villager the next morning, after which the vampire dies immediately (due to the poison in the villager the vampire ate). Unfortunately, all villagers who get poisoned also die the day after they are given the poison. If the goal of the villagers is to maximize the expected number of villagers at termination (termination is when either the vampire dies or all villagers die), what should be the optimal poisoning strategy? In other words, if there are n villagers on any day, how many villagers should be poisoned (as a function of n)?*

It is straightforward to model this problem as an MDP. The `State` is the number of villagers at risk on any given night (if the vampire is still alive, the `State` is the number of villagers and if the vampire is dead, the `State` is 0, which is the only `Terminal State`). The `Action` is the number of villagers poisoned on any given night. The `Reward` is zero as long as the vampire is alive, and is equal to the number of villagers remaining if the vampire dies. Let us refer to the initial number of villagers as `I`. Thus,

$$\\begin{array}{r} {\\mathcal{S} = \\left\\{ 0,1,\\ldots,I \\right\\},\\mathcal{T} = \\left\\{ 0 \\right\\}} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\mathcal{A}(s) = \\left\\{ 0,1,\\ldots,s - 1 \\right\\}\\text{~where~}s \\in \\mathcal{N}} \\\\ \\end{array}$$  

For all `s` ∈ 𝒩, for all `a` ∈ 𝒜(`s`),

$$\\begin{array}{l} {\\mathcal{P}\_{R}(s,a,r,s^{\\prime}) = \\left\\{ \\begin{array}{ll} \\frac{s - a}{s} & {\\text{~if~}r = 0\\text{~and~}s^{\\prime} = s - a - 1} \\\\ \\frac{a}{s} & {\\text{~if~}r = s - a\\text{~and~}s^{\\prime} = 0} \\\\ 0 & \\text{~otherwise~} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

It is rather straightforward to solve this with Dynamic Programming (say, Value Iteration) since we know the transition probabilities and rewards function and since the state and action spaces are finite. However, in a situation where we don't know the exact probabilities with which the vampire operates, and we only had access to observations on specific days, we can attempt to solve this problem with Reinforcement Learning (assuming we had access to observations of many vampires operating on many villages). In any case, our goal here is to test LSPI using this vampire problem as an example. So we write some code to first model this MDP as described above, solve it with value iteration (to obtain the benchmark, i.e., true Optimal Value Function and true Optimal Policy to compare against), then generate atomic experiences data from the MDP, and then solve this problem with LSPI using this stream of generated atomic experiences.

![](images/comp13_12.jpg)![](images/comp13_12_2.jpg)
