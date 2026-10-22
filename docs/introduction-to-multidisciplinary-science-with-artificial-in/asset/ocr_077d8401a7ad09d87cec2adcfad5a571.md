![](bbox=[0.13, 0.1, 0.86, 0.26])

Figure 6.34. Rayleigh-Taylor (or heavy over light) instability with t₂ > t₁ > t₀; a heavy fluid over a light fluid (heavy/light). These two fluids are immiscible. The density difference drives the Rayleigh-Taylor instability.

Rayleigh-Taylor instability and Kelvin-Helmholtz instability are concerned with the stability of an interface with tangential velocity and/or density that continuously changes to zero with respect to the mass flux. We start by introducing the Lagrangian and Eulerian formalisms of small perturbations. These formalisms are essential for the derivation of criteria for these instabilities.

# 6.4.1. Eulerian versus Lagrangian Formalisms

The Eulerian formalism uses fixed positions that do not change over time, as we did in the previous subsection. The Lagrangian formalism considers medium and position to be co-moving. Specifically, we are interested in establishing the differences between mathematical Eulerian and Lagrangian differentiation and between the Lagrangian and Eulerian formulations of small perturbation models. We will limit ourselves to non-, See for example, Fiedler and Burton, 2021 and Burton and Noble, 2014, relativistic formulation.

# Eulerian and Lagrangian time derivatives.

Consider, for example, the plasma density, ρ(x,t) at position x and time t. At time t + δt the element will be at position x + δx. The change in quantity ρ of the plasma element is

Dρ/Dt = lim_{δt→0} [ (ρ(x+δx, t+δt) - ρ(x,t)) / δt ] = lim_{δt→0} [ ∂ρ/∂t + (δx/δt)·∇ρ + O(δt, |δx|) ] , (6.142)

where
ρ(x+δx, t+δt) = ρ(x,t) + ∂ρ/∂t δt + δx·∇ρ + O(δt², |δx|², δt|δx|),

and where D/Dt is the Lagrangian derivative and ∂/∂t is the Eulerian derivative, respectively, of the density. So we have the following relation between the Lagrangian and Eulerian derivatives:

Dρ/Dt ≈ ∂ρ/∂t + (δx/δt)·∂ρ/∂x = ∂ρ/∂t + v·∇ρ . (6.143)
Lagrangian    Eulerian    convective    Eulerian    convective