
where `0 < ϵ < 1`, `p > 0`, and `0 < t[0] < 2π` are the parameters. The parameter `ϵ` is the eccentricity. Since the functions `g(t)` and `f(t)` are arbitrary, can be discontinuous, and may contain infinitely many parameters (for instance, the coefficient of a Taylor or Fourier series), it covers all the possible shapes that exist in the universe.

## 6.3 Shape signature

The concept of shape signature is not new, see [\[1](#Chp006_103-111_B9780443218576000102.xhtml#br0005),[3\]](#Chp006_103-111_B9780443218576000102.xhtml#br0015). Each shape (or set of points) is uniquely described by a normalized set called `signature`. In our context, this set can be a curve, a set of points, multiple broken curves, or a combination of these elements. The signature does not depend on the location or center of gravity of the shape. It depends on the orientation, though it is easy to generalize the definition to make it rotation-invariant, or to handle 3D shapes. The first step is to use the center of gravity (centroid) for the origin, and then rescale the shape by standardizing the variance of the radius `r[t]`.

The centroid is the weighted average of the points located on the shape. Typically, the weight is constant. However, if the points are not uniformly distributed on the shape, you may use appropriate weights to correct for this artifact. This is illustrated in [Fig. 6.2](#Chp006_103-111_B9780443218576000102.xhtml#f0015). I now dive into the details of the reweighting procedure.

Figure 6.2 Weighted centroid, shape signature.

### 6.3.1 Weighted centroid

Let `(x[t], y[t])` be the standard coordinates of the observed points on the shape. In other words, `x[t] = r[t] cos θ[t]` and `y[t] = r[t] sin θ[t]`. The centroid is defined as `(G[x], G[y])` with

```math
G_{x} = \frac{1}{\mu}\int_{T}w_{t}x_{t}dt,\quad G_{y} = \frac{1}{\mu}\int_{T}w_{t}y_{t}dt,\quad\text{with~}\mu = \int_{T}w_{t}dt.
```

Here `w[t] > 0` is the weight function, with `t ∈ T`. If `t` is discrete (for instance, the shape consists of observed data points), then the integrals are replaced by sums.

In most cases, the points are not evenly distributed on the curve. On a real data set, it translates by a curve that appears darker or thicker in locations with high point density; see [Fig. 6.2](#Chp006_103-111_B9780443218576000102.xhtml#f0015). If this is not a desirable feature, it can be eliminated by proper reweighting. To get the points evenly distributed on the curve, when computing the centroid, proceed as follows. Using notations from infinitesimal calculus, you want `Δs[t]`, the length of an infinitesimal curve segment encompassing `(x[t], y[t])`, to be proportional to `w[t]`. Since the proportion factor does not matter, we must have

```math
\Delta s_{t} = \sqrt{(\Delta x_{t})^{2} + (\Delta y_{t})^{2}} = w_{t}\Delta t.
```

This leads to

```math
w_{t} = \sqrt{\left( \frac{dx_{t}}{dt} \right)^{2} + \left( \frac{dy_{t}}{dt} \right)^{2}}.
```

It can be rewritten using polar coordinates as

```math
w_{t} = \sqrt{\left( \frac{dr_{t}}{dt} \right)^{2} + r_{t}^{2}\left( \frac{d\theta_{t}}{dt} \right)^{2}}.
```

The formula assumes differentiability of the functions involved. In many cases, there are points (values of `t`) where the functions are either left- or right-differentiable [[Wiki](https://en.wikipedia.org/wiki/Semi-differentiability)], but not both. Use the left or right derivative for these points.

### 6.3.2 Computing the signature

We want a mathematical object, easy to compute, that uniquely characterizes a shape, up to a translation vector and scaling factor. The set of all polar coordinates `(r[t], θ[t])`, with `t ∈ T`, uniquely characterizes the shape. But it is not scale- or translation-invariant. To fix this problem, you first need to change the coordinate system to make the centroid `(G[x], G[y])` defined by formula [(6.2)](#Chp006_103-111_B9780443218576000102.xhtml#deq4), the origin. You may use the weight function `w[t]` discussed in Section [6.3.1](#Chp006_103-111_B9780443218576000102.xhtml#s0025). Then, you need to rescale by a factor `σ`. Eventually, the new coordinates are

```math
u[t] = \sigma^{-1} \cdot (x[t] - G[x]) = \rho[t] \cos \phi[t],\quad v[t] = \sigma^{-1} \cdot (y[t] - G[y]) = \rho[t] \sin \phi[t].
```

Here `u[t], v[t]` are the new Cartesian coordinates replacing `x[t], y[t]`, and `ρ[t], φ[t]` the new polar coordinates replacing `r[t], θ[t]`. For reasons that will become obvious when comparing two shapes in Section [6.4](#Chp006_103-111_B9780443218576000102.xhtml#s0040), the scaling factor is chosen as follows:

```math
\sigma = \sqrt{\int_{T}{(x_{t} - G_{x})}^{2} + {(y_{t} - G_{y})}^{2}dt}.
```

It follows immediately that

```math
\rho_{t} = \sigma^{-1} \cdot \sqrt{{(x_{t} - G_{x})}^{2} + {(y_{t} - G_{y})}^{2}},\quad\text{and~}\int_{T}\rho_{t}^{2}dt = 1.
```

Now the signature is defined as the set of all `(ρ[t], φ[t])` with `t ∈ T`. By construction, `0 ≤ φ[t] ≤ 2π`. When plotting the signature, to keep it bounded on `[0, 2π] × [0, 1]` regardless of the shape, one can use `ρ[t]/(1 + ρ[t])` instead of `ρ[t]` on the vertical axis. An example of signature is shown in [Fig. 6.2](#Chp006_103-111_B9780443218576000102.xhtml#f0015) (right plot).

### 6.3.3 Example

The shape illustrated in Figs. [6.2](#Chp006_103-111_B9780443218576000102.xhtml#f0015) and [6.3](#Chp006_103-111_B9780443218576000102.xhtml#f0020) is different from that defined by [(6.1)](#Chp006_103-111_B9780443218576000102.xhtml#deq2). This time, it is defined by the parametric polar equation

```math
\theta[t] = (2\pi + 2\pi \sin(c t) + \eta) \bmod 2\pi,\quad r[t] = t^{a}(1 - t)^{b},\quad t \in T = [0, 1].
```
