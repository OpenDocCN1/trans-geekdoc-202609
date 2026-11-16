Sp = \frac{TN}{FP + FN} \quad (2.22)

Gm = \sqrt{Sn \times Sp} \quad (2.23)

where F1, Sn, Sp and Gm are F-score, sensitivity, specificity and geometric mean, respectively. The best results are listed in table 2.5.

As seen from table 2.5, the proposed SN achieved high F1-score, sensitivity, specificity and geometric mean. The used dataset is also a homogenous dataset. Therefore, we obtained these results which are listed in table 2.5. Also, the area under curve (AUC) was calculated as 100%.

As seen in table 2.5, the proposed SN extracts distinctive features, because the used conventional classifiers can achieve high success rates in a short time.

The successful machine learning methods generally have many layers and they should manage parameters efficiently. Hence, the computational complexities of these methods are very high. The proposed method has low computation cost because it is calculated as O(pn) ≅ O(n) where p defines a constant number and p is also number of used methods. Also, the average execution time of the SN is given in table 2.6 step by step.

This table proves that the developed model is very fast and lightweight. The success of the proposed method clearly indicates that the developed SN can achieve high accuracy rates using a larger sEMG dataset. Also, the computational complexity of the developed model is calculated to evaluate the proposed method. The computational complexity of the proposed SN is shown in table 2.7 step by step [53].

| Subjects | F1-score | Sn | Sp | Gm |
| :--- | :--- | :--- | :--- | :--- |
| F1 | 100.0% | 100.0% | 100.0% | 100.0% |
| F2 | 100.0% | 100.0% | 100.0% | 100.0% |
| F3 | 100.0% | 100.0% | 100.0% | 100.0% |
| M1 | 100.0% | 100.0% | 100.0% | 100.0% |
| M2 | 100.0% | 100.0% | 100.0% | 100.0% |
| Average | 100.0% | 100.0% | 100.0% | 100.0% |

| Step | Time (seconds) |
| :--- | :--- |
| Load signal | 2.11 ×10⁻⁴ |
| Pre-processing and feature extraction | 0.0383 |
| The proposed NCA and tansig based feature reduction | 0.0089 |
| Training using 10-fold cross validation | 0.1614 |