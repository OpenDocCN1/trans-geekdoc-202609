To include an endogenous trigger for regime change we must move to threshold models introduced by Tong and Lim (1980). These models were introduced in the context of autoregressive series and consequently known as threshold autoregressive (TAR) models. The transition function is defined as

$$f(z_t)=\begin{cases}1, & z_t>c,\\0, & z_t<c,\end{cases}\qquad(125A.6)$$

where $z_t$ is the transition variable and $c$ is the critical (threshold) value of $z_t$ that defines the change of state. Using this, the model becomes:

$$y_t=\begin{cases}\beta'x_t+\varepsilon_t, & z_t>c,\\\varphi'x_t+\varepsilon_t, & z_t<c.\end{cases}\qquad(125A.7)$$

In the case of much of the work on this model, it was assumed that $z_t$ was a lagged value of $y_t$ but this is not a necessary part of the model. The key advance of TAR over Markov models is the specification of the transition variable that triggers the transition between states. It is worth noting that it is only necessary to specify the transition variable, the critical value can be derived from the data (Chan, 1993).

The TAR model is still limited to instantaneous changes of state. In order to allow a gradual move between states $f(z_t)$ must change continuously as $z_t$ changes. There are a number of definitions of $f(z_t)$ that meet the definition of smooth transition, two are particularly useful and well understood, the logistic and exponential transition functions. These transition functions generate logistic (L-STR) and exponential (E-STR) smooth transition regression models, respectively. The logistic transition function is defined as

$$f(z_t)=\left[1+\exp\left(-\gamma(z_t-c)\right)\right]^{-1},\quad \gamma>0,\qquad(125A.8)$$

where $\gamma$ is the smoothness parameter (i.e., the slope of the transition function) and $c$ is the threshold. Choosing this transition function yields the L-STR model. In the limit, as $\gamma\to0$ or $\gamma\to\infty$, the L-STR model becomes linear as the value of $f(z_t)$ is constant. For intermediate values of $\gamma$, the degree of decay depends upon the value of $z_t$. As $z_t\to-\infty$, $f(z_t)\to0$ and the behavior of $y_t$ is given by $y_t=\beta'x_t+e_t$. As $z_t\to+\infty$, $f(z_t)\to1$ and the behavior of $y_t$ is given by $y_t=(\beta'+\varphi')x_t+e_t$.

The alternative exponential transition function is

$$f(z_t)=1-\exp\left(-\gamma(z_t-c)^2\right),\quad \gamma>0.\qquad(125A.9)$$

Again $\gamma$ is the smoothness parameter while the function is symmetric around $z_t=c$. This function produces the E-STR model. Like before as $\gamma\to0$