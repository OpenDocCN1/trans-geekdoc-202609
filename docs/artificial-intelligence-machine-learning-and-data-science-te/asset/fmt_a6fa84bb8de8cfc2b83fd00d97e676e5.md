
The complexity of the building of CART decision tree is `O(mnlog₂n)` where `m` is the number of the features and `n` is number the patients ([Sani et al., 2018](#ch09.xhtml#r028)).

## [1.5 Results and Discussion](#ch09.xhtml#h1-005b)

As far as we considered three channels, it is natural to compare their effectiveness from the point of view of classification. One of the main properties of such data sequences are their type. Thus, at the first stage it is useful to classify the color channels by their Hurst exponents: ergodic, chaotic, trend stable and fractal ([Tables 1.1](#ch09.xhtml#t1)–[1.3](#ch09.xhtml#t3)).

**Table 1.1**  
Classification of data sequences by red component

| **Type/group** | **Healthy** | **Breast cancer** | **Fibroadenomatosis** |
| --- | --- | --- | --- |
| Ergodic | 0 | 0 | 0 |
| Chaotic | 0 | 0 | 0 |
| Trend stable | 29 | 54 | 27 |
| Fractal | 0 | 14 | 6 |

**Table 1.2**  
Classification of data sequences by green component

| **Type/group** | **Healthy** | **Breast cancer** | **Fibroadenomatosis** |
| --- | --- | --- | --- |
| Ergodic | 0 | 0 | 0 |
| Chaotic | 0 | 0 | 0 |
| Trend stable | 2 | 6 | 6 |
| Fractal | 27 | 62 | 27 |

**Table 1.3**  
Classification of data sequences by blue component

| **Type/group** | **Healthy** | **Breast cancer** | **Fibroadenomatosis** |
| --- | --- | --- | --- |
| Ergodic | 0 | 0 | 0 |
| Chaotic | 0 | 0 | 0 |
| Trend stable | 29 | 43 | 24 |
| Fractal | 0 | 25 | 9 |

[Tables 1.1](#ch09.xhtml#t1) to [1.3](#ch09.xhtml#t3) indicate the blue component potentially can allow separation of the control group from the groups of patients suffering from breast cancer and fibroadenomatosis, because it provides the most clear distinction between healthy and breast cancer patients. Thus, further, we shall consider only the blue channel ([Table 1.4](#ch09.xhtml#t4)).

**Table 1.4**  
Pairwise specificity, sensitivity and accuracy of differential diagnosis by the first group of features in the blue channel

| | **Control vs breast cancer** | **Control vs fibroadenomatosis** | **Breast cancer vs fibroadenomatosis** |
| --- | --- | --- | --- |
| **Specificity, %** | 82.76 | 96.55 | 63.63 |
| **Sensitivity, %** | 95.59 | 93.94 | 52.94 |
| **Accuracy, %** | 91.75 | 95.16 | 56.44 |

Since it was not possible to distinguish cancer from fibroadenomatosis using the method described above, at the second stage the classes of patients with cancer and fibroadenomatosis were combined into a general class and the classification of healthy and sick patients was carried out ([Table 1.5](#ch09.xhtml#t5)). This situation is typical for screening, when among a large population of people it is necessary to recognize a risk group without making a differential diagnosis of diseases. In this case, all (29) healthy patients and half of the combined class (51 patients) were taken. The selection of sick patients was made at random. This was done for reasons of a large number of sick patients and a small number of healthy ones.

**Table 1.5**  
Specificity, sensitivity and accuracy of screening by the first group of features in the blue channel

| | **Control vs breast cancer and fibroadenomatosis** |
| --- | --- |
| **Specificity, %** | 96.55 |
| **Sensitivity, %** | 94.00 |
| **Accuracy, %** | 94.94 |

In [Tables 1.6](#ch09.xhtml#t6) and [1.7](#ch09.xhtml#t7) we present similar results obtained for descriptive statistics of the distribution of Hurst exponent (the second group of the features).

**Table 1.6**  
Pairwise specificity, sensitivity and accuracy of differential diagnosis by the second group of features in the blue channel

| | **Control vs breast cancer** | **Control vs fibroadenomatosis** | **Breast cancer vs fibroadenomatosis** |
| --- | --- | --- | --- |
| **Specificity, %** | 93.10 | 93.10 | 72.72 |
| **Sensitivity, %** | 86.76 | 90.91 | 69.12 |
| **Accuracy, %** | 88.66 | 91.94 | 70.30 |

The pairwise classification of “healthy – cancer” and “healthy – fibroadenomatosis” allows us to build a very good model based on the Serpinsky curve. Classification of all three cell types based on scanning of the Serpinsky curves led to the following results.

**Table 1.7**  
Specificity, sensitivity and accuracy of screening by the second group of features in the blue channel

| | **Control vs breast cancer and fibroadenomatosis** |
| --- | --- |
| **Specificity, %** | 96.55 |
| **Sensitivity, %** | 94.00 |
| **Accuracy, %** | 94.95 |

## [1.6 Conclusion and Future Scope](#ch09.xhtml#h1-006b)

Our investigation has shown that fractal dimension of the Feulgen-stained chromatin in interphase nuclei of buccal epithelium is an effective biomarker of breast cancer. The classification method developed on this basis has the excellent accuracy (94.95%), sensitivity (94%) and specificity (96.5%). For comparison, the sensitivity of the mammography is about 87% ([Breast Cancer Surveillance Consortium, 2017](#ch09.xhtml#r007)) and the specificity after the mammography varies from 93% to 88% ([Nelson et al., 2016](#ch09.xhtml#r015)) depending on the age (the younger the patient the higher the false positive rate). Our method allows effective detecting of the presence of malignant tumors in the human body during screening without invasive procedures. However, the differential diagnosis of cancer and fibroadenomatosis still remains an open problem.

## [References](#ch09.xhtml#rlist-001b)

*   [Adam R.](#ch09.xhtml#r001b), Silva R., Pereira F. et al. 2006. The fractal dimension of nuclear chromatin as a prognostic factor in acute precursor B lymphoblastic leukemia. *Cellular Oncology*. 28, pp. 55–59. DOI: [10.1155/2006/409593](https://doi.org/10.1155/2006/409593).

*   [Adhraryn S.G.](#ch09.xhtml#r002b), Dave B.J., Trivedi A.H. 1991. Cytogenetic surveillance of tobacco-areca nut (mava) chewers, including patient with oral cancers and premalignant conditions. *Mutation Research*. 261, 1, pp. 41–49. DOI: [10.1016/0165-1218(91)90096-5](https://doi.org/10.1016/0165-1218\(91\)90096-5).

*   [Andrushkiw R.I](#ch09.xhtml#r003b)., Boroday N.V., Klyushin D.A., Petunin Y.A. *Computer-aided cytogenetic method of cancer diagnosis*. New York: Nova Publishers, 2007. ISBN 10: 1-59454-882-X.

*   [Bedin V.](#ch09.xhtml#r004b) et al. 2010. Fractal dimension of chromatin is an independent prognostic factor for survival in melanoma. *BMC Cancer*. 10, 260. doi:[10.1186/1471-2407-10-260](https://doi.org/10.1186/1471-2407-10-260).

*   [Bikou O.](#ch09.xhtml#r005b) et al. 2016. Fractal dimension as a diagnostic tool of complex endometrial hyperplasia and well-differentiated endometrioid carcinoma. *In Vivo*. 30, pp. 681–690.

*   [Boroday N.](#ch09.xhtml#r006b), Chekhun V., Golubeva E. and Klyushin D. 2016. In vitro and in vivo densitometric analysis of DNA content and chromatin texture in nuclei of tumor cells under the influence of a nano composite and magnetic field. *Advances in Cancer Research & Treatment*. 2016, 706183. pp. 1–11, DOI: [10.5171/2016.706183](https://doi.org/10.5171/2016.706183).
