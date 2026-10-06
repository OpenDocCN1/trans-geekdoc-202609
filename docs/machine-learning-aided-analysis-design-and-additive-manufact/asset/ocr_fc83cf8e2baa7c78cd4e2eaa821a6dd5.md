![](bbox=[0.218, 0.175, 0.762, 0.417])

**Figure 10.9** Representative volume element examples for porous layers.
Source: Images used for training CNNs.

material properties of porous layers are deterministic and computed via Eqs. (10.6–10.8).
The bending analysis of the described FG porous beam is performed within the framework of Timoshenko beam theory:

```
$u^x(x,z) = u(x) + z\varphi(x)\nw^x(x,z) = w(x)$ (10.12)
```

in which $u^x(x,z)$ and $w^x(x,z)$ represent the axial and transverse beam displacements, $u(x)$ and $w(x)$ denote the corresponding displacement components on the mid-thickness plane, and $\varphi^x(x)$ reads the cross section rotation. Consequently, the normal and shear strains are expressed as [17,50,51]:

```
Normal strain $\varepsilon_{xx} = \partial u(x)/\partial x + z\partial \varphi(x)/\partial x$ (10.13)
```

```
Shear strain $\gamma_{xz} = \partial w(x)/\partial x + \varphi(x)$ (10.14)
```

```
Normal stress $\sigma_{xx} = \left(\\frac{E}{1-v^2}\right)\varepsilon_{xx}$ (10.15)
```

```
Shear stress $\sigma_{xz} = G\gamma_{xz}$ (10.16)
```