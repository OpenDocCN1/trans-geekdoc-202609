We have thus shown that:

```
$P(W_t|W_{t_0}, W_{t_1}) = \frac{1}{\sqrt{2\pi}} \sqrt{\frac{t_1-t_0}{(t-t_0)(t_1-t)}} \exp\left\{-\frac{(W_t-\mu)^2}{2V}\right\$\n=\frac{1}{\sqrt{2\pi}V} \exp\left\{-\frac{(W_t-\mu)^2}{2V}\right\}$
```

Thus the conditional distribution of $W_t$ is a Gaussian with mean

```
$\mu = W_{t_0} \frac{t_1-t}{t_1-t_0} + W_{t_1} \frac{t-t_0}{t_1-t_0}$
```

and variance

```
$V = \frac{(t-t_0)(t_1-t)}{t_1-t_0}$
```

and we can obtain a variate $\widetilde{W}_t$ from this distribution by using:

```
$\widetilde{W}_t = W_{t_0} \frac{t_1-t}{t_1-t_0} + W_{t_1} \frac{t-t_0}{t_1-t_0} + \sqrt{\frac{(t-t_0)(t_1-t)}{t_1-t_0}}Z,\text{ where } Z \sim \text{N}(0,1)$
```