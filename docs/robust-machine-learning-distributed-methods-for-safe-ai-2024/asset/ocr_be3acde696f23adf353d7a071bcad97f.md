Substituting from (5.5) in (5.7), we obtain that

\[
\|F(z_1,\ldots,z_n)-\bar v_S\|^2 \le \frac{8f}{n-f}\cdot\frac{\kappa+1}{|S|}\sum_{i\in S}\|v_i-\bar v_S\|^2.
\]

This completes the proof.

Recall that the lower bound for the robustness coefficient $\kappa$ is $\frac{f}{n-2f}\in O_n\left(\frac{f}{n}\right)$ (see Appendix C.1). This observation, in conjunction with Theorem 5.1, implies that if $F$ has a robustness coefficient $\kappa\in O_n(1)$, the two-step aggregation rule $F'=F\circ\mathrm{NNM}$ has an order-optimal robustness coefficient $\kappa'\in O_n\left(\frac{f}{n}\right)$. Note that the condition $\kappa\in O_n(1)$ is fairly general, thereby incorporating many standard robust aggregation rules, including those presented in Chap. 4. Specifically, if there exists a real value $\nu>0$ such that $n\ge(2+\nu)f$, then all the aforementioned aggregation rules (with parameter $q=f$) are $(f,\kappa)$-robust with $\kappa\in O_n(1)$. Hence, composing any of the aggregation rules from Chap. 4 with NNM yields an (order-)optimal robust averaging. Table 5.1 presents the values for $\kappa'$ obtained upon composing different aggregation rules with NNM. Even though CWTM achieves an order-optimal robustness coefficient, i.e., $\kappa\in O_n\left(\frac{f}{n}\right)$, without the use of NNM, the use of NNM significantly improves the empirical performance of CWTM.

**Table 5.1** List of robustness coefficients $\kappa'$ for robust aggregation rules from Chap. 4 when composed with NNM. The values are computed by applying Theorem 5.1. The last column provides the order of $\kappa'$ assuming that there exists a real value $\nu>0$ such that $n\ge(2+\nu)f$.

| Aggregation rule | Robustness coefficient $\kappa'$ | $\kappa'$ when $n\ge(2+\nu)f$ |
|---|---|---|
| CWMed | $\frac{8f}{n-f}\left(4\left(1+\frac{f}{n-2f}\right)^2+1\right)$ | $O_\star\left(\frac{f}{n}\right)$ |
| GeoMed | $\frac{8f}{n-f}\left(4\left(1+\frac{f}{n-2f}\right)^2+1\right)$ |  |
| CWTM$_f$ | $\frac{8f}{n-f}\left(\frac{6f}{n-2f}\left(1+\frac{f}{n-2f}\right)+1\right)$ |  |
| Multi-Krum$_{f,1}$ | $\frac{8f}{n-f}\left(6\left(1+\frac{f}{n-2f}\right)+1\right)$ |  |