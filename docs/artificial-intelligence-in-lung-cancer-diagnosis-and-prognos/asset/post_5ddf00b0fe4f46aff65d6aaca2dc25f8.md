
# Huang et al.

# Seminars in Cancer Biology 89 (2023) 30-37

![](img/fbb3a28917ea7454539e81aa3e8afb3a_2_0.png)

Fig. 2. Application of AI in screening and detection of lung cancer. a. the relationship between AI, ML, DL, NLP, and various needs for lung cancer. b. the type and differences between machine learning and deep learning for lung cancer diagnostic applications [84], c. the concept of NLP techniques in EHR-based lung cancer data and comparison with traditional methods. AI: AI; NLP: Natural Language Processing; ML: Machine Learning; DL: Deep Learning Health Research methods for NLP. Fig. 2c illustrates a paradigm for the application of NLP techniques to medical data. Some researchers have been developed to train NLP models using clinical data from a wide range of centers. Kennedy et al. [16] demonstrated the feasibility of training natural language medical models that extract results from imaging reports of non-cell lung cancer patients and screening reports. [18] demonstrated the general feasibility of such method in medical records, and further assisted the association between NLP-driven clinical annotation and overall survival probability.

Gomez et al. confirmed consistency in the detection of lung nodules by NLP-recognized chest CT reports [17]. Another study found that NLP techniques were used to automatically classify quality assurance tools from radiology reports and thereafter. The transformer has emerged as a major algorithm in NLP. Agnila Khastraya et al. demonstrated the effectiveness of representation learning using the hybrid models of Bidirectional LSTM addressed the need for essential medical record features from electronic health records which generated the amount of training data required by most deep learning models [19]. Fei et al. proposed the first approach to Chinese radiology reports to improve the quality of reports. A bidirectional log or short memory with a random field based model was deployed to extract entities from lung cancer radiology reports. Key information related to follow-up recommendations were proposed based on malignant knowledge graphs and rule templates [20].

diagnosis. Recent advances are obtained for deep learning models for lung cancer image feature [21]. In recent, reinforcement learning has been widely employed to analyze lung cancer localization, segmentation and classification [22]. Deep learning models with reinforcement learning have emerged to create new models, such as deep Q-learning and deep networks, which have [24] representative-deep learning models for lung cancer detection and diagnosis. The common types of lung cancer and the main features of each type are unique. Deep reinforcement learning identifies different patients through the accurate location of tumours [25]. However, application of reinforcement learning models to lung cancer screening still faces many challenges. It is still unclear how to define an appropriate reward for updating the Q-value for each case.

# 3. Applications in lung cancer diagnostic

## 3.1. In lung node screening and detection

At present, a large number of lung nodules have been found in the physical examination. Although most of lung nodules are benign, there is still a high frequency of early lung nodules larger than 3 cm in diameter which have a high probability of malignancy [26,27]. It is necessary to emphasize on mapping lung nodules for transformation. However, to provide an early treatment, the clinicians can accurately distinguish benign and malignant lung nodules. After currently, many researchers and enterprises have invested resources for developing AI image analysis of lung cancer is an important part of computer-aided to assist physicians in lung screening nodules (32). Their inventions will help radiologists quickly locate nodules and provide diagnosis and treatment to reduce misdiagnosis and missed. Various applications of AI in lung screening and detection are summarized in Table 1.

Artificial intelligence-aided computer diagnosis (CAD) tools have been developed. CAD systems can help radiologists identify and locate missed nodules in the early stages of cancer (33). They can be used to evaluate the degree of malignancy and treatment prognosis, improving the clinical workflow (34). The available databases, which are used for the detection, classification and quantitative assessment of lung nodules, include Lung Data Consortium (LIDC)/Image Database Access Retrival (IDRI) and Early Lung Cancer Atlas (ELCAP) (35). The LIDC/IDRI provides an open reference for the medical research community as an important resource for promoting the development, validation, and translation of AI algorithms. These algorithms were developed and tested using data sets from LIDC/IDRI (37–39). A total of 6400 images were selected from 80 CT scans and 6 images were labeled by 4 radiologists (37). The CAD system developed in this study achieved fast segmentation through a fast segmentation mechanism using random forest (RF). We evaluated the sensitivity, specificity, and accuracy of the receiver operating characteristic (ROC) for the diagnosis of benign and malignant lung nodules. Compared with the support vector machine (SVM), our method reduce the false positive rate and achieve a higher AUC (40).

# Table 1
Application of AI in lung screening and detection.

| Year | Method | Sample size | Reference |
|---|---|---|---|
| 2018 | SVM-based model constructed a prediction by using SVM with CT radiomic features, achieved an accuracy of 84.6%, which was 12.8% higher than lung-Rads. | 72 PN (benign and malignant) | [73] |
| 2020 | FGD-PET/CT AI-based algorithm for detection and segmentation of lung nodules | 320 patients (histologically confirmed cases) | [74] |
| 2020 | AI algorithm tests detection and segmentation of nodules on digital radiographs | Baseline (TO) postors from 485 | [75] |
| 2021 | DL-based algorithm for detection and segmentation of lung nodules | 57 patients 982 images | [76] |
| 2021 | DL neural network for fusion of nodules to provide support for radiologists | 81 benign and malignant | [77] |
| 2022 | AI identifies significant factors for cardiogenesis and standard screening to decrease healthcare costs | 158 patients | [78] |
| 2022 | Adaboost-SVM-CNN has good accuracy for the detection of lung nodules and anticipate its potential | 1018 CT scans | [79] |

## 2.3. Reinforcement learning

X-ray tomography (CT) has been used for decades in the management of lung cancer, including screening, diagnosis and treatment. The quantitative value of CT for lung nodules has also been recognized. However, multiple lung nodules are still common in clinical practice (41–42). For lung nodules, different shapes and sizes may and affect the patterns of metastasis [36,43]. CT images of lung nodules are multi-dimensional images. 3D convolutional neural networks (CNN) can utilize the full spatial content of lung nodule detection, which can improve the accuracy of 2D CNN for lung nodules and reduce the false positive rate (44). The recent progression of CT in lung detection of automated 3-D tomography has been reported (34,45). These studies focus on the improvement of the detection accuracy and shapes of the different types of nodules detection capability. The work will able to build electronic medical record system and picture archive (46,47).

AI is used in the diagnosis of benign and malignant nodules. For lung nodules, CT analysis can accurately determine benign and malignant nodules (48). Regular shape, ground shadow, margin spin, and sign are important for the basis for the analysis. The study reported that the detection rate of true positives by CT nodules by professional clinicians was 66.5%, much lower than 98.4% by AI technology (49). There are risks of misdiagnosis and misdiagnoses in CT scans. Some nodules are also related to mimic small lung special nodules, resulting in missed diagnosis and misdiagnoses. However, AI can effectively detect small lung nodules and reduce missed diagnoses (59–51). The true positive diagnosis rate of AI-based SVM is significantly higher than that of professional physicians (52,53).

## 3.2. Application in classification and diagnosis of lung cancer

Lung cancer is divided into non-small cell lung cancer (NSCLC) and small cell lung cancer (SCLC). NSCLC accounts
