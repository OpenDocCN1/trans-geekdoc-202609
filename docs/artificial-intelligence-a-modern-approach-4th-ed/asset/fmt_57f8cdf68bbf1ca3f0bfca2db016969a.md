
This means that we have reduced reinforcement learning to a standard supervised learning problem in which each example is a (state, reward-to-go) pair. We have a lot of powerful algorithms for supervised learning, so this approach seems promising, but it ignores an important constraint: The utility of a state is determined by the reward and the expected utility of the successor states. More specifically, the utility values obey the Bellman equations for a fixed policy (see also [Equation (16.14)](#Chapter16-02.xhtml#eq16-14)):

$\\begin{matrix} {U\_{i}(s) = {\\sum\\limits\_{s'}\\left. P(s' \\middle| s,\\pi\_{i}(s))\\lbrack R(s,\\pi\_{i}(s),s') + \\gamma U\_{i}(s')\\rbrack. \\right.}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(23.2)} \\\\ \\end{matrix}$

By ignoring the connections between states, direct utility estimation misses opportunities for learning. For example, the second of the three trials given earlier reaches the state (3,2), which has not previously been visited. The next transition reaches (3,3), which is known from the first trial to have a high utility. The Bellman equation suggests immediately that (3,2) is also likely to have a high utility, because it leads to (3,3), but direct utility estimation learns nothing until the end of the trial. More broadly, we can view direct utility estimation as searching for `U` in a hypothesis space that is much larger than it needs to be, in that it includes many functions that violate the Bellman equations. For this reason, the algorithm often converges very slowly.

## 23.2.2 Adaptive dynamic programming

An adaptive dynamic programming (or ADP) agent takes advantage of the constraints among the utilities of states by learning the transition model that connects them and solving the corresponding Markov decision process using dynamic programming. For a passive learning agent, this means plugging the learned transition model `P(s' | s, π(s))` and the observed rewards `R(s, π(s), s')` into [Equation (23.2)](#Chapter23-02.xhtml#eq23-2) to calculate the utilities of the states. As we remarked in our discussion of policy iteration in [Chapter 16](#Chapter16-00.xhtml), these Bellman equations are linear when the policy `π` is fixed, so they can be solved using any linear algebra package.

> Adaptive dynamic programming

Alternatively, we can adopt the approach of modified policy iteration (see [page 568](#Chapter16-02.xhtml#page_568)), using a simplified value iteration process to update the utility estimates after each change to the learned model. Because the model usually changes only slightly with each observation, the value iteration process can use the previous utility estimates as initial values and typically converge very quickly.

Learning the transition model is easy, because the environment is fully observable. This means that we have a supervised learning task where the input for each training example is a state–action pair, `(s, a)`, and the output is the resulting state, `s'`. The transition model `P(s' | s, a)` is represented as a table and it is estimated directly from the counts that are accumulated in `N_{s' | s a}`. The counts record how often state `s'` is reached when executing `a` in `s`. For example, in the three trials given on [page 843](#Chapter23-02.xhtml#page_843), Right is executed four times in (3,3) and the resulting state is (3,2) twice and (4,3) twice, so `P((3,2) | (3,3), Right)` and `P((4,3) | (3,3), Right)` are both estimated to be ½.

The full agent program for a passive ADP agent is shown in [Figure 23.2](#Chapter23-02.xhtml#fig23-2). Its performance on the 4 × 3 world is shown in [Figure 23.3](#Chapter23-02.xhtml#fig23-3). In terms of how quickly its value estimates improve, the ADP agent is limited only by its ability to learn the transition model. In this sense, it provides a standard against which to measure any other reinforcement learning algorithms. It is, however, intractable for large state spaces. In backgammon, for example, it would involve solving roughly 10^20 equations in 10^20 unknowns.

![](images/Fig-330.jpg)

Figure 23.2 A passive reinforcement learning agent based on adaptive dynamic programming. The agent chooses a value for `γ` and then incrementally computes the `P` and `R` values of the MDP. The `POLICY-EVALUATION` function solves the fixed-policy Bellman equations, as described on [page 567](#Chapter16-02.xhtml#page_567).

![](images/Fig-331.jpg)

Figure 23.3 The passive ADP learning curves for the 4 × 3 world, given the optimal policy shown in [Figure 23.1](#Chapter23-02.xhtml#fig23-1). (a) The utility estimates for a selected subset of states, as a function of the number of trials. Notice that it takes 14 and 23 trials respectively before the rarely visited states (2,1) and (3,2) “discover” that they connect to the +1 exit state at (4,3). (b) The root-mean-square error (see Appendix A) in the estimate for `U(1, 1)`, averaged over 50 runs of 100 trials each.

## 23.2.3 Temporal-difference learning

Solving the underlying MDP as in the preceding section is not the only way to bring the Bellman equations to bear on the learning problem. Another way is to use the observed transitions to adjust the utilities of the observed states so that they agree with the constraint equations. Consider, for example, the transition from (1,3) to (2,3) in the second trial on [page 843](#Chapter23-02.xhtml#page_843). Suppose that as a result of the first trial, the utility estimates are `Uπ(1, 3) = 0.88` and `Uπ(2, 3) = 0.96`. Now, if this transition from (1,3) to (2,3) occurred all the time, we would expect the utilities to obey the equation

`U^π(1,3) = -0.04 + U^π(2,3)`,

so `Uπ(1, 3)` would be 0.92. Thus, its current estimate of 0.88 might be a little low and should be increased. More generally, when a transition occurs from state `s` to state `s'` via action `π(s)`,

we apply the following update to `Uπ(s)`:

$\\begin{matrix} \\left. U^{\\pi}(s)\\leftarrow U^{\\pi}(s) + \\alpha\\lbrack R(s,\\pi(s),s')\\, + \\,\\gamma U^{\\pi}(s') - U^{\\pi}(s)\\rbrack. \\right. & {\\,\\,\\,\\,\\,(23.3)} \\\\ \\end{matrix}$

> Temporal-difference

Here, `α` is the learning rate parameter. Because this update rule uses the difference in utilities between successive states (and thus successive times), it is often called the temporal-difference (TD) equation. Just as in the weight update rules from [Chapter 19](#Chapter19-00.xhtml) (e.g., [Equation (19.6)](#Chapter19-06.xhtml#eq19-6) on [page 698](#Chapter19-06.xhtml#page_698)), the TD term `R(s,π(s), s') + γU^π(s') − U^π(s)` is effectively an error signal, and the update is intended to reduce the error.

All temporal-difference methods work by adjusting the utility estimates toward the ideal equilibrium that holds locally when the utility estimates are correct. In the case of passive learning, the equilibrium is given by [Equation (23.2)](#Chapter23-02.xhtml#eq23-2). Now [Equation (23.3)](#Chapter23-02.xhtml#eq23-3) does in fact cause the agent to reach the equilibrium given by [Equation (23.2)](#Chapter23-02.xhtml#eq23-2), but there is some subtlety involved. First, notice that the update involves only the observed successor `s''`, whereas the actual equilibrium conditions involve all possible next states. One might think that this causes an improperly large change in `Uπ(s)` when a very rare transition occurs; but, in fact, because rare transitions occur only rarely, the average value of `Uπ(s)` will converge to the correct quantity in the limit, even if the value itself continues to fluctuate.
