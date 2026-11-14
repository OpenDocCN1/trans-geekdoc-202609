![](bbox=[0.25, 0.1, 0.8, 0.32])

Starting from an initial policy \(\pi_0\), policy iteration alternates between policy evaluation (\(E\)) and improvement (\(I\)) steps, as illustrated below:

```
\(\pi_0 \xrightarrow{E} V_{\pi_0} \xrightarrow{I} \pi_1 \xrightarrow{E} V_{\pi_1} \dots \xrightarrow{I} \pi_* \xrightarrow{E} V_*\)
```

The algorithm stops at iteration \(k\), if the policy \(\pi_k\) is greedy with respect to its own value function \(V_{\pi_k}\). In this case, the policy is optimal. Since there are at most \(|\mathcal{A}|^{|\mathcal{S}|}\) deterministic policies, and every iteration strictly improves the policy, the algorithm must converge after finite iterations.

In PI, we alternate between policy evaluation (which involves multiple iterations, until convergence of \(V_\pi\)), and policy improvement. In VI, we alternate between one iteration of policy evaluation followed by one iteration of policy improvement (the "max" operator in the update rule). In generalized policy improvement, we are free to intermix any number of these steps in any order. The process will converge once the policy is greedy wrt its own value function.

Note that policy evaluation computes \(V_\pi\) whereas value iteration computes \(V_*\). This difference is illustrated in Figure 34.14, using a backup diagram. Here the root node represents any state \(s\), nodes at the next level represent state-action combinations (solid circles), and nodes at the leaves representing the set of possible resulting next state \(s'\) for each possible action. In the former case, we average over all actions according to the policy, whereas in the latter, we take the maximum over all actions.

# 34.6.3 Linear programming

While dynamic programming is effective and popular, linear programming (LP) provides an alternative that finds important uses, such as in off-policy RL (Section 35.5). The primal form of LP is given by

```
\(\min_V \sum_s p_0(s)V(s) \quad \text{s.t.} \quad V(s) \ge R(s,a) + \gamma \sum_{s'} p_T(s'|s,a)V(s), \quad \forall(s,a) \in \mathcal{S} \times \mathcal{A}\)
```

where \(p_0(s) > 0\) for all \(s \in \mathcal{S}\), and can be interpreted as the initial state distribution. It can be verified that any \(V\) satisfying the constraint in Equation (34.92) is optimistic [Put94], that is, \(V \ge V_*\). When the objective is minimized, the solution \(V\) will be "pushed" to the smallest possible, which is \(V_*\). Once \(V_*\) is found, any action \(a\) that makes the constraint tight in state \(s\) is optimal in that state.