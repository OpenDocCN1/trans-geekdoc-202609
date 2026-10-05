# Role of AI & ML in lung disease detection

| Training data | | Lung sound dataset | Testing data | | Abnormal sound detection (ASD) | 2 classes: normal/abnormal | Multi-classes: normal, crackle, wheeze, ... |
|---|---|---|---|---|---|---||
| Preprocessing | Feature extraction | Deep model | Output | Respiratory disease recognition (RDR) | Associated with |
| ● Noise reduction | ● Hardcraft feature | ● FNN | | ● 2 classes: health/disease | 3 classes: chronic disease recognition |
| ● Heart sound separation | ● Deep feature | ● CNN | | ● Multi-types: health, COPD, asthma, .. |
| | | ● RNN | | | Multi-classes: risk, improve, recovery, ..

Figure 1.2 Deep lung sound analysis.

# 1.3.6.1 System framework

Listening skills impact the doctor's' lung sound interpretations and clinical auscultation findings. By clinical findings, clinicians may misdiagnose patients. Clinicians advocate SVM, CNN, and random under-sampling boosting for lung disease data [103,104,105,106]. Most shallow ML-based lung sound analysis methods have 80% accuracy and were tested on few participants [107,108,109].

DL beats ML in lung sound accuracy and robustness [110]. They may boost performance. DL algorithms can automatically uncover task-relevant features without human feature extracting raw data. RNNs are utilized for lung sound analysis in extracting disease-related periodic oscillations. Transfer learning: DL methods may use common knowledge from adjacent areas like Audio Set [111], a large audio dataset, to enhance lung sound analysis and minimize training. Planning problems limit clinical data, making it vital for clinical applications.

DL lung sound investigations often include data collection, preprocessing, feature extraction, and classification. Digital stethoscopes listen to lungs. Preprocessing lung sounds reduces noise. For lung sound discrimination, feature extraction reduces high-dimensional preprocessed data. Disease classifiers map attributes and classifications.

# 1.4 PROPOSED METHODOLOGY

The main approach of the DL model used to classify lung sounds and illnesses is explained in Figure 1.3. Mel-frequency cepstral coefficients, or MFCC for short, are often used in audio signal processing to extract features from lung sounds that are present in datasets. As seen in Figure 1.4, the generated feature matrix is divided into training and testing sets and supplied to the DL model, respectively, yielding, the categorization of lung diseases and an analysis of lung sound. There are four possible classifications for lung sounds: crackles, wheezes, both crackles and wheezes, and