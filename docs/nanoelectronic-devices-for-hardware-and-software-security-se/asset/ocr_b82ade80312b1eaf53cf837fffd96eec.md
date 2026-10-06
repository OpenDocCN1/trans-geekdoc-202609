# 13.4 EFFECT OF SURFACE ROUGHNESS AT THZ FREQUENCY

As outlined in the introduction, due to intrinsic and unavoidable tolerances, the fabricated structure is not perfectly finished and often possesses irregularities such as surface roughness. As skin depth of the conductor becomes comparable with thickness of the conductor at THZ frequency, it becomes important to study the surface roughness. This study has been done through two analytical models, named (i) the Hammerstad-Bekkal model [7–8] and (ii) the Huray model [9–11]. The simulation results are also systematically presented in this chapter.

Although the metallization process involves microscopic level of roughness in any fabrication method, it does not affect device performance significantly in DC or low frequency application. However, in the high frequency domain it invites some detrimental effects. Conductivity and surface impedance of the metal layer gets changed. This work reports the effect of surface roughness in a metalized wall of a rectangular waveguide (WR-2.2) etched using silicon micromachining. Two well-known mathematical models have been implemented to quantify the effect of roughness in device performance.

# 13.4.1 Hammerstad–Bekkal Model

Here, surface roughness is treated as a series of peaks and valleys, as shown in Figure 13.3a. This model can predict well, while the RMS (root mean square) value of roughness ($h_{RMS}$) is comparable to the skin depth ($\delta_{skin}$) of the conducting layer. The roughness factor ($f_r$) is calculated from $h_{RMS}$ and $\delta_{skin}$ using the closed-form equation 13.1,

```
$f_r = 1 + \frac{2}{\pi} \tan^{-1} \left[ 1.4 \left(\frac{h_{RMS}}{\delta_{skin}}\right)^{2} \right] (13.1)
```

Where

```
$$\delta_{skin} = \frac{2}{\sigma_{smooth}\sqrt{\mu}}$
```

Consequently, the conductivity of the thin metal layer is altered as a function of $f_r$, and operating frequency as follows

```
$$\sigma_{rough} = \frac{\sigma_{smooth}}{f_r}$ (13.2)
```

With the modified conductivity (Figure 13.4a) of the metallic wall of the waveguide structure, its propagation or loss characteristics are also changed, as depicted in Figure 13.4b.