Δp ≈ δp + ξ·∇p₀  with  δp = −γp₀ ∇·ξ − ξ·∇p₀ ,  (6.156)

Δv ≈ δv + ξ·∇v₀  with  δv = ∂ξ/∂t + (v₀·∇)ξ − (ξ·∇)v₀ ,  (6.157)

ΔB ≈ δB + ξ·∇B₀  with  δB = ∇ × (ξ × B₀) .  (6.158)

Equation (6.155) is based on mass conservation, equation (6.156) is based on the equation of state, equation (6.157) is based on the momentum equation, and equation (6.158) is based on the equation of induction. By inserting these quantities into the Lagrangian momentum equation (6.145), we obtain a linearized equation of motion in ξ (Frieman and Rotenberg, 1960):

ρ₀ ∂²ξ/∂t² + 2ρ₀ v₀·∇(∂ξ/∂t) − G(ξ) = 0 ,  (6.159)

where

G(ξ) = F(ξ) + ∇·(ξρ₀ v₀·∇v₀ − ρ₀ v₀ v₀·∇ξ) ,  (6.160)

F(ξ) = −∇(δp) − B₀ × (∇ × δB) + (∇ × B₀) × δB + (∇Ψ)∇·(ρ₀ ξ) ,  (6.161)

where G is the generalized perturbation force acting on the plasma. It contains particular flow terms. In addition, 2ρ₀ v₀·∇ is an antisymmetric operator known as the gyroscopic operator. If ξ·F(ξ) < 0, the displacement and force are in opposite directions, the force opposes displacements, and the system will oscillate around the equilibrium. The configuration is stable. The displacement and force are opposite in direction if ξ·F(ξ) > 0, and the force encourages displacement, causing the perturbation to grow. The configuration is unstable (see Figure 6.37). If ξ·F(ξ) = 0, the perturbation is neutrally stable. Note that the force-like term G(ξ) can also be written as the total pressure as follows:

G = −∇Π + (B₀·∇δB + δB·∇B₀)/μ₀ − g ∇·(ρ₀ ξ) + ∇·( ρ₀ ξ dv₀/dt − ρ₀ v₀ v₀·∇ξ ) − ∂(ρ₀ v₀)/∂t · ∇ξ ,  (6.162)

where

Π = δp + B₀·δB/(2μ₀) = −γp₀ ∇·ξ − ξ·∇p₀ + B₀·δB/(2μ₀) ,  (6.163)

is the total pressure.