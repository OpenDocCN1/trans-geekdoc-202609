\sum_L \sum_S \psi_J(J, L, S) \sum_G \psi_L(L, G) \sum_H \psi_H(H, G, J) \sum_I \psi_S(S, I) \psi_I(I) \sum_D \psi_G(G, I, D) \sum_C \psi_C(C) \psi_D(D, C)
\underbrace{\dots}_{\tau_1(D)}
\sum_L \sum_S \psi_J(J, L, S) \sum_G \psi_L(L, G) \sum_H \psi_H(H, G, J) \sum_I \psi_S(S, I) \psi_I(I) \sum_D \psi_G(G, I, D) \tau_1(D)
\underbrace{\dots}_{\tau_2(G, I)}
\sum_L \sum_S \psi_J(J, L, S) \sum_G \psi_L(L, G) \sum_H \psi_H(H, G, J) \sum_I \psi_S(S, I) \psi_I(I) \tau_2(G, I)
\underbrace{\dots}_{\tau_3(G, S)}
\sum_L \sum_S \psi_J(J, L, S) \sum_G \psi_L(L, G) \sum_H \psi_H(H, G, J) \tau_3(G, S)
\underbrace{\dots}_{\tau_4(G, J)}
\sum_L \sum_S \psi_J(J, L, S) \sum_G \psi_L(L, G) \tau_4(G, J) \tau_3(G, S)
\underbrace{\dots}_{\tau_5(J, L, S)}
\sum_L \sum_S \psi_J(J, L, S) \tau_5(J, L, S)
\underbrace{\dots}_{\tau_6(J, L)}
\sum_L \tau_6(J, L)
\underbrace{\dots}_{\tau_7(J)}

Table 9.1: Eliminating variables from Figure 4.38 in the order C, D, I, H, G, S, L to compute P(J).

The above technique can be used to compute any marginal of interest, such as p(J) or p(J, H). To compute a conditional, we can take a ratio of two marginals, where the visible variables have been clamped to their known values (and hence don't need to be summed over). For example,

```
p(J = j|I = 1, H = 0) = \frac{p(J = j, I = 1, H = 0)}{\sum_{j'} p(J = j', I = 1, H = 0)} \qquad \text{(9.89)}
```

# 9.5.2 Computational complexity of VE

The running time of VE is clearly exponential in the size of the largest factor, since we have to sum over all of the corresponding variables. Some of the factors come from the original model (and are thus unavoidable), but new factors may also be created in the process of summing out. For example, in Table 9.1, we created a factor involving G, I, and S; but these nodes were not originally present together in any factor.

The order in which we perform the summation is known as the elimination order. This can have a large impact on the size of the intermediate factors that are created. For example, consider the ordering in Table 9.1: the largest created factor (beyond the original ones in the model) has size \(\tau_3\), corresponding to \(\tau_5(J, L, S)\). Now consider the ordering in Table 9.2: now the largest factors are \(\tau_1(I, D, L, J, H)\) and \(\tau_2(D, L, S, J, H)\), which are much bigger.