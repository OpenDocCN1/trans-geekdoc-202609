there are individual electrodermal differences as a function of trait-anxiety score, however people provide a deep study of the features for the signals, such as the use of these signals with the same purpose.

+   - In order to obtain the window length, the first limit found in the literature review is imposed by feature calculation. There are some features that require a minimum window length to be calculated, as HRV triangular index, which takes at least 20 min to be calculated [33–35]; Standard Deviation of NN intervals (SDNN) index, calculated as mean deviations of NN intervals for all 5 min of the entire recording [34], and for all derivatives (Standard Deviation of Successive deviations (SDSD), Standard Deviation of sequential 5-min RR interval (SDANN) found in [34]. In our case, we decided to use window lengths lower than 60 s, as the database could be cut down, which would change the study.

+   - In our study, we studied a large number of features which have been selected from a deep revision of the literature. The most frequently used ECG signals were obtained in both the frequency and time domain: frequency bands [23,43,44,46,47,48], and power ratios in frequency domain; and Heart Rate Variability (HRV) [23,26,38,39,41,42,45,48,50,51], the SDNN [42,48,49]. Number of N in 50 ms (NN50), pNN50 [34,48], as mean amplitude rate, frequency deviation and all the features found in the raw signals, [25,37–52]. In our study, we studied all the features found in a review of more than 90 papers.

The features extracted from the TEB signal were used in some works as, [24] where the approach is to study cardiovascular during emotional activation in men and women. Here, the TEB has been acquired with ECG and the heart sound. In [56] the full respiratory signal was derived from the thoracic impedance raw data, like in our case.

Finally, the EDA is studied in several papers, [26,42,49,53,57,58]. A complete all the features about the EDA signal is in [41,59].

+   - Most published papers used the calculated features to feed the classifier. Therefore, the number of features depends on the particular study. We implement element feature selection from all the features to find the best ones and avoid generalization problems in classification.

+   - The classifier is usually determined by the author without comparisons or detailed studies about suitability. In numerous works, the selected classifier is the Support Vector Machine (SVM). It is think to make a comparison of different classifiers with different characteristics.



A sensor network capable of acquiring the ECG, TEB and EDA signals was designed, in order to obtain a database of signals to be used in this study. The complete system requires all the signals described in the literature, that have been mentioned above, which is explained in detail in [25,60]. To acquire the multiple biosignals a sensitized sensors were used, which is shown in Figure 1.

A glove to acquire EDA measurement in, a bracelet to acquire EDA measurement in the arm and a vest to acquire ECG and TEB. These are connected to the measurement devices via GSR, which acquires the EDA signal and the vest is connected to the chest through a reader ECGZ2, which acquires ECG and TEB signals. The ECGZ2 is capable of sampling each signal with a different sampling frequency. For the TEB and EDA, the sampling frequency is 100 Hz and for the ECG, the sampling frequency is 250.

Measurements were collected from k = 40 subjects, students aged 20 to 49, including 12 females and 28 males. The duration of the complete experiment was approximately 90 min per subject. All of the experiments were performed under the conditions of respect for individual rights and ethical principles that govern biomedical research involving humans, and written informed consent was obtained from all participants. The experiments were approved by the Research Ethics