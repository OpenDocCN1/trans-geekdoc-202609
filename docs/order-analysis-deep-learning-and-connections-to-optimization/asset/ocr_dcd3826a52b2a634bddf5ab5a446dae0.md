# 7.5 Specialization to Interval-Valued Inputs

**Proposition 7.7** *Let the assumptions of Theorem 7.5 be fulfilled. The point $	ilde{z}$ solves problem (7.17) with the minimal value 0 if and only if $	ilde{z}$ solves the optimization*

```
$$\min_{j=1}^p \left(y_j^l \text{pred}(z) - y_j^l\right)^2 + \left(y_j^u \text{pred}(z) - y_j^u\right)^2$$
$$$\text{subject to}$
$$$\underline{b}_i \le \bar{b}_i \text{ for all } i \in {1, \dots, m\}$$
$$$z := (w_1, \dots, w_n, \underline{b}_1, \dots, \underline{b}_m, \bar{b}_1, \dots, \bar{b}_m) \in \mathbb{R}^{n+2m}$$
(7.18)
```

The point $\tilde{z}$ solves problem (7.17) with the minimal value 0 if and only if $	ilde{z}$ is feasible, i.e., the constraints are satisfied,

```
$$\max \left\{|y_j^l \text{pred}(z) - y_j^l|, |y_j^u \text{pred}(z) - y_j^u|\right\ = 0 \text{ for all } j \in {1, \dots, p}.$\$
(7.19)
```

Equation (7.19) is equivalent to

```
$$\y_j^l \text{pred}(z) - y_j^l = 0 \text{ and } \bar{y}_j^u \text{pred}(z) - \bar{y}_j^u = 0 \text{ for all } j \in {1, \dots, p}.$\$
```

which can be written as

```
$$\left(\underline{y}_j^l \text{pred}(z) - \underline{y}_j^l\right)^2 + \left(\bar{y}_j^u \text{pred}(z) - \bar{y}_j^u\right)^2 = 0 \text{ for all } j \in {1, \dots, p}.$\$
```

This means that $\tilde{z}$ solves the optimization problem (7.18) with the minimal value 0.

By Proposition 7.6, the activation map $\mathcal{F}$ is not differentiable, and the objective function of the optimization problem (7.18) is not differentiable. For numerical computations, one could smooth the max term in Eq. (7.14) or choose some other suitable activation function.

Finally, we discuss a simple illustrative example with the dataset in Table 7.3. The inputs, as well as the true classes, are given in the form of intervals. The corresponding input sets are shown in Fig. 7.10. These sets are rectangles or, in special cases, squares. In the following, we work with only two neurons similar to Fig. 6.19, which only indicates the special case of real-valued inputs. We solve the constrained optimization problem (7.18) using fmincon implemented in MATLAB R2021a. This optimization problem is not easy to solve because there seem to be many local minima. Therefore, it makes sense to start the optimization method from different arbitrarily chosen starting points. The following optimal solution is the best among a large number of