
We arrive at the local form of the EM energy equation in vacuum, which is known as Poynting’s theorem,

∇·(E×H)+ 1/2 ∂/∂t [ε₀E²+μ₀H²] + E·(J+∂P/∂t)+μ₀H·∂M/∂t = 0

or

∇·S + ∂W/∂t = −E·(J+∂P/∂t) − μ₀H·∂M/∂t . (3.42)

with

S = E×H   and   W = 1/2 [ε₀E²+μ₀H²] ,  (3.43)

where W is the energy density of the EM field and S is Poynting’s vector (the area density of electromagnetic power flow). Poynting’s vector is energy transferred per unit time per unit cross-sectional area (or power unit area). So in vacuum (i.e., J=0, P=0, and M=0) electric fields and magnetic fields carry half of the total energy.

Equation (3.42) is Poynting’s theorem. It does not immediately tell us much about energy in an electromagnetic field; but the physical interpretation becomes clearer if we convert it from differential form into integral form. Consider a given volume D. We integrate the equation of Poynting’s theorem in (3.42) by using the divergence theorem to obtain the global form of the EM energy equation; i.e.,

∫_{∂D} n·(E×H) dS(x) = ∂/∂t[∫_D {(1/2 ε₀E²)+(1/2 μ₀H²)} dV(x)] + ∫_D E·(J+∂P/∂t) dV(x) + μ₀ ∫_D H·∂M/∂t dV(x) .  (3.44)

Notice that we define n here to be an inward-pointing vector so that we can switch the order of E and H. The term in the bracket in the right-hand side of this equation is the energy contained in volume D. The first term of this bracket is the energy stored in the electric field and the second term is the energy stored in the magnetic field. In the vacuum, the energy density of the EM field in the vacuum is

W = 1/2 [ε₀E²+μ₀H²] = ε₀E²  (3.45)

because B = μ₀H = E/c₀ in the free space. Let us consider the particular case of a sinusoidal traveling wave of the form

E(x,t)= i₁ E₀ cos(kz−ωt)   and   B(x,t)= i₂ E₀/c₀ cos(kz−ωt) .  (3.46)

The energy density and Poynting’s vector of an electromagnetic field are

W = 1/2 [ε₀E²+μ₀H²] = ε₀E² = ε₀E₀² cos²(kz−ωt)  (3.47)

S = E × H = c₀ε₀E₀²k = c₀Wk = c₀ε₀E₀² cos²(kz − ωt)k (3.48)
with k = i₁ × i₂ = i₃. Since the average value of cos²(kz − ωt) over one period is 1/2, the average values of the energy density and Poynting's vector are

W_avg = ½ ε₀ E₀² and |S|_avg = ½ c₀ ε₀ E₀² . (3.49)

|S|avg is known as the wave intensity. It is the average amount of energy per unit area per unit time that passes through (or hits) a surface.

> **Exercise:** A source in the subsurface emits a cosine wave with an average power of 5 × 10^{-3} watts. (i) Determine the cosine wave intensity. (ii) Determine E₀ and B₀. We assume that the source radiates equally in all directions in a 31.623 m radius.

It is worthwhile to emphasize that ions and/or electrons themselves do not really travel all that much. Instead, what really travels is the Poynting vector which captures the interaction between ions and/or electrons. Imagine a lattice in a vacuum at rest made of magnets all located in such a way to repel each other. The interaction between them is such that they don't move. Now if we displace one of the magnets, you'll see the displacement spread. However, magnets themselves barely move, but the interaction spreads at light speed. That is why Poynting vector flows through conductors, allowing electricity to find its way into our homes and buildings.

We have six unknown fields (ρ_E, P, M, J, H, and E), including five vectorial quantities, but only four equations (Ampere's law, Faraday's law, and two Gauss' laws). Therefore, the macroscopic Maxwell's equation system is underdetermined. From a physical point of view, the electromagnetic field must be uniquely determined once the sources that generate the fields and the distribution of matter are given. Maxwell's equations for matter remain incomplete without another set of relations. These relations are called constitutive relations. Our next task is to describe the constitutive relations, which describe material behavior (i.e., matter distribution). They relate EM field intensities (primary fields) and EM displacement fields (secondary fields), as illustrated in Figure 3.4.

A second reason these relationships are between macroscopic quantities is that they are derived from experimental observations of material properties. In other words, they can be established without knowing the relations between local microscopic fields.

In constitutive equations, the primary fields, E and H, can be thought of as inputs to the secondary fields, D, B, and J (or P, M, and J) as outputs or predicted responses. In most general cases, constitutive equations are arbitrary relationships between the primary and secondary fields; i.e.,

```
J = J(E, H) , P = P(E, H) , M = M(E, H) (3.50)
```

![](img/f5b5b8709fc3a81631262f22d3552c5e_339_0.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_340_0.png)

(a) The constitutive relationships are the relationships between the primary fields, E and H, and the secondary fields, P, M, and J. (b) Alternatively, the constitutive relationships are the relationships between the primary fields, E and H, and the secondary fields, D, B, and J. These relationships depend on the matter (medium) in which the fields exist. There are no constitutive equations for the microscopic scale.

```
J = J(E,H) , D = D(E,H) , B = B(E,H) . (3.51)
```

If these relationships are linear, the medium is considered linear in its electromagnetic behavior. Otherwise, the medium is considered nonlinear in its electromagnetic behavior. Nonlinear materials are desirable in some applications such as light phase modulation. In other applications, however, they are undesirable. If the medium parameters that describe the relationships between the primary and secondary fields are invariant with orientation (that is, they are scalar), at a given point in space, the medium is considered isotropic at this point. Otherwise, the medium is anisotropic. In anisotropic materials, properties depend on the x-, y-, z-direction and constitutive relations may be written component-wise in matrix (or tensor) form. A wide class of materials have linear time-independence (i.e. properties do not change with time), and isotropic behavior in the presence of weak EM fields (E and H fields are sufficiently small). Such materials include crystalline minerals. Crystalline minerals are made up of randomly oriented microscopic crystals and behave as isotropic media on a macroscopic scale. We will now focus on time-independent linear isotropic media.

Table 3.4 shows parameters introduced by the discoveries of the linear relationships between primary and secondary fields. Equation J(x,t) = σ(x)E(x,t), which is known as Ohm's law, relates the current density, J, to the electric field, E, by the electrical conductivity, σ, which is a material's ability to pass electric current. The unit of conductivity is Siemens per meter (S/m).

Electrical conductivity varies between materials by more than 27 orders of magnitude, the greatest variation in any physical property. The reciprocal of electrical

Table 3.4. Parameters introduced by the discoveries of the linear relationships between primary and secondary fields in the case of time-independent linear isotropic media. In isotropic media, all these parameters are scalar (i.e., tensors of rank zero).

| Primary | Secondary | Parameter |
|---------|-----------|----------|
| E(x,t) | J(x,t) = σ(x)E(x,t) | σ: conductivity |
| E(x,t) | P(x,t) = ε₀χ^(e)(x)E(x,t) | χ^(e): Electric susceptibility |
| E(x,t) | D(x,t) = ε(x)E(x,t) = ε₀εᵣ(x)E(x,t) | ε: Permittivity |
|  | εᵣ: Relative permittivity |  |
| H(x,t) | M(x,t) = χ^(m)(x)H(x,t) | χ^(m): Magnetic susceptibility |
| H(x,t) | B(x,t) = μ(x)H(x,t) = μ₀μᵣ(x)H(x,t) | μ: Magnetic permeability |
|  | μᵣ: Relative magnetic permeability |  |

conductivity is electric resistivity; i.e., ρ(x) = 1/σ(x) . It is a measure of how strongly a given material opposes the flow of an electric current. The unit of electrical resistivity is the ohm-meter, i.e., Siemens/meter = 1/(ohm × meter) .

As shown in Figure 3.5, using conductivity values we can classify materials into electric conductors, electric insulators, and semiconductors. A conductor is an object or material that allows the movement of electric charges freely. An insulator is an object or type of material that strongly resists the flow of electric charges, meaning it does not conduct charges. A semiconductor is an object or type of material whose electrical conductivity is between that of a conductor and an insulator. Most metals are good electrical conductors. The most utilized materials in the construction of electrical equipment are copper and aluminum because of their great conductivity. Also, alloys of copper with other elements are used. The most utilized materials as insulators in the construction of electrical equipment are rubber, glass, plastic, and wood because of their very poor conductivity. Semiconductors form the backbone of our technological society. What makes semiconductors so important is their unique electrical behavior. They exhibit extreme sensitivity (exponential dependence) to the presence of minute quantities of solutes, which are known as dopants, thus giving us the possibility of controlling the electrical conductivity of a semiconductor by doping. All microchip processors are based on applications of semiconductors such as silicon (Si) and germanium (Ge). In addition, many devices used as sensors are also based on these semiconductor materials.

The electrical conductivity of rocks mostly depends on the porosity, temperature, and salinity of the water and rock interaction. Remember, porosity is the ratio between the pore volume and the total volume of a material. The saturated fluid is the dominant electrical conductor in the rock, and the degree of saturation
