
41. Adamichou, C.; Genitsaridi, I.; Nikolopoulos, D.; Nikoloudaki, M.; Repa, A.; Bortoluzzi, A.; Fanouriakis, A.; Sidiropoulos, P.; Boumpas, D.T.; Bertsias, G.K. Lupus or not? SLE Risk Probability Index (SLERPI): A simple, clinician-friendly machine learning-based model to assist the diagnosis of systemic lupus erythematosus. Ann. Rheum. Dis. 2021, 80, 758–766. [CrossRef]

42. Donner-Banzhoff, N. Solving the diagnostic challenge: A patient-centered approach. Ann. Fam. Med. 2018, 16, 353–358. [CrossRef]

43. Kinloch, A.J.; Asano, Y.; Mohsin, A.; Henry, C.; Abraham, R.; Chang, A.; Labno, C.; Wilson, P.C.; Clark, M.R. Machine learning to quantify in situ humoral selection in human lupus tubulointerstitial inflammation. Front. Immunol. 2020, 11, 593177. [CrossRef]

44. Usategui, I.; Barbado, J.; Torres, A.M.; Cascón, J.; Mateo, J. Machine learning, a new tool for the detection of immunodeficiency patterns in systemic lupus erythematosus. J. Investig. Med. 2023, 71, 742–752. [CrossRef] [PubMed]

45. Chen, W.; Lei, X.; Chakrabortty, R.; Pal, S.C.; Sahana, M.; Janizadeh, S. Evaluation of different boosting ensemble machine learning models and novel deep learning and boosting framework for head-cut gully erosion susceptibility. J. Environ. Manag. 2021, 284, 112015. [CrossRef] [PubMed]

Disclaimer/Publisher’s Note: The statements, opinions and data contained in all publications are solely those of the individual author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to people or property resulting from any ideas, methods, instructions or products referred to in the content.

## Searching for the Best Machine Learning Algorithm for the Detection of Left Ventricular Hypertrophy from the ECG: A Review

Simon W Rabkin

Department of Medicine, Division of Cardiology, University of British Columbia, 9th Floor 2775 Laurel St., Vancouver, BC V5Z 1M9, Canada; simon.rabkin@ubc.ca; Tel.: +1-(604)-875-5847; Fax: +1-(604)-875-5849

### Abstract

**Background:** Left ventricular hypertrophy (LVH) is a powerful predictor of future cardiovascular events. **Objectives:** The objectives of this study were to conduct a systematic review of machine learning (ML) algorithms for the identification of LVH and compare them with respect to the classical features of test sensitivity, specificity, accuracy, ROC and the traditional ECG criteria for LVH. **Methods:** A search string was constructed with the operators “left ventricular hypertrophy, electrocardiogram” AND machine learning; then, Medline and PubMed were systematically searched. **Results:** There were 14 studies that examined the detection of LVH utilizing the ECG and utilized at least one ML approach. ML approaches encompassed support vector machines, logistic regression, Random Forest, GLMNet, Gradient Boosting Machine, XGBoost, AdaBoost, ensemble neural networks, convolutional neural networks, deep neural networks and a back-propagation neural network. Sensitivity ranged from 0.29 to 0.966 and specificity ranged from 0.53 to 0.99. A comparison with the classical ECG criteria for LVH was performed in nine studies. ML algorithms were universally more sensitive than the Cornell voltage, Cornell product, Sokolow–Lyons or Romhilt–Estes criteria. However, none of the ML algorithms had meaningfully better specificity, and four were worse. Many of the ML algorithms included a large number of clinical (age, sex, height, weight), laboratory and detailed ECG waveform data (P, QRS and T wave), making them difficult to utilize in a clinical screening situation. **Conclusions:** There are over a dozen different ML algorithms for the detection of LVH on a 12-lead ECG that use various ECG signal analyses and/or the inclusion of clinical and laboratory variables. Most improved in terms of sensitivity, but most also failed to outperform specificity compared to the classic ECG criteria. ML algorithms should be compared or tested on the same (standard) database.

Keywords: left ventricular hypertrophy; electrocardiogram; machine learning; artificial intelligence

## 1. Introduction

A number of different groups have proposed machine learning models to evaluate ECG with or without additional clinical and laboratory data to construct an approach to identify left ventricular hypertrophy (LVH). LVH, or an increased left ventricular mass, is a powerful predictor of future cardiovascular events [1–3]. LVH can serve as a marker for the severity of (occult) cardiovascular disease, thereby identifying an increased risk of stroke or, more directly, by limiting myocardial perfusion, leading to myocardial ischemia and serious cardiac arrhythmias [4–8]. The ECG has been used for decades as an indicator of the presence of LVH, with increased QRS voltage being considered to be a marker for increased left ventricular mass [9–16]. Although the ECG QRS voltage criteria are not a highly sensitive indicator of LVH [17–25], the importance of predicting the presence of LVH and the imperative of cost efficiency, i.e., utilization of a low-cost ECG compared to a more expensive echocardiogram or MRI, has focused attention on how to extract more precise indicators of LVH from ECGs. This imperative is underscored by the use of a 12-lead ECG as part of the basic assessment of patients with cardiovascular disease [26,27].

Because of the importance of LVH identification, the ML disparate approaches and the variables considered in each approach, a review of this field has become increasingly needed. A meta-analysis, to construct a single estimate or effect size, is not realistic in fields such as machine learning, when different input variables and analytic techniques are employed by utilizing different algorithms on different datasets. Hence, an in-depth review is the best approach to evaluate different ML algorithms. The objectives of this study were to conduct a review of machine learning algorithms for the identification of LVH with respect to the classical features of sensitivity, specificity and accuracy. It also aimed to assess how each ML algorithm compares to the traditional ECG criteria for LVH, specifically Cornell voltage [13], Cornell product [28], Sokolow-Lyons [9] and Romhilt-Estes [29] criteria.

## 2. Methods

### 2.1. Literature Search

A search string was constructed using terms connected with Boolean operators “left ventricular hypertrophy AND electrocardiogram or ECG” AND machine learning to identify articles reporting a machine learning approach for the diagnosis of LVH. Medline and PubMed were systematically searched from their date of inception through to 31 October 2023. Preferred Reporting Items for Reviews and Meta-Analysis (PRISMA) was used to conduct the search [30] (Supplementary Figure S1).

Article titles and abstracts were assessed for full-text review. Papers on hypertrophic obstructive cardiomyopathy were excluded because this entity represents an asymmetric cardiac hypertrophy, which would alter ECG voltage in a different manner. The exclusion criteria were as follows: non-English studies, non-primary studies, studies without full texts, studies that have insufficient data for analysis, non-human studies and studies unrelated to the investigated topic. The review was not registered, and protocol is not available for access.

### 2.2. Data Extraction and Classification

Data extraction was performed by one reviewer. The following items were collected from each article: author, year of publication, recruitment center or clinical trial sampled, sample size, age and sex of participants, definition of LVH and its method of assessment. Reported sensitivity, specificity, positive predictive value, negative predictive value, area under the receiver operating curve (ROC), overall accuracy and F1 score were extracted. Input variables and the ML techniques utilized were also extracted.

## 3. Results

There were 14 studies that examined the detection of left ventricular hypertrophy with an approach utilizing the ECG and utilized at least one machine learning approach (Table 1). Some details of the study population characteristics and input variables are summarized in Table 1.

Lin and Liu evaluated data from 2196 men, aged 17 to 45 years of age, who were in the military, and used the support vector machine (SVM) classifier as the machine learning method [31]. The prevalence of echocardiographic LVH was about 6.5%. Thirty-one input variables were utilized that included three clinical ones, age, body height and body weight, and 28 ECG parameters, such as heart rate, the durations of P wave, PR interval, QRS interval, QT interval and QTc interval in Lead II and the axes of the P, QRS and T waves in Lead II, and the voltages of R waves in all Limb Leads I, II, III, aVR, aVL, aVF and S wave in Lead aVL, and the voltages of R and S waves in all precordial leads V1–V6 [31]. The model had high sensitivity (86.7%).
