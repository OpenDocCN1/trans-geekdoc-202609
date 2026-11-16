which supposes that the arrival and departure process rates are upper bounded. Due to the fact that C is a constant, minimizing the upper bound on DPP is as follows:

$V\mathbb{E}[P(\alpha[t])] + \mathbb{E}[Q[t] \cdot (a(\alpha[t]) - b(\alpha[t]))].$ (10)

# Algorithm 1. Stabilized Time-Average Penalty Function Minimization

```
Initialize:
1: \( t \leftarrow 0 \);
2: \( Q[t] \leftarrow 0 \);
3: Decision Action: \( \forall \alpha[t] \in \mathcal{A} \)
Time-Average Penalty Function Minimization subject to Stability
4: while \( t \le T \) do // T: operation time
5: Observe \( Q[t] \);
6: \( T^* \leftarrow \infty \);
7: for \( \alpha[t] \in \mathcal{A} \) do
8: \( T \leftarrow V \cdot P(\alpha[t]) + Q[t] \cdot (a(\alpha[t]) - b(\alpha[t])) \);
9: if \( T \le T^* \) then
10: \( T^* \leftarrow T \);
11: \( \alpha^*[t+1] \leftarrow \alpha[t] \);
12: end if
13: end for
14: end while
```

Finally, the dynamic control action decision-making \(\alpha[t]\) in each unit time t for time-average penalty function \(P(\alpha[t])\) minimization subject to queue stability can be formulated as follows based on the Lyapunov optimization theory:

```
\(\alpha^*[t+1] \quad \underset{\alpha[t] \in \mathcal{A}}{\arg \min} [V \cdot P(\alpha[t]) + Q[t] \cdot (a(\alpha[t]) - b(\alpha[t]))]\) (11)
```

where A is the set of all possible control actions and \(\alpha^*[t+1]\) is the optimal control action decision-making for the next time slot.

In order to verify whether (11) works correctly or not, following two example cases can be considerable:

+   Case 1: Suppose Q[t] \(\approx \infty\). Then

```
\(\alpha^*[t+1] \quad \underset{\alpha[t] \in \mathcal{A}}{\arg \min} [V \cdot P(\alpha[t]) + Q[t] \cdot (a(\alpha[t]) - b(\alpha[t]))]\) (12)
```

```
\(\approx \underset{\alpha[t] \in \mathcal{A}}{\arg \min} [a(\alpha[t]) - b(\alpha[t])].\) (13)
```

Then, (13) shows that control action decision-making should works as follows, i.e., (i) the arrival process should be minimized, and (ii) the