# Figure 4. Equivalent circuit of the Unified Power Flow Controller

![](bbox=[0.14, 0.135, 0.85, 0.48])

```
V_{cR}(\cos \delta_{cR} + j \sin \delta_{cR})
```

Where V_{vR} and \delta_{vR} are the controllable voltage magnitude and phase angle of the voltage source representing the shunt converter. Similarly, V_{cR} and \delta_{cR} are the controllable voltage magnitude and phase angle of the voltage source representing the series converter. The source impedance is considered to be resistance less.

The active and reactive power equations are

At bus k

```
P_k = [V_k V_m B_{km} \sin(\theta_k - \theta_m)] + [V_k V_{cR} B_{km} \sin(\theta_k - \delta_{cR})] + [V_k V_{vR} B_{vR} \sin(\theta_k - \delta_{vR})]
```

```
Q_k = -V_k^2 B_{kk} - [V_k V_m B_{km} \cos(\theta_k - \theta_m)] - [V_k V_{cR} B_{km} \cos(\theta_k - \delta_{cR})] - [V_k V_{vR} B_{vR} \cos(\theta_k - \delta_{vR})]
```