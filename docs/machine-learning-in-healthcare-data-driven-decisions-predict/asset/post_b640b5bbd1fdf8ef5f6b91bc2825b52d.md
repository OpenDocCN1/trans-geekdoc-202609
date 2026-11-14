
Figure 10: Bagging – SHAP values.

Figure 11: SHAP values of XGBoost.

![](img/106ef0dba620d314f9842503e8ef40c8_63_0.png)

Figure 12: Performance of bagging and boosting.

Table 1: Performance of all the models.

| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| LR | 76.62 | 65.62 | 61.76 | 63.64 |
| DT | 72.08 | 56.56 | 67.65 | 61.61 |
| SVM | 76.3 | 66.29 | 57.84 | 61.78 |
| RF | 76.62 | 65 | 63.73 | 64.36 |
| kNN | 75 | 63.16 | 58.82 | 60.91 |
| Hard voting | 76.95 | 67.03 | 59.8 | 63.21 |
| Soft voting | 78.25 | 67.68 | 65.69 | 66.67 |
| Bagging | 75 | 62.89 | 59.8 | 61.31 |
| AdaBoost | 75.32 | 62.5 | 63.73 | 63.11 |
| XGBoost | 76.62 | 63.64 | 68.63 | 66.04 |
| Stacking model 1 | 77.27 | 66 | 64.71 | 65.35 |
| Stacking model 2 | 78.25 | 68.42 | 63.73 | 65.99 |
| Stacking model 3 | 76.3 | 64.65 | 62.75 | 63.68 |
| Stacking model 4 | 74.03 | 60.38 | 62.75 | 61.54 |

![](img/106ef0dba620d314f9842503e8ef40c8_64_0.png)

Figure 13: Performance of stacking models. Bar graph displaying classification performance of four stacking ensemble models.

![](img/106ef0dba620d314f9842503e8ef40c8_64_1.png)

Figure 14: SHAP values of stacking 1.

## 5 Conclusion

Diabetes remains one of the leading global health challenges, demanding accurate and efficient diagnostic methods to optimize medical resources and improve patient outcomes. While machine learning has shown great potential in detecting diabetes, relying on a single model often falls short in capturing the complexity of the disease. This chapter validates various ensemble methods such as voting, boosting, bagging, and stacking and finds which offers a more robust and effective approach to combine models. Among the ensemble models for diabetes classification, the soft voting ensemble achieved the highest performance in terms of accuracy of 78.25%. This highlights the use of ensembling methods in medical data classification.

Although ensemble methods provide promising results than a single model, the complexity and computation resources required for building the ensemble model are huge. There is always a trade-off between model accuracy and complexity.

In future work, we aim to develop a user-friendly website where users can directly enter their data and find the diabetes result.

## References

- [1] S S, S., Surendiran, J., Yuvaraj, N., Ramkumar, M., Ravi, C., & Vidhya, R. (2022). Classification of diabetes using multilayer perceptron. In 2022 IEEE international conference on distributed computing and electrical circuits and electronics (icdcece) (pp. 1–5). doi: 10.1109/ICDCECE53908.2022.9793085.

- [2] Dubey, Y., Wankhede, P., Borkar, T., Borkar, A., & Mitra, K. (2021). Diabetes prediction and classification using machine learning algorithms. In 2021 IEEE international conference on biomedical engineering, computer and information technology for health (becthcon) (pp. 60–63). doi: 10.1109/BECITHCON54710.2021.9893653.

- [3] Lixandru-Petre, I.-O. (2020). A fuzzy system approach for diabetes classification. In 2020 international conference on e-health and bioengineering (EHB) (pp. 14). doi: 10.1109/EHB50910.2020.9279882.

- [4] Islam, N. U., & Khanam, R. (2021a). Classification of diabetes using machine learning. In 2021 international conference on computational performance evaluation (COMPE) (pp. 185–189). doi: 10.1109/CompE53109.2021.9751955.

- [5] Warsi, G. G., Saini, S., & Khatri, K. (2019). Ensemble learning on diabetes data set and early diabetes prediction. In 2019 international conference on computing, power and communication technologies (GUCON) (pp. 182–187).

- [6] Ramteke, N., & Maidamwar, P. (2023, Jul). Cardiac patient data classification using ensemble machine learning technique. In 2023 14th International Conference on Computing Communication and Networking Technologies(ICCCNT) (pp. 1–6). doi: 10.1109/icccnt56998.2023.10307702.

- [7] Juez-Gil, M., Arnaiz-González, Rodríguez, J. J., & García-Osorio, C. (2021, Sep). Experimental evaluation of ensemble classifiers for imbalance in big data. Applied Soft Computing, 108, 107447. doi: 10.1016/j.asoc.2021.

- [8] Aljame, M., Ahmad, I., Imtiaz, A., & Mohammed, A. (2020). Ensemble learning model for diagnosing covid-19 from routine blood tests. Informatics in Medicine Unlocked, 21, 100449. doi: 10.1016/j.imu.2020.100449.

- [9] Senthilkumar, T.P., & Prabhusundar, P. (2020, Mar). An effective feature selection and incremental classifier design for rice disease prediction. Journal of Advanced Research in Dynamical and Control Systems, 12(SP4), 770–786. doi: 10.5373/jardcs/V12SP4/20201545.

- [10] Islam, N. U., & Khanam, R. (2021b). Classification of diabetes using machine learning. In 2021 international conference on computational performance evaluation (COMPE) (pp. 185–189). doi: 10.1109/ComPE53109.2021.9751955.

- [11] Talapaneni, S., Kota, C. S., Yalagala, N., Nunna, R., & Mothukuri, R. (2024). Enhancing heart disease prediction and analysis: An efficient voting ensemble model. In 2024 international conference on communication, computer sciences and engineering (IC3SE) (pp. 156–160). doi: 10.1109/IC3SE62002.2024.10593602.

- [12] Kumar, A., Sushil, R., & Tiwari, A. K. (2021). Classification of breast cancer using user-defined weighted ensemble voting scheme. In Tencon 2021 – 2021 IEEE region 10 conference (TENCON) (pp. 134–139). doi: 10.1109/TENCON54134.2021.9707374.

- [13] Mijoya, I. B., Khurana, S., Gupta, N., & Gupta, K. (2023). Malware detection in mobile devices using hard voting ensemble technique. In 2023 international conference on computing, communication, and intelligent systems (ICCCIS) (pp. 116–121). doi: 10.1109/ICCCIS60361.2023.10425513.

- [14] Ramadhan, N. G., & Fitriana, G. F. (2024). Analysis comparison of hard and soft voting ensemble model for sentiment analysis on IMDB movie reviews. In 2024 ninth international conference on informatics and computing (ICIC) (pp. 1–4). doi: 10.1109/ICIC64337.2024.10956377.

- [15] Sen, K., & Verma, B. (2023). Heart disease prediction using a soft voting ensemble of gradient boosting models, random forest, and Gaussian Naive Bayes. In 2023 4th international conference for emerging technology (INCET) (pp. 1–7). doi: 10.1109/INCET57972.2023.10170399.

- [16] Wang, Y., Zheng, J., Wang, D., & Zhang, Z. (2023). Multi-objective planning model based on the soft voting ensemble learning algorithm. In 2023 IEEE international conference on electrical, automation and computer engineering (ICEACE) (pp. 1104–1107). doi: 10.1109/ICEACE60673.2023.10442166.

- [17] Sreenath, M., & Udhayan, J. (2015). Intrusion detection system using bagging ensemble selection. In 2015 IEEE international conference on engineering and technology (ICETECH) (pp. 1–4). doi: 10.1109/ICETECH.2015.7275015.

- [18] Ward, M., Malmsten, K., Salamy, H., & Min, C.-H. (2021). Data balanced bagging ensemble of convolutional–LSTM neural networks for time series data classification with an imbalanced dataset. In 2021 IEEE international symposium on circuits and systems (ISCAS) (pp. 1–5). doi: 10.1109/ISCAS51556.2021.9401389.

- [19] Tella, H., Mohandes, M., Al-Shaikhi, A., Liu, B., Rehman, S., & Nuha, H. (2023). Bagging and voting deep learning ensemble methods for binary classifications of solar panel cells defects. In 2023 20th international multi-conference on systems, signals devices (SSD) (pp. 104–108). doi: 10.1109/SSD58187.2023.10411247.

- [20] V, V., PK, M. J., S, N., & S, P. D. (2023). Ensemble machine learning based weather prediction system. In 2023 international conference on communication, security and artificial intelligence (ICCSAI) (pp. 996–1000). doi: 10.1109/ICCSAI59793.2023.10421274.

- [21] Omer, Z. M., & Shareef, H. (2019). Adaptive boosting and bootstrapped aggregation based ensemble machine learning methods for photovoltaic systems output current prediction. In 2019 29th Australasian universities power engineering conference (AUPEC) (pp. 1–6). doi: 10.1109/AUPEC48547.2019.211856.

- [22] Wu, S., & Nagahashi, H. (2014). Parameterized adaboost: Introducing a parameter to speed up the training of real adaboost. IEEE Signal Processing Letters, 21(6), 687–691 doi: 10.1109/LSP.2014.2313570.

- [23] Dutta, J., Kim, Y. W., & Dominic, D. (2020). Comparison of gradient boosting and extreme boosting ensemble methods for webpage classification. In 2020 fifth international conference on research in computational intelligence and communication networks (ICRCICN) (pp. 77–82). doi: 10.1109/ICRCICN50933.2020.9296176.
