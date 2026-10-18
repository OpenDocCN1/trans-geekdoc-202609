
Each iteration of GPI in the LSPI algorithm starts with a deterministic target policy `π[D](⋅)` that is made available as a greedy policy derived from the previous iteration's LSTDQ-solved `Q̂(s; a; w^(∗))`. The LSTDQ solution for `w^(∗)` is based on pre-generated training data and with the Q-Learning target policy set to be `π[D]`. Since we learn the Q-Value function for only `a = c`, the behavior policy `μ` generating experiences data for training is a constant function `μ(s) = c`. Note also that for American Options, the reward for `a = c` is 0. So each atomic experience for training is of the form `(s, c, 0, s′)`. This means we can represent each atomic experience for training as a 2-tuple `(s, s′)`. This reduces the LSPI Semi-Gradient Equation (13.2) to:

$$
\begin{array}{r} {{\sum\limits_{i}\phi}(s_{i}) \cdot (\phi{(s_{i})}^{T} \cdot \mathbf{\mathbf{w}}^{\*} - \gamma \cdot \hat{Q}(s_{i}^{\\prime},\pi_{D}(s_{i}^{\\prime});\mathbf{\mathbf{w}}^{\*})) = 0} \\\\ \end{array}
$$

(13.3)

We need to consider two cases for the term `Q̂(s[i]^′, π[D](s[i]^′); w^(∗))`:

*   `C1`: If `s[i]^′` is non-terminal and `π[D](s[i]^′) = c` (i.e., `ϕ(s[i]^′)^(T) ⋅ w ≥ g(s[i]^′)`): Substitute `ϕ(s[i]^′)^(T) ⋅ w^(∗)` for `Q̂(s[i]^′, π[D](s[i]^′); w^(∗))` in Equation (13.3)

*   `C2`: If `s[i]^′` is a terminal state or `π[D](s[i]^′) = e` (i.e., `g(s[i]^′) > ϕ(s[i]^′)^(T) ⋅ w`): Substitute `g(s[i]^′)` for `Q̂(s[i]^′, π[D](s[i]^′); w^(∗))` in Equation (13.3)

So we can rewrite Equation (13.3) using indicator notation `𝕀` for cases `C1`,`C2` as:

$$
\begin{array}{r} {{\sum\limits_{i}\phi}(s_{i}) \cdot (\phi{(s_{i})}^{T} \cdot \mathbf{\mathbf{w}}^{\*} - \mathbb{I}_{C1} \cdot \gamma \cdot \phi{(s_{i}^{\\prime})}^{T} \cdot \mathbf{\mathbf{w}}^{\*} - \mathbb{I}_{C2} \cdot \gamma \cdot g(s_{i}^{\\prime})) = 0} \\\\ \end{array}
$$

Factoring out `w^(∗)`, we get:

$$
\begin{array}{r} {({\sum\limits_{i}\phi}(s_{i}) \cdot {(\phi(s_{i}) - \mathbb{I}_{C1} \cdot \gamma \cdot \phi(s_{i}^{\\prime}))}^{T}) \cdot \mathbf{\mathbf{w}}^{\*} = \gamma \cdot {\sum\limits_{i}\mathbb{I}_{C2}} \cdot \phi(s_{i}) \cdot g(s_{i}^{\\prime})} \\\\ \end{array}
$$

This can be written in the familiar vector-matrix notation as: `A ⋅ w^(∗) = b`

$$
\begin{array}{r} {\mathbf{\mathbf{A}} = {\sum\limits_{i}\phi}(s_{i}) \cdot {(\phi(s_{i}) - \mathbb{I}_{C1} \cdot \gamma \cdot \phi(s_{i}^{\\prime}))}^{T}} \\\\ \end{array}
$$

$$
\begin{array}{r} {\mathbf{\mathbf{b}} = \gamma \cdot {\sum\limits_{i}\mathbb{I}_{C2}} \cdot \phi(s_{i}) \cdot g(s_{i}^{\\prime})} \\\\ \end{array}
$$

The `m × m` Matrix `A` is accumulated at each atomic experience `(s[i], s[i]^′)` as:

$$
\begin{array}{r} \left. \mathbf{\mathbf{A}}\leftarrow\mathbf{\mathbf{A}} + \phi(s_{i}) \cdot {(\phi(s_{i}) - \mathbb{I}_{C1} \cdot \gamma \cdot \phi(s_{i}^{\\prime}))}^{T} \right. \\\\ \end{array}
$$

The `m`-Vector `b` is accumulated at each atomic experience `(s[i], s[i]^′)` as:

$$
\begin{array}{r} \left. \mathbf{\mathbf{b}}\leftarrow\mathbf{\mathbf{b}} + \gamma \cdot \mathbb{I}_{C2} \cdot \phi(s_{i}) \cdot g(s_{i}^{\\prime}) \right. \\\\ \end{array}
$$

With Sherman-Morrison incremental inverse of `A`, we can reduce the time-complexity from `O(m³)` to `O(m²)`.

This solved `w^(∗)` updates the `Q`-Value Function Approximation to `Q̂(s, a; w^(∗))`. This defines an updated, improved deterministic policy `π[D]^′` (serving as the `Deterministic Target Policy` for the next iteration of GPI):

$$
\begin{array}{r} {\pi_{D}^{\\prime}(s) = \text{arg}\,\text{max}_{a}\hat{Q}(s,a;\mathbf{\mathbf{w}}^{\*})\text{~for~all~}s \in \mathcal{N}} \\\\ \end{array}
$$

Li, Szepesvari, Schuurmans ([Li, Szepesvári, and Schuurmans 2009](#bib01.xhtml#refbib_41)) recommend in their paper to use 7 feature functions, the first 4 Laguerre polynomials that are functions of the underlying price and 3 functions of time. Precisely, the feature functions they recommend are:

*   `ϕ[0](S[t]) = 1`

*   $\phi_{1}(S_{t}) = e^{- \frac{M_{t}}{2}}$

*   $\phi_{2}(S_{t}) = e^{- \frac{M_{t}}{2}} \cdot (1 - M_{t})$

*   $\phi_{3}(S_{t}) = e^{- \frac{M_{t}}{2}} \cdot (1 - 2M_{t} + M_{t}^{2}/2)$

*   $\phi_{0}^{(t)}(t) = sin(\frac{\pi(T - t)}{2T})$

*   `ϕ[1]^((t))(t) = log(T − t)`

*   $\phi_{2}^{(t)}(t) = {(\frac{t}{T})}^{2}$

where $M_{t} = \frac{S_{t}}{K}$ (`S[t]` is the current underlying price and `K` is the American Option strike), `t` is the current time, and `T` is the expiration time (i.e., `0 ≤ t < T`).

### 13.6.2 Deep Q-Learning for American Options Pricing

LSPI is data-efficient and compute-efficient, but linearity is a limitation in the function approximation. The alternative is (incremental) Q-Learning with neural network function approximation, which we cover in this subsection. We employ the same set up as LSPI (including Experience Replay)—specifically, the function approximation is required only for continuation value. Precisely,

$$
\begin{array}{l} {\hat{Q}(s,a;\mathbf{\mathbf{w}}) = \left\{ \begin{array}{ll} {f(s;\mathbf{\mathbf{w}})} & {\text{~if~}a = c} \\\\ {g(s)} & {\text{~if~}a = e} \\\\ \end{array}~ \right.\text{~for~all~}s \in \mathcal{N}} \\\\ \end{array}
$$

where `f(s; w)` is the deep neural network function approximation.

The Q-Learning update for each atomic experience `(s[i], s[i]^′)` is:

$$
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (\gamma \cdot \hat{Q}(s_{i}^{\\prime},\pi(s_{i}^{\\prime});\mathbf{\mathbf{w}}) - f(s_{i};\mathbf{\mathbf{w}})) \cdot \nabla_{\mathbf{\mathbf{w}}}f(s_{i};\mathbf{\mathbf{w}})} \\\\ \end{array}
$$

When `s[i]^′` is a non-terminal state, the update is:

$$
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (\gamma \cdot \max(g(s_{i}^{\\prime}),f(s_{i}^{\\prime};\mathbf{\mathbf{w}})) - f(s_{i};\mathbf{\mathbf{w}})) \cdot \nabla_{\mathbf{\mathbf{w}}}f(s_{i};\mathbf{\mathbf{w}})} \\\\ \end{array}
$$

When `s[i]^′` is a terminal state, the update is:

$$
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (\gamma \cdot g(s_{i}^{\\prime}) - f(s_{i};\mathbf{\mathbf{w}})) \cdot \nabla_{\mathbf{\mathbf{w}}}f(s_{i};\mathbf{\mathbf{w}})} \\\\ \end{array}
$$

## 13.7 VALUE FUNCTION GEOMETRY

Now we look deeper into the issue of the `Deadly Triad` (that we had alluded to in [Chapter 12](#chapter12.xhtml)) by viewing Value Functions as Vectors (we had done this in [Chapter 5](#chapter5.xhtml)), understand Value Function Vector transformations with a balance of geometric intuition and mathematical rigor, providing insights into convergence issues for a variety of traditional loss functions used to develop RL algorithms. As ever, the best way to understand Vector transformations is to visualize it and so, we loosely refer to this topic as Value Function Geometry. The geometric intuition is particularly useful for linear function approximations. To promote intuition, we shall present this content for linear function approximations of the Value Function and stick to Prediction (rather than Control) although many of the concepts covered in this section are well-extensible to non-linear function approximations and to the Control problem.
