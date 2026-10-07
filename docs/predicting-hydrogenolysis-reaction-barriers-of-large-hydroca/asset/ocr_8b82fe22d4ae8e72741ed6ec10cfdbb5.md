# X. Zong

Applied Catalysis B: Environment and Energy 353 (2024) 124070

![](bbox=[0.065, 0.055, 0.465, 0.305])

Fig. 7. Activation barriers for C-C and C-H bond scission in CHCH*

lowest activation barrier for C-C cracking, by Rh. This order in barriers demonstrates that Ru and Au-based catalysts provide the fastest catalysis, consistent with [74,75]. Based on previously measured turnover rates, the activity of noble metals decreases with Ru > Ir > Pt. Notably, of metals demonstrated lower barrier for C-H bond scission (CHCH* → C2H4 + H*), showing the significance of C-C scission from CHCH*. With a mean absolute error (MAE) of 0.2 eV and only on three metals in the training dataset, our model could be valuable in search of other potential catalysts. Without selection, our model captures the general trends and shifts on potential catalysts but detailed parameters and reference.

# Author contributions

X.Z. and Y.T performed the DFT calculations. X.P. performed data analysis and developed the machine learning models. D.G contributed to the idea and provided supervision. All authors contributed to analyzing the results and writing.

Dionisos G Wachlich: Writing & editing, Supervision. Project administration, funding acquisition, Conceptualization. Xue Xie: Writing & editing, writing original draft, methodology, Investigation, Formal analysis, Data curation. TJ (Tianjin) Xie: Writing – original draft, methodology.

# Declaration of Competing Interest

The authors declare no conflicts of interest.

# Data availability

The data supporting this study' findings are available from the corresponding author upon reasonable request.

# Acknowledgements

This work was supported as part of the Catalysis Center for Energy Innovation, an Energy Research Center funded by the US Department of Energy, Office of Basic Sciences under award number DE-SC-1006104. The earlier work was supported by the US Department of Energy, Office of Energy Advanced Manufacturing Office under Award Number DE-EE0007888-9. The Delta Energy Institute acknowledges gratitude for the support and partnership of the Delta team toward the RAPID projects.

# Appendix. Supplementary information

The following information is available of free: (1) BE relations on each metal C-C and C-H breaking reactions; (2) Examples of test case configurations for C-C and C-H cracking; (3) Performance of tested machine learning models (4) Summary of results for each ML; (5) ML model performance; (6) ML model transferability transferabilities. (7) DFT calculations for C-C cracking and C-H breaking reactions are provided in Supplementary_Y.xlsx file. Supplementary data associated with this article can be found in the online at doi:10.1016/j.jcatb.2024.124070.

# 4. Conclusions

Accurate prediction of activation energies is crucial for the performance of catalysts. In this study, we compiled a dataset of 2083 calculated activation barriers for reactions on various metals. We developed two methods to estimate activation energies. The first is an extension of traditional BE relationship, which applied to larger hydrocarbon species. However, BE relationship shows limitations, with correlations being more accurate than predicted-C-C cracking results. This finding shows that with the structural change the barriers are more accurate on Pt and Ru. However, when aggregating all data, BE entropy results in limited results for the prediction. [76,47]. These correlations are better than predicted in previous studies.

To address shortcomings of traditional BE, we developed ML models using easy descriptors for the catalyst, metal surface, and reaction type. The most effective method shows a mean absolute error of 0.19 eV and 0.6 eV when the reaction energy is a descriptor. Critical features include the homogeneous series (C-C vs. C-H reaction) and the metal atom's electronegativity and atomic mass. We also analyzed its transferability, showing reasonable applicability in predicting activation barriers across transition metals.

Finally, we showcased the use of the ML model to understand the

7