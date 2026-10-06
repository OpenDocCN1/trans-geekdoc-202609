
# Nanoelectronic Devices for Security

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_16_0.png)

FIGURE 1.2 Complementary CMOS inverter having n-MOS and p-MOS.

dissipation. The dynamic power dissipation is given by equation (1.2). The load capacitance $C_L$, and $f$ and $\alpha$ represent the frequency of operation and switching probability.

```
$P_S = V_{DS}I_{\text{OFF}} \quad (1.1)$
$P_D = V_{DS}^2 C_L f \alpha \quad (1.2)$
```

## 1.1.3 Scaling of CMOS

In order to make the device more feasible the power consumption of these transistors could be reduced. The static power dissipation could be lowered by reducing the OFF-state current and the supply voltage. The reduction in supply voltage reduces the ON-state current; thus, it should be lowered very efficiently. The reduction in OFF-state current is another option, which can be achieved by controlling factors discussed in Section 1.7. For reduction in dynamic power dissipation, we need to reduce the parameters load capacitance $C_L$, frequency of operation $f$ and switching probability $\alpha$. The frequency of operation determines the computational speed, so it needs to be increased. The parameter $\alpha$ determines the switching probability of the digital circuit so it cannot be changed. The load capacitance $C_L$ is basically reduced by minimizing the area of MOSFET. This reduction in area of MOSFET allows for scaling of MOSFET. A reduced gate length increases the ON-current, as $I_{ON}$ depends inversely on gate length. A reduced capacitance also increases the frequency of operation. The scaling also reduces the number of transistors on a single chip, which is essential in this era of miniaturization. Thus, scaling is the way forward for reduced power consumption. Constant field scaling and fixed voltage scaling are two methods of scaling done in the industry. In the constant field scaling, which is called Dennard’s scaling rule, the supply voltage is scaled in the same ratio as dimensions of MOSFET. For the fixed voltage scaling, the supply voltage is unchanged. Table 1.1 shows the scaling factor of various device structure parameters.

## 1.1.4 Moore’s Law

One of the famous laws which had predicted the scaling of transistors accurately is Moore’s law. G. Moore had forecasted that the scaling of transistors on a single chip will double after every 18 months. This law worked perfectly for around 40 years through CMOS scaling till 2010 [2]. However, the MOSFET's gate length became almost equivalent to the depletion region at drain-channel and source-channel interfaces, this law became inaccurate. Due to several effects caused by short channel effects, the device electrostatics of MOSFET have slightly changed. These short channel effects have a degrading effect on the MOSFET that will be discussed in the next section (1.2)

## TABLE 1.1 Dennard Scaling Rules

| DEVICE PARAMETER | FACTOR OF SCALING |
|---|---|
| Device dimensions $T_{ox}, W, L$ | $1/k$ |
| Doping concentration $N_a$ | $k$ |
| Delay time per circuit $\tau$ | $1/k$ |
| Capacitance $C A/t$ | $1/k$ |
| Current $I$ | $1/k$ |
| Voltage $V$ | $1/k$ |
| Power dissipation $VI$ | $1/k^2$ |
| Power density $W/A$ | 1 |

## 1.1.5 Komey's Law

A new law that predicted scaling in a slightly different perspective was Komey's law. Jonathan G. Komey had predicted that the number of computations performed by a microprocessor for a unit power consumption would double after 18 months. The number of computations at peak frequency doubled due to reduced power dissipation and increased operating speed as scaling after every 18 months. This was reported for the first time by J G. Komey. This law has held better than Moore's len, ever after 2010, when the short channel effects began to dominate the MOSFET electrostatics. Thus, in the era of aggressive scaling, the short channel effects have played a vital role, which is discussed in the subsequent section.

## 1.2 SHORT CHANNEL EFFECTS

When the device dimensions (channel) of the MOSFETs are similar to depletion lengths at source-channel interfaces and drain channel interfaces, it is called short channel MOSFET. There is an alarming increase in the OFF-state current attributable to these effects at sub-100 nm gate lengths. The reduction of threshold voltage with device dimensions is also present. The decrease in $I-V$ curves and the effect of drain bias on threshold voltage are some common problems in these devices. These phenomenon are known as short channel effects, which are discussed here.

### 1.2.1 Subthreshold Slope 'SS'

Subthreshold swing is treated as the quantity of gate voltage required a decade change in drain current. The equation of SS for a MOSFET is given as equation (1.3).

```
$SS = (kT/q) * \log (1 + (C_D /C_{OX})) \quad (1.3)$
```

In this equation, $k$ is the Boltzmann's constant, $T$ is the temperature, $q$ is the charge and $C_D, C_{OX}$ are the capacitances of depletion region and oxide, respectively. subthreshold slope determines the amount of current for a gate voltage. As $C_D \gg C_{OX}$, the SS for a MOSFET is restricted by the Boltzmann's limit $kT/q$ to 60 mV/dec. For a short channel device, it is severely hampered, as the OFF-state current is larger for a given threshold voltage.

### 1.2.2 Drain Induced Barrier Lowering 'DIBL'

As the channel length reduces, the depletion regions at drain-channel and source-channel interface begin to encounter each other. The electric field coupling takes place, and it affects the barrier height at source-channel interface. This lowering of barrier height at source-channel interface rises the leakage current in MOSFET. Thus, the control on the channel is loosened. The channel is also modulated by the application of drain bias. The drain acts as a second gate in the transistor. This is the 2D behavior of the transistor. It also results in poor saturation behavior of the transistor. This behavior is called drain induced barrier lowering (DIBL), as shown in Figure 1.3. In modern devices, as the channel length decreases, this is a serious challenge for device engineers.

### 1.2.3 Channel Length Modulation (CLM)

When the drain voltage $V_{DS}$ becomes greater than gate overvoltage $(V_{GS}-V_T)$, pinch-off of the channel occurs at the drain side. This reduction in channel length $\Delta L_G$ introduces a change in $I_D$ given by the equation (1.4).

```
$I_D = I_{Dat} / (1 - \Delta L_G / L_G) \qquad (1.4)$
```

This $\Delta L_G$ is significant with respect to $L_G$ in short channel devices as opposed to long channel devices. $\Delta L_G$ has a strong dependence on $V_{DS}$. Thus, for channel devices, this channel length modulation introduces a non-saturation behavior in the output characteristics of the transistor shown in Figure 1.4. The threshold voltage $V_T$ is also reduced for short channel lengths $L_G$. This effect is called as the threshold voltage roll-off. This also affects the $I_{ON}/I_{OFF}$ ratio of the device.

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_18_0.png)

FIGURE 1.3 DIBL in MOSFET.

### 1.2.4 Gate-Induced Leakage (GIDL)

Before explaining the physics of GIDL, we need a brief review about the tunneling phenomenon. Tunnelling is a quantum-mechanical phenomenon where the wave particles are able to penetrate through barrier greater than their energies. Similarly, in an ultra-scaled MOSFET or other devices ($L_G < 100$ nm) where the drain side conduction band is in close proximity of the channel valence band, the electrons are able to tunnel through the potential barrier shown in Figure 1.5a. The electrons in the filled valence band on the channel find empty states in the drain side conduction band. The electrons tunnel through the potential barrier instead of going over, as they famously called band-to-band tunneling (BTBT). This BTBT is of two types—lateral and transverse. Lateral BTBT takes place when electrons tunnel laterally from the channel to the drain region in the direction of electron flow. Transverse BTBT takes place when electrons tunnel perpendicular to the direction of electron flow. It usually happens under the drain region when gate/drain overlap is formed by diffusion of dopant atoms from the channel either side (Figure 1.5b). BTBT-induced GIDL is responsible for conduction of electrons even at negative gate voltages, degrading the transistor performance (Figure 1.5c).

### 1.2.5 Doping Gradient

Another very common problem associated with a short channel MOSFET is the realization of ultra-steep doping gradients or junctions at short channel lengths. A MOSFET contains a junction on either side of the channel, that is drain-channel and source-channel junctions. The doping concentration of drain and source regions are naturally $10^{20}$ $	ext{cm}^{-3}$, while the channel is comparatively doped at $10^{17}$ $	ext{cm}^{-3}$. The doping gradients are generally 2–3 nm/decade in ion-implantation processes. This consumes a large chunk of channel region from either side to side bringing the doping concentration down to $10^{17}$ $	ext{cm}^{-3}$ (channel) to $10^{20}$ $	ext{cm}^{-3}$ (source/drain). This leads to a large area of channel with high doping concentration in a lower gate level MOSFET. This diffusion of dopant atoms is unavoidable, as high temperature annealing is used.
