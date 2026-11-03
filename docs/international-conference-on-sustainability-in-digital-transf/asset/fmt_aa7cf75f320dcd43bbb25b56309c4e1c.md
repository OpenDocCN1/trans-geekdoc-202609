
`Precision = TP/(TP + FP)`

(3)

`Recall = TP/(TP + FN)`

(4)

`F-measure = (2*precision*recall)/(precision + recall)`

(5)

`Mean absolute error (MAE) = (p[1]-a[1]) + (p[2]-a[2]) + ....(P[n]-a[n]) divided by n`

Where `p` denotes predicted value and `a` denotes actual value.

## Result and Implementation

“[Figure 27.2](#ch27.xhtml#fig27_2) presents the pre-processing and extraction of dental dataset showing distinct 12 attributes that needs to be worked upon. These are dental diseases namely Odontoclasis, caries, dental eruptions, Gingivitis, Mumps etc.”

![Figure 27.2 Feature extraction using WEKA](images/fig27_2_C.jpg)

[Figure 27.2 Feature extraction using WEKA](#ch27.xhtml#R_fig27_2)

“[Figure 27.3](#ch27.xhtml#fig27_3) displays the successful execution of `KNN` classifier on dental dataset. The model is evaluated on full training dataset by taking features extracted into consideration.”

![Figure 27.3 Applying KNN classifier](images/fig27_3_B.jpg)

[Figure 27.3 Applying KNN classifier](#ch27.xhtml#R_fig27_3)

[Figure 27.4](#ch27.xhtml#fig27_4) shows the successful validation of our methodology by using `KNN` classifier. It is done using 10 folds cross validation which leads to values of `MAE`, `Precision`, `recall` etc.

![Figure 27.4 Validation of Dataset using KNN Classifier](images/fig27_4_C.jpg)

[Figure 27.4 Validation of Dataset using KNN Classifier](#ch27.xhtml#R_fig27_4)

“[Figure 27.5](#ch27.xhtml#fig27_5) shows successful execution of `MLP` classifier on dental dataset. The model is evaluated on full training dataset by taking features extracted into consideration.”

![Figure 27.5 Applying MLP classifier](images/fig27_5_C.jpg)

[Figure 27.5 Applying MLP classifier](#ch27.xhtml#R_fig27_5)

[Figure 27.6](#ch27.xhtml#fig27_6) shows Entropy calculated values & [Figure 27.7](#ch27.xhtml#fig27_7) displays the Evaluation metrics which is been attached below in the article.

![Figure 27.6 Entropy calculated values in response to Table 27.1](images/fig27_6_C.jpg)

[Figure 27.6 Entropy calculated values in response to](#ch27.xhtml#R_fig27_6) [Table 27.1](#ch27.xhtml#tab27_1)

[Table 27.1 Entropy calculation results with respect to dental conditions.](#ch27.xhtml#R_tab27_1)

| ATTRIBUTES | VALUES |
|---|---|
| `Odontoclasts` | -2 log base2 = 0.25 |
| `Caries` | -4 log base 2 = 0.0625 |
| `Dental Eruption` | -5 log base 2= 0.03125 |
| `Gingivitis` | -3 log base 2 = 0.125 |
| `Mumps` | -7 log base 2= 0.07812 |
| `Xerostomia` | -1 log base 2 = 0.5 |
| `Wisdom Tooth Inflammation` | -8 log base 2 = 0.003906 |
| `Bruxism` | -9log base 2 = 0.001953 |
| `Jaw Dislocation` | 0.25 |
| `Gnashing` | 0.125 |

![Figure 27.7 Evaluation metrics comparison](images/fig27_7_C.jpg)

[Figure 27.7 Evaluation metrics comparison](#ch27.xhtml#R_fig27_7)

[Table 27.2](#ch27.xhtml#tab27_2) shows that our approach works best with `MLP` classifier with an accuracy of 97.4% and excellent ROC area under curve as 0.85.

[Table 27.2 Comparison of evaluation metrics with respect to 10 folds crosses validation of dental diseases dataset.](#ch27.xhtml#R_tab27_2)

| Metrics | `KNN` | `MLP` |
|---|---|---|
| **Correctly classified instances** | 95.5% | 97.4% |
| `Mae` | 1.23 | 0.159 |
| `Precision` | 0.94 | 0.95 |
| `Recall` | 0.95 | 0.96 |
| `Accuracy` | 94.6% | 97.4% |
| `F-Measure` | 0.94 | 0.95 |
| `ROC Area` | 0.75 | 0.85 |

## Conclusion and Future Work

In this research, we want to identify the most efficient predictive data mining algorithms for diagnosing oral health issues. The dataset was extracted from Kaggle’s repository, cleaned, and filtered to increase precision and reduce the likelihood of bias. To identify oral health issues, we implemented a multilayer perceptron and `KNN` predictive data mining system. To ensure each classifier’s baseline performance is at its highest possible level, it was calibrated to find its unique ideal parameter values. Algorithms’ impartial predicting accuracy was evaluated using a 10-fold cross-validation assessment that included a stratified sample.

Naive bayes, multilayer perceptron and `J48` decision tree induction are all promising methods for clinical prediction that we want to explore in future studies.

## References

1. [Chitnis, G., Bhanushali, V., Ranade, A., Khadase, T., Pelagade, V., and Chavan, J.](#ch27.xhtml#R_ref27_1) (2020). A review of machine learning methodologies for dental disease detection. In IEEE India Council International Subsections Conference (INDISCON), Visakhapatnam, India, (pp. 63-65), doi: [10.1109/INDISCON50162.2020.00025](http://dx.doi.org/10.1109/INDISCON50162.2020.00025).

2. [Manurung, J., Perwira, Y., and Sinaga, B.](#ch27.xhtml#R_ref27_2) (2022). Expert system to diagnose dental and oral disease using naive bayes method. In IEEE International Conference of Computer Science and Information Technology (ICOSNIKOM), Laguboti, North Sumatra, Indonesia, (pp. 01-04), doi: [10.1109/ICOSNIKOM56551.2022.10034871](http://dx.doi.org/10.1109/ICOSNIKOM56551.2022.10034871).

3. [Hossam, A., Mohamed, K., Tarek, R., Elsayed, A., Mostafa, H., and Selim, S.](#ch27.xhtml#R_ref27_3) (2021). Automated dental diagnosis using deep learning, In 16th International Conference on Computer Engineering and Systems (ICCES), Cairo, Egypt, Egypt, (pp. 1-5), doi: [10.1109/ICCES54031.2021.9686185](http://dx.doi.org/10.1109/ICCES54031.2021.9686185).

4. [Usha Kiruthika, S., Priya, J., and Kanaga Suba Raja, S.](#ch27.xhtml#R_ref27_4) (2023). Systematic review of deep learning models for dental images, In 7th International Conference on Computing Methodologies and Communication (ICCMC), Erode, India, (pp. 287-291), doi: [10.1109/ICCMC56507.2023.10083729.](http://dx.doi.org/10.1109/ICCMC56507.2023.10083729)

5. [Zegan, G., Carausu, E. M., Anistoroaei, D., Golovcencu, L., Sodor-Botezatu, A., and Dascalu, C. G.](#ch27.xhtml#R_ref27_5) (2021). Assessment of dental students’ knowledge about SarS-CoV-2 infection through an online questionnaire, In International Conference on e-Health and Bioengineering (EHB), Iasi, Romania, (pp. 1-4), doi: [10.1109/EHB52898.2021.9657697.](http://dx.doi.org/10.1109/EHB52898.2021.9657697)

6. [Kurniawan, R., Hasana, W., Negara, B. S., Zakree Ahmad Nazri, M., Lestari, F., and Iskandar, I.](#ch27.xhtml#R_ref27_6) (2021). Prediction model for diagnosis of pulpitis diseases using learning vector quantization 3. In 4th International Conference of Computer and Informatics Engineering (IC2IE), Depok, Indonesia, (pp. 9-12), doi: [10.1109/IC2IE53219.2021.9649223.](http://dx.doi.org/10.1109/IC2IE53219.2021.9649223)

7. [Kanna, R. K., Surendhar, P. A., Rubi, J., Jyothi, G., Ambikapathy, A., and Vasuki, R.](#ch27.xhtml#R_ref27_7) (2022, December). Human Computer Interface Application for Emotion Detection Using Facial Recognition. In 2022 IEEE International Conference on Current Development in Engineering and Technology (CCET) (pp. 1-7). IEEE.

8. [Samiappan, D., Jayaraj, R., Nijanth Shankar, K., and Nithish Kumar, N.](#ch27.xhtml#R_ref27_8) (2023). Analysis of dental x-ray images for the diagnosis and classification of oral conditions. In 7th International Conference on Computing Methodologies and Communication (ICCMC), Erode, India, (pp. 564-569), doi: [10.1109/ICCMC56507.2023.10083914](http://dx.doi.org/10.1109/ICCMC56507.2023.10083914).

9. [Moein, S., Yan, H., Das, S., Hall, M., and Eghtesady, P.](#ch27.xhtml#R_ref27_9) (2015). Prediction of systemic-to-pulmonary artery shunt surgery outcomes using administrative data. In IEEE International Conference on Bioinformatics and Biomedicine (BIBM), Washington, DC, (pp. 737-741), doi: [10.1109/BIBM.2015.7359777.](http://dx.doi.org/10.1109/BIBM.2015.7359777)
