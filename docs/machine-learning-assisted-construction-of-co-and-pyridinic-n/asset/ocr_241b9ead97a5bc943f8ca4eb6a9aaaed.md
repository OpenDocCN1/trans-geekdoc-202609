# Machine learning-assisted construction of C=O and pyridinic N active sites in sludge-based catalysts

Xu Heᵃ, Wenjie Gaoᵃ, Jinglei Xuᵃ, Zhanjun Chengᵃ, Wenchao Pengᵇ, Beibei Yanᵃ, Guanyi Chenᵃᶜ, Ning Liᵃ

ᵃ School of Environmental Science and Engineering/Tianjin Research Center for Safe Disposal of Organic Solid Waste and Energy Utilization Engineering, Tianjin University, Tianjin 300072, China
ᵇ School of Chemical Engineering and Technology, Tianjin University, Tianjin 300050, China
ᶜ School of Mechanical Engineering, Tianjin University of Commerce, Tianjin 300134, China

+   ### ARTICLE INFO
+   
+   *Article history:*
+   - Received 21 October 2024
+   - Revised 13 January 2025
+   - Accepted 27 February 2025
+   - Available online 28 February 2025
+   
+   *Keywords:*
+   - Machine learning
+   - Catalyst
+   - Active sites
+   - Sludge
+   - Model ensemble

# ABSTRACT

The type and quantity of active sites on a catalyst surface determine catalytic activity. In this study, machine learning was employed to assist in the construction of C=O and pyridine N active sites using sludge waste. Reactive descriptors, including C%, N%, O%, Fe%, pyrolysis temperature, heating rate, and pyrolysis time were proposed. Decision tree, extra tree, extreme gradient boosting (XGB), automatic relevance determination, and Bayesian ridge regression models were constructed and optimized. Among these, the XGB model was demonstrated with superior accuracy for prediction of C=O sites on the catalyst surface. Additionally, an ensemble model combining extra trees and XGB was developed to predict pyridine N, with R² value as high as 0.80 and minimum root mean square error (RMSE) of 0.1386. The ensemble model demonstrated a 17% improvement in accuracy compared to individual models. The model enables high-throughput screening of construction conditions for C=O and pyridine N. The study found that a pyrolysis temperature above of 500–800 °C, a heating rate of 10–20 °C/min, and a heating time of 120–200 min favor the generation of C=O active sites. For pyridine N sites, a pyrolysis temperature between 400 °C and 600 °C, a heating rate of 5–10 °C/min, and a pyrolysis time of around 150 min are optimal. Experimental validation demonstrated that both models exhibit excellent predictive performance, with prediction errors below 10% in all cases. This research provides a method to assist in the construction of C=O and pyridine N active sites, which is beneficial for guiding the design of sludge catalysts.

Sewage sludge (SS), a byproduct of wastewater treatment, has aroused widespread attention. The safe disposal of SS becomes one of the key concerns for wastewater treatment plants. Currently, the global annual production of dry solid sewage sludge is approximately 53 million tons. However, >80% is not properly treated, posing a potential threat to the environment [1,2]. Therefore, effective measures are urgently needed to manage SS. Sludge is rich in organic matter and usually needs to be dehydrated before being burned to generate electricity or heat. In addition, the mineral composition of sludge is similar to that of clay, so sludge can be used as a raw material to produce building materials such as ceramists, replacing some clay resources. In addition, sludge is rich in nitrogen, phosphorus and potassium, which can be used as an organic fertilizer to improve soil quality [3]. For sustainability, resource utilization of SS has emerged as a preferred option [4].

Fortunately, thermal treatment provides an efficient and environmentally friendly method for high-value recovery by converting sludge waste into functional biochar [5,6]. Utilizing SS as a raw material for carbon-based catalysts preparation is regarded as a novel approach for both sludge reduction and resource recovery [7–9].

Advanced oxidation processes (AOPs) are widely applied in pollutant removal and energy conversion. Carbon atoms with sp² hybridization and electron-rich functional groups, such as C–O and C=O, can act as interfacial sites for the activation of peroxymonosulfate (PMS). The sp² hybridized carbon serves as an efficient electron transport medium, enabling the activation of PMS via electron transfer to generate sulfate radicals (SO₄•⁻) and hydroxyl radicals (•OH) [10]. Pyridinic N acted as Lewis basic sites to transfer electrons to electrophilic oxygen in C–S₂O₈²⁻ complex, leading to the cleavage of O–O bond and generation of SO₄•⁻ and O₂⁻ [11]. Additionally, the π-electron delocalization and abundant structural defects in the highly graphitized carbon lattice enhance

* Corresponding author.

*E-mail address:* linningect@tjtu.edu.cn (N. Li).