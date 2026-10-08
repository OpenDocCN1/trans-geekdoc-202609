We now sketch this approach for the GD optimization method in (7.4) resulting in the popular SGD optimization method applied to (7.2).

Specifically, let $S = \{1, 2, \ldots, M\}$, $J \in \mathbb{N}$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, for every $n \in \mathbb{N}$, $j \in \{1, 2, \ldots, J\}$ let $\mathbf{m}_{n,j} : \Omega \rightarrow S$ be a uniformly distributed random variable, let $\ell: \mathbb{R}^{9} \times S \rightarrow \mathbb{R}$ satisfy for all $\theta \in \mathbb{R}^{9}$, $m \in S$ that

$\ell(\theta, m) = |\left(\mathcal{N}_{\frac{\partial d}{\partial \mathbf{w}_{n,1}}, \mathbf{w}_{n,2}, \ldots, \mathbf{w}_{n,\ell}, \mathrm{id}_{G}}(x_m) - \boldsymbol{y}_m\right)|^{2},$ (7.5)

and let $\Theta = (\Theta_n)_{n \in \mathbb{N}_0} : \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{9}$ satisfy for all $n \in \mathbb{N}$ that

$\Theta_{0} = \xi \quad \text{and} \quad \Theta_{n} = \Theta_{n-1} - \gamma_{n}\left[\frac{1}{J} \sum_{j=1}^{J}\left(\nabla_{\theta} \ell\right)\left(\Theta_{n-1}, \mathbf{m}_{n,j}\right)\right].$ (7.6)

The stochastic process $(\Theta_n)_{n \in \mathbb{N}_0}$ is an SGD process for the minimization problem associated to (7.2) with learning rates $(\gamma_n)_{n \in \mathbb{N}_0}$, constant number of Monte Carlo samples (batch sizes) $J$, initial value $\xi$, and data $(\mathbf{m}_{n,j})_{(n,j) \in \mathbb{N} \times \{1, \ldots, J\}}$ (see Definition 7.2.1 below for the precise definition). Note that in (7.6) in each step $n \in \mathbb{N}$ we only employ a Monte Carlo approximation

$\frac{1}{J}\sum_{j=1}^{J}\left(\nabla_{\theta} \ell\right)\left(\Theta_{n-1}, \mathbf{m}_{n,j}\right) \approx \frac{1}{M}\sum_{m=1}^{M}\left(\nabla_{\theta} \ell\right)\left(\Theta_{n-1}, m\right) = \left(\nabla \mathcal{L}\right)\left(\Theta_{n-1}\right)$ (7.7)

of the exact gradient of the objective function. Nonetheless, in deep learning applications the SGD optimization method (or other SGD-type optimization methods) typically result in good approximate minimizers of the objective function. Note that employing approximate gradients in the SGD optimization method in (7.6) means that performing any step of the SGD process involves the computation of a sum with only $J$ summands, while employing the exact gradient in the GD optimization method in (7.4) means that performing any step of the process involves the computation of a sum with $M$ summands. In deep learning applications when $M$ is very large (for instance, $M \geq 10^{6}$) and $J$ is chosen to be reasonably small (for example, $J = 128$), this means that performing steps of the SGD process is much more computationally affordable than performing steps of the GD process. Combining this with the fact that SGD-type optimization methods do in the training of ANNs often find good approximate minimizers (cf., for instance, Remark 9.14.5 and [100, 391]) is the key reason making the SGD optimization method and other SGD-type optimization methods the optimization methods chosen in almost all deep learning applications. It is the topic of this chapter to introduce and study SGD-type optimization methods such as the plain-vanilla SGD optimization method in (7.6) above.

# 7.2 SGD optimization

In the next notion we present the promised stochastic version of the plain-vanilla GD optimization method from Section 6.1, that is, in the next notion we present the plain-