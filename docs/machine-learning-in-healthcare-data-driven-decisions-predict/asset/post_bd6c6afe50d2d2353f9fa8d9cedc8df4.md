
### 5. Feature Integration and Emotion Selection
We merge the newly derived features with the customized dataset. We notice that certain emotions very rarely occur in the dataset. For example, sadness, fear, and anger appear only 61, 1, and 2 times, respectively. Therefore, we exclude those emotions from our dataset. As a result, six emotions remain in our dataset: alert, happy, neutral, rested/relaxed, tensed/anxious, and tired.

As shown in Table 1, our extracted features are categorized into time-domain, signal-domain, linear, and nonlinear features. They capture different aspects of the heart rate signal, providing a more holistic view of our data. The newly generated merged dataset contains 7,513 rows and 164 columns.

Table 1: Derived features from heart rate variability (HRV) are categorized into four major domains – time domain, signal domain (frequency domain), linear, and nonlinear – each reflecting different physiological aspects of cardiac autonomic regulation.

| Category | Features |
| :--- | :--- |
| Time domain | Mean_bpm, var_bpm, min_bpm, max_bpm, range_bpm, median_bpm, std_bpm, skew_bpm, kurtosis_bpm, iqr_bpm, coefficient_variation, rms, signal energy, peak to peak amplitude, num_peaks, time_above_mean, time_below_mean, autocorr_lag1, autocorr_lag5, sum_autocorr, adf_pvalue, dfa, sample entropy, Poincare_sd1, Poincare_sd2, poincare area, recurrence rate, determinism, Hjorth_activity, Hjorth_mobility, Hjorth_complexity, first_derivative_mean, first_derivative_std, first_derivative_max, second_derivative_mean, second_derivative_std, second_derivative_max, emotional_stability, max_emotional_shift, zero_crossings, max_rate_of_change, linear trend, quadratic trend |
| Signal domain | Dominant_freq, dominant_power, peak_power, spectral_centroid, spectral_spread, spectral_rolloff, spectral_flux, spectral_flatness, spectral_entropy, ultra_low_power, low_power, mid_power, high_power, low_high_ratio, ultra_high_ratio, vif_power, lf_power, hf_power, lf_hf_ratio, total_power, wavelet energy 1-6, wavelet ratio 1-6, wavelet entropy 1-6, total_power_log, lf_power_log, hf_power_log, vif_power_log |
| Linear | Mean_bpm, var_bpm, min_bpm, max_bpm, range_bpm, median_bpm, std_bpm, skew_bpm, kurtosis_bpm, iqr_bpm, coefficient_variation, rms, signal energy, peak_to_peak_amplitude, time_above_mean, time_below_mean, auto_corr_lag1, autocorr_lag5, sum_autocorr, adf_pvalue, dominant_freq, dominant_power, peak_power, spectral_centroid, spectral_spread, spectral_rolloff, spectral_flux, spectral_flatness, spectral_entropy, ultra_low_power, low_power, mid_power, high_power, low_high_ratio, ultra_high_ratio, vif_power, lf_power, hf_power, lf_hf_ratio, total_power, Hjorth_activity, Hjorth_mobility, Hjorth_complexity, first_derivative_mean, first_derivative_std, first_derivative_max, second_derivative_mean, second_derivative_std, second_derivative_max, emotional_stability, max_emotional_shift, zero_crossings, max_rate_of_change, linear_trend, quadratic_trend, wavelet energy 1-6, wavelet ratio 1-6, total_power_log, lf_power_log, hf_power_log, vif_power_log |
| Nonlinear | dfa, sample entropy, poincare_sd1, poincare_sd2, poincare area, recurrence rate, determinism, wavelet entropy 1-6 |

### Data Preprocessing
We conduct extensive preprocessing on the customized dataset before applying any machine learning or neural network models. The preprocessing is divided into four parts: (I) data analysis in time domain, (II) data analysis in signal domain, (III) data cleaning, and (IV) data imputation and scaling, as follows:

- (I) Data Analysis in Time Domain: As depicted in Figure 3, we observe that the distribution of the collected data is uneven over the collected months and year. The maximum and minimum numbers of data entries occur in July 2021 and April 2021, respectively. As per the description of the LifeSnaps dataset, data is collected in two rounds: in the first round, 38 participants contribute data from May 24 to July 26, 2021, while in the second round, 34 participants contribute data from November 15, 2021 to January 17, 2022. One participant is common to both rounds, making the total number of unique participants 71. However, Figure 3 shows that some data is also collected outside the specified study periods, namely during April, August, September, and October 2021.

- (II) Data Analysis in Signal Domain: To validate whether the newly generated features provide new information, we generate characteristic graphs for different users. Here, we show the time-domain and signal-domain features of four users in Figures 4 and 5. In Figure 4, we observe the dominant frequency components present in the signals. The VLF (very low frequency) dominates across all users, highlighting its significant frequency band. User 2 shows the highest power overall, especially in the VLF range. All four users display similar patterns but with different power levels, indicating individual variability. This transformation allows us to identify recurring patterns that may help link physical parameters to emotional states.

In Figure 5, we illustrate the dynamic variability in the data, which associates with autonomic nervous system activity. The spread and shape of the plots describe how physiological responses fluctuate over time. User 1 shows more dispersed points, indicating higher variability in heart rate and RR intervals, potentially reflecting more dynamic heart rate behavior. User 2 shows denser and tighter points, suggesting a more regular and stable heart rhythm with less short-term variability. User 3 shows moderate variability with a balanced rhythm, and user 4 shows high consistency with low short-term variation.

From the observation, we now say that frequency-based features provide additional discriminative power. These features enhance emotion classification models by revealing underlying periodicities that are not as apparent in the raw time-domain signal. The graphical observation supports the feasibility of incorporating signal domain features into predictive modeling, potentially leading to improved accuracy in emotion recognition systems.

![](img/106ef0dba620d314f9842503e8ef40c8_322_0.png)

![](img/106ef0dba620d314f9842503e8ef40c8_322_1.png)

Figure 3: Analyze participants' activity levels during the survey period and observe variation in data collection. Fourteen individuals participate extensively for 60–70 days, while only a few contribute data for 0–10 days.

![](img/106ef0dba620d314f9842503e8ef40c8_323_0.png)

![](img/106ef0dba620d314f9842503e8ef40c8_323_1.png)

![](img/106ef0dba620d314f9842503e8ef40c8_323_2.png)

![](img/106ef0dba620d314f9842503e8ef40c8_323_3.png)

Figure 4: Frequency domain compares four users' VLF, LF, and HF heart rate components via power spectral density.

![](img/106ef0dba620d314f9842503e8ef40c8_324_0.png)

Figure 5: Time domain compares four users using Poincaré plots, highlighting individual differences in heart rate variability and autonomic regulation.

- (III) Data Cleaning: We remove all the unnecessary features from our dataset. As an example, stai stress category and stai stress are available in the dataset. But if we observe, we can see that stai stress category is derived from stai stress.

- (IV) Data Imputation and Scaling: We impute numerical values using the median, while we fill time-series data using a forward/backward fill strategy. Emotions and activity-related data are imputed with the help of the KNN fill-up method, as their granularity is different from the numerical data. After that, we use min-max scaling.

## 3.3 Recursive Feature Elimination

We use recursive feature elimination (RFE) to find the most essential features and remove the unnecessary ones. As shown in Figure 6, We implement two different approaches, which are (I) selective feature-based approach and (II) holistic feature-based approach.

- (I) Selective Feature-Based Approach: As shown in Figure 6, In this approach, we divide the features into two groups: the time domain and the signal domain. RFE selects the features separately from each group using an XGBoost classifier as the best estimator. This approach selects three features from the time domain and three features from the signal domain, and in each subsequent iteration, the number of features increases incrementally until it reaches the maximum available features in each group. After each iteration, the selected features and ranking update. The updated features list then serves as input for the next generation.

- (II) Holistic Feature-Based Approach: In the holistic feature-based approach as shown in Figure 6, we directly work on all the derived features without grouping them. In this approach, we iteratively remove three features in each iteration to find the best relevant features with emotions. In each iteration, the RFE with XGBoost classifier selects a subset of features equal to n_selected = n_current − 3, where n_selected is the number of features available at the start of the iteration. That means here, we remove the three least significant features recursively. The process continues until the predefined number of iterations is reached or a minimal subset of features remains.

## 3.4 Machine Learning and Neural Network Models

We use several ML and neural network models to predict emotions. They are support vector machine (SVM), logistic regression (LR), decision tree (DT), random forest (RF), XGBoost, hybrid machine learning model (HMM), feedforward neural network (FNN), and bidirectional long short-term memory (BiLSTM). The details about the implementation are discussed in Section 4.
