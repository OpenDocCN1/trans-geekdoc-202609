Table 1 provides an overview of the characteristics of patients exhibiting immunodeficiency patterns. The patients under study demonstrated a decline in the count of several immune cells. This was particularly evident in the case of NK cells, a component of the innate immune system, and CD19 B-cells, a part of the adaptive immune system. The latter includes IgG subclasses and IgM, both of which also showed a decrease. These patients exhibited reduced levels of various immune cells, as illustrated in Table 1, with notable decreases observed in NK cells within the innate immune system and CD19 B-cells within the adaptive immune system, including IgG subclasses and IgM.

# Table 1. Characteristics of patients with immunodeficiency patterns.

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

The study employed a range of ML techniques to discern patterns of innate and adaptive immunodeficiency within the SLE population. The findings derived from these techniques, coupled with several ML algorithms for identifying immunodeficiency, are detailed below. Performance metrics such as BA, recall, specificity, precision, and AUC for the investigated ML methods are exhibited in Tables 2 and 3. Both tables provide a detailed summary of performance metrics for different ML methods applied to variables IgG, IgG2, IgG3, IgG4 (Table 2), and IgM, NK, CD19, CD3 (Table 3). These variables are associated with immunoglobulins and immune cell populations, whilst the ML methods evaluated include SVM, BLDA, DT, KNN, and the RF proposed method. The results offer insights into how well each ML method performs in predicting or classifying the specified immunological variables, providing a comparative analysis of their strengths in terms of these metrics. The comprehensive nature of the data facilitates an informed selection of the most suitable method for each variable, based on the desired performance criteria. Of particular note is the RF proposed method, which consistently outperforms across all variables, achieving the highest accuracy. KNN also demonstrates strong performance, particularly in IgM and CD3. LR were the lowest results obtained, whilst SVM, BLDA, and DT generally exhibit competitive results but with slightly lower accuracy than RF and KNN. In summary, the evaluation underscores the robust performance of the proposed