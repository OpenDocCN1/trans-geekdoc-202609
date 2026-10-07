# Applied Catalysis: Environment and Energy 353 (2024) 124070

Contents lists available at ScienceDirect

# Applied Catalysis: Environment and Energy

![](bbox=[0.058, 0.066, 0.193, 0.149])

journal homepage: www.elsevier.com/locate/atcatb

![](bbox=[0.833, 0.071, 0.941, 0.103])

# Predicting hydrolysis reaction barriers of large hydrocarbons using machine learning: implications for polymer reconstruction

Xue Zong $^{a,b}$, Tianjie Jie $^{b}$, Dionisos G. Vachos $^{a,b,c,*}$

$^a$Department of Chemical and Biomedical Engineering, 150 Academy St., University of Delaware, Newark, DE 19716, United States
$^b$Delaware Energy Institute (DEI), 221 Academy St., University of Delaware, Newark, DE 19716, United States
$^c$Center for Plastics Innovation, 221 Academy St., University of Delaware, Newark, DE 19716, United States

![](bbox=[0.833, 0.196, 0.891, 0.222])

| ARTICLE INFO | ABSTRACT |
|---|---|
| Keywords: | Calculating activation energies of chemical reactions for large reaction networks is computationally demanding. Brunsted-Evans-Polanyi (BEP) relations are used to predict activation energies, but they are prone to substantial errors. Here, machine learning is used to predict energies for reactions on metals, including Ru, Pt, and Rh. The dataset includes 380 DFT-calculated activation energies of C-C and C-H reactions from C1 to C65. The mean absolute error of BEP is 0.38 eV, providing predictions on hydrocarbons with much larger errors. In comparison, an XGBoost model achieves better accuracy for the DFT-calculated energies. The model selects the most features among reactions and the electronegativity and atomic mass of the metal atoms as keys. The model appears transferable across classes. This approach can provide rapid and accurate estimates of energies for recycling. We showcase the impact of hydrocarbon chain length and branching on barriers, discuss implications for the depolymerization rate of polypropylene and low-density polyethylene, and the feasibility of hydrolysis catalysis.

# 1. Introduction

Plastic waste accumulation in oceans and soils has become an environmental crisis [1]. This issue intensified during the recent pandemic [2], marked by a spike in plastic use. This surge has increased reliance on consumption, contributing to CO2 emissions [3], and landfilling of consumer packaging, forms, and products presents a major challenge for polyfins, like polypropylene and polyethylene, where recycling cycles are low. Chemical recycling [6–8], to provide high yields [9], is a promising approach to converting plastic waste into valuable products.

energies. These are typically derived from density functional theory (DFT) calculations. However, calculating activation barriers of complex reactions is computationally demanding. Correlations, such as the Brunsted-Evans-Polanyi (BEP) relation [23–25], have been developed to estimate reaction barriers by relating them to reaction energies, which are easier to extrapolate beyond the training range. [26–28]. This approach estimates all reaction barriers using a BEP calibration which is unreliable and inaccurate for certain reaction types.

Machine learning (ML) has become an effective approach for evaluating catalyst performance and screening potential catalysts [16–22] but requires accurate MRM parameters, particular activation

To increase the accuracy of predicting activation energies of various reactions, we used deep learning models, which have become more common in [29–34]. Nerskov and co-workers [34] developed an ML model to predict reaction barriers of reactions, with a mean absolute error (MAE) of 0.26 eV, having here 7 additional descriptors besides the reaction energy. Gold et al. [25] developed generalized BEP relationships (gPs) by adding features to describe the change in chemical identity in a reaction. They achieved an error of 0.23 eV for

Corresponding author: Department of Chemical and Biomedical Engineering, 150 Academy St., University of Delaware, Newark, DE 19716, United States.
E-mail: vlachos@udel.edu (D.G. Vachos).

https://doi.org/10.1016/j.jcat.2024.124070
Received 15 January 2024; Received from revised form 7 July 2024; Accepted 11 April 2024
Available online 12 April 2024
©0226-377X © 2024 Elsevier B.V. All rights reserved.