
Chapter 9 illustrates the basic principles for Parkinson’s disease (PD) detection using ML algorithms and provides a survey of AI-based PD identification. The chapter reviews various feature extension and reduction methods to find reliable solutions for detecting PD in its early stages.

Chapter 10 reviews several commonly used breast cancer datasets. It also provides an overview of the efficacy of several DL architectures for breast cancer screening. The chapter helps us to realize the current developments in DL approaches for breast tumor diagnosis.

Chapter 11 explains the working principles of digital pathology based on the WSI system. It illustrates how the application of image processing and AI extracts meaningful insights that are largely beyond the scope of traditional pathology, which eventually leads to precise disease diagnosis and improved patient care.

Chapter 12 provides an overview of how ML and DL techniques can be applied to extract various features related to diabetes mellitus and exploit them for early prediction and management of diabetes in a cost-effective way. This early warning mechanism can aid in the prevention of the disorder by taking appropriate measures and, at minimum, to reduce the severity of the disease and prolong its onset.

Chapter 13 describes how IoT and DL can be applied to assist physicians and radiologists in remotely diagnosing skin lesions. In addition, the chapter explains the importance of trustworthy applications via a demonstration of cloud-based computer-assisted diagnosis.

Chapter 14 presents an automated facemask detection scheme in a real-time video stream. The technique uses a deep convolutional neural network (DCNN)-based transfer learning approach. The experimental results suggest that the proposed framework can be advantageous in public health management during the crisis in COVID-19-like pandemics.

Chapter 15 illustrates the importance of wireless technologies to fulfill the requirements of AI-enabled medical systems in the era of 5G and beyond. Furthermore, it explains how we can protect wireless health systems and networks from external adversaries and internal intruders with respect to the wireless body area network (WBAN).

Chapter 16 presents the AI-based security and privacy solutions for physiological data protection following an end-to-end signal flow. It highlights the shortcomings of the associated ML approaches and provides some indications of overcoming the identified weaknesses.

Finally, in Chapter 17, we provide a short overview of the future challenges in AI for disease diagnosis and prognosis.

## Bibliography

- 1. S. M. R. Islam, D. Kwak, M. H. Kabir, M. Hossain, and K.-S. Kwak, “The internet of things for health care: a comprehensive survey,” IEEE Access, vol. 3, pp. 678–708, 2015.

- 2. F. Ali, S. M. R. Islam, D. Kwak, P. Khan, N. Ullah, S.-j. Yoo, and K. S. Kwak, “Type-2 fuzzy ontology-aided recommendation systems for IoT-based healthcare,” Computer Communications, vol. 119, pp. 138–155, 2018.

- 3. S. K. Saha, S. M. R. Islam, K.-S. Kwak, M. Rahman, S.-G. Cho, F. Ali, “Prom1 and prom2 expression differentially modulates clinical prognosis of cancer: a multiomics analysis,” Cancer Gene Therapy, vol. 27, no. 3, pp. 147–167, 2020.

- 4. P. Khan, M. F. Kader, S. M. R. Islam, A. B. Rahman, M. S. Kamal, M. U. Toha, and K.-S. Kwak, “Machine learning and deep learning approaches for brain disease diagnosis: principles and recent advances,” IEEE Access, vol. 9, pp. 37622–37655, 2021.

- 5. S. Kaur, J. Singla, L. Nkenyereye, S. Jha, D. Prashar, G. P. Joshi, S. El-Sappagh, M. S. Islam, and S. M. R. Islam, “Medical diagnostic systems using artificial intelligence (AI) algorithms: principles and perspectives,” IEEE Access, vol. 8, pp. 228049–228069, 2020.

- 6. N. El-Rashidy, S. El-Sappagh, S. M. R. Islam, H. M. El-Bakry, and S. Abdelrazek, “End-to-end deep learning framework for coronavirus (COVID-19) detection and monitoring,” Electronics, vol. 9, no. 9, p. 1439, 2020.

![](img/bffdb4a72252285ac92f0fad78a7f104_20_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Machine Learning for Disease Assessment

Sujay Saha

Department of Electrical and Electronic Engineering, University of Dhaka

Shekh Mahmudul Islam

Department of Electrical and Electronic Engineering, University of Dhaka

## CONTENTS

- 2.1 Introduction .................................................................................... 8
- 2.1.1 Methodology for Disease Assessment ........................................... 9
- 2.1.2 Dataset and Model Description ................................................... 12
- 2.2 Machine Learning Algorithms ........................................................... 13
- 2.2.1 Supervised Learning ..................................................................... 13
- 2.2.2 Unsupervised Learning ................................................................. 21
- 2.2.3 Other Methods ............................................................................. 24
- 2.3 Disease-Risk Prediction ................................................................... 29
- 2.4 Evaluation Methods ........................................................................... 30
- 2.5 Applications in Real-Life Scenarios .................................................. 31
- 2.6 Conclusion ......................................................................................... 33

MACHINE LEARNING (ML) has attracted significant interest toward developing smart healthcare systems by providing intelligent clinical decision making especially on disease assessment and its associated risk prediction. At present, many diseases need to be identified at early stages to prevent the associated risk which can also play an important role in smart digital healthcare interventions. When ML is applied to clinical data it tries to interpret the data to suggest the best action that needs to be performed to improve the individual’s health. However, there remain significant challenges to incorporate the ML-based approach in a real-world setting such as performance between trained model and computational time, and so on. This chapter focuses on discussing the basics of the methodology of the ML approach for disease assessment and it also highlights different assessment aspects. Additionally, it will also discuss different disease detection and assessment-related application areas of the ML-based approach and its associated pros and cons. It will also elucidate different challenges of this approach and potential solutions to bring this ML approach in real-world settings for the benefit of humanity.

### 2.1 INTRODUCTION

In the modern world, the number of incurable and deadly diseases is increasing rapidly even though there is a significant advancement in the medical field [5]. For the betterment of human health incurable and deadly diseases need to be identified at their early stage. Therefore, there is a need for analyzing medical data and images in a minimum amount of time with greater accuracy. Analyzing medical data with greater efficiency can also help to predict and detect the disease promptly. Implementing and designing new effective algorithms for processing medical data is always challenging as decision-making from medical data is difficult due to the complex nature of the medical data. Additionally, processing large medical data requires a huge amount of time as a huge amount of data needs to be processed for decision making. In the healthcare field, starting from information from medical data and then for disease diagnosis machine learning (ML) is gaining attention and has significant progress.

ML is being applied in different techniques and algorithms in various healthcare activities [3]. For clinical decision-making, machine learning is being mostly employed. When ML is applied to medical data, then the learning model can interpret the data to suggest the best actions that need to be performed to improve an individual's health. In general, the ML model needs to learn the problem statement and the quality of the data is also important for decision making [5]. In general, the ML model is not very strong and concrete when it is first used but with repetition, it gains experience from the previous iterations. Additionally, the learning model can also become robust and automated with the previous training experience. There are two ways that clinical decision-making is performed by comparing the previous knowledge that is included in the dataset. The first one is based on intuition on the underlying pattern of the medical dataset and is mostly used in medical emergencies. Another approach is a slow and reasoned approach where a large medical dataset is used to train the learning model. The second approach is more accurate but it takes a little bit more time as a large dataset needs to be handled to train the learning model. With the advancement of the processing power of computing devices, a reasoned approach is being used in the healthcare sector to improve quality.

Artificial intelligence (AI) is a branch of computer science where the intelligence of the machine is being integrated to perform any task. ML is a subset of AI and it is training algorithms for decision making. ML is being used in different areas of healthcare where the goal to integrate ML is to interpret the medical data in a meaningful way for the prediction and assessment of a disease [6]. ML models are being used in different areas such as heart disease prediction, type 2 diabetes risk prediction, and so on [6]. ML model is trying to bring a paradigm shift to healthcare due to the rapid progress of the analytical technique [6]. Most recently, the world is undergoing unprecedented challenges due to the COVID pandemic [4]. Different researchers are also trying to integrate AI and ML models for predicting the risk factor of COVID-19 infected patients [2]. For disease assessment, it is not always about detecting or predicting disease but it covers the broader spectrum including medical treatment research, public healthcare policy-making, patient care, hospital
