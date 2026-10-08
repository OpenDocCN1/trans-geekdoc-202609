# # Appendix H:
Brownian motion: more results

# ## H.1 Some results concerning Brownian motion

Here we will prove some facts concerning Brownian motion
If the Brownian motion has zero drift then:

```
$dX_t = \sigma \sqrt{dt} dZ_t, \quad dZ_t \sim N(0,1) \quad (H.1.1)$
```

and

```
$P(m_t^x \le b, X_t \ge x) = N_1(\frac{2b-x}{\sqrt{t}}) \quad (H.1.2)$
```

where $m_t^X$ denotes the minimum value of $X_t$ over the time interval $[0, t]$, $b \le 0$, and $x \ge 0$.
When the Brownian motion has nonzero drift

```
$d\bar{X}_t = v dt + \sigma \sqrt{dt} dZ_t, \quad d\bar{Z}_t \sim N(0,1) \quad (H.1.3)$
```

and the following equations are satisfied by $m_t^{ar{X}}$ and $\bar{X}_t:$

```
$P(\bar{X}_t \le K) = N_1(\frac{K-vt}{\sqrt{t}}) \quad (H.1.4)$
```

```
$P(\bar{X}_t \ge K) = N_1(\frac{vt-K}{\sqrt{t}}) \quad (H.1.5)$
```

```
$P(m_t^{ar{X}} \le b, \bar{X}_t \ge x) = \exp(\frac{2vb}{\sigma^2})N_1(\frac{2b-x+vt}{\sqrt{t}}) \quad (H.1.6)$
```

```
$P(m_t^{ar{X}} \ge b, \bar{X}_t \ge x) = N_1(\frac{vt-x}{\sqrt{t}}) - \exp(\frac{2vb}{\sigma^2})N_1(\frac{2b-x+vt}{\sqrt{t}}) \quad (H.1.7)$
```

```
$P(m_t^{ar{X}} \le b) = N_1(\frac{b-vt}{\sqrt{t}}) + \exp(\frac{2vb}{\sigma^2})N_1(\frac{b+vt}{\sqrt{t}}) \quad (H.1.8)$
```

```
$P(m_t^{ar{X}} \ge b) = N_1(\frac{vt-b}{\sqrt{t}}) - \exp(\frac{2vb}{\sigma^2})N_1(\frac{b+vt}{\sqrt{t}}) \quad (H.1.9)$
```

where $K$ is a constant, $\bar{X} \ge 0$, $b \le 0$, and **P(condition)** denotes the probability associated with the appropriate condition, i.e., $\bar{X}_t \ge K, m_t^{ar{X}} \ge b, \bar{X}_t \ge x$, etc.