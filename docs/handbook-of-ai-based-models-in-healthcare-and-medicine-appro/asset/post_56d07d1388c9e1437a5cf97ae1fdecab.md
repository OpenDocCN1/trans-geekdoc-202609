
The various machine learning techniques and algorithms that are currently employed in the prediction of heart disease from ECG signals are covered in this chapter. This chapter discusses ways the ventricular late potential (VLP), which appears on ECG data, might be used to predict cardiac disease. One of the main goals of machine learning-based prediction systems for healthcare is the development of models that can be used to predict health. This contributes to the reduction of disease severity and, consequently, mortality. The general flowchart for a healthcare management system based on machine learning is given in Figure 13.1. The main step in the machine learning pipeline is collecting data for the ML model's training. The accuracy of the prediction is dependent on the data size and characteristics used to train the model. Various denoising approaches are used to eliminate noise from the data, which is then followed by feature extraction and feature selection, where the optimum features are chosen from the extracted features. To predict diseases, these chosen features are input into a variety of classification algorithms. The expected values are observed, and, depending on the severity, decisions are made on whether to seek immediate medical supervision or to continue taking the recommended regular medications.

The prediction technique for a system with an ECG signal as input involves the prediction of abnormalities from deviations that occur in the ECG. Each of the

![](img/a2fc2296b12812e9151e817bff1de16d_247_0.png)

FIGURE 13.1 Flowchart for machine learning-based healthcare management system

![](img/a2fc2296b12812e9151e817bff1de16d_248_0.png)

FIGURE 13.2 General ECG heartbeat – PQRST segment

elements in the PQRST segment has a particular significance in the cardiac cycle and any deviation may contribute to some type of abnormality. Careful examination of these deviations is an important factor in the prediction of particular CVDs. Manually locating deviations may not give accurate results, whereas an automatic prediction system using ML techniques is used to produce more reliable results. A segment of the ECG signal consisting of the PQRST segment is given in Figure 13.2.

Early CVD prediction and treatment are both possible with meticulous analysis of ECG signals, which lowers the mortality rate. However, there will be a number of mistakes made when manually deciphering the signals to identify the various CVDs, owing to the non-stationary characteristic of the ECG data. Therefore, to analyze ECGs for the existence of various CVDs and circumvent the limits of manually interpreting the ECG signals, an automatic detection method is crucial.

## 13.2 THE NEED FOR MACHINE LEARNING IN ECG ANALYSIS

The main objectives of machine learning in ECG analysis are:

- To maximize the amount of information extracted from comprehensive ECG signals. By using a continuous monitoring system, a large amount of data for the ML model is obtained from the patients, which makes it possible to identify the minute variations or abnormalities that occur in the ECG signal.
- To predict the type of disease from the information extracted. Each CVD is related to minute variations in the ECG signal extracted. The ML-based system helps in identifying the type of disease.
- To determine the disease's severity. The severity of the abnormality that occurred has a direct link with the amount of deviation on the ECG signal using the pretrained ML model.
- The ML-based system enables the early prediction of diseases and thus enables giving immediate treatment based on the severity, thereby reducing the mortality rate.

## 13.3 THE PROCESS INVOLVED IN MACHINE LEARNING-BASED ECG CLASSIFICATION

The steps involved in ML-based ECG classification are discussed below.

### 13.3.1 DENOISING

The extracted original ECG signals have a lot of interference, with multiple noise signals. Appropriate denoising techniques are required to extract the original ECG signals from these noisy signals. For accurate and reliable analysis of the signals to predict various diseases, signals devoid of noise are essential. The most important noises in the ECG signal are electromyographic (EMG)/muscle artifact [6, 7], baseline wander (BW) [8, 9] and power line interferences (PLI) [10]. Several denoising techniques are used to remove the above-discussed noises from ECG signals. The traditionally used denoising techniques are the adaptive filtering method [11], principal and independent component analysis [12], and fuzzy wavelet denoising [13]. Discrete wavelet transform (DWT) and empirical mode decomposition (EMD) are found to be the most effective denoising techniques and are discussed in detail.

- **Discrete wavelet transform (DWT):** In DWT, it is important to define the optimal function for a particular ECG signal [14]. For instance, Ho et al. utilized the wavelet energy to calculate the necessary wavelet coefficients, and then a sub-band smoothing filter is applied to further reduce noise [15]. The number of wavelet decomposition layers has an impact on the denoising effect. The mother wavelet product and the wavelet coefficients are combined linearly to represent the signal in DWT. The fundamental principle of WT is the breakdown of a signal into several frequency level coefficients. Determining how signals behave in various frequency ranges may be done using the basic capacity to analyze signals in various frequency bands and scales. The signal is broken down into specific information using DWT, making it possible to analyze the signal at various frequency bands and resolutions [16, 17]. The precision of the denoising process is dependent on some factors, including DWT’s wavelet function, the choice of the threshold approach and the DWT decomposition level. The mathematical representation of continuous wavelet transform (CWT) is given as:

$$CWT(a,b;x(t),\psi(t))=\int_{-\infty}^{\infty}x(t)\frac{1}{a}\psi^*\left(\frac{t-b}{a}\right)dt \tag{13.1}$$

and frequency. SFE approaches provide the mean, standard deviation, variance, kurtosis measures, and skew measurements of the provided medical data in certain circumstances. With these measurements, medical professionals may analyze the signal and, on their advice, the signal's qualities are extracted.

### 13.3.3 FEATURE SELECTION

The size of the medical record volume makes processing the entire record challenging and time-consuming. In the medical sector, saving a patient's life depends on speed. Here, choosing which features to use is a necessary effort. Various feature selection techniques can be utilized, depending on the patient test result pattern or the medical record pattern [20].

- **The filter methods:** The filter method calculates the significance of the characteristic, which indicates the feature's capacity for class distinction. Lower-ranked characteristics are eliminated based on the determined relevance value. The feature's ability to distinguish between the various groups is indicated by its significance. A few of the filter methods which use the ranking methods are Euclidean distance, one-way analysis of variance (ANOVA) test, T-test, chi-squared test (χ²), correlation-based feature selection (CFS), ReliefF method, information gain method, and minimum redundancy maximum relevance (MRMR) method.
- **The wrapper-based method:** This method chooses the best features instead of the most relevant collection of features. This technique takes into account various feature combinations. The best subset of features is chosen after these combinations have been analyzed and contrasted with other feature combinations. The subset of features is selected in a greedy way based on a backward elimination process, by which the dependency between the features and the subset of features is maintained. The most commonly used wrapper-based methods are recursive feature elimination (RFE), backward and forward elimination, and sequential forward selection (SFS).
- **Embedded methods:** The above-listed advantages of the filter-based method and wrapper-based method are combined in embedded methods. Algorithms with built-in feature selection strategies put these methods into practice. Among the best-known examples of these approaches are regression techniques like LASSO and RIDGE, which have built-in penalization procedures to reduce overfitting.

### 13.3.4 CLASSIFIERS AND PREDICTORS

The classification of various diseases from the ECG signal and the prediction of the severity of the condition is based on the automatic detection method and classification is based on many machine learning (ML) techniques. The ML methods for the
