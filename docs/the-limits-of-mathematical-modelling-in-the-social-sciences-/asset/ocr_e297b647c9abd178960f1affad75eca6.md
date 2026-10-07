# The Limits of Mathematical Modeling in the Social Sciences

Now a weaker version of Proposition 13.6 is as follows.

**Proposition 13.8.** If T is arithmetically sound, there is a polynomial expression over Z $p(x_1, \dots, x_n)$ such that $\mathbf{N} \models \forall x_1, \dots, x_n \in \omega \ p(x_1, \dots, x_n) > 0$,

```
$T 
ot\models \forall x_1, \dots, x_n \in \omega \ p(x_1, \dots, x_n) > 0$
```

and

```
$T 
ot\models \exists x_1, \dots, x_n \in \omega \ p(x_1, \dots, x_n) = 0$.
```

**Proof.** If $p(m, x_1, \dots, x_n)$, $m = 	au(q, r)$, is an universal polynomial with $	au$ being Cantor’s pairing function (see Rogers, 1967), then $\{m : \exists x_1 \dots \in \omega \ p(m, x_1, \dots) = 0\}$ is recursively enumerable but not recursive. Therefore there must be an $m_0$ such that $\forall x_1 \dots \in \omega (p(m_0, \dots))^2 > 0$.

**Proposition 13.9.** If PA is consistent and $\mathbf{N} \models 	ext{PA}$ is standard, and if $P$ is nontrivial then there is a term-expression $\zeta \in \mathcal{L}_{	ext{PA}}$ such that $\mathbf{N} \models P(\zeta)$ while $PA 
ot\models P(\zeta)$ and $PA 
ot\models 
eg P(\zeta)$.

**Proof.** $\zeta = \xi + r(x_1, \dots, x_n)_v$, for $r = 1-(q+1)$, $q$ as in Proposition 13.6 (or as $p$ in Proposition 13.8).

**Remark 13.10.** Therefore, every nontrivial arithmetical $P$ in theories from formalized arithmetic turns out to be undecidable. We can generalize that result to encompass other theories $T$ that include arithmetical; see below.

# 14. $	heta$ functions and the arithmetical hierarchy

**Definition 14.1.** The sentences $\xi, \zeta \in \mathcal{L}_T$ are demonstrably equivalent if and only if $T \vdash \xi \leftrightarrow \zeta$.

**Definition 14.2.** The sentence $\xi \in \mathcal{L}_T$ is arithmetically expressible if and only if there is an arithmetic sentence $\zeta$ such that $T \vdash \xi \leftrightarrow \zeta$.

Then, for $\mathbf{N} \models T$, a model makes it arithmetically sound.