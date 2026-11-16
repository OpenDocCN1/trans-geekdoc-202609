
- **Personal info**
  - Age.
  - Sex
  - Smoking/no smoking
  - ... etc.

- **Omics data**
  - Genomics
  - Transcriptomics
  - Metabolomics
  - Proteomics
  - Lipidomics
  - ... etc.

- **Clinical data**
  - Wearable imaging
  - ECG
  - EHR
  - ... etc.

Data collection

Data preprocessing

Feature extraction

- Supervised
- Unsupervised
- Semi-supervised
- Reinforcement learning

ML model training

Classification

- Prediction of HF
- Type of HF
- Readmission, mortality risk

Figure 8.1 Overall architecture of HF diagnosis/prediction using ML models.

(ICD), medication, lab orders, etc. can be represented as a sequence of categorical variables over time, when each patient visit is an element of this sequence. Hence, there is similarity between EHR data representation and natural language representation where the text is represented as a sequence of words or sentences. Therefore, ML models developed in the area of language understanding can readily be applied to EHR data.

In Rasmy et al. [47], a large EHR data set is used for the predictive modeling of HF onset risk. The data set included more than 150,000 HF patients and over 1,000,000 controls from about 400 hospitals. Patients are defined based on the two criteria: (i) at least three encounters with related HF had to occur within 12 months; (ii) the first HF diagnosis occurred when they were over 50 years old. For each case, 10 matched controls are identified based on the primary care hospital, sex, and age. Furthermore, the time span of the control and case data were matched by ensuring that the first visit of the controls were within one year of the first visit of the matched case and there was at least one visit a month before or any time after the diagnosis date of the matched case. Each visit is represented by the medical codes related to diagnoses, medication, and surgical procedure data. For diagnoses and surgical procedures, ICD-9 and ICD-10 were used. For medication information, the National Drug Codes (NDC) were used.

A known deep learning model called RETAIN (reverse time attention model) has been previously used for HF prediction [48] based on a relatively small data set compared with the one used in Rasmy et al. [47]. The model was designed to predict the diagnosis of HF at the next visit. Hence at each visit, the model gives a probability score for the patient having an HF. RETAIN is a two-branch neural attention model on top of an embedding layer. It takes as input the sequence of recorded events in the patient's EHR. First, an embedding layer is responsible for reducing the dimensionality of the input representation and converting the multi-hot vector unit to a real-valued smaller size vector representation. Then two gated recurrent unit (GRU) RNNs are derived in parallel. The first RNN (RNNα) is responsible for deriving attention weights of the visits, which is a vector α where length is the number of visits. Therefore, it is possible to infer which visits are most important for predicting HF. The second RNN (RNNβ) is used to derive the clinical code level attention. Hence, it is possible to know which event (diagnosis, medication, surgical procedure) is most relevant for the prediction of HF. These two RNNs can be applied to new patients not seen during model training. They provide good interpretability properties of the model.

In order to compare the RETAIN model with classical ML approaches, a baseline logistic regression model using an aggregated feature vector on the temporal dimension was adapted. Each dimension represents the count of each code event in the subject's history. L1 and L2 regularization terms were evaluated in the experimental analysis. Also, the embedding from RETAIN was used as input to train the logistic regression. EHRs from multiple hospitals were gathered for the Cerner Health Facts database. For each hospital the cohort was divided into training, validation, and test sets with a ratio of 7:1:2. A regularized logistic regression model was used as a baseline model. The feature vector for the baseline was the codes' occurrence of the aggregated data on the temporal dimension. The RETAIN model achieved an AUC of 82% compared with 79% for logistic regression. The generalizability of the model across hospitals was performed by training RETAIN using a single hospital data and evaluating the model on other hospital data. This led to a 3.6% reduction in AUC. The combination of deep learning and EHR is a promising future direction for building accurate predictive models for clinical decision support tools for HF.

## 8.8 ML Techniques for Predicting HF

Predicting of HF risks using ML is becoming one of the top priorities for medical doctors and physicians. Specifically, when ML is applied to different kinds of medical records, it helps in predicting survival in patients who have HF symptoms, and detecting the main clinical features leading to HF. However, much work is still needed to improve the accuracy of HF predictors as most of them have failed to reach high performance levels [49, 50]. In addition to the traditional ML models, deep learning algorithms are gaining much popularity because of their supremacy in terms of performance compared with conventional models, especially if they are trained with huge amounts of data, and their ability to improve on human specialists’ performance.

To predict HF risks, data sets including medical records of HF patients are usually used for training the ML algorithms. The process is similar to the diagnosis and detection of HF already explained in Figure 8.1, but with some differences regarding the types of input data that need to be fed into the ML models and the output to be produced. Therefore, the objectives are also different, as they are more oriented to predicting HF mortality and severity risks, HF destabilizations, HF relapses, and/or HF readmission [37, 51]. In this context, in addition to the EHR data (e.g. demographics, admission characteristics, medical history, visits to emergency departments, history of medication use, and healthcare services out of hospital), telemonitoring data can be utilized for identifying and predicting different HF risks (e.g. readmission risks) [52]. Moreover, by combining EHR data with tele-HF data and wearable sensor data the accuracy of predicting HF risks can be improved as discussed in Mortazavi et al. [53].

### 8.8.1 Prediction of In-Hospital Mortality

J. Kwon et al. have developed an ML model to predict in-hospital mortality for a patient with heart conditions based on echocardiography [54]. The cohort was based on a multicenter retrospective data set. The data from hospital A was used to train a deep learning model while data from hospital B was used for validation. The study size was 25,776 patients, with 1026 registered in-hospital mortalities. Predictor variables were extracted from the echocardiography first raw text reports. First extracted were 11 continuous variables, such as age, weight, height, left or right ventricular systolic dysfunction (LVSD/ RVSD), left atrial dimension (LAD), etc. First, these continuous variables were zero-mean and standard-deviation-one normalized. Then 54 categorical variables were parsed from the report. These variables are counts on the occurrence of specific keywords in the raw text. For example, mitral valve description gathers 10 variables for keywords such as stenosis [5 possible values: absent/trace/mild/moderate/severe], calcification [2 possible values: Y/N], prosthesis [2 possible values: Y/N], etc. The input feature vector formed by the concatenation of the continuous and categorical variables were passed to the deep learning model for training. The model consists of three dense layers with batch normalization and dropout. Comparison with logistic regression and random forests models were conducted, and additional validation of results for coronary heart disease and HF subgroups were conducted in the experimental analysis. The test set included 3840 patients from hospital A and 1560 patients from hospital B. The used performance metrics are the area under ROC curve (AUROC) and the area under precision recall curve (AUPRC). Based on the hospital A held-out set, the deep learning model (AUROC: 0.912, AUPRC: 0.143) outperformed RFs (AUROC: 0.893, AUPRC: 0.134) and logistic regression (AUROC:0.841, AUPRC: 0.205) in the prediction of in-hospital mortality. For the hospital B test set, the deep learning model (AUROC: 0.898, AUPRC: 0.280) outperformed RFs (AUROC: 0.848, AUPRC: 0.186) and logistic regression (AUROC: 0.841, AUPRC: 0.20) in the prediction of in-hospital mortality. The previous results were based on the general cohort of the heart disease cohort. For the subgroup of HF patients, the chosen baselines were the Meta-Analysis Global Group in Chronic Heart Failure deep learning model (MAGGIC) and the Get With The Guidelines-Heart Failure (GWTG-HF) program [55, 56]. The deep learning model (AUROC: 0.913, AUPRC: 0.351) significantly outperformed both MAGGIC (AUROC: 0.806, AUPRC: 0.154) and GWTG-HF (AUROC: 0.783, AUPRC: 0.285).

### 8.8.2 Prediction of 30-Day HF Readmission

HF readmission is a major healthcare problem. Patient deterioration is correlated with 30-day readmission and significant costs are attached to it. The early prediction of readmission risk can contribute to the reduction of this problem. Scheduling early follow-up based on this predictive model can play an important role in preventing patient readmission and health complications. J. Frizzel et al. proposed a comparison of ML approaches for this task [57, 58]. The following models were compared: tree-augmented Naive Bayesian network (TAN), an RF algorithm, a gradient-boosted model (GBM), and logistic regression models (LR and LASSO). The baseline models are statistical models built using EHR data (EHR model) [59] and administrative claims model (CMS) [60]. The cohort included 56,477 patients from the GWTG-HF data set. The study population's overall 30-day readmission rate was 21.2%. The variables included in the analysis were extracted from patient EHRs and cover demographics, socioeconomic status, medical history, characterization of HF, lab results, etc. In total, about 250 variables were used as features in the analysis. The data set was randomly divided into training (70%) and validation (30%). The models' performance was assessed based on the validation set. The C statistic was used as a performance measure to distinguish between a readmission or not. The performance of the ML models and the statistical models are respectively TAN(0.62), LR(0.62), LASSO(0.62), RF(0.61), GBM(0.61), EHR model (0.59), and CMS (0.6). The experimental results revealed that there is no significant difference between ML models and statistical models in this context. One limitation of this study is the use of only C statistics as performance metrics. It is possible that additional metrics might better reveal a difference between the studied models.
