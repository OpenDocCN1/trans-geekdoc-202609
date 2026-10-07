
# Zong et al.

# Applied Catalysis B: Environment and Energy 353 (2024) 124070

![](img/6dd3dd7ab6fde28f2003342f8b513bcf_2_0.png)

Fig. 1. BEPR correlations on intervals for (A-C) reactions, (B-C) reactions, and (C) data. Color black: Ru; red Pt; blue Rh. Correlation parameters in Table 1.

Table 1
Summary of BEPR relations of C-H and C-C bond scissors, number of points, $R^2$, and mean absolute error (MAE) in eV. R values are correlation coefficients. The 95% confidence intervals for the slopes and intercepts are.

| Homologous | Metal | Slope (eV) | Intercept (eV) | Number of Data Points | $R^2$ | MAE |
|---|---|---|---|---|---|---|
| C-C | Ru | 0.53 ± 0.11 | 1.09 | 101 | 0.47 | 0.16 |
| | Pt | 0.55 ± 0.04 | 1.48 | 108 | 0.63 | 0.18 |
| | Rh | 0.08 ± 0.04 | 1.36 | 57 | 0.56 | 0.18 |
| | All | 0.64 ± 0.07 | 2.27 | 266 | 0.53 | 0.22 |
| C-H | Ru | 0.75 ± 0.06 | 0.68 | 84 | 0.50 | 0.18 |
| | Pt | 0.71 ± 0.03 | 0.30 | - | - | 0.09 |
| | Rh | 0.14 ± 0.04 | 0.17 | - | - | 0.04 |
| | All | 0.77 ± 0.09 | 1.14 | 114 | 0.63 | 0.16 |
| All | All | 0.80 ± 0.09 | 1.10 | 380 | 0.47 | 0.30 |

![](img/6dd3dd7ab6fde28f2003342f8b513bcf_2_1.png)

Fig. 2. Transition state configurations of C-C cracking and C-H breaking reactions. (a) C-C cracking side view, (b) C-H cracking side view, (d) C-H breaking side view.

reactivity of metal [46]. Table 1 indicates that the BEP slopes are comparable across metals for the homologous series, where the transition state geometries are similar. Furthermore, C-C reactions typically have moderate to late transition states, whereas C-H cracking and C-breaking reactions in Ru. C-C reactions result in a dehydrogenated environment, where carbon atoms remain bonded to the same metal atom after dissociation for larger hydrocarbons, and the hydrogens on any ring or top sit with minimal penalty energy, cited in the literature [61]. C-C bond breaking in particular is shown to occur on neighboring sites on a metal surface. One or more cleaved fragments then bind to the surface [62], which requires diffusion to a next-neighbor site to minimize the repulsive interactions. For larger hydrocarbons, C-C breaking reactions, in particular the intrinsic activation barriers are significantly larger than the other metals. This is consistent with the activation energies observed in earlier experiments by Morita and co-workers [63, 64]

Our analysis indicates that BEPs for small hydrocarbons do not extrapolate well and for large are uncertain. However, the MAE error of 0.3 eV when considering all data points is acceptable. Predicting energies takes considerable time and calculation of the final state is challenging due to many possible configurations of the molecules. To overcome the limitations of traditional BEP relationships and provide a more accurate and rapid estimation of reaction energies and activation barriers, we turned to ML.

Morita and co-workers [65] reported that the hydrogenation of n-pentane and n-heptane reactions shows the order Ru > S > Pt, with the activation barriers being significantly larger than others.

the categorical variable into a form that can be effectively used in regression algorithms. The correlation matrix is shown in Fig. 3. The metal descriptors are strongly correlated with each other. The reaction energy is most intensely correlated with the activation energy, as expected, and follows the expected properties. The importance of including C-C breaking as a descriptor arises from the activation barriers of C-C reactions having a much wider range than C-H reactions, as shown in Fig. 1.

## 3.3. Model performance

To predict the activation energies, we exploited several regression algorithms and tuned their hyperparameters. We tested linear, kernel, and boosting models, including support vector regression (SVR), random forest (RF), and extreme gradient boosting (XGB). We prioritized simpler models to improve interpretability. The MAE was chosen as the performance metric.

To evaluate the performance, we used a test set of 50 reactions. The MAE of 0.24 eV indicates that even basic models can be effective when using well-selected features. Among all tested, the XGBoost outperformed the others, with an MAE of 0.16 eV on the test set. However, it also required much longer training time due to its optimization process by solving a complex function in a high-dimensional space.

The XGBoost model performance is summarized in Table 4. The importance of each feature is summarized in Table 5, with no MAE greater than 0.20 eV. From our analysis, the MAE is lower than a lower traditional BEP approach.

To compare with traditional BEP relations, we included the reaction energy as a feature in the XGBoost model. After tuning hyperparameters, the model's test set was reduced from 0.16 eV (0.9 eV), notably smaller than the 0.3 eV of traditional BEP relations. The included relation estimates activation energies accurately.

Our analysis uses 80% of the data points for training and 20% for testing. We evaluate the XGBoost model performance for different dataset sizes and

## 3.2. Feature selection and correlation

Feature selection is crucial for ML models. We selected features from [35, 66], describing the reactant, metal surfaces, and the reaction type, selected (Table 2). No structure information was included, only one (11) was considered. The first set of features includes the molecular weight of the reactant, adsorption energy on the metal, and number of C-C structures of the reactant.

We included information following our work [67], such as the atomic mass of the metal, electronegativity, ionization potential, number of electrons, and electron affinity. This is

We analyzed the correlation among features, reaction energies, and activation energies. The categorical variables were first converted to numerical numbers without encoding since no relation occurred. One-hot encoding converted each categorical value into a numerical value and column as thus columns indicating the

Table 2
Features included in the machine learning (ML) model.

| Category | Abbreviation | Type | Feature Description |
|---|---|---|---|
| Reactant | Reactant C1 valence | Numerical | Molecular weight of the reactant |
| | | Numerical | Adsorption energy of the reactant bonding to the metal surface |
| | | | Adsorption energy of the second reactant |
| Cis/Trans | | | Cis/trans fracture of the reactant. Three types used: cis, trans, or deive |
| Metal | Metal_Mass | Numerical | Atomic mass |
| | chi | Numerical | Electronegativity |
| | n_d | Numerical | Number of electrons |
| | EA | Numerical | Electron affinity |
| Reaction | Reaction_Type | Categorical | Type: C-C or C-H |

![](img/6dd3dd7ab6fde28f2003342f8b513bcf_3_0.png)

Fig. 4. ML model performance. (a) MAE of ML models with different test sets; de represents the reaction energy. (b) Activation energies of the XGBoost model vs. DFT Color code: purple points are the training set (80%); grey points are the test set (20%). (c) SHAP values of test data show the impact of each feature. (d) Feature importance based on mean SHAP values. See Table 2 for reference,model convergence, we varied the test set from 0% to 90%, adjusting the training set size in 10% increments. We observed a large set with 90% test size. As we increased the training set size, the test error decreased and eventually stabilized reaching 80% of the training set, indicating no overfitting.

## 3.4. Feature analysis

Identifying the features that influence the activation energy is vital. For this purpose, we employed the SHAP (Shapley Additive exPlanations) method proposed by Lee et al. [51] to assess the performance of the XGBoost model. SHAP is an advanced machine learning technique grounded in game theory. We calculated Shapley values for predicting activation energies, displaying each feature's importance and their average impact on model predictions. Notably, the reaction, specifically the C-C cracking has a higher feature value, consistent with correlation in Fig. 3. The two most important features are electronegativity and the molecular weight of the reaction. Fig. 4d shows the features in terms of how important and how each feature affects the model output. For example, when the reaction, type-C has a higher value in the plot, the model output is larger, consistent with the C-C cracking reactions having higher activation energy.
The cis/trans descriptor only has a minor effect. The model after this feature gives a set test size MAE of 0.20, close to the original model. A plausible explanation could be the limited number of cis/trans isomers in our dataset, potentially underrepresenting this feature's significance. Considering, we opted to retain this feature in the model.

![](img/6dd3dd7ab6fde28f2003342f8b513bcf_4_4.png)

Fig. 5. Learning curve of the XGBoost model with different training and test sets.
