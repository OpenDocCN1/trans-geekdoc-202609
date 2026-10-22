symmetry implies ∂/∂θ = ∂/∂φ = 0 and ψ(r,θ,φ) = ψ(r). The time-independent Schrödinger equation can be written as follows:

− h²/2m_e ∇² ψ(r) + V(r) ψ(r) = 0 ⇒ − h²/2m r² d/dr (r² d/dr) ψ(r) + V(r) ψ(r) = 0 .

It is easy to check that if we write the wave function ψ(r) = u(r)/r, the function u(r) obeys the following one-dimensional equation

− h²/2m_e d²u(r)/dr² + V(r) u(r) = 0 with r > 0 . (4.23)

This equation is exactly like a particle in one dimension, except that here r is only positive, and u(r) must go to zero at the origin.

Let us consider the full three-dimensional case. We now use ψ(r,θ,φ) with all its dependencies to solve

− h/2m_e ∇² ψ(r,θ,φ) ψ − e²/4πε₀ r ψ = U ψ , (4.24)

where m_e is the electron mass, assuming the following form

ψ(r,θ,φ) = R(r) Θ(θ) Φ(φ) = R(r) Y(θ,φ) , (4.25)

with Y(θ,φ) = Θ(θ) Φ(φ). In other words, the variations of the radius, the polar angle, and the azimuthal angle of the solution to Schrödinger equation are separated. For atoms and molecules, the wave function is actually a function of the coordinates of all the electrons and nuclei. We have here used the Born-Oppenheimer approximation by ignoring the nucleus coordinates. This approximation is based on the fact that nuclei have much larger masses than electrons; i.e.,

 h²/2m_nucleus ≪ h²/2m_e for these terms of the Schrödinger equation, where m_nucleus is the nucleus mass and m_e is the electron mass. To a reasonable approximation, one can solve the Schrödinger equation only for electrons and assume the nuclei are frozen.

By substituting (4.25) and (4.22) into (4.24), we arrive at

(1/Φ) d²Φ/dφ² = − (sin²θ / R) d/dr (r² dR/dr) − (sinθ / θ) d/dθ (sinθ dΘ/dθ) − (2m r² sin²θ / h²) [U + e²/(4πε₀ r)] = −m² , (4.26)

where m² is an integer constant (not to be confused with the mass). We used the fact that the first term of these equalities is independent of r and θ and the second term is independent of φ to determine that these equalities must be constant. We can deduce the first term of this first fundamental Schrödinger equation for hydrogen

d²Φ/dφ² + m² Φ = 0 ⇒ Φ = C_φ exp[i m φ] , (4.27)