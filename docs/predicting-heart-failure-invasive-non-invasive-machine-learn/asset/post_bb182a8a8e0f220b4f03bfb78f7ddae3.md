
Clinical examinations
Left bundle branch block or intraventricular delay, Right bundle branch block or intraventricular delay, Left ventricular Ejection fraction

Symptoms
Dyspnea, Paroxysmal atrial fibrillation,

Physical examination
Body Mass Index, Murmurs, Systolic Blood Pressure, Diastolic Blood Pressure, Heart Rate

Echocardiogram
E ratio, Interventricular Septal Thickness at end-diastole, Posterior Wall Thickness at end-diastole, Left Ventricular Mass Index, Left atrial size (average 4ch & 2ch), Left Ventricular Internal Dimension in diastole, Deceleration time, Ejection fraction, Peak_E_Value

General demographic information
Age, Gender, Device

Personal history of cardiovascular disease
Coronary Artery Disease

Drugs
Calcium Channel Blocker, Statins, Antiplatelet therapy, Renin Angiotensin Aldosterone System, Beta Blocker, Oral Anticoagulant, Lipid-Lowering drugs,

Classical cardiovascular risk factors
Hypertension

Laboratory Findings
NT-proBNP

Figure 9.4 Features for HF diagnosis.

Table 9.6 HF diagnosis classification results, unbalanced class.

| Classifier | Feature Selection | Accuracy% | Classifier | Feature Selection | Accuracy% |
|---|---|---|---|---|---|
| BN | No | 91.86 | BN | Yes | 94.00 |
| NB | No | 92.72 | NB | Yes | 94.65 |
| SVM | No | 95.50 | SVM | Yes | 95.07 |
| k-NN | No | 88.87 | k-NN | Yes | 93.36 |
| ROT | No | 96.36 | ROT | Yes | 95.07 |
| C4.5 | No | 91.43 | C4.5 | Yes | 92.51 |
| LMT | No | 94.65 | LMT | Yes | 95.50 |
| RF | No | 95.29 | RF | Yes | 94.86 |

## 9.2.2.2 Methodology

The development of the model for the NYHA class detection module consisted of three basic stages: preprocessing, feature selection, and classification. During preprocessing, features with more than (≥) 60.00% missing values were removed. Furthermore, discrete features with unbalanced distribution of values were removed. In the second step, the wrapper approach and correlation-based feature selection algorithm were used. In the classification stage, RF, LMT, C4.5, ROT, SVM, radial basis function (RBF) Network, BN, Naive Bayes (NB), and Simple CART classifiers were applied. The classifiers were combined with resampling techniques (SMOTE algorithm), when the class was unbalanced. Resampling was performed only during the training of the model and not during the test for avoiding bias of classification results.

## 9.2.2.3 Results for HF Severity Estimation

The features removed after applying the preprocessing step are depicted in Figure 9.6. The data set consisted of 92 patients’ data. The model was trained to detect NYHA class II, NYHA class III, and NYHA class IV, since HF patients belonging only to one of these classes participated in the project. Different combinations of features were employed and the best results are presented in Table 9.8.

The RF classifier with 95% accuracy using the optimal set of features was selected. The features that remained following the feature selection were those shown in Figure 9.7.

Table 9.7 HF diagnosis classification results, balanced class

| Classifier | Feature Selection | Accuracy% | Classifier | Feature Selection | Accuracy% |
|---|---|---|---|---|---|
| BN | No | 92.82 | BN | Yes | 93.78 |
| NB | No | 92.34 | NB | Yes | 94.50 |
| SVM | No | 94.98 | SVM | Yes | 94.74 |
| k-NN | No | 88.52 | k-NN | Yes | 93.30 |
| ROT | No | 95.22 | ROT | Yes | 95.22 |
| C4.5 | No | 93.78 | C4.5 | Yes | 92.82 |
| LMT | No | 95.22 | LMT | Yes | 94.98 |
| RF | No | 94.98 | RF | Yes | 94.50 |

![](img/721c7a2c71f4dc63a8585e2ef46838f7_232_0.png)

Figure 9.5 Data description for HF severity estimation and adverse events prediction.

## 9.2.2.4 Results for the Prediction of Adverse Events

The adverse events prediction model was built using the data from 82 patients. The results are presented in Table 9.9.

The classifier that produced the best results (in terms of accuracy) using the optimal set of features was selected. The classifier, according to Table 9.9, is ROT with 89.00% accuracy. The optimal set of features is the set of features remaining after the feature selection step (Figure 9.8).

![](img/721c7a2c71f4dc63a8585e2ef46838f7_232_1.png)

Figure 9.6 Removed features after the application of the preprocessing step.

**Table 9.8 Results of the NYHA class detection model.**

| | Accuracy% | Classifier |
|---|---|---|
| Features only from sensors | 86.00 | RF |
| Features only from biomarkers | 75.00 | RF |
| Features from sensors and biomarkers | 81.00 | RF |
| All features without biomarkers | 89.00 | RF |
| All features without sensors | 91.00 | RF |
| Optimal set of features | 95.00 | RF |

![](img/721c7a2c71f4dc63a8585e2ef46838f7_233_0.png)

Figure 9.7 Optimal set of features for severity estimation.

**Table 9.9 Results of the adverse events prediction model.**

| | Accuracy% | Classifier |
|---|---|---|
| Features only from sensors | 78.00 | RBF |
| Features only from biomarkers | 81.00 | LMT |
| Features from sensors and biomarkers | 77.00 | ROT |
| All features without biomarkers | 80.00 | ROT |
| All features without sensors | 83.00 | ROT |
| Optimal set of features | 89.00 | ROT |

![](img/721c7a2c71f4dc63a8585e2ef46838f7_233_1.png)

Figure 9.8 Optimal set of features for adverse events prediction.

## 9.3 Conclusions

In this chapter, after an introduction to HF, and HF classification, evaluation, and diagnosis methods we highlighted the importance and necessity of using ML techniques in medicine. Due to the increased incidence and the large financial costs required to diagnose HF, the diagnosis and treatment of the disease are extremely important.

An extensive review of the state of the art in the applications of ML in the management of HF was demonstrated, utilizing several types of features, HRV measurements, heart sound characteristics, ECG recorded signals, and EHR features – and studies using the Cleveland heart disease database or the EFFECT study data set.

As presented in the comparison Table 9.1 different approaches in the literature provide methods for detecting and diagnosing HF, acute HF, or the various types of HF (HFpEF, HFmrEF, HFrEF) based on several methods, with accuracies ranging from 72.41 to 99.93%. Moreover, other studies focus on ML applications for severity estimation of HF. Most of the studies classify patients according to NYHA classification with accuracies ranging from 71.00% to 97.00%. HF imposes a significant burden on both patients and healthcare institutions and thus much effort has been given to developing methods to predict adverse events among patients with HF or acute HF. Studies address this problem by predicting mortality or readmission over various time periods.

In the last part of the chapter, two novel methods of HF diagnosis, severity estimation, and adverse events prediction (mortality or rehospitalization) were presented. The models are based on ML approaches and consist of data cleaning, feature selection, class balancing, and classification steps. The results are high for all the addressed problems, while the innovation of the studies derives from the multiple data types that are utilized, especially the biomarkers and the data from the biosensors. Since these studies are based on the Kardiatool and Hearten projects, the demonstrated method for the HF diagnosis is integrated in a diagnostic tool in Kardiatool. In addition, the HF severity estimation and the adverse events prediction are embedded in the Hearten Knowledge Management System, which offers decision support in HF management. Through these tools, healthcare professionals can receive information related to a patient, detect the presence of HF, estimate the severity of a patient’s condition, and predict the risk for adverse events; they can therefore adapt patient management accordingly.

## References

- 1 Yancy, C., et al. (2013). 2013 ACCF/AHA guideline for the management of heart failure: executive summary. *Circulation* 128 (16): 1810–1852.

- 2 Dassanayaka, S. and Steven, J.P. (2015). Recent Developments in Heart Failure. *Circulation Research* 117 (7): 58–63.

- 3 Heusch, G. (2016). Myocardial Ischemia. *Circulation Research* 119 (2): 194–196.

- 4 Ponikowski, P., et al. (2019). Heart rate and blood pressure monitoring in heart failure. *European Heart Journal Supplements: Journal of the European Society of Cardiology* 21 (Suppl. M): 13–16.
