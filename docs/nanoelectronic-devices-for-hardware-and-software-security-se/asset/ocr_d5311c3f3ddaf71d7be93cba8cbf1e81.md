# 3 Heterojunction Tunnel-Effect Transistor 69

are regulated by the gate biasing voltage. However, in the case of the MOSFET, thermionic emission will oppose the injected charges, due to which high voltage is required to suppress the barrier. This process of tunneling charges from source to channel medium of the device is called the BTBT process [33].

The main advantage of the tunneling phenomena is that the energy band cuts the 'tail' of the Boltzmann electrons in the p-type region [28–29]. This reduces thermal dependency, which allows a steeper subthreshold slope (SS) below the 60 mVdecade. The tunneling current thus obtained can be expressed as in equation 3.2 [34].

```
$I_{BTBT} \approx A e^{\exp\left(\frac{B}{\varepsilon}\right)} \quad (3.2)$
```

Where A and B are material parameters. The p–i–n structured TFET device is reverse biased for the Off-state region, and the leakage current is smaller than in MOSFET. Therefore, TFET has ability to avoid SCEs, can achieve high $I_{ON}/I_{OFF}$ ratio, and is independent of geometrical scaling.

# 3.1.5.2 The WKB Approximation Method

The Wentzel–Kramer–Brillouin (WKB) approximation enables the probability tunneling current to be determined using arbitrary sharp potential barriers. A formal rigorous derivation is detailed in [35]. TFET will employ the BTBT modes (lateral and vertical tunneling). The multiple advantages of perpendicular vertical tunneling to the gate-dielectric interface semiconductor makes it attractive compared to a traditional TFET design. Obtaining high ON current in TFETs is a challenging task, as ION is critically dependent on the transmission probability, $T_{WKB}$ of the barrier can be estimated by a triangular shape, so that $T_{WKB}$ can be measured using the WKB approximation [35].

```
$T_{WKB} \approx \exp\left(-\frac{4\lambda\sqrt{2m^*E_c}}{3hl(E_G + \Delta\phi)}\right) \quad (3.3)$
```

Where the bandgap is $E_G$ and the effective mass is $m^*$. The spatial extent of the transition region at the source–channel interface is defined here by screening length ($\bar{\lambda}$) depending on the specific geometry of the device, shown in Figure 3.7. In a TFET, the gate voltage ($V_{GS}$) at constant drain voltage ($V_{DS}$).

![](bbox=[0.273, 0.653, 0.732, 0.888])

**FIGURE 3.7** BTBT can be calculated by approximating the energy barrier width by a triangular potential energy barrier, where the electrons must tunnel through the widest distance at the base of the triangle.