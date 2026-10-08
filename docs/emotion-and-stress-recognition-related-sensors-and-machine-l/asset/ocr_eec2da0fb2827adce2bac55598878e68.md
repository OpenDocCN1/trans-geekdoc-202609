# 4.2. Signal Pre-Processing

The raw data recorded from the sensors usually shows a low signal-to-noise ratio, thus, it is generally necessary to pre-process the data, namely filtering to remove motion artefacts, outliers, and further noise. Additionally, since different modalities were acquired, further filtering specifications are required according to each sensor modality. Considering what is typically found in the state-of-the-art [1], the filtering for which each modality was performed as:

+   - Electrocardiography (ECG): Finite impulse response (FIR) band-pass filter of 300 and 3-45 Hz cut-off frequency;
- Electrodermal Activity (EDA): Butterworth band-pass filter of order 4 and 1 Hz-0.35 Hz cut-off frequency.
- Respiration (RESP): Butterworth band-pass filter of order 4 and 1-8 Hz cut-off frequency.
- Blood Volume Pulse (BVP): Butterworth band-pass filter of order 4 and 1

After noise removal, the data was segmented into 40 s sliding windows with 75% overlap. Lastly, the data was normalised per user, by subtracting the mean and dividing by the standard deviation, to values between 0-1 to remove subjective biases.

# 4.3. Supervised Learning Using Single Modality Classifiers

The ER classification is performed with a classifier tuned for Arousal and another for Valence. Table 2 presents the experimental results for the SL techniques.
As can be seen, from the TMED dataset, the state-of-the-art results [7] were available for each sensor modality, which we display, and our methodology was able to achieve superior results. Additionally, we observe higher accuracy values in the Valence dimension compared to the Arousal stride. Finally, for the WSAD dataset, the F-score drops significantly to 0.0, compared to the Accuracy value. The F-score low value derives from the fact, that the class labels were largely unbalanced, with some of the test sets having only one of the labels. To conclude, overall the sensors modalities competitive results

We present the classifiers per sensor modality and class dimension in Table 3. Additionally, the features obtained using the forward feature selection algorithm are displayed in Tables 3 and 5, for the Arousal and Valence dimensions, respectively. As shown, they explore similar correlated aspects in each modality.

Both the classifiers and features were selected via a 4-fold CV, to be used for the SL evaluation and for the DF algorithm, which is detailed in the next section. However, no classifier was generally able to emerge as optimal as the ER on the aforementioned aspects. Lastly, concerning the features for each modality, we selected 570, 373, 322, and 487 features respectively the EDA, ECG, BVP, and RESP sensor data. However, such high dimension feature vector is both redundant and has many zero column features, therefore, we were able to reduce the feature vector without significant degradation of the classification performance.

Figure A1 in Appendix A displays two histograms the features used in the SL methodologies in all the datasets for Arousal and Valence axis. The figure shows that most features were selected via the SFFS methodology, specifically for each dataset (a value of 1 means that the features were selected in just one dataset). The features EDA on spectrum mean value, and BVP signal are selected in 2 datasets for the Arousal axis; while, the features EDA spectrum mean value (in 4), RESP mean (in 2), BVP (in 2) signal mean, and ECG NNI (NN intervals) minimum peak value, are repeated for the Valence axis.