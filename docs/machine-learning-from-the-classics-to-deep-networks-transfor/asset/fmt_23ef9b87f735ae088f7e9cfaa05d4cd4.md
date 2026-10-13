
$$
\widehat{\mathbf{s}}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,y) = \mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,\varnothing) + \gamma\left( \mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,y) - \mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,\varnothing) \right),
$$

where $\gamma > 0$ is a guidance scale constant. In words, the output of the neural network is extrapolated further to the direction of $\mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,y)$ and away from $\mathbf{s}_{\mathbf{\theta}_{\ast}}(\mathbf{x}_{t},t,\varnothing)$. If one takes the negative of both sides and multiply with the associated, for the time step, standard deviation, then Eq. [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) can be equivalently expressed in terms of the corresponding $\boldsymbol{\epsilon}_{\boldsymbol{\theta}}$ estimates in place of the $\mathbf{s}_{\boldsymbol{\theta}}$'s. Observe that if $\gamma = 0$ Eq. [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) reduces to the unconditional model, and if $\gamma = 1$ it aligns with the vanilla class-conditional one.

The interpretation of Eq. [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) relies on Eq. [(19.83)](#Chp019_997-1102_B9780443292385000251.xhtml#deq165). Eq. [(19.85)](#Chp019_997-1102_B9780443292385000251.xhtml#deq168) involves the approximate gradients of their true counterparts in Eq. [(19.83)](#Chp019_997-1102_B9780443292385000251.xhtml#deq165), if in the place of the classifier we use an *implicit* one,

$$
q^{(i)}(y|\mathbf{x}_{t}) \propto \left( \frac{q(\mathbf{x}_{t}|y)}{q(\mathbf{x}_{t})} \right)^{\gamma}.
$$

Note that according to the Bayes rule,
