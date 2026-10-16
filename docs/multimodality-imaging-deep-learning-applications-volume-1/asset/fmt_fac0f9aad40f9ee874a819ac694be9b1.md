
The ELM system’s performance is determined by plotting the area-under-the-curve (AUC) and receiver operating characteristic (ROC) curve for each set of CV protocols. The performance characteristics, including accuracy, sensitivity, and specificity, which are detailed in section [10.6.1](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10s10-6-1), are also recorded. In section [10.6.2](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10s10-6-2) the stability and dependability analyses are assessed.

#### 10.6.1 ROC curves

The ELM’s performance was calculated using ROC curves for all three types of datasets: S0, S4, and S8. We used four different cross-validation techniques for each dataset: K2, K3, K5, and K10. We show the 12 ROC curves in figures [10.9](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10fig9)(A)–(C). The ROC curves were generated using the ELM and SVM for each permutation of K and S. Tables [10.1](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10t1), [B.1](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10tB_1), and [B.2](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10tB_2) exhibit the AUCs for the S0, S4, and S8 datasets. For each dataset (S0, S4 and S8), the K10 performs better of all four CV protocols and better performance was shown by the ELM when compared to the SVM (0.97 versus 0.91).

![Figure 10.9. ROC curves for (a) K2, (b) K3, (c) K5, and (d) K10 cross-validations using the S0 dataset. (Reproduced with permission from \[54\]. Copyright 2017 Springer.)](images/bk978-0-7503-2244-7ch10f9a_online.jpg)

**Figure 10.9.** ROC curves for (a) K2, (b) K3, (c) K5, and (d) K10 cross-validations using the S0 dataset. (Reproduced with permission from \[[54](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib54)\]. Copyright 2017 Springer.)

#### 10.6.2 Reliability and stability analysis

The dependability and stability of the ELM are examined in this section. This evaluation is critical because it shows how the system operates under varied settings and under recurring conditions. This demonstrates that the outcomes are regular and reproducible. The basis of the reliability index (RI) depends on the divergence of the accuracy with respect to its average as the data size increases \[[33](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib33)\]. The reliability index *ζ*[*N*[*L*]] (%)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-2244-7ch10ieqn17.gif"/ is specified as

$$\\zeta\_{N\_{L}}\\ \\left( \\% \\right) = \\left( {1 - \\frac{\\mu\_{N\_{L}}}{\\sigma\_{N\_{L}}}} \\right) \\times 100,$$  

(10.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch10eqn18.gif" position="float"/

where *μ*[*N*[*L*]]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch10ieqn19.gif"/ is the average accuracy and *σ*[*N*[*L*]]inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch10ieqn20.gif"/ represents the standard deviation for all US liver images, *N*[*L*][inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch10ieqn21.gif"/.

The stability evaluation examines how the system responds to repeated situations. We accomplish this by employing a control theory approach to dynamics \[[34](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib34)\]. To begin, a 5 % variation stability requirement is established, i.e. the system is deemed to be unstable if it varies by more than 5%. The standard deviation (SD) is then calculated for each calculation using varying data sizes. We can say that the system is stable if the SD < 5%. The RIs for all four *K*‑fold protocols in table [10.5](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10t5) are greater than 0.95, showing that the ELM classification system is quite reliable. We used second-class biometric facial data to further confirm our ELM and SVM categorization (appendix [A](#Chapter_10.xhtml#ST266)).

**Table 10.5.** ELM reliability index for varying data sizes using different *K*‑fold cross-validations. (Reproduced with permission from \[[54](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib54)\]. Copyright 2017 Springer.)

| Data size (Images)  || Normal/abnormal || Reliability index (%) |
| --- | --- | --- |
| K2 || K3 || K5 || K10 |
| 64 || 27/37 || 99.7 || 98.9 || 100.0 || 99.9 |
| --- | --- | --- | --- | --- | --- |
| 252 || 104/148 || 99.6 || 98.9 || 99.4 || 99.8 |
| 4032 || 1664/2368 || 99.8 || 99.9 || 100.0 || 99.9 |

**Table 10.6.** Benchmarking. (Reproduced with permission from \[[54](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib54)\]. Copyright 2017 Springer.)

| Authors  || Data type || Classifier type || Types of features || No. of features || Data size || Accuracy (%) |
| --- | --- | --- | --- | --- | --- | --- |
| Acharya *et al* (2012) \[[11](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib11)\] || Liver || Decision tree || HOS, texture, DWT ||  || 100 || 93.3 |
| --- | --- | --- | --- | --- | --- | --- |
| Acharya *et al* (2014) \[[29](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib29)\] || Thyroid || FC || Wavelet transform || 40 || 526 || 84.6 |
| Subramanya *et al* (2014) \[[19](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib19)\] || Liver || SVM || FOS, Gr, MI, GRLM, GLCM, Laws || 636 || 53 || 84.9 |
| Saba *et al* (2016) \[[21](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib21)\] || Liver || BPNN || BG, Fourier, DCT, Harlick, Gupta, Gabor || 128 || 62 || 97.6 |
| Liu *et al* (2017) \[[42](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib42)\] || Liver || SVM || CNN based features || 500 || 91 || 89.2 |
| Proposed work ||  || ELM ||  || 46 || 64 || 92.4 |
| Proposed work ||  ||  || 46 || 252 || 94.8 |
| Proposed work ||  ||  || 46 || 4032 || 96.7 |

FC: Fuzzy Classifier; FOS: First Order Statistics; Gr: Gradient based features; Laws: Laws texture features; BG: Basic geometric

### 10.7 Discussion

This study presented a reliable and rapid tissue characterization system (a type of Symtosis system) based on the ELM for FLD disease stratification in US liver imaging. The SLFFNN was taught using the ELM. The parameters from the input to hidden layers were initiated at random to save time and money. The parameters from the hidden to output layers were the only ones to be trained, and this was done in one pass (without iteration), making the ELM quicker than the SVM model. A previously established, the SVM based characterization system was compared to an ELM based characterization system. It is worth noting that the ELM and SVM systems have the same set of features. GRLM, GLCM, and Gabor were the three most popular grayscale features. The study’s major goal was to contrast the ELM with the SVM. We compared the ELM to the BPNN since the ELM is an NN based system. The ELM was shown to have equal accuracy and speed when the number of features was reduced by one third and the number of hidden layers was reduced by one third (as proved by the BPNN \[[21](#Chapter_10.xhtml#bk978-0-7503-2244-7ch10bib21)\]). The scientific validation was carried out by utilizing the biometric facial datasets listed in appendix [A](#Chapter_10.xhtml#ST266).

#### 10.7.1 Benchmarking
