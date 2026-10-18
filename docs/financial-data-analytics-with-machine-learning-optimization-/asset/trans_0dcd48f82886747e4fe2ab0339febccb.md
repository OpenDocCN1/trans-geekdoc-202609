

3. **Student's t-distribution:** 如果 $z \sim N(0, 1)$ 与 $x \sim \chi^2_\nu$ 独立，则 $t := \frac{z}{\sqrt{x/\nu}}$ 被称作服从具有 $\nu$ 个自由度的 $t$-分布 $t_\nu$。因此，如果 $y_1, \dots, y_n$ 是 iid $N(\mu, \sigma^2)$，则 $\frac{\sqrt{n}(\bar{y} - \mu)}{s_y} \sim t_{n-1}$；实际上，由于 $\bar{y} \sim N(\mu, \sigma^2/n)$，我们有 $z := \frac{\sqrt{n}(\bar{y} - \mu)}{\sigma} \sim N(0, 1)$，且 $x := \frac{(n-1)s_y^2}{\sigma^2} \sim \chi^2_{n-1}$，此外，根据 [Proposition 1.2](#c01.xhtml#c01-fea-0008)，$\bar{y}$ 与 $s_y^2$ 独立。因此，$t = \frac{z}{\sqrt{x/(n-1)}} = \frac{\sqrt{n}(\bar{y} - \mu)}{s_y} \sim t_{n-1}$。

