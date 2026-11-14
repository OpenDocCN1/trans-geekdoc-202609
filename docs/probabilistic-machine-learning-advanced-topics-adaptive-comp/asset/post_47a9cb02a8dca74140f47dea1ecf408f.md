

we call these **deep state-space models**, also known as **dynamical variational autoencoders**. (To be consistent with the literature on VAEs, we denote the observations by $x_t$ instead of $y_t$.) For a detailed review, see [Ged+20; Gir+21].

## 29.13.1 Deep Markov models

Suppose we create a SSM in which we use a deep neural network for the dynamics model and/or observation model; the result is called a **deep Markov model** [KSS17] or **stochastic RNN** [BO14; Fra+16]. (This is not quite the same as a variational RNN, which we explain in Section 29.13.4.)

We can fit a DMM using SVI (Section 10.1.4). The key is to infer the posterior over the latents.

From the first-order Markov properties, the exact posterior is given by

$p(z_{1:T}|x_{1:T}) = \prod_{t=1}^T p(z_t|z_{t-1}, x_{1:T}) = \prod_{t=1}^T p(z_t|z_{t-1}, x_{t:T})$ (29.164)

where we define $p(z_1|z_0, x_{1:T}) = p(z_1|x_{1:T})$, and the cancelation follows since $z_t \perp x_{1:t-1}|z_{t-1}$, as pointed out in [KSS17].

In general, it is intractable to compute $p(z_{1:T}|x_{1:T})$, so we approximate it with an inference network. There are many choices for $q$. A simple one is a fully factorized model, $q(z_{1:T}) = \prod_t q(z_t|x_{1:t})$. This is illustrated in Figure 29.42a. Since $z_t$ only depends on past data, $x_{1:t}$ (which is accumulated in the RNN hidden state $h_t$), we can use this inference network at run time for online inference. However, for training the model offline, we can use a more accurate posterior by using

$q(z_{1:T}|x_{1:T}) = \prod_{t=1}^T q(z_t|z_{t-1}, x_{1:T}) = \prod_{t=1}^T q(z_t|z_{t-1}, x_{t:T})$ (29.165)

Note that the dependence on past observation $x_{1:t-1}$ is already captured by $z_{t-1}$, as in Equation (29.164). The dependencies on future observations, $x_{t:T}$, can be summarized by a backwards RNN, as shown in Figure 29.42b. Thus

$q(z_{1:T}, h_{1:T}|x_{1:T}) = \prod_{t=T}^1 \mathbb{I}(h_t = f(h_{t+1}, x_t)) \prod_{t=1}^T q(z_t|z_{t-1}, h_t)$ (29.166)

![](img/ca72c1626f4850f058a9edc138c1ac73_1059_0.png)

Given a fully factored \(q(\mathbf{z}_{1:T})\), we can compute the ELBO as follows.

```
\log p(\mathbf{x}_{1:T}) = \log \left[ \sum_{\mathbf{z}_{1:T}} p(\mathbf{x}_{1:T}|\mathbf{z}_{1:T})p(\mathbf{z}_{1:T}) \right]
= \log \mathbb{E}_{q(\mathbf{z}_{1:T})} \left[ p(\mathbf{x}_{1:T}|\mathbf{z}_{1:T}) \frac{p(\mathbf{z}_{1:T})}{q(\mathbf{z}_{1:T})} \right]
= \log \mathbb{E}_{q(\mathbf{z}_{1:T})} \left[ \prod_{t=1}^T \frac{p(\mathbf{x}_t|\mathbf{z}_t)p(\mathbf{z}_t|\mathbf{z}_{t-1})}{q(\mathbf{z}_t)} \right]
\ge \mathbb{E}_{q(\mathbf{z}_{1:T})} \left[ \sum_{t=1}^T \log p(\mathbf{x}_t|\mathbf{z}_t) + \log p(\mathbf{z}_t|\mathbf{z}_{t-1}) - \log q(\mathbf{z}_t) \right]
= \sum_{t=1}^T \mathbb{E}_{q(\mathbf{z}_t)} [\log p(\mathbf{x}_t|\mathbf{z}_t)] - \mathbb{E}_{q(\mathbf{z}_{t-1})} [D_{\text{KL}} (q(\mathbf{z}_t) \| p(\mathbf{z}_t|\mathbf{z}_{t-1}))]
```

If we assume that the variational posteriors are jointly Gaussian, we can use the reparameterization trick to use posterior samples to compute stochastic gradients of the ELBO. Furthermore, since we assumed a Gaussian prior, the KL term can be computed analytically.

## 29.13.2 Recurrent SSM

In a DMM, the observation model \(p(\mathbf{x}_t|\mathbf{z}_t)\) is first-order Markov, as is the dynamics model \(p(\mathbf{z}_t|\mathbf{z}_{t-1})\). We can modify the model so that it captures long-range dependencies by adding deterministic hidden states as well. We can make the observation model depend on \(\mathbf{z}_{1:t}\) instead of just \(\mathbf{z}_t\) by using \(p(\mathbf{x}_t|\mathbf{h}_t)\), where \(\mathbf{h}_t = f(\mathbf{h}_{t-1}, \mathbf{z}_t)\), so \(\mathbf{h}_t\) records all the stochastic choices. This is illustrated in Figure 29.43a. We can also make the dynamical prior depend on \(\mathbf{z}_{1:t-1}\) by replacing \(p(\mathbf{z}_t|\mathbf{z}_{t-1})\) with \(p(\mathbf{z}_t|\mathbf{h}_{t-1})\), as is illustrated in Figure 29.43b. This is known as a **recurrent SSM**.

We can derive an inference network for an RSSM similar to the one we used for DMMs, except now we use a standard forwards RNN to compute \(q(\mathbf{z}_t|\mathbf{x}_{1:t-1}, \mathbf{x}_{1:t})\).

![](img/ca72c1626f4850f058a9edc138c1ac73_1060_0.png)

Figure 29.43: Recurrent state-space models. (a) Prior is first-order Markov, p(z_t|z_{t-1}), but observation model is not Markovian, p(x_t|h_t) = p(x_t|z_{1:t}), where h_t summarizes z_{1:t}. (b) Prior model is no longer first-order Markov either, p(z_t|h_{t-1}) = p(z_t|z_{1:t-1}). Diamonds are deterministic nodes, circles are stochastic.

![](img/ca72c1626f4850f058a9edc138c1ac73_1060_1.png)

Figure 29.44: Unrolling schemes for SSMs. The labels z_{t:j} is shorthand for p(z_t|x_{1:j}). Solid lines denote the generative process, dashed lines the inference process. Arrows pointing at shaded circles represent log-likelihood loss terms. Wavy arrows indicate KL divergence loss terms. (a) Standard 1 step reconstruction of the observations. (b) Observation overshooting tries to predict future observations by unrolling in latent space. (c) Latent overshooting predicts future latent states and penalizes their KL divergence, but does not need to care about future observations. Adapted from Figure 3 of [Haf+19].

## 29.13.3 Improving multistep predictions

In Figure 29.44(a), we show the loss terms involved in the ELBO. In particular, the wavy edge z_{t|t} → z_{t|t−1} corresponds to E_{q(z_{t−1})} [D_{KL}(q(z_t) || p(z_t|z_{t−1}))], and the solid edge z_{t|t} → x_t corresponds to E_{q(z_t)} [log p(x_t|z_t)]. We see that the dynamics model, p(z_t|z_{t−1}), is only ever penalized in terms of how it differs from the one-step-ahead posterior q(z_t), which can hurt the ability of the model to make long-term predictions.

One solution to this is to make multistep forwards predictions using the dynamics model, and use these to reconstruct future observations, and add these errors as extra loss terms. This is called observation overshooting [Amo+18], and is illustrated in Figure 29.44(b).

A faster approach, proposed in [Haf+19], is to apply a similar idea but in latent space. More precisely, let us compute the multi-step prediction model, by repeatedly applying the transition model and integrating out the intermediate states to get p(z_t|z_{t−d}). We can then compute the ELBO

![](img/ca72c1626f4850f058a9edc138c1ac73_1061_0.png)

Figure 29.45: Variational RNN. (a) Generative model. (b) Inference model. The diamond-shaped nodes are deterministic.

for this as follows:

```
\(\log p_d(x_{1:T}) \triangleq \log \int \prod_{t=1}^T p(z_t | z_{t-d}) p(x_t | z_t) dz_{1:T}\)
```

```
\(\ge \sum_{t=1}^T \mathbb{E}_{q(z_t)} [\log p(x_t | z_t)] - \mathbb{E}_{p(z_{t-1} | z_{t-d}) q(z_{t-d})} [D_{KL} (q(z_t) \| p(z_t | z_{t-1}))]\)
```

To train the model so it is good at predicting at different future horizon depths d, we can average the above over all \(1 \le d \le D\). However, for computational reasons, we can instead just average the KL terms, using weights \(\beta_d\). This is called latent overshooting [Haf+19], and is illustrated in Figure 29.44(c). The new objective becomes

```
\(\frac{1}{D} \sum_{d=1}^D \log p_d(x_{1:T}) \ge \sum_{t=1}^T \mathbb{E}_{q(z_t)} [\log p(x_t | z_t)]\)
```

```
\(- \frac{1}{D} \sum_{d=1}^D \beta_d \mathbb{E}_{p(z_{t-1} | z_{t-d}) q(z_{t-d})} [D_{KL} (q(z_t) \| p(z_t | z_{t-1}))]\)
```

## 29.13.4 Variational RNNs

A variational RNN (VRNN) [Chu+15] is similar to a recurrent SSM except the hidden states are generated conditional on all past hidden states _and_ all past observations, rather than just the past hidden states. This is a more expressive model, but is slower to use for forecasting, since unrolling into the future requires generating observations _x_<sub>_t_+1</sub>, _x_<sub>_t_+2</sub>, ... to "feed into" the hidden states, which controls the dynamics. This makes the model less useful for forecasting and model-based RL (see Section 35.4.5.2).

More precisely, the generative model is as follows:

```
\(p(x_{1:T}, z_{1:T}, h_{1:T}) = \prod_{t=1}^T p(z_t | h_{t-1}, x_{t-1}) \mathbb{I}(h_t = f(h_{t-1}, x_{t-1}, z_t)) p(x_t | h_t)\)
```

