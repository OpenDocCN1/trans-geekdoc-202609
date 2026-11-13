This simple update rule is known as the **REINFORCE** algorithm. One improvement of this simple idea is to add a baseline, and we refer to section 13.4 of Sutton and Barto (2018) for a detailed account on this topic.

# 16.3.2 Extensions

A popular extension of REINFORCE is the so-called **actor-critic** (AC) method which combines policy gradient with Q- or v-learning. The AC algorithm can be viewed as some kind of mix between policy gradient and SARSA. A central requirement is that the state-value function $v(\cdot)$ be a differentiable function of some parameter vector **w** (it is often taken to be a neural network). The update rule is then

\(\boldsymbol{\theta} \leftarrow \boldsymbol{\theta} + \eta (R_{t+1} + \gamma v(S_{t+1}, \mathbf{w}) - v(S_t, \mathbf{w})) \frac{\nabla_\pi \boldsymbol{\theta}}{\pi_\boldsymbol{\theta}},\)
(16.17)

but the trick is that the vector **w** must also be updated. The actor is the policy side which is what drives decision making. The critic side is the value function that evaluates the actor’s performance. As learning progresses (each time both sets of parameters are updated), both sides improve. The exact algorithmic formulation is a bit long and we refer to Section 13.5 in Sutton and Barto (2018) for the precise sequence of steps of AC.

Another interesting application of parametric policies is outlined in Aboussalah and Lee (2020). In their article, the authors define a trading policy that is based on a recurrent neural network. Thus, the parameter \(\boldsymbol{\theta}\) in this case encompasses all weights and biases in the network.

Another favorable feature of parametric policies is that they are compatible with continuous sets of actions. Beyond the form (16.14), there are other ways to shape \(\pi_\boldsymbol{\theta}\). If \(\mathcal{A}\) is a subset of \(\mathbb{R}\), and \(f_\mathbf{\Omega}\) is a density function with parameters \(\mathbf{\Omega}\), then a candidate form for \(\pi_\boldsymbol{\theta}\) is

\(\pi_\boldsymbol{\theta} = f_{\mathbf{\Omega}(s, \boldsymbol{\theta})}(a),\)
(16.18)

in which the parameters \(\mathbf{\Omega}\) are in turn functions of the states and of the underlying (second order) parameters \(\boldsymbol{\theta}\).

While the Gaussian distribution (see section 13.7 in Sutton and Barto (2018)) is often a preferred choice, they would require some processing to lie inside the unit interval. One easy way to obtain such values is to apply the normal cumulative distribution function to the output. In Wang and Zhou (2019), the multivariate Gaussian policy is theoretically explored, but it assumes no constraint on weights.

Some natural parametric distributions emerge as alternatives. If only one asset is traded, then the Bernoulli distribution can be used to determine whether or not to buy the asset. If a riskless asset is available, the beta distribution offers more flexibility because the values for the proportion invested in the risky asset span the whole interval; the remainder can be invested into the safe asset. When many assets are traded, things become more complicated because of the budget constraint. One ideal candidate is the Dirichlet distribution because it is defined on a simplex (see Equation (16.13)):

\(f_\alpha(w_1, \dots, w_n) = \frac{1}{B(\boldsymbol{\alpha})} \prod_{n=1}^N w_n^{\alpha_n - 1},\)