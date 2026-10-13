
where the property `trace{AB} = trace{BA}` has been used. Thus, we can finally write

![Equation](images/B9780443292385000111/fx010.jpg) (5.46)

Let us now elaborate on it a bit more. Taking into account that `Q Q^T = I`, we get (see the chapter's Additional Material part)

```
J_{\text{exc},n} = \sum\limits_{i = 1}^{l}\lambda_{i}\left\lbrack \Sigma_{v,n - 1} \right\rbrack_{ii} = \mathbf{\lambda}^{T}\mathbf{s}_{n - 1},
```

![Equation](images/B9780443292385000111/si219.png) (5.47)

where `s[n]` is the vector of the diagonal elements of `\Sigma[v, n]` and obeys the difference equation in [(5.41)](#Chp005_177-248_B9780443292385000111.xhtml#deq77). Assuming that `\mu` has been chosen so that convergence is guaranteed, then for large values of `n` the *steady state* has been reached. In a more formal way, an online algorithm has reached the steady state if

```
\mathbb{E}[\mathbf{\theta}[n]] = \mathbb{E}[\mathbf{\theta}[n - 1]] = \text{Constant},
```

![Equation](images/B9780443292385000111/si220.png) (5.48)

```
\Sigma[\theta, n] = \Sigma[\theta, n - 1] = \text{Constant}.
```

![Equation](images/B9780443292385000111/si221.png) (5.49)

Thus, in steady state, we assume in Eq. [(5.41)](#Chp005_177-248_B9780443292385000111.xhtml#deq77) that `s[n] = s[n - 1]`; if this is exploited in Eq. [(5.47)](#Chp005_177-248_B9780443292385000111.xhtml#deq87) this leads to (Problem [5.9](#Chp005_177-248_B9780443292385000111.xhtml#o0050))

```
J_{\text{exc},\infty}: = \lim\limits_{n\rightarrow\infty}J_{\text{exc},n} \approx \frac{\mu\sigma_{\eta}^{2}\text{trace}\{\Sigma_{x}\}}{2 - \mu\text{trace}\{\Sigma_{x}\}},
```

![Equation](images/B9780443292385000111/si223.png) (5.50)

and for the misadjustment (since under our assumptions `J[min] = \sigma[\eta]^2`),
