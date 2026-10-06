
> In this paper, we propose an effective electrocardiogram (ECG) signal classification method using `XGBoost` classifier. The ECG signals are passed through four phases of data acquisition, noise filtering, feature extraction, and classification. In first phase, dataset is collected from the MIT-BIH arrhythmia database. In second phase, noise is removed using baseline wandering removal filter. In next phase, 45 descriptors from four prominent features which showed good results in previous work, namely, wavelets, higher order statistics (HOS), morphological descriptors, and R-R intervals, are being employed. Using these features as an input to the `XGBoost` classifier, the signals are being classified into four classes (N, S, V, and F) as per the ANSI-AAMI standards; of all the classifiers, `XGBoost` shows best result with an accuracy of 99.43%.
>
> **Keywords:** Arrhythmia, `XGBoost`, ECG, wavelet, morphology, R-R interval

## 8.1 Introduction

Arrhythmia is defined as an abnormality in normal heart rate; it is a general indication of cardiovascular diseases which can be severe in most cases if left unattended. It signifies that the heart is not beating at its normal rate or it is beating with an irregular pattern [1]. Timely detection of this irregularity is helpful in curing it and saving the patient from cardiovascular diseases [2].

Electrocardiogram (ECG) signal, which is the result of electrical activity in the heart due to its depolarization and repolarization, is used. It is measured by putting electrodes at various points of the body and is recorded when the heart goes through its cardiac cycle. ECGs from healthy persons have a characteristic natural shape; any kind of abnormality can change the electrical activity of the heart which, in turn, leads to change in ECG shape. Diseases like abnormal heart rhythms, heart attack can be detected using arrhythmia detection. Classification of ECG signals as normal or arrhythmic is a challenging task and, if done manually, can lead to a lot of errors and wrong detection. This is why a lot of work is needed in this field of arrhythmia detection [3].

Different papers have taken the ECG signals from different databases; two of the most common ones are MIT-BIH and ECG-ID arrhythmia database. The dataset from these sources are not completely pure as they have various high frequency noises. These are unwanted and can affect our results if not removed. So, the dataset is made to go through the process of de-noising. Generally, noises include power line interference of 50/60 Hz that is caused by electromagnetic interference of power line, electromyography (EMG) noise that comes at the time of muscle activity and baseline wandering which is the low-frequency component is present in ECG system. To get rid of these noises, different filters have been employed in different papers like digital Infinite Impulse Response (IIR) filter, which is a type of notch filter capable of removing power line interference, along with that Finite Impulse Response (FIR) filters, which have also been used [4].

从数据库中获取无噪声的数据集后，下一步是特征提取；特征是基本定义数据集条件的描述符。许多不同的特征提取技术在不同论文中被使用；大多数基于频率和时间技术。时间域提取的特征包括心跳间隔、持续时间参数（`PR`、`QT`、`QRS`）以及幅度特征（`ST` 和 `QRS`）。时间域提取的特征作为分类器的特征并不十分出色。取而代之的是频率域方法是更好的替代方案；因此，功率谱密度（`PSD`）和傅里叶变换等技术在该领域很受欢迎，但频率方法的缺点是它们不提供 ECG 信号的时间信息。在所有频率域方法中，小波变换是最广泛使用的方法 [5]。

Mahmoud *et al*. [6] 提出了一种使用非 fiducial 特征集合、 fiducial 特征集合以及非 fiducial 与 fiducial 特征融合的技术，并使用三种分类器——人工神经网络（`ANN`）、K 最近邻（`KNN`）和支持向量机（`SVM`）进行分类。Rajagopal *et al*. [7] 使用了一组特征，包括 1) 心跳的时间特征，如 `P-Q` 间隔、`QRS` 间隔、`S-T` 间隔、`Q-R` 间隔以及相邻心跳之间的 `R-R` 间隔；2) 幅度特征；3) 小波变换基于的特征，如 Harr 小波和 Daubechies 小波；4) Stockwell 变换基于的特征，并使用结合 `KNN` 和 `SVM` 的协同决策模型进行分类。

Mondejarr-Guerra *et al*. [8] 展示了使用小波、高阶统计（`HOS`）、1D 局部二值模式、形态学描述符以及 `R-R` 间隔作为特征进行分类；分类器是一个 `SVM` ensemble，其中每个特征分别输入 `SVM`，结果通过 One-Versus-One（`OVO`）投票策略合并，得到最终类别。

Mathews *et al*. [9] 使用了深度信念网络（`DBN`）和受限玻尔兹曼机（`RBM`）进行 supraventricular 和 ventricular 心跳的分类。Sannino *et al*. [10] 提出了深度神经网络，并与 11 个 `WEKA` 工具进行了比较，结果显示其准确率更高。Diker *et al*. [12] 采用了 Pan Tompkins 方法和离散小波变换（`DWT`）方法提取关键点，然后将这些关键点输入传统的极限学习机算法进行分类。

本文讨论 ECG 分类，组织方式如下：Section 8.2 讨论用于 ECG 分类的特征选择及理论背景概述。Section 8.2 同时介绍本文使用的主要分类器及其架构。Section 8.3 重点展示实验结果以及与其他现有工作的对比。结论在 Section 8.4 中给出。

## 8.2 Materials and Methods

The dataset has been taken from MIT-BIH database and is pre-processed first to remove the noises. Then, features are extracted from the dataset which are used by the classifier to classify the signals into four classes (N, S, V, and F) as per the ANSI-AAMI standard. Different steps involved in the process can be summarized by the following workflow diagram Figure 8.1.

![Figure 8.1 Workflow diagram describing the approach to ECG classification used in the paper.](img/fig8-1.jpg)

**Figure 8.1** Workflow diagram describing the approach to ECG classification used in the paper.

## 8.2.1 MIT-BIH Arrhythmia Database

The database contains ECG signals from 47 patients of about 30 minutes which is sampled at 360 Hz at 11-bit resolution. There are two signals in each record modified-lead II (ML II), and one of V1, V2, V4, or V5. As ML II is common in all the records, only it is considered while doing the classification, and there are approximately 110,000 beats. These beats have been classified into five classes [11]. There are certain records that contain paced beats which are not considered for the process of classification. The database is highly imbalanced with majority of beats belonging to Normal (N) class. The database distribution is presented in Table 8.1. The unknown beat (Q) class has been ignored in this work as it is practically nonexistent with very rare samples belonging to this class [12, 13]. The database has been used using the intra-patient's scheme where the dataset is taken together and from that collection some are used for training and some for testing. In this work, only out of signals from all the other electrodes only lead II are taken into consideration [14].

**Table 8.1** Classes present in MIT-BIH database with their percentage.

| **Classes** | **Records (%)** |
| --- | --- |
| N | 90 |
| SVEB | 3 |
| VEB | 6 |
| F | 1 |

## 8.2.2 Signal Pre-Processing

Pre-processing is the step in which we filter the signals so that the features extracted from the signal are pure and without any noise and disturbances. This is crucial as this directly affects the classification results. Median filter are useful in reducing random noise using the median value in the segmented window. In this paper, baseline wandering removal using the median filter with a local window size of kernel size 180 has been proposed.

## 8.2.3 Feature Extraction

In this paper, for the purpose of extraction of features, symmetric window of size 180 was taken around the R-peak and features were extracted from the window. The features extracted were as follows.

Wavelets: Wavelets are the descriptor of the waveform of the ECG signal so they contain information of the time as well as frequency domain, Daubechies wavelet function (db1) with 3 levels of decomposition has been applied here. It provides in total 23 descriptors. This is proved to give relevant information by different authors [15].

RR-Interval: The highest point in the amplitude of the ECG signal is the R-peak, distance between the successive R-peaks can give useful information about the state of ECG signals, and it is categorized into four types, namely, Pre-RR, which is the distance between current and preceding R peak, Post-RR, that is the distance between current and following R peak, local RR, which is the mean value of previous 10 pre-RR values, and global-RR, which I the mean value of the pre-RR values of last twenty minutes. In addition to these, their normalized values are also used so total 8 features are extracted from the RR-Interval [16].
