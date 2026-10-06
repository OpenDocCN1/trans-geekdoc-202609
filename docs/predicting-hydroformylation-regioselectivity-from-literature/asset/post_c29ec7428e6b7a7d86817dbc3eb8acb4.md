
# Chem Catalysis

# CellPress

Preview

# Predicting hydroformylation regioselectivity from literature data machine learning

Shai Chen¹ and Robert Police²*

In this issue of *Chem Catalysis*, Mao et al. develop machine learning models that predict terminal alkene regioselectivity in catalytic hydroformylation, showing that high temperature, low pressure and low metal concentration favor linear products. These models enable high-throughput screening, potentially advancing innovations in this most olefins, oct-1-ene and styrene. The general-olefin models are created by using all data for a single model, as opposed to the specialized models where data are split by olefin. Unlike the general-like model, the specialized gradient boosting models for oct-1-ene and styrene achieve useful performance with R² of 0.850 and 0.789, respectively, outperforming the general-olefin model significantly for these substrates.

![](img/4b2aa915a163b752e3c571e656a6cb7d_0_0.png)

Hydroformylation of olefins (HPOs) is a chemical transformation that converts olefins, carbon monoxide, and molecular hydrogen into linear or branched aldehydes (Figure 1). It is one of the most large-scale homogeneous-catalyzed transformations in the chemical industry and is a prototype of a highly atomic-economic conversion. In the 1970s, rhodium complexes were discovered both the most effective and chemolective hydroformylation catalysts. Later, other catalysts based on cobalt, ruthenium, iridium, palladium and platinum were developed as alternatives.²

The full representation used in this case is 4 dimensional and encompasses descriptors for the olefin, reaction metal catalyst, solvent, and reaction conditions. The researchers applied principal component analysis to reduce the dimensionality of the reaction representation and improve the robustness of the supervised ML models. When reduced to eight dimensions, prediction performance was best for olefins. When only oct-1-ene was used as a substrate, reducing the representation to four dimensions showed the highest prediction accuracy. In contrast to the oct-1-ene-specific model, reducing the representation to 15 dimensions maximized prediction for the styrene-specific model.

Recently, machine learning (ML) has emerged as a transformative tool in organic synthesis and chemical engineering. This development has led to breakthroughs in guiding synthesis, optimizing reactions, and discovering new pathways.³ One of the ML approaches is supervised learning, which aims to learn the relationship between a set of inputs and outputs and to predict the outcome of unseen chemical reactions. In general, constructing robust and accurate supervised models hinges on the use of high-quality chemical databases, and the selection of appropriate representations, and the choice of ML algorithms.

The first trained models to predict the outcome of all olefins in their database, which used the general-olefin model, and analyzed them found that these models could not distinguish between olefins as various olefins were clustered and, consequently, the performance was not good enough. Specifically, the researchers proposed specialized models for the

The researchers were also interested in understanding the most important features of the models. The shapley explanations (SHAP) were applied to the models constructed, and the corresponding results were averaged over the three models with the best predictive performance. This approach revealed that, in the general-olefin model, low bite values are associated with low L/B ratios, consistent with previous literature. Additionally, containing electron-substituted alkenes tend to form branched products. In terms of reaction conditions, high temperatures are conducive to induce L/B ratios. For specific to oct-1, longer reaction times generally increase the probability of L/B. In addition, low pressure favors the occurrence of β-hydrogen elimination, which reduces the selectivity of branched products and styrene-products. SHAP analysis revealed a novelty in the importance of the conditions to the substrates and for the styrene-specific model. Lower catalyst concentrations can accelerate β-hydrogen elimination, forming less branched products. The oct-1-specific and the styrene-specific models show that higher catalyst concentrations, pressure, and lower L/B values were present in the general-olefin model. Additionally, while the researchers used descriptors to differentiate between catalysts and solvents, the best-performing ML models do not generalize to rare substrates, as the data was biased toward common chemical species. Overall, this study by Mao and coworkers presented a comprehensive framework for terminal hydroformylation regioselectivity.

> ¹Institute of Chemistry, Groningen, Germany
²Correspondence: r.police@uio.no
https://doi.org/10.1016/j.chemchem.2024.101111

Chem Catalysis 4 (101111), September 2024 | Elsevier © 2024
All rights reserved; except for text and data mining, AI training, and other services.

![](img/4b2aa915a163b752e3c571e656a6cb7d_1_0.png)

## A Olefin Substrate Distribution
- 1-Octane (25.4%)
- Styrene (22.4%)
- Vinyl Acetate (9.0%)
- Alkyl Cyanide (7.8%)
- Other (35.4%)

## B Catalyst Element Distribution
- Rh (99.8%)
- Pd (1.3%)
- Ir (2.3%)

## C Solvent Distribution
- Toluene (64.3%)
- THF (11.5%)
- Benzene (10.6%)
- DCM (2.9%)
- Other (11.6%)

## Publication Year Distribution
- 2020-2024 (8.0%)
- 2015-2019 (14.7%)
- 2010-2014 (28.6%)
- 2005-2009 (12.7%)
- 2000-2004 (22.9%)
- 1995-1999 (11.1%)

![](img/4b2aa915a163b752e3c571e656a6cb7d_1_1.png)
![](img/4b2aa915a163b752e3c571e656a6cb7d_1_2.png)
![](img/4b2aa915a163b752e3c571e656a6cb7d_1_3.png)
![](img/4b2aa915a163b752e3c571e656a6cb7d_1_4.png)
![](img/4b2aa915a163b752e3c571e656a6cb7d_1_5.png)

Figure 1. Summary of predicting hydroformylation regioselectivity via machine learning

(A) Mechanism of HFOs.
(B) Distribution of the chosen olefin substrate, catalyst element, solvent, and year.
(C) Workflow of predicting hydroformylation regioselectivity.

## ACKNOWLEDGMENTS
S.C acknowledges funding from China Scholarship Council (grant No.20231926)

## DECLARATION OF INTEREST
The authors declare no interests.

## REFERENCES
- 1. Vches-Herrera, M., Domke, L., and Börner, A. (2014). Hydroformylation: tandem reactions. ACS Catal., 4, 1706–1713. https://doi.org/10.1021/acsacatal.500273
- 2. van Leeuwen, P.W.N.M., and Claver, C. (2002). Rhodium Catalysis. Wiley-VCH, Dordrecht.
- 3. Xiang, K., Luo, S., Liu, K., Jiang, S., Ma, J., Jiang, J., and Shu, Z. (2024). Artificial intelligence and automation to power the future of chemistry. Chem. Rep. Phys. Chem. Sci., 3, 102499. https://doi.org/10.1016/j.crcp.2024.102499
- 4. Cole, J., Wang, J., Jaskola, T., Green, W., and Jensen, K. (2017). Prediction of organic reactions using machine learning. Science, 356, aaa764. https://doi.org/10.1126/science.aaa764
- 5. Wang, H., Chen, Y., Yu, H., Qi, M., Xia, D., Liu, Y., Lu, B., Gao, R., Wang, Y., and Mao, S. (2024). Generalized machine learning models of terminal hydroformylation for regioselectivity. Chem. Catal., 4, 10179. https://doi.org/10.1016/j.cccat.2024.10179
- 6. Pedrosrosa, F., Varqueaux, G., Gramfort, A., Michel, V., Thion, B., Gisel, O., Blondel, N., Usnay, J., and V derberg, V., et al. (2011). Scikit-learn: Machine learning in Python. J. Machine Learning Res., 12, 2825–2830.
- 7. Lundberg, S.M., and Lee, S.-I. (2017). A unified approach to interpreting model predictions. Advances in Neural Information Processing Systems, 30, pp. 4765–4774.
