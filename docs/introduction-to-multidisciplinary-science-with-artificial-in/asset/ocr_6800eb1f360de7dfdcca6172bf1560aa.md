![](bbox=[0.12, 0.11, 0.9, 0.32])

Figure 6.41. Consider two plasmas. The upper (z > 0) and lower (z < 0) fluids have different densities ρ₁ and ρ₂. There are two different magnetic fields applied to the plasmas. The disturbance at the interface of the plasma is the vertical displacement z = ξ(x, y, t); that is, the perturbed position of the interface at ξ(x, y, t).

+   - Lower layer (-b < z ≤ 0): ρ = const., v₂ = [vₓ₂, vᵧ₂, 0]ᵀ = const., B₂ = [Bₓ₂, Bᵧ₂, 0]ᵀ = const., and p₂ = p₀ - ρ₂ g z. According to (6.177), we have
+   
+     d²ξ⁽²⁾/dz² - k₀² ξ⁽²⁾ = 0 , with ξ⁽²⁾(-b) = 0 ⟹ ξ⁽²⁾ = C₂ sinh[k₀(z + b)] / sinh(k₀ b) ,
+   
+     where C₂ is constant of integration.
+   - The first boundary condition is the kinematic boundary condition that expresses the continuity of the normal component of plasma displacement (or normal velocity) at the interface; i.e.,
+   
+     ξ⁽¹⁾(0) = ξ⁽²⁾(0) ⟹ C₁ = C₂ .
+   - The second boundary condition is the dynamic boundary condition expressing the continuity of the total pressure (pressure balance) at the interface, z = 0; i.e.,
+   
+     [Π - ρ g ξ]₁² = 0 ⟹ [ (ρ/k₀²)(~ω² - ω_A²) (1/ξ) dξ/dz - ρ g ]₁² = 0 ,   (6.209)
+   
+     where Π is total pressure (kinetic plus magnetic) defined in (6.177) for depth-dependent incompressible plasmas (i.e., γ ⟶ ∞), which implies that ∇·ξ = 0.

The standard method for analyzing an instability is to find its dispersion relation. Inserting solutions for ξ₁ and ξ₂ (6.209) yields the dispersion equation:

-ρ₁ [ (ω - Ω₀₁)² - ω_A₁² ] coth(k₀ a) - k₀ ρ₁ g
= -ρ₂ [ (ω - Ω₀₂)² - ω_A₂² ] coth(k₀ b) - k₀ ρ₂ g.   (6.210)