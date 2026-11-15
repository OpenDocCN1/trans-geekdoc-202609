
## Table 4. The table presents the F1 score, MCC, DYI and Kappa values for variables IgG, IgG2, IgG3 and IgG4.

| Methods | F1 score | MCC | DYI | Kappa |
|---|---|---|---|---|
| SVM | 80.61 | 71.74 | 80.85 | 71.98 |
| BLDA | 77.87 | 69.31 | 78.11 | 69.54 |
| DT | 83.60 | 74.40 | 83.85 | 74.65 |
| LR | 70.06 | 64.59 | 69.83 | 64.23 |
| RF | 93.68 | 83.37 | 93.96 | 83.65 |
| KNN | 86.12 | 76.65 | 86.38 | 76.90 |

| Methods | F1 score | MCC | DYI | Kappa |
|---|---|---|---|---|
| SVM | 81.61 | 72.63 | 81.85 | 72.87 |
| BLDA | 77.14 | 68.65 | 77.37 | 68.88 |
| DT | 82.91 | 73.79 | 83.16 | 74.04 |
| LR | 69.54 | 64.12 | 69.32 | 63.76 |
| RF | 94.30 | 83.92 | 94.58 | 84.20 |
| KNN | 85.73 | 76.30 | 85.99 | 76.55 |

| Methods | F1 score | MCC | DYI | Kappa |
|---|---|---|---|---|
| SVM | 81.32 | 72.37 | 81.56 | 72.61 |
| BLDA | 78.92 | 70.24 | 79.16 | 70.47 |
| DT | 83.57 | 74.38 | 83.82 | 74.62 |
| LR | 69.48 | 64.06 | 69.25 | 63.70 |
| RF | 94.14 | 83.78 | 94.42 | 84.06 |
| KNN | 86.31 | 76.81 | 86.57 | 77.07 |

| Methods | F1 score | MCC | DYI | Kappa |
|---|---|---|---|---|
| SVM | 81.11 | 72.19 | 81.35 | 72.43 |
| BLDA | 78.69 | 70.03 | 78.93 | 70.27 |
| DT | 83.01 | 73.88 | 83.26 | 74.13 |
| LR | 70.19 | 64.72 | 69.96 | 64.35 |
| RF | 94.22 | 83.85 | 94.50 | 84.13 |
| KNN | 85.81 | 76.37 | 86.07 | 76.62 |

## Table 5. The table presents the F1 score, MCC, DYI and Kappa values for variables IgM, NK, CD19 and CD3.

| Methods | F1 score | MCC | DYI | Kappa |
|---|---|---|---|---|
| SVM | 81.00 | 72.09 | 81.24 | 72.33 |
| BLDA | 77.87 | 69.31 | 78.11 | 69.54 |
| DT | 83.10 | 73.96 | 83.35 | 74.21 |
| LR | 69.90 | 64.45 | 69.67 | 64.08 |
| RF | 94.51 | 84.12 | 94.80 | 84.40 |
| KNN | 86.12 | 76.65 | 86.38 | 76.90 |

| Methods | F1 score | MCC | DYI | Kappa |
|---|---|---|---|---|
| SVM | 80.82 | 71.93 | 81.06 | 72.17 |
| BLDA | 77.29 | 68.78 | 77.52 | 69.01 |
| DT | 84.59 | 75.28 | 84.84 | 75.53 |
| LR | 69.54 | 64.12 | 69.32 | 63.76 |

## Table 5. Cont.

| Methods | F1 score | MCC | DYI | Kappa |
|---|---|---|---|---|
| **NK.** | | | | |
| RF | 94.46 | 84.07 | 94.75 | 84.35 |
| KNN | 86.25 | 76.76 | 86.51 | 77.02 |
| **CD19.** | | | | |
| SVM | 81.97 | 72.95 | 82.21 | 73.19 |
| BLDA | 76.66 | 68.23 | 76.89 | 68.45 |
| DT | 83.79 | 74.57 | 84.04 | 74.82 |
| LR | 69.68 | 64.25 | 69.45 | 63.89 |
| RF | 94.06 | 83.71 | 94.34 | 83.99 |
| KNN | 84.98 | 75.63 | 85.24 | 75.89 |
| **CD3.** | | | | |
| SVM | 81.22 | 72.28 | 81.46 | 72.52 |
| BLDA | 76.98 | 68.51 | 77.21 | 68.74 |
| DT | 83.91 | 74.68 | 84.16 | 74.93 |
| LR | 70.45 | 64.96 | 70.22 | 64.59 |
| RF | 94.83 | 84.40 | 95.12 | 84.68 |
| KNN | 86.12 | 76.65 | 86.38 | 76.90 |

## ROC

![](img/46da2aabc253ed283db238584dfa3d21_20_0.png)

Figure 2. Example of ROC curve for the five assessed ML predictors for variable CD19.

In the study conducted, it was also observed that the subsets used for training the model exhibited high scores in the training metrics. When these models were tested, they showed a noticeable decrease in their scores. Nonetheless, as depicted in Figures 3 and 4, the RF system emerges as a well-calibrated model, attaining an optimal point in training without succumbing to overfitting or underfitting. This approach consistently delivers accurate predictions for novel inputs. The RF system’s superior performance is evident, where it surpasses other methods by covering a larger area in the radar plots in both the training and testing phases.

![](img/46da2aabc253ed283db238584dfa3d21_21_0.png)

Figure 3. The figure shows the radar plots of the variables IgG, IgG2, IgG3 and IgG4, respectively.

![](img/46da2aabc253ed283db238584dfa3d21_22_0.png)

Figure 4. The figure shows the radar plots of the variables IgM, NK, CD19 and CD3, respectively.

## 4. Discussion

The task of managing patients with SLE is crucial in order to reduce the risk of irreversible organ damage [30,31]. This is not only vital for maintaining the health-related quality of life of the patients [32,33], but also for managing the direct costs associated with the treatment of SLE [34,35]. However, this task presents significant challenges due to the heterogeneous nature of SLE, which is characterized by variations in disease progression [36,37]. There is therefore an urgent need to improve the accuracy and classification of SLE flares, taking into account that the trigger of activity may be an infection in a situation of immunodeficiency. Numerous studies have been conducted to address this need, including recent research that has emerged over the last few years [31,33]. These studies have emphasized potential treatments for severe lupus manifestations such as lupus nephritis [31]. Despite the existence of several therapeutic agents in SLE, the disease continues to cause significant morbidity [31]. It is encouraging that a variety of therapeutic options are currently under investigation [31].

In clinical practice, the manifestation of a malar rash, coupled with the detection of anti-DNA autoantibodies in patients, often guides healthcare professionals towards the diagnosis of SLE [38,39]. It is noteworthy that SLE is characterized by a significant degree of phenotypic diversity, which includes both systemic and localized forms. The evolution of immunological and clinical features over time underscores the dynamic nature of this disease [33,40].

A multitude of models have been established to estimate the probability of SLE occurrence, providing a degree of confidence in differentiating it from other rheumatological disorders. These models leverage unsupervised clustering based on the nature and abundance of features, mirroring diagnostic reasoning, especially during initial patient consultations [41,42]. Certain models incorporate gene analysis techniques to improve the classification of SLE patients [19]. Recent research has delved into the utilization of machine learning techniques for SLE analysis, customizing their methodologies to the specific dataset under investigation [22,43,44]. For example, Jorge et al. [20] utilized ML techniques to predict the hospitalization of SLE patients.

In the present study, the RF method, among all the ML classifiers employed, exhibited the most robust classification performance. It demonstrated superior accuracy levels and facilitated the identification of immunodeficiency patterns within the SLE population. This method offers scalability, rapid execution, and other beneficial features that enhance its classification capabilities [45]. ML models possess the capability to evaluate multiple variables and their interrelationships concurrently, accommodating non-linear patterns in the development of predictive systems [45]. Furthermore, we conducted a comparative analysis of our proposed system's performance against various ML algorithms documented in Tables 2–5. Notably, the RF method exhibited a substantial improvement, outperforming DT, BLDA and SVM, which demonstrated lower performance. Whilst the KNN method closely approached our proposed method, achieving AUC = 86% and Recall = 86%, RF demonstrated superior performance, surpassing both metrics with remarkable values of AUC and Recall, reaching around 94%. This notable improvement highlights the efficacy of the RF method in capturing complex patterns and enhancing the overall predictive capabilities.

Additionally, Figures 3 and 4 illustrate a well-balanced performance graph for our proposed system, indicating minimal disparities between training and testing phases and no signs of overfitting. This establishes the system as a dependable tool, facilitating automated analysis to aid in the classification of SLE patients. Our results affirm the efficacy of the RF system in precisely predicting SLE patients, establishing it as a valuable tool for supporting SLE diagnosis.

## 5. Conclusions

In conclusion, due to the complexity of this elusive autoimmune disease, the use of ML algorithms such as RF is critical for the classification and rapid detection of patients with SLE flares. SLE presents with a range of challenging symptoms that are particularly difficult to diagnose accurately in its early stages. The intricate relationship between infections and autoimmunity in SLE underscores the critical need for preventative measures and the early detection of infections in SLE patients exhibiting heightened susceptibility. This integrated approach aims to address the multifaceted challenges of SLE, providing a more holistic understanding for improved patient care.

RF's proficiency in handling diverse datasets and extracting intricate patterns makes it well-suited for identifying subtle indicators of SLE. The algorithm's swift information processing enables quick detection, allowing for timely intervention and personalized treatment plans for SLE patients. Given the rarity and importance of SLE, the use of RF and similar ML approaches not only improves the diagnostic accuracy of SLE activity, but
