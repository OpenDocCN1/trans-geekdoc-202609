
## MULTIVARIABLE SENSOR BASED ON MXENE AND MACHINE LEARNING FOR SELECTIVE DETECTIONS OF VOCS

Dongsheng Li, Mengjiao Qu, Qian Zhang, and Jin Xie*

State Key Laboratory of Fluid Power and Mechatronic Systems, Zhejiang University, Hangzhou, Zhejiang 310027, China

## ABSTRACT

Two-dimensional transition metal carbides/nitrides, known as MXenes, have recently received significant attention for gas sensing applications. However, MXenes have strong adsorption to many types of volatile organic compounds (VOCs), and therefore gas sensors based on MXenes generally have poor selectivity. Herein, we developed a Ti3C2Tx based multivariable sensor which allows identification of different VOCs, and concentration prediction of the target VOC in variable backgrounds. The sensor’s responses from the broadband impedance spectra create a unique fingerprint for each VOC. Based on the methodologies of principal component analysis and linear discrimination analysis, we demonstrate highly accurate identifications for different types of VOCs and mixtures using this multivariable sensor. Furthermore, we demonstrate an accuracy of 93.2% for the prediction of ethanol concentrations in the presence of different concentrations of water and methanol. The high level of identification and concentration estimation shows the great potential of MXene based multivariable sensor for detection of target VOCs in the presence of known and unknown interferences.

## KEYWORDS

MXene; 2D Material; Selectivity; Multivariable VOC Sensing; Broadband Impedance Spectra.

## INTRODUCTION

Gas sensing has attracted considerable research interests in recent years [1, 2]. In particular, detection of volatile organic compounds (VOCs) in exhaled breath is regarded as a promising method for early diagnosis of illness [3]. Around 200 VOCs have been detected in human breath and the contents of these VOCs reflect a person’s physical conditions [4]. Accordingly, gas sensors are required not only to sensitively detect an individual VOC but also to effectively distinguish different VOCs and quantify the specific target VOC in the presence of a complex background.

Two-dimensional (2D) materials are among the most promising materials for gas sensing applications, because of their large surface area, versatile surface chemistry, and capability of sensitive detection at room temperature [5]. Recently, gas sensors based on a new family of 2D materials called MXene have also shown promising performance [6]. As one of the 2D transition metal carbides/nitrides, MXenes possess a metallic conductivity, while their surfaces are covered with functional groups. Such a good combination makes MXene based gas sensors having ultrahigh signal-to-noise ratios and low limit of detection compared with those based on the other 2D materials.

However, MXenes have strong adsorption to many types of VOCs. The selectivity of these MXene based VOC sensors remains a key challenge. The poor selectivity can be mitigated through combining sensors into arrays [7]. However, increasing number of sensors in the sensor array increases the possibilities of breakdown. A recent breakthrough comes from the multivariable sensor [8], in which one individual sensor can generate multi-dimensional signals similar to those produced by the sensor array. These multivariable sensors are mostly relied on varying the temperature of the sensing element to overcome cross-sensitivity of those sensors based on the measurement of resistance (or capacitance) [9]. Nevertheless, a permanent change of material properties for the sensing layer may occur when temperature cycling is applied.

Herein, we propose a Ti3C2Tx based multivariable sensor which allows identification of different types of VOCs, and estimation of concentration for the single VOC within a multiple VOCs mixture. In this method, we deposit a thin film of Ti3C2Tx on the surface of an interdigital electrode (IDE) to form a multivariable sensor, which was then exposed to a range of different VOCs with various concentrations. The broadband impedance spectra of the Ti3C2Tx based sensor were obtained at various conditions. They were then used as the inputs for supervised and unsupervised machine learning, and the impedance responses obtained at different frequencies were analyzed systematically. To the best of our knowledge, this is the first report of a multivariable sensor based on MXene and broadband impedance spectra.

## EXPERIMENTAL SECTION

### Fabrication of MXene based multivariable sensor

A schematic illustration of the fabricated Ti3C2Tx based sensor is shown in Fig. 1a. The sensor was prepared by covering the fabricated IDE with a layer of Ti3C2Tx. Two atomic layers of carbon were sandwiched between three atomic layers of titanium in the Ti3C2Tx structure. With a typical synthesis method, we expect that the surface of Ti3C2Tx would be randomly terminated with hydroxyl (-OH), oxygen (-O), and fluorine (-F) groups. An IDE was made on Al2O3 ceramic substrate (5 mm × 5 mm) with 11 pairs of interdigitated Au/Ni/Cu electrodes (thicknesses of 10 μm / 4 μm / 1 μm). The distances among Au strips and their widths were both 100 μm. A dispersion of Ti3C2Tx in deionized water with a concentration of 0.05 mg/mL was dropped on the prepared IDEs and dried in a vacuum chamber, thus forming a sensing layer.

### Analysis of Ti3C2Tx based sensor data

The sensing performance was investigated by exposing the Ti3C2Tx based multivariable sensor to various concentrations of the different VOCs. The broadband impedance spectra (with frequencies from 20 Hz to 2 MHz)

![](img/0a26dfd3b403563edffabb903a3a54f8_1_0.png)

Figure 1: (a) Schematic illustration of the Ti3C2Tx film based sensor. (b) SEM image of the Ti3C2Tx based sensor surface. (c) Cross-section view of the Ti3C2Tx film.

![](img/0a26dfd3b403563edffabb903a3a54f8_1_1.png)

Figure 2: Contour plot of unique fingerprint patterns of different VOCs.

![](img/0a26dfd3b403563edffabb903a3a54f8_1_2.png)

Figure 3: 3D plot of the first 3 principal components of oxygenated (a) and non-oxygenated (b) VOCs.

of the sensor were measured. The response was defined as the relative change in the impedance of the sensor after exposure to VOCs compared to the baseline impedance (ΔR(X)/R0(X0) (%)). Predictive models were developed using eight representative parameters obtained from the broadband impedance spectra, i.e. using the resistance values at 20 Hz, 336 kHz, 2 MHz, and the reactance values at 189 kHz, 299 kHz, 710 kHz, 1.19 MHz, 2 MHz. First, principal component analysis (PCA) was applied for classification of multivariate data and to reduce the dimensionality of the original data set. PCA is a powerful unsupervised analysis tool that allows a qualitative survey of the discriminating power of the sensor [10]. The linear discrimination analysis (LDA) was performed as a supervised pattern recognition tool meaning that the correct classification is known for each object. The resultant principal components in the PCA were used as input variables to the LDA to quantitatively identify different test analytes [11]. A cross-validation method was used to estimate the identification. To quantify concentrations of individual vapor in a mixture, we applied partial least squares (PLS) with five latent variables (LVs) [8]. Multivariate data processing (PCA, LDA and PLS) was carried out in MATLAB programs in this study.

## RESULTS AND DISCUSSION

The surface morphology of the Ti3C2Tx based sensor is shown in Fig. 1b, which reveals a uniform deposition of the Ti3C2Tx film. A cross-sectional SEM image of the Ti3C2Tx film is shown in Fig. 1c, which is produced through vacuum filtration of the same Ti3C2Tx solution used for the sensor fabrication. The observed layered structure is due to the ordered stacking of individual layers of Ti3C2Tx, which results in increased surface-to-volume ratio, potentially contributing to a large sensing response. The Ti3C2Tx based sensor was exposed to eight different VOCs (i.e. methanol (MeOH), ethanol (EtOH), acetone, isopropanol (IPA), acetonitrile (MeCN), dichloromethane (DCM), hexane, and toluene (TOL)) with different concentrations from 100 ppm to 800 ppm, and the broadband impedance spectra were measured. Based on the impedance spectra obtained, we selected eight representative parameters mentioned above as the VOC
