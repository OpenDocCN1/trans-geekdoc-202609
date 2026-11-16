# 3.2.3 Power-law prior

Looking at Figure 3.7(c-d), it seems clear that movie grosses and poem length can be modeled by a **power law** distribution of the form \(p(T) \propto T^{-\gamma}\) for \(\gamma > 0\). (If \(\gamma > 1\), this is called a Pareto distribution, see **??**.) Power-laws are characterized by having very **long tails**. This captures the fact that most movies make very little money, but a few blockbusters make a lot. The number of lines in various poems also has this shape, since there are a few epic poems, such as Homer's _Odyssey_, but most are short, like haikus. Wealth has a similarly skewed distribution in many countries, especially in plutocracies such as the USA (see e.g., `inequality.org`).

In the case of a power-law prior, \(p(T) \propto T^{-\gamma}\), we can compute the posterior median analytically. We have

```
p(t) \propto \int_t^\infty T^{-(\gamma+1)} dT = -\frac{1}{\gamma} T^{-\gamma}|_t^\infty = \frac{1}{\gamma} t^{-\gamma} \quad (3.16)
```

Hence the posterior becomes

```
p(T|t) = \frac{T^{-(\gamma+1)}}{\frac{1}{\gamma} t^{-\gamma}} = \frac{\gamma t^\gamma}{T^{\gamma+1}} \quad (3.17)
```

for values of \(T \ge t\). We can derive the posterior median as follows:

```
p(T > T_M|t) = \int_{T_M}^\infty \frac{\gamma t^\gamma}{T^{\gamma+1}} dT = - \left( \frac{t^\gamma}{T} \right) \big|_{T_M}^\infty = \left( \frac{t}{T_M} \right)^\gamma \quad (3.18)
```

Solving for \(T_M\) such that \(P(T > T_M|t) = 0.5\) gives \(T_M = 2^{1/\gamma} t\).

This is plotted in Figure 3.8 (bottom middle). We see that the predicted duration is some constant multiple of the observed duration. For the particular value of \(\gamma\) that best fits the empirical distribution of movie grosses, the optimal prediction is about 50% larger than the observed quantity. So if we observe that a movie has made $40M to date, we predict that it will make $60M in total.

As Griffiths and Tenenbaum point out, this rule is inappropriate for quantities that follow a Gaussian prior, such as people's ages. As they write, "Upon meeting a 10-year-old girl and her 75-year-old grandfather, we would never predict that the girl will live a total of 15 years (\(1.5 \times 10\)) and that the grandfather will live to be 112 (\(1.5 \times 75\))." This shows that people implicitly know what kind of prior to use when solving prediction problems of this kind.

# 3.2.4 Erlang prior

Looking at Figure 3.7(e), it seems clear that the number of years a US Representative is approximately modeled by a gamma distribution (**??**). Griffiths and Tenenbaum use a special case of the Gamma distributon, where the shape parameter is \(a = 2\); this is known as the **Erlang distribution**:

```
p(T) = \text{Ga}(T|2, 1/\beta) \propto T e^{-T/\beta} \quad (3.19)
```

For the Erlang prior, we can also compute the posterior median analytically. We have

```
p(t) \propto \int_t^\infty \exp(-T/\beta) dT = -\beta \exp(-T/\beta) \big|_t^\infty = \beta \exp(-t/\beta) \quad (3.20)
```

so the posterior has the form

```
p(T|t) = \frac{\exp(-T/\beta)}{\beta \exp(-t/\beta)} = \frac{1}{\beta} \exp(-(T-t)/\beta) \quad (3.21)
```

for values of \(T \ge t\). We can derive the posterior median as follows:

```
p(T > T_M|t) = \int_{T_M}^\infty \frac{1}{\beta} \exp(-(T-t)/\beta) dT = - \exp(-(T-t)/\beta) \big|_{T_M}^\infty = \exp(-(T_M-t)/\beta) \quad (3.22)
```

Solving for \(T_M\) such that \(p(T > T_M|t) = 0.5\) gives \(T_M = t + \beta \log 2\).

This is plotted in Figure 3.8 (bottom right). We see that the best guess is simply the observed value plus a constant, where the constant reflects the average term in office.