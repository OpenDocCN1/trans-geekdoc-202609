
## CHAPTER 4
Compressional and Shear Sonic Log Determination Using Data-Driven Machine Learning Techniques

*Daniel Asante Otchere,¹,²,* Raoof Gholami,³ Vanessa Nta⁴ and Tarek Omar Arbi Ganat⁵*

### 1. Introduction

Shear (Vs) and Compressional (Vp) sonic waves are significant parameters in subsurface engineering. They provide valuable information for reservoir exploration, development, recovery and fluid sequestration (Azizia et al., 2017; Zoveidavianpoor et al., 2013). These parameters or its ratio are useful in reflection seismology, lithologic identification, and formation evaluation (Castagna et al., 1985), pore fluid and pore pressure information (Duffaut and Landrø, 2007; Rojas, 2008), reservoir characterisation (Eberli et al., 2003; Pickett, 1963), geophysics (Phadke et al., 2000; Waluyo et al., 1995), and geomechanical properties (Asoodeh and Bagheripour, 2014; Rasouli et al., 2011). There are several ways of measuring these parameters, as summarised in Table 4.1.

¹ Centre of Research for Subsurface Seismic Imaging, Universiti Teknologi PETRONAS, 32610, Seri Iskandar, Perak Darul Ridzuan, Malaysia.
² Institute for Computational and Data Sciences, Pennsylvania State University, University Park, PA, USA.
³ Department of Energy Resources, University of Stavanger, Kjell Arholmsgate 41, Stavanger, 4021, Norway.
⁴ Shell Oil Company, 150 N Dairy Ashford Rd, Houston, TX, 77079, United States of America.
⁵ Department of Petroleum and Chemical Engineering, Sultan Qaboos University, Muscat, Oman.
* Corresponding author: ascotjnr@yahoo.com

Table 4.1. Common methods of estimating Vs sonic velocity.

| Methods | Types of Measurement |
|---|---|
| Laboratory | Core measurements |
| Direct | Dipole Sonic Log |
| Empirical Correlations | Castagna, Gassman, Brocher, Carroll and Greenberg-Castagna correlations |
| Machine Learning | Examples of models |

The acquisition of continuous Vs and Vp subsurface data is reliably done via wireline logs. The Dipole Shear Sonic Log, invented in the 1980s, is the most commonly used logging tool used to record the waveform values and process the data to compute Vs and Vp sonic velocity and became ubiquitous in the 1990s (Close et al., 2009). This measuring tool indicates how fast sound propagates through subsurface interfaces. Although the dipole sonic log is available, its expensiveness has rendered the direct measurement of Vs not worth the cost, as such, Vs is not ubiquitous in all wells. This limitation has necessitated further research in estimating Vs from other logs, mainly from the Vp log (Brocher, 2005; Carroll, 1969; Castagna et al., 1985; Dvorkin and Mavko, 2014; Gassmann, 1951; Greenberg and Castagna, 1992). With the advancement of fluid sequestration, geothermal energy, and unconventional resources, Vs and Vp have become more prevalent. However, older wells never acquired Vs and Vp data before the dipole sonic log. Acquiring the data now is not feasible. As such, extensive research is required to provide substantial study in estimating these two logs from other conventional wireline logs. In this study, estimating Vs and Vp from wireline logs using a multioutput supervised machine learning approach is investigated for the Volve field siliciclastic oil-bearing reservoirs. This study is of the utmost significance, especially in more mature fields, as shear and compressional sonic logs were never obtained in old wells. This method would result in better accuracy in predicting compressional and shear sonic logs for hundreds of wells useful for geomechanics, performing well-to-seismic inversion, and other operations.

### 2. Literature Review

Prior to the influx of data, empirical and laboratory techniques have been useful in estimating Vs from Vp. One of the pioneering articles that were published by (Pickett, 1963) established the concept of using the compressional to shear wave velocities ratio as a lithology indicator. Figure 4.1, which has been modified from Pickett’s study, demonstrates the clear distinction in Vp/V that exists between dolomites, limestones, and clean sandstones. According to (Castagna et al., 1985), the Vp/Vs ratio tends to change fairly linearly between the velocity ratios of the end members with increasing composition in binary combinations of quartz and carbonates. The results of this study served as the foundation of several empirical approaches. This study will discuss two of the most commonly used techniques for estimating Vs.

![](img/80b94770dd572ad559c67fa9921bb887_75_0.png)

**Fig. 4.1.** Vs and Vp sonic velocities from *in-situ* sonic and field seismic measurements for mudrocks. Modified after Castagna et al. (1985).

Research conducted by (Castagna et al., 1985) concluded that Vs sonic velocity is directly related to Vp sonic velocity for both water-saturated and dry siliciclastic sedimentary rocks, as shown in Fig. 4.1. Shales tend to have a relatively greater Vp/Vs than clean sandstones, given a similar Vp. From their results, Vp/Vs is almost homogeneous for dry sandstones. Wet sandstones and mudstones exhibited an indirect monotonic relationship between Vp and Vp/Vs. The Vs sonic velocities measured in water-saturated sandstone agreed with those predicted by Gassmann’s equations. This empirical linear relationship between the Vp and Vs sonic velocity in brine-saturated clastic silicate rocks is known as the mudrock line and is expressed from *in-situ* sonic and field seismic measurements as:

$$V_p = 1.16V_s + 1.36 \tag{4.1}$$

This linear equation is partly explained by the location of the clay point near a line joining the quartz point with the water velocity. The equation was formulated assuming that Vp and Vs velocities decrease linearly as increasing clay porosity approaches water. Similarly, when pure clay is mixed with quartz, velocities increase monotonically as the quartz point is approached. These constraints correspond with those deduced from Tosaya and Nur (1982) empirical relations, except for high porosity behaviour.

Greenberg and Castagna (1992) proposed a correlation, the Greenberg-Castagna formulation, for pure unit completely brine-saturated mineral rocks based on linear relations of Vp to estimate the Vs sonic velocity from other petrophysical parameters. To predict Vs sonic velocity of a 100% saturated rock, it is required to perform fluid replacement calculations by utilising Gassman relations. In order to mitigate the major limitation of the Greenberg-Castagna formula, fluid substitution is done when there are hydrocarbon-bearing rocks. It requires several sets of operations known as Gassmann fluid substitutions (Gassmann, 1951). They utilised the regression weights for different lithologies shown in Table 4.2 to satisfy the expression:

$$V_s = a_{i2} V_p^2 + a_{i1} V_p + a_{i0} \tag{4.2}$$

The lines of fit for the lithological regression weights are based on Simm and Bacon (2014). The method's fundamental process entails completing multiple iterations beginning with Vp assumptions for brine until it reaches a considerable convergence, assuring the validity of the Vs prediction. The regression coefficients of Vs are presented in Table 4.2.

Table 4.2. Regression coefficients of Vs presented by Castagna et al. (1993).

| Lithology | ai2 | ai1 | ai0 | R² |
|---|---|---|---|---|
| Sandstone | 0 | 0.80416 | -0.85588 | 0.98352 |
| Limestone | -0.05508 | 1.01677 | -1.03049 | 0.99096 |
| Dolomite | 0 | 0.58321 | -0.07775 | 0.87444 |
| Shale | 0 | 0.76969 | -0.86735 | 0.97939 |
