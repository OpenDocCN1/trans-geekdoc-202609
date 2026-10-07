
* Xin Wei

J. Zhang

Computers in Biology and Medicine 162 (2023) 107050

more directly the biochemical changes related to AD in the brain, these CSF components provide valuable information for AD detection.

Many studies are conducted in computer-aided diagnosis of AD. Only a small fraction of research utilizes multi-modal data, and even fewer studies cover multi-class diagnosis. Most studies differentiate AD from normal control (CN), while the MCI stage is ignored, and it is more critical to recognize the multi-class diagnosis of AD, MCI patients and healthy elderly. Biomarkers from different modalities can reflect changes connected with AD at various stages, providing comprehensive information for its diagnosis and further achieving more reliable results.

- 2. To exploit the complimentary interaction, a multi-modal module based on the cross-attention mechanism is introduced to learn the inter-correlations between CSF and PET components to enhance each other AD diagnosis.

- 3. To avoid the discrepancy of modalities between multi-modal data and the performance of AD diagnosis, an objective function including modality alignment and classification loss is designed to bridge the heterogeneity between different modalities and optimize the classification performance.

- 4. We evaluate the effectiveness of the approach using multi-modal data in the public dataset ADNI, with results demonstrating that MCAD achieves promising performance over existing methods in AD-associated tasks. The evaluation capturing interactions could provide critical evidence for AD diagnosis.

[14–17]. Although the previous approaches have been proven effective, there remain still some challenges in AD diagnosis based on multi-class data. First, although multi-class methods are an important component of modality learning, which is cross-modal interaction. These methods combine information from different modality by concatenating features from different modality, yet not optimal for exploiting the complimentary information across modalities. Second, the modality variation caused by different modalities, which greatly affects the feature and diagnosis of AD, especially the multi-class nature of AD, needs to be addressed. There are up to least three key challenges for AD diagnosis in multi-class data, (1) when considering different AD-related scenarios, including two-class classification; (2) how to exploit the interaction between modalities to better play their complementary role; (3) to reduce the discrepancy between modalities.

To address the issues above, we propose a multi-class framework for diagnosis of AD/MCI using multi-modal data, including CSF, PET, and GF. The framework maintains two sets of encoders for both imaging and non-imaging data, multi-modal interaction (MI) module and classification module. In this framework, an encoder is designed to extract features from different modality respectively. For example, the CSF component is embedded to the non-imaging data effectively. Due to the size of brain regions affected by disease in brain data and different modality, each encoder extracts features with the corresponding receptive field without losing information. Then, we introduce a multi-modal interaction module, which takes advantage of cross-modal attention to integrate modalities (CSF, PET and GF) and fusion them. Finally, an objective function is designed to minimize the discrepancy between representations for multi-modal data to guide AD diagnosis. The classification task includes AD two-class classification (AD vs. CN), MCI two-class classification (MCI vs. CN), and multi-class classification.

The main contributions of this study are summarized as follows

- 1. We propose a novel framework MCAD that can be leveraged to learn complementary information from different modalities for AD diagnosis more efficiently and accurately. And we study for various scenarios including AD-related two-class and multi-class classification.

## 2. Related work

We review previous studies on AD diagnosis, particularly multi-modal biomarkers, which are categorized into two groups: 1, machine learning approaches [16–20], and deep learning approaches [21–26].

Many studies [19] demonstrate the effectiveness of biomarker based learning approaches in AD diagnosis, which are includes two parts feature extraction and classification. For instance, Lin et al. [16] used multi-modal data (MRI, PET, and CSF) to classify MRI, PET, GF, and genes. The others indicated the disease prediction, enrolling multi-class diagnosis of AD. W. Waldhof et al. [17] developed logistic regression to the AD diagnosis using MRI and PET data for classification and at the same time markers which are significant to dementia cognition. Kahn et al. [29] applied the machine learning classifier to classify the features from brain image and genetic data. The association of filter and feature for selection to achieve AD diagnosis using multiple biomarkers, which enhanced the diagnostics accuracy.

In recent years, deep learning has made outstanding efforts employing convolutional networks (CNN) to learn features. With the rapid development of CNN, various neural networks are employed to provide a variety of ideas for AD diagnosis. For classification performance, deep learning has shown potential through various techniques [22,23,31]. Many methods are based on neuraisism, such as AD, MRI, PET and GF functional magnetic resonance (MRI) for AD diagnosis, [23,25–27,39], which CNN is used to extract high-level image representations to capture the complexity of manual feature extraction. The existing image representation methods can be categorized into four groups based on the type of input (pixel-level, methods-level, and decision-level methods). Researchers consider adding different modality data, such as clinical and biological biomarkers, implying representations for fusion to achieve the more accurate comprehensive diagnosis. For example, Spasov et al. [17] employed a multi-modal AD classification

J. Zhang et al.

Computers in Biology and Medicine 162 (2023) 107050

![](img/35eb289ac20da6b2112bd8090073aee2_2_0.png)

Fig. 1. The illustration of data scales of the dataset.

framework based on the 3D surface and grouped convolutions that make SMRI and clinical analysis and generic measures as inputs. Xu et al. [40] proposed an interpreted learning network that extracts discriminant features from multi-modal data of sMRI, age, gender, and class labels. Pan et al. [23] included multiform features from sMRI with the registration-class AD classification. Again, Tong et al. [41] presented a non-graph fusion framework that efficiently simplified the fusion between SMRI, CSF and PET for AD classification with performance of 60.2%. Li et al. [42] proposed a multi-class task with AD diagnosis and clinical score regression, using sMRI and demographic information using CNN-based attention mechanisms.

Table 1
Summary of demographics and clinical scores

| Diagnosis | Subjects | Scans | Age | MMSE | CDR-SB |
|---|---|---|---|---|---|
| CN | 110 | 156 | 72.7(09) | 29.12(10) | 0.90(39) |
| MCI | 125 | 158 | 71.86(73) | 22.32(30) | 1.4(14) |
| AD | 129 | 157 | 73.7(77) | 18.5(05) | 4.82(02) |
