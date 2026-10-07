Axiomatics, the Social Sciences, and the Gödel Phenomenon: A Toolkit 41

can view those sets as ordered $k$- and $k^*$-ples; $u$ and $v$ are recursive codings for them (see Rogers, 1967). $D_u(A)$ and $D_v^*(A)$ sets can be coded as follows: only finitely many elements of $A$ are queried during an actual converging computation with $y$; if $k'$ is the highest integer queried during such computation, and if $d_A \subset c_A$ is an initial segment of the characteristic function $c_A$, we take a standby for $D$ and $D^*$ the initial segment $d_A$ where the length $l(d_A) = k' + 1$.

We can effectively list all oracle machines with respect to a fixed $A$, so that we can compute its index (or Gödel number) $x$, and given $x$ we can recover the corresponding machine.

+   (2) Given an $A$-partial recursive function $\phi_x^A$, we form the oracle Turing machine that computes it. We then do the computation $\phi_{y,A}^A(y) = z$ that outputs $z$. The initial segment $d_{y,A}$ is obtained during the computation.

+   (3) The oracle machine is equivalent to an ordinary two-Turing machine that takes as input $(y, d_{y,A})$; $y$ is written on tape 1 $d_{y,A}$ is written on tape 2. When this new machine enters state $s_0$ it proceeds as the oracle machine. (For an ordinary computation, no converging computation enters $s_0$, and $d_{y,A}$ is empty.)

+   (4) The two-tape Turing machine can be made equivalent to a one-tape machine, where some adequate coding places on the single tape all the information about $(y, d_{y,A})$. When this third machine enters $s_0$ it scans $d_{y,A}$.

+   (5) We can finally use the standard map $\tau$ that codes $n$-ples one-to-one onto $\omega$ and add to the preceding machine a Turing machine that decodes the single natural number $\langle y, d_{y,A}\rangle$ into its components before proceeding to the computation.

Let $w$ be the index for that last machine; we note the machine $\phi_w$. If $x$ is the index for $\phi_x^A$, we write $w = \rho(x)$, where $\rho$ is the effective one-to-one procedure as described above maps indices for oracle machines into indices for Turing machines. Therefore,

```
$$\phi_x^A(y) = \phi_{\rho(x)}(\langle y, d_{y,A}\rangle)$
```