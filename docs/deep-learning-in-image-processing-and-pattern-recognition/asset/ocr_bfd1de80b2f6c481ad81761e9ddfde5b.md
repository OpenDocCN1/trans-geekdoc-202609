**Table 5.** *p*-Values of the McNemar’s significance test on UR-Fall dataset.

| Method | RetinaNet | YOLOv5 | YOLOv7 |
|---|---|---|---|
| YOLOv7 | <0.001 | 0.085 | 1 |

**Table 6.** Testing Performance of different models in UR Fall detection dataset.

| Method | Accuracy (%) | 0.5 mAP | Precision of Fall |
|---|---|---|---|
| RetinaNet [49] | 40.9 | 0.464 | 0.818 |
| YOLOv5 [54] | 89.8 | 0.925 | 0.881 |
| YOLOv7 [32] | 92.4 | 0.944 | 0.893 |
| The proposed method | 93.2 | 0.960 | 0.920 |

# 5. Conclusions

This paper proposes a vision-based fall detection system with an improved deep-learning-based tracking-by-detection method. The proposed method integrates dual illumination estimation to the YOLOv7 + Deep SORT tracking algorithm to enhance fall detection performance under suboptimal lighting conditions caused by dim or uneven light. The proposed method also incorporates exposure correction for fall detection in videos. The performance of the proposed method is validated on two fall detection datasets, namely, Le2i FDD and UR-Fall datasets. For future experiments, we aim to implement a self-learning framework that automatically adapts to false alarms and adds correct results to help the current fall detection systems to improve their performance.

**Author Contributions:** Conceptionalization, X.Z. and M.P.; methodology, X.Z. and K.C.; software, X.Z. and K.C.; validation, X.Z., K.C., A.B., J.L. and M.P.; formal analysis, X.Z., K.C. and A.B.; investigation, X.Z. and K.C.; resources, X.Z., J.L. and M.F.; data curation, X.Z. and K.C.; writing—original draft preparation, X.Z.; writing—review and editing, X.Z., K.C., A.B., J.L. and M.P.; visualization, K.C., A.B. and J.L.; supervision, J.L. and M.P.; project administration, A.B. and M.P.; funding acquisition, J.L. and M.P. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research received no external funding.

**Conflicts of Interest:** The authors declare no conflict of interest.

# References

+   1.  World Health Organization (WHO). Falls. 2021. Available online: https://www.who.int/news-room/fact-sheets/detail/falls (accessed on 17 July 2022).
2.  Alam, E.; Sufian, A.; Dutta, P.; Leo, M. Vision-based human fall detection systems using deep learning: A review. *Comput. Biol. Med. 2022*,*146*, 105626. [CrossRef] [PubMed]
3.  Burns, E.; Kakara, R. Deaths from Falls Among Persons Aged $\geq$ 65 Years—United States, 2007–2016. *MMWR. Morb. Mortal. Wkly. Rep. 2018*,*67*, 509–514. [CrossRef]
4.  Kelsey, J.L.; Procter-Gray, E.; Hannan, M.T.; Li, W. Heterogeneity of Falls Among Older Adults: Implications for Public Health Prevention. *Am. J. Public Health 2012*,*102*, 2149–2156. [CrossRef]
5.  Vishnu, C.; Datta, R.; Roy, D.; Babu, S.; Mohan, C.K. Human Fall Detection in Surveillance Videos Using Fall Motion Vector Modeling. *IEEE Sensors J. 2021*,*21*, 17162–17170. [CrossRef]
6.  Mubashir, M.; Shao, L.; Seed, L. A survey on fall detection: Principles and approaches. *Neurocomputing 2013*,*100*, 144–152. [CrossRef]
7.  Saleh, M.; Jeannes, R.L.B. Elderly Fall Detection Using Wearable Sensors: A Low Cost Highly Accurate Algorithm. *IEEE Sensors J. 2019*,*19*, 3156–3164. [CrossRef]
8.  Wang, X.; Ellul, G.; Azzopardi, G. Elderly Fall Detection Systems: A Literature Survey. *Front. Robot. AI 2020*,*7*. [CrossRef]
9.  Alwanandi, S.; Lofi, A.; Powell, H.; Appiah, K. Video Based Fall Detection Using Features of Motion, Shape and Histogram. In Proceedings of the 11th Pervasive Technologies Related to Assistive Environments Conference, Corfu, Greece, 26–29 June 2018; pp. 529–536. [CrossRef]
10. Yaday, S.K.; Luthra, A.; Tiwari, K.; Pandey, H.M.; Akbar, S.A. ARFDNet: An efficient activity recognition & fall detection system using latent feature pooling. *Knowl. Based Syst. 2022*,*239*, 109748. [CrossRef]