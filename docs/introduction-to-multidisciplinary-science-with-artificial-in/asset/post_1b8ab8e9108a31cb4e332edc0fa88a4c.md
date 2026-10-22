
rising material and the lithospheric rocks that it contacts.

## Thermal geotherm.

Deriving the geotherm of the mantle comes down to solving the convection-diffusion equation, in (2.67) or in (2.69). This equation is also known as the advection-diffusion equation. In this first example, we assume the thermal steady state (i.e., ∂T/∂t = 0), and no radioactive heat production rate (i.e., q' = 0), and that horizontal heat flow is not important so that we can reduce the problem to a one-dimensional one (i.e., 1D assumption). Equation (2.69) becomes

```
\left( u_z \frac{\partial T}{\partial z} - \alpha \frac{\partial^2 T}{\partial z^2} = 0 \iff T(z) = C_1 [\exp(Pe z) - 1] + C_2 , (2.119)
```

where Pe = (u_z × L)/α is the Péclet number (a dimensionless number, named after the French physicist Jean Claude Eugène Péclet), L is the length scale of the convection process (e.g., the width of a fluid duct), u_z is the flow velocity, α is thermal diffusivity, and C₁ and C₂ are the integration constants resulting from the integration of the simplified diffusion equation twice with respect to z. We here assumed that u_z and α are constants. The Péclet number can alternatively be written in term of diffusion and advection times, as follows:

```
Pe = \frac{t_{diffusion}}{t_{advection}} = \frac{L^2 u_z}{L \alpha} = \frac{L u_z}{\alpha} . (2.120)
```

We can see that if Pe ≪ 1 then, advection can be neglected and the processes will be diffusion dominated. Temperatures can be modeled with u_z = 0 in (2.119). If Pe ≈ 1, then both advection and diffusion terms must be included in the modeling of temperatures. If Pe ≫ 1 then advection plays the dominant role in the modeling of temperatures.

To obtain C₁ and C₂ in (2.119), we assume constant temperatures at the top of mantle (i.e., T = T_S at z = 0) and the bottom of mantle (base mantle) (T = T_M at depth z = z_M). The analytical solution of the 1D steady advection-diffusion equation in (2.119) is then

```
T(z) = (T_M - T_S) \frac{\exp(Pe z) - 1}{\exp(Pe z_M) - 1} + T_S . (2.121)
```

Figure 2.29 shows this geotherm for various values of Pe. When Pe = 0, the advection-diffusion equation in (2.119) reduces to pure diffusion transport; i.e.,

```
\frac{d^2T(z)}{dz^2} = 0 \iff T(z) = C_1' z + C_2' , (2.122)
```

where C₁' and C₂' are the integration constants. For T(z = 0) = 0 = C₂' and at T(z = z_M) = T_M = z_M C₁', the geotherm is a straight line between z = 0 and z_M like in oceanic crust, as illustrated in Figure 2.29; i.e.,

```
T = T_M \frac{z}{z_M} . (2.123)
```

When Pe is positive, the flow direction is from the top of the mantle to the base of the mantle. For large Pe values, T_S prevails almost everywhere except the small
![](img/f5b5b8709fc3a81631262f22d3552c5e_238_0.png)

Figure 2.30. The steady advection-convection Peclet number. Pe = 10 indicates fluid advection and Pe = 0.1 indicates thermal conduction.

linear case (see Figure 2.30b), when the exponential factor is positive and quite late age (see Figure 2.30c), compared to the linear case when the exponential factor is positive. Similarly, the temperature-dependence of thermal conductivity can cause the steady states of advection to tend toward those of geothermal conduction, when the exponential factor is positive (see Figure 2.30d) or to further limit the temperature variations to the base of the mantle (see Figure 2.30f). In other words, the temperature-dependence of thermal conductivity is central in fitting observed or inferred temperature distributions to a particular heat model of the subsurface.

> Quiz: Is the Péclet number mainly positive or negative for glaciers? Explain your answer.

## Example: Adiabatic geotherm.

We here derive the temperature gradient of the mantle under the assumption of no heat exchange occurs during convection (that is constant entropy); i.e., (dT/dz)_S . This gradient is known as the adiabatic gradient and the corresponding geotherm as adiabatic geotherm (or adiabat). We refer to the gradient derived in the previous example as thermal geotherms. Remember that constant entropy means that no heat is lost or gained in the process under consideration. So the adiabatic gradient

and adiabatic gradients. In general we can write the thermal gradient as follows:

$$\frac{dT}{dz}=\underbrace{\left(\frac{\partial T}{\partial P}\right)_S\frac{\partial P}{\partial z}}_{\text{Adiabat}}+\underbrace{\left(\frac{\partial T}{\partial S}\right)_P\frac{\partial S}{\partial z}}_{\text{Non-adiabat}}.$$ (2.133)

Notice that the first term on the right-hand side includes the adiabatic gradient and the second term is obviously zero for adiabatic geotherm (adiabat). The second term characterizes the mantle’s convection, including its vigor.

## Example: Solidus and liquidus.

Along with adiabatic geotherms, solidus and liquidus are other limits of thermal geotherms of solid Earth. Solidus (also known as the melting curve) is the curve above which rocks start to melt. Liquidus is the curve above which rocks become entirely liquid. Both the geotherm and melting-point curves generally increase gradually with depth (see Figure 2.32). Despite the large increase in temperature, materials are not necessarily melting because of the simultaneous increases in temperature and pressure. Materials under increasing temperature tend toward being liquid and under increasing pressure tend toward being solid. This dynamic allows the melting-point curve to also increase with depth. Generally, the melting point curve increases more rapidly with depth than the geotherm, as illustrated in Figure 2.32.

Our knowledge of solidus and liquidus is derived from laboratory experiments of melting key subsurface materials, namely, olivine, peridotite, basalt, granite, and iron. Because of the very high in-situ temperatures and very high in-situ pressures of

![](img/f5b5b8709fc3a81631262f22d3552c5e_241_0.png)

**Figure 2.32.** A schematic diagram of solidus and liquidus of mantle rocks. The dark color indicates solid rock, and the light color indicates molten rock. At a certain depth, with increasing temperature, rock starts to melt. The first melt appears at solidus temperature. Then the amount of the solid portion reduces gradually with more temperature. The rock completely melts beyond liquidus.

![](img/f5b5b8709fc3a81631262f22d3552c5e_242_0.png)

Figure 2.33. (a) In continental areas away from tectonically active zones, geotherm never reaches the solidus (melting points of dry basalt at in-situ pressure; dry granite is also used) instead of the rock; geotherm is always well below mantle solidus temperature, so the mantle does not melt. The melting curves are characterized as dry because we are in a dry environment. (b) At mid-ocean ridges, the temperature increases quickly with depth due to rising hot magma beneath a thin lithosphere. The geotherm crosses the solidus and the mantle starts melting. (c) At hotspots, there is also a zone in which the geotherm exceeds the solidus, leading to melting and magma formation. Mantle plumes also undergo melting as they rise toward the surface. This is known as decompression melting. (d) Temperature increases slowly with depth at subduction zones due to the relatively cool sediments and fluids (i.e., seawater) being subducted along with the old, cold ocean lithosphere. Even though the rock is relatively cool, the solidus (melting point of wet granite at insitu pressure; wet basalt is also used) is depressed by water-bearing rock and sediment, leading to melting and convergent plate boundary volcanism. The melting curves are characterized as wet because we are in a wet environment.

the subsurface, it cannot be replicated in laboratories (e.g., in the core, pressure and temperature conditions can exceed 364 GPa and 5,000 degrees Kelvin, respectively), the solidus and liquidus are obtained by extrapolating the results of experimental data obtained at moderate pressures.

How close the geotherm is to the melting point of a material not only determines whether a material is molten or not, an essential feature for the occurrence of mantle convection, but how stiff it is. Melting begins when the geotherm, including the adiabat, crosses the solidus. In continental areas away from tectonically active zones, the geotherm never reaches the solidus (melting point) of the rock (see Figures 2.33 and 2.34). In mid-ocean ridges, temperature increases quickly due to rising hot
