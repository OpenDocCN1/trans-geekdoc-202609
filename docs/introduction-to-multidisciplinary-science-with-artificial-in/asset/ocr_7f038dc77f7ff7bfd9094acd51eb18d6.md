![](bbox=[0.18, 0.1, 0.8, 0.4])

Figure 3.29. An illustration of the general solution of the differential equation for charge density, which is a damped exponential. Characteristic damping time is τ_c = ε/σ, where ε is the permittivity and σ is the conductivity. This solution tells us that any charge density initially present at time zero is exponentially damped and dissipated in a characteristic time, τ_c.

However, the characteristic collision time of free electrons in pure copper is τ_collision = 3.2 × 10^-13 second; hence τ_c << τ_collision. We can see that the characteristic time in pure copper is very small compared to the collision time in pure copper. So, if we are willing to wait a short time (e.g., a pico of a second) then, any initial free-charge density accumulated inside a good conductor at time zero will have dissipated away/damped out, and from that time onward, free-charge density can safely be assumed to be zero in a conductor. That is the assumption we are making here for Maxwell’s equations in a conductor.

# The EM wave equation.

For a good conductor with ρ_E(x, t > Δt) = 0 (e.g., Δt = 20τ_c), we can write Maxwell’s equations for t ≥ Δt (an uncharged ohmic conductor) as follows:

```
-∇ × H + σ E + ε ∂E/∂t = 0    (3.146)

∇ × E + μ ∂H/∂t = 0           (3.147)

∇ · E = 0                      (3.148)

∇ · H = 0 .                    (3.149)
```