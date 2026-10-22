
![](img/f5b5b8709fc3a81631262f22d3552c5e_228_0.png)

Figure 2.24. Here are lithosphere thermal geotherms under the thermal linear unsteady state and horizontal heat flow (one-dimensional one) with no heat production, as described in (2.113). The thermal diffusivity here is the order of that of granite; that is, α = 8 × 10⁻⁷ m²/s.

By taking the derivative of (2.113) with respect to z, we obtain conductive heat flow versus age; i.e.,

$q = -k \left.\frac{\partial T(z,t)}{\partial z}\right|_{z=0} = -\frac{k(T_M - T_S)}{\sqrt{\pi \alpha t}}. \qquad (2.114)$

In other words, the heat flow at the surface decreases with increasing age as one might expect.

Let us now add internal heat generation to our unsteady heat-conduction equation. We can use the finite-difference scheme described in Ikelle and Amundsen (2018) to solve this equation. Here is an example of a Matlab script:

```
L = 30 * 10^3; tau = 1 * 10^(15); TS = 0;
TM = 800.00; Ti = 800;
alpha = 8.0645e-7; q = 15.0e-6; rhocp = 3.1 * 10^6;
nx = 100; dz = L/(nx - 1); dt = 0.25 * (dz^2/alpha); nt = tau/dt;
r = alpha * dt/dz^2; s = q/(rhocp) * dt; T = zeros(nx + 1,1) + Ti;
T(1) = TS; T(nx + 1) = TM;
for n = 1 : nt; Told = T; for j = 2 : nx
    T(j) = Told(j) + r * (Told(j + 1) - 2 * Told(j) + Told(j - 1)) + s;
end;
TF(:,n) = T(:); end
[M, c] = contour(TF,9); colormap; c.LineWidth = 1.05;
```

## Radiation, Conduction, and Convection

![](img/f5b5b8709fc3a81631262f22d3552c5e_229_0.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_229_1.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_229_2.png)

Figure 2.25. Here are lithosphere thermal geotherms under the thermal linear unsteady state and horizontal heat flow (one-dimensional one) with no heat production, as described in (2.113). The thermal diffusivity here is α = 8 × 10^{-7} m²/s, the surface heat flux is q₀ = 8 × 10^{-2} W/m², and the thermal conductivity is k = 2.0 W/m°C.

The results in Figure 2.25, for T(z, t = 0) = T_M and T(z, 0, t) = T_S, show that even uniform heat production has significant effects on the temperature profile. In addition to the creation of the ocean crust, it is possible to model decreasing temperatures with increasing depth when heat production is very high. Because large heat production is rare in the ocean crust, the occurrence of the temperature profile, in Figure 2.25c, is more likely in the continental crust.

## Example: Nonlinear heat-conduction equation.

> ρcP ∂T/∂t = ∂/∂z [ k(T) ∂T/∂z ] + q' , (2.115)

> ρcP ∂T/∂t = k(T) ∂²T/∂z² + dk(T)/dT (∂T/∂z)² + q' . (2.116)

## Table 2.10. The Matlab commands for predicting the nonlinear Earth's crust geotherm.

```
clear all; close all; rho=3*10^3; cp=2.5*10^3; k0=2.5; b0=0.0022;
nt=91; nx=81; tfinal=15*10^(13); dt=tfinal/(nt-1); A=rho*cp/dt;
x0=0.01*10^3; xL=30*10^3; dx=(xL-x0)/(nx-1); T0=0.75*10^3; TL=1.5*10^3;
x=zeros(nx,1); TT0=zeros(nx,1); t=zeros(nt,1);
TT1=zeros(nx,1); TT=zeros(nx,1);
Tnew=zeros(nx,1); G=zeros(nx,1); TF=zeros(nx,nt);
for i=1:nx; x(i)=x0+(i-1)*dx; TT0(i)=TL; end;
for n=1:nt; t(n)=(n-1)*dt; end;
L=zeros(nx,nx); L(1,1)=1; L(nx,nx)=1; TF(:,1)=TT0;
for n=2:nt
  TT=TF(:,n-1); TT1=TF(:,n-1); eps=1;
  while(eps>0.0001)
    G(1)=TT(1)-T0; G(nx)=TT(nx)-TL;
    for i=2:nx-1
      k=k0*exp(b0*TT(i)); Dk=b0*k; D2k=b0*Dk;
      DT=(TT(i+1)-TT(i-1))/(2*dx); f=(A*(TT(i)-TT1(i))-...
      Dk*DT*DT)/k;
      q=(-f*Dk+A-D2k*DT*DT)/k; p=-2*Dk*DT/k;
      G(i)=TT(i+1)-2*TT(i)+TT(i-1)-dx*dx*f;
      L(i,i-1)=1+0.5*dx*dx*p; L(i,i)=-2*dx*dx*q; L(i,i+1)=1-0.5*dx*dx*p;
    end
    Tnew=TT-L\G; eps=sqrt(dx*(Tnew-TT)*(Tnew-TT)); TT=Tnew;
  end
  TF(:,n)=TT;
end; [M,c]= contourf(x,t,TF'); colormap; c.LineWidth = 1.05;
```

Equation (2.115) is generally solved numerically by using the finite-difference technique using a code like the one in Table 2.10 (see also Ikelle and Amundsen, 2018). Figure 2.26 shows the solutions to linear (i.e., k = k0 = constant, ρ = constant, cP = constant, and q' = 0) and nonlinear conduction-diffusion equations for k(T) = k0 exp(b0 T), ρ = constant, cP = constant, and q' = 0. The temperature increases at a slower rate as one moves deep in the solid Earth for the nonlinear case than in the linear case. The linear solution suggests the lithosphere will not reach a steady state (i.e., a state at which temperatures do not vary time) at an unrealistic age, while in the nonlinear solution steady state, around 2 million years; the thickness of the lithosphere does not grow without limit. The linear and nonlinear solutions in Figure 2.26, along with the linear solutions in Figure 2.25, explain why the thickness of the oceanic crust is smaller than that of the continental crust. Also remember that the most formulas derived in this subsection and the associated figures describe heat flows by conduction down a gradient of decreasing temperature. From the changes in temperatures in Figures 2.24, 2.25, and 2.26, it is clear that thermal conduction in the lithosphere is very slow; about 10 km per a million year or 1 cm/year. The temperature rises more slowly as one moves farther away from the heat source.

## Summary.

To conclude this subsection, let us make some remarks on lithosphere heat flow on geotherm. The crust of continents and oceans (the continental

![](img/f5b5b8709fc3a81631262f22d3552c5e_234_0.png)

temperature was around 6 degrees Celsius cooler than today. For perspective today the average global temperature in the 20th century is 14 degrees Celsius, making the average global temperature back then 8 degrees Celsius.

At best, the CO2 emission of the industrial era, which began in the late 1700s, have a marginal effect on the Quaternary glaciation Ice Age. So far, it is just like most past ice ages. This is a period when thick ice sheets cover vast areas of land, especially near the poles. An ice age lasts for millions of years. The causes of an ice age are still unclear. Major ice causes of ice ages include plate tectonics, ocean currents, and heat distribution. Earth’s climate did not stay freezing cold during the entire ice age. Instead, climate changes between glacial and interglacial periods. Glacials are very cold, and last 100,000 years. Interglacials are a much warmer period between two glacials, and they last between 10,000 and 15,000 years. We are currently in the Holocene Interglacial.

The mantle starts at a 10 to 70 km depth and goes down to the outer core at a 2,900 km depth. Our objective here is to use the convection-diffusion equation in (2.67) and (2.69), which allows us to determine the geothermal of the mantle. We start by defining mantle convection. As illustrated in Figure 3.3a of Ikel (2023a), we need a fluid layer bounded by two surfaces and a heater to produce convection. In

the interior solid Earth, we have convection between the cooler crust (cooler rocks at shallow depth) and the hotter core (hotter rocks at great depth). In other words, the mantle can be described as a layer of fluid heated from below and cooled from above (see Figure 3.33b of Ikelle (2023a)). The “fluids” (mantle plume) here are the sublithospheric mantle’s rocks, which heat up and partially or completely melt in the deeper and hotter mantle. These so-called fluids are viscous (viscosity is the rock’s resistance to flow; it decreases with increasing temperature). In any event, we have mantle convection as first pointed out by Bull (1921) and Holmes (1931).

As pointed out in Ikelle (2023a), convection takes place in fluids (liquid or gas) with a constant density before the change in temperature. It is obvious that the mantle is not a fluid and its density is not homogeneous. Yet mantle-wide convection (or partial mantle convection) is a central tenet of plate tectonics. We will revisit this issue in Chapter 6. However, in the context of building an educational background, which is the main goal of this book, the validity of these assumptions has little effect. If these assumptions are far from reality, we still have to demonstrate to our students how to derive and interpret geotherm related to convention. Moreover, this exercise will help them understand and contribute to future developments in this area.

Here are some mantle parameters (Schubert et al., 2001):

ρ ≈ 4000 (kg/m³)
g ≈ 10 (m/s²)
β = 3 × 10⁻⁵ (K⁻¹)
ν = 10²² Pa·s
ΔT ≈ 3000 K,
d = 2900 km,
α = 10⁻⁶ m²/s
} ⇒ Rₐ ≈ 10⁷

The Rayleigh number is approximately 10⁷, which is well beyond critical although the mantle viscosity is extremely high. However, the mantle is also very hot and very large and hence it is convecting vigorously.

Note again that rock expands as its temperature increases, its density thereby decreases slightly. A one percent expansion requires an increase of 300-400 degrees Celsius and leads to a 1 percent decrease in density. Viscosity is the propensity of rock to ductile flow. Rock does not need to melt before it can flow. The presence of H₂O encourages flow in solid rock. Convection currents bring hot rocks upward from Earth’s interior. The rock in the lithosphere is too cool for convection to continue. Heat moves through the lithosphere primarily by conduction. The lithosphere-asthenosphere boundary is about 1,300 degrees Celsius.

To summarize, solid Earth moves heat via convection and conduction as follows:

Heating → expansion → rise → cooling → contraction → sink .
Mantle                     Lithosphere

Basically, hot material expands and rises, and cold material contracts and sinks through a process of creation and destruction of the oceanic lithosphere. Heat is delivered to the base of the lithosphere by mantle convection that brings hot material to shallower depths, thus releasing pressure, enabling melting of both the
