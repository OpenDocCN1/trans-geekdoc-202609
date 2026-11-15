| Compounds | Formable or Stable | Charge capacity (mAhg⁻¹) | Source |
|---|---|---|---|
| RbTeGeO₆ | Both | 380 | Current results |
| Ge₂NaAl₅O₆ | Both | 372 | Current results |
| TcCaMnBeO₆ | Both | 359 | Current results |
| ReCsAlCeO₆ | Both | 355 | Current results |
| OsSeAlCo₆O₆ | Both | 352 | Current results |
| TiH₃S₂O₆ | Stable | 602.37 | DFT Input |
| Al₂CaSiO₆ | Stable | 368.6 | DFT Input |
| VCdPHO₆ | Stable | 368 | DFT Input |
| MnZn₂SiO₆ | Stable | 346 | DFT Input |
| Y₃Sb₅O₆ | Stable | 319.7 | DFT Input |
| TlBTeGeF₆ | Both | 215.63 | Current results |
| WTeBeAuF₆ | Both | 212.3 | Current results |
| MnRBeGeF₆ | Both | 211.6 | Current results |
| ReTeBeAuF₆ | Both | 211.5 | Current results |
| FeTeBeGeF₆ | Both | 211.1 | Current results |
| Ge₂NOF₆ | Stable | 464.91 | DFT Input |
| Na₂LiAlF₆ | Stable | 138 | DFT Input |
| NaLi₂TiF₆ | Stable | 134.8 | DFT Input |
| Na₂LiSCF₆ | Stable | 126.5 | DFT Input |
| Li₂AlCuCuF₆ | Stable | 122.7 | DFT Input |

The Energy above hull (Eₕ) of 4075 compounds are obtained from the DFT database obtained from Materials Project. The energy above the hull as a function of their calculated charge capacities (mAhg⁻¹) is shown in Figure 9. The stable and unstable perovskites are shown along with their charge capacities. The threshold of energy above the hull is set to 50 meV to demarcate stable and unstable perovskite materials. The charge capacities corresponding to the materials from the reported DFT database have been indicated in Fig. 9. From the figure, it can be depicted that the maximum charge capacity corresponding to stable oxide and halide perovskites are 602.37 mAhg⁻¹ (TiH₃S₂O₆) and 464.91 mAhg⁻¹ (Ge₂NOF₆), respectively. An identical pattern has been observed with the predicted compounds as well. Here it is worth noting that the predicted compounds using the ML model are claimed to be formable and stable. However, the data pattern from the reported DFT database has only listed stable compounds. The prime objective is to explore potential novel compounds with high charge densities. A comparison of novel compounds with the stable compounds of the DFT database is presented in Table 2.

# 6. Conclusions

A systematic analysis is presented to explore novel perovskite materials using advanced classification techniques of machine learning by preparing feature sets and a new database. The formability classification model is trained with the existing experimental database of known materials and by preparing feature sets of large chemical space of single and double oxide perovskites and halide perovskites. Similarly, the stability classification model is trained using the DFT-based database and feature sets of large chemical space of single and double perovskites. Only cubic symmetries of DFT datasets are considered in stability classifications and an energy threshold of 50 meV is selected in energy convex hull to define stable and unstable compounds in the DFT dataset. By increasing the threshold, the range of stability can be tuned and this increases the overlap with the formability database. However, this may increase the risk of adding unstable compounds to the final list of compounds. The cubic (Pm-3m) symmetry is a prototype phase of perovskites even though they can belong to other space groups like tetragonal (P4/mbm) and orthorhombic (Pmbn), but considering

multiple space groups presents a complex challenge that demands the development of more sophisticated machine learning models for formability and stability predictions. The stability database uses the convex hull estimation techniques of all the compounds to predict the shape, unstable, and metastable nature of compounds using the Material Project database.

The databases comprising several atom-specific features and geometric feature sets have been prepared. The formability and stability classification models are built based on the random forest (RF) technique. These ML models are built to maximize the accuracy and reduce the variance. Another classifier, Gaussian Process Classifier (GPC) has also been employed for formability and stability models to verify the RF classifier model. It can be seen that the proposed RFC-based models are more robust and reliable. Further, the predictive values of features are measured to understand the relationship between the feature and the true outcome. The hierarchical clustering technique is used to analyze the effect of multi-collinearity among selected features and their effect on perovskite formability and stability, respectively. The formability classification model predicts 475024 new formable compounds, whereas the stability classification model predicts 437828 new stable compounds. Finally, 591 compounds are shortlisted as they are formable and stable compounds, simultaneously with great confidence. These 591 compounds are the most promising novel oxide and halide perovskites for future experimental realization. Further, these shortlisted compounds are tested theoretically for energy storage applications. The final list of compounds consists of 247 oxide perovskites, 19 fluoride perovskites, 132 chloride perovskites, and 190 bromide perovskites. The highest charge capacity is found in a fluoride perovskite but the overall highest charge capacity is found in oxide perovskites. With this ML approach, one can also study the properties of novel compounds of other crystal structures for distinct applications. The ML approach can set the path to examine the functionality of novel compounds in an extensive approach.

# CRediT authorship contribution statement

Neelesh Gupta: Writing – review & editing, Writing – original draft, Visualization, Validation, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. Ravi Kumar: Writing – review & editing, Supervision, Resources, Project administration, Conceptualization. Alankar Alankar: Writing – review & editing, Supervision, Software, Resources, Project administration, Methodology, Investigation, Funding acquisition, Conceptualization.

# Declaration of Competing Interest

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

# Data availability

We have provided a link to the program and data in the manuscript.

# Acknowledgements

The authors would like to gratefully acknowledge the funding received from the project Ceramic Technologies for Futuristic Mobility (project number: SB22231272MMETW0008702), an Institute of Eminence Initiative of IIT Madras.