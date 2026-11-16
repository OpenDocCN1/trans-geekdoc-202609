
| Study | Target | Method | Features | Data Set | Evaluation Measures |
|---|---|---|---|---|---|
| Zhang et al. 2013 | Prediction of death or risk or hospitalization due to worsening HF at 12 months | Decision trees, LR | Demographics, physical examination, laboratory findings, medical history, quality of life, EuroQoL | TEN-HMS study 284 patients for training 160 patients for validation | Accuracy 89.20% for mortality prediction with decision trees Accuracy 79.70% for adverse events prediction with decision trees |
| Tripoli et al. 2017 | Prediction of adverse events in patients with HF | ROT | Breath and saliva biomarkers | 27 patients | 77% accuracy, sensitivity, and specificity |
| Awan et al. 2019 | Prediction of 1-month readmission or death rate for HF patients | MLP | Demographics, admission characteristics, medical history visits to emergency departments, medication, healthcare services out of hospital, death. | 10,757 HF patients over 65 years old 23.6% were readmitted or died within 1 month of hospital discharge | AUC 62.00% Sensitivity 48.00% Specificity 70.00% |
| Angraal et al. 2020 | Prediction of adverse events in patients with HFpEF through 3 years of observation | LR with a forward selection of variables, LR with a LASSO regularization for variable selection, RF, gradient descent boosting, SVM | Demographics, laboratory findings, ECG features, symptoms and quality of life score | 1767 patients 50 years of age or older from the TOPCAT trial | RF classifier achieved the best result: 0.72 C-statistic for predicting mortality 0.76 C-statistic for hospitalization |
| Beezy 2020 | Prediction of 1-month or 6-month readmission or all-cause mortality in patients with acute or chronic HF | Extreme gradient boosting | Socioeconomic features, clinical history, laboratory, and radiologic findings, ECG and invasive coronary angiographic parameters | 3774 patients with acute or chronic HF. 3160 patients without planned death/readmission within 1 month after discharge. 614 patients with unplanned death/readmission within 1 month after discharge. | AUC 75.60% |
| Yang et al. 2020 | Prediction of all-cause readmission or death at 1 month and 12 months for HF patients over 65 years of age | A Cox regression model was used to identify factors for the prediction of readmission or death at 1 month and 12 months. A nomogram was developed with bootstrap validation. RF, LR, SVM, NN | Demographics, echocardiographic and biochemical data, comorbidities, medications | 854 patients. 165 with 1-month readmission or death. 212 with 12-month readmission or death. 477 no events. | The C-index of the 1-month and 12-month prediction model was 77.80% and 73.80% respectively |
| Zahavi et al. 2020 | Prediction of 1-month and 12-month readmission or mortality | EHR data | EHR data | 3838 patients | 1-month readmission: RF AUC; 12-month readmission: RF AUC; 1-month mortality: RF AUC; 12-month mortality: RF AUC |

Angraal et al. in 2020 [97] utilized various classification algorithms to train the model for predicting the mortality and HF hospitalization through 3 years of follow-up in HFpEF patients. The RF classifier achieved the best result with a mean C-statistic of 0.72 for predicting mortality (Brier score: 0.17), and 0.76 for HF hospitalization (Brier score: 0.19). They used data from 1767 patients from the TOPCAT trial (Treatment of Preserved Cardiac Function Heart Failure with an Aldosterone Antagonist) and more specifically their data set consisted of demographic features, laboratory findings, electrocardiography data, symptoms, and quality of life score.

Also in 2020, Yang et al. [98] developed a method to predict all-cause readmission or mortality for HF patients over 65 years of age. The Cox regression model was used to identify the predictive features for adverse events at 1 month and 12 months. A nomogram was developed with bootstrap validation. The C-index of the 1-month and 12-month prediction model was 0.778 and 0.738, respectively. Zahavi et al. [99] compared various ML models (RF, LR, SVM, and NN) for 1-month and 12-month prediction of readmission and mortality. Their models were trained on 3838 patients during hospitalization for HF with 182 variables collected from EHR. RF achieved the best results in terms of AUC for all predictions.

Beezy et al. [100] also analyzed EHR data to predict the unplanned adverse events due to HF using a prediction window of 1 month or 6 months. In a total of 3774 subjects with acute or chronic HF, they implemented extreme gradient boosting with AUC 75.60%.

## 9.2 Two Prominent Applications

In this second part of the chapter, we demonstrate the results of two innovative studies: the first for HF diagnosis, and the second for HF severity estimation based on NYHA classification and the prediction of adverse events. The results for the HF diagnosis are part of the Kardiatool project [101], and the results for the severity estimation and the prediction of adverse events are part of the Hearten project [102].

### 9.2.1 HF Diagnosis

#### 9.2.1.1 The Data Set

The data set for HF diagnosis consisted of 467 subjects (258 used as control subjects, 180 subjects with chronic HF, and 29 with acute HF). The HF diagnosis classification problem is defined as classifying the 258 control subjects versus the 209 HF subjects.

Data was provided by University College Dublin, National University of Ireland (409 patients), and the 2nd Department of Cardiology of the University Hospital of Ioannina (58 patients) as part of the Kardiatool project [101].

For each patient, data from different categories were recorded. More specifically, they were grouped into the following categories: general demographic information, personal history of cardiovascular disease, drugs, classical cardiovascular risk factors, laboratory findings, clinical examinations, symptoms, physical examination, and echocardiographic features (Figure 9.3).

### Clinical examinations

Left bundle branch block or intraventricular delay. Right bundle branch block or intraventricular delay, Left ventricular Ejection fraction

### Symptoms

Dyspnea, Orthopnea, Paroxysmal atrial fibrillation, NYHA class

### Physical examination

Body Mass Index. Murmurs. Systolic Blood Pressure, Diastolic Blood Pressure, Heart Rate

### Echocardiogram

E ratio, Interventricular Septal Thickness at end-diastole, Posterior Wall Thickness at end-diastole Left Ventricular Mass Index. Left atrial size (average 4ch & 2ch). Early Filling (E wave)/Early Diastolic Mitral Annular Velocity (E'), Left Ventricular Internal Dimension in diastole, Deceleration time, Early Filling (E wave)/Late diastolic filling (A wave) ratio, Ejection fraction, Peak E Value MR grade, Left Ventricular End Diastolic Dimension, HFpEF, HFrEF, HFmrEF

### General demographic information

Age, Gender, Device

### Personal history of cardiovascular disease

Myocardial Infarction, Coronary Artery Disease, Angina

### Drugs

Mineralocorticoid Receptor Antagonists, Loop diuretic, Thiazide diuretic, Calcium Channel Blocker, Statins, Antiplatelet therapy, Renin Angiotensin Aldosterone System, Beta Blocker, Oral Anticoagulant, Lipid-Lowering drugs, Angiotensin-converting enzyme inhibitors, Angiotensin Receptor Blocker, Alpha blocker, Digoxin, Eplerenone Warfarin, Plavix Clopidogrel, Aspirin, Nitrate, Diabetes drugs

### Classical cardiovascular risk factors

Hypertension, Diabetes Mellitus

### Laboratory Findings

NT-proBNP

Figure 9.3 Data description for HF diagnosis.

### 9.2.1.2 Methodology

The proposed methodology consisted of three basic stages: preprocessing, feature selection, and classification. At the preprocessing stage features with more than (≥) 50% missing values and discrete features with unbalanced distribution of values were removed. Next, outliers and typos (e.g., 4.5 being recorded instead of 4.5) per feature were detected and corrected. A correlation-based feature selection method was used to assess the predictive ability of feature subsets and the degree of redundancy among them, preferring sets of features that were highly correlated with the class but with low intercorrelation [103]. In the classification stage, C4.5, RF, ROT, NB, k-NN, SVM, logistic model trees (LMT), and Bayes Network (BN) classifiers were applied. In order to achieve class balancing, the undersampling method was applied to the data set. The undersampling method is quite common for dealing with this problem [104]. It produces a random sub-sample with a given spread between class frequencies. The maximum spread between the rarest and most common class is specified. In our case, a random undersample of the majority class was followed, so that all classes have the same number of instances. The 10-fold cross-validation was applied in testing.

### 9.2.1.3 Results

After removing features with ≥ 50% missing values and deleting discrete features with unbalanced distribution of values, there were 30 remaining features (Figure 9.4). We also excluded from the data set NYHA classification that was recorded in all patients, since that would indicate a patient’s condition. Finally, the classification of HF phenotype (HFpEF, HFrEF, HFmrEF) did not fit in our analysis since the models would be used for HF diagnosis in previously undiagnosed patients.

The results for the HF diagnosis problem, for the unbalanced class, are depicted in Table 9.6.

The results for HF diagnosis problem, for the balanced class, are depicted in Table 9.7.

The ROT classifier for the unbalanced class, without feature selection, gives the best result with an accuracy of 96.36%, sensitivity 96.50%, and specificity 96.20%.

## 9.2.2 Severity Estimation and Adverse Events Prediction

### 9.2.2.1 The Data Set

For both the severity estimation problem and the adverse event prediction, the data were collected retrospectively by three different clinical centers: Universita Di Pisa, Servicio Andaluz de Salud, and the 2nd Department of Cardiology of the University Hospital of Ioannina, as part of the HEARTEN project [102].

The recorded data can be grouped in the following categories: general information, medical condition, drugs, clinical examination, score information, biological data, allergies and drugs side-effects, sensor data, and biosensor data. More specifically, during hospitalization, for each patient the data shown in Figure 9.5 were collected.

Regarding the data retrieved from the sensor, the clinicians had to monitor the patient (starting from the day of admission) using a sensor device for 20 minutes every other day and at discharge.
