# APPENDIX: A PHASE TRANSITION IN THE DIFFUSION PROCESS

and the initialization condition

```
$$$p_t^{(0)} = 1-\epsilon/v, \quad (324)$
$$p_t^{(L)} = 1/v. \quad (325)$$
```

From $p_t^{(0)}$ and $p_t^{(l)}$, at layer $l$, the average probability of the correct value $p_t^{(l)}$ is given by

```
$$$p_t^{(l)} = \frac{p_t^{(l-1)} + (1-p_t^{(l-1)})}{v-1} \quad (326)$$
```

# C.2.1.3 Validity of the mean-field theory

Due to the randomness of the production rules, the messages $v_i(x)$, $v_j(x)$ are random variables that depend on the specific realization of the rules. Their fluctuations are not captured by the averages computed in Equation 321, we observe that $p_t^{(l)}$ and $p_t^{(l)}$ capture the average behavior of the messages at layer $l$. In Figure 44, the values of $v_i^{(l)}(x)$ are reported on the bottom 5 levels of a Random Hierarchical Model with $L=10, s=2, v=3, m=8$, and noise level $\epsilon=0.5$. At each layer $l$, the index $i$ of the nodes from $s$ to $l$ and for each of them, there are $v=3$ messages $v_i^{(l)}$ for each entry of the alphabet. At layer $l=0$, the messages $v_i^{(0)}$ are initialized according to Equation 285. After one iteration, at layer $l=1$, we observe that the largest messages at each node, those corresponding to the most probable features $x_i$, are spread around some mean value that is captured by the theoretical prediction of Equation 321. We observe also for the upper layers, the average behavior of the largest messages is well captured by the theory.

The comparison between the theory and the BP algorithm for every $\epsilon$ is reported in Figure 45 and Figure 46. The upward iteration is reported in Figure 45 and shows an excellent agreement with the prediction of Equation 321. In particular, from the input layer $l=0$ to the class variable $l=L$ ($L=10$ in Figure 45), the messages for the most probable features show a sharper transition at a threshold value $\epsilon^*$, which corresponds to the phase transition of the theoretical iteration in Equation 305 when $L \to \infty$. The downward iteration in Figure 46 shows that the theory also captures the trend in $\epsilon$ of the downward messages. However, we observe that the messages have large fluctuations around their mean value. The reason for this behavior is that, in the Random Hierarchical Model, there is a number $m$ of synonyms $(x_1, \dots, x_s)$ that code for the higher level feature $y$. Therefore, having perfect information on $y$ and $x_2, \dots, x_s$ is not enough to perfectly reconstruct the value of $x_1$, thereby resulting in large fluctuations of the messages at small noise