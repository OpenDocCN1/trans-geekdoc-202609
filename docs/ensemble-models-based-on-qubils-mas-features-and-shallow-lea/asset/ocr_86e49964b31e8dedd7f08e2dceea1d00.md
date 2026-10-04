# Ensemble Models Based on QuBiLS-MAS Features and Shallow Learning for the Prediction of Drug-Induced Liver Toxicity: Improving Deep Learning and Traditional Approaches

Jose R. Mora, Yovani Marquez-Ponce,‡ César R. García-Jacas, and Amileth Suarez Causedo

Cite This: Chem. Res. Toxicol. 2020, 33, 1855–1873

Read Online

ACCESS | Metrics & Mere | Article Recommendations | Supporting Information

![](bbox=[0.313, 0.327, 0.803, 0.488])

ABSTRACT: Drug-induced liver injury (DILI) is a safety concern in drug development and a regulatory concern. Thus, in many drugs are proposed to induce the hepatotoxicity of organic chemicals. Here, classifiers for the prediction of DILI were developed based on 2D-3D descriptors and machine learning techniques on a training set of 1075 molecules. The best ensemble model E13, was obtained with good statistical parameters for the learning series, with the following accuracy = 0.840, sensitivity = 0.890, precision = 0.761; MannWhitney's correlation = 0.660, and under the ROC curve = 0.904. The model was also validated with Y-sampling testing, and repeated k-fold cross-validation and repeated k-fold-validation. In addition, external validation was also carried out using two and five external test sets (accuracy = 0.802, sensitivity = 0.845, precision = 0.715; 98.4% accuracy in its applicability domain). A statistical analysis of the performance of the E13 model, with regard to results and predictions, showed that DAE, Dropout SoftClassifier, Deep Learning, and Random Forest were also presented in the literature. In general, E13 presented the best global performance in all experiments. The sum of the ranking procedures provided a similar grouping procedure to that of the MANOVA statistical analysis, where E13 was identified as the best model for DILI predictions. A recommendation tool for DILI prediction was also developed, which is freely available at http://tomcomond.com/api/ptoxra. This software was used for screening of various data sets, containing natural products, leads, toxic materials, and FDA approved drugs, to assess the usefulness of the QSAR models in the DILI labeling of substances; the evaluated molecules are DILI-like compounds. In all, it is stated that the E13 model is a relevant method for the prediction of DILI risk in humans, and it shows the best results among all of the methods used.

# ## INTRODUCTION

The liver is an organ major of toxins, because it is associated with drugs and xenobiotic metabolism. The drug-induced liver injury (DILI)² is one of the most expensive and dangerous types of toxicity. Decisions about the survival of many clinical trials, rejection of new drugs, and withdrawal of drugs have been made on the evidence of liver damage caused by hepatotoxic drugs. The identification of DILI in an early stage is needed, although there exists a limited correlation between vitro/in

elements in humans, and for the prediction of idiosyncratic effects in the liver is observed when the population is exposed to the drug marketing.⁵⁶ Consequently, in conjunction with the classic studies

Received: February 27, 2020
Published: May 14, 2020

![](bbox=[0.833, 0.846, 0.903, 0.915])

© 2020 American Chemical Society 1855
https://doi.org/10.1021/acs.ctrx.0.00030
Chem. Res. Toxicol. 2020, 33, 1855–1873