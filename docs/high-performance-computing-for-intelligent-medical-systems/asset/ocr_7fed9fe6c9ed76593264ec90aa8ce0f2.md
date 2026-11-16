It reveals that the velocity of the pulse in a vessel which is known as *pulse wave velocity* (PWV) equals \([L \times C(P)]^{-1/2}\). Therefore, the time for the wave to pass a length of \(l\) (PTT) is:

PTT = \(l\sqrt{LC(P)}\) (4.7)

According to equation (4.7), PTT depends on BP inversely. If we assume that C is constant, the PWV becomes:

PWV = \(\frac{1}{\sqrt{L \times C}} = \sqrt{\frac{A dP}{\rho d A}} = \sqrt{\frac{Eh}{2 \rho r}}\) (4.8)

This equation is known as the Bramwell–Hill and Moens–Korteweg equation [7].

Besides PWV and PTT, many other studies try to define other hand-crafted features and find out their relationship with BP [8, 9]. In this study, however, we emphasize automatic feature extraction using deep-learning techniques. We believe that similar to many other applications, machine-learning abilities can be utilized for finding appropriate representations of signals for BP estimation. Afterwards, we develop several methods to achieve this goal¹.

# ## 4.3 Data source

We use the *Multiparameter Intelligent Monitoring in Intensive Care II* (MIMIC-II) database to implement and evaluate our deep models for BP estimation. It encompasses high-resolution data of a diverse population of patients in the intensive care unit (ICU). The dataset includes clinical documentation, laboratory results, and various physiological waveforms [10].

We consider invasive arterial BP, ECG, and PPG signals of 200 patients (86 women and 114 men) in this research. The mean and standard deviation of the subject ages are 61.6 ± 14.6 years. The sampling frequency of all waveforms is 125 Hz.

Systolic and diastolic BPs² in each cardiac cycle are extracted from invasive BP waveforms to use them as target values during the training and validation phases of the models. All selected records contain 51 884 cycles. Figure 4.2 shows the binned-scatter plot and the distribution histogram of the BP. As we expected, the figure indicates the direct correlation between systolic and diastolic BP [11].

# ## 4.3.1 Preprocessing procedures

We apply several filters to remove artifacts from signals and improve their quality. Then, PPG signals are segmented to prepare the input data to feed our deep networks. For each input segment, systolic and diastolic BPs are extracted from