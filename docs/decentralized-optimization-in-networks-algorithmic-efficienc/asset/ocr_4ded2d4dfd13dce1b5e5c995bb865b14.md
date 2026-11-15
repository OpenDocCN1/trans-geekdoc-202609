delves into comprehensive privacy analyses. Section 8.5 includes conducted simulation examples. Finally, Section 8.6 summarizes the findings. Additional proofs are included in the appendices.

Notation: The symbols \(1_m\) and \(0_m\) represent \(m\)-dimensional column vectors filled with ones and zeros, respectively. The transpose of vector \(x\) is denoted by \(x^{\mathrm{T}}\). The notation \(|\cdot|\) signifies the absolute value of a real number. For a random estimator \(\mathrm{y}\), \(\mathbb{P}[\mathrm{y}]\) and \(\mathbb{E}[\mathrm{y}]\) represent its probability and expectation, respectively. The vector \(\mathrm{e}_i=[0,\dots,1_i,\dots,0]^{\mathrm{T}}\) is defined as a standard basis vector. A function \(f\) is considered strictly convex if for any vectors \(c\) and \(d\), the inequality \(f(a c+(1-a) d)<a f(c)+(1-a) f(d)\) holds for all \(a \in(0,1)\). The term “almost surely” is abbreviated as a.s..

# 8.2 Problem description and algorithm construction

This section outlines the EDP and introduces the problem transformation. Subsequently, a privacy-protected decentralized random sleep algorithm is proposed.

# 8.2.1 Problem description

This study considers a network of \(m\) generators collaboratively solving the following EDP in smart grids:

```
\min_{p \in \mathbb{R}^m} J(p) = \sum_{i=1}^m J_i(p_i),
\text{s.t.} \sum_{i=1}^m p_i = \sum_{i=1}^m d_i = D,
p_i^{\min} \le p_i \le p_i^{\max}, \forall i = 1, ..., m,
(8.1)
```

where \(J_i : \mathbb{R}_{\ge 0} \to \mathbb{R}_{\ge 0}\), \(p=[p_1, p_2, ..., p_m]^{\mathrm{T}} \in \mathbb{R}^m\) with \(p_i \in \mathbb{R}_{\ge 0}\), \(D \in \mathbb{R}_{\ge 0}\), and \(d_i \in \mathbb{R}_{\ge 0}\). Define \(Pi=\{p^{\dagger} \in \mathbb{R} | p_i^{\min} \le p_i^{\dagger} \le p_i^{\max}\}\) and \(P=P_1 \times \dots \times P_m\). To ensure the feasibility of problem (8.1) and the reliable operation of smart grids, the total power demand satisfies \(\sum_{i=1}^m p_i^{\min} \le D \le \sum_{i=1}^m p_i^{\max}\). Let \(p^*=[p_1^*, p_2^*, ..., p_m^*]^{\mathrm{T}} \in \mathbb{R}^m\) be the optimal dispatch to (8.1).

Similar to many EDP studies [21,23,24,36], this chapter considers general convex cost functions that satisfy the following assumption.

**Assumption 8.1.** The function \(J_i : \mathbb{R} \to \mathbb{R}, i \in \mathcal{V}\), is strictly convex and continuously differentiable.

Assumption 8.1 implies that the EDP (8.1) is a convex problem with a unique optimal solution. The cost function considered here is similar to those in the literature [13,19,36], such as quadratic functions used for privacy analysis. Thus Assumption 8.1 is easily met.