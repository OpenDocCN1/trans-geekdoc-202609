
![](img/a2fc2296b12812e9151e817bff1de16d_256_0.png)

### FIGURE 13.4 Detection of VLP using EMD

The SAECG signal is obtained by calculating the mean of the aligned beats obtained using the matched filter. Equation 13.2 represents the SAECG signal obtained from an ECG signal consisting of N-beats.

$$SAECG = \frac{1}{N} \sum_{i=1}^{N} s_i \tag{13.2}$$

Where $s_i$ is the i$^{th}$ beat of any ECG signal. This shows the output obtained by averaging the consecutive beats of the matched filter output signal.

The PhysioNet database is used to obtain the ECG signals. The MIT Arrhythmia database is used to get ECG signals with VLP, while the Fantasia database is used to provide normal ECG signals. The original ECG signal from the MIT Arrhythmia database is displayed in Figure 13.5. Figure 13.6 displays the SAECG signal that was produced after the ECG signal was filtered and beats were aligned.

After applying EMD to the acquired SAECG signal, IMFs and residuals are obtained. The EMD of the SAECG signal obtained from an abnormal ECG signal is shown in Figure 13.7. The existence of VLP is indicated by low-amplitude signals in the residue signal at the end of the QRS complex. The need for the occurrence of the VLP signal is indicated by the presence of signals with an amplitude of less than 20 microvolts that occur at the end of the QRS complex and linger for more than 38 milliseconds. As a result, Figure 13.7 shows that the resulting residue contains VLP. In Figure 13.8, the IMFs obtained by the decomposition of the normal ECG signal where there are no continuous low-amplitude signals present indicate there are no VLP present.

![](img/a2fc2296b12812e9151e817bff1de16d_257_0.png)

![](img/a2fc2296b12812e9151e817bff1de16d_257_1.png)

![](img/a2fc2296b12812e9151e817bff1de16d_258_0.png)

### FIGURE 13.7 EMD applied to abnormal ECG signal

The power spectrum of obtained IMFs is plotted and three features, namely mean, spectral entropy, and peak amplitude, are extracted.

The feature selection was done on the extracted features based on a ranking method, a one-way ANOVA test [66]. The Fisher’s discrimination index (F) and probability (p) were used to determine the potential for discrimination of the features and, based on the values of F and p, the features were sorted in descending and ascending order, respectively. The different classifiers receive the ranking features one at a time as input. The comparison of the outcomes with the current and existing works is shown in Table 13.3. It is observed that the suggested strategy yields superior outcomes.

![](img/a2fc2296b12812e9151e817bff1de16d_259_0.png)

### FIGURE 13.8 EMD applied to normal ECG signal

Thus, the proposed method analyzes the ECG waveform, extracts these low-amplitude signals using the EMD method and classifies the normal and abnormal signals based on the bagging and boosting classifiers.

## TABLE 13.3 Performance Evaluation Comparison

| Technique Used | Metric | Value |
|---|---|---|
| Wavelet transform and ANN [59] | ACC | 78 |
|  | SP | 77 |
|  | SP | 80 |
| Wigner-Ville distribution [60] | SP | 86.31 |
|  | SN | 83.1 |
| Wavelet transform and ACO [61] | SP | 95.24 |
|  | SN | 94.12 |
| Wavelet decomposition and SVM [67] | ACC | 98.82 |
|  | SP | 94.04 |
|  | SN | 99.71 |
| Wavelet decomposition and SVM [68] | ACC | 98.35 |
|  | SP | 98.36 |
|  | SN | 98.33 |
| Wavelet decomposition and quadratic discriminant [69] | ACC | 98 |
| Empirical mode decomposition with bagging and AdaBoost [62] | ACC | 98.93 |
|  | SP | 98.62 |
|  | SN | 99.84 |

## 13.5 CHALLENGES IN ML-BASED ECG ANALYSIS

- 1. Intensity of care is reduced due to a lack of direct monitoring of the patients. The direct personal care of patients by medical experts is reduced, which may increase the risk for the patients. The number of visits may be reduced due to the continuous monitoring of the patients, but this may hide side effects that have occurred because monitoring is done only for a specific disease.
- 2. Wrong diagnosis during long-term monitoring may happen, due to the need for long-term continuous monitoring and the huge amounts of data required, which necessitates that the patient wear the device for a substantial period of time. Any careless action by the patient may lead to a loss of data or a wrong prediction being made. Sometimes, irregularities of data may occur, which may subside the crucial symptoms that have occurred in the patients.
- 3. The data acquired by the continuous monitoring of patients is given with the trust that data confidentiality will be maintained. But the reality is that it is not possible to rely on the medical expert alone to maintain the data confidentially. The medical history of the patient becomes known to a number of people, disturbing the patient’s personal space.
- 4. A huge volume of data is collected from the patients. In times of emergency, it is required to segregate the critical data from the normal data. But this huge volume of data sometimes makes the extraction process very slow.
- 5. The machine learning algorithms used in predicting diseases may sometimes create a lot of conflicts between the medical expert and the researcher in terms of the analysis that is being done by the medical experts to predict the diseases.
- 6. Due to continuous monitoring, the external noises being introduced in the ECG and the artifacts due to various parameters, such as stress and anxiety, which are not filtered by the denoising techniques, can sometimes be misinterpreted as CVDs, leading to wrong predictions being made.

## 13.6 CONCLUSION

ML-based ECG analysis enables the continuous monitoring of the patient, helping medical experts to locate any abnormality in the ECG and thereby predict the presence of a particular CVD. Based on the severity of the abnormality detected, immediate treatment is given to the patients by medical experts, which can reduce mortality to a great extent. The manual prediction of disease from the ECG, which is time-consuming, is reduced by using the ML-based technique. The ML-based approach to ECG analysis will be an effective approach in post-CVD affected patients. These systems are trained using the existing data, making it much easier and less tense for the medical experts and the patients who are under examination.

A method to detect the ventricular late potential (VLP) using the ML-based system is discussed in this chapter. The VLP signals are considered important parameters in the detection of CVDs. In post-MI patients, VLPs can be used to notice factors in the ECG signal to avoid sudden cardiac death. Though VLPs play a significant role in the CVD characterization process, the detection process is not widespread. In this work, an EMD-based detection of VLPs is proposed. This method, along with an automatic detection phase, can be used for clinical applications. Using machine learning methods to create an automated ECG analysis system will help physicians more effectively diagnose a disease and suggest appropriate remedies at an early stage, thereby enhancing treatment and reducing mortality.

## REFERENCES

- 1. Carroll, W. M. (2019). The global burden of neurological disorders. *The Lancet Neurology*, 18(5), 418–419. https://doi.org/10.1016/S1474-4422(19)30029-8
- 2. Kyu, H. H., Abate, D., Abate, K. H., Abay, S. M., Abbafati, C., Abbasi, N., & Breitborde, N. J. (2018). Global, regional, and national disability-adjusted life-years (DALYs) for 359 diseases and injuries and healthy life expectancy (HALE) for 195 countries and territories, 1990–2017: A systematic analysis for the Global Burden of Disease Study 2017. *The Lancet*, 392(10159), 1859–1922. https://doi.org/10.1016/S0140-6736(18)32335-3
- 3. World Health Organization (2000). Global health estimates: Deaths by cause. Age, sex and country, 2012, 2014.
- 4. Acharya, U. R., Bhat, P. S., & Niranjan, U. C. (2002). Comprehensive visualization of cardiac health using electrocardiograms. *Computers in Biology and Medicine*, 32(1), 49–54. https://doi.org/10.1016/S0010-4825(01)00029-4
- 5. Richardson, J., Haywood, L. J., Murthy, V. K., & Harvey, G. (1971). A mathematical model for ECG wave forms and power spectra. *Mathematical Biosciences*, 12(3–4), 321–328. https://doi.org/10.1016/0025-5564(71)90026-5
- 6. Clifford, G. D., Azuaje, F., & Mcsharry, P. (2006). ECG statistics, noise, artifacts, and missing data. *Advanced Methods and Tools for ECG Data Analysis*, 6(1), 18.
- 7. Friesen, G. M., Jannett, T. C., Jadallah, M. A., Yates, S. L., Quint, S. R., & Nagle, H. T. (1990). A comparison of the noise sensitivity of nine QRS detection algorithms. *IEEE Transactions on Bio-Medical Engineering*, 37(1), 85–98. https://doi.org/10.1109/10.43620
- 8. Van Alste, J. A., & Schilder, T. S. (1985). Removal of base-line wander and power-line interference from the ECG by an efficient FIR filter with a reduced number of taps. *IEEE Transactions on Bio-Medical Engineering*, 12(12), 1052–1060. https://doi.org/10.1109/TBME.1985.325514
- 9. Levkov, C., Mihov, G., Ivanov, R., Daskalov, I., Christov, I., & Dotsinsky, I. (2005). Removal of power-line interference from the ECG: A review of the subtraction procedure. *BioMedical Engineering Online*, 4(1), 1–18.
- 10. Frölich, L., & Dowding, I. (2018). Removal of muscular artifacts in EEG signals: A comparison of linear decomposition methods. *Brain Informatics*, 5(1), 13–22.
- 11. Martens, S. M., Mischi, M., Oei, S. G., & Bergmans, J. W. (2006). An improved adaptive power line interference canceller for electrocardiography. *IEEE Transactions on Bio-Medical Engineering*, 53(11), 2220–2231. https://doi.org/10.1109/TBME.2006.883631
- 12. Łęski, J. M., & Henzel, N. (2005). ECG baseline wander and powerline interference reduction using nonlinear filter bank. *Signal Processing*, 85(4), 781–793. https://doi.org/10.1016/j.sigpro.2004.12.001
- 13. Romero, I., Geng, D., & Berset, T. (2012, September). Adaptive filtering in ECG denoising: A comparative study. In *Computing in Cardiology*. IEEE, pp. 45–48.
- 14. Chawla, M. P. S. (2009). A comparative analysis of principal component and independent component techniques for electrocardiograms. *Neural Computing and Applications*, 18(6), 539–556.
- 15. Ho, C. Y. F., Ling, B. W. K., Wong, T. P. L., Chan, A. Y. P., & Tam, P. K. S. (2003). Fuzzy multiwavelet denoising on ECG signal. *Electronics Letters*, 39(16), 1163–1164. https://doi.org/10.1049/el:20030757
- 16. Aqil, M., Jbari, A., & Bourouhou, A. (2017). ECG signal denoising by discrete wavelet transform. *International Journal of Online Engineering*, 13(9), 51–68.
- 17. Singh, B. N., & Tiwari, A. K. (2006). Optimal selection of wavelet basis function applied to ECG signal denoising. *Digital Signal Processing*, 16(3), 275–287. https://doi.org/10.1016/j.dsp.2005.12.003
- 18. Huang, N. E., Shen, Z., Long, S. R., Wu, M. C., Shih, H. H., Zheng, Q., & Liu, H. H. (1998). The empirical mode decomposition and the Hilbert spectrum for nonlinear and non-stationary time series analysis. *Proceedings of the Royal Society of London. Series A: Mathematical, Physical and Engineering Sciences*, 454(1971), 903–995. https://doi.org/10.1098/rspa.1998.0193
- 19. Oweis, R. J., & Al-Tabbaa, B. O. (2014). QRS detection and heart rate variability analysis: A survey. *Biomedical Science and Engineering*, 2(1), 13–34.
