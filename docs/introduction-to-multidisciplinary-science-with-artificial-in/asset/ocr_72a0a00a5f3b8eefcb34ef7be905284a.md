metal, graphite, or metal sulfides. Note that oil and gas are good insulators and therefore have high resistivities. Brine is a good conductor therefore it has low resistivity.

Remember that fluid saturation is the ratio of the fluid volume to the pore volume in a given sample; i.e.,

$S_w = \frac{V_w}{V_p} , \quad S_o = \frac{V_o}{V_p} , \quad \text{and} \quad S_g = \frac{V_g}{V_p} \text{ with } S_w + S_o + S_g = 1 ,$

where $V_w$ is the volume of water, $V_o$ is the volume of oil, and $V_g$ is the volume of gas, $V_p$ is the volume of pores, $S_w$ is water saturation, $S_o$ is oil saturation, and $S_g$ is gas saturation. In oil and gas exploration and production, it is generally assumed that all pore space not filled with water is occupied by hydrocarbons when rocks are not dry.

In the context of well-logging, we deal with quasi-time-independent electromagnetic fields. Electrostatics and magneto-statics are the branches of electromagnetics corresponding to this case (see Chapter 3). For a charge, $q$, in a sphere with radius $r = |\mathbf{x}|$, the electric current can be written as

$I = \int_S J dS = \int_S (\sigma E) dS = \frac{\sigma q}{4\pi \varepsilon_0 r^2} 4\pi r^2 = \frac{\sigma q}{\varepsilon_0} = \frac{q}{R_t \varepsilon_0} , \tag{5.42}$

where $J = |\mathbf{J}|$, the electric field is

$\mathbf{E}(\mathbf{x}) = \frac{1}{4\pi\varepsilon} q \frac{\mathbf{x}}{|\mathbf{x}|^3} = -\nabla \phi(\mathbf{x}) , \tag{5.43}$

$E(\mathbf{x}) = |\mathbf{E}(\mathbf{x})|$, and the electric potential is

$\phi(\mathbf{x}) = V(\mathbf{x}) = \frac{1}{4\pi\varepsilon_0} \frac{q}{|\mathbf{x}|} . \tag{5.44}$

By substituting (5.44) into (5.42), we arrive at

$V(\mathbf{x}) = \frac{1}{4\pi|\mathbf{x}|} R_t I \quad \text{or} \quad R_t = 4\pi|\mathbf{x}| \frac{V}{I} = K \frac{V}{I} , \tag{5.45}$

where $K = 4\pi|\mathbf{x}|$ is constant for most device.

Resistivity logging consists of electrodes emitting current of intensity $I$ (active source) and electrodes measuring voltage between two points (receiver), $V$, as illustrated in Figure 5.30. We deduce the resistivity $R_t$ for various depths, $z$, as follows:

$R_t(z) = K \frac{V(z)}{I} , \tag{5.46}$

where $K$ is the tool constant related to electrode spacing, the subscript $t$ stands for “true,” and $R_t$ is for true resistivity or resistivity in the uninvaded zone of the formation. We added the adjective *uninvaded* in the properties of the rocks in undisturbed drilling conditions because the act of drilling the borehole is the single most disturbing thing that can happen to a formation, as illustrated in