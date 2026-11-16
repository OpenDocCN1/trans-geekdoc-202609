Furthermore, for a reference point $x_0 \in \Omega_t$, we consider the angular momentum density $(x - x_0) \times \rho v$ as the subject $\psi$ of the balance equation (2.16). Then, the balance of angular momentum reduces to (Liu, 2002)

```
$$ \sigma = \sigma^{\top}, $$
```

if the balance of linear momentum (2.22) is satisfied. Thus, the symmetry of the Cauchy stress tensor guarantees the conservation of angular momentum for non-polar materials, i.e., for the case that no momentum densities act on the volume $\Omega_t$.

# ## 2.4 Description of fiber orientation states

Since the effective behavior of a fiber suspension depends on the fiber orientation statistics in the suspension, a mathematical description of the orientation state is essential to the study of fiber suspensions. In the following, we use a fiber orientation distribution function (Kanatani, 1984)

```
$$ \rho: S^2 \rightarrow \mathbb{R}, \quad n \mapsto \rho(n), $$
```

to encode the probability that fibers are oriented in direction $n$ on the 2-sphere $S^2$, and thus describe the orientation state of a fiber suspension. The temporal and spatial evolution of the orientation distribution function $\rho$ is governed by a partial differential equation, the Fokker–Planck equation (Fokker, 1914). However, in component scale molding simulations, computing the evolution of the orientation distribution function $\rho$ using the Fokker–Planck equation requires huge computational effort. Instead, it is common (Kennedy and Zheng, 2013) to use the second order fiber orientation tensor (Kanatani, 1984; Advani and Tucker III,