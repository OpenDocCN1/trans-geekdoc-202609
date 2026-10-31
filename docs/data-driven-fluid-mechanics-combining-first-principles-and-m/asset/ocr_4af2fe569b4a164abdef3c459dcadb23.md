![](bbox=[0.28, 0.14, 0.78, 0.36])

Figure 1.8 Cylinder wake configuration with volume force actuation and hot-wire sensor.

In this differential algebraic system, a3 is slaved to the fluctuation energy (1.18). Here, b is the actuation command, for example, the induced acceleration in the circular region, while the positive gain g quantifies the effect on the dynamics and depends, for instance, on the size and location of the volume force support. Without loss of generality, the actuation term only effects a1 by suitable rotation of the modes u1, u2.

The forced growth rate of the fluctuation energy K = r²/2 = (a₁² + a₂²)/2 reads

```
dK/dt = a₁ da₁/dt + a₂ da₂/dt = σ r² + g b a₁.  (1.21)
```

The fluctuation energy can be mitigated with negative actuation power g b a1, that is, b has to have the opposite sign of a1. For simplicity, a linear control law is assumed,

```
b = -k a₁,      k > 0.  (1.22)
```

The control gain k shall ensure a forced exponential decay rate σc < 0 of the amplitude r. This implies with (1.22) and (1.21),

```
dK/dt = σc r² = σ r² + g k a₁².  (1.23)
```

Averaging over one period and exploiting overline{a₁²} = r²/2 yields the control gain k and thus the control law

```
b = 2 (σc - σ)/g a₁.  (1.24)
```

The implications of this law are plausible: the higher the unforced growth rate and the higher the desired damping, the larger the volume force amplitude must become. Contrary, the larger the gain g of actuation on the dynamics, the smaller the volume force needs to be. It should be born in mind that σ is r dependent.

For the sensor-based control, the state a = [a₁, a₂]ᵀ is estimated from the sensor signal with a dynamic observer. The resulting stabilization effect is shown in Figure 1.9. While the model allows complete stabilizing, the fluctuation energy of the DNS has been reduced by 30% in the observation region x < 6. The model is only partially accurate as it ignores shedding mode changes due to actuation and convection