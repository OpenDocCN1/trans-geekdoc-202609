u and k. The second randomness property (R2) states that the distribution of runs is as expected in a random sequence.

The third randomness property is of a different nature.

# 16.12 Definition.

Let $\mathcal{S}_1 = (a_n)$ and $\mathcal{S}_2 = (b_n)$ be sequences, defined over the same alphabet, and periodic with the same period $\rho$. Define $\epsilon$, where

$$\epsilon(x, y) = \begin{cases} +1 \in \mathbb{R} & \text{if } x = y \\ -1 \in \mathbb{R} & \text{if } x \neq y. \end{cases}$$

The correlation function $C(\tau)$, $\tau = 0,1,\dots,\rho - 1$ is defined by

$$C(\tau) = \frac{1}{\rho} \cdot \sum \epsilon(a_n, b_{n+\tau}) = \frac{1}{\rho} \cdot \sum_n (-1)^{a_n + b_{n+\tau}}$$

where the sum is over a full period. If $\mathcal{S}_1 = \mathcal{S}_2$, then $C(\tau)$ is the **autocorrelation function** of our periodic sequence.

The autocorrelation $C(\tau)$ certainly satisfies $-1 \le C(\tau) \le 1$. For $\tau = 0$ (the **in-phase autocorrelation**) it is maximal: $C(0) = 1$. In general, $C(\tau)$ is small if the sequence and its shift disagree in many coordinates. It may be considered as typical of random sequences that the **out-of-phase autocorrelation** $C(\tau)$, $\tau > 0$ is close to being constant. The difference of $\mathcal{S}$ and a cyclic shift is a nonzero element of the code $\mathcal{C}$. It therefore has weight $(q - 1)q^{r-1}$. As $\mathcal{S}$ and its shift agree in precisely $q^{r-1} - 1$ positions, it follows that $C(\tau) = (q^{r-1} - 1) - (q - 1)q^{r-1}/(q^r - 1) = (-q^r + 2 \cdot q^{r-1} - 1)/(q^r - 1)$, when $\tau \neq 0$.

# 16.13 Proposition.

Let $\mathcal{S}$ be a maximum length LSRS. Then the out-of-phase autocorrelation of $\mathcal{S}$ is

$$C(\tau) = \frac{-q^r + 2 \cdot q^{r-1} - 1}{q^r - 1}, \quad 0 < \tau < q^r - 1.$$

In particular the following is satisfied:
(R3) The autocorrelation of $\mathcal{S}$ is two valued.

# Extremal correlation properties

Families of sequences with low correlation have applications in communications and cryptography; see the survey article by Helleseth and Kumar [110]. Let $(a_n) = (\operatorname{tr}(\epsilon^n u))$ be an LSRS of period $N = 2^r - 1$. Consider a **decimation** of this sequence: $(b_n)$, where $b_n = a_{tn}$ for some $t$ coprime to $N$. The correlation $C(\tau)$ of these sequences can be expressed in terms of the