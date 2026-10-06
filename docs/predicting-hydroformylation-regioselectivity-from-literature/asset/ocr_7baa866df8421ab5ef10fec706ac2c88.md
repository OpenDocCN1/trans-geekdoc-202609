# # CellProcess

# # Chem Catalysis
Preview

![](bbox=[0.115, 0.125, 0.415, 0.335])

# A

# B

# Olefin Substrate Distribution

# Catalyst Element Distribution

![](bbox=[0.535, 0.165, 0.665, 0.255])

![](bbox=[0.735, 0.165, 0.865, 0.255])

+   - 1-Octane (25.4%)
 Styrene (22.4%)
 Vinyl Acetate (9.0%)
- Alkyl Cyanide (7.8%)
 Other (35.4%)
- Rh (99.8%)
 Pd (1.3%)\ Ir (2.3%)

# C

# Solvent Distribution

# Publication Year Distribution

![](bbox=[0.115, 0.365, 0.415, 0.465])

![](bbox=[0.535, 0.365, 0.665, 0.465])

+   - Toluene (64.3%)
 THF (11.5%)
 Benzene (10.6%)
- DCM (2.9%)
 Other (11.6%)
- 2020-2024 (8.0%)
 2015-2019 (14.7%)
 2010-2014 (28.6%)
- 2005-2009 (12.7%)
 2000-2004 (22.9%)
 1995-1999 (11.1%)

![](bbox=[0.735, 0.365, 0.865, 0.465])

Figure 1. Summary of predicting hydroformylation regioselectivity via machine learning

(A) Mechanism of HFOs.
(B) Distribution of the chosen olefin substrate, catalyst element, solvent, and year.
(C) Workflow of predicting hydroformylation regioselectivity.

angle values are associated with low L B ratios, consistent with previous literature. Additionally, containing electron-substituted alkenes tend to form branched products. In terms of reaction conditions, high temperatures are conducive to induce L/B ratios. For specific to oct-1, longer reaction times generally increase the probability of L/B. In addition, low pressure favors the occurrence of β-hydrogen elimination, which reduces the selectivity of branched products and styrene-products. SHAP analysis revealed a novelty in the importance of the conditions to the substrates and for the styrene-specific model. Lower catalyst concentrations can accelerate β-hydrogen elimination, forming less branched products. The oct-1-specific and the styrene-specific models show that higher

temperature, pressure, and lower L/B concentration values. Additionally, while the researchers used descriptors to differentiate between the solvents present in the dataset, the descriptors were inconsistent, consistent with the absence of a solvent effect on the hydroformylation regioselectivity.

Overall, this study by Mao and coworkers presented the construction of a comprehensive database for terminal olefin hydroformylation. The developed workflows to cluster molecular features for both catalysts and solvents facilitate physicochemical choices. Regarding regioselectivity, ML models for oct-1 and styrene were constructed with practically perfect accuracy. The data was biased toward specific chemical species

catalysts and olefins, and even the best-performing ML models do not generalize to use rare substrates, as the presented workflow is an important contribution demonstrating the power of ML in chemistry to accelerate the prediction of catalyst performance. 10

# ACKNOWLEDGMENTS

S.C acknowledges funding from the China Scholarship Council (grant No. 2023.2006.1903266)

# DECLARATION OF INTEREST

The authors declare not have competing interests.

# REFERENCES

+   1. Hood, D.M., Johnson, R.A., Carpenter, A.E., Ymerlin, J.J., Vinayrd, D.J., and Stanley, G.G. (2020). Highly active carbonyl catalyst(s) hydroformylation reaction. Chemical Science, 36(5), 542–548. https://doi.org/10.1039/C9CT004772A
2. Brest, B. (2003). Synthetic applications of enanti- and stereoselective hydroformylation. Angew. Chem. Soc., 42(27), 2664–2675. https://doi.org/10.1002/ac020596

2 Chem Catalysis, 4(101191), 2024, 19 * Wei-Wei