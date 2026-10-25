![](bbox=[0.215, 0.07, 0.715, 0.435])

Figure 3. Pearson correlation matrix of the original 31 features.

The features about characterization properties of each material ($L_i$) are extracted from the literature including the average grain size (GS), maximum dielectric constant ($\varepsilon_m$), relaxation diffuseness ($\gamma$) calculated by the modified Curie–Weiss law (eq 4), and maximum and remnant polarization ($P_{max}$ and $P_r$) at the applied electric field. According to eq 5, $P_{max}$ and $P_r$ are combined into single feature $\Delta P$ and placed into the feature pool. These features provide the microstructure, dielectric properties, relaxor behavior, and polarization characteristics of each material. Therefore, the feature pool of strategy II ($L_r + C_t$) contains 27 features in total.

```
1/\varepsilon_r - 1/\varepsilon_m = (T - T_m)^\gamma / C
```

```
\Delta P = P_{max} - P_r
```

The manufacturing process of ceramics can significantly affect the microstructure of materials, particularly in the case of BT-BMO materials. Due to the relatively low melting point of Bi2O3 (825 °C), improper processing will result in abnormal grain growth and formation of voids at grain boundaries, which can adversely affect the energy storage performance. Thus, the processing parameters of each material are extracted from published papers to expand the feature pool ($P_i$), including calcination temperature (CT), calcination time (ct), sintering temperature (ST), and sintering time (st). So, the feature pool of strategy III ($P_i + L_i + C_t$) encompasses 31 features. The detailed list of features is shown in Table S1 in the Supporting Information.

When the number of features in a data set is large, the complexity of the model will correspondingly increase, which will affect the efficiency of model training and may also lead to overfitting of the model. A combination of physical knowledge, the Pearson correlation coefficient, and feature importance analysis methods were employed to perform dimensionality reduction on the feature space. The Pearson correlation matrix is utilized to identify the highly correlated features, as shown in Figure 3. The red and blue colors represent negative and positive correlations between two features, with brighter shades denoting higher correlations. Generally, an absolute value of

the Pearson correlation coefficient between features exceeding 0.8 is considered to indicate a strong correlation between them. For groups of strongly correlated features, only one feature was retained to avoid redundancy. During the process of feature selection and elimination, we relied on both physical knowledge and the feature importance feedback from the model. Considering that the calcination and sintering times (Ct and St) of BT-BMO ceramics reported in the literature are mostly in the range of 2–4 h with no significant variation, these two features were excluded from the final pool. The final feature pools of each strategy are given in Tables 1 and 2.

**Table 1. Final Feature Pool of Each Strategy for the** $W_{rec}'$ **Model**

| strategy | final feature pool |
|---|---|
| I | AM, PE, MN, DV, VEN, D, IE, E |
| II | AM, PE, MN, DV, VEN, D, IE, E, GS, Conmax, DIF, $\Delta P$ |
| III | AM, PE, MN, DV, VEN, D, IE, E, GS, Conmax, DIF, $\Delta P$, CT, ST |

**Table 2. Final Feature Pool of Each Strategy for the** $\eta'$ **Model**

| strategy | final feature pool |
|---|---|
| I | $\mu$, AM, PE, MN, R, DV, VEN, E |
| II | $\mu$, AM, PE, MN, R, DV, VEN, E, GS, Conmax, DIF, $\Delta P$ |
| III | $\mu$, AM, PE, MN, R, DV, VEN, E, GS, Conmax, DIF, $\Delta P$, CT, ST |

**Model Establishment and Evaluation.** Employing a suitable inference model is recognized to be a crucial part of machine learning. There is no ML model universally optimal for all problems; instead, each particular problem needs a particular ML model to analyze.62 Six typical models are trained via every feature construction strategy to predict the log-scaled energy storage density values ($W_{rec}'$) and arcsine square root $\eta$ values ($\eta'$), including the linear regression algorithm (linear), support vector regression with a radial basis