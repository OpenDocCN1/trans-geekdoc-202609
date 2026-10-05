# 88 Atomic Modeling of Friction

velocities, the sliding velocity $v_0$ is no longer negligible when compared with the peak velocity during the instability. This renders the friction-velocity dependence susceptible to the choice of the thermostats. Damping with respect to the substrate leads to strictly monotonically increasing forces, whereas damping with respect to the top wall can result in non-monotonic friction-velocity relationships.$^{46}$

So far, we have considered the zero temperature case. Once fluctuations are allowed, a qualitative friction-velocity relationship exists, which can be shown by choosing thermal energies as small as $k_B T = 0.1 v_0$ [see Figure 10(b)]. Jumps can be thermally activated, and the friction forces with decreasing velocity. Again, at small $v_0$, there is little effect of the thermostat on the measured friction forces. Even changing $v_{ij}$ by as much as a factor of 16 results in all undetectable effect at small $v_0$. This behavior originates from the fact that the system can get very close to thermal equilibrium at every position of the top wall for very sliding velocities. As such, linear response theory applies and follows that friction and velocity are linearly related at sufficiently small values of $v_0$. This linearity is generally valid unless the energy barriers are infinitely high and explains the linear dependence of friction upon the small $v_0$ and finite $T$, as shown in Figure 5.

# Dissipative-Dynamics Thermostat

A disadvantage of Langevin thermostats is that they require a (local) reference system. Dissipative particle dynamics (DPD) overcomes this problem by assuming that damping and random forces act on the center-of-mass system of a pair of atoms. The DPD equations of motion read as

```
dot{\mathbf{r}}_i = -
abla V - \sum_j \gamma_{ij}(\mathbf{r}_i - \mathbf{r}_j) + \Gamma_{ij}(t)$
```

With $\Gamma_{ij}(t) = -\Gamma_{ji}(t)$. The usual relations for fluctuation and dissipation apply

```
$$\Gamma_{ij,\alpha}(t) = 0$$
```

```
$(\Gamma_{ij,\alpha}(t))(\Gamma_{kl,\beta}(t')) = 2k_B T \gamma_{ij}(\delta_{ik}\delta_{jl} + \delta_{il}\delta_{jk})\delta_{\alpha\beta} \frac{\delta_{t,t'}}{\Delta t}$
```

Note that $\gamma_{ij}$ can be chosen to be distance dependent. A common approach is to assume that $\gamma_{ij}$ is a constant for a distance smaller than a cut-off radius $r_{cut,DPD}$ and to set $\gamma_{ij} = 0$. As calculating random numbers may be a task of relatively significant computational effort in force-field-based simulations, it may be sensible to make $r_{cut,DPD}$ smaller than the cut-off radius