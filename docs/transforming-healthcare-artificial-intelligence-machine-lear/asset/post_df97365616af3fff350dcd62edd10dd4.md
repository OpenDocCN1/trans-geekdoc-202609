
## Role of AI & ML in lung disease detection

or clicking sounds. They usually result from sudden pressure shifts in restricted airways. COPD is likely the cause if they appear upon inspiration. Localized, coarse, and loud crackles suggest bronchiectasis or pulmonary edema. Crackling is a fine late-inspiratory symptom in extensive fibrosis.

## 1.3.3 Overview of the methodology

Audio-based respiratory condition screening using breathing sounds to classify and develop categorical predictions. Preprocessing real-world audio data feeding into ML models is necessary since these signals may include several sounds. The temporal and spectral properties of transformed spectrograms explain audio transmissions. These attributes may be used directly by standard classifiers or intuitively by DL models. Figure 1.1 shows automated-based respiratory screening system development. Contemporary databases were discussed before. Here, we compare the most prevalent models and propose preprocessing approaches. Take note of audio-derived physio-markers. Social markers (e.g., subject demographics) and biomarkers are also important, but this article will concentrate on noise physio-markers.

## 1.3.4 Machine learning

In artificial intelligence, ML is newer. Without human coding, computers and systems learn and improve via experience. This fascinating discipline of computer science uses statistical methods and algorithms to develop intelligent robots that work rules. ML allows computers to learn, predict, and make decisions without human intervention [96]. Using various techniques and approaches, the data is thoroughly examined to accurately find correlation sequences and extract crucial information hidden in parameter interrelations. Thus, deep data analysis mathematical approaches can be used to create ML algorithms that can learn from massive quantities of empirical data, automate, and precisely adapt to new situations [97].

![](img/bb14ad24e4d4babb616ee31f6e899c86_27_0.png)

Figure 1.1 Automatic respiratory conditional screening system development.

### 1.3.4.1 Supervised learning

First, a ML model with labeled data helps the ML system define input data and output via a target variable. The model is trained on the dataset's relationships, linkages, and function, then applied to remarkably similar, new data to forecast. Lung noises, rising the condition's level, etc. are examples.

### 1.3.4.2 Unsupervised learning

No output variables are predefined, and the ML model is trained on unlabeled data. Finding hidden data structures, patterns, or groupings is the goal. Association rule mining and clustering group comparable lung sound patterns for unsupervised learning [98]. ML computers recognize data patterns. It may be utilized for vision, languages, money, and health. If the lung sounds are aberrant, pneumonia or other respiratory illnesses may be detected early. It has also proven that patient traits affect sounds. Generation millennials and improved data collection accuracy promote modernization. The increase in lung sound analysis is the cause. Thus, clinicians can better identify and treat respiratory problems [99].

### 1.3.5 Deep learning

Increasing ML improves lung sound detection and categorization. CNNs excel at computer vision, brain activity prediction, and behavioral analysis. Convolutional, max pooling, fully linked, and SoftMax output CNN layers are standard. Many CNN models employ LeNet, AlexNet, and VGGNet designs. Complex CNN architectures improve these models. Examples include DenseNet, GoogLeNet with Inception units, and Residual Networks. These complex systems share convolution and pooling but vary in connection, computational complexity, and layer operations [100,101].

DL techniques, particularly CNN models, may increase automated lung sound systems' accuracy and dependability. DL's capacity to extract and learn meaningful features from data without human feature engineering helps lung sound categorization and respiratory disease detection [102].

### 1.3.6 Deep learning in lung sound analysis

Figure 1.2 shows the system structure, shared datasets, preprocessing, feature extraction, and DL algorithms developed for medical applications in this section's overview of lung sound analysis.

## Role of AI & ML in lung disease detection

| Training data | | Lung sound dataset | Testing data | | Abnormal sound detection (ASD) | 2 classes: normal/abnormal | Multi-classes: normal, crackle, wheeze, ... |
|---|---|---|---|---|---|---|---|
| Preprocessing | Feature extraction | Deep model | Output | Respiratory disease recognition (RDR) | Associated with | | |
| ● Noise reduction | ● Hardcraft feature | ● FNN | | ● 2 classes: health/disease | 3 classes: chronic disease recognition | |
| ● Heart sound separation | ● Deep feature | ● CNN | | ● Multi-types: health, COPD, asthma, .. | | |
| | | ● RNN | | | Multi-classes: risk, improve, recovery, .. | | |

Figure 1.2 Deep lung sound analysis.

### 1.3.6.1 System framework

Listening skills impact the doctor's' lung sound interpretations and clinical auscultation findings. By clinical findings, clinicians may misdiagnose patients. Clinicians advocate SVM, CNN, and random under-sampling boosting for lung disease data [103,104,105,106]. Most shallow ML-based lung sound analysis methods have 80% accuracy and were tested on few participants [107,108,109].

DL beats ML in lung sound accuracy and robustness [110]. They may boost performance. DL algorithms can automatically uncover task-relevant features without human feature extracting raw data. RNNs are utilized for lung sound analysis in extracting disease-related periodic oscillations. Transfer learning: DL methods may use common knowledge from adjacent areas like Audio Set [111], a large audio dataset, to enhance lung sound analysis and minimize training. Planning problems limit clinical data, making it vital for clinical applications.

DL lung sound investigations often include data collection, preprocessing, feature extraction, and classification. Digital stethoscopes listen to lungs. Preprocessing lung sounds reduces noise. For lung sound discrimination, feature extraction reduces high-dimensional preprocessed data. Disease classifiers map attributes and classifications.

## 1.4 PROPOSED METHODOLOGY

The main approach of the DL model used to classify lung sounds and illnesses is explained in Figure 1.3. Mel-frequency cepstral coefficients, or MFCC for short, are often used in audio signal processing to extract features from lung sounds that are present in datasets. As seen in Figure 1.4, the generated feature matrix is divided into training and testing sets and supplied to the DL model, respectively, yielding, the categorization of lung diseases and an analysis of lung sound. There are four possible classifications for lung sounds: crackles, wheezes, both crackles and wheezes, and healthy.

## 14 Transforming Healthcare

![](img/bb14ad24e4d4babb616ee31f6e899c86_30_0.png)

Figure 1.3 Workflow of the proposed methodology.

![](img/bb14ad24e4d4babb616ee31f6e899c86_30_1.png)

Figure 1.4 Systematic diagram of the proposed methodology.

### 1.4.1 Dataset collection

Input lung sounds were obtained from normal and abnormal male and female patients with COPD, asthma, and lower and upper respiratory tract infections (LRTI, URTI). Two Portuguese and Greek research teams created a respiratory sound database with 126 input records (ICBHI, 2017 Challenge) [112]. Data samples include healthy and diseased respiratory sounds. Patients of various ages include children, adults, and seniors. The collection includes 520 annotated audio samples from 126 persons,

## Role of AI & ML in lung disease detection

Table 1.1 Lung sounds data distribution in ICBHI database
| S.No. | Lung sounds | No of samples |
|---|---|---|
| 1. | Crackles | 551 |
| 2. | Wheezes | 247 |
| 3. | Crackles and wheezes | 71 |
| 4. | Healthy | 51 |

Table 1.2 Lung diseases distribution in ICBHI
| S. No | Lung diseases | No of samples |
|---|---|---|
| 1. | Bronchiectasis | 16 |
| 2. | Broncholitis | 13 |
| 3. | COPD | 793 |
| 4. | Healthy | 37 |
| 5. | Pneumonia | 23 |
| 6. | URTI | 35 |

comprising 5.5 hours with 6,898 respiratory cycles, 1,864 of which had crackles, 886 wheezes, and 506 both. According to respiratory experts, the cycles had no adventitious respiratory sounds, crackles, wheezes, or both. Diff rent equipment were used to record the 10-to-90-second records. The chest locations where recordings were collected are included. Some breathing cycles feature real-world-like loud noises. The dataset included lung sounds from two to six thoracic locations using a Littman 3,200 electronic stethoscope. After that, the recordings were saved as “way”, files on a computer. Table 1.1 shows the total Crackles, Wheezes, Crackles and Wheezes, and Healthy categories. Table 1.2 shows the lung disease distribution.

### 1.4.2 Data preprocessing

Delete quiet parts, reduction, and resample audio to a uniform rate to preprocess audio files. The MATLAB Signal Processing and DSP tools are popular for these jobs. Audio mixes high-dimensional data with unnecessary and repetitive information. Sound waveforms have traditionally provided DL architectures with low-level and MFCC characteristics such as spectral shape descriptors and zero-crossing rate. These traits make computationally efficient and need less training data. DL models, large, well-labeled datasets, and easier processing capacity have reduced hand-designed feature dependence. Figure 1.5 shows the audio
