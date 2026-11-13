
## REFERENCES

- 1. G. Fico et al., “Integration of Personalized Healthcare Pathways in an ICT Platform for Diabetes Managements: A Small-Scale Exploratory Study,” IEEE Journal of Biomedical and Health Informatics, vol. 20, no. 1, pp. 29–38, Jan. 2016, doi: 10.1109/JBHI.2014.2367863.

- 2. S. G. Mougiakakou et al., “SMARTDIAB: A Communication and Information Technology Approach for the Intelligent Monitoring, Management and Follow-up of Type I Diabetes Patients,” IEEE Transactions on Information Technology in Biomedicine, vol. 14, no. 3, pp. 622–633, May 2010, doi: 10.1109/TITB.2009.2039711.

- 3. J. Theis, W. L. Galanter, A. D. Boyd and H. Darabi, “Improving the In-Hospital Mortality Prediction of Diabetes ICU Patients Using a Process Mining/Deep Learning Architecture,” IEEE Journal of Biomedical and Health Informatics, vol. 26, no. 1, pp. 388–399, Jan. 2022, doi: 10.1109/JBHI.2021.3092969.

- 4. S. Sarathambekai et al., “A Comparative Analysis of Diabetes Prediction Models Using Machine Learning Algorithms,” 2022 8th International Conference on Advanced Computing and Communication Systems (ICACCS), Coimbatore, India, 2022, pp. 261–265, doi: 10.1109/ICACCS54159.2022.9785280.

- 5. H. El Bouhissi, R. El-Qutaish, A. Ziane, K. Amroun, N. Yaya and M. Lachi, “Towards Diabetes Mellitus Prediction Based on Machine-Learning,” 2023 International Conference on Smart Computing and Application (ICSCA), Hail, Saudi Arabia, 2023, pp. 1–6, doi: 10.1109/ICSCA57840.2023.10087782.

- 6. M. A. Samir, Z. A. Mohamed, M. A. A. Hussein and A. Atia, “Applying Deep Learning to Track Food Consumption and Human Activity for Non-intrusive Blood Glucose Monitoring,” 2021 IEEE 12th Annual Ubiquitous Computing, Electronics & Mobile Communication Conference (UEMCON), New York, NY, USA, 2021, pp. 0319–0324, doi: 10.1109/UEMCON53757.2021.9666662.

- 7. J. Kim and L. Tran, “Ensemble Learning Based on Convolutional Neural Networks for the Classification of Retinal Diseases from Optical Coherence Tomography Images,” 2020 IEEE 33rd International Symposium on Computer-Based Medical Systems (CBMS), Rochester, MN, 2020, pp. 532–537, doi: 10.1109/CBMS49503.2020.00106.

- 8. C. Santos, M. S. de Aguiar, D. Welfer and B. M. Belloni, “Detection of Fundus Lesions through a Convolutional Neural Network in Patients with Diabetic Retinopathy,” 2021 43rd Annual International Conference of the IEEE Engineering in Medicine & Biology Society (EMBC), Mexico, 2021, pp. 2692–2695, doi: 10.1109/EMBC46164.2021.9630075.

- 9. T. Subha, N. Susila, R. Ranjana, V. Priya and V. Nithyashree, “Analysis of Diabetic Retinopathy and Its Causes Using Fuzzy C-Means Model,” 2021 4th International Conference on Computing and Communications Technologies (ICCCT), Chennai, India, 2021, pp. 527–532, doi: 10.1109/ICCCT53315.2021.9711840.

- 10. B. Sazdov et al., “Prediction of Hospital Readmission Using Federated Learning,” 2023 30th International Conference on Systems, Signals and Image Processing (IWSSIP), Ohrid, North Macedonia, 2023, pp. 1–5, doi: 10.1109/IWSSIP58668.2023.10180282.

## Diabetes Mellitus Detection Using Deep Learning Model

M. Karthikeyan and R. Rengaraj

### 7.1 INTRODUCTION

The number of people with diabetes mellitus (DM) is high in developing countries like India owing to an increase in obesity and unhealthy lifestyles [1]. Type 2-DM can lead to microvascular and macrovascular problems. Recently, in India, these multiple organ problems have lead to an unconditional probability of death at an young age [1]. Type 2-DM is one of the most challenging threats to the Indian health care systems. The international diabetes federation estimated 74.9 million people with DM in 2021 with an expected projection of 124.9 million people with DM in 2045 [2]. According to the World Health Organization (WHO), people with age (≥45 and seldom exercising), body mass index (≥24 kg/m²), impaired glucose tolerance or impaired fasting glucose, family history of DM, lower high-density lipoprotein cholesterol or hypertriglyceridemia, hypertension, or cardiovascular disease and gestation female (age ≥30) are at a high risk of DM [3]. The targets set by the WHO to achieve in the year 2030 are:

- 1. 80% of people with diabetes are to be diagnosed [4].
- 2. 80% of people with diagnosed diabetes should have good control of glycaemia [4].
- 3. 80% of people with diagnosed diabetes should have good control of blood pressure [4].
- 4. 60% of people with diabetes of 40 years or older must receive statins [4].
- 5. 100% of people with type 1 diabetes must have access to affordable insulin treatment and blood glucose self-monitoring [4].

The clinical detection of type 2-DM uses a fasting plasma glucose level greater than threshold. This glycaemic threshold levels may vary according to people belonging to a particular region because of the different glycaemic risk levels. Despite these difficulties, a decision support system for detecting type 2-DM is the need of the hour to reach a meaningful decision at a possible early stage. These constraints kindle the need for a simplified diagnostic process to detect type 2-DM.

With the latest technological development and the impact of artificial intelligence (AI) in every day activities, development of machine learning (ML) algorithms helps in making a quick decision support system in type 2-DM detection. Several neural network-based algorithms [5], deep neural networks [6,7], and conventional ML models [8–17] are used in the research of type 2-DM detection.

Considering the challenges and accuracy rate in type 2-DM detection available in the literature and the usage of modern AI tools, there is vital need for a new improved model. Hence, in this chapter, we propose a robust deep learning model (DLM) for type 2-DM detection to create an efficient decision support system. The chapter's contributions can be outlined as follows:

- 1. We propose a simple DLM for type 2-DM detection. We also explore the ML algorithm with Bayesian optimization for hyperparameter tuning. A comparison is made in terms of performance metrics for the algorithms considered.
- 2. The model undergoes training using a dataset from Germany hospital dataset and is subsequently tested with PIMA Indian diabetes dataset (PIDD) showing the generalization supremacy of the proposed model with the available ML.
- 3. The concept of transfer learning is strengthened by training the model with one dataset and testing it with another dataset that was not part of the training process.

The remainder of the chapter is structured as follows: Section 7.2 presents the literature on DM prediction. Section 7.3 introduces the methodology. Section 7.4 presents the proposed DLM. Section 7.5 presents the experimental dataset. Results and discussions are explained in Section 7.6. Section 7.7 concludes the chapter.

### 7.2 RELATED WORK

In recent years, the field of AI and ML has played a vital role to detect the likelihood of type-2 DM disease. Many algorithms and tools have been developed showing the incredible potential of this research domain. We limit our review to recent findings which are closely related to the issue presented. Neural network-based prediction shows improvement in prediction accuracy recently in DM research. In Ref. [6], authors utilized min-max normalization and autoencoder to resolve data normalization, imbalance in dataset, and feature augmentation. Multilayer perceptron was used for classification to achieve a 92.31% accuracy [6]. In Ref. [5], authors designed a classifier based on artificial backpropagation scaled conjugate gradient neural network with 93% accuracy without data pre-processing. An improved neural network-based method was reported in Ref. [18] using k-nearest neighbour to achieve an F1-score of 98%. Authors of Ref. [19] applied Pearson correlation and median value imputation for feature selection. Their deep neural network model achieved 88.6% accuracy [18].

The ML classification model yielded good prediction accuracies when compared to neural network-based methods. In Ref. [20], authors evaluated different ML classifiers: light gradient boosting machine (LGBM), linear regression (LR), and support vector machines (SVMs) with LGBM outperforming other models with an accuracy of 86%. In Ref. [18], classification accuracies of ML algorithms decision tree (DT), random forest (RF), naïve bayes (NB), k-nearest neighbour (KNN), and adaptive boosting (AB) were compared. Authors of Ref. [7] developed a deep neural network model with an accuracy of 98.07%. In Ref. [21], feature selection methods
