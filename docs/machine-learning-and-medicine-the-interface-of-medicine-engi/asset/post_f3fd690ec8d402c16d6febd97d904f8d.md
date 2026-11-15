
Table 1 provides an overview of the characteristics of patients exhibiting immunodeficiency patterns. The patients under study demonstrated a decline in the count of several immune cells. This was particularly evident in the case of NK cells, a component of the innate immune system, and CD19 B-cells, a part of the adaptive immune system. The latter includes IgG subclasses and IgM, both of which also showed a decrease. These patients exhibited reduced levels of various immune cells, as illustrated in Table 1, with notable decreases observed in NK cells within the innate immune system and CD19 B-cells within the adaptive immune system, including IgG subclasses and IgM.

## Table 1. Characteristics of patients with immunodeficiency patterns.

| Characteristics of Patients with Immunodeficiency Patterns | |
|---|---|
| N | 77 |
| Median age (years) | 52 |
| Female/Male | 68/9 |
| SLE evolution time (years) | 14 |
| Corticosteroids (n) | 50 (64.9%) |
| Immunosuppressants (n) | 25 (32.4%) |
| Hydroxychloroquine (n) | 37 (48%) |
| Severe infections (n) | 51 |
| Immunodeficiency patterns (n) | |
| Leucocytes (<4000 cL/µL ) | 9 |
| Lymphocytes (<1500 cL/µL) | 28 |
| Neutrophils (<1800 cL/µL) | 9 |
| CD3 (<700 cL/µL) | 10 |
| CD4 (<300 cL/µL) | 6 |
| CD8 (<200 cL/µL) | 3 |
| CD19 (<100 cL/µL) | 23 |
| NK (<90 cL/µL) | 13 |
| IgK (<870 mg/dL) | 17 |
| IgG1 (<383 mg/dL) | 3 |
| IgG2 (<242 mg/dL) | 36 |
| IgG3 (<22 mg/dL) | 16 |
| IgG4 (<4 mg/dL) | 7 |
| IgA (117 mg/dL) | 8 |
| IgM (<60 mg/dL) | 20 |
| C3 (<90 mg/dL) | 13 |
| C4 (<10 mg/dL) | 6 |

The study employed a range of ML techniques to discern patterns of innate and adaptive immunodeficiency within the SLE population. The findings derived from these techniques, coupled with several ML algorithms for identifying immunodeficiency, are detailed below. Performance metrics such as BA, recall, specificity, precision, and AUC for the investigated ML methods are exhibited in Tables 2 and 3. Both tables provide a detailed summary of performance metrics for different ML methods applied to variables IgG, IgG2, IgG3, IgG4 (Table 2), and IgM, NK, CD19, CD3 (Table 3). These variables are associated with immunoglobulins and immune cell populations, whilst the ML methods evaluated include SVM, BLDA, DT, KNN, and the RF proposed method. The results offer insights into how well each ML method performs in predicting or classifying the specified immunological variables, providing a comparative analysis of their strengths in terms of these metrics. The comprehensive nature of the data facilitates an informed selection of the most suitable method for each variable, based on the desired performance criteria. Of particular note is the RF proposed method, which consistently outperforms across all variables, achieving the highest accuracy. KNN also demonstrates strong performance, particularly in IgM and CD3. LR were the lowest results obtained, whilst SVM, BLDA, and DT generally exhibit competitive results but with slightly lower accuracy than RF and KNN. In summary, the evaluation underscores the robust performance of the proposed method across the variables related to immunoglobulins and immune cell types, being the preferred model for classifying SLE patients due to its consistently high accuracy, balanced performance metrics, ensemble learning strengths, and robustness to noisy data observed.

## Table 2. The table summarises the values of BA, recall, specificity, precision and AUC for variables IgG, IgG2, IgG3 and IgG4.

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 80.85 | 80.95 | 80.76 | 80.28 | 80.00 |
| BLDA | 78.11 | 78.20 | 78.02 | 77.55 | 78.00 |
| DT | 83.85 | 83.95 | 83.75 | 83.25 | 83.00 |
| LR | 70.02 | 69.75 | 68.84 | 68.95 | 68.42 |
| RF | 93.96 | 94.07 | 93.85 | 93.29 | 94.00 |
| KNN | 86.38 | 86.48 | 86.28 | 85.76 | 86.00 |

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 81.85 | 81.95 | 81.76 | 81.27 | 81.00 |
| BLDA | 77.37 | 77.46 | 77.28 | 76.82 | 77.00 |
| DT | 83.16 | 83.26 | 83.06 | 82.57 | 83.00 |
| LR | 69.51 | 69.24 | 68.33 | 68.44 | 68.42 |
| RF | 94.58 | 94.69 | 94.47 | 93.90 | 94.00 |
| KNN | 85.99 | 86.09 | 85.89 | 85.38 | 86.00 |

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 81.56 | 81.66 | 81.47 | 80.98 | 81.00 |
| BLDA | 79.16 | 79.25 | 79.06 | 78.59 | 79.00 |
| DT | 83.82 | 83.92 | 83.72 | 83.22 | 83.00 |
| LR | 69.44 | 69.17 | 68.27 | 68.38 | 68.42 |
| RF | 94.42 | 94.53 | 94.31 | 93.75 | 94.00 |
| KNN | 86.57 | 86.67 | 86.47 | 85.95 | 86.00 |

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 81.35 | 81.45 | 81.26 | 80.77 | 81.00 |
| BLDA | 78.93 | 79.02 | 78.83 | 78.36 | 78.00 |
| DT | 83.26 | 83.36 | 83.16 | 82.67 | 83.00 |
| LR | 70.15 | 69.88 | 68.97 | 69.08 | 68.42 |
| RF | 94.50 | 94.61 | 94.39 | 93.83 | 94.00 |
| KNN | 86.07 | 86.17 | 85.97 | 85.46 | 86.00 |

## Table 3. The table summarises the values of BA, recall, specificity, precision and AUC for variables IgM, NK, CD19 and CD3.

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 81.24 | 81.34 | 81.15 | 80.67 | 81.00 |
| BLDA | 78.11 | 78.20 | 78.02 | 77.55 | 78.00 |
| DT | 83.35 | 83.45 | 83.25 | 82.76 | 83.00 |
| LR | 69.86 | 69.59 | 68.68 | 68.79 | 68.42 |
| RF | 94.80 | 94.91 | 94.69 | 94.12 | 94.00 |
| KNN | 86.38 | 86.48 | 86.28 | 85.76 | 86.00 |

### NK.

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 81.06 | 81.16 | 80.97 | 80.49 | 81.00 |
| BLDA | 77.52 | 77.61 | 77.43 | 76.97 | 77.00 |
| DT | 84.84 | 84.94 | 84.74 | 84.24 | 84.00 |
| LR | 69.51 | 69.24 | 68.33 | 68.44 | 68.42 |
| RF | 94.75 | 94.86 | 94.64 | 94.07 | 94.00 |
| KNN | 86.51 | 86.61 | 86.41 | 85.89 | 86.00 |

### CD19.

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 82.21 | 82.31 | 82.12 | 81.63 | 82.00 |
| BLDA | 76.89 | 76.98 | 76.80 | 76.34 | 76.00 |
| DT | 84.04 | 84.14 | 83.94 | 83.44 | 84.00 |
| LR | 69.65 | 69.38 | 68.47 | 68.58 | 68.42 |
| RF | 94.34 | 94.45 | 94.23 | 93.67 | 94.00 |
| KNN | 85.24 | 85.34 | 85.14 | 84.63 | 85.00 |

### CD3.

| Methods | BA | Recall | Specificity | Precision | AUC |
|---|---|---|---|---|---|
| SVM | 81.46 | 81.56 | 81.37 | 80.88 | 81.00 |
| BLDA | 77.21 | 77.30 | 77.12 | 76.66 | 77.00 |
| DT | 84.16 | 84.26 | 84.06 | 83.56 | 84.00 |
| LR | 70.41 | 70.14 | 69.22 | 69.33 | 68.42 |
| RF | 95.12 | 95.23 | 95.01 | 94.44 | 95.00 |
| KNN | 86.38 | 86.48 | 86.28 | 85.76 | 86.00 |

Moreover, Tables 4 and 5 present performance metrics, including F1 score, MCC, DYI, and Kappa values, for the ML methods applied. The observed values provide insights into the models' effectiveness in classifying SLE patients. Thus, in Table 4 (variables IgG, IgG2, IgG3, and IgG4), RF consistently outperforms again other methods across all metrics, exhibiting high F1 score, MCC, DYI, and Kappa values. This suggests RF's robustness in achieving a balanced trade-off between precision and recall, capturing the model's ability to handle both positive and negative instances effectively. Again, KNN also shows competitive performance, while SVM, BLDA, and DT demonstrate slightly lower performance across these metrics, being LR the one which obtained the lowest performance values. Similar trends are observed in the variables related to immune cell types in Table 5 (IgM, NK, CD19, and CD3), where RF again demonstrates superior performance, especially notable in achieving high F1 score and DYI values. This reinforces RF's suitability for SLE classification, indicating its ability to maintain a balance between true positives, true negatives, false positives, and false negatives. KNN also perform well, but RF consistently stands out as the top-performing model across the diverse set of variables.

For a comprehensive view of the trade-off between the true/false positive rates between the proposed system and other ML methods, the Receiver Operating Characteristic (ROC) curves were also generated. With this purpose in mind, the ROC curve is employed to quantify sensitivity and 1-specificity at various threshold levels. As illustrated in Figure 2, which shows the ROC curve for CD19 variable as example, the system that utilizes RF generates the largest area under the curve, indicating a superior level of predictive accuracy.
