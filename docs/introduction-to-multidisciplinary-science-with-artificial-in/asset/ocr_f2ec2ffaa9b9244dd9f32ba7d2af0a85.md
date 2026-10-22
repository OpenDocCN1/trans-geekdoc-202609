gravitational potential, Ψ₀. In this uniform gas distribution, we assume small perturbations caused, for example, by a shock wave due to a nearby supernova or a passing spiral arm of the galaxy. As a result, density, pressure, and velocity distributions are perturbed from their original states. We have
ρ = ρ₀ + δρ , p = p₀ + δp , Ψ = Ψ₀ + δΨ , and v = δv ,
where the amplitudes of perturbations are assumed to be smaller, that is, |δρ|/ρ₀ ≪ 1, |δp|/p₀ ≪ 1 and |δv|/c_s ≪ 1. Variables change only in the z direction. Using (6.150)-(6.153), we have
∂δρ/∂t + ρ₀ ∂δv_z/∂z = 0 , ρ₀ (∂δv_z/∂t) = -∂δp/∂z - ρ₀ ∂δΨ/∂z ,
and
p₀ = c_is²ρ₀ = k_B ρ₀ T / μ m_H and δp = c_is² δρ ⇒ c_is² = k_B T / μ m_H , (6.188)
where μ is the mean molecular weight (with μ = 1 for the gas fully neutral), m_H is the mass of hydrogen, and T is the mean cloud's temperature. In addition, we have assumed the perturbation itself to be isothermal so that c_is remains unchanged. By substituting the continuity equation and the state equation in the momentum equation, we arrive at
∂δv_z/∂t = c_is² ∂δρ/∂z - ρ₀ ∂δΨ/∂z . (6.189)

By taking the derivative with respect to z of (6.189) and substituting the continuity equation and the Poisson equation (∇²δΨ = 4πG₀ δρ) in the resulting equation, we obtain the growth of density perturbation due to the self-gravity; i.e.,
∂²δv_z / ∂z ∂t = -c_is² ∂²δρ / ∂z² - 4πG₀ ρ₀ δρ  ⇌  ∂²ρ / ∂t² = c_is² ∂²ρ / ∂z² + 4πG₀ ρ₀ δρ . (6.190)

If G₀ = 0, this equation expresses the propagation of sound waves in a homogeneous medium. In other words, this equation shows how sound waves propagate in a self-gravitational medium. By decomposing the perturbations in Fourier modes of the form δρ(z, t) ∝ exp[i(kz − ωt)], we obtain the following dispersion relation
ω² = c_is² k² - 4πG₀ ρ₀ . (6.191)

We can distinguish two cases: ω² > 0 the wave is an ordinary oscillatory wave and instability occurs when ω² < 0. The critical wavenumber (i.e., the border between these two regimes; ω = 0) and critical wavelength are
k_J = √(4πG₀ ρ₀ / c_is²) and λ_J = 2π / k_J = √(π c_is² / G₀ ρ₀) , (6.192)