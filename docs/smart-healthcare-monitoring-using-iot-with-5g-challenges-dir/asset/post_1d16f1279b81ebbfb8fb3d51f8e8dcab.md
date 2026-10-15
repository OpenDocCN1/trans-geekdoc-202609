
DTL model. Here, only limited numbers of data are required to run the model. To diagnose COVID-19 disease and analyze, only 307 chest radiographs were taken as a dataset and three pre-trained models, namely AlexNet [40], GoogleNet [41], and ResNet [42] have been used. GoogleNet has reported the highest accuracy among these three pre-trained models.

## 2.5 DESCRIPTION OF PROPOSED MODEL TO MITIGATE COVID-19

As already highlighted earlier, DTL is effective in building predictive models to deal with COVID-19 situation. DTL does not need much data. There is another technique known as EC that is also useful when computing power is limited. As a result, combining both of these computational approaches or models may be more useful for developing AI-driven methods to deal with COVID. We may assume that DTL on EC (DTLEC) is a special combination to deal with the COVID pandemic. The advantages of both DTL and EC are incorporated to formulate these models. This DTLEC concept is not practically used to mitigate COVID-19 but is evolving [43–69]. It has been observed that such a model could be useful in the healthcare industry, critical care units, quarantine facilities, and other areas where an outbreak could occur. Figure 2.3 shows edge devices or IoT devices implemented on EC and configured to use AI for decision making. Further, the system is designed to trigger an alert system implemented using a cloud-based approach. Later this edge device with a fine-tuning mechanism can be implemented with pre-trained datasets. Further, a DL-based graphical processing unit (GPU) enabled cloud server, which uses a standard dataset for performing feature extraction, is considered. Moreover, a pre-trained data model (DL based) is run over edge devices. With a fine-tuning mechanism, this edge device is considered to be implemented with pre-trained approach and dataset.

![](img/7bb239370082cb34554bae1e45e2b0d7_38_0.png)

FIGURE 2.3 Proposed model for DTL using EC.

![](img/7bb239370082cb34554bae1e45e2b0d7_39_0.png)

FIGURE 2.4 Proposed IoT-based smart monitoring system.

A typical COVID-19 outbreak scenario is depicted in Figure 2.3, where the proposed model or architecture is visualized for dealing with COVID-19 situations using DTL and EC. This device can monitor if any person is wearing mask in public or not or maintaining social distance. If the model detects any such scenarios, an automated text message with all pertinent information will be sent to the nearest police station as well as pedestrians registered with local mobile networks. Nevertheless, we have not considered a limitation. Children play a major role in spreading the virus. Children are less likely to wear masks on a regular basis because they don’t understand the benefits of wearing masks in public areas (Figure 2.4).

## 2.6 REVIEW OF CERTAIN REPORTED WORKS RELATED TO ML/DL APPROACHES OF COVID-19 DETECTION, PREDICTION, AND OTHER ISSUES

Various research studies have recently reported the application of ML-based approaches for COVID-19 detection, prediction, and monitoring, among other things. Table 2.1 contains a summary of selected works. Some of these works are related to diagnosis [70,71], patient screening [72], observation of COVID-19 from radiographs, scan images, [73–77]; genome sequencing [78], monitoring [79], and prediction [80–82].

Table 2.2 provides a summary of some of the works based on DTL. Here, we see that DTL has been used for prediction [84,85], screening [86], detection, and diagnosis [39,87–91]. There are some works are based on EC (Table 2.3). Here we see that EC has been used for screening [91–93], controlling spreading [13,94], monitoring [95,96]. Table 2.4 includes some recent techniques developed using ML/DL approaches used exclusively for COVID-19 outbreak prediction. The outcomes are found to be accurate. Table 2.5 shows a few works related to tracking and detection of virus spread. The works use big data and related analysis for tracking and detection of virus spread. Table 2.6 shows a few works (which use big data from the Kyoto Genes storage) related to diagnosis and treatment of corona virus.

## TABLE 2.1

### Current DL based works to reduce pandemics

| Sl. No. | Work | Specific Objective | Principal Contributions |
|---|---|---|---|
| 1 | 71 | Diagnosis using Deep Bayes-Squeeze Nets and X-ray images. | Using functional DL algorithm for image processing to develop an intelligent recognition system.<br>A modern COVID-19 decision-making framework that combines traditional and cutting-edge approaches for chest radiographs. |
| 2 | 72 | Screening for corona virus disease pneumonia in 2019. | Research compared several computational models for classifying different types of pneumonia.<br>According to CT tests, the accuracy of different cases was 0.996 (95% CI: 0.989-1.00), with a sensitivity of 98.2% and specificity of 92.2%. |
| 3 | 73 | Detection and classification of COVID-19 infection from CT images. | Weakly controlled DL for COVID-19 contamination observation and classification from radiograms.<br>Reduce the amount of labeling needed for CT pictures. |
| 4 | 74 | Active cases are automatically detected using raw radiograph. | Different types of pneumonia could be observed by DL-based binary, multi-classification representation.<br>To ensure good precision, a combination of YOLO and Dark Net models were used as the model's backbone. |
| 5 | 75 | Identification of COVID-19 patterns in radiograms. | Detection of virus patterns in radiographs.<br>Datasets from a resourcefulness model giving an accuracy of 91.4%, sensitivity of 90%, and forecasting of 100% were developed [83]. |
| 6 | 76 | Distinguishing between novel corona virus and influenza pneumonias. | An early diagnosis method for distinguishing corona virus pneumonia from standard Influenza with transferability on chest CT images. |
| 7 | 77 | SARSCoV-2 was identified using expanding genomic sequences. | The interaction of viromics and DL.<br>A DL-assisted model for developing and future studies. |
| 8 | 78 | Deep learning and CT image analysis are used to automate detection and patient monitoring. | Clinical awareness model based on 2D- and 3D-DL.<br>Suggested a continual monitoring method for active patients. |

## TABLE 2.1 (Continued)

### Current DL based works to reduce pandemics

| Sl. No. | Work | Specific Objective | Principal Contributions |
|---------|------|--------------------|------------------------|
| 9 | 79 | Predict the COVID-19 outbreak in Iran. | • The information was gathered from the Google Trends website. • Positive COVID-19 cases were estimated using linear regression and LSTM models. |
| 10 | 80 | Using computer-assisted tomography images of the upper body; a fully automated framework to detect COVID-19 has been developed. | • COVNet was developed to detect the presence of this virus using visual features derived from scan. • A large number chest scans of patients were collected from six different hospitals. |
| 11 | 81 | Case detection using an open access chest radiograph image dataset. | • COVID-Net, for detecting active cases from scan images, was proposed as a publicly accessible COVID-Net. • COVIDx is a publicly available chest radiographs dataset. |
| 12 | 82 | A model for pandemic forecasting. | • A forecasting model based on Monte-Carlo approach. |
| 13 | 83 | Applying DL to predict infectious disease with the help of big data. | • Comparison among DL and other models for forecasting possible contamination diseases. • The schematic model aimed to strengthen current monitoring systems in order to spot emerging viral diseases in the future. |

Table 2.7 shows a few works related to drug and vaccine development. The research employs molecular docking for drug development, and various peptides have been suggested for the development of a vaccine to combat this deadly virus.

From the above, we may conclude that big data and AI technologies are important in combating the pandemic in different ways. The significant approaches are:

- i. Forecast of outbreak.
- ii. Tracing and detection of spread.
- iii. Detection and therapy.
- iv. Drug and discovery of booster dose.

Learning-based approaches such as DL have also been found to be useful in virus centric modeling, grouping, and approximation. AI supports smart problem-solving tools for projecting successful and secure COVID-19 drug/booster dose design, which would be useful from both a science and a financial standpoint.
