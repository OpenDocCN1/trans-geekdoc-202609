
![](img/75406d5bb714dfd3e68fbbc717bd8f67_231_0.png)

Figure 9.10. Representation of heat map matrix visualization for feature importance.

Table 9.3. Representation of different tree algorithms performance after features selection.

| Statistics | Naive Bayes | Decision tree | Extra tree | Random forest | Bagging |
|:---|:---|:---|:---|:---|:---|
| Kappa | 0.589 | 0.667 | 0.744 | 0.85 | 0.958 |
| Overall fraction correct | 0.795 | 0.835 | 0.874 | 0.927 | 0.98 |
| Mis-classification rate | 0.205 | 0.165 | 0.126 | 0.073 | 0.02 |
| Sensitivity | 0.799 | 0.814 | 0.883 | 0.893 | 0.979 |
| Specificity | 0.79 | 0.862 | 0.862 | 0.983 | 0.983 |
| Prevalence | 0.528 | 0.567 | 0.567 | 0.62 | 0.62 |

We find a major gap between different classifiers’ performance. The prediction of all selected classifiers depends upon more related features. If the relation between features is high then classification accuracy is always high. Figure 9.12 represents the improvement of accuracy is continuous for each classifier after features selection.

![](img/75406d5bb714dfd3e68fbbc717bd8f67_232_0.png)

Figure 9.11. Representation of different algorithms for Parkinson's disease after features selection.

### Overall Fraction Correct

![](img/75406d5bb714dfd3e68fbbc717bd8f67_232_1.png)

Figure 9.12. The prediction of different classifiers in Parkinson's disease.

Parkinson's is a very dangerous disease and many research works on this disease have already been done using machine learning algorithms. Some research papers are mentioned on Parkinson's Disease using machine learning. The research areas, using techniques and their performance are listed in table 9.4. On the basis of our previous analysis of Yadav and Pal [26–29], we calculated high accuracy on the basis of the ensemble method and majority of voting. In this chapter, we try to predict better performance by some selected classifiers and finally find better classification accuracy compared to all other listed research papers. The highest accuracy of any previous research paper is (97%) by RF but in our research we find (98%) classification accuracy of Bagging Ensemble Method.

| Author's name | Area of application | Methods | Accuracy |
|---|---|---|---|
| Khoury et al [18] | Disease of Parkinson's | K-NN | 90 |
| | | CART | 86 |
| | | RF | 83 |
| | | NB | 80 |
| | | SVM | 76 |
| | | K-Means | 75 |
| | | GMM | 69 |
| Pérez et al [19] | Disease of Parkinson's | RBF | 85 |
| | | Linear | 84 |
| | | MLP | 81 |
| | | Quadratic | 79 |
| Tejeswinee et al [2] | Disease of Parkinson's | RF | 85 |
| | | K-NN | 82 |
| | | SVM | 94 |
| Cavallo et al [6] | Disease of Parkinson's | RF | 79 |
| | | SVM | 80 |
| Mostafa et al [20] | Disease of Parkinson's | DT | 86 |
| | | NB | 74 |
| | | NB | 88 |
| | | RF | 87 |
| | | SVM | 86 |
| Turker et al [21] | Disease of Parkinson's | KNN | 97 |
| | | Linear SVM | 84 |
| | | RBF SVM | 87 |
| | | Log-Reg | 85 |
| Ricciardi et al [22] | Disease of Parkinson's | RF | 86 |
| Betrouni et al [23] | Disease of Parkinson's | SVM | 84 |
| | | KNN | 88 |
| Oh et al [24] | Disease of Parkinson's | Convolutional NN | 85 |
| Cigdem et al [25] | Disease of Parkinson's | SVM | 94 |

## 9.7 Conclusion

The achieved UCI dataset contains three voice recording replications and their continuity. In a Parkinson's disease dataset, we take 756 instances and 21 attributes with target variable. All the predictions were completed and prepared a better result by features selection techniques. After the prediction, we found improvement of all selected classifiers but Bagging Ensemble Method predicted better performance from the previous to the final experiment. In future, we can use other ensemble techniques for other large datasets and select more features selection techniques for better prediction results in machine learning.

## Acknowledgments

The author is grateful to Veer Bahadur Singh Purvanchal University Jaunpur, Uttar Pradesh, for providing financial support to work as Post-Doctoral Research Fellowship.

## References

- [1] Nemmi F, Pavy-Le Traon A, Phillips O R, Galitzky M, Meissner W G, Rascol O and Péran P 2019 A totally data-driven whole-brain multimodal pipeline for the discrimination of Parkinson’s disease, multiple system atrophy and healthy control *NeuroImage: Clin.* **23** 101858
- [2] Tejeswinee K, Shomona G J and Athilakshmi R 2017 Feature selection techniques for prediction of neuro-degenerative disorders: a case-study with Alzheimer’s and Parkinson’s disease *Procedia Comput. Sci.* **115** 188-94
- [3] Behroozi M and Sami A 2016 A multiple-classifier framework for Parkinson’s disease detection based on various vocal tests *Int. J. Telemed. App.* **2016** 6837498
- [4] Tubishat M, Idris N, Shuib L, Abushariah M A and Mirjalili S 2019 Improved salp swarm algorithm based on opposition based learning and novel local search algorithm for feature selection *Expert Syst. App.* **145** 113122
- [5] Xiao B, He N, Wang Q, Cheng Z, Jiao Y, Haacke E M, Yan F and Shi F 2019 Quantitative susceptibility mapping based hybrid feature extraction for diagnosis of Parkinson’s disease *NeuroImage: Clin.* **24** 102070
- [6] Cavallo F, Moschetti A, Esposito D, Maremmani C and Rovini E 2019 Upper limb motor pre-clinical assessment in Parkinson’s disease using machine learning *Park. Relat. Disord.* **63** 11-116
- [7] Berus L, Klancnik S, Brezocnik M and Ficko M 2019 Classifying Parkinson’s disease based on acoustic measures using artificial neural networks *Sensors.* **19**
- [8] Drotar P and Zdenek S M 2014 Comparative study of machine learning techniques for supervised classification of biomedical data *Acta Electrotechn. Inform* **14** 5-10
- [9] Sharma P, Sundaram S, Sharma M, Sharma A and Gupta D 2019 Diagnosis of Parkinson’s disease using modified grey wolf optimization *Cogn. Syst. Res.* **54** 100-15
- [10] Bellino G M, Schiaffino L, Battisti M, Guerrero J and Rosado-Muñoz A 2019 Optimization of the KNN supervised classification algorithm as a support tool for the implantation of deep brain stimulators in patients with Parkinson’s disease *Entropy.* **21** 346
- [11] Yadav D C and Pal S 2019 To generate an ensemble model for women thyroid prediction using data mining techniques *Asian Pac. J. Cancer Prev* **20** 1275-81
- [12] Yadav D C and Pal S 2019 Decision tree ensemble techniques to predict thyroid disease *Int. J. Recent Technol. Eng. (IJRTE)* **8** 8242-6
- [13] Che D, Liu Q, Rasheed K and Tao X 2011 Decision tree and ensemble learning algorithms with their applications in bioinformatics *Software Tools and Algorithms for Biological Systems* (New York: Springer) pp 191-9
- [14] Zhou Y, Howroyd J, Danicic S and Bishop J M 2015 Extending naive bayes classifier with hierarchy feature level information for record linkage *Workshop on Advanced Methodologies for Bayesian Networks* (Cham: Springer) pp 93-104
- [15] Sachin R, Sowmya V, Govind D and Soman K P 2017 Dependency of various color and intensity planes on CNN based image classification *Int. Symp. on Signal Processing and Intelligent Recognition Systems* (Cham: Springer) pp 167-77
- [16] Cutler A, Cutler D R and Stevens J R 2012 Random forests Ensemble Machine Learning (Boston, MA: Springer) pp 157–75
- [17] Bühlmann P 2012 Bagging, boosting and ensemble methods Handbook of Computational Statistics (Berlin, Heidelberg: Springer) pp 985–1022
- [18] Khoury N, Attal F, Amirat Y, Oukhellou L and Mohammed S 2019 Data-driven based approach to aid Parkinson’s disease diagnosis Sensors. 19 242
- [19] Pérez C J, Campos-Roca Y, Naranjo L and Martín J 2016 Diagnosis and tracking of Parkinson’s disease by using automatically extracted acoustic features J. Alzheimers Dis. Park 6 2161–0460
- [20] Mostafa S A, Mustapha A, Mohammed M A, Hamed R I, Arunkumar N, Ghani M K, Jaber M M and Khaleefah S H 2019 Examining multiple feature evaluation and classification methods for improving the diagnosis of Parkinson’s disease Cogn. Syst. Res. 54 90–9
- [21] Tuncer T, Dogan S and Acharya U R 2020 Automated detection of Parkinson’s disease using minimum average maximum tree singular value decomposition method with vowels Biocybern. Biomed. Eng. 40 211–20
- [22] Ricciardi C et al 2019 Using gait analysis’ parameters to classify Parkinsonism: a data mining approach Comput. Methods Programs Biomed 180 105033
- [23] Betrouni N, Delval A, Chaton L, Defebvre L, Dujardin A, Moonen A, Leentjens A F and Dujardin K 2019 Electroencephalography-based machine learning for cognitive profiling in Parkinson’s disease: preliminary results Movement Disord 34 210–7
- [24] Oh S L, Hagiwara Y, Raghavendra U, Yuvaraj R, Arunkumar N, Murugappan M and Acharya U R 2018 A deep learning approach for Parkinson’s disease diagnosis from EEG signals Neural Comput. App. 32 10927–33
- [25] Cigdem O, Beheshti I and Demirel H 2018 Effects of different covariates and contrasts on classification of Parkinson’s disease using structural MRI Comput. Biol. Med. 99 173–81
- [26] Yadav D C and Pal S 2021 Analysis of heart disease using parallel and sequential ensemble methods with feature selection techniques: heart disease prediction Int. J. Big Data Analyt. Healthcare (IJBDAH) 6 40–56
- [27] Yadav D C and Pal S 2020 Analysis of Heart Patients Using a Tree Based Ensemble Model (Bristol: IOP Publishing Ltd) pp 10-1–23
- [28] Yadav D C and Pal S 2019 Thyroid prediction using ensemble data mining techniques Int. J. Inform. Technol. https://doi.org/10.1007/s41870-019-00395-7
- [29] Yadav D C and Pal S 2020 Prediction of heart disease using feature selection and random forest ensemble method Int. J. Pharm. Res. 12 56–66
