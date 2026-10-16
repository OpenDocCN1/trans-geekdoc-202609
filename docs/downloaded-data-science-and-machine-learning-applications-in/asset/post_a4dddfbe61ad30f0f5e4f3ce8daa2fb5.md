
![](img/80b94770dd572ad559c67fa9921bb887_53_0.png)

Fig. 3.1. The excitation and relaxation of polarised hydrogen atomic nuclei in response to an external magnetic field (Otchere et al., 2022a).

The concept of using NMR to predict pore fluid types is to use the magnetic properties of certain nuclei to provide information about a reservoir’s fluid composition and rock properties. This prediction is achieved by measuring the proton density and relaxation times of the fluids in the reservoir, which are unique to different fluid types, such as water, oil, and gas. When CMR is used for porosity partitioning, the total porosity is calculated by measuring the magnetic susceptibility of the pore fluids and using the relationship between magnetic susceptibility and fluid volume fraction. This method is based on the assumption that the magnetic susceptibility of the bound fluid is different from the free fluid, which is a key concept in CMR. The following equations are used to calculate total porosity, BFV, and FFV in reservoirs:

(φT) = φB + φF

(3.1)

where the total porosity is represented as φT, which is a dimensionless value between 0 and 1, representing the fraction of the rock sample that is made up of pores, φB is the bound fluid volume fraction, and φF is the FFV fraction.

BFV = φB × Vp

(3.2)

where Vp is the pore volume.

FFV = φF × Vp

(3.3)

V_p is typically calculated by multiplying the bulk volume of the rock sample (Vb) by the total porosity (φT).

$V_p = \phi T \times V_b$ (3.4)

where V_b is the bulk volume of the rock sample, which can be measured by using various techniques such as helium pycnometry, mercury intrusion porosimetry, or gas adsorption. It is worth mentioning that the pore volume can also be calculated by measuring the rock sample’s bulk volume and subtracting the solid grains’ volume from it. This method is known as the grain volume method and is another way to calculate the pore volume. These equations are based on the assumption that the magnetic susceptibility of the bound fluid is different from the free fluid. This means that the bound fluid can be distinguished from the free fluid by measuring the magnetic susceptibility of the pore fluids.

### 2.2 Works Related to the Use of Machine Learning in NMR for Reservoir Characterisation

Machine learning has been extensively employed to complement conventional methods and, in some instances, provide certain advantages. The deployment of machine learning techniques and AI algorithms to overcome intricate issues has gained traction in numerous sectors, including the petroleum industry (Otchere et al., 2021a). The application of machine learning in reservoir characterisation has seen massive growth underlining its importance in this field. Machine learning models have become quite useful in situations where not much data is collected. These models have been used to predict various logs, which, due to time and cost, were not run in wells. These models have illustrated high accuracy compared to actual logs, saving time and money while providing a real-time estimate of reservoir properties during drilling. A review of articles utilising machine learning techniques and NMR data to provide accurate alternatives is presented below.

Rezaee (2022) expounds upon a study that employed an extensive repository of CMR to engender outputs from an NMR logging tool for clastic rocks. The study intended to evaluate the effectiveness of diverse machine learning (ML) methodologies employing customary well-logs as input data. The study generated outputs for CMR data, including irreducible pore fluid (BVI), clay bound water (CBW), producible fluid (FFI), irreducible water saturation (Swirr), logarithmic mean of T₂ relaxation time (T₂LM), and permeability. To this end, well logs from 14 Western Australian wells were gathered, of which 80% were used for model training and validation and the remaining 20% for testing purposes. Upon comparing the outcomes, it was revealed that the Adaptive Boosting (AdaBoost) model demonstrated the most notable results, with R² values exceeding 0.9 for the blind set. These findings indicate that the ML methodology can be employed for the generation of NMR logs with a high degree of precision.

Masroor et al. (2022) describe an ML procedure for estimating NMR permeability from conventional well logs. The methodology employs three supervised (ML) algorithms: group method of data handling, Random Forest (RF), and one-dimensional convolutional neural network (CNN). Additionally, a modified version of the two-dimensional CNN (Residual 2D-CNN) is devised, receiving artificial 2D feature maps derived from conventional logs. The ML and deep learning (DL) models’ hyperparameters are optimised using genetic algorithms to enhance their efficacy. The results indicate that nonlinear machine and DL techniques help estimate NMR permeability, with the Res 2D-CNN model providing the most efficient results (accuracy of 0.97). The study underscores the significance of employing produced feature maps to train the Res 2D-CNN model and the favourable impact of integrating residual and deeper bottleneck architectures in enhancing prediction accuracy and minimising training duration.

Tamoto et al. (2023) also describe a study aimed at developing ML models for the estimation of NMR porosity from well logs. NMR logs are considered valuable for porosity quantification but are limited by high costs and adverse subsurface acquisition conditions. The adjusted RMSE and R² and metrics compared and evaluated four supervised ML models. The best results were achieved with the CatBoost regressor, producing an RMSE of less than 0.01 and an adjusted R² of 0.87. The ML models substantially improved total porosity prediction compared to traditional empirical computations. The dissimilarities between actual NMR logs and the ML predictions were mostly below 5%. Additionally, a porosity model based on well logs was developed using tree boosting, and the impacts of input variables on model estimates were investigated. The study also scrutinised the behaviour of the model’s linear and nonlinear characteristics to comprehend their relationships with the dataset.

Li et al. (2020) present a study on the use of two neural-network-based ML models, long short-term memory (LSTM) network and a variational autoencoder with a convolutional layer (VAEc) network, for the generation of synthetic NMR T₂ distributions from formation mineral and fluid saturation logs. The models are trained and tested on a limited sample of data from the Bakken shale formation. The results show that both models perform well, synthesising fluid-filled pore size distributions even when the input data is corrupted by noise. The proposed method has the potential to improve reservoir characterisation under data constraints. NMR logs provide valuable information on fluid mobility, fluid-filled pore size distribution, fluid mobility, porosity, and permeability in the near-wellbore reservoir volume. However, their acquisition is limited due to financial and operational challenges. Hence, the use of ML can make NMR logs available in all wells.

Gu et al. (2021) present a ML approach to estimate fluid saturation in reservoirs by evaluating fluid components in the T₂-D spectrum. The method integrates a GABP neural network and Gaussian Mixture Model (GMM) to determine a new saturation formula based on the physical significance between the T₂-D spectrum and fluid saturation. The approach is evaluated through numerical simulations, and results demonstrate improved accuracy and stability compared to traditional BP neural networks. The GMM determines different Gaussian probability distribution functions to characterise different fluids in the T₂-D spectrum, leading to more accurate saturation estimates. The proposed method has the ability to quantitatively evaluate fluid components in the T₂-D spectrum.

These studies demonstrate the potential of using ML algorithms to analyse wireline log and NMR data and predict various reservoir properties such as pore-scale properties, permeability, fluid saturations, and fluid types. These methods have been shown to be accurate and have the potential to improve the efficiency and accuracy of reservoir characterisation.

## 3. Methodology

### 3.1 Data Collection and Description

Conventional wireline logs from a vertical exploration gas well were used in this study. The CMR tool was logged in the well. The objective of the CMR logging was to evaluate the formation’s total porosity, bound and free fluid, and permeability. CMR was logged over a carbonate section capped by shale. Over the zone of interest, we do not observe borehole effects on the CMR signal due to a relatively smooth borehole combined with moderate mud salinity (approximately 58 ppk equivalent NaCl using chart GEN-9 with Rmf = 0.0694 ohm·m at 21 deg C). No anomalies were observed on the raw echoes, T2 distribution, total porosity, and bin porosities. Since the well is drilled with water-based mud, the T₂ distribution reflects the pore size distribution. The data used in this study underwent quality control and reprocessing. The parameters selection for the CMR reprocessing used in this study is captured in Table 3.2. Figure 3.2 shows the incremental increase in porosity and multiple pore size distribution with favourable connectivity between pores, identified through the multi-exponential decay time analysis of NMR T₂ distribution in 100% brine saturated samples. The partitioning of the porosity was done as follows:

- 1. Small Pore Porosity (T₂ min to 3 ms) – this can be considered as water-filled porosity associated with clay (water resistivity of Rwb in the Dual Water Saturation model).
- 2. Capillary Bound Fluid (3 ms to T₂ cutoff) – this can be considered part of effective porosity. In clastic rocks, this would be expected to be water
