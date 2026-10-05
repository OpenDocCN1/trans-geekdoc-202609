# D.1 THE RANDOM HIERARCHY MODEL 221

Therefore, given the noisy observation $x_t$, the prior belief $v_{\uparrow}(h_i^{(0)})$ on the value of the token $i$ being equal to $a$ is given by $p(x_{0,j}|x_{t,i})$, that is:

```
$v_{\iota}(h_i^{(0)} = a) = \delta_{ar{a},a}, \quad \text{if } x_{t,j} = \bar{a} \in \mathcal{V}^{(0)};\n$v_{\iota}(h_i^{(0)} = a) = 1/v, \quad \forall a \in \mathcal{V}^{(0)} \text{if } x_{t,j} = [\text{MASK}].$ (341)
```

e-PROCESS In process, instead of running a forward diffusion process, we act directly on the leaves. We introduce a noise-signal ratio $\epsilon \in [0,1]$, which controls the noise level instead of the diffusion time $t$. Starting from a datum $x_0$, whose $i$-th token has value $ar{a} \in \mathcal{V}^{(0)}$, the prior beliefs at the leaf $i$ taking values in $\mathcal{V}^{(0)}$ are defined

```
$v_{\iota}(h_i^{(0)} = \bar{a}) = 1 - \epsilon + \epsilon/v, \quad \text{for } x_{0,j} = \bar{a};\n$v_{\iota}(h_i^{(0)} = a) = \epsilon/v, \quad \forall a \in \mathcal{V}^{(0)} \setminus \\bar{a}.$ (342)
```

The role of $\epsilon$ is to decrease the prior belief on the starting value of a token. This process can be interpreted as an averaged forward process, where the average is made over different forward trajectories. In the example of masking diffusion (Equation 341), calling $1-\alpha_t$ the probability of a token being masked at time $t$, the prior beliefs at the leaves

```
$v_{\iota}(h_i^{(0)} = \bar{a}) = \alpha_t + \frac{1-\alpha_t}{v}, \quad \text{where } x_{0,j} = \bar{a};\n$v_{\iota}(h_i^{(0)} = a) = \frac{1-\alpha_t}{v}, \quad \forall a \in \mathcal{V}^{(0)} \setminus \\bar{a}.$ (343)
```

which have the same functional form as Equation 342 by identifying $\epsilon = 1-\alpha_t$. Both $\epsilon$ and $1-\alpha_t$ vary between 0 and 1 and play the role of noise-to-signal ratio in their respective processes. However, the fluctuations of the upward beliefs around their mean in the masking diffusion change the statistics of the BP messages propagating upwards and make the mapping $\epsilon = 1-\alpha_t$ inaccurate. In the example of Figure 12, the transition in the e-process is located at $\epsilon^* \approx 0.74$, while it is found that $1-\alpha_t = t'/T \approx 0.3$ for masking diffusion.

# D.1.1.3 BP sampling versus diffusion

BP SAMPLING As discussed at the end of section D.1.1.1, BP allows for sampling directly from the posterior probability $p(\hat{x}_0|x_t)$. Given a noisy observation $x_t$, and the corresponding marginal probabilities $p(h_i^{(t)}|x_t)$, the sampling proceeds as follows:

+   root symbol $h_l^{(L)} = \hat{g}, \hat{g} \in \mathcal{V}^{(L)}$, is sampled according to the probability $p(h_l^{(L)}|x_t);