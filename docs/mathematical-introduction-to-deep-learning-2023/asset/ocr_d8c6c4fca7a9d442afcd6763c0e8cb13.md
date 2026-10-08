This shows for all $x \in (0,1]$ that
\begin{equation}
\Gamma(x+1) \leq 1 = x^{\lfloor x \rfloor} = \max\{1, x^x\}.
\end{equation}
Induction, item **(i)** in Lemma **11.2.1**, and the fact that $\forall x \in (0, \infty) : x - \lfloor x \rfloor \in (0,1]$ therefore imply that for all $x \in [1, \infty)$ it holds that
\begin{equation}
\Gamma(x+1) = \left[\prod_{i=1}^{\lfloor x \rfloor}(x-i+1)\right]\Gamma\big(x-\lfloor x \rfloor+1\big) \leq x^{\lfloor x \rfloor}\Gamma(x-\lfloor x \rfloor+1) \leq x^{\lfloor x \rfloor} \leq x^x = \max\{1, x^x\}.
\end{equation}
Combining this and **(11.23)** with item **(i)** in Lemma **11.2.1** establishes item **(ii)**. Moreover, observe that Hölder’s inequality and item **(i)** in Lemma **11.2.1** demonstrate that for all $x \in (0, \infty), \; \alpha \in [0,1]$ it holds that
\begin{equation}
\begin{aligned}
\Gamma(x+\alpha) & = \int_0^\infty t^{x+\alpha-1}e^{-t} \, \mathrm{d}t = \int_0^\infty t^{\alpha x - \alpha}t^{(1-\alpha)x-(1-\alpha)}e^{-(1-\alpha)t} \, \mathrm{d}t \\
& = \int_0^\infty \big[t^{x}e^{-t}\big]^\alpha\big[t^{x-1}e^{-t}\big]^{1-\alpha} \, \mathrm{d}t \\
& \leq \left( \int_0^\infty t^{x}e^{-t} \, \mathrm{d}t \right)^\alpha \left( \int_0^\infty t^{x-1}e^{-t} \, \mathrm{d}t \right)^{1-\alpha} \\
& = \big[\Gamma(x+1)\big]^\alpha \big[\Gamma(x)\big]^{1-\alpha} = x^\alpha\big[\Gamma(x)\big]^\alpha\big[\Gamma(x)\big]^{1-\alpha} \\
& = x^\alpha\Gamma(x).
\end{aligned}
\end{equation}
This and item **(i)** in Lemma **11.2.1** prove that for all $x \in (0, \infty), \; \alpha \in [0,1]$ it holds that
\begin{equation}
\begin{aligned}
x \, \Gamma(x) = \Gamma(x+1) = \Gamma\big(x + \alpha + (1-\alpha)\big) \leq (x+\alpha)^{1-\alpha}\Gamma(x+\alpha).\end{aligned}
\end{equation}
Combining **(11.25)** and **(11.26)** ensures that for all $x \in (0, \infty), \; \alpha \in [0,1]$ it holds that
\begin{equation}
\frac{x}{(x+\alpha)^{1-\alpha}} \leq \frac{\Gamma(x+\alpha)}{\Gamma(x)} \leq x^{\alpha}.
\end{equation}
In addition, note that item **(i)** in Lemma **11.2.1** and **(11.27)** show that for all $x \in (0, \infty), \; \alpha \in [0,1]$ it holds that
\begin{equation}
\frac{\Gamma(x+\alpha)}{\Gamma(x+1)} = \frac{\Gamma(x+\alpha)}{x \, \Gamma(x)} \leq x^{\alpha-1}.
\end{equation}
This implies for all $\alpha \in [0,1], \; x \in (\alpha, \infty)$ that
\begin{equation}
\frac{\Gamma(x)}{\Gamma\big(x+(1-\alpha)\big)} = \frac{\Gamma\big((x-\alpha)+\alpha\big)}{\Gamma\big((x-\alpha)+1\big)} \leq (x-\alpha)^{\alpha-1} = \frac{1}{(x-\alpha)^{1-\alpha}}.
\end{equation}
This, in turn, establishes for all $\alpha \in [0,1], \; x \in (1-\alpha, \infty)$ that
\begin{equation}
(x+\alpha-1)^\alpha = (x-(1-\alpha))^\alpha \leq \frac{\Gamma(x+\alpha)}{\Gamma(x)}.
\end{equation}


412