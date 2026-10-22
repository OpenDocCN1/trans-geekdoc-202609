![](bbox=[0.17, 0.12, 0.8, 0.33])

Figure 6.39. An illustration of the cloud collapse when the inwards directed gravitational force is bigger than the outwards directed pressure force. During collapse, cloud sub-regions emerge. These sub-regions start collapsing on their own. This leads to fragmentation.

where α is a small and positive fudge factor of order unity that depends on the internal density structure; for a diatomic molecule like H₂, α = 5/2 and for monatomic gas, α = 3/2. We use the fact that m = (4/3)πr³ρ₀ in the definition of a cloud's gravitational potential energy. We can deduce the condition for gravitational collapse as follows:

2K < U ⟹ (3 m k_B T)/(μ m_H) < α G₀ m^{5/3} (3/(4π ρ₀))^{-1/3} ⟺ m > m_J , (6.199)

where

m_J = 9/(2 α^{3/2} √π) (k_B/(G₀ μ m_H))^{3/2} T^{3/2} ρ₀^{-1/2} . (6.200)

We return to the Jeans mass in (6.193) by selecting α = (3/π)².

# Magnetized Jeans instability: magnatohydrostatic clouds.

For a more realistic instability criterion, we should consider a rotating and magnetized plasma in addition to self-gravitating. We will work in cylindrical coordinates (r, θ, z) or (i_r, i_θ, i_z), where i_r is the direction of cloud expansion and contraction, i_θ describes the rotation of the cloud, and i_z describes the direction of cloud collapse. We assume that δv = [δv_r, δv_θ, 0]^T, and δB = [0,0,δB_z]^T as shown in Figure 6.39. By taking the Fourier transforms of (6.150)-(6.153) with respect to t and r, we arrive at the following perturbation equations of the mass conservation, gravitational potential, equation of state, momentum conservation, and magnetic flux conservation of the ideal MHD laws

ω δρ/ρ₀ - k_r δv_r = 0 , k² Ψ + 4π G₀ δρ = 0 , δp/δρ = p₀/ρ₀ = c_{is}² , (6.201)

-i ω δv_r - 2 Ω₀ δv_θ + i k_r δp/p₀ + k_r δΨ + i k_r c_A² δB_z/B₀ = 0 (6.202)

κ² δv_r/(2 Ω₀) - i ω δv_θ = 0 , ω δB_z/B₀ + k_r δv_r = 0 , (6.203)