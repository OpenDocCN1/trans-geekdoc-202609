
202

FG porous composite structures

![](img/90ed165a39fa708ec438fcda79319c25_403_0.png)

![](img/90ed165a39fa708ec438fcda79319c25_403_1.png)

**Figure 15.19** Stress–strain curves of graded foams with different nonmonotonic gradient distributions: (A) highest and (B) lowest local densities; (C) contoured of graded foams with different nonmonotonic gradient densities; (C) highest and (D) lowest local densities. *Source:* Reproduced with permission from Duan Y, Zhao X, Liu Z, Hou N, Liu H, Du B, et al. Dynamic response of actively manufactured graded foams. Compos Part Eng 2020;183107630. Copyright 2020, Elsevier.

In other words, introducing gradient distribution has little influence on the elastic modulus, plateau strain as well as densification strain. Thus a predictive model can be developed to mimic the quasi-static compressive properties of graded foams based on the uniform-foam mechanical properties, as well as the investigation of how gradient distribution controls the plateau stage.

For dynamic tests, the relationship between graded foam and uniform foam is in general similar to the findings in quasi-static tests. The nominal stress–strain curves of uniform and graded foams are compared in Fig. 15.21. Note that the uniform foam U8 and graded foam M1-NG have nearly the same elastic modulus.

Mechanical behavior of additively manufactured functionally graded porous structures 403

![](img/90ed165a39fa708ec438fcda79319c25_404_0.png)

**Figure 15.20** A comparison of nominal stress–strain curves of uniform foam "U8" and graded foam "M1-PG" under quasi-static compression.
Source: Reproduced with permission from Duan Y, Zhao X, Du B, Shi X, Zhao H, Hou B, et al. Quasi-static compressive behaviour and constitutive model of graded foams. Int J Mech Sci 2020;105603. Copyright 2020, Elsevier.

This indicates that the graded foam and uniform foam have the same elastic modulus when their relative densities are identical. Since all cells in foams have the same strain at the elastic stage, the elastic modulus of graded foams is the average of all cells for any gradient distribution.

As seen from Fig. 15.21, the graded foam M1-NG and uniform foam U10 possesses a similar collapse stage (the first peak after the elastic stage). When the foams begin to collapse, the graded foams always collapse initially in their weakest layer (up to 10 MPa). As result, the collapse stress of graded foam depends on the strength of the weakest layer. For the plateau stage, uniform foams exhibit a constant plateau stage where graded foams M1-NG exhibit a gradually increasing plateau stage (Fig. 15.21). This phenomenon can be explained by the successive deformation mode of graded foams since they deform from the weakest layer to the strongest one. When a weaker layer is compressed, the mechanical response would stay at the plateau of the current layer. After the weaker layer totally collapses, a stronger layer continues to sustain the applied load, and the mechanical response follows a new plateau stage in the current layer. This behavior behaves continuously from the weakest region to the strongest region, gradually increasing stress with increasing nominal strain.

404

FG porous composite structures

![](img/90ed165a39fa708ec438fcda79319c25_405_0.png)

**Figure 15.21** Comparison of stress–strain curves of specimens U8, U10, and M1-NG under dynamic compression (20 m/s). *Source:* Reproduced with permission from Duan Y, Zhao X, Liu Z, Hou N, Liu H, Du B, et al. Dynamic response of manufactured graded foams. Compos Part Eng 2020;1831. Copyright 2020, Elsevier.

From Fig. 15.21, the graded foam M1-NG and uniform foam U8 have similar densification stage because of similar relative densities. As foams are compressed into the densification stage, their mechanical properties only depend on the relative density rather than the internal structure.

In conclusion, mechanical properties of graded foams are related to those of uniform foams. At the elastic stage, graded and uniform foams have the same modulus if their relative densities are identical. At the plateau stage, graded foams exhibit multiple plateau stresses of their composition at each layer. At the densification stage, graded foams have similar densification stages to uniform foams with a similar overall density. Hence, the stress–strain curves of graded foams can be predicted by those of uniform foams with different relative densities.

## 15.5 Establishment of predictive model

Firstly, the relationship between mechanical properties and relative densities of uniform foams should be established. By fitting the quasi-static and dynamic experimental data into power-law equations, Eqs. (15.6) and (15.7) can be obtained respectively:

406

Mechanical behavior of additively manufactured functionally graded structures

$$\begin{aligned} \frac{E^*}{E_s} &= 0.756 \left(\frac{\rho_{pl}}{\rho_c}\right)^{1.747} \\ \frac{\sigma^*_{pl}}{\sigma_{ys}} &= 1.096 \left(\frac{\rho_{pl}}{\rho_c}\right)^{1.450} \\ \frac{E^*}{E_s} &= 0.806 \left(\frac{\rho_{pl}}{\rho_c}\right)^{1.369} \end{aligned}$$ (15.6) (15.7)

where $E^*, \sigma^*_{pl}, \sigma^*_{ys}$ are the elastic modulus, collapse stress, and plateau stress of foams, respectively. $E_c$ and $\sigma_{ys}$ are the elastic modulus and the yield stress of the base materials, respectively. The elastic modulus $E_c$ and the yield stress $\sigma_{ys}$ are 11 and 52.86 MPa, respectively.

Secondly, the compression of a graded foam is illustrated in Fig. 15.22. Graded foams deform successfully from weaker regions to stronger regions. As the specimen is compressed to the position $h$, the height of the plastically deformed region (blue region inside foams) is $H-h$. In Figure 15.22 it is assumed that the deformed region is fully compressed as all pores inside foams are compressed to densified. The height of the plastically deformed region (red region in Fig. 15.22) is $h_{deformed}$, where $\rho_{deformed}$ is the average relative density of the plastically deformed region and can be computed:

$$\rho_{deformed} = \frac{\int_0^h \rho(h) dh}{h}$$ (15.8)

where $h$ is the normalized height and can be determined by $h/H$.

![](img/90ed165a39fa708ec438fcda79319c25_406_0.png)

Fig. 15.22 Descriptions of the compression process of a graded foam.

407

Finally, the nominal strain of the specimen can be determined by:

$$\varepsilon = \frac{H-(h\rho_{deformed}}+H-h)}{H} = \tilde{h} - \int_{0}^{\tilde{h}} \tilde{\rho}(h)\mathrm{d}h = f(\tilde{h}).$$ (15.9)$$

Eq. (15.9) gives the relationship between the nominal strain of graded foams and the value of normalized height. When the gradient distribution function $\tilde{\rho}(h)$ is identified, the nominal strain to the normalized height can be given by Eq. (15.9). The gradient density can be expressed as $\tilde{f}^{-1}(\varepsilon)$, therefore the local relative density corresponding to each nominal strain can be determined:

$$\sigma(\varepsilon) = E^*-\sigma_{\text{y}}^*e^{-\varepsilon/\lambda})+\sigma_{\text{y}}^*\varepsilon.$$ (15.10)

$\rho_{\text{av}} = \frac{1}{H}\int_{0}^{H}\rho(h)\mathrm{d}h$ and $\tilde{\rho}=\rho(h)$, where $\kappa$ and $\lambda$ are the shape parameter and the scale parameter, respectively. The shape parameter and the scale parameter are insensitive to the relative density and are 0.0335 and 1.469, respectively. The Weibull distribution is applied to Eq.(15.10) because it captures the elastic stage and the stress-drop region of foams [48]. In addition, as discussed in Section 15.5, the densification stage of graded foams can be determined by using foams with a similar relative density. However, this requires experimental data of considering foams, which brings extra work in practical engineering applications. More, foam material loses its energy absorption potential entering the densification stage. Hence, this stage is not considered in the present elastic, plastic-hardening model for generality and conciseness.

Combining Eqs.(15.6), (15.7) and (15.10), the comparison between the experimental model and the elastic, plastic-hardening model is illustrated in Fig. 15.23.

![](img/90ed165a39fa708ec438fcda79319c25_407_0.png)

Fig. 15.23 Verifications of experimental results of the elastic, plastic-hardening model for (A) quasi-static test and (B) dynamic test.
