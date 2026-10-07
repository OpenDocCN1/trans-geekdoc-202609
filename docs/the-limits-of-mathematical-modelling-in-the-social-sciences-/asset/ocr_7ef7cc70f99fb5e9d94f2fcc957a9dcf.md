Axiomatics, the Social Sciences, and the Gödel Phenomenon: A Toolkit

# **Proposition 14.3.** *If $T$ is arithmetically sound, then for every $m \in \omega$ there is a sentence $\xi \in T$ such that $N \models \xi$ for no $k \leq n$ there is a $\Sigma_k$ sentence in PA demonstrably equivalent to $\xi$.*

**Proof.** The usual proof for PA is given in Rogers (1967, p. 321). However we give here a slightly modified argument that actually Proposition 13.8. First notice

```
$$\phi^{(m+1)} = \{x : \phi_x^{\phi^{(m)}}\}$
```

is recursively enumerable but not recursive in $\phi^{(m)}$. Therefore, $\phi^{(m+1)}$ isn’t recursively enumerable in $\phi^{(m)}$, but contains a proper $\phi^{(m)}$-recursively enumerable set. Let us take a look at those theorems.

We need a lemma: form the theory $T^{(m+1)}$ whose axioms are for $T$ plus a demonstrably infinite set of statements of the form “$n_0 \in \phi^{(n)}$, $n_1 \in \phi^{(n)}$, $\dots$” that describe $\phi^{(m)}$. Of course, this theory doesn’t have a recursively enumerable set of theorems. Then,

# **Lemma 14.4.** If $T^{(n+1)}$ is arithmetically sound, then $\phi_x^{\phi^{(m)}} \downarrow$ if and only

```
$T^{(m+1)} \models \exists x_1, \dots, x_n \in \omega p(\rho(z), \langle z, d_{y,\\phi^{(m)}} \rangle, x_1, \dots, x_n) = 0$.
```

**Proof.** Similar to the proof in the nonrelativistic case; see Machtey and Young (1979, p. 126 ff).

Therefore, we have that $\phi_x^{\phi^{(m)}} \downarrow$ and if only

```
$T^{(m+1)} \models \exists x_1, \dots, x_n \in \omega p(\rho(z), \langle z, d_{y,\\phi^{(m)}} \rangle, x_1, \dots, x_n) = 0$.
```

However, since $\phi^{(m+1)}$ isn’t recursively enumerable in $\phi^{(m)}$, then there will be an index $m_0(\phi^{(m)}) = \rho(z), \langle z, d_{y,\\phi^{(m)}} \rangle$ such that

```
$$N \models \exists x_1, \dots, x_n[p(\m_0, x_1, \dots, x_n)]^2 > 0$,
```

while it cannot be proved disprove within $T^{(m+1)}$. It is therefore demonstrably equivalent to a $\Pi_{m+1}$ assertion.

Now let $q(m_0(\phi^{(m)}), x_1, \dots) = p(m_0(\phi^{(m)}), x_1, \dots)^2$ be in Proposition 14.3. We have the following corollary.