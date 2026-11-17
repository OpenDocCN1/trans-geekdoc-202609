learning models, such as Multi-Layer Perceptions (MLPs), ensemble models often perform better for tabular data [66]: unlike MLPs, tree-ensemble models do not exhibit bias towards non-smooth target functions, and tree-ensemble models are more robust to uninformative and colinear features [66,67]. In addition, tree-based ensemble models are easier to implement and tune (e.g., ensemble trees allow the feature to be directly used as inputs to the ensemble model without the need for normalization:

Tree-based ensemble models use two main ensemble methods, particularly bagging and boosting. In bagging, each decision tree in the ensemble is trained using a randomly sampled subset of the training dataset. In gradient boosting, the base decision trees in the ensemble are sequentially fitted with another decision tree to resolve inaccurate predictions produced by the previous decision tree [68]. Further details on the RF, GBR, and CatBoost algorithms are provided in Supplementary Information Text S2, and the hyperparameters of each ensemble tree model are provided in Supplementary Information Table S5.

# Machine learning workflow

Our machine learning workflow is detailed as follows: (1) We performed the train-test split once (90%–10% train-test). (2) We used grid cross validation on the training set to find the optimal hyperparameters. (3) The model is trained on the training set that is partitioned at the start. (4) Model performance is evaluated and compared based on the test set.

# Aspen plus thermodynamic simulations

Thermodynamic equilibrium calculations of dry reforming of methane (DRM) at any given temperature (i.e., 500°C–800 °C) and at atmospheric pressure (i.e., 1 bar) are based on minimizing the Gibbs free energy of a multicomponent system. The overall system is assumed to contain the main DRM reaction (i.e., CH4 + CO2 ⇌ 2 H2 + 2CO) and its most prominent side reaction, the reverse water gas shift (RWGS, i.e., H2 + CO2 ⇌ H2O + CO). The total Gibbs free energy (Gtotal) of the overall chemical system is the sum of the chemical potential of each species involved (i.e., CH4, CO2, H2, CO, H2O and He, which is used as a diluent):

```
$G^{total} = \sum_{i=1}^N n_i \mu_i$ (1)
```

where $n_i$ is the number of moles of species $i$ and $\mu_i$ is the corresponding chemical potential of species $i$. The chemical potential can be defined as:

```
$\mu_i = \Delta G_{f_i}^0 + RTln(\gamma_i \hat{\varphi}_i \frac{P}{P_0})$ (2)
```

where $\Delta G_{f_i}^0$ is the standard Gibbs free energy of formation for species $i$ at standard conditions. $R$ is the molar gas constant, $T$ is the temperature, $y_i$ is the molar fraction of species $i$, $\widehat{\varphi}_i$ is the fugacity coefficient of species $i$, $P$ is the operating pressure, and $P_0$ is the pressure at standard conditions. The fugacity coefficient, $\widehat{\varphi}_i$, can be estimated from equation of state modelling in the gas phase. Based on Carlson’s decision tree for equations of state selection, the Peng-Robinson Equation of State is the optimal choice for estimating fugacity coefficients in non-polar chemical systems, and hence chosen in our thermodynamics calculations [69]. The analysis was performed on Aspen Plus V12 using RGibbs reactor.

The same model was used for thermodynamic simulations with varying extents of DRM reaction at different temperatures to determine the syngas ratio trend. A conversion reactor was used to specify the extent of the reaction, and a Gibbs equilibrium reactor for RWGS was used to ensure RWGS is at equilibrium conversion. The simulated feed was an undiluted equimolar mixture of CH4 and CO at a pressure of 1 bar.

# Associated content

# Supplementary Information

Search string used in Scopus, theoretical background of models used, additional data visualization plots, tables of descriptive statistics, list of outliers, ML model hyperparameters (PDF).

# Appendix A. Supporting information

Supplementary data associated with this article can be found in the online version at doi:10.1016/j.apcatb.2023.122593.

# References

+   [1] J. Rogelj, G. Luderer, R.C. Pietzcker, E. Kriegler, M. Schaeffer, V. Krey, K. Riahi, Energy system transformations for limiting end-of-century warming to below 1.5 °C, Nat. Clim. Change 5 (2015) 519–527.
+   [2] S. Cheng, Z. Sun, K.H. Lim, T.Z.H. Gani, T. Zhang, Y. Wang, H. Yin, K. Liu, H. Guo, T. Du, J. Liu, G.K. Yi, Z. Yin, S. Zhai, Emerging strategies for CO2 photocorreduction to CH4: from experimental to data-driven design, Adv. Energy Mater. 12 (2022) 2200389.
+   [3] Y. Song, E. Ozdemir, S. Ramesh, A. Adishev, S. Subramanian, A. Harale, M. Albulai, B.A. Fadhel, A. Jamali, D. Moon, S.H. Choi, C.T. Yavuz, Dry reforming of methane by stable Ni-Mo nanocatalysts on single-crystalline MgO, Science 367 (2020) 777–781.
+   [4] K. Wittich, M. Krämer, N. Bottke, S.A. Schunk, Catalytic dry reforming of methane: Insights from model systems, ChemCatChem 12 (2020) 2130–2147.
+   [5] I.V. Yentekakis, P. Panagiotopoulou, G. Artemetis, A review of recent efforts to promote dry reforming of methane (DRM) to syngas production via bimetallic catalyst formulations, Appl. Catal. B (2021), 120210.
+   [6] S. Lögdberg, D. Tristantini, Ø. Borg, L. Ilver, B. Gevert, S. Járás, E.A. Blekkan, A. Holmen, Hydrocarbon production via Fischer–Tropsch synthesis from H2-poor syngas over different Fe-Co-/$\gamma$-Al2O3 bimetallic catalyts, Appl. Catal. B 89 (2009) 167–182.
+   [7] S. Damyanova, B. Pawelec, K. Aristhrova, M.V.M. Huerta, J.L.G. Fierro, The effect of CeO2 on the surface and catalytic properties of Pt/Co–O–ZrO2 catalysts for methane dry reforming, Appl. Catal. B 89 (2009) 149–159.
+   [8] I.V. Yentekakis, G. Goula, M. Hatzisymeon, I. Besti–Argyropoulou, G. Botzolaki, K. Kousi, D.I. Kondarides, M.J. Taylor, C.M. Parlett, A. Osatiashtiani, Effect of support oxygen storage capacity on the catalytic performance of Rh nanoparticles for CO2 reforming of methane, Appl. Catal. B 243 (2019) 490–501.
+   [9] W. Kong, Y. Fu, L. Shi, S. Li, E. Vok, X. Zhou, R. Si, B. Pan, C. Yuan, S. Li, Nickel nanoparticles with interfacial confinement mimic noble metal catalyst in methane dry reforming, Appl. Catal. B 285 (2021), 119837.
+   [10] A.L.A. Marinho, R.C. Rabelo-Neto, F. Epron, N. Blon, F.S. Toninlo, F.B. Noronha, Embedded Ni nanoparticles in CeZrO2 as stable catalyst for dry reforming of methane, Appl. Catal. B 268 (2020), 118387.