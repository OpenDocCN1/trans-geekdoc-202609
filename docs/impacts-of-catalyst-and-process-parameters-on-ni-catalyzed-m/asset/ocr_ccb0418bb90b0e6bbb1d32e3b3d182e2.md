# # Impacts of catalyst and process parameters on Ni-catalyzed methane dry reforming via interpretable machine learning

Keerthana Vellayappan , Yifei Yue , Kang Hui Lim , Keyu Cao , Ji Yang Tan , Shuwen Cheng , Tianchang Wang , Terry Z.H. Gani , Iftekhar A. Karimi , Sibujing Kawi

Department of Chemical and Biomolecular Engineering, National University of Singapore, Singapore 119260, Singapore
School of Metallurgy, Northeastern University, Shenyang 100819, PR China

# ## ARTICLE INFO

+   - Machine Learning
+   - Heterogeneous catalysis
+   - Dry reforming of methane
+   - Syngas
+   - Catalyst design

# ## ABSTRACT

Dry reforming of methane (DRM) is a promising technology for valorizing two potent greenhouse gases, namely CO2 and CH4. Although design principles for active and stable catalysts are well-established, predicting selectivity of DRM over competing side reactions that alter product H2/CO ratio remains challenging. Here, we curate a set of 1638 data points from published literature and train tree regressor models to predict H2/CO ratio as a function of 11 catalyst and process parameters. The CatBoost regressors achieved best prediction performance with R2 = 0.91. Feature importance analysis reveals, in addition to well-known effects of process parameters on DRM performance, the potential roles of Ni particle size and loading in tuning H2/CO ratio independently of reactant conversions. Our exploratory study highlights ability of data-driven ML models to unearth structure–property relationships in heterogeneous catalysis by isolating effects of individual design parameters in a manner that would be difficult to achieve experimentally.

# ### 1. Introduction

The adverse effects of global warming have prompted vigorous international efforts to counteract its harmful effects and foster sustainable development, such as the coordinated efforts to limit warming to 1.5 °C above pre-industrial temperatures [1]. Processes that can convert greenhouse gases such as CO2 into useful chemical products have thus received intense interest in recent years as a possible means of decarbonizing the chemical industry [2]. For instance, the dry reforming of methane (DRM) (Eq. 1) is a promising alternative to steam methane reforming for the production of syngas (i.e., a mixture of CO and H2) [3]. With a theoretical H2/CO ratio of near unity, the syngas produced is well-suited for subsequent processing via oxo chemistry into acetic acid or aldehydes [4], or via Fischer-Tropsch chemistry into high-value liquid hydrocarbon products such as diesel and jet fuels [5,6].

CH4 + CO2 ⇌ 2 H2 + 2 CO, ΔH298 K = +247.3 kJ/mol (1)

In addition to noble metals such as Pt that are highly active catalysts for DRM, certain earth-abundant elements such as Ni also show reasonable activity but are prone to coking and sintering which cause

deleterious effects such as deactivation and reactor pressure buildup [7, 8]. Hence, strategies for improving the activity and stability of earth-abundant DRM catalysts by targeting their coking and sintering resistance have been broadly explored [4,5,9]. For instance, surface modification by redox-active oxides such as CeO2 or ZrO2 with high oxygen mobility can improve coke resistance by promoting the dissociation of CO2 and subsequent gasification of deposited carbon by reactive oxygen species [10], and sintering can be physically inhibited by confinement within mesoporous channels [11]. Notably, both of these advantages can be simultaneously realized via encapsulation within a porous reducible oxide shell, in which the core-shell morphology plays a dual role of physically preventing sintering while also maximizing the fraction of Ni-reducible oxide interfacial sites that are active for CO formation [12–14].

Another challenge associated with Ni-based DRM catalysts that has received much less attention is the tendency for the product syngas ratio (i.e., H2/CO ratio) to fall below unity because of the parasitic reverse water-gas shift (RWGS) reaction (Eq. 2) that consumes H2 and produces H2O as an unwanted by-product [15]. A low syngas ratio is undesirable because the syngas stream must then be replenished with H2 before it