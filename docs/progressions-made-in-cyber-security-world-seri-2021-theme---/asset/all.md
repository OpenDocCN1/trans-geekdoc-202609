![](images/coverpage.jpg)

﻿ ![Cover: Progressions Made in Cyber-Security World, “SERI-2021” Theme – “Cryptography, Applied Cryptography, Cyber Security and Privacy”, edited by D. Nethra Pingala Suthishni, S. Asha and A. Roshni, published by CRC Press, Taylor and Francis Group](images/coverpage.jpg)

﻿ 

﻿ 

First edition published 2022

by CRC Press

 2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

and by CRC Press

 6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

© 2022 selection and editorial matter, G. Padmavathi et. al.; individual chapters, the contributors

*CRC Press is an imprint of Informa UK Limited*

The right of D. Nethra Pingala Suthishni et. al. to be identified as the authors of the editorial material, and of the authors for their individual chapters, has been asserted in accordance with sections 77 and 78 of the Copyright, Designs and Patents Act 1988.

All rights reserved. No part of this book may be reprinted or reproduced or utilised in any form or by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying and recording, or in any information storage or retrieval system, without permission in writing from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice:* Product or corporate names may be trademarks or registered trademarks, and are used only for identification and explanation without intent to infringe.

*British Library Cataloguing-in-Publication Data*

A catalogue record for this book is available from the British Library

*Library of Congress Cataloging-in-Publication Data*

A catalogue entry has been requested.

ISBN: 978-1-003-30238-4 (ebk)

DOI: 10.201/9781003302384

﻿ 

﻿ 

# Preface

SERI-2021 was a success with the presence of our valuable Guest Speakers who lead the discussion in various session in just the right direction showering the audiences with their esteemed valuable knowledge and insights in the field. The various sessions we had such as “Quad: Cyber security capabilities”, “National Interventions and Programs for Security Education”, “Cyber First: This and next generation”, “Crypto: Releasing possibilities” etc. not only focussed on the present scenario but also defined the futuristic scope of in the filed of cyber-security. The Conference had an interesting competition judged by the top scholarly of cyber-security field as Paper-Presentation which saw number of entries and few finally making it to the top. This book has the top 3 papers presented. Hope you will enjoy surfing through new interventions in the field.

# Detection of Malicious Insider in Cloud Environment based on behavior Analysis

**Padmavathi G**

Department of Computer Science Avinashilingam Institute for Home Science and Higher Education for Women Coimbatore, Tamilnadu, India [padmavathi\_cs@avinuty.ac.in](mailto:padmavathi_cs@avinuty.ac.in)

**Shanmugapriya D**

Department of Information Technology Avinashilingam Institute for Home Science and Higher Education for Women Coimbatore, Tamilnadu, India [shanmugapriya\_it@avinuty.ac.in](mailto:shanmugapriya_it@avinuty.ac.in)

**Asha S**

Department of Computer Science Avinashilingam Institute for Home Science and Higher Education for Women Coimbatore, Tamilnadu, India [20phcsf005@avinuty.ac.in](mailto:20phcsf005@avinuty.ac.in)

**Abstract:** *Insider threat is one of the most stimulating security threats in an organization that possesses sensitive information. In an organization, detecting malicious insider threats is more challenging due to the behavioral changes of malicious insider. To avoid the sensitive information leakage that causes enormous loss, detecting the malicious insider within an organization is necessary. The principal focus of this paper is to find the user’s unauthorized activity by analyzing their behavior on website i.e., websearch analysis. To find the user’s unauthorized activity by analyzing each user’s behaviour, such as the website activity of each individual. The user is classified as a genuine user or malicious userbased on user’s websearch behavior. This paper proposes an insider threat detection framework to analyze and detect the malicious insider threat within an organization using user’s statistical behavior analysis.*

**Keywords:** Insider threat detection, behavior analysis, Malicious Insider.

## I. INTRODUCTION

In the rapidly developing world, all business organizations and the corporate sector recommend and enhance the business by possessing the Internet-as-a-solution. Cloud computing is a framework that accomplishes rapid provisioning on-demand charge restricted self-service resources to its user over the Internet. The migration of an organization to the cloud faces some severe threats due to its changing environment. One of the most challenging security threats faced by an organization is Malicious insider or an authorized individual employee who attempts to gain access to confidential information. Recent reports show that 53% of organizations and 42% of U.S. federal agencies suffer from insider threats every year \[[1](#06_ch1.xhtml#r1_1)\]. Insider threat-related activities can be carried out intentionally, such as information system sabotage, intellectual property theft, and disclosure of classified information, as well as unintentionally, such as careless use of computing resources \[1\]. The primary goal of malicious insiders is to cause economic and reputation loss by leaking sensitive data to the competitive organization. So, it is significant to detect the malicious insiderthreat in an organization. one of the way for detecting the malicious insider is by analysing the behavior of the user. This paper proposes the detection of malicious insider activity using behavior analysis. This paper aims to explore the insider data using the logging behavior of employees within the organization. The entire paper is organized into four sections. Section II tabulates the literature study on malicious insider detection method. Section III explains the overview of proposed methodology. Section IV discusses the obtained result. Section V concludes with possible scope for future enhancement.

## II. Literature Review

The primary concern is to analyze the CERT data to detect the malicious insiders using logging behavior analysis. [Table I](#06_ch1.xhtml#t1_1) describes the work done in the field of various Insider Threat detection frameworks.

[**Table 1**](#06_ch1.xhtml#t1_1b) Literature Review

 
| S.no || Author || Insider Threat Detection Framework applied || Algorithms applied || Observations |
| --- | --- | --- | --- | --- |
| 1. || Jiang et al. (2018) || User Behavior Analysis || XGBoost, SVM, Random Forest (RF) || User behaviour analysis using XGBoost outperforms other algorithms based on F-measure up to 99.96% to detect the malicious activity using CERT dataset \[5\] |
| --- | --- | --- | --- | --- |
| 2. || Eberle and Holder (2009) || Graph based anomaly detection || GBAD-MDL, GBAD-P (probability) and GBAD-MPS (maximum partial substructure) || Graph-based anomaly detection using MDL algorithm identifies the graph-based anomalies such as email, phone traffic and business process to detect the insider threat than Probability and MPS algorithm \[6\] |
| 3. || Liu and et. (2018) || Anomaly- based Insider detection || Deep Autoencoder (AE) || Deep A.E. detects all malicious insider activity with a reasonable false positive rate using US-CERT data \[7\] |
| 4. || Diop and et. (2019) || Ensemble Learning Behavior Anomaly Detection Framework || (Forest, One-Class SVM, Local outlier factor (LOF), Elliptic envelope (EE), artificial neural network (ANN), Gaussian naive Bayes (Gnb), Bagging classifiers (Bgc), random forest (RF) and gradient boosting (Gbc) || Ensemble learning behavior using Gbc algorithm outperforms other algorithms with (75%-99%) in both unsupervised learning based testing and supervised learning based testing. An ANN followed this with (60%-99%) result in both tests \[8\]. |
| 5. || Jiang et al. (2019) || Graph Convolutional Network || RF, SVM, Logistic Regression (LR), Convolutional Neural Network (CNN), Graph Convolutional Network (GCN) || GCN performs better than other algorithm based on accuracy, precision and recall to detect malicious insider and fraud activities \[9\]. |
| 6. || Kim et al. (2019) || User Behavior Modeling and Anomaly Detection Algorithms || Gaussian density estimation, Parzen window density, Principal component || User behavior modelling and anomaly detection using Parzen and PCA provided a better result than other algorithms to detect malicious insider threats \[10\]. |
| 7. || Senator et al. (2013) || Detecting Insider Threats in a Real Corporate Database || IP Thief Ambitious Leader Scenario Detector, File Events Indicator Anomaly Detection, Relational Pseudo Anomaly Detection, Repeated Impossible Discrimination Ensemble, Grid- based Fast Anomaly Discovery given Duplicates (GFADD) || The multiple methods detect the malicious insider threat using computer log activity in an actual corporate database \[11\]. |
| 8. || Lv et al. || Method based on user and role behavior (MURB) and Anomaly Detection (ADAD) || Isolation Forest || MURB outperforms the ADAD with 80% precision and accuracy for detection of the malicious insider threat using CERT data \[12\]. |
| 9. || Gamachchi and et. (2017) || Graph and anomaly detection Framework || Isolation Forest || The combined graph-based anomaly detection framework identifies 79% of individuals as Genuine users and 31% as malicious insiders with suspicious activity \[13\]. |
| 10. || Liu et al. (2020) || Behaviour analysis || Behaviour analysis || The new behaviour analysis framework named Doc2vec simplifies insider threat detection based on spatial and temporal metrics \[14\]. |
| 11. || Le and Heywood (2021) || Anomaly Detection for Insider Threats Using Unsupervised Ensembles || AutoEncoder, Isolation Forest, Lightweight on-line detector of anomalies (LODA), Local Outlier Factor (LOF) || Unsupervised ensemble-based anomaly detection using Autoencoder outperforms the other algorithm based on voting metrics to detect the malicious insider threat \[15\]. |
| 12. || Legg (2015) || Behavior based malicious insider threat detection || Visual Analytics || Visual analytics is recommended to detect malicious insider threat activity based on profiling behaviour and selected features as a mitigation strategy \[16\]. |

The above table shows that the various types of insider threat framework utilize different user behavior modelling technique to detect the malicious insider. Hence, the behavior analysis is implemented to improve the precise detection of a malicious insider in an organization.

## III. METHODOLOGY

The following [Fig. 1](#06_ch1.xhtml#f1_1) shows the proposed malicious insider threat framework methodology using behavior analysis to detect a malicious insider threat in an organization.

### A. Dataset

Data can be obtained from the monitoring process of the organization, where different log files, such as email and weblogs, firewall logs, network traffic captures, and different types of user records are common \[[2](#06_ch1.xhtml#r1_2)\]. The publicly available dataset gathered from U.S. based Computer Emergency Response Team (US-CERT) is used. It consists of information regarding both malicious insider and genuine user activity. This dataset has been collected from [https://kilthub.cmu.edu/articles/dataset/](https://www.kilthub.cmu.edu) Insider Threat Test Dataset/12841247/1\[2\]. The above dataset contains the activity information of individual employees in an organization. It comprises the following data input: (i) user activity log data such as web URL, email, file, access log, and removable device connectivity records. It is dynamic and used for the behavior analysis of users. (ii) Structure and information of user and organization. It is considered as meta information for data analysis. For example, Lightweight Directory Access Protocol (LDAP) is considered as metadata in CERT data.

![Fig. 1 Methodology Overview](images/page4_1_B.jpg)

[**Fig. 1**](#06_ch1.xhtml#f1_1b) Methodology Overview

In CERT data, the log information of malicious and non-malicious activity is given based on the threat scenario mentioned below.

*   Scenario 1: An individual in an organization works after working hours, carries a removable drive and uploads sensitive information to the unauthorized website such as wikileaks.org. Tries to resign from the organization.
*   Scenario 2: An individual in an organization visits a job portal website and explores the employment opportunities of a business competitor. An individual’s anomalous activity increases the use of a removable device. Resigns the organization in future.
*   Scenario 3: Unauthenticated administrator attempts to use unauthorized software to collect sensitive credentials, utilizes the removable device to get sensitive information and tries to access the secure system. Later email the critical information and resigns from the organization.
*   Scenario 4: Over three months, an individual often logs in, searches, and forwards sensitive information from other users’ computers to personal email addresses.
*   Scenario 5: Uploads sensitive information such as documents to Dropbox for personal gain.

Based on the dataset version, the particular scenario is used. The proposed methodology uses the dataset version r3.1. It satisfies the scenario 1 and scenario 2 from the above-mentioned scenarios for further processing.

### B. Data pre-processing

The primary CERT data contains log details of 516 days, where 4000 users generate 135,117,169 log events. The events are activity including email-based, login-based, device storage-based, HTTP operations, psychometric details, file information and daily log details \[[3](#06_ch1.xhtml#r1_3)\]. The above mentioned five scenarios apply scenario-1 and scenario-2 related malicious insider threat data in this research. Other information is ignored. The selected data undertakes three pre-processing steps to make the data suitable for insider detection. It includes data integration, data transformation and data level sampling.

1.  *Data Integration:* The malicious and non-malicious activity information that satisfies the selected scenario are gathered from device connectivity, login status and website operation for detection of malicious insider threat. A simple feature concatenation technique is used to integrate the selected records. [Table II](#06_ch1.xhtml#t1_2) demonstrates the details of integrated data. 
    
    [**Table II.**](#06_ch1.xhtml#t1_2b) Integrated Data
    
     
    | S.no || Feature name || Explanation |
    | --- | --- | --- |
    | 1. || InsiderThreat || Malicious activity or not |
    | --- | --- | --- |
    | 2. || Vector || origin of data (HTTP/logon/device) |
    | 3. || date || Date |
    | 4. || User || The user id of an employee |
    | 5. || Pc || Unique identification for each computer |
    | 6. || Activity || Actual activity of an employee in the pc |
    
2.  *Data Transformation:* The integrated data requires data transformation to encode the absolute value for further processing. The features, namely ‘vector’, ‘pc’, ‘user’ and ‘activity’ from integrated data is converted into a numerical value. The value of ‘date’ is converted into a number of epochs. [Table III](#06_ch1.xhtml#t1_3) shows the encoded data. 
    
    [**Table III.**](#06_ch1.xhtml#t1_3b) Encoded data
    
     
    | S.no || Feature || Before Encoding || After Encoding |
    | --- | --- | --- | --- |
    |  || InsiderThreat || Numerical || Numerical |
    | --- | --- | --- | --- |
    |  || Vector || Categorical || Numerical |
    |  || date || Timestamp || Number of epochs |
    |  || User || Categorical || Numerical |
    |  || Pc || Categorical || Numerical |
    |  || Activity || Categorical || Numerical |
    
3.  *Data Level Sampling:* Jia et al. (2014) had proposed the solution at the data level for the class imbalance problem is based on sampling methods \[[4](#06_ch1.xhtml#r1_4)\]. It is accomplished using the undersampling technique such as Near-Miss 2. In Near-Miss 2 algorithm, the instance of the majority class was selected if it satisfies the average distance for N outermost instance of a minority class is minimum. In the pre-processed dataset, a feature named ‘InsiderThreat’ is selected as the target variable where class 0 is majority class non-malicious event and class 1 is minority class malicious event. After resampling, the majority class instance 0 is restructured and equals the minority class instance 1. [Table IV](#06_ch1.xhtml#t1_4) shows the sampled data. 
    
    [**Table IV.**](#06_ch1.xhtml#t1_4b) Sampled Data
    
     
    | S.no || Training set || Before Sampling || After Sampling |
    | --- | --- | --- | --- |
    | 1. || Non-Malicious Majority class instance || (0, 39732) || (0, 268) |
    | --- | --- | --- | --- |
    | 2. || Malicious Minority class instance || (1, 268) || (1, 268) |
    

### C. Logging Behavioral Analysis

The behavior of each individual in an organization needs to be analyzed to detect the malicious insider threat. Logging behavior analysis using pre-processed data is used to get more insight into the activity of each individual in an organization. Based on the selected scenario, the visited website of each individual is analyzed to identify the malicious user behavior. It is accomplished by analyzing website activity to detect malicious activity. Website activity behavior is an efficient way to collect sensitive evidence from the organization. The website behavior comprises visited website URLs for each individual. Based on the selected scenario, unauthorized access such as [www.wikileaks](http://www.wikileaks). org and job-related websites is considered an unauthorized malicious activity. Others are considered non-malicious activity. It further conducts an in-depth analysis of user website behavior to detect malicious activity.

## IV. RESULTS AND DISCUSSIONS

The following [Fig. 2](#06_ch1.xhtml#f1_2) demonstrates the activity count of genuine users and malicious users using pre-processed data. From the [Fig. 2](#06_ch1.xhtml#f1_2), it is observed that the activity of the genuine user (0) is comparatively less than 10 activities per month. In comparison, the total activity count of the malicious user ([1](#06_ch1.xhtml#r1_1)) is more than 70 activities per month. Hence, the activity of the malicious user is increasingly high than the average genuine user, and it is required to detect the user who possesses the malicious activity. The users who visit unauthorized websites are categorized as “Malicious” and others as “Non-Malicious”. It is required to find the total number of unique activities of each individual in a particular personal computer (pc) for both malicious and genuine users.

![Fig. 2 Activity Count of Genuine User and Malicious User](images/page7_1_B.jpg)

[**Fig. 2**](#06_ch1.xhtml#f1_2b) Activity Count of Genuine User and Malicious User

The following [Fig. 3](#06_ch1.xhtml#f1_3) visualize the total number of activity counts for both malicious and genuine users. The non-malicious insider may possess the malicious activity. So, categorize the user based on malicious activity to foresee the user activity in [Fig. 4](#06_ch1.xhtml#f1_4).

![Fig. 3 Total Number of Activity Count for each User](images/page7_2_B.jpg)

[**Fig. 3**](#06_ch1.xhtml#f1_3b) Total Number of Activity Count for each User

It pinpoints user’s activity based on the frequency of various visited URLs using a particular device. [Fig. 4](#06_ch1.xhtml#f1_4) shows that user 162 is an insider who visits the job-related website, namely, [http://lockheedmartinjobs.com](http://lockheedmartinjobs.com) for 13 times and frequently uses the removable device for connection and disconnection. This is categorized as a malicious insider that satisfies scenario-2 based rule. User 221 is an insider who visits the unauthorized website, namely [http://wikileaks.org](http://wikileaks.org) for 2 times and is categorized as a malicious insider based on scenario-1 based rule.

![Fig. 4 Total Number of Activity Count for each User Based on Category](images/page7_3_B.jpg)

[**Fig. 4**](#06_ch1.xhtml#f1_4b) Total Number of Activity Count for each User Based on Category

The following [Fig. 5](#06_ch1.xhtml#f1_5) explains the personal computer used by a malicious user. i.e., user 162 uses the pc, namely 45, to perform the malicious activity. User 221 uses the pc, namely 403, to perform the malicious activity. By converting the numerical value into categorical value, the user id is retrieved. Hence, user CCH0959 and CSF0929 is considered a malicious insider who visits the unauthorized website and performs the malicious activity.

![Fig. 5 Personal Computer used by Malicious User](images/page7_4_B.jpg)

[**Fig. 5**](#06_ch1.xhtml#f1_5b) Personal Computer used by Malicious User

**Table V.** Information of Malicious Insider

 
| User id || Name || Email || Roles || Department || Supervisor |
| --- | --- | --- | --- | --- | --- |
| CCH0959 || Cedric Cyrus Harrison || [Cedric.Cyrus.Harrison@dtaa.com](mailto:Cedric.Cyrus.Harrison@dtaa.com) || Industrial Engineer || 1– Industrial Engineering || Desiree Claudia Booth |
| --- | --- | --- | --- | --- | --- |
| CSF0929 || Chaney Sean Fuentes || [Chaney.Sean.Fuentes@dtaa.com](mailto:Chaney.Sean.Fuentes@dtaa.com) || Production Line Worker || 3- Assembly || Theodore Upton Barry |

Table V demonstrates the company profile of malicious insiders from LDAP. It shows that the user CCH0959 is Cedric Cyrus Harrison, an Industrial Engineer from the Industrial Engineering department who is considered a malicious insider based on scenario-2. The user CSF0929 is Chaney Sean Fuentes, a Production Line Worker from Assembly Department considered a malicious insider based on scenario-1.

## V. CONCLUSION AND FUTURE ENHANCEMENT

In this proposed research paper, the logging behavior analysis is implemented using pre-processed insider threat data to detect the malicious insider threat in an organization. The user who visits the unauthorized data leak websites and job-related websites are considered malicious insiders based on scenario-1 and scenario-2. The predicted malicious insider who possesses malicious activity is correctly detected. It pinpoints the basic information of malicious insiders from LDAP to further mitigate such activity that could happen in the cloud environment. It is highly beneficial in real-time insider threat detection. In future, the graph-based behavior analysis using deep learning can be proposed to detect the malicious insider threat.

1.  This work is supported by the Centre for Cyber Intelligence (CCI), DST-CURIE-AI-Phase II Project, Avinashilingam Institute for Home Science and Higher Education for Women. Coimbatore. Tamil nadu, India.

## REFERENCES

1.  [Collins, M.](#06_ch1.xhtml#r_r1_1) Common sense guide to mitigating insider threats. CARNEGIE-MELLON UNIV PITTSBURGH PA PITTSBURGH United States, 2016.
2.  [Glasser, J., and Lindauer, B.](#06_ch1.xhtml#r_r1_2) 2013. Bridging the gap: A pragmatic approach to generating insider threat data. In 2013 IEEE Security and Privacy Workshops, pp. 98–104. IEEE.
3.  [Meng, F., Lou, F., Fu, Y., and Tian, Z.](#06_ch1.xhtml#r_r1_3) 2018. Deep learning based attribute classification insider threat detection for data security. In 2018 IEEE Third International Conference on Data Science in Cyberspace (DSC), pp. 576–581. IEEE.
4.  [Pengfei, J., Chunkai, Z., and Zhenyu, H.](#06_ch1.xhtml#r_r1_4) 2014. A new sampling approach for classification of imbalanced data sets with high density. In 2014 International Conference on Big Data and Smart Computing (BIGCOMP), pp. 217–222. IEEE.
5.  Jiang, W., Tian, Y., Liu, W., and Liu, W. 2018. An Insider Threat Detection Method Based on User Behavior Analysis. In International Conference on Intelligent Information Processing, pp. 421–429. Springer, Cham.
6.  Eberle, W., and Holder, L. 2009. Applying graph-based anomaly detection approaches to the discovery of insider threats. In 2009 IEEE International Conference on Intelligence and Security Informatics, pp. 206–208. IEEE.
7.  Liu, L., De Vel, O., Chen, C., Zhang, J., and Xiang, Y. 2018. Anomaly-based insider threat detection using deep autoencoders. In 2018 IEEE International Conference on Data Mining Workshops (ICDMW), pp. 39–48. IEEE.
8.  Diop, A., Emad, N., Winter, T., and Hilia, M.. 2019. Design of an Ensemble Learning Behavior Anomaly Detection Framework. International Journal of Computer and Information Engineering *13*, 10: 547–555.
9.  Jiang, J., Chen, J., Gu, T., et al. 2019. Anomaly detection with graph convolutional networks for insider threat and fraud detection. In MILCOM 2019-2019 IEEE Military Communications Conference (MILCOM), pp. 109–114. IEEE.
10.  Kim, J., Park, M., Kim, H., Cho, S., and Kang, P. 2019. Insider threat detection based on user behavior modeling and anomaly detection algorithms. Applied Sciences *9*, 4018.
11.  Senator, T. E., Goldberg, H. G., Memory, A., et al. 2013. Detecting insider threats in a real corporate database of computer usage activity. In Proceedings of the 19th ACM SIGKDD international conference on Knowledge discovery and data mining, pp. 1393–1401.
12.  Lv, Q., Wang, Y., Wang, L. and Wang, D. 2018. Towards a user and role-based behavior analysis method for insider threat detection. In 2018 international conference on network infrastructure and digital content (IC-NIDC), pp. 6–10. IEEE.
13.  Gamachchi, A., Sun, L. and Boztas, S. 2018. A graph based framework for malicious insider threat detection. arXiv preprint arXiv:1809.00141.
14.  Liu, L., Chen, C., Zhang, J., De Vel, O. and Xiang, Y. 2020. Doc2vec-based insider threat detection through behaviour analysis of multi-source security logs. In 2020 IEEE 19th International Conference on Trust, Security and Privacy in Computing and Communications (TrustCom), pp. 301–309. IEEE.
15.  Le, D.C. and Zincir-Heywood, N. 2021. Anomaly detection for insider threats using unsupervised ensembles. IEEE Transactions on Network and Service Management *18*, 2: 1152–1164.
16.  Legg, P. A. 2015. Visualizing the insider threat: challenges and tools for identifying malicious user activity. In 2015 IEEE Symposium on Visualization for Cyber Security (VizSec), pp. 1–7. IEEE.

# Evaluation of Supervised Machine Learning Classifiers to Detect Mobile Malware

**Dr. G. Padmavathi**

*Department of Computer Science Avinashilingam Institute for Home Science and Higher Education for Women Coimbatore, India [padmavathi\_cs@avinuty.ac.in](mailto:padmavathi_cs@avinuty.ac.in)*

**Dr. D. Shanmugapriya**

*Department of Information Technology Avinashilingam Institute for Home Science and Higher Education for Women Coimbatore, India [shanmugapriya\_it@avinuty.ac.in](mailto:shanmugapriya_it@avinuty.ac.in)*

**A. Roshni**

*Center for Cyber Intelligence Avinashilingam Institute for Home Science and Higher Education for Women Coimbatore, India [roshini\_cci@avinuty.ac.in](mailto:roshini_cci@avinuty.ac.in)*

Abstract: *Due to the rapid growth of android applications and mobile users in this technological era, there is a large increasing cyber attacks through mobile phones. During Pandemic period, mobile malware attacks are one of the top most cyber attacks observed in android mobile users to steal the user personal credentials by intrusion of adware, spyware, banking malware, SMS malware, riskware, viruses and so on. Machine learning methods are very useful and amicable to detect mobile malwares. Automation of the mobile malware detection is the need of the hour and it is imperative to identify the most suitable machine learning techniques. This paper investigates the evaluation of supervised machine learning algorithms that are applied to detect and classify the mobile malwares. A systematic method of evaluation of supervised machine learning model to detect the malware data points and to classify them into binary classification as malware or benign is essential. The purpose of evaluating the supervised machine learning algorithms is to identify the best supervised machine learning model for mobile malware detection with high efficacy rate. All important performance measures are applied and the entire experiments are conducted using benchmark dataset. Nine Supervised Machine Learning methods are experimented and the results are discussed.*

Keywords: Machine Learning, Malware Classification, Mobile Malware, Supervised Learning, Python

## I. INTRODUCTION

A Malware or Malicious Software is one of the most common types of cyber attack which was highly pre-dominant during the pandemic by the means of intruding as a malicious code to take over the system control by monitoring all the user activities and steal the user personal credentials without the knowledge of the user \[[2](#07_ch2.xhtml#r2_2)\] \[[3](#07_ch2.xhtml#r2_3)\] \[[4](#07_ch2.xhtml#r2_4)\].

Mobile malware are the important threats and android based mobile malware are very significant today and they compromise user’s credentials through unauthorized access \[[2](#07_ch2.xhtml#r2_2)\] \[[3](#07_ch2.xhtml#r2_3)\] \[[4](#07_ch2.xhtml#r2_4)\]. The aim of the paper is to identify efficient supervised machine learning algorithms to detect mobile malwares. The applied algorithms classify the dataset into malware data and benign data using a systematic approach which is vital towards automation of mobile malware detection.

Automation is the way of handling the problems without human intervention by incorporating AI methods to provide solution to reduce the processing time \[[9](#07_ch2.xhtml#r2_9)\]. The proposed approach experiments nine different supervised machine learning models, evaluate the models and recommends the most efficient supervised ML model for accurate malware detection. The evaluation of the supervised machine learning models is done in terms of performance metrics such as accuracy, precision, recall, F1 score, R2 score, TPR, FPR and ROC \[[5](#07_ch2.xhtml#r2_5)\] \[[7](#07_ch2.xhtml#r2_7)\] \[[8](#07_ch2.xhtml#r2_8)\].

The major contribution of this paper is to devise a systematic methodology to test the supervised machine learning model suitable for android based mobile malware detection. This paper is divided into different phases of Machine Learning work flow. The first step is to acquire the dataset and analyze the data to fit for the further development process. The malware dataset taken for study contains 1,00,000 records with 35 feature attributes. In the second step, data pre-processing methods are applied to check whether the data contains any null values or irrelevant values, which helps to remove the unwanted data values then split the data into training and test data set as in the ratio of 70:30. Third step, applies the feature selection methods to find out the important features of the dataset. Selecting the significant features from the dataset will help to improve the data processing time and provides better accuracy of the ML algorithms. The methodology uses three different feature selection algorithms namely, (i) Univariate Selection (ii) Feature Importance and (iii) Recursive Feature Elimination. By applying the above mentioned feature selection methods, out of 35 features top 10 important features are selected for effective malware classification. Fourth step, applies supervised machine learning algorithms to identify and classify the data into malware/benign \[[1](#07_ch2.xhtml#r2_1)\] \[[2](#07_ch2.xhtml#r2_2)\] \[[6](#07_ch2.xhtml#r2_6)\] \[[9](#07_ch2.xhtml#r2_9)\] \[[10](#07_ch2.xhtml#r2_10)\]. Following supervised machine learning algorithms are evaluated in this study.

1.  Decision tree
2.  Random forest
3.  K – Nearest Neighbors (KNN)
4.  Support Vector Machine (SVM)
5.  Naïve Bayes
6.  AdaBoost
7.  Neural Network (MLP)
8.  Logistic Regression
9.  Linear Discriminant Analysis

Fifth step, evaluate the performance of the supervised machine learning models using various evaluative metrics to provide the best model for mobile malware detection \[[1](#07_ch2.xhtml#r2_1)\] \[[4](#07_ch2.xhtml#r2_4)\].

## II. PROBLEM DEFINITION

For automation of mobile malware detection, it is necessary to develop a systematic framework. This study applies supervised machine learning algorithms to detect and classify the mobile malware. Nine different supervised machine learning algorithms are implemented and evaluated for performance and the most suitable supervised machine learning models are identified based on their performance.

## III. METHODOLOGY

A study has been conducted for dynamic behavior based android mobile malware classification using supervised machine learning techniques \[[2](#07_ch2.xhtml#r2_2)\]. The entire methodology is divided into five different phases. The first phase of the work is to acquire the appropriate malware dataset for the problem. The second phase involves data pre-processing to investigate the quality of the data by removing the duplicate records, noisy data and conversion of null values into well defined format. The third phase is to apply Feature Selection methods to find out the best features of the dataset that strives to detect or classify the malware data points with high efficacy rate with less processing time. The fourth phase is building a nine different Supervised Machine Learning Models which automatically detects and classifies the malware data points based on the training data \[[1](#07_ch2.xhtml#r2_1)\] \[[2](#07_ch2.xhtml#r2_2)\] \[[6](#07_ch2.xhtml#r2_6)\] \[[9](#07_ch2.xhtml#r2_9)\] \[[10](#07_ch2.xhtml#r2_10)\]. The fifth phase is to make a comparative analysis between the nine different Supervised Machine Learning models developed in the previous phase by evaluating them using performance metrics to suggest the best classifier model that can detect and classify the malware data points accurately \[[1](#07_ch2.xhtml#r2_1)\] \[[4](#07_ch2.xhtml#r2_4)\]. [Figure 1](#07_ch2.xhtml#f2_1) illustrates the step – by – step methodology followed in this paper.

![Fig. 1 Proposed Workflow Methodology](images/page12_1_B.jpg)

[**Fig. 1**](#07_ch2.xhtml#f2_1b) Proposed Workflow Methodology

The above illustrated methodology is implemented using Python programming in Jupyter Notebook environment.

### A. About the Dataset

Understanding of the dataset is very important for the accurate prediction and classification. In this work, the benchmark dataset is taken from the kaggle community. The dataset consists of 1,00,000 records and 35 feature attributes. The identification of malware and classification as malware or benign depends on the behavioral features. [Table I](#07_ch2.xhtml#t2_1) shows the description of the 35 android kernel attributes involved in the dataset.

[**TABLE I.**](#07_ch2.xhtml#t2_1b) Mobile Malware Dataset – Attribute Description

 
| S. No || Malware Data Attributes || Description |
| --- | --- | --- |
| 1 || hash || It is a common method to uniquely identify the malware, which acts as a fingerprint for malware detection. This data contains 100 unique hash values. (i.e. unique apk app names) |
| --- | --- | --- |
| 2 || millisecond || It denotes the time in millisecond ranges from 0 to 999 milliseconds. |
| 3 || state || It denotes the flag of unrunable or runnable or stopped tasks as ‘0’. |
| 4 || usage: counter || It shows the reference count for task\_struct of process as ‘0’. |
| 5 || prio || It denotes the system task structure with normal priority value from 0 to 99 and real-time from 100 to 140 as ‘3.07b’. |
| 6 || static\_prio || It holds the processes’ initial priority value ranging from 14.0k to 31.9k. |
| 7 || normal\_prio || It denotes the priority without taking RT-inheritance into account as ‘0’. |
| 8 || policy || It denotes the scheduling policy used for this process as ‘0’. |
| 9 || vm\_pgoff || It is the page offset of the area in the file. This is the file position of the first page mapped in this area when a file or device is mapped. It is the first page of the file or device marked as ‘0’ in the vm\_area. |
| 10 || vm\_truncate: count || It denotes the vm: areatruncate\_count values ranging from 9695 to 27.2k. |
| 11 || task\_size || It represents the current task size as ‘0’. |
| 12 || cached\_hole: size || It represents the size of the free address space hole as ‘0’. |
| 13 || free\_area: cache || It represents the first address space hole ranging from 0 to 515. |
| 14 || mm\_users || It represents the address space of users ranging from 612 to 995. |
| 15 || map\_count || It denotes the number of mapping areas ranging from 2588 to 28.2k. |
| 16 || hiwater\_rss || It represents the high watermark of resident set and sets the peak of resident set size as ‘0’. |
| 17 || total\_vm || It denotes the total number of memory pages ranging from 4 to 2810. |
| 18 || shared\_vm || It denotes the number of shared pages ranging from 112 to 120. |
| 19 || exec\_vm || It represents the number of executable memory pages ranging from 92 to 196. |
| 20 || reserved\_vm || It represents the number of reserved memory pages ranging from 29 to 755. |
| 21 || nr\_ptes || It represents the number of page table entries as ‘0’. |
| 22 || end\_data || It represents the end address of data ranging from 112 to 120. |
| 23 || last\_interval || It denotes the last interval time before thrashing ranging from 0 to 9526. |
| 24 || nvcsw || It denotes the number of voluntary context switches ranging from 338k to 385k. |
| 25 || nivcsw || It denotes the number of in voluntary context switches ranging from 0 to 365. |
| 26 || min\_flt || It represents the minor page faults ranging from 0 to 256. |
| 27 || maj\_flt || It represents the major page faults from 112 to 120. |
| 28 || fs\_excl: counter || It holds the file system exclusive counter value ranging from 0 to 18. |
| 29 || lock || It denotes the file lock as ‘3.20b’ |
| 30 || utime || It represents the cumulative time spends on user code ranging from 372k to 422k. (i.e. user time) |
| 31 || stime || It represents the cumulative time spent executing system code ranging from 3 to 7. (i.e. system time) |
| 32 || gtime || It denotes the group time, cumulative resource counter ranging from 0 to 15. (i.e. guest time) |
| 33 || cgtime || It denotes the cumulative group time, cumulative resource counter as ‘O’. |
| 34 || signal\_nvcsw || It denotes the cumulative resource counter as ‘O’. |
| 35 || classification || It contains binary classification as malware or benign. |

### B. Data Acquisition and Data Importing

The first and foremost step in developing a Supervised Machine Learning Model is to acquire the appropriate dataset and import them into the working environment. Python is a platform excellence to support enormous Machine Learning algorithms and it is the suitable environment experiments methodology of machine learning model. In this step, the acquired malware dataset is converted into the CSV file format and imported into the Python Jupyter notebook environment.

### C. Data Pre-processing

After importing the dataset, the second consequent step to be performed is data pre-processing \[[4](#07_ch2.xhtml#r2_4)\]. Data pre-processing is the significant step to derive the best results from the classifier models. The data pre-processing is carried out by verifying that the taken dataset contains any null values, un-defined values or irrelevant values which may deviate the results and degrade the performance of the models. The null values are replaced into “zero (0)” or “unknown” data values to overcome the processing issue. Label encoding method is applied to convert the attributes into the integer data type format to develop suitable machine learning model. For developing ML models the entire dataset is divided into training set and testing set in the ratio of 70% for training and 30% for testing \[[1](#07_ch2.xhtml#r2_1)\] \[[2](#07_ch2.xhtml#r2_2)\]. After this step, the dataset is now available in a well defined format for further processing.

### D. Feature Selection

Feature selection is an important step of Feature Engineering in Machine Learning process \[[6](#07_ch2.xhtml#r2_6)\] \[[7](#07_ch2.xhtml#r2_7)\] \[[8](#07_ch2.xhtml#r2_8)\] \[[10](#07_ch2.xhtml#r2_10)\]. Feature Engineering is the third step, in the Machine Learning process which extracts the features from the raw dataset to provide labels for appropriate classification. Following feature selection methods are used to choose the top 10 important features precisely out of 35 attributes of given dataset.

#### i. Univariate Feature Selection

The univariate feature selection approach is a statistical technique for identifying relevant features having a strong association to the target variable. The scikit-learn library in Python includes a function called SelectKBestclass. The SelectKBest class is used in this study to choose the top 10 features out of 35 features in a mobile malware dataset using the chi-square statistical test. It calculates the Chi-square coefficient for each non-negative feature in the target class and chooses the desired top 10 features with the highest Chi-square scores.

**Chi – Square Formula:**

$X^{2} = {\\sum\\frac{\\left( {Observed\\text{?}value - Expected\\text{?}value} \\right)^{2}}{Expected\\text{?}Value}}$

#### ii. Feature Importance Based Feature Selection

The feature importance property of the ensemble model is used by the python tool feature importance to pick important features of the dataset. Every property of the dataset is given a score. Greater the score, higher the significance or relevance feature towards target variable. Using the python sklearn ensemble model with the Extra tree classifier method, the system calculates the top 10 features and displays the scores of all the calculated features.

#### iii. Recursive Feature Elimination (RFE)

Recursively deleting characteristics and then developing a classifier model with the remaining attributes is how the recursive feature elimination is done. The model selects the top 10 features of the data by recursively eliminating the smallest features using the python sklearn feature selection library, RFE method, and the logistic regression classifier algorithm, and the selected features are discernible as True in the support array, and the features are ranked using the choice “1” in the ranking array.

After incorporating three different feature selection methods, the top 10 features are selected based on the highest occurring nature of attributes from the three different feature selection methods. This selection helps in malware data point selection in optimum time. [Figure 2](#07_ch2.xhtml#f102_2) indicates the top 10 selected features out of the 35 features shown in Table I. The Top 10 Selected Features are listed below.

*   hash
*   state
*   static\_prio
*   vm\_truncate\_count
*   map\_count
*   total\_vm
*   reserved\_vm
*   nvcsw
*   nivcsw
*   utime

![Fig. 2 The Top 10 Selected Features Based on the Three Different Feature Selection Methods](images/page15_1_B.jpg)

[**Fig. 2**](#07_ch2.xhtml#f102_2b) The Top 10 Selected Features Based on the Three Different Feature Selection Methods

### E. Supervised Machine Learning Models

The fourth phase is Model building. After selecting the top 10 best features out of 35 attributes in the dataset, now the data is ready for developing the model based on Supervised Machine Learning algorithms for the function of classification of mobile malware as malware or benign. Following nine supervised machine learning algorithms are implemented to develop a mobile malware classification model \[[1](#07_ch2.xhtml#r2_1)\] \[[2](#07_ch2.xhtml#r2_2)\] \[[6](#07_ch2.xhtml#r2_6)\] \[[9](#07_ch2.xhtml#r2_9)\] \[[10](#07_ch2.xhtml#r2_10)\].

1.  Decision Tree
2.  Random Forest
3.  KNN
4.  SVM
5.  Naïve Bayes
6.  AdaBoost
7.  Neural Network (MLP)
8.  Logistic Regression
9.  Linear Discriminant Analysis

The above specified supervised learning algorithms are developed using python Scikit learn library. The general steps involved in developing the above mentioned supervised machine learning models for Mobile Malware classification is explained below:

*   **Step 1:** Import the necessary Scitkit learn Supervised Machine Learning algorithm library.
*   **Step 2:** Fit the Supervised Machine Learning model to the given training set.
*   **Step 3:** Based on the training data, forecast the test result.
*   **Step 4:** Then, perform test data predictions and calculate accuracy.
*   **Step 5:** Finally, the Supervised Machine Learning Classifier model is ready.

Each Supervised Machine Learning algorithm detects and classifies the malware data points depending upon their own mechanism of calculating the attributes thresholds. The distance calculation measures vary for each algorithm and the weights for the model parameters are determined for final classification. Table II describes the criteria used to detect and classify the mobile malware data points.

**TABLE II.** Supervised Machine Learning Algorithm’s Classification Criteria

 
| Algorithm Name || Classification Criteria |
| --- | --- |
| Decision Tree || Attribute Selection Measure (Entropy or Gini Index) |
| --- | --- |
| Random Forest || Attribute Selection Measure (Entropy or Gini Index) |
| KNN || Euclidian Distance Measure |
| SVM || Hyperplane Dimensionality |
| Naïve Bayes || Bayes Theorem |
| AdaBoost || Ensemble Learning |
| MLP || Back Propagation |
| Logistic Regression || Sigmoid Function |
| LDA || Collinearity / Class Variance |

### F. Performance Evaluation Metrics

Following performance metrics are used to evaluate the nine Supervised Machine Learning models \[[1](#07_ch2.xhtml#r2_1)\] \[[4](#07_ch2.xhtml#r2_4)\]:

*   Accuracy
*   Precision
*   Recall
*   F1 Score
*   R2 Score
*   Confusion matrix

The error rates of each Supervised Machine Learning models are also calculated based on the following \[[9](#07_ch2.xhtml#r2_9)\]:

*   Mean Absolute Error (MAE)
*   Mean Squared Error (MSE)
*   Root Mean Squared Error (RMSE)

The results are also visualized in Receiver Operating Characteristic (ROC) curve form.

**Accuracy:** It is defined as the percentage of accurate predictions of the test data.

$Accuracy = \\frac{TP + TN}{TP + TN + FP + FN}$

**True Positives (TP)** – These are the accurately predicted positive values, indicating that the actual and predicted class values are both True.

**True Negatives (TN)** – These are the precisely predicted negative values, indicating that the actual and predicted class values are both False.

**False Positives (FP)** – When the predicted class is True, but the actual class is False.

**False Negatives (FN)** – When the predicted class is False, but the actual class is True.

**Precision:** It is the ratio of successfully predicted positive observations to total expected positive observations. It refers to the classifier’s ability to avoid mislabeling a negative sample as positive.

> **Precision = TP/TP + FP**

**Recall:** It is the proportion of accurately predicted positive observations to all observations in the actual class of observations. It refers to the capacity of classifier on its ability to locate all positive samples.

> **Recall = TP/TP + FN**

**F1 Score:** It is the weighted average, or Harmonic Mean, of Precision and Recall. As a result, this score takes into account both false positives and false negatives.

> **F1 Score = 2\*(Recall \* Precision) / (Recall + Precision)**
> 
> **Or**
> 
> **F1 = 2TP / 2TP + FP + FN**

**R2 Score:** The coefficient of determination (sometimes referred to as R-Squared) is a statistical metric used in regression models to determine how much variance in the dependent variable can be explained by the independent variable.

$R^{2} = 1 - \\frac{\\sum\\left( {y\_{i} - \\hat{y}} \\right)^{2}}{\\sum\\left( {y\_{i} - \\overline{y}} \\right)^{2}}$

Where, *ŷ* is the predicted value of *y* and *ȳ* is the mean value of *y*.

**Confusion Matrix:** It is a matrix that is used to evaluate classification model’s performance for a certain set of test data. Only if the true values for test data are known, it can be determined. Since it displays the errors in the model’s performance as a matrix, it is also known as an error matrix. [Figure 3](#07_ch2.xhtml#f2_3) shows the confusion matrix.

[Fig. 3](#07_ch2.xhtml#f2_3b) Confusion Matrix

 
| N = Total Predictions || Actual Positive (1) || Actual Negative (0) |
| --- | --- | --- |
| Predicted Positive (1) || TP || FP |
| Predicted Negative (0) || FN || TN |

**Mean Absolute Error (MAE) (L1 Loss):** It is the average of the absolute difference in the dataset’s actual and forecasted values. It computes the average of the residuals in the dataset.

$MAE = \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}\\left| y\_{i} - \\hat{y} \\right|}$

**Mean Squared Error (MSE) (Quadratic Loss or L2 Loss):** It is the average of the squared difference between the original and forecasted values. It calculates the residuals’ variance.

$MSE = \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}\\left( {y\_{i} - \\hat{y}} \\right)^{2}}$

**Root Mean Squared Error (RMSE):** It is the standard deviation of the errors that occur when making a prediction on a dataset. This is the same as MSE (Mean Squared Error). Only the root of the number is taken into account when determining the model’s accuracy. The square root of Mean Squared Error is termed as RMSE. It calculates the residuals’ standard deviation.

$RMSE = \\sqrt{MSE} = \\sqrt{\\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}\\left( {y\_{i} - \\hat{y}} \\right)^{2}}}$

Where, *ŷ* is the predicted value of *y* and *ȳ* is the mean value of *y*.

**Receiver Operating Characteristic (ROC) Curve:** It is a graph that shows how effectively a classification algorithm works across all the conceivable thresholds. The graph shows both the true positive rate (Y-axis) and the false positive rate (X-axis). As a function of the model’s positive classification threshold, it plots the true positive rate (TPR) against the false positive rate (FPR).

**AUC (Area under the Curve):** It is a statistic used for calculating the classification model’s overall performance based on the area under the ROC curve.

#### G. Comparative Analysis

Based on the above given evaluation measures, a comparative analysis is made between the nine different supervised machine learning models to discover the best classifier model with high efficacy rate. [Figure 4](#07_ch2.xhtml#f2_4) shows the overall accuracy comparison of all supervised machine learning model. Table III and Table IV describes the comparative analysis of nine supervised machine learning algorithms based on the evaluation metrics such as accuracy, precision, recall, F1 score, R2 score and the error rate evaluation based on Mean Absolute Error (MAE), Mean Squared Error (MSE) and Root Mean Squared Error (RMSE).

![Fig. 4 Overall Accuracy Comparison of all Supervised ML Model](images/page17_1_B.jpg)

[**Fig. 4**](#07_ch2.xhtml#f2_4b) Overall Accuracy Comparison of all Supervised ML Model

**TABLE III.** Comparison of Precision, Recall, F1, R2 Score between Supervised Machine Learning Algorithms

 
| S. No || Supervised Machine Learning Algorithms || Accuracy Score || Precision Score || Recall Score || F1 Score || R2 Score |
| --- | --- | --- | --- | --- | --- | --- |
| 1 || Decision Tree Classifier || **1.0** || **1.0** || **1.0** || **1.0** || **1.0** |
| --- | --- | --- | --- | --- | --- | --- |
| 2 || Random Forest Classifier || **1.0** || **1.0** || **1.0** || **1.0** || **1.0** |
| 3 || K – Nearest Neighbor Classifier || 0.996 || 0.996 || 0.996 || 0.996 || 0.986 |
| 4 || Support Vector Machine Classifier || 0.999 || 1.0 || 0.999 || 0.999 || 0.999 |
| 5 || Naïve Bayes Classifier || 0.909 || 0.895 || 0.927 || 0.911 || 0.638 |
| 6 || AdaBoost Classifier || **1.0** || **1.0** || **1.0** || **1.0** || **1.0** |
| 7 || Neural Network (MLP) Classifier || **1.0** || **1.0** || **1.0** || **1.0** || **1.0** |
| 8 || Logistic Regression Classifier || **1.0** || **1.0** || **1.0** || **1.0** || **1.0** |
| 9 || Linear Discriminant Analysis Classifier || 0.997 || 0.999 || 0.995 || 0.997 || 0.990 |

**TABLE I.** Comparison of MAE, MSE, RMSE between Supervised Machine Learning Algorithms

 
| S. No || Supervised Machine Learning Algorithms || MAE || MSE || RMSR |
| --- | --- | --- | --- | --- |
| 1 || Decision Tree Classifier || **0.0** || **0.0** || **0.0** |
| --- | --- | --- | --- | --- |
| 2 || Random Forest Classifier || **0.0** || **0.0** || **0.0** |
| 3 || K - Nearest Neighbor Classifier || 0.003 || 0.003 || 0.057 |
| 4 || Support Vector Machine Classifier || 6.666 || 6.666 || 0.008 |
| 5 || Naïve Bayes Classifier || 0.0904 || 0.0904 || 0.3007 |
| 6 || AdaBoost Classifier || **0.0** || **0.0** || **0.0** |
| 7 || Neural Network (MLP) Classifier || **0.0** || **0.0** || **0.0** |
| 8 || Logistic Regression Classifier || **0.0** || **0.0** || **0.0** |
| 9 || Linear Discriminant Analysis Classifier || 0.0024 || 0.0024 || 0.0496 |

## IV. RESULTS AND DISCUSSION

From the above comparative analysis (Table III and Table IV) made between nine different supervised machine learning algorithms it is evident that the Decision Tree, Random Forest, AdaBoost, Neural Network based Multi Layer Perceptron (MLP), Logistic Regression accurately detect and classify the malware data points with 100% accuracy at 0% error rate for Mobile Malware binary classification. Moreover, KNN algorithm classifies with 99.7%, SVM algorithm classifies with 99.9%, Naïve Bayes algorithm classifies with 90.9%, LDA algorithm classifies with 99.7% accuracy. When compared with Decision tree, Random forest, KNN, SVM, AdaBoost, MLP, Logistic Regression and LDA supervised model classifiers; the Naïve Bayes classifier model performs little low in accuracy for the given dataset.

[Figure 5](#07_ch2.xhtml#f2_5), [Figure 6](#07_ch2.xhtml#f2_6), [Figure 7](#07_ch2.xhtml#f2_7), [Figure 8](#07_ch2.xhtml#f2_8) and [Figure 9](#07_ch2.xhtml#f2_9) shows the results of comparative analysis between the nine supervised machine learning models evaluated based on the performance metrics such as accuracy, train accuracy, test accuracy, precision, recall, F1 score, R2 score, confusion matrix, TPR, FPR and ROC curve.

![Fig. 5 Train Accuracy Comparison of all Supervised ML Models](images/page18_1_B.jpg)

[**Fig. 5**](#07_ch2.xhtml#f2_5b) Train Accuracy Comparison of all Supervised ML Models

![Fig. 6 Test Accuracy Comparison of all Supervised ML Models](images/page19_1_B.jpg)

[**Fig. 6**](#07_ch2.xhtml#f2_6b) Test Accuracy Comparison of all Supervised ML Models

![Fig. 7Precision Comparison of all Supervised ML Models](images/page19_2_B.jpg)

[**Fig. 7**](#07_ch2.xhtml#f2_7b)Precision Comparison of all Supervised ML Models

![Fig. 8 Recall Comparison of all Supervised ML Models](images/page20_1_B.jpg)

[**Fig. 8**](#07_ch2.xhtml#f2_8b) Recall Comparison of all Supervised ML Models

![Fig. 9 Overall Comparative Representation of Supervised ML Algorithms in ROC Curve](images/page20_2_B.jpg)

[**Fig. 9**](#07_ch2.xhtml#f2_9b) Overall Comparative Representation of Supervised ML Algorithms in ROC Curve

## V. CONCLUSION

Android based mobile malware are of serious threats to the user community due to challenges with user data compromise. Therefore, automatic detection and dynamic analysis of mobile malware are very crucial to develop. The implementation of various Supervised Machine Learning Models using Mobile Malware Dataset, it is observed that, out of nine Supervised Machine Learning algorithms, the Naïve Bayes Classifier Model performs little low when compared with other different eight given Supervised Machine Learning algorithms for the given dataset.

This paper clearly describes the step-by-step implementation procedure to develop an effective Machine Learning Model using a Mobile Malware Dataset in an elaborative way. Moreover, all Supervised Machine Learning algorithms support Malware classification with higher efficacy rate. Thus, this study will be helpful for the learners to understand and implement Supervised Machine Learning algorithms in a systematic way by incorporating mobile malware datasets to arrive at the best results.

## ACKNOWLEDGEMENT

This work is supported by DST-CURIE-AI project during 2021–2023 by Centre for Cyber Intelligence established under Centre for Machine Learning and Intelligence, Avinashilingam Institute for Home Science and Higher Education for Women, Coimbatore – 43, Tamilnadu, INDIA.

## REFERENCES

1.  [Prema Agarwa., and Bhushan Trivedi](#07_ch2.xhtml#r_r2_1). 2020 (November). Evaluating Machine Learning Classifiers to detect Android Malware. International Conference for Innovation in Technology (INOCON). IEEE.
2.  [Samaneh Mahdavifar, Andi Fitriah Abdul Kadir, Rasool Fatemi, Dima Alhadidi, and Ali, A. Ghorbani](#07_ch2.xhtml#r_r2_2). 2020. Dynamic Android Malware Category Classification using Semi-Supervised Deep Learning. International Conference on Dependable, Autonomic and Secure Computing, International Conference on Pervasive Intelligence and Computing, International Conference on Cloud and Big Data Computing, International Conference on Cyber Science and Technology Congress. IEEE.
3.  [Muhammad ‘Afif Husainiamer, Madihah Mohd Saudi, and Azuan Ahmad](#07_ch2.xhtml#r_r2_3). 2020. Classfication for iOS Mobile Malware Inspired by Phylogenetic: Proof of Concept. IEEE Conference on Open Systems (ICOS). IEEE.
4.  [Jianguo Jiang., Song Li., Min Yu., et al.](#07_ch2.xhtml#r_r2_4) 2019. Android Malware Family Classification Based on Sensitive Opcode Sequence. IEEE Symposium on Computers and Communications (ISCC). IEEE.
5.  [Ken, F. Yu., and Richard, E. Harang.](#07_ch2.xhtml#r_r2_5) 2017. Machine Learning in Malware Traffic Classifications. Milcom 2017 Track 3 – Cyber Security and Trusted Computing. IEEE.
6.  [Marian Kuhnel., and Ulrike Meyer](#07_ch2.xhtml#r_r2_6). 2016. Classification of Short Messages Initiated by Mobile Malware. 11th International Conference on Availability, Reliability and Securit. IEEE.
7.  [Xinjian Ma., Qi Biao., Wu Yang., and Jianguo Jiang](#07_ch2.xhtml#r_r2_7). 2016. Using Multi-features to reduce false positive in Malware Classification. IEEE.
8.  [George Cabau., Magda Buhu., and Ciprian Oprisa](#07_ch2.xhtml#r_r2_8). 2016. Malware Clasiification Based on Dynamic Behavior. 18th International Symposium on Symbolic and Numeric Algorithms for Scientific Computing. IEEE.
9.  [Mohammed, S. Alam, and T. Vuong](#07_ch2.xhtml#r_r2_9). 2013. Random Forest Classification for Detecting Android Malware. IEEE International Conference on Green Computing and Communications and IEEE Internet of Things and IEEE Cyber Physical and Social Computing. IEEE.
10.  [Ivan Firdausi., Charles Lim., Alva Erwin., and Anto Satriyo Nugroho](#07_ch2.xhtml#r_r2_10). 2010. Analysis of Machine Learning Techniques used in Behavior-Based Malware Detection. Second International Conference on Advances in Computing, Control, and Telecommunication Technologies. IEEE.

# Secure Data Aggregation Process Using Memetic Algorithm in IoT Enabled Wireless Sensor Networks

Dr. D. Nethra Pingala Suthishni

Assistant Professor, Department of Information Technology Avinashilingam Institute for Home Science and Higher Education for Women Coimbatore, India

[nethra\_it@avinuty.ac.in](mailto:nethra_it@avinuty.ac.in)

Mr. K.S. Senthil Kumar

Assistant Professor, PG & Research Department of Computer Science Hindusthan College of Arts & Science, Coimbatore, India

[senth4u4m@gmail.com](mailto:senth4u4m@gmail.com)

**Abstract:** *In the last decade, the Internet of Things (IoT) serves as a backbone for entirely connected sensor devices to achieve integrated communication settings and platforms, both virtual and real-world, in terms of distributed systems. In Internet of Things (IoT), Wireless Sensor Networks (WSNs) is considered as the key element. IoT is sensing the environment, collecting data and sending to the base station (BS). IoT environment routing protocols are designed for WSNs. But, WSNs doesn’t work properly due to heterogeneity of nodes. As IoT network is a decentralized type of network, the network senses the information and passes it on to the base station. Small size of sensor nodes consumes more energy in this type of network and this seems to be a major issue. They are vulnerable to a variety of attacks due to the usage of wireless communication channels and the possibility of deployment in harsh settings or unsupervised areas. In addition, the installed security systems in these contexts have inherent drawbacks. As a result, such systems are susceptible to cyber security threats. To enhance the performance of the network and to overcome the cyber security risks, a new algorithm called Memetic algorithm is proposed in this research. Memetic algorithm is one of the best algorithms in terms of security breaches. The algorithm is based on routing mechanism and uses mobile sink for data gathering mechanism to prevent network partitioning problem. The simulation of the proposed technique is done using NS2 Simulator. The experimental results are compared with the prevailing algorithms to demonstrate the efficiency of the proposed scheme against some common security risks such as traffic interception, and ransomware. The proposed work also achieves better performance in terms of throughput, network lifetime, packet lost, end to end delay and energy consumption. Node authentication, data integrity, anti-compromise, and traffic analysis resistance are all features of the proposed system.*

**Keywords:** Wireless Sensor Networks (WSNs), IoT, Cyber Security, Security Breaches, Memetic Algorithm.

## I. INTRODUCTION

WSNs are a key component of the Internet of Things (IoT), which uses IoT devices to monitor and provide useful data from the environment to users. Home automation, forest monitoring, healthcare systems, precision agriculture, and smart city development are all examples of IoT applications today. In the monitoring region, IoT devices or sensors sense various physical factors like as pressure, humidity, and temperature, and communicate this useful information to the Base Station (BS) via single-hop or multi-hop communication. Sensor nodes have energy restrictions in WSNs for IoT.

Several issues with the clustering process, such as energy hole and network segmentation, severely reduces network longevity and subsequently leads to possibilities of cyber threats. In this scenario, the need for securing the sensor network from various cyber threats arises. These threats may either harm the individual nodes on the network or the entire sensor network. Cluster Head (CH) nearby sensor nodes relay more data packets than far away sensor nodes, resulting in the early mortality of the CH nearest sensor nodes in the clustering mechanism. Faraway sensor nodes have enough energy for data transmission in this situation, but they are unable to transmit data packets to the CH and BS due to a lack of network structure and this tends to be an energy hole problem. Due to the energy hole issues, the network has been divided into numerous distinct portions. Dividing the network into partitions thus leads to cyber security threats and hence the cyber risks grow in complexity. Due to the lack of appropriate communication links, certain portions are unable to communicate to the Base Station.

Encryption and decryption are two data transformations defined by a cryptosystem. To generate cipher text, encryption is applied to plain text, i.e. the data to be transferred. i.e. data that has been encrypted using an encryption key. The decryption key is used to transform cypher text to plain text, which is the original data. Symmetric cryptography is defined as encryption and decryption keys that are the same or can be deduced from one another.

One key, known as the private key, is kept private, while the other, known as the public key, is made public. The public key encrypts the communication, which can only be decrypted with the private key. As a result, anyone with the public key cannot decrypt the encrypted message, allowing for safe communication. The most prominent public key algorithm called RSA (named after its creators Rivest, Shamir, and Adleman) \[[8](#08_ch3.xhtml#r3_8)\] is adapted.

The deployed nodes are usually immobile, and the sink position in traditional data collection algorithms is usually fixed. Due to the high overhead of relaying messages, sensor nodes close to the static sink use more energy than those further away. Because of the issue, sensor nodes near the static sink perish significantly faster than other nodes, reducing network longevity \[[1](#08_ch3.xhtml#r3_1)\]. And, this concern eventually increases the possibility of cyber threats.

Heterogeneous nodes have significantly greater communications and data processing capabilities than common nodes. However, heterogeneous nodes are expensive, and it is vital to investigate how to balance energy consumption and to extend network lifetime \[[2](#08_ch3.xhtml#r3_2)\].

Data redundancy keeps track of every transfer in the network and helps to prevent Denial-of-Service attacks. Authentication, risk assessment, and data security are application layer security requirements for the protection of digital content, which is very important in order to secure the environment. External authentications are required in order to grant access to data and information.

The remaining part of the paper is organized as follows: [Section II](#08_ch3.xhtml#c3_2) surveys the related work process of IoT enabled Wireless Sensor Networks, Network Security and the evolution of Cyber Threats. [Section III](#08_ch3.xhtml#c3_3) explains the Problem Statement. [Section IV](#08_ch3.xhtml#c3_4) derives the Proposed Work and algorithm details. [Section V](#08_ch3.xhtml#c3_5) explains the Simulation Environment and Performance Metrics details. Results and Discussion are described in [Section VI](#08_ch3.xhtml#c3_6). [Section VII](#08_ch3.xhtml#c3_7) explains the conclusion the paper.

![Fig. 1 IoT in WSN](images/page24_1_B.jpg)

**Fig. 1** IoT in WSN

## II. RELATED WORK

**Chuan Zhu, Kangning Quan, Guangjie Han and Joel J.P.C. Rodrigues \[[1](#08_ch3.xhtml#r3_1)\]** explain with mobile sinks, we offer a high-availability and location-predictive data collection strategy. Sensor nodes can determine the locations of mobile sinks based on time synchronisation, which minimises sensor node energy usage for sink location updates. When the network uses the high-available data gathering technique, it can continue to gather data even if part of the mobile sinks are inaccessible. Furthermore, by altering the moving trajectory of a mobile sink, the energy consumption of nodes near resident sites can be balanced. When there is a problem at the resident point, however, data uploading to the mobile sink is severely hampered.

**Chunlin Li, Jingpan Bai, Jinguang Gu, Xin Yan and Youlong Luo \[[2](#08_ch3.xhtml#r3_2)\]** explain to balance energy and extend network lifetime, the clustering routing method for wireless sensor networks (CHRA) is introduced. The combination of heterogeneous nodes and cluster heads is taken into account. To begin, a model of optimal node placement for heterogeneous nodes is created. Second, a clustering routing method for wireless sensor networks (CHRA) is proposed, which combines the heterogeneous routing algorithm for wireless sensor networks (HRA) with the LEACH-C cluster heads choosing technique. Finally, extensive tests are used to evaluate the performance of our proposed routing method and several earlier conventional routings. The routing algorithm can significantly extend the lifetime and stability of a network. It can also drastically reduce energy consumption.

**Gurbinder Singh Brar, Shalli Ra,i, Vinay Chopra, Rahul Malhotra, Houbing Song and Syed Hassan Ahmed \[[3](#08_ch3.xhtml#r3_3)\]** explain a PEGASIS-DSR optimised routing protocol (PDORP) based on hybrid optimization, which combined the cache and directional transmission concepts of proactive and reactive routing protocols. Our suggested protocol’s simulation findings show a reduction in end-to-end transmission delay and bit error rate without sacrificing energy efficiency. In order to obtain a quick and non-damaged path with decreased transmission latency, both proactive and reactive routing methodologies were applied in PDORP.

**Jianhua Huang, Danwei Ruan and Weiqiang Meng \[[4](#08_ch3.xhtml#r3_4)\]** explain ASGRP is a low-energy multi-hop routing protocol for WSNs based on annulus sector grid clustering. In a wireless sensor network, the suggested protocol enhances the way clusters are formed. The main concept is to divide the network area into annulus sector grids, with the BS as the circular region’s centre point. Each annular sector grid’s nodes are clustered into a cluster. An annular sector grid, as opposed to a rectangular grid, can ensure that the distance between the grid nodes and the BS is approximately the same. The angle between the boundary where the BS is located and the line from the nodes to the BS is used to create an annular sector grid. We also designed an inter-level multi-hop routing strategy to boost data transmission efficiency between the BS and cluster head nodes. The suggested routing method uniformizes energy use and minimises transmission energy consumption. Multi-hop EEBCDA, EEMRP, and CAMP, as well as ASGRP, achieve more consistent energy usage, greatly extend network lifetime, and have superior scalability in networks with varying numbers of nodes and sizes.

**Jianhua Huang, Yadong Hong, Ziming Zhao and Yubo Yuan \[[5](#08_ch3.xhtml#r3_5)\]** explain to extend the network lifetime, we presented an energy-efficient multi-hop routing protocol based on grid clustering. The suggested protocol divides the network region across unequal grids to produce clusters of varying levels. Because grids located further away from the sink are larger, cluster distribution is more acceptable, and energy consumption among functional nodes is efficiently balanced. Sensor nodes in the grids nearest to the sink send data directly to the sink, whereas sensor nodes in subsequent grids send data via multi-hop transmission. To reduce the complexity of the election, a management technique based on CM nodes is provided, which may eliminate the randomness of electing CH nodes, optimise the position of CH nodes, and lower the communication cost of member nodes within clusters. It is concluded that the suggested protocol outperforms the other protocols in terms of energy efficiency, network lifetime, and scalability.

**Mbanaso, U. M. and Chukwudebe, G. A. \[[6](#08_ch3.xhtml#r3_6)\]** explain the dangers and vulnerabilities of IoT systems are investigated, and a novel adjustable policy-based specification is presented for resolving trust, confidentiality, and privacy challenges in dispersed situations. Smart entities should become more trusted, reliable, and secure in an era where gadgets must collaborate and interact seamlessly to solve problems across many domains, assuring end-to-end dynamic security and safety. It has developed a system that allows IoT entities to define their Capabilities and Requirements in a fine-grained policy construct for mutual and immediate negotiation of proven attributes and resources. It also provides means for auditable and dispute resolution, which are essential success elements in IoT environments, in addition to resolving trust, privacy, and secrecy in a unified manner.

**Moosa Ayati, Mohammad Hossein Ghayyoumi and Atiyeh Keshavarz-Mohammadiyan \[[7](#08_ch3.xhtml#r3_7)\]** explain reducing energy usage in WSNs is critical since it extends the network’s lifetime. Clustering is an effective way to extend the life of a network. LEACH is the most widely used clustering method currently available. Data overhead in the BS is decreased in a WSN with low energy usage. One of the most critical factors that reduces network lifetime and raises the risk of data loss is data overhead. Data packets collide with each other when data overhead develops, and some of them may be lost. As a result, the missing packets must be retransmitted. The nodes lose energy as a result of these retransmissions. To control data overhead, a reliable method for WSNs is necessary. Only the super cluster head is responsible for transmitting data to the BS in the proposed SCHFTL. The proposed solution reduces data overhead, loss, and retransmission, resulting in a longer network lifetime.

**Preetha, M. and Nithya, M. \[[8](#08_ch3.xhtml#r3_8)\]** explain the encryption is a small modification of the well-known and practical RSA-OAEP. Even in the multi-query context, the security of the RSA problem remains significantly tied to the complexity of the RSA problem, according to this scheme. The RSA gives the business application the highest level of security. Furthermore, without using hybrid or symmetric encryption, this approach can be utilised to encrypt large messages.

**Ranida Hamidouche, Zibouda Aliouat and Abdelhak Gueroui \[[9](#08_ch3.xhtml#r3_9)\]** explain Wireless sensor networks, which are used in a variety of important applications such as health care and battlefield monitoring, face the problem of limited energy capacity. A distributed protocol based on genetic algorithms, called LECR-GA, is presented to achieve efficient energy use. Longer system operability and maximum data rate with minimal complexity were achieved by using the correct chromosomal representation, fitness function, and GA operations. The proposed algorithms outperform GABEEC and GAEEP in terms of energy usage and throughput, according to the findings of the experiments.

**Se-Ra Oh and Young-Gab Kim \[[10](#08_ch3.xhtml#r3_10)\]** explain the oneM2M (i.e., Mobius) OAuth 2.0-based security component is designed to offer authentication and authorization, which are critical security goals for IoT security and secure interworking between IoT platforms. The examples include a section of security component code, a token request, and a security component response. A resource request from an unauthorized user will be blocked by the oneM2M security component, whereas a resource request from an authorized user will be passed through.

**Yiqun Zhang, Li Xu, Qing Dong, Jingcheng Wang, David Blaauw, and Dennis Sylvester \[[11](#08_ch3.xhtml#r3_11)\]** explain the limited computing resources and required flexibility, IoT security presents numerous issues. ASICs and coprocessors on the market today have a number of drawbacks. In this study, we offer Recryptor, a new architecture that leverages in-memory and near-memory computation to support massive vector calculations for crypto algorithms effectively. When compared to baseline CPU architecture, it preserves programmability and saves approximately 80% of runtime and energy. In terms of balancing area, energy, throughput, and programmability, Recryptor is a reasonable intermediate option.

## III. PROBLEM STATEMENT

The clustering process causes a number of issues, including energy hole problem and network segmentation, which drastically increases the possibilities of threats in the sensor networks and reduces the network lifetime. The sensor nodes relay more data packets with nearby Cluster Head (CH) than far away sensor nodes, resulting in the early mortality of the CH. The energy hole problem in the network is divided into numerous distinct pieces. Due to a lack of sufficient communication links, the segments are unable to communicate with the Base Station (BS). Sensor nodes have sufficient energy for data transmission, but they are unable to relay data packets to the CH and BS due to a lack of network topology. The clustering mechanism consumes lot of extra energy to overcome energy hole problem and network partitioning issue. Rather, they use hardware resources to overwhelm the same.

## IV. PROPOSED WORK AND ALGORITHM PROPOSED WORK

There are three types of the phases explained in IoT-enabled wireless sensor networks. The first phase is Memetic algorithm based cluster creation. The second phase is data collection phase based mobile sink based data collecting and third phase is RSA algorithm based cryptography process.

Memetic Algorithm is used to elect CHs during the cluster building phase using a strict memetic approach. Data collecting describes a cluster creation method based on a memetic algorithm, followed by a data collection scheme based on a mobile sink. RSA based cryptography process algorithm uses key-based encryption and decryption mechanism to improve cryptography.

### ALGORITHM

#### RSA Algorithm

The algorithm is used for encrypting and decrypting a single integer. Converting larger (or different) pieces of information into (possibly big) numbers is the first step towards encoding them. Because RSA is a slow method, it is generally used to encrypt the key of a quicker algorithm. This supplemental technique uses the key decrypted by RSA to decode the rest of the message.

To decipher the algorithm mathematically, one must first solve the factoring issue (find the two prime numbers that, when multiplied, produce the given result). When the chosen numbers are large enough, the problem is difficult to solve by brute force, and there is currently no easier analytic solution.

#### Memetic Algorithm

The phase is identifying effective CHs in the network that can drastically lower the energy consumption of deployed nodes. As a result, for optimal CH selection, we adopt a memetic algorithm, an intelligence based optimization mechanism that provides a better optimal solution in a heterogeneous WSN environment.

A local search approach is being introduced via a genetic algorithm. It’s a meta-heuristic algorithm that uses evolutionary computation. It’s a nature-inspired search-based optimization challenge. It gives solutions that are close to ideal. The term “optimization” refers to the process of maximizing or minimizing objective functions based on input parameters. They offer a variety of options. These solutions are then mated and mutated, resulting in offspring, a process that occurs over several generations.

Each person has a fitness rating, and the fittest are picked to be parents. As a result, evolution will proceed until the termination condition is met. A genetic algorithm has the advantage of optimizing both continuous and discrete functions, as well as providing a pool of solutions rather than a single solution that improves with time. When a big number of factors are involved, it is an excellent option. It is a good fit for NP-hard problems.

The cluster head is found inside the network’s nodes using a memetic technique. It is split into two sections. If a node’s energy is larger than the average energy of the network’s nodes, that node can participate in the CH selection. The first bit string of the chromosome is created, with CH being assigned a value of ‘1’ and the rest of the nodes being assigned a value of ‘0’. When the aforementioned requirement is no longer true, a memetic algorithm is used to select the CH. The steady state phase, in which a fitness function is applied before crossover and mutation, is referred to as the steady state phase.

#### Initial Process

Parameters are selected that are responsible for network performance. The parameters are then given an initial value. Parameters include several sinks, number of nodes, the position of each node, dimension of the network, number of chromosomes, population size, crossover rate, mutation rate, and generation number, weight coefficients are initialized.

#### Fitness Function

These are the objective function that guides to take the solution to the aspiring results and optimize them. Then chromosomes are converged to better solutions by applying iterative fitness function generations after generations. It has to accelerate to the solution quickly and should correlate to the aim.

#### Cluster Formation

Initially generate the x and y co-ordinate value of the nodes. Initiate the Sink node. Sink node is divided into no of grid cells. The grid cell takes the midpoint to form a group of the nodes for grid formation. Create the grid formation to assign a grid id and node id to all nodes. Grids are square in form and static in nature in the network area. It may be a mobile or static during the collection of information at the sink. Among all the other nodes in the grid cell, the midpoint of the grid cell is initially chosen as a cluster head (CH). CH is chosen as the node that has a minimum distance to the midpoint. Node-id and grid ids are allocated to each node in the network.

#### Data Collection Phase

In the data gathering phase, a mobile sink follows the trajectory to a rendezvous location and then broadcasts a data uploading message in communication range 2R. The MS sends this data uploading message to the CHs in order to upload all of the network’s information. A mobile sink ID and location information are included in the message. This message will only be received by CHs that are all within the mobile sinks’ communication range. The CH verifies its buffer state after receiving the data upload message. If the CH’s current buffer is empty, the MS’s data uploading message is simply ignored. Otherwise, it sends a reply message to the mobile sink if the CH’s current buffer status is not empty. The CH ID, leftover energy, and position information are all included in the reply message. When the mobile sink receives a reply message from the CH, it allots a separate time slot to each responded CH. Every CH that communicates with the mobile sink is given their own time window. The CH can send its reply only in the assigned time slot. A proper scheduling is been performed among the CHs in the queue. Mobile sinks broadcast a schedule message in communication range 2R. The scheduling message contains the individual CH data uploading schedule.

#### Path Updating

Initialize the source node (S) and distance node (D) value. The source node and destination nodes check the present Cluster head of the group nodes. Source node is not up to destination node. After sending the results, the algorithm is implemented to verify the cluster group head. The source input, the source node’s value, includes the CH. Finally, to the Destination Node, CH is sent.

### ALGORITHM STEPS

#### 1. Enhanced RSA Algorithm Steps

*   Step 1: Generate two different primes *k* and *y*
*   Step 2: Give a key to present the file location
*   Step 3: Read the input key value and split character wise
*   Step 4: Calculate modulus *a* = *k* + *y*
*   Step 5: Calculate totient $(*n*) = (*k*\-1) \* (*y*\-1)
*   Step 6: Select the *e* integer of the public exponent, so that 1 < *e* < $(a) and gcd ($(a), *e*) = 1
*   Step 7: Calculate a value for *d* for a private exponent such that *d* = *e*\-1 mod $(*n*)
*   Step 8: Separated characters are arranged in ascending order and with new characters write new line
*   Step 9: Public key = \[e, a\]
*   Step 10: Private key = \[d, a\]

#### 2. Enhanced Memetic Algorithm Based Cluster Formation Steps

*   Step 1: Deploy BS and M[1] to form WSN
*   Step 2: Setup Phase
*   Step 3: for each *k* 1 to *n* do
*   Step 4: while *S*[ei] ≤ *E*[th] do
*   Step 5: Participate in election to Selection CH[k]
*   Step 6: if *S*[ek] > *S*[ei], 1 ≤ *j* ≤ *in*, *j* ≠ *k* then
*   Step 7: S[ek] Elect CH[k] of C[k]
*   Step 8: CH[k] bit = = 1 and ∀*S[i]bit* = = 0
*   Step 9: end
*   Step 10: end
*   Step 11: Steady State Phase
*   Step 12: Centralized configuration of the cluster by Mobile Sink
*   Step 13: Separate the each grid cell by node id and grid id after find the nodes distance and energy value
*   Step 14: The node chooses the CH (Cluster to find the value to check the low distance value and the highest energy value.
*   Step 15: Apply MA for next generation population and CH[k] Selection
*   Step 16: CH[k] bit = = 1 and ∀*S[i]bit* = = 0
*   Step 17: if CH[k] energy < E[th] then
*   Step 18: Calculate *F*[*n*] = (*ω*1\**α*+*ω*2\**β*+*ω*3\**γ*+*ω*4\**δ*)^( − 1)
*   Step 19: Apply crossover between two top competitors
*   Step 20: Calculate new chromosome after mutation
*   Step 21: Apply local search
*   Step 22: Select new CH[k]
*   Step 23: CH[k] bit = = 1 and ∀b’*S[i]bit* = = 0
*   Step 24: End

#### 3. Enhanced Data Collection Phase

*   Step 1: if MS is at a RP then
*   Step 2: broadcast uploading message at range 2R with mobile sink ID, location info
*   Step 3: Initially include the source and destination
*   Step 4: Initialize for loop and then include the all nodes after all nodes are check source node *F**o**r*(*j*\=0; *j*<*n*; *j*++)
*   Step 5: if CH receives uploading message from MS then
*   Step 6: if buffer of CH = = empty then
*   Step 7: Find source node present the group of cluster then, *f*(*s*!=*d*&amp;&amp;*s*\==*C**H*)*t**h**e**n*
*   Step 8 : Cluster message send from source to CH
*   Step 9 : if (d = = CH1 && CH! = CH1) then
*   Step 10: Cluster message send from CH to CH1 and CH1 send cluster message to destination
*   Step 11: Discard the message.
*   Step 12: else
*   Step 13: sends reply message to MS with CH ID, residual energy, location info
*   Step 14: end
*   Step 15: if Ms receives reply msg from CH then
*   Step 16: allot individual time slot
*   Step 17: End

### Flow Diagram

![Fig. 2 Flow Diagram of Proposed Method](images/page30_1_B.jpg)

**Fig. 2** Flow Diagram of Proposed Method

## V. SIMULATION ANALYSIS

**Simulation Parameters**

**Table 1** Simulation Parameters

 
| S. No || Environment / Parameters || Values |
| --- | --- | --- |
| 1 || Simulator || NS - 2 |
| --- | --- | --- |
| 2 || Channel Type || Wireless |
| 3 || Number of Nodes || 100 |
| 4 || Traffic Model || CBR |
| 5 || Simulation Area || 2250m \* 2250m |
| 6 || Transmission range || 400m |
| 7 || Routing Protocol || DSR |
| 8 || Mac Protocol || 802.11 |
| 9 || Simulation Total Time || 100ms |

**Performance Metrics**

This section emphasis the simulation performance of Enhanced Memetic Algorithm for IoT enabled WSN. The simulations have performed using network simulator (NS-2). The network simulator NS2 is discrete event simulation software for performing network simulations. It performs the simulation events such as sending, receiving, forwarding and dropping packets in the network. Some of the performance metrics of the protocol were discussed. Performance metrics used for comparison are,

*   End to End Delay
*   Packet Delivery Ratio
*   Network Lifetime
*   Energy Consumption
*   Throughput
*   Packet Lost

### i. End to End Delay

Time taken by the packet to travel from source node to the destination node is said End to End Delay time. It includes all the delay taken by the router to seek the path in network consumption, propagation delay, processing delay and End to end delay for packet pac which was sent by the node k, as a source node and received successfully at destination node is calculated by the formula

> ***EndtoEndDelay[kpac]*** = ***starttime[kpac]*** − ***endtime[kpac]***

Where start-time kpac is the time when sending of packet pack at node k starts, end-time kpac, is the time when packet pac is send by node k is received successfully at destination area.

### ii. Packet Delivery Ratio

Packet delivery ratio (PDR) signifies the total number of packets delivered from the source node to the destination node. It is used for calculating the packet loss rate during the data transmission.

While transmitting from the source node to destination node some packets may lost or erroneously routed to other node, in order to find this loss PDR is calculated and measures up both the correctness and efficiency of ad-hoc routing protocols in terms of the loss rate. A higher packet delivery ratio is hoped in any network is said as best transmission.

> ***Packet Delay Ratio*** = Σ ***Number of packet receive*** / Σ ***Number of packet send***

### iii. Energy Consumption

At the beginning of the simulation, the node has certain initial value that is the energy level of the node at the initial level of energy. This is termed as Initial Energy in the equation. In the simulation environment, the term “energy” represents the energy level in a node at a particular time supplied by the battery power or by other source. If any node in the simulation environment attains zero energy level, it cannot transmit or receive anymore packets it becomes idle.

> ***Nodes energy*** = ***Current[—]Energy*** − ***Initial[—]Energy***

### iv. Network Lifetime

The capability of monitoring the phenomena of interest among the nodes is the maximum duration of time during the deployed sensors in the simulation. Higherr range of Network Lifetime incurs the efficient performance.

> ***Lifetime = 100*** − Σ***Ai*** ΣAi - Average of energy

### v. Throughput

Total number of packets transmitted within the transmission time or successful data

transmission in the preferred time is termed as throughput value. The value of transmission is calculated as the average rate of successfully packets delivered from the source to destination node. It is represented in bits/bytes per second.

> ***Average throughput*** = ***Sum of packets successfully delivered*** − ***Total number of packets/Transmission time***

### vi. Packet Lost

Packet lost is difference between the total number of transmitted packets and Total number of received packets.

> ***Packet Lost*** = ***Number of Transmitted Packets*** – ***Number of received Packets***

## VI. RESULTS AND DISCUSSION

The experimental results of the proposed retrievals are experimented and evaluated in NS2. The simulation area is 2250 × 2250 meters. Then apply the 100 of the nodes in the given simulation area. Then the proposed algorithm is applied to the gathered propagation of the metrics.

The proposed and existing methods are measured with the help of the classification methods like that Enhanced Memetic Algorithm and Enhanced Data Collection Phase and Enhanced RSA Algorithm. These metrics results of the different method are discussed below.

 **Table II** End to End Delay 

 
| Time (ms)  || End to End Delay |
| --- | --- |
| Zigbee || ZRP |
| 0 || 10 || 10 |
| --- | --- | --- |
| 20 || 14.6321 || 12.5533 |
| 40 || 16.7812 || 14.0445 |
| 60 || 21.4381 || 19.5593 |
| 80 || 23.8123 || 21.6712 |
| 100 || 27.3541 || 24.9813 |

![Fig. 3 End to End Delay](images/page32_1_B.jpg)

**Fig. 3** End to End Delay

 **Table III** Energy Consumption 

 
|  || Energy Consumption |
| --- | --- |
| Time (ms) || Zigbee || ZRP |
| 0 || 100 || 100 |
| --- | --- | --- |
| 20 || 80.32 || 77.80 |
| 40 || 76.43 || 74.56 |
| 60 || 74.24 || 71.72 |
| 80 || 71.39 || 68.79 |
| 100 || 68.34 || 65.97 |

![Fig. 4 Energy Consumption](images/page32_2_B.jpg)

**Fig. 4** Energy Consumption

 **Table IV** Packet Delivery Ratio 

 
| Time (ms)  || Packet Delivery Ratio |
| --- | --- |
| Zigbee || ZRP |
| 0 || 1.57 || 1.57 |
| --- | --- | --- |
| 20 || 1.7625 || 1.7824 |
| 40 || 1.8254 || 1.8640 |
| 60 || 1.9354 || 1.9640 |
| 80 || 1.9952 || 2.0532 |
| 100 || 2.1089 || 2.1358 |

![Fig. 5 Packet Delivery Ratio](images/page32_3_B.jpg)

**Fig. 5** Packet Delivery Ratio

 **Table V** Throughput 

 
| Time (ms)  || Throughput |
| --- | --- |
| Zigbee || ZRP |
| 0 || 1.57 || 1.57 |
| --- | --- | --- |
| 20 || 43.12 || 45.19 |
| 40 || 50.36 || 50.36 |
| 60 || 58.53 || 60.18 |
| 80 || 63.12 || 66.78 |
| 100 || 68.29 || 70.52 |

![Fig. 6 Throughput](images/page33_1_B.jpg)

**Fig. 6** Throughput

 **Table VI** Network Lifetime 

 
| Time (ms)  || Network Lifetime |
| --- | --- |
| Zigbee || ZRP |
| 0 || 0 || 0 |
| --- | --- | --- |
| 20 || 1500 || 2000 |
| 40 || 5200 || 6800 |
| 60 || 10250 || 12000 |
| 80 || 12090 || 14000 |
| 100 || 15035 || 16000 |

![Fig. 7 Network Lifetime](images/page33_2_B.jpg)

**Fig. 7** Network Lifetime

 **Table VII** Packet Lost 

 
| Time (ms)  || Packet Lost |
| --- | --- |
| Zigbee || ZRP |
| 0 || 500 || 500 |
| --- | --- | --- |
| 20 || 450.29 || 425.28 |
| 40 || 382.54 || 350.17 |
| 60 || 290.26 || 265.23 |
| 80 || 260.48 || 210.98 |
| 100 || 190.95 || 150.28 |

![Fig. 8 Packet Lost](images/page33_3_B.jpg)

**Fig. 8** Packet Lost

## VII. CONCLUSION

For IoT-enabled wireless sensor networks, a memetic algorithm with mobile sink-based data gathering strategy is used to improve network performance. The proposed method contains a novel clustering strategy in which the memetic algorithm with Powell’s conjugate gradient mechanism is used to perform CH selection and cluster building. It significantly minimises cluster creation message overhead. The memetic algorithm with the Powells conjugate gradient mechanism, on the other hand, finds the appropriate number of CHs to minimise data transmission energy loss. In the proposed approach, the mobile sink chooses the best data gathering channel to collect data from several CHs, resulting in a significant reduction in end-to-end delay. The RSA algorithm uses encrypted bits with a public key that has a major impact on decryption time and cryptosystem strength. This eventually reduces the possibility of cyber threats or risks in the network. We have shown a variety of simulation results to assess the suggested scheme’s performance. It has been shown that the proposed algorithm outperforms in terms of throughput, network lifetime, energy consumption, packet delivery ratio, packet lost and throughput. As cyber risks continue to grow in sophistication, the proposed method outperforms well than the existing methods in terms of network performance and network security.

## REFERENCES

1.  [**Chuan Zhu, Kangning Quan, Guangjie Han and Joel J.P.C. Rodrigues**](#08_ch3.xhtml#r_r3_1). “A High-Available and Location Predictive Data Gathering Scheme with Mobile Sinks for Wireless Sensor Networks”, Computer Networks, Vol. 145, November 2018.
2.  [**Chunlin Li, Jingpan Bai, Jinguang Gu, Xin Yan and Youlong Luo**](#08_ch3.xhtml#r_r3_2). “Clustering Routing Based on Mixed Integer Programming for Heterogeneous Wireless Sensor Networks”, Ad Hoc Networks, Vol. 172, April 2018.
3.  [**Gurbinder Singh Brar, Shalli Rai, Vinay Chopra, Rahul Malhotra, Houbing Song and Syed Hassan Ahmed**](#08_ch3.xhtml#r_r3_3). “Energy Efficient Direction-Based PDORP Routing Protocol for WSN”, IEEE Access, Vol. 4, June 2016.
4.  [**Jianhua Huang, Danwei Ruan and Weiqiang Meng**](#08_ch3.xhtml#r_r3_4). “An annulus sector grid aided energy-efficient multi-hop routing protocol for wireless sensor networks”, Computer Networks, Vol. 147, December 2018.
5.  [**Jianhua Huang, Yadong Hong, Ziming Zhao and Yubo Yuan**](#08_ch3.xhtml#r_r3_5). “An energy-efficient multi-hop routing protocol based on grid clustering for wireless sensor networks”, Cluster Computing, Vol. 20, June 2017.
6.  [**Mbanaso, U. M. and Chukwudebe, G.A.**](#08_ch3.xhtml#r_r3_6) “Requirement Analysis of IoT Security in Distributed Systems”, 2017 IEEE 3rd International Conference on Electro-Technology for National Development (NIGERCON), Ieee, Vol. 5, Issue 7, February 2018.
7.  [**Moosa Ayati, Mohammad Hossein Ghayyoumi and Atiyeh Keshavarz-Mohammadiyan**](#08_ch3.xhtml#r_r3_7). “A fuzzy three-level clustering method for lifetime improvement of wireless sensor networks”, Annals of Telecommunications, Vol. 73, March 2018.
8.  [**Preetha, M. and Nithya, M.**](#08_ch3.xhtml#r_r3_8) “A Study and Performance Analysis of RSA Algorithm”, International Journal of Computer Science and Mobile Computing, Vol. 2, Issue. 6, June 2013.
9.  [**Ranida Hamidouche, Zibouda Aliouat and Abdelhak Gueroui**](#08_ch3.xhtml#r_r3_9). “Low Energy-Efficient Clustering and Routing Based on Genetic Algorithm in WSNs”, Springer, Mobile, Secure, and Programmable Networking, January 2019.
10.  [**Se-Ra Oh and Young-Gab Kim**](#08_ch3.xhtml#r_r3_10). “Development of IoT Security Component for Interoperability”, 2017 13th International Computer Engineering Conference (ICENCO), Vol. 12, Issue. 4, February 2018.
11.  [**Yiqun Zhang, Li Xu, Qing Dong, Jingcheng Wang, David Blaauw, and Dennis Sylvester**](#08_ch3.xhtml#r_r3_11). “Recryptor: A Reconfigurable Cryptographic Cortex-M0 Processor With In-Memory and Near-Memory Computing for IoT Security”, IEEE Journal of Solid-State Circuits, Vol. 9, Issue. 3, February 2018.