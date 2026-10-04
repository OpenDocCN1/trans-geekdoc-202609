
20. [Chaurasiya, K. L., Harsha, A. S., Sinha, Y., and Bhattacharya, B.](#ch5.xhtml#R_ref5_20) (2022). Design and development of non-magnetic hierarchical actuator powered by shape memory alloy based bipennate muscle. Sci. Reports, 12(1), 10758.

21. [Schaffner, M., Faber, J. A., Pianegonda, L., Rühs, P. A., Coulter, F., and Studart, A. R.](#ch5.xhtml#R_ref5_21) (2018). 3D printing of robotic soft actuators with programmable bioinspired architectures. Nat. Comm., 9(1), 878.

22. [Chen, Y., Yang, Y., Li, M., Chen, E., Mu, W., Fisher, R., and Yin, R.](#ch5.xhtml#R_ref5_22) (2021). Wearable actuators: An overview. Textiles, 1(2), 283–321.

23. [Wang, L., Lou, Z., Wang, K., Zhao, S., Yu, P., Wei, W., Wang, D., Han, W., Jiang, K., and Shen, G.](#ch5.xhtml#R_ref5_23) (2020). Biocompatible and biodegradable functional polysaccharides for flexible humidity sensors. Research.

24. [Revert Calabuig, N., Laarossi, I., Álvarez González, A., Pérez Nuñez, A., González Pérez, L., and GarcíaMinguillán, A. C.](#ch5.xhtml#R_ref5_24) (2023). Development of a low-cost smart sensor GNSS system for real-time positioning and orientation for floating offshore wind platform. Sensors, 23(2), 925.

25. [Socoró, J. C., Alías, F., and Alsina-Pagès, R. M.](#ch5.xhtml#R_ref5_25) (2017). An anomalous noise events detector for dynamic road traffic noise mapping in real-life urban and suburban environments. Sensors, 17(10), 2323.

# 6 Systematic Literature Review on Diagnosis of Arrhythmia Using Intelligent Computing Methods

Neha Goyal^[6](#fn6)

## Abstract

In today’s era, the life style of people has become much sophisticated due to involvement of stress, anxiety and depression in daily routine of human being. In such scenario cardiac diseases are growing rapidly in youngsters as well as in senior citizens. It is also observed that cardiac diseases are much crucial and sensitive including life threatening chances. So, it is very essential to detect and prevent such type of cardiac disorder within required time for recovery. Since it has become a lot of research in prediction and prevention of cardiac disorders and cardiac arrhythmia is also one of the majorly occurring disease in a bulk of population. Electrocardiogram (ECG) is the cheap and best way for the diagnosis of the problem of cardiac arrhythmia and there is a huge amount of data which is collected day by day in hospitals and pathological centers. Previously there are developed various automated models for detection of cardiac arrhythmia using various machine learning (ML) and deep learning approaches. In this work a review on recent developed automated model is performed based on their performance based on some specific parameters like deployed datasets, variation of input data, applied application, methodology and results obtained by the developed model. There are also mentioned the limitations of reviewed papers in addition with their future scope of improvement.

**Keywords:** Intelligent computing, arrhythmia, ECG, machine learning

## 1. Introduction

Arrhythmia is generally considered a problem of irregular heart beat in human and it is very crucial for life threats and misses happenings. There exists various kind of arrhythmia with some specific recognition and features and so it becomes very helpful to classify and distinguish the various categories of arrhythmia. Generally, the detection of arrhythmia is by classifying it into two classes, whereas the first one is diagnosed by the problem of a single irregularity in heart beat and so called as morphological arrhythmia. The second phase of the arrhythmia is diagnosed with the feature of multiple irregularity in heart beats and hence considered as a problem of rhythmic arrhythmia.

Basically, there are observed some changes and alterations in wave form of the heartbeats if an individual is consisting with morphological or rhythmic arrhythmia. The detection and diagnosis of the issue is done by electrocardiography (ECG) as well as with the echocardiogram (ECHO). The problem of arrhythmia is directly associated with issue in valve of heart which results some irregular heart rates.

The ECG is a well-established tool in cardiology for assessing a patient’s heart status. ECG stands for electrocardiogram, which is an electrical representation of the heart’s contractile activity that may be conveniently recorded using surface electrodes on the patient’s limbs or chest. In the world of medicine, the ECG is one of the most well-known and widely used biological signals. Counting the R peaks of the ECG wave throughout one minute of recording ([Figure 1](#ch6.xhtml#fig6_1)) is a simple way to calculate the heart’s rhythm in beats per minute (bpm). More importantly, cardiovascular illnesses and disorders impact the rhythm and morphology of the ECG waveform.

![Figure 6.1: Steps of learning system.](images/fig6_1_C.jpg)

[Figure 6.1: Steps of learning system.](#ch6.xhtml#R_fig6_1)

A heart trace is an ECG. It can tell you about your heart’s rhythm and pace. Abnormal heart tracings can indicate a variety of diseases, in addition to heart rhythm abnormalities. Fast heartbeats (tachycardia), slow heartbeats (bradycardia), heart blockages, and irregular heartbeats are all examples of heart rhythm disorders (atrial fibrillation). It can also reveal information on heart chamber enlargement and anomalies in the heart muscle. An echocardiogram is a moving picture of the heart’s structure and function obtained by an ultrasound scan. It displays precise information on the heart’s pumping activity as well as the diameters of the heart chambers. As a result, they’re a useful test for determining the severity of heart failure. Echocardiograms can also tell you how well your heart valves are working. So generally, ECG is considered better and comfortable for detection of arrhythmia due to its low cost and time consumption features in addition with having capability to determine irregularity in heart palpitations more accurately.

Finding and classifying arrhythmias can be extremely difficult for a human being because it is necessary to assess each heartbeat of ECG readings obtained by a holter monitor over hours or even days. Furthermore, due to fatigue, there is a risk of human error during the processing of ECG records The use of computational tools for automatic classification is an option.

A complete automatic approach for detecting arrhythmias from ECG signals may be broken down into four parts ([Figure 6.1](#ch6.xhtml#fig6_1)): Pre-processing of ECG signals; heartbeat segmentation; feature extraction; and learning/classification. A step is taken in each of the four processes, with the eventual goal of determining the type of heartbeat. The first two steps of such a classification system (ECG signal pre-processing and heartbeat segmentation) have been extensively studied [[2](#ch6.xhtml#ref6_2)–6]. Pre-processing procedures have a direct impact on the final outcomes, thus they should be carefully chosen. In the case of QRS detection, the findings from the heartbeat segmentation stage are almost perfect. However, there is still room for exploration and improvements in the steps related to classification (feature extraction and learning algorithms). Even though the problem of ECG delineation is still open, it is not so useful for the methods in the literature surveyed here.
