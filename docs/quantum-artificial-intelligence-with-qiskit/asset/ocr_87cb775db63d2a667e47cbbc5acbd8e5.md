Table 8.1 Execution of a simple pure production system or sorting a string.

| Iteration | Working Memory | Conflict Set | Rule Fired |
|---|---|---||}{
| 0 | cdcab | 1, 6 | 1 |
| 1 | cdcab | 6 | 6 |
| 2 | dccba | | Halt |

+   4. $cb ightarrow cb$
5. $bd ightarrow db$
6. $cd ightarrow dc$

The production (rule) can fire if the precondition matches portion of the string in the working memory.

+   * $\gamma_i \in \Sigma$ is the initial state: *cdcab*
* $\gamma_g \in \Sigma$ is the goal state: *dccba*
* $\delta$ is the control function: random choice of a production

The execution is indicated in the Table 8.1.

# 8.2.1 Quantum Production System for Sorting a String

To port simple production systems into the quantum production system, we first represent the finite alphabet $\Sigma$ by two qubits and approximate a problem by reformulation of the rules without a precondition that has been tested.

+   * $\Sigma: a = |00>, b = |01>, c = |10>, d = |11>
* $W$ is the working memory. It represents a state of teen qubits $\gamma \in \Sigma$, two qubits represent a position $p_i$

```
$x_7x_6x_5x_4x_3x_2x_1x_0 = |p_5p_4p_3p_2p_1|$
```

+   - index [11]: $p_21 ightarrow p_12$
- index [10]: $p_32 ightarrow p_23$
- index [01]: $p_43 ightarrow p_34$
- index [00]: $p_54 ightarrow p_45$

At each step all four rules can be applied in parallel.

+   * $\gamma_i \in \Sigma$ is the initial state: *cdcab = |101100000|*