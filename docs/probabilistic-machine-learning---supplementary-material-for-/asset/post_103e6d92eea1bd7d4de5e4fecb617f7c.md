
In this section, we will consider a convex outer approximation, $\mathbb{L}(G)$, based on pseudo marginals, as in Section 9.1.3.1. We also need to approximate the entropy (which was not needed when performing MAP estimation, discussed in Section 9.1.3). We discuss this entropy approximation in Section 10.1.3.1, and then show how we can use this to approximate log $Z$. Finally we show that loopy belief propagation attempts to optimize this approximation.

## 10.1.3.1 Bethe free energy

From Equation (9.17), we know that a joint distribution over a tree-structured graphical model can be represented exactly by the following:

$$p_{\boldsymbol{\mu}}(\boldsymbol{x}) = \prod_{s \in V} \mu_s(x_s) \prod_{(s,t) \in E} \frac{\mu_{st}(x_s, x_t)}{\mu_s(x_s)\mu_t(x_t)}$$ (10.11)

This satisfies the normalization and pairwise marginalization constraints of the outer approximation by construction.

From Equation 10.11, we can write the exact entropy of any tree structured distribution $\boldsymbol{\mu} \in \mathbb{M}(T)$ as follows:

$$\mathbb{H}(\boldsymbol{\mu}) = \sum_{s \in V} H_s(\mu_s) - \sum_{(s,t) \in E} I_{st}(\mu_{st})$$ (10.12)

$$H_s(\mu_s) = - \sum_{x_s \in \mathcal{X}_s} \mu_s(x_s) \log \mu_s(x_s)$$ (10.13)

$$I_{st}(\mu_{st}) = \sum_{(x_s, x_t) \in \mathcal{X}_s \times \mathcal{X}_t} \mu_{st}(x_s, x_t) \log \frac{\mu_{st}(x_s, x_t)}{\mu_s(x_s)\mu_t(x_t)}$$ (10.14)

Note that we can rewrite the mutual information term in the form $I_{st}(\mu_{st}) = H_s(\mu_s) + H_t(\mu_t) - H_{st}(\mu_{st})$, and hence we get the following alternative but equivalent expression:

$$\mathbb{H}(\boldsymbol{\mu}) = - \sum_{s \in V} (d_s - 1) H_s(\mu_s) + \sum_{(s,t) \in E} H_{st}(\mu_{st})$$ (10.15)

where $d_s$ is the degree (number of neighbors) for node $s$.

The Bethe$^1$ approximation to the entropy is simply the use of Equation 10.12 even when we don't have a tree:

$$\mathbb{H}_{\text{Bethe}}(\boldsymbol{\tau}) = \sum_{s \in V} H_s(\tau_s) - \sum_{(s,t) \in E} I_{st}(\tau_{st})$$ (10.16)

We define the Bethe free energy as the expected energy minus approximate entropy:

$$\mathcal{F}_{\text{Bethe}}(\boldsymbol{\tau}) \triangleq - [\boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{\text{Bethe}}(\boldsymbol{\tau})] \approx - \log Z$$ (10.17)

Thus our final objective becomes

$$\max_{\boldsymbol{\tau} \in \mathbb{L}(G)} \boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{\text{Bethe}}(\boldsymbol{\tau})$$ (10.18)

We call this the Bethe variational problem or BVP. The space we are optimizing over is a convex set, but the objective itself is not concave (since $\mathbb{H}_{\text{Bethe}}$ is not concave). Thus there can be multiple local optima. Also, the entropy approximation is not a bound (either upper or lower) on the true entropy. Thus the value obtained by the BVP is just an approximation to $\log Z(\boldsymbol{\theta})$. However, in the case of trees, the approximation is exact. Also, in the case of models with attractive potentials, the resulting value turns out to be an upper bound [SWW08]. In Section 10.1.5, we discuss how to modify the algorithm so it always minimizes an upper bound for any model.

## 10.1.3.2 LBP messages are Lagrange multipliers

In this subsection, we will show that any fixed point of the LBP algorithm defines a stationary point of the above constrained objective. Let us define the normalization constraint as $C_{ss}(\boldsymbol{\tau}) \triangleq -1 + \sum_{x_s} \tau_s(x_s)$, and the marginalization constraint as $C_{ts}(x_s; \boldsymbol{\tau}) \triangleq \tau_s(x_s) - \sum_{x_t} \tau_{ts}(x_t, x_s)$ for each edge \(t \to s\). We can now write the Lagrangian as

$$
\mathcal{L}(\boldsymbol{\tau}, \boldsymbol{\lambda}; \boldsymbol{\theta}) \triangleq \boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{\text{Bethe}}(\boldsymbol{\tau}) + \sum_s \lambda_{ss} C_{ss}(\boldsymbol{\tau}) + \sum_{s,t} \left[ \sum_{x_s} \lambda_{ts}(x_s) C_{ts}(x_s; \boldsymbol{\tau}) + \sum_{x_t} \lambda_{st}(x_t) C_{st}(x_t; \boldsymbol{\tau}) \right]
$$

(The constraint that \(\boldsymbol{\tau} \ge 0\) is not explicitly enforced, but one can show that it will hold at the optimum since \(\boldsymbol{\theta} > 0\).) Some simple algebra then shows that \(\nabla_{\boldsymbol{\tau}} \mathcal{L} = \mathbf{0}\) yields

$$
\log \tau_s(x_s) = \lambda_{ss} + \theta_s(x_s) + \sum_{t \in \text{nbr}(s)} \lambda_{ts}(x_s)
$$

$$
\log \frac{\tau_{st}(x_s, x_t)}{\tilde{\tau}_s(x_s)\tilde{\tau}_t(x_t)} = \theta_{st}(x_s, x_t) - \lambda_{ts}(x_s) - \lambda_{st}(x_t)
$$

where we have defined \(\tilde{\tau}_s(x_s) \triangleq \sum_{x_t} \tau(x_s, x_t)\). Using the fact that the marginalization constraint implies \(\tilde{\tau}_s(x_s) = \tau_s(x_s)\), we get

$$
\log \tau_{st}(x_s, x_t) = \lambda_{ss} + \lambda_{tt} + \theta_{st}(x_s, x_t) + \theta_s(x_s) + \theta_t(x_t) + \sum_{u \in \text{nbr}(s) \setminus t} \lambda_{us}(x_s) + \sum_{u \in \text{nbr}(t) \setminus s} \lambda_{ut}(x_t)
$$

To make the connection to message passing, define \(m_{t \to s}(x_s) = \exp(\lambda_{ts}(x_s))\). With this notation, we can rewrite the above equations (after taking exponents of both sides) as follows:

$$
\tau_s(x_s) \propto \exp(\theta_s(x_s)) \prod_{t \in \text{nbr}(s)} m_{t \to s}(x_s)
$$

$$
\tau_{st}(x_s, x_t) \propto \exp \left( \theta_{st}(x_s, x_t) + \theta_s(x_s) + \theta_t(x_t) \right) \times \prod_{u \in \text{nbr}(s) \setminus t} m_{u \to s}(x_s) \prod_{u \in \text{nbr}(t) \setminus s} m_{u \to t}(x_t)
$$

where the \(\lambda\) terms and irrelevant constants are absorbed into the constant of proportionality. We see that this is equivalent to the usual expression for the node and edge marginals in LBP.

To derive an equation for the messages in terms of other messages (rather than in terms of \(\lambda_{ts}\)), we enforce the marginalization condition \(\sum_{x_t} \tau_{ts}(x_s, x_t) = \tau_s(x_s)\). Then one can show that

$$
m_{t \to s}(x_s) \propto \sum_{x_t} \left[ \exp \left\{ \theta_{st}(x_s, x_t) + \theta_t(x_t) \right\} \prod_{u \in \text{nbr}(t) \setminus s} m_{u \to t}(x_t) \right]
$$

We see that this is equivalent to the usual expression for the messages in LBP.

## 10.1.3.3 Kikuchi free energy

We have shown that LBP minimizes the Bethe free energy. In this section, we show that generalized BP (??) minimizes the Kikuchi free energy; we define this below, but the key idea is that it is a tighter approximation to $\log Z$. In more detail, define $\mathbb{L}_t(G)$ to be the set of all pseudo-marginals such that normalization and marginalization constraints hold on a hyper-graph whose largest hyper-edge is of size $t + 1$. For example, in Figure **??**, we impose constraints of the form

$$\sum_{x_1, x_2} \tau_{1245}(x_1, x_2, x_4, x_5) = \tau_{45}(x_4, x_5), \sum_{x_6} \tau_{56}(x_5, x_6) = \tau_5(x_5), \dots$$ (10.26)

Furthermore, we approximate the entropy as follows:

$$\mathbb{H}_{\text{Kikuchi}}(\boldsymbol{\tau}) \triangleq \sum_{g \in E} c(g) H_g(\tau_g)$$ (10.27)

where $H_g(\tau_g)$ is the entropy of the joint (pseudo) distribution on the vertices in set $g$, and $c(g)$ is called the **overcounting number** of set $g$. These are related to **Mobius numbers** in set theory. Rather than giving a precise definition, we just give a simple example. For the graph in Figure **??**, we have

$$\mathbb{H}_{\text{Kikuchi}}(\boldsymbol{\tau}) = -[H_{1245} + H_{2356} + H_{4578} + H_{5689}] - [H_{25} + H_{45} + H_{56} + H_{58}] + H_5$$ (10.28)

Putting these two approximations together, we can define the **Kikuchi free energy**$^2$ as follows:

$$\mathcal{F}_{\text{Kikuchi}}(\boldsymbol{\tau}) \triangleq -[\boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{\text{Kikuchi}}(\boldsymbol{\tau})] \approx -\log Z$$ (10.29)

Our variational problem becomes

$$\max_{\tau \in \mathbb{L}(G)} \boldsymbol{\theta}^T \boldsymbol{\tau} + \mathbb{H}_{\text{Kikuchi}}(\boldsymbol{\tau})$$ (10.30)

Just as with the Bethe free energy, this is not a concave objective. There are several possible algorithms for finding a local optimum of this objective, including generalized belief propagation. For details, see e.g., [WJ08, Sec 4.2] or [KF09, Sec 11.3.2].

## 10.1.4 Convex belief propagation

The mean field energy functional is concave, but it is maximized over a non-convex inner approximation to the marginal polytope. The Bethe and Kikuchi energy functionals are not concave, but they are maximized over a convex outer approximation to the marginal polytope. Consequently, for both MF and LBP, the optimization problem has multiple optima, so the methods are sensitive to the initial conditions. Given that the exact formulation Equation (10.4) is a concave objective maximized over a convex set, it is natural to try to come up with an approximation of a similar form, without local optima.

**Convex belief propagation** involves working with a set of tractable submodels, $\mathcal{F}$, such as trees or planar graphs. For each model $F \subset G$, the entropy is higher, $\mathbb{H}(\boldsymbol{\mu}(F)) \ge \mathbb{H}(\boldsymbol{\mu}(G))$, since $F$ has fewer constraints. Consequently, any convex combination of such subgraphs will have higher entropy, too:

$$\mathbb{H}(\boldsymbol{\mu}(G)) \le \sum_{F \in \mathcal{F}} \rho(F) \mathbb{H}(\boldsymbol{\mu}(F)) \triangleq \mathbb{H}(\boldsymbol{\mu}, \rho)$$ (10.31)

where $\rho(F) \ge 0$ and $\sum_F \rho(F) = 1$. Furthermore, $\mathbb{H}(\boldsymbol{\mu}, \rho)$ is a concave function of $\boldsymbol{\mu}$.

Having defined an upper bound on the entropy, we now consider a convex outer bound on the marginal polytope of mean parameters. We want to ensure we can evaluate the entropy of any vector $\boldsymbol{\tau}$ in this set, so we restrict it so that the projection of $\boldsymbol{\tau}$ onto the subgraph $G$ lives in the projection of $\mathbb{M}$ onto $F$:

$$\mathbb{L}(G; \mathcal{F}) \triangleq \{ \boldsymbol{\tau} \in \mathbb{R}^d : \boldsymbol{\tau}(F) \in \mathbb{M}(F) \, \forall F \in \mathcal{F} \}$$ (10.32)

This is a convex set since each $\mathbb{M}(F)$ is a projection of a convex set. Hence we define our problem as

$$\max_{\boldsymbol{\tau} \in \mathbb{L}(G; \mathcal{F})} \boldsymbol{\tau}^T \boldsymbol{\theta} + \mathbb{H}(\boldsymbol{\tau}, \rho)$$ (10.33)

$^2$Ryoichi Kikuchi is a Japanese physicist.
