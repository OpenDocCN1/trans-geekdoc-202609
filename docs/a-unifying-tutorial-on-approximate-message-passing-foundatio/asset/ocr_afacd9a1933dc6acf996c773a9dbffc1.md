from (A.60) and (A.61) that

```
\frac{1}{|\mu|} \left( 1 - \frac{\sigma^2}{\sigma^2 + \mu^2 \sigma_0^2} \right) \le |g'|\n\le \frac{1}{|\mu|} \left\{ 1 + \frac{\sigma^2}{\sigma^2 + \mu^2 \sigma_0^2} \left( \frac{\mu^2(b-a)^2}{4(\sigma^2 + \mu^2 \sigma_0^2)} - 1 \right) \right\}
```

on R. The expression on the right hand side is therefore a Lipschitz constant for g.

_Proof of Lemma 3.7._ Let \(\psi: \mathbb{R}^2 \to [0, \infty)\) be any measurable loss function, and fix \(s_1, s_2 \in (0, \infty)\) with \(s_1 > s_2\). Taking \(G' \sim N(0, s_1^2 - s_2^2)\), \(V \sim \pi\) and \(G \sim N(0, 1)\) to be jointly independent, we first claim that

```
R_{\pi, \psi}(s_2^{-2}) = \inf_g \mathbb{E}\{\psi(g(V + s_2G), V)\} = \inf_{\tilde{g}} \mathbb{E}\{\psi(\tilde{g}(V + s_2G, G'), V)\}, \tag{A.62}
```

where the infima are taken over all measurable \(g: \mathbb{R} \to \mathbb{R}\) and \(\tilde{g}: \mathbb{R}^2 \to \mathbb{R}\) respectively. Indeed, the first equality holds since \(V + s_2G = s_2(\sqrt{\rho}V + G)\) when \(\rho = s_2^{-2}\), and the middle expression is clearly bounded below by the final one, so it remains to prove the reverse inequality. For any fixed \(\tilde{g}: \mathbb{R}^2 \to \mathbb{R}\), we have

```
\tilde{\Psi}(a) := \mathbb{E}\{\psi(\tilde{g}(V + s_2G, a), V)\}\\n\ge \inf_g \mathbb{E}\{\psi(g(V + s_2G), V)\} = R_{\pi, \psi}(s_2^{-2})
```

for all \(a \in \mathbb{R}\), so it follows from Lemma B.7 that \(\mathbb{E}\{\psi(\tilde{g}(V + s_2G, G'), V)\} = \mathbb{E}(\tilde{\Psi}(G')) \ge R_{\pi, \psi}(s_2^{-2})\), and hence that (A.62) holds. Since \((V, V + s_2G + G') \stackrel{d}{=} (V, V + s_1G)\), we deduce that

```
R_{\pi, \psi}(s_2^{-2}) = \inf_{\tilde{g}} \mathbb{E}\{\psi(\tilde{g}(V + s_2G, G'), V)\}\\n\le \inf_g \mathbb{E}\{\psi(g(V + s_2G + G'), V)\}\\n= \inf_g \mathbb{E}\{\psi(g(V + s_1G), V)\} = R_{\pi, \psi}(s_1^{-2}).
```

In addition, arguing as above for (A.62), we have

```
R_{\pi, \psi}(s_1^{-2}) = \inf_g \mathbb{E}\{\psi(g(V + s_1G), V)\} \le \inf_{a \in \mathbb{R}} \mathbb{E}\{\psi(a, V)\}\\n= \inf_g \mathbb{E}\{\psi(g(G), V)\} = R_{\pi, \psi}(0).
```

Thus, \(\rho \mapsto R_{\pi, \psi}(\rho)\) is non-increasing on \([0, \infty)\).