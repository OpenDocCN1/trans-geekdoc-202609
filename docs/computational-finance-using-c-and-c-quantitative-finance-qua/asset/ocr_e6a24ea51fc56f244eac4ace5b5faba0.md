which means that:

```
$p(\{m_{t_1,t}}^{\bar{X}} \leqslant b, \bar{X}_t)|\bar{X}_0) = \frac{1}{\sqrt{2\pi}} exp\left(\frac{2vb}{\sigma^2}\right)\n\times \exp\left(\frac{(2b-\bar{X}_t+vt)^2}{2\sigma^2}\right) \quad (H.9.4)$
```

where as usual we take $\bar{X}_0=0$. So Eq. (H.9.4) gives the probability density for the Brownian motion which goes through the points $\bar{X}_0$ and $\bar{X}_t$ and has a minimum value which is less than or equal to $b$.

Instead of considering the complete path of $\bar{X}_t$ from $\bar{X}_0$ we can move the origin to the point $\bar{X}_{t_1}$, where $t_1 \leqslant t$. Substituting into Eq. (H.9.4) we then obtain:

```
$p(\{m_{t_1,t}}^{\bar{X}} \leqslant b, \bar{X}_t)|\bar{X}_{t_1}) = \frac{1}{\sqrt{2\pi(t-t_1)}} exp\left(\frac{2v(b-\ar{X}_t)}{\sigma^2}\right)\n\times \exp\left(\frac{(2(b-\ar{X}_{t_1})-(\bar{X}_t-\ar{X}_{t_1})+v(t-t_1))^2}{2\sigma^2(t-t_1)}\right)\n= \frac{1}{\sqrt{2\pi(t-t_1)}} exp\left(\frac{2v(b-\ar{X}_t)}{\sigma^2}\right)\n\times \exp\left(\frac{(2b-\bar{X}_t-\bar{X}_t+v(t-t_1))^2}{2\sigma^2(t-t_1)}\right)$
```

which can be re-expressed as:

```
$p(\{m_{t_1,t_2}}^{\bar{X}} \leqslant b, \bar{X}_{t_2})|\bar{X}_{t_1}) = \frac{1}{\sqrt{2\pi\Delta t}} exp\left(\frac{2v(b-\ar{X}_{t_2})}{\sigma^2}\right)\n\times \exp\left(\frac{(ar{X}_{t_1}+\bar{X}_{t_2}-2b-v\Delta t)^2}{2\sigma^2\Delta t}\right)$
```

where $t_2 \geqslant t_1$ and $\Delta t = t_2-t_1$.