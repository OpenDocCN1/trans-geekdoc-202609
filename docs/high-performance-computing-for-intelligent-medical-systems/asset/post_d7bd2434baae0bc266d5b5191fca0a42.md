
If dopamine production is less in the body then it indicates some symptoms in the human body such as:

- minor tremors felt in hands, legs and head;
- minor stiffness felt in limbs and trunk;
- minor slowness seen in movement;
- seen impaired balance and coordination;
- seen depression and difficulty in speaking;
- seen disruptions in sleeping.

It is critical to correctly diagnose and declare Parkinson’s disease. If dopamine production stops in the body then Parkinson’s disease will be at a high level.

## 9.2 Related work

Some researchers have done work on Parkinson’s disease by different features selection techniques: GA, PSO, correlation based, filtered based etc [1–5].

Nemmi et al. discussed two Parkinsonian syndromes identified by MRI protocol and used pipeline combined with several feature selection and finally found best accuracy (94%). The pipeline evaluated more relative important features of Parkinson’s disease with a different model set. The pipeline performed a good balance between classification accuracy and relative important features [1].

Tejeswinee et al. discussed a neuro-degenerative data set by data mining technique. They found a correlation based feature subset selection method gave the highest accuracy (94%) by support vector machine (SVM) and used different classifiers on 111 instances of a Parkinson’s dataset in which they found 74 genes unique and 37 different genes different [2].

Behroozi et al. discussed Parkinson’s disease. They used multiple classifier frameworks KNN, SVM Linear Kernel, SVM (RBF), Naïve Bayes and Discriminant Analysis for speech dataset. They used filter based feature selection and found accuracy K-nearest neighbor (K-NN) (K = 7) (77%), SVM Linear Kernel (85%), radial based functional (RBF) (87%), Naïve Bayes (80%) and Discriminant Analysis (82%)[3].

Tubishat M et al. analyzed algorithms for features selection. They used ‘Salp Swarm Algorithm, Classification, Feature selection Optimization, Machine Learning Algorithm’ and ‘Opposition Based Learning’ on 18 different datasets. They finally selected the optimal subset in wrapper mode and solved the feature selection problem [4].

Xiao B et al. predicted hybrid features of Parkinson’s disease which was based on QSM, SN and CNN. They observed a dataset from MRI image biomarkers and evaluated area under curve (AUC), sensitivity, specificity and accuracy by NF, convolutional neural networks (CNN) and SVM. SVM evaluated highest accuracy (96%) after features selection [5].

Some authors have predicted on the basis of machine learning algorithms such as: SVM, Naïve Bayes, Random Forest’ etc [6–10].

Cavallo et al. analyzed a feature array as the most significant to discriminate among the different classes and different groups of classification. They compared SVM, Random Forest and Naïve Bayes by various datasets. Finally, they achieved highest accuracy of SVM (97%) [6].

Berus et al. analyzed 26 different voice samples of Parkinson's patients. They used 'multiple feed-forward artificial neural networks (ANNs) in the prediction of Parkinson's disease of tested individuals. Finally, they found highest accuracy (86%) of neural network [7].

Drotar and Zdenek, discussed identification of diseases or differential diagnosis of various types of disorders. They used machine learning algorithms SVM, RF, AdaBoost, Deep Belief Networks, K-NN, Naïve Bayes, LDA and Perceptron. They found better framework for classification and calculated accuracy. Finally, they found classification accuracy of SVM (94%), RF (97%), AdaBoost (93%), Deep Belief Networks (76%), K-NN (96%), Naïve Bayes (96%), LDA (91%) and Perceptron (98%) [8].

Sharma et al. predicted Parkinson's disease for identification of symptoms. They presented the Modified Grey Wolf Optimization algorithm for symptom identification of premature stages of Parkinson's disease. They used datasets of voice, handwriting and speech. They used RF, KNN and Decision Tree for better prediction and by measured (94%) accuracy by forward algorithm [9].

Bellino et al. discussed the relationship between gait parameters and falls incidence. They predicted the risk among older adults of approximately 105 adults older than 65. The entire functional and fundamental assessment fall event was recorded in diaries. J48 algorithm was applied for fall in future prediction with (84%) accuracy [10].

Some authors used ensemble methods for better prediction. They added various algorithms in Bagging, Stacking, Boosting etc ensemble methods [11, 12].

Yadav and Pal discussed thyroid patients and their predictions. They used a thyroid symptoms based dataset and generated an ensemble technique for prediction. They generated techniques (Stacking) and (Bagging + Boosting) applied, and after evaluation they found (97%) ROC of stacking [11].

Yadav and Pal analyzed hormones disorders in thyroid disease. They used J48, Hoeffding and RF for better prediction. Selected machine learning algorithms trained input samples in various forms then found better classification accuracy of the ensemble method [12].

## 9.3 Methodology

The proposed methodology is divided into three main parts:

- 1. Predict Parkinson's disease using different machine learning classifiers and analyze the obtained result.
- 2. Select important features from the dataset with high methods Chi square, Extra Tree and Heatmap prepared dataset with high importance.
- 3. Apply once again selected machine learning classifiers on the prepared dataset (after feature selection) comparing the results from previous predictions.

### 9.3.1 Data description

The selected dataset contains three voice recording replications of the continued (sustained). The number of instances in the whole dataset is 756 and available numbers of attributes are 21. All the dataset depends upon replication consideration. The examination of dataset depends upon matching a combination of classical concepts of some subject voice recordings. It is a critical problem to identify more similar features from different subjects (table 9.1).

In most of the studies, we find Parkinson's disease identifies by many symptoms.

In this chapter we select and predict speech based dataset categories as:

- 1. Contain the repetition of one term;
- 2. Consist of different spoken terms.

Dataset is accessible from the UCI machine learning repository. We select a Parkinson's speech dataset with multiple types of sound recording for prediction.

Table 9.1. Parkinson's dataset features and description.

| Feature name | Description | Measure |
|---|---|---|
| ID | Subjects are required for identification | |
| Recording | How many times recording is available | |
| Status | 0 = Healthy, 1 = Parkinson's disease | |
| Gender | 0 = Man, 1 = Woman | |
| RPDE | Recurrence period density entropy in measurement | |
| DFA | Signal fractal scaling exponent of detrended fluctuation analysis in measurement | |
| PPE | Pitch (area of play) period entropy in measurement | |
| GNE | Glottal-to-noise excitation ratio in measurement | |
| Jitter | ‘Local, Absolute, Rap, PPQ5 and DDP’ | Frequency |
| Pulses | ‘Number of pulses, Period: Number, Mean and Standard Deviation’ | Pitch Local Perturbation |
| Shimmer | ‘Local (Shim_loc), dB (Shim_dB), 3-point (Shim_APQ3), 5-point (Shim_APQ5), 11-point (Shim_APQ11)’. | Amplitude perturbation quotient |
| Harmonic-to-noise ratio | 0–500 Hz (HNR05), 0–1500 Hz (HNR15), 0–2500 Hz (HNR25), 0–3500 Hz (HNR35), 0–3800 Hz (HNR38). | Frequency band |
| Mel frequency cepstral coefficient | 0–12 (MFCC0, MFCC1,..., MFCC12) and (Delta0, Delta1,..., Delta12). | MFCC-based spectral and their derivatives |

Some features focused on only identification, recording, status and gender of particular diseases of Parkinson's. Some other features measure signal scaling, area of play, noise and density entropy.

Six features related to all words and voiced features of frequency. The feature Glottal isolates the voiced folds vibrations during large variation in vocal folds. Jitter measures cycle-to-cycle variations in frequency and Shimmer measures the variations of peak amplitude decibels.

Both Jitter and Shimmer are defined by different points mentioned in the above table.

### 9.3.2 Whisker plotting

We used whisker plot for Parkinson's data because it easily represents variables location with spread at a glance (figure 9.1). It is required to know the summary about all features of the Parkinson's dataset. Whisker plot checks outlier data (normal/non-normal).

### 9.3.3 Histogram plotting

We used a histogram for frequency measurement of data in graphical form (figure 9.2). In the histogram is found the distribution of data with data summary in bar. Each bar frequency is represented along with each feature in the dataset.

## 9.4 Algorithms description

In this chapter we use different data mining tree algorithms with ensemble method for better prediction.

### 9.4.1 Decision tree

Decision tree is used for prediction of variables of many medical datasets. It is focused on dependable variables or target variable (figure 9.3). It is basically used for

![](img/75406d5bb714dfd3e68fbbc717bd8f67_224_0.png)

Figure 9.1. Representation of Parkinson's dataset by Whisker plot.
