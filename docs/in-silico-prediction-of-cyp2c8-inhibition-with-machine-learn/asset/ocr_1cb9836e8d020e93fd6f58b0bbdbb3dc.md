morphism. 14 For example, the combination of the inhibitor gemfibrozil and the substrate civerazation of CYP2C8 has caused serious adverse drug reactions. 15 Therefore, rapid identification of CYP2C8 inhibition is of great significance for guiding the design and development of new drugs. At present, however, no prediction models have been reported for CYP2C8 inhibition.

In this study, we developed in silico models for classifying CYP2C8 inhibitors and noninhibitors by multiple machine-learning methods. The robustness of the built models was evaluated by the test and external validation sets. On the basis of the Euclidean distance method, the applicability domain was defined to exclude some extreme compounds. In addition, the differences in structural characteristics between inhibitors and noninhibitors were detected by information gain and substructure frequency analysis to derive privileged substructures accounting for the CYP2C8 inhibition.

# ## 2. MATERIALS AND METHODS

# ### 2.1. Data Collection and Preparation

In this study, we collected the data sets from the PubChem bioassay database 16 and two publications. 14,17 Compared to other literature reports, the data provided by these two publications is more comprehensive, basically covering the currently known CYP2C8 inhibitors.

The data sets used for developing classification models were manually collected from the PubChem bioassay database 16 and the literature published in 2005. 17 For the data from PubChem, compounds with activity ≤ 50 μM or explicitly reported as active by ChemBL are flagged as active in the CYP2C8 bioassay representations. The active type used for each compound is one of IC 50 , INH, and K I . From the literature from 2005, 17 209 drugs at 30 μM were examined for the inhibition of CYP2C8. Among them, 48 compounds exhibited greater than 50% inhibition and were further evaluated for measurement of IC 50 . The results showed that the IC 50 values of 6 drugs are less than 1 μM, 17 drugs are between 1 and 10 μM, and 25 drugs are in the range from 10 to 40 μM. The compound activity criteria in the literature and in PubChem are similar. Therefore, the data from PubChem and the literature, we regarded the compounds labeled "active" as CYP2C8 inhibitors and "inactive" as noninhibitors. The chemicals without compound values or literature support were deleted. The 48 compounds collected from the literature 17 were categorized into inhibitors and noninhibitors. All molecules were converted into simplified molecular-input line-entry system (SMILES) strings. In order to get high-quality data, the two data sets were carefully preprocessed by the following steps: (1) nonganic substances were removed, (2) salts were converted to the corresponding bases or acids, and (3) duplicate chemical structures were removed. Then, the CYP2C8 inhibitors were marked as "1" and noninhibitors as "0". Finally, the pretreated data sets were randomly divided into a training set and a test set with a ratio of 8:2 by an in-house python script.

To assess the generalization ability of the built models, an external validation set was constructed from different sources, including the DrugBank database, 18 the literature by Backman et al., 15 and the Indiana University School of Medicine ( https://drug-interactions. medicine.iu.edu/Main/Table.aspx ). Similar to the data processing for PubChem, the drugs obtained from the DrugBank without a literature source were excluded. The remaining CYP2C8 inhibitors were considered as the positive data. In addition, six CYP2C8 inhibitors collected from the Indiana University School of Medicine data set were added to the positive data set. The compounds with IC 50 > 100 μM reported in the literature were regarded as the negative data. For the external validation set, the same data preprocessing procedure as in the training and test sets was applied and the duplicate data in the training or test sets were excluded.

The diversity and quality of the data set are crucial for building a highly robust model. 6,13 In our work, we exploited the chemical space distribution and Tanimoto average similarity index 20 to evaluate the chemical diversity of the data sets. The chemical space distribution is defined as a two-dimensional space distribution map of the molecular weight (MW) and the lip/water partition coefficient (ALogP), which were calculated by the Pipeline Pilot 2017 R2 software. 19 The Tanimoto similarity index, having a value between 0 and 1, was calculated using the python script. The smaller the value, the less similar the structures of two compounds.

# ### 2.2. Molecular Representation

Molecular fingerprints were employed to represent the molecules in the above data sets. A molecule can be translated into a binary string of structural keys and a index for input to machine-learning models by fingerprints. Nine types of molecular fingerprints were calculated by the PADEL-Descriptor software tool, 21 including the Atom Pairs 2D fingerprint (AP2D, 780 bits), Estate fingerprint (Est, 79 bits), Extended fingerprint (Ext, 512 bits), Fingerprint-FP (FP, 1024 bits), Graph only fingerprint (Gra, 1024 bits), Klekota-Roth fingerprint (KR, 4860 bits), MACCS fingerprint (Mac, 166 bits), Pubchem fingerprint (Pub, 881 bits), and Substructure fingerprint (Sub, 307 bits). The detailed descriptions of these fingerprints can be found in the original literature. 1,2,5

# ### 2.3. Construction of the Models

In this study, five widely used machine-learning algorithms were employed to build the predictive models of CYP2C8 inhibitors and noninhibitors, including support vector machine (SVM), 23 random forest (RF), 24 k-nearest neighbor (KNN), 25 neural network (NN), 26 and logistic regression (LR). 27 All algorithms were implemented using the scikit-learn package version 0.21. 4.

Since several machine-learning algorithms were heavily affected by the parameter settings, k-fold cross validation was exploited to traverse all of the data in a training set. First, the training set was divided into k subsets, k − 1 subsets were first used to build the models, and the remaining subset was applied for model validation. This process was repeated k times. Then a grid search algorithm was chosen to select an optimal parameter for the machine-learning method. In this study, the value of k was set to 10. The detailed parameter settings of the top five models obtained by cross validation are shown in Table S1.

# ### 2.4. Performance Evaluation of Models

In this study, the 10-fold cross validation of the training set was employed to examine the robustness of the built models. The test set was applied to further evaluate the predictive power, and the external validation set from different sources was used to assess the models generalization ability. Several indicators were calculated to evaluate the quality of the models intuitively. In binary classification models, data sets are generally divided into two categories, positive and negative. True positive (TP) means that CYP2C8 inhibitors are correctly predicted to be positive. True negative (TN) indicates that CYP2C8 noninhibitors are accurately predicted to be negative. False positive (FP) means that CYP2C8 noninhibitors are incorrectly predicted as inhibitors, while false negative (FN) infers that CYP2C8 inhibitors are incorrectly predicted as noninhibitors. 28 On the basis of these definitions, sensitivity (SP), specificity (SP), Mathews' correlation coefficient (MCC), and classification accuracy (CA) were calculated using the following formula

```
$$ SE = \frac{TP}{TP + FN} $$ (1)
```

```
$$ SP = \frac{TN}{TN + FP} $$ (2)
```

```
$$ CA = \frac{TP + TN}{TP + TN + FP + FN} $$ (3)
```

```
$$ MCC = \frac{(TP \times TN - FP \times FN)}{\sqrt{(TP + FP)(TP + FN)(TN + FP)(TN + FN)}} $$ (4)
```

where CA represents the total proportion of the number of accurately classified chemicals to all positive and negative data. SE and SP are two commonly used classified performance metrics. SE is the predictive accuracy of CYP2C8 inhibitors. SP is the percentage of