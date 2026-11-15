Because of the importance of LVH identification, the ML disparate approaches and the variables considered in each approach, a review of this field has become increasingly needed. A meta-analysis, to construct a single estimate or effect size, is not realistic in fields such as machine learning, when different input variables and analytic techniques are employed by utilizing different algorithms on different datasets. Hence, an in-depth review is the best approach to evaluate different ML algorithms. The objectives of this study were to conduct a review of machine learning algorithms for the identification of LVH with respect to the classical features of sensitivity, specificity and accuracy. It also aimed to assess how each ML algorithm compares to the traditional ECG criteria for LVH, specifically Cornell voltage [13], Cornell product [28], Sokolow-Lyons [9] and Romhilt-Estes [29] criteria.

# 2. Methods

# 2.1. Literature Search

A search string was constructed using terms connected with Boolean operators “left ventricular hypertrophy AND electrocardiogram or ECG” AND machine learning to identify articles reporting a machine learning approach for the diagnosis of LVH. Medline and PubMed were systematically searched from their date of inception through to 31 October 2023. Preferred Reporting Items for Reviews and Meta-Analysis (PRISMA) was used to conduct the search [30] (Supplementary Figure S1).

Article titles and abstracts were assessed for full-text review. Papers on hypertrophic obstructive cardiomyopathy were excluded because this entity represents an asymmetric cardiac hypertrophy, which would alter ECG voltage in a different manner. The exclusion criteria were as follows: non-English studies, non-primary studies, studies without full texts, studies that have insufficient data for analysis, non-human studies and studies unrelated to the investigated topic. The review was not registered, and protocol is not available for access.

# 2.2. Data Extraction and Classification

Data extraction was performed by one reviewer. The following items were collected from each article: author, year of publication, recruitment center or clinical trial sampled, sample size, age and sex of participants, definition of LVH and its method of assessment. Reported sensitivity, specificity, positive predictive value, negative predictive value, area under the receiver operating curve (ROC), overall accuracy and F1 score were extracted. Input variables and the ML techniques utilized were also extracted.

# 3. Results

There were 14 studies that examined the detection of left ventricular hypertrophy with an approach utilizing the ECG and utilized at least one machine language approach (Table 1). Some details of the study population characteristics and input variables are summarized in Table 1.

Lin and Liu evaluated data from 2196 men, aged 17 to 45 years of age, who were in the military, and used the support vector machine (SVM) classifier as the machine learning method [31]. The prevalence of echocardiographic LVH was about 6.5%. Thirty-one input variables were utilized that included three clinical ones, age, body height and body weight, and 28 ECG parameters, such as heart rate, the durations of P wave, PR interval, QRS interval, QT interval and QTc interval in Lead II and the axes of the P, QRS and T waves in Lead II, and the voltages of R waves in all Limb Leads I, II, III, aVR, aVL, aVF and S wave in Lead aVL, and the voltages of R and S waves in all precordial leads V1–V6 [31]. The model had high sensitivity (86.7%).