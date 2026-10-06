# 88 CHAPTER | 4 European Options

$P(m^Z \le b|Z_{t_2}, Z_{t_1}),$

where $m^Z$ denotes the maximum of $Z$ over the time interval $[t_1, t_2]$.
The probability of $Z_{t_2}$ conditional on $Z_{t_1}$ is

```
$P(Z_{t_2}|Z_{t_1}) = \frac{1}{\sigma\sqrt{2\pi\Delta t}} \exp\left\{\frac{(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}ight\},$
```

where $\Delta t = t_2 - t_1$.
From Bayes, we know that

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) = \frac{P(\{m^Z \le b, Z_{t_2}\}|Z_{t_1})}{P(Z_{t_2}|Z_{t_1})}.$
```

We show in [Appendix H.1](#)

```
$P(\{m^Z \le b, Z_{t_2}\}|Z_{t_1}) \n= \frac{1}{\sigma\sqrt{2\pi\Delta t}} \exp\left(\frac{2v(b-Z_{t_1})^2}{\sigma^2}\right)\exp\left\frac{(Z_{t_2}+Z_{t_1}-2b-v\Delta t)^2}{2\sigma^2\Delta t}\right\},$
```

so

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) \n= \exp\left(\frac{2v(b-Z_{t_1})^2}{\sigma^2}\right)\exp\left\frac{(Z_{t_2}+Z_{t_1}-2b-v\Delta t)^2+(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}\right).$
```

We will now use algebra to simplify this expression.

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) \n= \exp\left(\frac{4v\Delta t(b-Z_{t_1})^2+(Z_{t_2}+Z_{t_1}-2b-v\Delta t)^2+(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}\right) \n= \exp\left(\frac{4v\Delta t(b-Z_{t_1})-(Z_{t_2}-Z_{t_1}-v\Delta t)^2+2(b-Z_{t_1}))^2+(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}\right) \n= \exp\left(\frac{4v\Delta t(b-Z_{t_1})+4(b-Z_{t_1})(Z_{t_2}-Z_{t_1}-v\Delta t)+4(b-Z_{t_1})^2}{2\sigma^2\Delta t}\right) \n= \exp\left(\frac{2(b-Z_{t_1})(b-Z_{t_2})}{\sigma^2\Delta t}\right).$
```

which finally yields

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) = \exp\left(\frac{2(\log(b)-\log(S_{t_1}))(\log(b)-\log(S_{t_2}))}{\sigma^2\Delta t}\right). (4.5.19)$
```

Equation (4.5.19) gives the probability of the option having been knocked out between times $t_1$ and $t_2$ even when the asset prices $S_{t_1}$ and $S_{t_2}$ are greater