
## Table 2.18. The Matlab commands for predicting the 1D bioheat.

```
nt=100; nx=40; L=0.05; dz=L/nx; time=30; dt=time/nt; wrcp=0.9*3770; cc=4200; kc=0.5; qo=1400; Tb=37; Tinit=37; Tnew=zeros(nx+2,nt); Tnew(1:nx+2,1)= Tinit;
for n=1:(nt-1)
    atop=zeros(1,nx+1); atop(1)=2*kc/dz; atop(2)=kc/dz; atop(nx+1)=2*kc/dz;
    abot=zeros(1,nx+1); abot(1)=2*kc/dz; abot(nx)=kc/dz;
    a=zeros(1,nx+2); a(1)=atop(1); a(nx+2)=1;
    a(2)=(3*kc/dz)+(cc*dz/dt)+wrcp*dz; a(nx+1)=(3*kc/dz)+(cc*dz/dt)+wrcp*dz;
    b=zeros(nx+2,1); b(1)=qo; b(nx+2)=Tb; b(2)=wrcp*Tb*dz+(cc*dz/dt)*Tnew(2,n);
    b(nx+1)=wrcp*Tb*dz+(cc*dz/dt)*Tnew(nx+1,n); A=zeros(nx+2,nx+2);
    for i=3:nx
        atop(i)=kc/dz; abot(i-1)=kc/dz; a(i)=(2*kc/dz)+(cc*dz/dt)+wrcp*dz;
        b(i)=wrcp*Tb*dz+(cc*dz/dt)*Tnew(i,n);
    end; A=diag(a,0)+diag(-atop,1)+diag(-abot,-1);
    for i=1:nx+2
        D(i,i-1)=1; U(1,i)=A(1,i);
    end; Y(1,1)=b(1);
    for i=2:nx+2
        D(i,i-1)=A(i,i-1)/U(i-1,i-1); U(i,i)=A(i,i)-D(i,i-1)*A(i-1,i); Y(i,1)=b(i)-D(i,i-1)*Y(i-1);
    end
    for i=1:nx+1
        U(i,i+1)=A(i,i+1);
    end; Tnew(:,n+1)=U\Y;
end; [M, c]= contourf(Tnew);colormap; c.LineWidth = 1.05;
```

The temperature distribution in a biological tissue reaches the steady-state, as we have seen in the previous example for depth. The surface temperature of the skin decreases gradually toward the steady state. Along with the penetration depth, the time to reach steady-state temperature distribution in a biological tissue is also an important parameter in the estimation of treatment time. This time depends on boundary conditions, as we can see in Figure 2.45, through its dependence on the heat flux at surface, qS. The time to reach steady-state with the first kind boundary condition, in (2.152), is 1.35×ℓb/α, while that of second kind boundary condition, in (2.152), is 2.30×ℓb/α, where α=ρb cb/k. The time of third kind boundary condition, in (2.152), varies from 1.35 to 2.30×ℓb/α.

Accurate early assessment of the skin damage in a burn injury can greatly improve post care. It has been found that burns cause changes in blood flow and heat conduction of the skin, depending on the degree of the burn. For example, the normal and burned tissues can be defined with different properties: k = 0.5 W/m·K, ω = 0.0005 ml/s/ml for normal tissue, and k = 0.2 W/m·K, ω = 0.0001 ml/s/ml for burned tissue. The main reason that the burned tissues have lower values of thermal conductivity and blood perfusion rate is the possible loss of water and the damage of blood vessels during burning. Results in Figure 2.45 demonstrate a very different transient temperature profile at the skin surface for the two types of tissue, so the detection of surface temperature can be used to determine the burned degree.

> Exercise: We can alternatively solve (2.153) for these two BCs:
> 
> \(-k \frac{dT}{dx} \big|_{x=0} = h_f [T_f - T(x = 0)]\) and \(T(x) = T_c\),
> 
> where \(T_c\) is the core temperature, \(h_f\) is the heat convection coefficient between the skin surface and the surrounding air that describes the overall contribution from natural convection and radiation, and \(T_f\) is the surrounding air temperature.
> 
> Verify that the solution of (2.153) becomes
> 
> \[T(x) = T_B + \frac{(T_c - T_B) \left[ \frac{1}{\ell_B} \cosh(x/\ell_B) + \frac{h_f}{k} \sinh(x/\ell_B) \right]}{\frac{1}{\ell_B} \cosh(L/\ell_B) + \frac{h_f}{k} \sinh(L/\ell_B)} + \frac{\frac{h_f}{k} (T_f - T_B) \sinh((L - x)/\ell_B)}{\frac{1}{\ell_B} \cosh(L/\ell_B) + \frac{h_f}{k} \sinh(L/\ell_B)} \]

One of the other major problems that makes space unfriendly to human bodies is the high radiation levels. On Earth, we are protected by the atmosphere and its structure from most of the harmful sun's radiation. In other words, without a strong magnetic field and atmosphere, such as those provided by the Earth, we cannot escape high levels of radiation in other space environments in our solar system. As illustrated in Figure 2.45c, the high radiation is so penetrating that it can reach internal organs, the human's entire body, in a matter of minutes and even seconds because high radiation is accompanied by significant changes in blood perfusion. As we can see in Figure 2.45d, in a matter of seconds, organs are affected and death may occur nearly instantaneously. On the surface of the Moon, for example, the lack of an atmosphere exposes human bodies to radiation without mitigation. On Mars, with a thin atmosphere, only about 1 percent of the Earth's (see Ikelle, 2023a), the radiation level is so intense that underground habitats (e.g., caves/lava tubes) are being considered, along with strongly shielded vehicles for excursions on Mars's surface. In fact, harmful radiation is more of a deterrent to human space travel than variations in gravity fields.

> Example: 1D unsteady-state nonlinear bioheat solution. Tumors are known to have a different perfusion rate than normal healthy tissue, as mentioned earlier. Blood flows through them more quickly than healthy tissues. Therefore, the ability to know the effects and measurements of this abnormal perfusion rate helps evaluate the size and severity of a tumor. By varying the blood perfusion, it is possible to examine the effect that different volume flow rates of blood have on the heat transfer inside the biological bodies. In a number of hyperthermia treatments, blood perfusion is usually assumed to vary in the following exponential form
> 
> \(\omega_b(T) = a_1 \exp(a_2 T) \),
> 
> (2.158)

![](img/f5b5b8709fc3a81631262f22d3552c5e_271_0.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_271_1.png)

## Figure 2.45. (Continued.)

where $a_1$ and $a_2$ are positive constants with $a_1 = 0.0002\ 1/s$ and $a_2 = 0.008$ being the typical values for normal healthy tissue and $a_1 = 0.002\ 1/s$ and $a_2 = 0.008$ for tumors. For small values of $a_2$ such as $a_2 = 0.001$, the exponential blood-perfusion rate is almost linear because $a_2^2$ is very small, therefore the quadratic

![](img/f5b5b8709fc3a81631262f22d3552c5e_272_0.png)

Figure 2.45. The temperature distribution as a function of depth and time for a 1D unsteady-state linear bioheat: (a) q_w = 40 W/m³ and ω_b = 0.0007 1/s; (b) q_w = 1400 W/m³ and ω_b = 0.0007 1/s; (c) q_w = 1000 W/m³ and ω_b = 0.0003 1/s; and (d) q_w = 1400 W/m³ and ω_b = 0.0003 1/s.

![](img/f5b5b8709fc3a81631262f22d3552c5e_273_0.png)

Figure 2.46. The temperature distribution as a function of depth and time for a 1D unsteady-state nonlinear bioheat: (a) a₁ = 0.0002 1/s, a₂ = 0, and cₚ = c_b = 4200 Ws/kg/K; (b) a₁ = 0.002 1/s, a₂ = 0, and cₚ = c_b = 4200 Ws/kg/K; (c) a₁ = 0.0002 1/s, a₂ = 0.008, and cₚ = c_b = 4200 Ws/kg/K; and (d) a₁ = 0.002 1/s, a₂ = 0.008, and cₚ = c_b = 4200 Ws/kg/K.

temperature-dependent blood perfusion and the higher terms of the Taylor expansion are negligible. Figure 2.46 shows the temperature distribution as a function of distance and time for exponential and constant blood-perfusion rates. The highest temperature is found to exceed 45 degrees Celsius, due to the nonlinearity of the bioheat-transfer equation.

**Computational exercise:** Consider the following one-dimensional unsteady bio-heat with radiative heat:

$$\frac{\partial T(x,t)}{\partial t} = \alpha \frac{\partial^2 T(x,t)}{\partial x^2} + \omega_b (T_b - T(x,t)) + h \left[ T_\infty^4 - T^4(x,t) \right] ,$$

where $T(x,t)$ is the temperature distribution in the body segment, $T_\infty$ is the surrounding temperature. The time step of explicit finite-difference modeling (see Ikelle and Amundsen, 2018) can be written as follows:

$$T_{n+1,j} = \frac{U_n}{D_n},$$

where

$$U_n = T_{n,j} \left(1 - \frac{\Delta t}{(\Delta x)^2}\right) + \frac{\Delta t}{(\Delta x)^2} \left(T_{n,j+1} + T_{n,j-1}\right) + \frac{h \Delta t}{T_b^4} \left[T_{n,j}^2 + T_\infty^2\right] \left[T_{n,j} + T_\infty\right] T_\infty$$

and

$$D_n = 1 + \frac{h \Delta t}{T_\infty^3} \left[T_{n,j}^2 + T_\infty^2\right] \left[T_{n,j} + T_\infty\right].$$

with the following initial $T_{0,j} = T_0 \sin(\pi \times j \times \Delta x / L)$, and BCs $T_{n,0} = T_1$ and $T_{n,N} = T_2$. Develop a Matlab script for this problem.

## 2.5. Heat Engines and Pumps

When the two reservoirs are brought into direct contact, an amount of heat is transferred from the high-temperature reservoir to the low-temperature reservoir (Figure 2.1). No work is produced by this process. Also, this process is the reason you cannot cool your kitchen by leaving your refrigerator open! When the two reservoirs are not in direct contact, and an engine is used to transfer heat from the high-temperature reservoir to the low-temperature reservoir by engine doing work; we have the basic principle of design of heat engine. Thermodynamics originally grew from the desire to design and build efficient versions of such heat engines, before it becomes central to all theoretical sciences through the discovery of entropy and the first and second laws of thermodynamics by Carnot, Clausius, Kelvin, Planck, Gibbs, and Carathéodory. So a heat engine is a physical or theoretical device that converts thermal energy (heat) to mechanical output (work). It operates in a cyclic process—that is, it periodically returns to its initial conditions, repeating the same process over and over. Examples of heat engines include power plants that produce electricity, internal combustion engines of automobile, steam engines, and jet engines. We here describe the basic components of heat engines and how they are related to the second law of thermodynamics. We also describe pump engines, which are just reverse-heat engines; they take heat from a cold reservoir and transfer it to a hot reservoir. Refrigerators and air conditioners are typical examples of pump engines.
