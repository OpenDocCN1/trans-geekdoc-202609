

### Table 15.4 Performance evaluation measures.

| Performance measures | Mathematical representation | Depiction |
| :--- | :--- | :--- |
| Accuracy | \(\frac{T_P + T_N}{T_P + T_N + F_P + F_N}\) | It can be represented as the ratio of the accurately marked labels to the entire dataset. It is the most common performance representation. |
| Sensitivity/Recall | \(\frac{T_P}{T_P + F_N} \times 100\) | Sensitivity is depicted as the division of the accurately positive labeled by methodology to every data which represents individuals who have seizures truly. |
| Specificity | \(\frac{T_N}{T_N + F_P} \times 100\) | Specificity measures how effectively a classifier measures the negative labels |
| Precision | \(\frac{T_P}{F_P + F_P} \times 100\) | It is a class agreement between the data labels and the positive labels the classifier gives |
| f1-score | \(\frac{2 * (Recall * Precision)}{Recall + Precision}\) | Metric which uses both precision and recall. It is calculated as the average of the precision and recall (harmonic mean) |

The software which is utilized for this methodology is Anaconda version 2019.10, in which python 3.6 is used as our programming language on Windows 8.1. Libraries like keras, tensorflow have been included for accomplishing better results. An 8-GB RAM Lenovo ThinkStation P330 is used as a hardware. To reduce the time operational ability, this workstation which requires 2 min for each epochs to run while contrasting it and the ordinary system, may requires 8 min for each epoch to execute. The entire methodology has been operated over 200 epochs to accomplish better performance result while contrasting to already proposed methodology. Different parameters have been tuned to get the best results; a representation of different performance metrics is represented in Table 15.4 [39]. The best outcome is resulted by setting the parameters as batch size 11, the size proportion as 80–20, and learning rate as 0.01, which gives us the higher results measures when contrasted with tuning other parameters of the model.

## 15.5 Experimental Results and Discussion

### 15.5.1 Performance Measurement Criteria

Following are the various performance measures which have been calculated:

### 15.5.2 Experimental Results

In order to achieve the best results for the detection of an epileptic seizure, we used various tuning parameters like learning rate, size ratio, batch size,

### Table 15.5 Performance metric when learning rate is set to 0.001.

| Batch size | Size ratio | Sensitivity | F1-score | Accuracy | Specificity | Precision |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2 | 90–10 | 95.23 | 94.87 | 94.87 | 95.25 | 94.97 |
| 4 | 90–10 | 94.97 | 94.81 | 94.81 | 95.21 | 94.23 |
| 6 | 90–10 | 95.23 | 94.92 | 94.92 | 95.67 | 95.01 |
| 8 | 90–10 | 95.21 | 94.91 | 94.91 | 95.61 | 94.90 |
| 10 | 90–10 | 95.14 | 94.67 | 94.67 | 95.21 | 94.28 |
| 11 | 90–10 | 92.23 | 92.87 | 92.87 | 93.25 | 93.97 |
| 2 | 80–20 | 91.19 | 92.12 | 92.12 | 92.12 | 92.09 |
| 4 | 80–20 | 92.97 | 92.81 | 92.81 | 93.21 | 92.23 |
| 6 | 80–20 | 93.23 | 92.92 | 92.92 | 92.67 | 93.01 |
| 8 | 80–20 | 93.21 | 93.91 | 92.91 | 93.61 | 92.90 |
| 10 | 80–20 | 92.14 | 93.67 | 93.67 | 92.21 | 92.28 |
| 11 | 80–20 | 96.34 | 95.47 | 95.47 | 95.28 | 95.12 |
| 2 | 70–30 | 95.12 | 94.47 | 94.47 | 94.12 | 93.16 |
| 4 | 70–30 | 95.23 | 94.92 | 94.92 | 95.01 | 95.01 |
| 6 | 70–30 | 92.34 | 90.69 | 90.69 | 91.23 | 91.98 |
| 8 | 70–30 | 92.56 | 90.94 | 90.94 | 91.35 | 92.01 |
| 10 | 70–30 | 92.45 | 90.91 | 90.91 | 91.30 | 91.98 |
| 11 | 70–30 | 93.21 | 91.21 | 91.21 | 92.27 | 92.30 |

etc. Various performance measures have been calculated, which are shown in the tables below.

Table 15.5 represents the various performance measures which is calculated with different tuning parameters but one of the parameter is kept constant which is the learning rate used. The best results are achieved with the tuning parameters when batch size was kept as 11, the training testing size ratio set as 80–20 and learning rate was fixed as 0.001. More results have been calculated with the learning rate of 0.01 and 0.1, which are shown in Tables 15.6 and 15.7, respectively. The best results among all

### Table 15.6 Performance metric when learning rate is set to 0.01.

| Batch size | Size ratio | Sensitivity | F1-score | Accuracy | Specificity | Precision |
|---|---|---|---|---|---|---|
| 2 | 90–10 | 95.12 | 94.47 | 94.47 | 94.12 | 93.16 |
| 4 | 90–10 | 95.23 | 94.92 | 94.92 | 95.01 | 95.01 |
| 6 | 90–10 | 92.34 | 90.69 | 90.69 | 91.23 | 91.98 |
| 8 | 90–10 | 92.56 | 90.94 | 90.94 | 91.35 | 92.01 |
| 10 | 90–10 | 92.45 | 90.91 | 90.91 | 91.30 | 91.98 |
| 11 | 90–10 | 93.21 | 91.21 | 91.21 | 92.27 | 92.30 |
| 2 | 80–20 | 94.56 | 94.36 | 94.36 | 94.56 | 94.78 |
| 4 | 80–20 | 95.97 | 95.81 | 95.81 | 95.21 | 94.23 |
| 6 | 80–20 | 96.23 | 96.92 | 96.92 | 95.67 | 96.01 |
| 8 | 80–20 | 97.21 | 97.91 | 97.91 | 96.61 | 96.90 |
| 10 | 80–20 | 98.14 | 98.67 | 98.67 | 98.21 | 97.28 |
| 11 | 80–20 | 98.94 | 99.20 | 99.20 | 98.89 | 98.86 |
| 2 | 70–30 | 95.12 | 94.47 | 94.47 | 94.12 | 93.16 |
| 4 | 70–30 | 95.23 | 94.92 | 94.92 | 95.01 | 95.01 |
| 6 | 70–30 | 92.34 | 90.69 | 90.69 | 91.23 | 91.98 |
| 8 | 70–30 | 92.56 | 90.94 | 90.94 | 91.35 | 92.01 |
| 10 | 70–30 | 92.45 | 90.91 | 90.91 | 91.30 | 91.98 |
| 11 | 70–30 | 93.21 | 91.21 | 91.21 | 92.27 | 92.30 |

### Table 15.7 Performance metrics when learning rate is set to 0.1.

| Batch size | Size ratio | Sensitivity | F1-score | Accuracy | Specificity | Precision |
| --- | --- | --- | --- | --- | --- | --- |
| 2 | 90–10 | 93.23 | 92.87 | 92.87 | 92.25 | 92.97 |
| 4 | 90–10 | 92.97 | 92.81 | 92.81 | 92.21 | 92.23 |
| 6 | 90–10 | 92.23 | 92.92 | 92.92 | 92.67 | 92.01 |
| 8 | 90–10 | 92.21 | 92.91 | 92.91 | 92.61 | 92.90 |
| 10 | 90–10 | 93.14 | 93.67 | 92.67 | 93.21 | 93.28 |
| 11 | 90–10 | 92.23 | 92.87 | 92.87 | 93.25 | 93.97 |
| 2 | 80–20 | 92.21 | 92.45 | 92.45 | 92.89 | 92.19 |
| 4 | 80–20 | 92.97 | 92.81 | 92.81 | 93.21 | 92.23 |
| 6 | 80–20 | 93.27 | 92.92 | 92.92 | 92.67 | 93.01 |
| 8 | 80–20 | 93.21 | 93.91 | 92.91 | 93.61 | 92.90 |
| 10 | 80–20 | 92.14 | 93.67 | 93.67 | 92.21 | 92.28 |
| 11 | 80–20 | 91.34 | 91.47 | 91.47 | 91.28 | 91.12 |
| 2 | 70–30 | 91.12 | 91.47 | 91.47 | 91.12 | 91.16 |
| 4 | 70–30 | 91.23 | 91.92 | 91.92 | 91.01 | 91.01 |
| 6 | 70–30 | 92.34 | 90.69 | 90.69 | 91.23 | 91.98 |
| 8 | 70–30 | 92.56 | 90.94 | 90.94 | 91.35 | 92.01 |
| 10 | 70–30 | 92.45 | 90.91 | 90.91 | 91.30 | 91.98 |
| 11 | 70–30 | 93.21 | 91.21 | 91.21 | 92.27 | 92.30 |

the three learning rate is achieved with the learning rate of 0.01 which is shown in Table 15.6.

## 15.6 Discussion

Restricted Boltzmann Machine is a methodology that is valuable in dimensionality reduction, regression, pattern classification, topic demonstration and collaborative filtering. Various researchers have extracted a large number of features from the EEG signals in the time domain and frequency domain in order to detect or predict epileptic seizures. Table 15.8 shows the various

### Table 15.8 Comparative analysis of already proposed methodologies.

| Authors | Features | Classifier used | Performance metric |
|---|---|---|---|
| Thorodroff et al. [35] | Discrete wavelet transform coefficients | RCNN | Sens: 85% |
| Yusuf Khan et al. [36] | Discrete wavelet transform coefficient | ConvNets | Sens: 87.8% |
| Truong et al. [17] | Short Term Fourier Transform | ConvNets | Sens: 81.2% |
| Yoo, Ji-Hyun [26] | Frequency Domain Signals | RCNN | Sens: 90% |
| Rajamanickam et al. [37] | Discrete wavelet transform coefficients | ConvNets | Sens: 86.29% |
| Zhou et al. [19] | Time Domain Signals | ConvNets | Accu: 97.5% |
| Ozcan et al. [18] | Spectral power, Statistical moments | ConvNets | Sens: 87.01% |
| Xinghua et al. [21] | Time Domain Signals | Bi-LSTM | Sens: 88.80% Spec: 88.60% |
| Frieselbern et al. [22] | Time Domain Signals | CNN-GRU | Sens: 89% Accu: 75.6% |
| Xiaoyan et al. [24] | Time Domain Signals | CNN-LSTM | Acc: 93.4% Sens: 91.88% Spec: 86.13% |
| Wei Xia et al. [25] | Discrete wavelet transform coefficients | CNN-LSTM | Acc: 98.60% Spec: 98.54%, Sens: 84% |
| Choi et al. [38] | Short Term Fourier Transform | CNN-GRU | Sens: 89.4% |
| **Proposed Method** | **Time Domain Signals** | **Restricted Boltzmann Machine** | Acc: 99.20% Spec: 98.89%, Sens: 98.94% |

existing methods which have been proposed before this work. In 2018, Truong et al. [17] used the CNN classifier to achieve the sensitivity of 81.2% using Short Term Fourier Transform for the feature extraction. Various researchers have also proposed their methodology; in 2017, Khan et al. [36]

