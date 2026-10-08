# 5.3. Selected Features

In order to complete the study, we will show which features and measurements are the most frequently selected and the percentage of selection. Table 3 shows the average number of features by the GAs from each measurement and signal, considering a maximum number of selected features Nmax=40, for the different combination of signals. As we can see, the most selected measurement from the ECG is the RR. Considering the TEB, the RF and the BRV measurements present high ratios in the case of considering all signals in the combination. And the most selected measurement from the EDA is the processed measurement taken in hand.

Table 3. Average number of features selected from the measurements of different signals, with Nmax=40 features.

| Signal Measurement | ECG Arm | TEB Arm | EDA Arm | ECG EDA | TEB EDA | EDA EDA |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| ECG | 6.5 | | | | 1.5 | 3.5 | 3.8 |
| RR | 13.1 | | | | 4.9 | 8.3 | 6.0 |
| RA | 6.7 | | | | 2.4 | 3.5 | 2.1 |
| HR | 6.5 | | | | 1.5 | 2.9 | 1.1 |
| HRV | 2.8 | | | | 2.4 | 2.4 | 2.2 |
| PSD | 0.6 | | | | 0.4 | 0.7 | 0.3 |
| PSD-VLF | 0.5 | | | | 0.3 | 0.4 | 0.7 |
| PSD-LF | | | | | 0.4 | 0.5 | 0.8 |
| PSD-HF0 | 0.9 | | | | 0.4 | 0.6 | 0.9 |
| PSD-VHF | 0.6 | | | | 0.3 | 0.4 | 0.7 |
| TEB | | 8.4 | | | | | 1.6 |
| LF | | 8.9 | | | 1.4 | 3.8 | 1.5 |
| RF | | 10.1 | | | 2.0 | 1.2 | 3.3 |
| BRV | | 5.0 | | | 2.5 | 3.6 | - |
| PSD | | 1.9 | | | 0.3 | 0.6 | 0.2 |
| PSD-VLF | | 0.9 | | | 0.6 | 0.5 | 0.7 |
| PSD-LF | | 0.8 | | | 1.0 | 1.0 | 1.1 |
| PSD-HF | | 2.3 | | | 1.0 | 0.9 | - |
| PSD-VLF | | 0.8 | | 0.6 | 0.6 | 0.6 |
| EDA-Original | | | 5.6 | | 1.6 | 1.3 | 2.6 |
| EDA-Process | | | 9.8 | | 1.4 | 2.5 | 3.5 |
| EDA-LF | | | 8.9 | | 1.5 | 1.3 | 4.0 |
| EDA-HF | | | 0.7 | | 0.6 | 0.8 | 3.8 |
| EDA-PSD | | | 3.2 | | 0.5 | 0.9 | 1.4 |
| EDA-PSD-LF | | | 1.9 | | 0.4 | 0.7 | 0.5 |
| EDA-PSD-HF | | | | | 0.8 | 0.6 | 1.3 |
| EDA-Original | | | 2.8 | | 1.7 | 2.1 | 2.3 |
| EDA-processed | | | 11.6 | 3.9 | 6.0 | 6.9 | 9.2 |
| EDA-LF | | | 6.1 | 1.5 | 1.9 | 2.7 |
| EDA-HF | | | 6.6 | 1.4 | 1.7 | 2.0 | 2.2 |
| EDA-PSD | | | 1.3 | 0.2 | 0.4 | 0.7 | 0.8 |
| EDA-PSD-LF | | | 0.7 | 0.2 | 0.6 | 2.4 | 3.1 |
| EDA-PSD-HF | | | 4.6 | 0.2 | | 1.2 | 1.6 |

To go deeper into the analysis, Table 4 shows the top-40 selected features, in the case of selecting a maximum of Nmax=40 features. In this case, we show the percentage of occurrence in the three best combinations of signals: the TEB, the EDA and the ECG, and the case of using all biosignal. We can see that, in general, the mean baseline is one of the most frequent parameters.

+   The most selected features from each signal: the generic mean of the HRV, the mean baseline of the RR, the length of the SD of the RR, and the DFA1 of the HR.