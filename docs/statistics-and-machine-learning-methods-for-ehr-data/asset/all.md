![image](images/Cover.jpg)

Statistics and Machine  
Learning Methods  
for EHR Data

**Chapman & Hall/CRC Healthcare Informatics Series**

**Series Editors  
Christopher Yang,** Drexel University, USA

**Recently Published Titles**

**Process Modeling and Management for Healthcare**  
*Carlo Combi, Giuseppe Pozzi, Pierangelo Veltri*

**Statistics and Machine Learning Methods for EHR Data: From Data Extraction to Data Analytics**  
*Hulin Wu, Jose-Miguel Yamal, Ashraf Yaseen, Vahed Maroufy*

For more information about this series, please visit: [https://www.routledge.com/Chapman–HallCRC-Healthcare-Informatics-Series/book-series/HEALTHINF](https://www.routledge.com)

Statistics and Machine  
Learning Methods  
for EHR Data

From Data Extraction  
to Data Analytics

Edited by  
Hulin Wu, Jose-Miguel Yamal, Ashraf  
Yaseen, and Maroufy Vahed

![image](images/logo.jpg)

First edition published 2021

by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2021 Taylor & Francis Group, LLC

CRC Press is an imprint of Taylor & Francis Group, LLC

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-0-367-44239-2 (hbk)

ISBN: 978-1-003-03000-3 (ebk)

Typeset in Palatino

by MPS Limited, Dehradun

# ![image](images/inline1_2.jpg)

# Contents

[Preface](#preface.xhtml#ST0)

[About the Editors](#preface.xhtml#ST0)

[List of Contributors](#contributor.xhtml#ST0)

[**1 Introduction: Use of EHR Data for Scientific Discoveries—Challenges and Opportunities**](#ch01.xhtml#chapter1)

Hulin Wu

[**2 EHR Project Management**](#ch02.xhtml#chapter2)

Yashar Talebi and Ashraf Yaseen

[**3 EHR Databases and Data Management: Data Query and Extraction**](#ch03.xhtml#chapter3)

Gen Zhu, Vi K. Ly, Michael Gonzalez, Leqing Wu, Hulin Wu and Ashraf Yaseen

[**4 EHR Data Cleaning**](#ch04.xhtml#chapter4)

Yashar Talebi, Han Feng, Yuefan Huang and Vahed Maroufy

[**5 EHR Data Pre-Processing and Preparation**](#ch05.xhtml#chapter5)

Duo Yu, Xueying Wang and Hulin Wu

[**6 Missing Data Issues in EHR**](#ch06.xhtml#chapter6)

Chenguang Zhang, Vahed Maroufy, Baojiang Chen and Hulin Wu

[**7 Causal Inference and Analysis for EHR Data**](#ch07.xhtml#chapter7)

Stacia M. DeSantis, Momiao Xiong, Jose-Miguel Yamal, Gen Zhu, Duo Yu, Xueying Wang, Chenguang Zhang and Vi K. Ly

[**8 EHR Data Exploration, Analysis and Predictions: Statistical Models and Methods**](#ch08.xhtml#chapter8)

Gen Zhu, Frances Brito, Stacia M. DeSantis and Vahed Maroufy

[**9 Neural Network and Deep Learning Methods for EHR Data**](#ch09.xhtml#chapter9)

Duo Yu, Ashraf Yaseen and Xi Luo

[**10 EHR Data Analytics and Predictions: Machine Learning Methods**](#ch10.xhtml#chapter10)

Yuxuan Gu, Yuefan Huang, Vi K. Ly, Ashraf Yaseen and Hongyu Miao

[**11 Use of EHR Data for Research: Future**](#ch11.xhtml#chapter11)

Hulin Wu

[Index](#index.xhtml#index)

#   
![image](images/inline1_2.jpg)

# [Preface](#contents.xhtml)  
               

Electronic medical records (EMRs) are digitized clinical charts and information in clinics, hospitals and healthcare facilities. EMRs contain the data of patients’ medical histories as well as other information collected in clinician’s offices, clinics or hospitals, and are mostly used by health care providers for diagnosis and treatment. EMRs allow clinicians to track patient data over time, identify patients for preventive visits and screenings, monitor patients and improve health care quality. Electronic health records (EHRs) are built to go beyond standard clinical data gathered in a health care provider’s office or clinic; instead, EHR systems are much broader in health-related data collection. EHRs contain digitized data and information on a patient from all the clinicians and health providers involved in a patient’s care. EHR systems are also designed to share the data and information with all authorized clinicians, caregivers, stakeholders and the patients themselves. EHRs may also contain the data and information from and to be accessed by laboratories, specialists, nursing homes and other health care providers across the region or even across the country. With fully functional EHRs, all authorized healthcare providers at any location or any organization have ready access to the latest information on patients, allowing for more coordinated, patient-centered care.

Although EMR systems started in the 1960s, they became more visible after the Internet became more popular in this new century. As a part of the American Recovery and Reinvestment Act, all public and private healthcare providers were required to demonstrate “meaningful use” of EMRs by 1 January 2014. The EMR system was initially designed primarily for the purposes of documentation, billing and clinical practice support. The use of EMR or EHR data for research and scientific advancement is still in its infancy. The use of EMR or EHR data to generate real-world evidence to support decision-making processes in clinical practice and scientific research is challenging but promising. In this book, we intend to address some of the challenges based on our experiences, particularly, from statistical and data science perspectives. So far, statistical literature for EMR/EHR data processing and analysis is sparse, although there are many data processing and analysis issues and challenges that require more attention from statisticians and data scientists. We have identified some significant questions and issues that need to be addressed for initial EMR/EHR data exploration and analysis. In this book, we focus mainly on sharing our experiences for EMR/EHR data processing and analytics, and supplement this with an overview of general methodologies and approaches.

*Statistics and Machine Learning Methods for EHR Data: From Data Extraction to Data Analytics* is one of the Big Data projects initiated by the newly established Center for Big Data in Health Sciences (CBD-HS) at the School of Public Health, University of Texas Health Science Center at Houston (UTHealth SPH). We started an EHR Working Group consisting of faculty members, students and research staff from the School of Public Health, School of Biomedical Informatics, McGovern Medical School and Cizik School of Nursing in UTHealth in the fall of 2017. The EHR Working Group initiated the first project on evaluation of vasopressor treatments for subarachnoid hemorrhage (SAH) patients, which was proposed by our clinical collaborator, Dr. George Williams, MD, FCCP, Associate Professor, Director of Critical Care, Department of Anesthesiology, McGovern Medical School, UTHealth, in November 2017. From 2018–2020, more than 20 faculty members and students joined the EHR Working Group and began to further explore a large nationwide EHR database (Cerner Health Facts) for more research projects and scientific discoveries.

In this book, we will review and illustrate the EMR/EHR data processing and analysis methods in a systematic way. The book consists of 11 chapters. In Chapter 1, after a brief introduction to EHR data challenges and opportunities, we propose and discuss the whole cycle of an EHR research project. EHR project management is introduced in Chapter 2. Since a large EHR database can be used for many research projects, it is necessary to manage these projects in an efficient way so that the resources can be leveraged and the reproducibility of the results can be ensured. Chapters 3–5 describe three important steps to extract, clean, process and prepare the EHR data before any formal data analysis can be performed.  Based on our experience, these steps can be very time consuming and tedious. In these three chapters, we will share our experience for data extraction, cleaning, processing and preparation using examples from our EHR research projects. Missing data and many confounding factors are two major problems for observational studies and they are more challenging for EHR data. Chapters 6 and 7 provide an overview on the methodologies that can be used to deal with these two issues. We review some basic statistical methods for EHR data exploration and analysis in Chapter 8. Chapters 9 and 10 focus on machine learning methods, including neural network and deep learning approaches for outcome predictions based on EHR data. Finally, we briefly discuss the future trend of EHR data research in Chapter 11. Actual EHR research projects and examples are used to illustrate the methodologies, and the computer codes for implementing the methods are provided. A website ([http://sph.uth.edu/dept/bads/ehr-research](http://sph.uth.edu)) for this book was established to provide updates and share our computer codes and other information with readers.

For readers who have little experience in EMR/EHR data and databases, you should read Chapters 1–5 carefully since these chapters provide an overview of EHR data features and data processing challenges. For statisticians who are familiar with basic statistical methods, missing data approaches and causal inference for dealing with confounding factors, you may skip some of the contents in Chapters 6–8. Chapters 9–10 provide an overview of machine learning methods for EHR data analysis and predictions with real data examples, which are good for those readers who are not familiar with these methods and their applications to EHR data. Readers may gain some ideas on the future trends of EHR data research from Chapter 11.

We deeply appreciate all the EHR Working Group members who have made significant contributions to the EHR research projects. Their novel ideas and insightful discussions inspired us to write this book. In particular, we would like to take this opportunity to thank Dr. George Williams, MD, Associate Professor and Director of Critical Care, and Dr. David Aguilar, MD, Associate Professor of Cardiovascular Medicine and Epidemiology, at UTHealth, who provided clinical and scientific guidance to the EHR Working Group during EHR data extraction, cleaning, processing and analysis during the past few years. We are also grateful to all the investigators and students from UTHealth School of Public Health, School of Biomedical Informatics, McGovern Medical School and Cizik School of Nursing, who have participated in the EHR Working Group discussions and worked on different EHR research projects. Without their involvement and contributions, it would have been impossible for us to complete this book in a timely manner.

Hulin Wu, Jose-Miguel Yamal, Ashraf Yaseen, Vahed Maroufy  
EHR Working Group  
Center for Big Data in Health Sciences  
Department of Biostatistics and Data Science, School of Public Health  
University of Texas Health Science Center at Houston  
Houston, Texas, USA

# ![image](images/inline1_2.jpg)

# [About the Editors](#contents.xhtml)  
               

**Hulin Wu**, PhD, is the Betty Wheless Trotter Professor and Chair, Department of Biostatistics & Data Science, School of Public Health (SPH), University of Texas Health Science Center at Houston (UTHealth). Dr. Wu also holds a joint appointment as professor at UTHealth School of Biomedical Informatics. Dr. Wu received BS and MS training in engineering and a PhD in statistics. He has many years of experience in developing novel statistical methods, mathematical models and informatics tools for biomedical data analysis and modeling. He is the Founding Director of the Center for Big Data in Health Sciences (CBD-HS) and he is the director of the EHR Research Working Group at UTHealth SPH.

**Jose-Miguel Yamal**, PhD, is a tenured associate professor in the Department of Biostatistics & Data Science and a member of the Coordinating Center for Clinical Trials at UTHealth School of Public Health. Dr. Yamal has extensive experience in clinical trials including data coordinating centers and has served on Data Safety Monitoring boards for clinical trials in stroke and traumatic brain injury. He has also contributed toward statistical methodologies for classification problems for nested data as well as machine learning applications.

**Ashraf Yaseen**, PhD, is an assistant professor of data science at the School of Public Health, UTHealth. He has extensive experience in database design, implementation and management, machine learning and high-performance computing. In his current research, Dr. Yaseen is exploring big data integration and deep learning technologies for EHR data to address clinical and public health questions.

**Vahed Maroufy**, PhD, is an assistant professor, Department of Biostatistics & Data Science, UTHealth School of Public Health. Dr. Maroufy received MSc and PhD training in statistics and has experience in applied and theoretical statistics, including geometry of statistical models, mixture models, Bayesian inference, predictive models using EHR data and analysis of genetic data in cancer research.

# ![image](images/inline1_2.jpg)

# [Contributors](#contents.xhtml)  
               

**Frances Brito, MSc**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Baojiang Chen, PhD**

Associate ProfessorDept. of Biostatistics and Data ScienceUTHealth School of Public Health Austin, TX, US

**Stacia M. DeSantis, PhD, AB**

Professor Dept. of Biostatistics and Data Science UTHealth School of Public Health Houston, TX, US

**Han Feng, MS, BS**

Dept. of Biostatistics and Data Science UTHealth School of Public Health Houston, TX, US

**Michael Gonzalez, MS**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Yuxuan Gu, MPH, BM**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Yuefan Huang, MS, BA**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Xi Luo, PhD**

Associate ProfessorDept. of Biostatistics and DataScience UTHealth School of Public Health Houston, TX, US

**Vi K. Ly, BS**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Hongyu Miao, PhD, MS**

Associate Professor Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Yashar Talebi, MD**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Xueying Wang, MS, BS**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Leqing Wu, PhD, BS**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Momiao Xiong, PhD**

Professor Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Duo Yu, MS, BS**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Chenguang Zhang, MS, BS**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

**Gen Zhu, MS, BS**

Dept. of Biostatistics and Data ScienceUTHealth School of Public Health Houston, TX, US

# [1](#contents.xhtml#toc1_4)  
![image](images/inline1_1.jpg)

# [Introduction: Use of EHR Data for Scientific Discoveries—Challenges and Opportunities](#contents.xhtml)  
               

Hulin Wu

## ![image](images/inline1_1.jpg)  
1.1 Real-World Data and Real-World Evidence: Big Data in Practice

In this new era of advanced digital technologies, a huge amount of data is rapidly generated from all walks of life. In particular, the data generated from biomedical research fields and patient care practice are extremely valuable in improving public health and quality of life. Big Data is often a product of real-world practices and daily business operations and not specifically collected for research purposes. In order to use (or reuse) these real-world data to extract meaningful insights for scientific discoveries, there are many technical, analytical, and interpretation challenges and issues that need to be addressed. At the same time, great opportunities exist.

The real-world data such as the data from electronic medical record (EMR) or electronic health record (EHR) systems could provide real-world evidence for important clinical and scientific questions. These data can complement data from well-designed experiments and randomized controlled trials (RCTs), which are considered as the gold standard in clinical research and evidence-based medicine ([Van Poucke et al. 2016](#ch01.xhtml#ref1_23), [Frieden 2017](#ch01.xhtml#ref1_8)). Usually, the environment and conditions for the designed experiments and RCTs are different from the real world and the inclusion/exclusion criteria of many RCTs are very restrictive since the designed experiments and RCTs are trying to control the noise levels and balance potential confounding factors between study groups. Usually, the confounding factors, including unknown or unmeasured confounding factors, are randomly balanced between treatment and control groups, thus, the conclusions from the well-designed experiments and RCTs are statistically and scientifically valid. However, the well-designed experiments and RCTs also have some limitations. First, the generalizability of the designed experiments and RCTs may be limited due to the following reasons: 1) the inclusion/exclusion criteria may be too restrictive; 2) the environment of designed experiments and RCTs may be different from the real-world situation; 3) subjects who consent to participate in a clinical trial may have significant differences in characteristics from those in a general population; and 4) the sample size is limited in a specific population for the convenience of subject recruitment, study implementation, and ethical considerations. In addition, the conclusion from RCTs is usually based on the population mean effect, and the individual effect of treatments or interventions are ignored. Moreover, the RCTs are often expensive with a high cost in labor and time and sometimes the RCTs are infeasible due to ethical issues and other reasons. That is why currently RCTs only provide support to 10–20% of clinical decisions ([Mills, Thorlund, and Ioannidis 2013](#ch01.xhtml#ref1_18), [Tricoci et al. 2009](#ch01.xhtml#ref1_22), McGinnis et al. 2013). It is necessary to use the data from observational studies and real-world data to provide complementary evidence for clinical decisions. Some literature suggests that the results from the RCTs and nonrandomized observational studies have strong agreements ([Anglemyer, Horvath, and Bero 2014](#ch01.xhtml#ref1_1), [Ioannidis et al. 2001](#ch01.xhtml#ref1_13)). In addition, we also expect that real-world data could be used to better design and inform RCTs.

The use of large hospital discharge records, disease registry databases, Intensive Care Unit (ICU) databases and insurance claim databases have recently become popular for clinical and epidemiological research. However, the complete and large EMR or EHR databases from real-world clinical practice, including both in-patient and out-patient data from many hospitals and clinics, are not easily accessible to researchers. This type of EHR data could provide a more complete profile for patients’ health records. Harnessing big EHR databases allows researchers to investigate rare diseases, low-frequency conditions and long-term adverse events, and to address many important questions from personalized treatment and precision medicine perspectives.

Real-world data often have the features of “Big Data” ([Laney 2001](#ch01.xhtml#ref1_16)), including big volume, big variety and big velocity (“3V” features of Big Data). At the same time, the real-world data are often noisy with a big variability and we also need to evaluate their reliability (veracity) in order to ensure the reproducibility of analysis results. We expect that the real-world data could produce a big value if appropriate analyses are performed, and bias and confounding factors are carefully handled.

In this book, we focus on EHR data, which are real-world data coming from patient care systems, including in-patient hospitals and out-patient clinics. The EMR or EHR systems are originally designed for clinical practice, documentation, and billing purposes. Thus, the EMR or EHR data were not collected for research or analysis purposes. If we try to reuse the EMR or EHR data to address clinical or scientific questions, we need to overcome many barriers and deal with a lot of problems in the real-world data. In this book, we share our experience in addressing these issues for scientific discoveries. This will include data extraction, cleaning, pre-processing, preparation, analysis, and modeling.

This book was based on the authors’ experience mostly from the Cerner Health Facts database ([Cerner 2020](#ch01.xhtml#ref1_4)), a de-identified and longitudinal electronic health record (EHR) database to facilitate research. Our current version of the Cerner EHR database covers all of the healthcare records for 85 systems with 750 hospitals and healthcare facilities in the United States from 2000 to 2018 (19 years’ records). The main patient-level data in Cerner include longitudinal encounters with detailed records of diagnoses, medications, clinical events, procedures and lab procedures. It represents a total of 69 million unique patients across the United States. Of the 69 million patients, 52% are female and 42% are male (6% are gender-unidentified). The racial makeup of the 69 million patients is 52.8% Caucasian, 11.8% African American, 3.0% Hispanic, 1.8% Asian, 0.7% Native American, 6.1% other races (including Asian/Pacific Islander, Biracial, Mid Eastern Indian, Pacific Islander), and 23.7% racial status unknown. In total, the database includes 487 million unique encounters with 939 million diagnoses, coded in International Classification of Diseases (ICD-9 and ICD-10) codes. The database has 674 million medication records, 118 million procedure records, 5.3 billion clinical event records and 4.2 billion lab procedure records.

By 2016, in collaboration with biomedical informaticians, we began to work on an earlier version of the Cerner EHR database. We started an EHR project with predictions of heart failure using the Recurrent Neural Network (RNN) machine learning model ([Rasmy et al. 2018](#ch01.xhtml#ref1_21)). Another collaboration project was to establish a disease-disease network based on the disease comorbidities of all patients in the Cerner EHR database. In Fall 2017, we formally established an EHR Working Group with the support of the newly established Center for Big Data in Health Sciences in the Department of Biostatistics and Data Science, School of Public Health, University of Texas Health Science Center at Houston (UTHealth). This working group consists of statisticians, biomedical informaticians, data scientists, data managers, computer programmers, epidemiologists, clinicians and other investigators from the School of Public Health, School of Biomedical Informatics, McGovern Medical School and Cizik School of Nursing in UTHealth. This multidisciplinary team, including faculty, research associates, students and research staff, started to work together to harness the Big EHR database for scientific discoveries. The EHR Working Group initiated the first project on evaluation of vasopressor treatments for subarachnoid hemorrhage (SAH) patients, which was proposed by our clinical collaborator, Dr. George Williams (MD and FCCP, Associate Professor, Director of Critical Care, Department of Anesthesiology, McGovern Medical School, UTHealth) in November 2017. In Summer 2018, four PhD students were recruited to start the Cerner EHR data cleaning for the SAH project. This SAH project has resulted in publications in both biomedical journals and statistical journals ([Williams et al. 2020](#ch01.xhtml#ref1_24), [Yu et al. 2020](#ch01.xhtml#ref1_25), [Brown et al. 2020](#ch01.xhtml#ref1_3)). In April 2019, we acquired a new version of the Cerner EHR database with the data records from 2000 to 2018, and several new EHR projects, including projects of HIV/AIDS, hospital-acquired infections and antibiotics drug-resistance, and diabetes, were initiated based on this new version of the Cerner EHR database. This book is mainly based on our accumulated experience from these completed and ongoing projects over the past years.

## ![image](images/inline1_1.jpg)  
1.2 Use of EMR/EHR Database for Research and Scientific Discoveries: Procedure and Life Cycle

Electronic medical records (EMRs) are a digital version of the paper charts of patients in the hospital, clinic or clinician’s office. An EMR system usually contains the medical and treatment history of patients to help with the clinician’s decision on diagnosis and treatment for patient care. EMRs allow clinicians to better track patient’s data over time, identify and remind patients for preventive checkups and disease screenings, monitor patients and improve healthcare quality. Electronic health records (EHRs) are much broader than EMRs and contain all relevant health data of patients in addition to EMRs, which may include the data from laboratories, specialists, nursing homes and other healthcare providers. EHR systems are also designed to share the patient’s data with all authorized clinicians, caregivers, stakeholders, and even the patients themselves. Thus, a fully functional EHR system enables all authorized healthcare providers to access the latest information of patients anywhere and at any time so that more coordinated and patient-centered care can be provided timely to the patients. At the same time, the EHRs also serve as documentation for administration and billing purposes. Recently, EHR data became one of the major sources for real-world evidence to evaluate treatments, improve diagnosis and healthcare quality, reduce side effects and adverse events of drugs, predict disease risks and treatment outcomes, optimize and personalize patient care (MIT [2016](#ch01.xhtml#ref1_5)).

Since EHR data are very complex and noisy, analysis and interpretation require sophisticated statistical methods and data science techniques as well as multidisciplinary collaborations between data scientists and domain experts. In addition, a novel data-driven research paradigm and state-of-the-art approaches from a systematic perspective are necessary in order to harness a big EHR database and translate it into clinical knowledge for best practice. Based on our experience and from a systematic perspective, we summarize the procedure and the life cycle to use the EHR database for research and scientific discoveries in the following steps:

1.  Initiate a project: proposing a research topic with some potential high-impact biomedical/clinical questions or hypotheses
    
2.  Data queries and data extraction
    
3.  Data cleaning
    
4.  Data pre-processing or processing
    
5.  Data preparation
    
6.  Data analysis, modeling and prediction
    
7.  Result validation
    
8.  Result interpretation
    
9.  Publication and dissemination
    

This procedure is quite similar to the data mining procedure for knowledge discoveries in databases (KDD) ([McLachlan 2017](#ch01.xhtml#ref1_17), [Fayyad, Piatetsky-Shapiro, and Smyth 1996](#ch01.xhtml#ref1_6), [Fernández-Arteaga et al. 2016](#ch01.xhtml#ref1_7), [Holzinger, Dehmer, and Jurisica 2014](#ch01.xhtml#ref1_11), Mitra, Pal, and Mitra 2002). We will provide the details and explanation for each of these steps in the following sections.

### 1.2.1 Initiate a Project

To initiate a project, one should start by proposing a research direction or topic, usually with a focus on a particular disease, treatment, medication, or other conditions of interest. Ideally, domain-specific clinicians, epidemiologists, or biomedical scientists in the multidisciplinary team may initiate a project with some potential biomedical or clinical hypotheses or scientific questions, although it may not need to be specific. Since the EHR database usually contains data from a large number of patients and covers many different diseases, treatments and conditions, it is easy to raise many clinical, biomedical, or epidemiological questions. However, it may not be easy to identify a good question.

What is a good question? Based on our experience, a good research question based on the EHR database should satisfy the following criteria:

*   Clinically or scientifically important and high-impact: If we could answer the question or prove/disprove the hypothesis, the results and conclusions are clinically important with a high impact so that we can publish the results in a high impact journal.
    
*   Appropriate to use the available EHR data to address: The EHR data are appropriate or even the best data to address the proposed question or hypothesis. Sometimes the available EHR data may not be good or the best for the question or hypothesis. It is ideal if one can justify that using EHR data is the only way to address the proposed question or hypothesis and there is no other alternative.
    
*   Appropriate and reliable endpoint or outcome data are available or can be derived from the EHR database for the proposed question or hypothesis. For any clinical or scientific question and hypothesis, appropriate endpoints or outcomes must be defined and identified, and sometimes good biomarkers can be used. It is necessary to confirm that these endpoint or outcome data are available and reliable in the EHR database. For example, to use mortality as the outcome or endpoint to evaluate a disease treatment, the researcher needs to carefully evaluate whether the EHR system captures the mortality reliably for most of the death cases due to the treatment. However, for chronic disease treatments, this may not be true since the follow-up time is usually not long enough to capture death due to the chronic diseases by the EHR system.
    
*   The sample size is big enough: The sample size (the number of subjects, events and/or measurements) is usually quite large in the EHR database. However, for a particular question or hypothesis, we must screen the subjects based on the inclusion/exclusion criteria. For questions or hypotheses related to rare diseases or rare events, the sample size may still be an issue. Thus, it is also crucial to carefully define the study cohort based on the proposed question or hypothesis and develop the appropriate inclusion/exclusion criteria in order to ensure the sample size to be large enough.
    

The types of observational studies include 1) Case study or case report, a descriptive report on one or a series of special or unique clinical cases, which is a good source to generate hypotheses, instead of exploring any association or cause-effect relationships; 2) Cross-sectional study, the data of exposure or intervention/prevention treatments and outcomes are collected simultaneously from a specified population at a given time point via a survey or other approaches. These kinds of studies are typically used to define incidence, prevalence and associated risk factors for diseases or outcomes, but it is difficult to identify causal-effect relationships using cross-sectional studies; 3) Case-control study, based on the historical data, the subjects of controls are selected to match those of the cases for important factors so that these two groups of outcomes can be compared fairly in some sense. This kind of study can be used to compare the effectiveness of exposures, treatments and prevention/intervention strategies, but caution has to be taken due to sample selection bias and potential confounding factors of observational studies; 4) Cohort study, including both prospective and retrospective cohort studies with longitudinal data collected over a period of time. This kind of study can provide some evidence on the causal-effect relationships between the exposure and outcome; and 5) Real-world data study, the data such as EHR data are collected for business operation, reporting and practice purposes. These kinds of data were not collected for research purposes, but it can be used to formulate the four types of studies mentioned above based on real-world data. Furthermore, the real-world data such as EHR and insurance claim databases can be used to develop accurate predictive models for future disease burdens and outcomes, and pharmacovigilance to detect rare drug adverse events due to its long-term follow up time period and large sample size.

Notice that some questions such as treatment evaluation or group comparisons may not be easy to address using the retrospective EHR data. This is because the patients are not randomized to the comparison groups and the results can be confounded by many factors including patient severity that may not be available from the EHR database. Causal inference approaches may help address this confounding problems to some degree. Thus, in formulating a good study question or hypothesis, one should try to avoid comparison between groups unless the fair comparison can be justified or supported by the data.

To identify a good clinical research question based on the EHR database requires close collaborations between domain clinical/epidemiological scientists and data scientists. Initial data exploration is necessary and it may take several iterative interactions between domain-specific clinicians/epidemiologists and data scientists before a good question or hypothesis can be identified. The question or hypothesis may be modified or changed during the data exploration and even during the data analysis stage. A vague or general question regarding a disease, treatment or condition can be an initial target to start data exploration by statisticians and data scientists. The data exploration results can be presented to the clinical or epidemiological experts so that more specific questions or hypotheses can be gradually identified. A data extraction summary statistics report (see [Chapter 3](#ch03.xhtml#chapter3) for details) may be drafted to serve as a communication channel between the data scientists and domain-specific clinicians/epidemiologists. It is possible that the initial clinical or epidemiological question can be modified, improved, or even completely changed based on the data exploration results. Sometimes, the clinical question or hypothesis may not be finalized until the final data analysis is done. Data visualization and descriptive/summary statistics are usually used for initial data exploration in order to identify a good clinical question or hypothesis.

Our focus here is on clinical or scientific research projects. One may also initiate a statistical or computational methodology research project based on the EHR database. The procedure or life cycle for a methodology research project is different and will not be discussed in this book.

### 1.2.2 Data Queries and Data Extraction

The EHR database should be converted into a structured relational database for easy querying and data extraction. Ideally, the database is converted into the OMOP Common Data Model ([OHDSI 2020](#ch01.xhtml#ref1_20)) that allows for the systematic analysis of disparate observational databases. The concept behind the OMOP Common Data Model (CDM) is to transform the data from different databases into a common format (data model) and a common representation (terminologies, vocabularies, coding schemes, etc.) so that systematic analyses can be performed using a library of standard analytic routines that have been written based on the common format.

Querying the database to extract the relevant data for a particular clinical research question is not trivial sometimes. To establish the inclusion/exclusion criteria for data extraction, one needs to be familiar with the database structure and the terminologies, vocabularies and coding systems for diseases, medications, clinical events, vital signs, lab tests, procedures, etc. For example, to extract the data from all the patients with a particular disease diagnosis such as stroke, heart failure and diabetes, it may not be easy to get a full list of all disease diagnosis codes related to a particular disease. The keyword search of the disease code description may not get a complete list if the correct keywords related to the disease are not appropriately identified. The clinical domain experts need to be consulted for this purpose. Some natural language processing techniques may need to be used to deal with this problem.

It is warranted to develop and use more robust data extraction approaches to avoid or minimize data extraction errors since the data analysis results and conclusions are not reliable if the data extraction error or uncertainty is too big. Sometimes, it may require redundant data extractions by multiple people and/or multiple approaches to avoid errors or mistakes. In order to use all the data from the EHR database to address a clinical question or hypothesis, one key principle for data extraction is to extract all the relevant data and not drop any data before exploring the data carefully. This suggests that all the data from all relevant subjects from all EHR tables should be extracted. Each of the variables in all the EHR tables should be considered and explored. The data at different encounters should be carefully reviewed. The time period for data extraction should be well defined for a particular clinical question or hypothesis.

Another data extraction problem is that the data of any variables in the EHR database may contain errors. For example, if one is trying to extract the data from patients 18 years or older, the age or birth date of the patients may contain errors. The extracted data may include the data from some of the patients who are younger than 18 years due to errors. If the data are extracted from patients with a particular disease, the disease diagnosis may also contain errors. How to confirm a patient with a particular disease is not trivial either. All these errors are difficult to validate and correct since these are historical data from the EHR system and the subjects cannot be traced back. Thus, there always exists some degree of uncertainty in extracting the data for the targeted cohort of patients based on the inclusion/exclusion criteria provided by domain experts. EHR phenotyping approaches ([Banda et al. 2018](#ch01.xhtml#ref1_2), [Glicksberg et al. 2018](#ch01.xhtml#ref1_9), [Hubbard et al. 2019](#ch01.xhtml#ref1_12), [Gronsbell et al. 2019](#ch01.xhtml#ref1_10)), including rule-based methods, national language processing or text mining methods, regression and machine learning methods, and latent variable approaches, can be used for cohort identification (see [Chapter 3](#ch03.xhtml#chapter3) for more details). Phenotyping may need to be performed after data cleaning (next step) if necessary. In addition, it is challenging to consider data extraction errors and uncertainties in the subsequent data analysis.

### 1.2.3 Data Cleaning

We carefully define “data cleaning” and distinguish it from the data processing/pre-processing and data preparation. Data cleaning is the process to remove redundancies, correct errors, standardize the inconsistency of coding systems, unify the units of the variables, and combine the data or variables that were mistakenly spread out in different tables or wrong places. Some data cleaning examples include:

*   Some patients may have multiple and conflicting race, gender or birthdate (age) records from different clinical visits (encounters) that need to be unified.
    
*   The disease diagnosis table may use different disease coding systems such as ICD-9, ICD-10 or ICD-10-CM that need to be standardized.
    
*   The same medication may have different spellings of its generic names.
    
*   Some lab test results or clinical event measurements may use different units at different encounters for different patients.
    
*   The procedure, surgical procedure and other tables may also use different coding systems that need to be standardized.
    

Data cleaning is not dependent on a particular project or a particular purpose of data analyses, it should be done for the whole EHR database since this is needed for all the projects and all the data analyses unless a project aims to study the errors of EHR data entry or data management. A challenge for data cleaning is that we may not be able to identify all the possible errors from the data and some errors are not trivial to detect. Thus, the cleaned data may still be error-prone, which may not be easy to handle.

### 1.2.4 Data Pre-Processing or Processing

Before we perform formal data analyses to address a clinical or scientific question, we must always process the data, summarize the data or extract useful features from the data in order to analyze the data or fit a statistical model to the data. Data pre-processing or processing may include the following tasks:

*   Summarize the data into new data variables or generate some derived variables from the original data.
    
*   Deal with the data issues: e.g., missing data imputation or redundant data combination.
    
*   There are multiple timestamps for a clinical visit (encounter), medication, clinical event, procedure or other event and some of these timestamps are missing. A standardized timestamp is needed for each event and a rule for imputing the missing timestamp needs to be established for different purposes.
    
*   Derive different features based on the repeated measurements of some variables.
    
*   Extract features using feature engineering and dimension reduction approaches.
    

The data pre-processing or processing is project-specific. Different projects may require processing the data in various ways for different purposes. Usually, this step may need to be iteratively performed with the next step, data preparation, and these two steps may not have a clear boundary.

### 1.2.5 Data Preparation

After data cleaning and data processing, we need to prepare the data in various formats for different purposes of analyses. Data preparation is purpose-driven, and different objectives for a project may require the data to be prepared in different ways. Thus, even for a particular project, many versions of the data set may need to be prepared for different analyses and different purposes. Data preparation may include, but are not limited to, the following tasks:

*   Project-specific data cleaning for data preparation: For example, some encounters for a patient may overlap with each other or have close time intervals and we may need to combine or separate the overlapping encounters in order to perform particular data analysis.
    
*   Define, classify and label the patients for different outcomes or endpoints for different purposes.
    
*   Define the encounters or time intervals to prepare the data for different analysis purposes.
    
*   Prepare the data for different scenarios or cases, including sensitivity analysis purposes.
    

As aforementioned, data preparation and data processing may need to be iteratively performed. Since many versions of the prepared data may be created in this step, it is very important to document or label the latest version of the prepared data and make sure that all the team members use the correct version of the prepared data for final data analyses.

It is very time consuming and tedious to perform data cleaning, processing and preparation before formal data analyses can be performed. It is also easy to make mistakes and these mistakes may render the data analysis invalid. Thus, it is recommended to perform Steps 3–5 carefully and patiently. In order to appropriately process and prepare the data for a particular research question or hypothesis, it may require data visualization and heavy data exploration using some statistical methods and tools. After initial data exploration and data processing, we may further evaluate whether the original question or hypothesis can be addressed based on the extracted EHR data. It is quite often that we may need to modify or change the original questions based on the results of initial data exploration and data processing. Sometimes we may even completely change to new questions that are answerable based on the processed and prepared data. It is necessary to have close interactions and collaborations between data scientists and clinical/epidemiological domain experts in performing Steps 3–5.

### 1.2.6 Data Analysis, Modeling and Prediction

In the formal data analysis step, one must carefully deal with many issues. First, it is challenging to select a statistical model or method for a particular scientific question since there are many models and methods available for a particular question. Different models and different analysis methods may produce different results and different conclusions, thus, it is critical to select the appropriate models and data analysis methods. Sensitivity analyses may be necessary to ensure that the results are reproducible and reliable.

Second, there are many data analysis issues that we need to address. For example, there are many variables available from the EHR database, including disease diagnoses, medications, clinical events (including vital signs), lab results, procedures etc. Not only we have to deal with high-dimensional data problems, but many of these variables are also binary or categorical (ordinal) data, with a high missing rate. Many of these variables are also highly correlated, which may require novel dimension-reduction approaches before data analyses. It is also challenging to adjust for high-dimensional confounding factors when we use the observational EHR data for group comparisons. Some new casual inference and analysis methods are needed to deal with this issue. As mentioned above, the extracted data from the EHR database contains errors and uncertainties, and therefore the cohort or subject population may not be well defined. It is warranted to develop new methods to take these uncertainties into account in the follow-up data analysis and inference.

Prediction is one of the important tasks in big EHR data analysis. The term “prediction” is not well defined in the Big Data or data science community. Sometimes prediction and estimation terms are used interchangeably. For better communications, we need to clearly define what “prediction” means: predicting an unknown quantity or occurrence of an event in the future based on the historical data occurred or collected before that future event. In this case, we need to clearly define the time interval of the historical data (observation window) and the prediction window (the time from the last time point of the historical data to the first time of the event or quantity that needs to be predicted). If one intends to estimate a quantity, parameter or event within the observation window, we should call it “estimation” instead of “prediction”. Following the concept from engineering, if we are trying to estimate a state or a quantity at the last time point of the historical data, we can call it “filtering”, which means to filter out the observational noise. Based on this clarification, we need to clearly involve the “time-stamp” in the prediction model and make sure that the prediction is regarding estimation or prediction of a quantity, parameter or event for a future time based on the historical data.

It is also important to draft a data analysis report to carefully document the assumptions, models, methods, results and conclusions in detail. The report may also include a brief introduction for the overall project, the objectives of data analyses, study design, inclusion/exclusion criteria for data extraction, a summary of the data cleaning, processing and preparation steps. The analytic models and methods with corresponding assumptions should be well documented and justified for the purpose of the data analyses. The main data analysis results should be detailed with appropriate visualization approaches (figures and tables) although some of the results, including figures and tables, can be deferred in the appendix or as online materials if the size of the results is too large. Some conclusions and discussions may be provided, and the limitations of the EHR data and analysis methods may need to be acknowledged and discussed. The references should be included at the end of the report. Notice that the data analysis report is different from a manuscript for publication purposes. The data analysis report should document all the key steps, processes, models, methods and results in detail, but not all these results can be published. The data analysis report may also include the results that are good for multiple manuscripts for publications. Thus, the data analysis report serves as a documentation and/or a communication channel to all the stakeholders of the EHR project.

### 1.2.7 Result Validation

Since the EHR data are observational data that were collected to support clinical practice and for documentation or billing purpose, the results derived from the EHR data are possibly biased or confounded by many factors. It is necessary to validate the results via both internal and external data sources. The internal validation can be done using cross-validations, i.e., divide the data into training and testing data sets, use the training data set to derive the results and use the testing data set to test or validate the results. Because EHR data usually has very large sample sizes, splitting the data often does not have a substantial adverse effect on the power of the statistical tests. Ideally, the external validation can be done using different data sources such as a different EHR database or a randomized clinical trial, although this will need more effort and cost.

### 1.2.8 Result Interpretation

We also need to carefully interpret the results derived from the EHR data since there are some limitations and bias of EHR data as we suggested above. We must admit these limitations and some validations are necessary to confirm the results. Domain clinical and epidemiological experts and data scientists need to work together to interpret the results carefully.

### 1.2.9 Publication and Dissemination

Finally, a manuscript or report must be drafted in order to disseminate the results to the research communities or the general public. The research team needs to work together to decide which parts of the results, if not all, should be included in the manuscript or report for publications. Reliability and reproducibility should be considered when selecting and determining the results for publications. Publication bias should be avoided.

It is important to consider all the above steps in a systematic way. We will present and discuss the detailed methodologies for each of these steps in the subsequent chapters. We believe that systematic thinking is critical to harness and mine EHR data for scientific and knowledge discoveries.

## ![image](images/inline1_1.jpg)  
1.3 Challenges and Opportunities

Although the EHR data are often rich and reflect the real-world practice, there are many challenges and barriers to use the EHR data for research and scientific discoveries from both methodological and practical perspectives. First, it is not easy to acquire or access a complete and general EHR database for research purposes. Although MIMIC ([Johnson et al. 2016](#ch01.xhtml#ref1_14)) is an openly available EMR database, it only contains the EMR data from the ICU at Beth Israel Deaconess Medical Center (BIDMC), which is limited in size and scope. The general commercial EHR and insurance claim databases are usually not freely accessible for researchers, and some of them can be purchased but at a high cost, which is usually beyond the affordability of most individual investigators. The major barriers for sharing the EHR data openly include the difficulties to de-identify the data for privacy protection and data safety issues. Fortunately, our institution was able to acquire the de-identified Cerner EHR database ([Cerner 2020](#ch01.xhtml#ref1_4)) at an affordable cost, although a huge amount of effort is still needed to process and clean the data before it can be analyzed for research and scientific discoveries. A major limitation of the current version of our Cerner EHR database is that it only includes the structured EHR data; the unstructured data such as clinical notes, images from radiology and pathology, and high-frequent data including EEG and ECG data are not available to us. In this book, we are going to share our experience of EHR data processing, cleaning and analysis based on the Cerner structured EHR data.

Since the EHR data were not collected for research or scientific discovery purpose, the data collection may have a bias toward its original purpose of EHR systems, i.e., for patient management, documentation and billing purposes. Some of the data or variables that are important for research questions, but may not be important for patient management, documentation or billing, may not have been collected. Thus, we need to consider the data collection bias in our data analysis and result interpretation.

From a methodological perspective, as we have discussed above, there exist many challenges in each of the research steps from data extraction to data analytics and predictions. We may also need to deal with some new challenges from the EHR data. For example, it is difficult to confirm a patient with a particular disease diagnosis or characteristics, which may be part of the inclusion criteria for analysis due to missing data issues and lack of confirmed diagnosis or test results. In this case, it is likely that some of the patients that are included in the data analysis may not satisfy the inclusion/exclusion criteria due to data errors, which may result in bias in the analysis. The high missing rate of many variables and factors in the EHR database is another issue that is not easy to handle. The missing rate can range from 1% to 99% and missing may not be at random. There are also many factors or variables that are important for clinical outcomes but are not collected. In this case, it may not be easy to do treatment or group comparisons due to confounding factors that are not measured or not collected in the EHR database. Thus, it is generally difficult to justify the comparison results based on the data from a retrospective observational study.

Due to the EHR data complexities, a multidisciplinary team is required to deal with the challenges not only in the data analysis step but also for data extraction, cleaning and processing. A good collaboration team may include database experts, computer scientists or informaticians, statisticians, data scientists, clinicians and epidemiologists. It is also important to recruit experts who are familiar with EHR systems and hospital or clinic data entry procedures. High-performance computing facilities with a high volume of storage are necessary for the large volume of the EHR data. Thus, the cost is high in personnel and computational equipment in order to use the EHR data for research and scientific discoveries.

Although there are many challenges and limitations to use the EHR data for research and scientific discoveries, there are also ample opportunities. Usually, the EHR databases include the data from a huge number of patients with different characteristics and conditions, which can be used to address many clinical and epidemiological questions for different diseases, in particular for rare diseases or rare conditions. Although the gold standard for comparing treatments or intervention strategies is to use randomized clinical trials, the retrospective data analysis based on the EHR database reflects more real-world conditions, which can be used to generate many good hypotheses for future randomized trials. At the same time, the results from the EHR data analysis can serve as important priors in order to better design the randomized trials. There are also many opportunities for statisticians and data scientists to develop new statistical methods and computational or predictive algorithms to address the limitations and challenges of the EHR data.

### References

Anglemyer, Andrew, Horvath Hacsi T., and Bero Lisa. 2014. Healthcare outcomes assessed with observational study designs compared with those assessed in randomized trials. *Cochrane Database of Systematic Reviews* 2014 Apr 29(4):MR000034.

Banda, Juan M., Martin Seneviratne, Tina Hernandez-Boussard, and Nigam H. Shah. 2018. Advances in electronic phenotyping: from rule-based definitions to machine learning models. *Annual Review of Biomedical Data Science* **1**, 53–68.

Brown, Derek W., Stacia M. DeSantis, Thomas J. Greene, Vahed Maroufy, Ashraf Yaseen, Hulin Wu, George Williams, and Michael D. Swartz. 2020. A novel approach for propensity score matching and stratification for multiple treatments: Application to an EHR-derived study. *Statistics in Medicine* 39(17), 2308–2323.

Cerner. 2020. “ *Cerner website.”* [https://www.cerner.com/ap/en/solutions/data-research](https://www.cerner.com).

Fayyad, Usama, Gregory Piatetsky-Shapiro, and Padhraic Smyth. 1996. From data mining to knowledge discovery in databases. *AI Magazine* **17**((3)), 37–54.

 Fernández-Arteaga, Verónica, Carlos Alfonso Tovilla-Zárate, Ana Fresán, Thelma Beatriz González-Castro, Isela E. Juárez-Rojop, Lilia López-Narváez, and Yazmín Hernández-Díaz. 2016. Association between completed suicide and environmental temperature in a Mexican population, using the knowledge discovery in database approach. *Computer Methods and Programs in Biomedicine* **2016 Oct; 135**, 219–224.

Frieden, Thomas R. 2017. Evidence for health decision making—beyond randomized, controlled trials. *New England Journal of Medicine* **377**((5)), 465–475.

Glicksberg, Benjamin S., Riccardo Miotto, Kipp W. Johnson, Khader Shameer, Li Li, Rong Chen, and Joel T. Dudley. 2018. Automated disease cohort selection using word embeddings from electronic health records. *Pacific Symposium on Biocomputing*. 2018; 23, 145–156.

Gronsbell, Jessica, Jessica Minnier, Sheng Yu, Katherine Liao, and Tianxi Cai. 2019. Automated feature selection of predictors in electronic medical records data. *Biometrics* **75**((1)), 268–277.

Holzinger, Andreas, Matthias Dehmer, and Igor Jurisica. 2014. Knowledge discovery and interactive data mining in bioinformatics-state-of-the-art, future challenges and research directions. *BMC Bioinformatics* **15**((6)), I1.

Hubbard, Rebecca A, Jing Huang, Joanna Harton, Arman Oganisian, Grace Choi, Levon Utidjian, Ihuoma Eneli, L. Charles Bailey, and Yong Chen. 2019. A Bayesian latent class approach for EHR-based phenotyping. *Statistics in Medicine* **38**((1)), 74–87.

Ioannidis, John P. A., Anna-Bettina Haidich, Maroudia Pappa, Nikos Pantazis, Styliani I. Kokori, Maria G. Tektonidou, Despina G. Contopoulos-Ioannidis, and Joseph Lau. 2001. Comparison of evidence of treatment effects in randomized and nonrandomized studies. *JAMA* **286**((7)), 821–830.

Johnson, Alistair E. W., Tom J. Pollard, Lu Shen, H. Lehman Li-wei, Mengling Feng, Mohammad Ghassemi, Benjamin Moody, Peter Szolovits, Leo Anthony Celi, and Roger G. Mark. 2016. MIMIC-III, a freely accessible critical care database. *Scientific Data* **3**, 160035.

Laney, Doug. 2001. 3D data management: Controlling data volume, velocity and variety. *META Group Research Note* **6**((70)), 1.

Mark,  Smith, Leigh,  Stuckhardt Robert,  Stuckhardt McGinnis,  J. Michael (editors). (2013). *Best Care at Lower Cost: The Path to Continuously Learning Health Care in America,* Washington DC: National Academies Press.

McLachlan, Scott. 2017. “ *Realism in synthetic data generation: a thesis presented in fulfilment of the requirements for the degree of Master of Philosophy in Science, School of Engineering and Advanced Technology, Massey University*, Palmerston North, New Zealand.” Massey University.

Mills, Edward J., Kristian Thorlund, and John P. A. Ioannidis. 2013. Demystifying trial networks and network meta-analysis. *BMJ* **346**, f2914.

MIT Critical Data, 2016. *Secondary Analysis of Electronic Health Records*, Springer Open.

Mitra, Sushmita, Sankar K. Pal, and Pabitra Mitra. 2002. Data mining in soft computing framework: a survey. *IEEE Transactions on Neural Networks* **13**((1)), 3–14.

OHDSI. 2020. “ *Observational Health Data Sciences and Informatics (OHDSI): OMOP Common Data Model*.” [https://www.ohdsi.org/data-standardization/the-common-data-model/](https://www.ohdsi.org).

Rasmy, Laila, Yonghui Wu, Ningtao Wang, Xin Geng, W. Jim Zheng, Fei Wang, Hulin Wu, Hua Xu, and Degui Zhi. 2018. A study of generalizability of recurrent neural network-based predictive models for heart failure onset risk using a large and heterogeneous EHR data set. *Journal of Biomedical Informatics* **84**, 11–16.

Tricoci, Pierluigi, Joseph M. Allen, Judith M. Kramer, Robert M. Califf, and Sidney C. Smith. 2009. Scientific evidence underlying the ACC/AHA clinical practice guidelines. *JAMA* **301**((8)), 831–841.

Van, Poucke, Sven, Michiel Thomeer, John Heath, and Milan Vukicevic. 2016. Are randomized controlled trials the (g)old standard? From clinical intelligence to prescriptive analytics. *Journal of Medical Internet Research* **18**((7)), e185.

Williams, George, Vahed Maroufy, Laila Rasmy, Derek Brown, Duo Yu, Hai Zhu, Yashar Talebi, Xueying Wang, Emy Thomas, Gen Zhu, Ashraf Yaseen, Hongyu Miao, Luis Leon Novelo, Degui Zhi, Stacia DeSantis, Hongjian Zhu, Jose-Miguel Yamal, David Aguilar, and Hulin Wu. 2020. Vasopressor treatment and mortality following non-traumatic subarachnoid hemorrhage: A nationwide EHR analysis. *Neurosurgical Focus*. 48(5), E4, May 2020.

Yu, Duo, George W. Williams, David Aguilar, Jose-Miguel Yamal, Vahed Maroufy, Xueying Wang, Chenguang Zhang, Yuefan Huang, Yuxuan Gu, Yashar Talebi, and Hulin Wu. 2020. Machine learning prediction of the adverse outcome for nontraumatic subarachnoid hemorrhage patients. Annals of Clinical and Translational Neurology, *in press*.

# [2 ](#contents.xhtml#toc1_18)  
![image](images/inline1_1.jpg)

# [EHR Project Management](#contents.xhtml)  
               

Yashar Ashraf TalebiYaseen

## ![image](images/inline1_1.jpg)  
2.1 Introduction

Statista, a German online portal for statistics, valued the global Big Data and business analytics at $168.8 billion in 2018. According to their forecast, this value will grow to $274.3 billion by 2022 ([Statista 2019](#ch02.xhtml#ref2_1), Global big data and business analytics revenue 2019). In an article by TechRepublic, it was pointed out that the healthcare industry could save as much as 300 billion dollars if it could only integrate its Big Data with other systems and business processes (TechRepublic 2019).

Big Data, by nature, is an iterative and continuously updating resource for analytic researchers. This means that as the data grows or its structure changes, the codes or algorithms prepared by research teams need to be re-run or updated repetitively. This issue becomes more important when we deal with the Electronic Health Record (EHR) data. Any research in the field of health sciences may have high impact on the general population; and if the research generates false reports, it has the potential to be disastrous. Some of the most famous misleading findings are the association between measles, mumps and rubella (MMR) vaccine and autism, and the lobotomy procedure for the treatment of schizophrenia ([Soares et al. 2013](#ch02.xhtml#ref2_4), [Hviid et al. 2019](#ch02.xhtml#ref2_5)).

Because of the sensitivity of EHR research, the researchers in this field must ensure that the following conditions are met:

1.  The data come from a reliable source with good quality.
    
2.  The data cleaning procedure is reliable, unbiased and the rate of error is at a minimum.
    
3.  The analytical methods to be used are sound and acceptable to the scientific community.
    
4.  The report represents the findings appropriately.
    
5.  The research results are reproducible.
    

The first four of the above-mentioned items will be covered in the upcoming chapters. In this chapter, we will cover the research reproducibility through proper project management.

Research on Big Data usually demands multiple individuals or a team of multidisciplinary members to work collaboratively where some tasks can be done in parallel while others in sequence. In these situations, the work of one team member can affect another team member or a team member cannot begin to perform a task unless the results from another team member become available. Furthermore, there is usually a back and forth relationship between team members. For example, a team member who conducts the data analysis usually needs to wait for the data cleaning team member to finish the data cleaning procedure. At the next step, the analysts may feel that the data cleaning procedure needs to be adjusted and ask the data cleaning team member to redo the data cleaning with new adjustments. All of this can get complicated rapidly for a large EHR research team and a good framework for project management is usually necessary.

### 2.1.1 What is Project Management?

To answer this question, we first need to define a project. A project is a task (or a collection of related tasks) that needs to be done in a finite time frame with finite resources and should result in a predefined objective with an acceptable quality (APM 2020). The limitation of time and resources is the key point to distinguish project management from management as a general term. The formal definition of project management in Wikipedia is&#160;: “Project management is the practice of initiating, planning, executing, controlling, and closing the work of a team to achieve specific goals and meet specific success criteria at the specified time. The primary challenge of project management is to achieve all of the project goals within the given constraints” ([Project management - Wikipedia, 2020](#ch02.xhtml#ref2_7)).

As a result, for any project, the following questions should be considered:

*   Why the project is necessary?
    
*   What type of resources are needed?  
    For example, an EHR research project requires some of these resources:
    
    *   Members with enough expertise and skills to form a project team.
        
    *   Data with acceptable quality and size to conduct the project.
        
    *   Computing infrastructure hardware (PCs, servers, clusters, etc.) and software.
        
    *   Funding to support all of the above resources.
        

*   Is the result of the project financially (or sometimes ethically) justifiable?
    
*   Can the organization secure the resources needed for the accomplishment of the project?
    
*   What is the management plan for this specific project?
    
*   What are the deliverables and what is the expected quality of each deliverable?
    
*   What are the possible risks and issues?
    
*   How much change is acceptable to continue the project?
    
*   How should the progress of the project be monitored?
    
*   How will the project be completed?
    

The means and methods to address these questions are called project management [(Munns et al. 1996)](#ch02.xhtml#ref2_8).

### 2.1.2 Why We Need Project Management?

Project management, in contrast with general management, focuses on smaller goals with constraints on resources and time. Considering these limitations and defining an achievable goal is the backbone of project management. Over the past decades, it has been noted that project management is an efficient and critical part of the management of any organization. Since the project manager will focus on smaller goals, he/she is a faster and better decision-maker for an individual project and can supervise team members more efficiently. The increased interaction between the project manager and team members increases the former's ability to recognize each team member’s strengths and weaknesses. All of these benefits the progress of the project and increases the rate of success. Also, project management will focus on accomplishing a single or a limited number of tasks, but if it is done properly, the tools and methods developed during these projects can be used at a higher scale (i.e., at organizational management level) for future projects. The project manager should have effective communication and collaboration with organizational managers to decide what parts of the project have the potential to become a part of the other projects of the corresponding organization. This means that project managers should have a bigger picture in mind to make the developed methods flexible and generalizable, otherwise, the side products of his/her project will be wasted and it will not be cost-effective for the organization.

### 2.1.3 Project Management Goals and Principles

Each of the steps for an EHR research project is time-consuming. In addition, tracking changes in project resources, such as files, and managing multiple teams can be challenging in a multiple research group setting. The goal of EHR project management is to make the whole procedure more efficient and resources reusable so that we can reduce mistakes and errors while developing some sort of semiautomatic pipelines to process the initial steps of each project. In this chapter we describe current methods for project and file management based on our experience, and we also discuss customized methods to manage multiple EHR research projects. The main focus of this chapter is to describe how to manage EHR projects to make resources reusable, reproducible, scalable and generalizable.

## ![image](images/inline1_1.jpg)  
2.2 Project and Sub-Project in EHR Research

Typically, multiple EHR research teams work on different parts of the same EHR database. Each of these research teams usually focuses on a single or group of closely related diseases. In this setting, the main project will be the cohort of the patients that have been selected by the research team (e.g., a project for all HIV positive patients) and subprojects are different goals based on the same cohort of patients (e.g., subproject-1: Effect of HIV on cancer; subproject-2: association of HIV with psychologic disorders, etc.).

Since the data usually comes from a single EHR database or data warehouse, the structure of the data (tables and formatting of the data) stays the same in most cases. This means, if the algorithms for data extraction, data quality assessments, data cleaning, and even data preparation have been developed carefully following generalizability guidelines, the same algorithms (with minor changes in settings) can be reused to fulfill the needs of the majority of the research teams ([Oussous et al. 2018](#ch02.xhtml#ref2_9)).

On the other hand, it is not uncommon that, even during the report writing (which is considered as one of the later stages of the research), the research team notices that there was an error during data extraction or they want to modify their data pool. This means that the extracted data needs to be changed and all of the steps need to be re-done again. This issue is especially troublesome when there is more than one research team with multiple team members using the same extracted data, so if they need to use the previous version of the extracted data, they should be able to do so. These issues can be grouped as a folder, file, code, and product management.

## ![image](images/inline1_1.jpg)  
2.3 Data, Code and Product Management

### 2.3.1 Data Loss Prevention

One of the first challenges that a research team should address is how to prevent data loss. Data loss can usually happen in one of the following three scenarios:

*   **Hardware failure:** Although there is a major development in producing more reliable and longer-lasting data storage hardware, all of this hardware will fail at some time point. To prevent this type of data loss, the data managers may use a combination of RAID^([1](#ch02.xhtml#en2_1)) (namely RAID 1,5,6,10) and backup storage servers.
    
*   **Virus/malware/ransomware attack:** This is one of the most troubling data loss scenarios. You may not only lose your data but your data may also become available to unauthorized users or entities. This is especially important for EHR data because it usually contains sensitive information for a big population. The use of firewalls and security software and hardware is recommended to protect your data.
    
*   **Intentional or unintentional data manipulation by users:** EHR data research teams usually involve a large number of users or team members working on the same set of data files. These users may move the files to different locations on server storage or may delete them. The problem arises when another user wants to run a code and notices that he/she cannot find the data files needed to run the code. In this situation, Version Control Systems (VCS) are the best tool to prevent this type of data loss.
    

### 2.3.2 Naming Conventions

Creating a file and folder naming convention at the beginning of an EHR project is important for three reasons:

1.  The number of files can rapdily increase. Having a mutually agreed convention for folder structure and following these rules helps all of the team members find the needed files faster.
    
2.  It is easier to develop a convention and follow this convention during the first steps of EHR data team creation. Trying to reorganize the files and folders that are already created and named can be time-consuming and challenging.
    
3.  A file, folder, and even data field naming convention increase the performance of code developers. The developers can just follow the same convention in writing their code and even if the team updates their files, this code is not prone to raising errors. Furthermore, the developers just need to memorize the names of the files or data fields and they can follow the convention for the path to these files and format of the file name or data fields.
    

Some may think that the convention proposed as an example in [Section 2.7](#ch02.xhtml#sec2_7) is somewhat extreme but keep in mind that organizational needs may grow over time and it is better to overestimate the future needs than underestimating it. In the next steps, first, we briefly review the major types of version control systems, and then we will describe why it is important for the whole group to follow a standard coding scheme.

### 2.3.3 Version Control

Version Control is a system that is used to track and record the changes to a file or a set of files. It allows the user to revert a file or a set of selected files to its previous version, revert the whole project to its previous stage, compare the changes that have been made to project or files, see who last modified the file, and so on. Generally, a Version Control system (VCS) records all of the changes to a file and stores it with a timestamp. There are three major types of version control systems:

1.  **Local VCS:** Revision Control System (RCS) is the most prominent in this category. This is an early generation VCS and its usage is limited. It is simple to use but lacks security features. All of the changes will be stored on the user’s local computer and it is not recommended for big projects with multiple users (Chacon et al. 2014).
    
2.  **Centralized VCS:** These systems were developed for groups of developers who are using different systems. CVS, Subversion, and Perforce are some of the well-known Centralized VCS. This system has a single server that contains all the versioned files and each client accesses the main server to check the version and revert the changes. It is a major improvement compared to the previous generation. The main drawback is its dependence on a single server (Chacon et al. 2014).
    
3.  **Distributed VCS:** In this type of VCS, each client has a full copy of the file’s history. Git is one of the most well-known VCS in this category. Since each client has a copy of the repository, this system is not sensitive to the failure of the server and in fact, rebuilding the server repository by the use of copies on the client’s computers is easily doable (Chacon et al. 2014).
    

Git is the most widely used version control system in the world. Git is an open-source and actively maintained project which was originally developed by Linus Torvalds (the creator of Linux operating system kernel). Git has a distributed architecture and is considered as a Distributed Version Control System (DVCS). Git is developed with performance, security, and flexibility in mind (Atlassian Git Tutorial 2019).

Nowadays, almost all servers have some kind of VCS installed (it is unwise not to do so), but there is a caveat in using VCS with EHR databases. Because of the sensitivity of the EHR data in nature and the Health Insurance Portability and Accountability Act of 1996 (HIPAA law), the owner of the original EHR data may prohibit your organization from creating copies of whole or even parts of the data on client computers or uploading them into cloud-based storage servers. Such limitations reduce the pool of suitable software or applications. As a result, distributed VCS such as Git and cloud-based platforms such as Google Cloud or Amazon Web Services (AWS) may not be an option for version control of the files extracted from the EHR database. In this case, centralized VCS may be a better option.

### 2.3.4 Coding Convention

Since team members in the EHR research group should rely on other members’ code and output, it is strongly recommended for all team members to follow a standard coding schema. There are good resources online for how to adhere to a standard format in coding. Here we list some of the important ones:

*   Prologue comments: Programmer name, program description, date, etc.
    
*   Document each variable and constant. Use meaningful variables (do not use single letter variables).
    
*   Use standard Indentation and spacing.
    
*   Use comments to describe your code.
    

#### Object-Oriented or Non-Object-Oriented Programming

In Object-Oriented Programming (OOP), computer programs create objects from classes and this paradigm facilitates the interaction with other OOP codes ([Potok et al. 1999](#ch02.xhtml#ref2_12)). Many developers recommend using Object-Oriented Programming. Since the EHR data is typically used by multiple developers or team members and it is a multi-step procedure, object-oriented coding can be a better choice in this setting. Object-oriented codes can be called from inside of other codes and it is easier to make a pipeline using this schema. Hence, it is recommended to pick a middle ground for doing your code as object-oriented. Writing the code in an excessively object-oriented manner can make your code difficult to understand.

### 2.3.5 Document Management: Data Analysis Report, Papers and Read-Me Documents

After creating a new file (report, paper, data) the team member should inform the corresponding project manager so he/she can track and record the advancement of the project. Then the project manager can give the green light to other team members affected by the new product to continue with their duties as necessary. Each file should be accompanied by a readme file. If applicable, the user should also include the code that has been used to generate the main file.

It is recommended that the user uses a standard file submission form for the readme file (an example is provided in the appendix as a template). The readme file should not be very complex and it is better to keep it short. In the template provided in the appendix, the readme file is two pages long. The first page is for file information and the second page is for a brief description of the file. If the procedure is too complex, it is recommended to generate a report and place it in a separate report folder.

## ![image](images/inline1_1.jpg)  
2.4 Team/People Management

Team/people management is one of the essential roles of team leaders and the need for a suitable project management tool will become more paramount as the numbers and size of each team increase overtime. Staff turnover is another issue that should be considered at the time of designing the organizational chart and project management framework.

The sensitivity of EHR data necessitates a well-designed organizational chart. Access level and user privileges should be clearly defined in the organizational chart. The assignment of tasks to each team and each member of that team should be tracked and its progress should be regularly monitored. Such steps are needed so team leaders can decide if a team needs more staff or help, and discover the bottlenecks in conducting research. Maintaining a good project management framework is hard without the use of tools that are already available.

### 2.4.1 How to Form a Team: What Expertise is Needed for EHR Projects?

The research on EHR Big Data is somewhat different from research on other types of Big Data. The range of skills needed for conducting an EHR data research is usually more diverse than other Big Data research topics. Here we list some of the skills and expertise that are needed for conducting such kind of research. Each specific research has different needs and this list should be adjusted accordingly.

1.  Project Manager/Team Leader. The project manager is the most critical member of the team. We describe some of the responsibilities of project managers throughout this chapter. The project manager should be familiar with all aspects of the research (but not necessarily experts in all fields) to be able to bridge between different members of the project. For example, computer scientists may not be able to communicate with clinicians efficiently. The project manager/team leader can perform as a translator to simplify or describe the technical terms to team members so everybody in the team can be on the same page. As a result, project managers should have excellent communication and organizational skills. The success of the project mainly depends on the efficiency of the project manager.
    
2.  Information Technology (IT) Support. Each Big Data research needs the involvement of team members with IT skills. If the research project is big enough, it may be financially justifiable to hire dedicated IT support personnel, otherwise, the IT support is usually provided by the organization’s IT department.
    
3.  Data Managers. Data managers are responsible for the maintenance of the data server or servers to secure the database’s functionality, quality, integrity, and stability. Sometimes the data manager can function as IT support too. For EHR data research, it is recommended that the data manager be familiar with the common structure of the EHR database and relations of the data fields to each other from the medical or clinical perspective.
    
4.  Data Scientists and Statisticians. These team members have the required expertise on how to extract insights from data using advanced analytic approaches. They usually have strong programming skills and a solid understanding of statistics. As a result, a data scientist should have a sound background in computer sciences and statistics. For EHR Big Data research, it is recommended that the data scientists are familiar with both biostatistics methods and have a background in medical terminology.
    
5.  Medical and Clinical Professionals. Any EHR research project needs at least one team member with clinical knowledge and expertise about the current project-specific subject. The clinician should be involved from the beginning of the study so they can guide the team through different aspects of EHR data research (from data extraction to analysis and generating deliverables, see [Figure 2.1](#ch02.xhtml#fig2_1) above).
    
6.  Health Administrator. For some specific topics in EHR research, it can be extremely valuable to involve a team member with knowledge of health administrative systems. Such a team member can clarify the process that data has been generated, define the data sources, identify which data source is more reliable, describe what data fields are related to each other, and so on. For example, there are different types of coding systems (such as ICD-9, ICD-10, CPT, HCPCS, etc.) and team members with health administration experience/knowledge can tell which coding system is more valuable for getting the needed information.
    
7.  Other Team Members. Each aspect of the EHR data research usually needs more than one team member. Depending on the complexity of the project, multiple team members can work as data managers, data scientists, etc. In this situation, it is recommended that one senior member from each of the above-mentioned categories act as a leader of the group.
    

![Figure 2.1 Steps of data handling and preparation for final data analysis.](images/fig2_1.jpg)

**Figure 2.1**  
Steps of data handling and preparation for final data analysis.

Having a smaller team with experienced team members is generally more efficient than having a large team consisting of inexperienced team members. But, if the project manager hesitates to include new team members, he/she will restrict the probability of finding innovative ideas. The best approach could be a well-balanced team of experienced and new team members to get the benefit of both.

### 2.4.2 How to Efficiently Manage a Multidisciplinary Team?

As previously mentioned, any EHR research project needs a multidisciplinary team. Managing a multidisciplinary team can be a challenging task for project managers. The following issues should be noted by the project manager so he/she can manage his/her team efficiently.

*   **Do not assume all team members have the same goals.** In a multidisciplinary team, each team member has a different set of skills and capabilities, and they may have a diverse background. As a result, they may have a different understanding of the goal of the project. For example, a clinician may focus more on the clinical application of the project whereas the statistician may be interested in the methodology (even if it may not have an application yet). The project manager should ensure that all team members understand the nature of the deliverables and adjust their role in the team accordingly.
    
*   **Understand the capabilities of team members.** The project manager should know and understand the capabilities of each team member. Assigning a task to a team member that is beyond his/her capabilities can reduce the quality of the deliverables or delay the project.
    
*   **Use the right resources and tools.** The project manager should decide what kind of resources are best fitted for the current project and do his/her best to acquire them. Failing to provide the necessary tools or selecting the wrong tools for the project, at best, can delay the project and increase the overall cost or, at worse, can result in the failure of the project.
    
*   **Create a community for the team.** Sometimes, humankind is called the social animal. Social interaction and the need to belong are of utmost importance for any person ([Tomasello 2014](#ch02.xhtml#ref2_13)). It is important that team members know each other and feel they belong to a team. The project manager should facilitate social interactions among team members. Such policies increase team performance toward a mutual objective. This goal can be achieved by regular formal meetings and occasional informal social events. The project manager should be available to team members so they can discuss their issues with him/her.
    

### 2.4.3 Task Management

Task management is one of the essential roles of the project manager. Good task management will increase the productivity of the team. The project manager should:

1.  Define the tasks and their requirements.
    
2.  Set priorities for each task.
    
3.  Set a realistic time-to-finish for each task according to the available resources.
    
4.  Add some buffer for the unforeseen circumstances that may delay or alter a task.
    
5.  Assign the task to team members according to their capabilities.
    
6.  Track the progress of each task and the whole project.
    
7.  Update the task and their priorities if necessary.
    
8.  Create reports for the project progress and discuss it with team members to find the bottlenecks or issues and fix them if needed.
    

With complex projects like EHR Big Data research, it is recommended that the team uses some task management tools to better monitor the progress of the project. Gantt charts have become a standard method to visualize the task management ([Figure 2.2](#ch02.xhtml#fig2_2)). In the next section ([Section 2.5](#ch02.xhtml#sec2_5)), we will review some of the well-known tools for this purpose.

![Figure 2.2 An example of a Gantt chart for task management.](images/fig2_2.jpg)

**Figure 2.2**  
An example of a Gantt chart for task management.

## ![image](images/inline1_1.jpg)  
2.5 Management Methods and Software Tools

In this section, we give a brief description of some of the well-known methods/tools that are currently being used for our project and file management. We will describe how we utilize these tools to develop a sample data/project management framework. Please keep in mind that the framework we will describe in the upcoming section ([Section 2.6](#ch02.xhtml#sec2_6)) of this chapter can (and should) be modified to meet the specific needs of each research team for different projects.

There are multiple project management tools but, in this section, brief descriptions of the three most popular ones are presented. We should emphasize that although the latter two software tools are mainly used for creating a platform to enhance collaboration work and sharing files and content between teams and among team members (and hence not considered pure project management software), they have enough capability to be used as a project management framework.

*   **Microsoft Project:** This tool is a project management software designed to run on local computers. Microsoft Project is a well-known project management software and has some advanced features. However, it is designed to work on local computers, it is not recommended for EHR project management. EHR data research teams are usually big and some team members need to be able to work remotely.
    
*   **Slack for Project Management:** Slack is a cloud-based project management/collaboration software. Currently, it is the second most common project management/collaboration software available. The ability to share and work on files by the team members, messaging, group chat, and video conferencing are the major selling point of this software. Setting up Slack is easier in comparison with our next project management software.
    
*   **Microsoft Teams:** This cloud-based project management/collaboration tool is the most common one. The features of Microsoft Teams are similar to Slack, but it has fewer limitations. For example, the number of users who can participate in a video conference is higher in Microsoft Teams in comparison with Slack. Furthermore, it is compatible with other Microsoft products such as Microsoft Office package and a growing number of add-ons can be utilized within Microsoft Teams. As a result, Microsoft Teams is a more favorable project management/collaboration tool for larger organizations.
    

Similar to the argument discussed in the last section, if it is mandated by the EHR data owner, team members should refrain from sharing patient data files on any cloud-based storage server (such as Slack or Microsoft Teams). Sharing the reports of a group of patients or papers is usually acceptable, but team leaders should be familiar with the detail of the contract with the EHR Data owner to prevent legal and ethical issues.

For a single project, the selection of project management software is usually mandated by the organization. Most of the time, purchasing a new project management software or tool for one or a small number of projects is not time and cost-efficient (keep in mind that with new software comes the training of the team members). As a result, the choice of project management software is very limited. If the project manager has the freedom of choosing the project management software/tool, Microsoft Teams can be a good choice because of the above-mentioned reasons.

## ![image](images/inline1_1.jpg)  
2.6 An Example of a Data Management Framework

In the remainder of this chapter, we describe a data management framework that is being used by our team at the School of Public Health, University of Texas Health Science Center at Houston. We have multiple teams working on different EHR research projects and other Big Data projects (e.g., Cerner, UK Biobank, GEO, etc.). Each team has focused on one or more cohorts of patients with particular diseases (e.g., Subarachnoid hemorrhage (SAH) project or HIV/AIDS project based on the Cerner EHR database) and each project has one or more sub-projects (e.g., vasopressor comparison and mortality prediction subprojects within the SAH project). The SAH cohort consists of all patients in the EHR database who had a history of Subarachnoid Hemorrhage (SAH) diagnosis between 2000 and 2018 and includes around 50,000 patients. The AIDS cohort consists of all patients in the EHR database who had a history HIV positive test for the same period and includes around 100,000 patients.

In this section, we will describe a data management framework based on our experience on these ongoing EHR research projects. We assume that your data management team already set up a reliable data loss prevention structure and your organization has a collaboration/project management tool ready. We begin with a proposed folder (directory in non-windows operating systems) structure and we will set a convention on how to name the folders and files.

### 2.6.1 Folder Management

The following naming and folder structure convention should be considered as an example. Each organization, depending on their needs, should create its file and folder structure and naming convention. The following rules can be a good starting point.

#### Naming

There are two main methods for the general format of your files and folder names. The first method is to separate\_each\_word\_with\_underscore, the second method is to use CamelCaseTheFirstLetter. The first method is usually recommended because it makes the name more readable. In this framework, we will use the first method. In the proposed method, each word in the folder name should begin with a capital letter followed by lower case letters (except for “and”, “of”, etc.). The acceptable characters are case sensitive alphanumeric (A-Z, a-z, 0–9) and “\_” (underscore).

Avoid using “” (space) in the name since it may lead to errors in some codes or software. The use of abbreviated words will reduce the length of the names and is highly recommended. Do not use the date as part of the folder name, because it is usually not meaningful and if it is necessary, it can be added separately in the data management framework that we will describe later. The following examples show some of the acceptable and unacceptable names for folders:

*   SAH, Cerner, UK\_Biobank, HT\_and\_HF: **Acceptable and recomm-ended.**
    
*   Hypertension\_and\_Heart\_Failure, SubarachnoidHemorrhage: **Acc-eptable but not recommended.**
    
*   UK Biobank, SAH\_20190128, Cerner$: **Unacceptable.**
    

#### Structure

You should create a folder to include all of the files for your unit or research center. For security and maintenance reasons, it is better not to include the actual database names in these folders. In this example, the main folder that contains all the data is named CBD\_HS, which indicates our Center for Big Data in Health Sciences (CBD-HS). The general structure of the sub-folders is presented in [Figure 2.3](#ch02.xhtml#fig2_3). Except for the end folders, other folders should not contain files.

![Figure 2.3 The general structure of the folders.](images/fig2_3.jpg)

**Figure 2.3**  
The general structure of the folders.

An example of the folder structure for the SAH project is presented in [Figure 2.4](#ch02.xhtml#fig2_4).

![Figure 2.4 Part of the SAH project and its main up and down sub-folders.](images/fig2_4.jpg)

**Figure 2.4**  
Part of the SAH project and its main up and down sub-folders.

[Figure 2.4](#ch02.xhtml#fig2_4) shows part of the mortality prediction sub-project from the SAH project and its main up and down sub-folders. In the following part, the details of each type of sub-folders are presented.

In this framework, we define four user groups. The details of each user group described in later sections but the access level is described alongside each folder description. These user groups are:

*   Super\_admin.
    
*   Admin.
    
*   Project\_manager.
    
*   Regular\_user.
    

##### *Main Folders*

###### CBD\_HS

This is the main folder that contains all project data.

*   User groups with read/execute access: Super\_admin, Admin, Project\_manager, Regular\_user.
    
*   User groups with write access: Super\_admin, Admin.
    

Each working group or team has its folder in the CBD\_HS. Only admins can create a new working group (by creating a new folder). Project managers have to write permission for the contents of their corresponding working group, but they cannot create a new working group.

Each working group or team should have at least one main project and each main project should have at least one sub-project. For instance, in [Figure 2.5](#ch02.xhtml#fig2_5), we created a new research working group called “Brownsville”. We are in the exploratory phase of this study. To keep the correct structure for our CBD\_HS folder, we create a folder named “Exploration” as the main project and create another folder named “Explore\_1” inside of it. It is crucial to keep this convention in creating the tree of folders, otherwise, our data management framework may miscategorize them.

![Figure 2.5 Adding a new workgroup or team to the folder structure.](images/fig2_5.jpg)

**Figure 2.5**  
Adding a new workgroup or team to the folder structure.

###### Public\_Folder

Project managers do not have access to the individual user folder, so the public\_folder acts as a shared media for all working groups or research teams. The users can store the files they want to place in the CBD\_HS folder and inform their corresponding project manager, then the project manager can move these files to their appropriate location. It is recommended to perform these procedures as soon as possible so the public\_folder does not get crowded by files. Alternatively, you may want to use your server’s shared folder for this purpose.

*   User groups with read/execute access: Super\_admin, Admin, Project\_manager, Regular\_user.
    
*   User groups with write access: Super\_admin, Admin, Project\_manager, Regular\_user.
    

###### Admin

This folder is for administrator:

*   User groups with read access: Super\_admin, Admin.
    
*   User groups with write access: Super\_admin, Admin.
    

Admin folder contains three sub-folders ([Figure 2.6](#ch02.xhtml#fig2_6)):

1.  The data management framework (DMF). This folder contains:
    
    *   The DMF core.
        
    *   Archived sub-folder to store previous versions of DMF core.
        
2.  Network. This folder contains:
    
    *   Current network status.
        
    *   Current network status graph object.
        
    *   Archived sub-folder to store previous versions of network structure and status.
        
3.  Manual. This folder contains:
    
    *   The manual for data management framework set up and use for admins.
        
    *   Extras sub-folder for the images and extra files used in the manual.
        
    *   Archived sub-folder to store previous versions of manuals.
        

![Figure 2.6 Admin folder structure.](images/fig2_6.jpg)

**Figure 2.6**  
Admin folder structure.

###### Useful\_Info

This folder is created to share the educational and other materials such as ICD-9 or ICD-10 dictionaries that are useful for all of the working groups or teams.

*   User groups with read/execute access: Super\_admin, Admin, Project\_manager, Regular\_user.
    
*   User groups with write access: Super\_admin, Admin.
    

DMF will not map the contents of this folder. If any of the files in this folder is used for any of the projects, a copy of the file should be placed in the “CBD\_HS/Working\_Group/Project/Sub\_Project/Raw\_Data/Extras/” folder and use this path to address the dependencies. The concept of dependencies and DMF will be discussed later.

##### Group Folders

One folder should be created for each research group or team (e.g., Cerner, UK\_Biobank). These folders contain all of the individual projects and data.

*   User groups with read/execute access: Super\_admin, Admin, corresponding Project\_manager.
    
*   User groups with write access: Super\_admin, Admin.
    

##### Project Folders

This folder is for each project in the working group. It contains at least one sub-project and the Main\_Raw\_File folder to store the data extracted from the database. This main raw file is shared between all sub-projects.

*   User groups with read access: Super\_admin, Admin, corresponding Project\_manager, users of the same project.
    
*   User groups with write access: Super\_admin, Admin, corresponding Project\_manager.
    

##### Sub\_Project Folders

*   User groups with read access: Super\_admin, Admin, corresponding Project\_manager, users of the same project.
    
*   User groups with write access: Super\_admin, Admin, corresponding Project\_manager.
    

The following sub-folders should be created for each sub-project (the numbers at the beginning of folders are added to show the stepwise process of the data):

1.  01\_Raw\_Data:
    
    *   It contains multiple folders for each category of the extracted raw data. It is recommended to create separate folders for different categories of the raw data (they can be empty) as a reminder of the tables that may need to get extracted data from the database and also to make it suitable for future expansions. If the sub-project is using the Main\_Raw\_Data, these folders will be empty. But if the sub-project needs its specific data, then it should be placed in these folders to prevent confusion between multiple sub-projects. Even if there is only one sub-project within the main project, the same rule should be applied because of the possibility of adding other sub-projects in the future. Each of these categories should have an Archived sub-folder to store the previous versions ([Figure 2.6](#ch02.xhtml#fig2_6)).
        
    *   Extras sub-folder to store miscellaneous files or files copied from Useful\_Info main folder.
        
2.  02\_Cleaned\_Data:
    
    *   Same as Raw\_Data contains multiple folders for each category of the cleaned data.
        
    *   Extras sub-folder to store miscellaneous files.
        
3.  03\_Prepared\_Data:
    
    *   Same as Raw\_Data, Contains multiple folders for each category of the prepared data. If the file is prepared by using multiple cleaned or raw files and contains information about multiple categories of data, the corresponding project manager should judge what is the category of the majority of the fields and place it in the appropriate folder. It is better to avoid creating new folders or placing them in the “Extras” folder.
        
    *   Extras sub-folder to store miscellaneous files.
        
4.  Reports:
    
    *   It contains multiple sub-folders for each report. Each of these folders should have an Archived sub-folder to store the previous versions.
        
    *   Extras sub-folder to store miscellaneous files.
        
5.  Papers:
    
    *   It contains multiple sub-folders for each paper. Each of these folders should have an Archived sub-folder to store the previous versions.
        
    *   Extras sub-folder to store miscellaneous files ([Figure 2.7](#ch02.xhtml#fig2_7)).
        

![Figure 2.7 Raw\_Data folder structure inside the SAH project, Mortality\_Prediction sub-project.](images/fig2_7.jpg)

**Figure 2.7**  
Raw\_Data folder structure inside the SAH project, Mortality\_Prediction sub-project.

### 2.6.2 File Management

#### Naming

Same as folder naming, each word in the file name should begin with a capital letter followed by lower case letters (except for “and”, “of”, etc.). The acceptable characters are case sensitive alphanumeric (A-Z, a-z, 0–9) and “\_” (underscore). The filename has four essential parts. Each part separated from the next with “\_”: **Project\_Category\_Extra\_YYYYMMDD.ext**

1.  Project/Sub-project name: The name of the project (e.g., SAH, HT, etc.). Keep it as short as possible. This part should be repeated for all of the files in a Sub-project. For example, if the project manager of the Mortality\_Prdiction sub-project decides to begin the name of the files with SAH\_Mortality, every file in this folder should begin with SAH\_Mortality.
    
2.  Category: The category that the file belongs to (e.g., Demographic, Labs, etc.)
    
3.  Extra: The use of it should be minimized. Long file names will not look good on visualization and add more lines to the codes.
    
4.  Date (also called version) of the file in the YYYYMMDD format. This format helps to sort the files by date easily. You can use version instead of the date but a date will carry more information and it is less ambiguous.
    

Adding the type of the file (raw\_data, cleaned\_data, …) is not necessary and not recommended. For example:

*   SAH\_Mortality\_Demographic\_20190110.csv: **Acceptable and recomm-ended.**
    
*   SAH\_Demographic\_version\_1\_reduced\_20190110.csv**: Acceptable but not recommended.**
    
*   SAH\_Demographic.csv: **Unacceptable** (no date).
    
*   SAH\_Demographic\_2019\_01\_10.csv:?**Unacceptable**?(invalid?date format).
    
*   SAH\_Demographic\_20193005.csv: **Unacceptable** (invalid date format, day before month).
    

If a file gets updated but the data structure stays the same (same field names and formats), the project manager should **change the date part of the file name only and keep the other parts the same**. Changing other parts of the file will be detected as data with a different format by DMF.

#### Structure

The file data structure should be kept fixed as much as possible. For instance, if one column is formatted as integers, it is better to keep it as an integer. Changing the format of the column may raise errors in other codes. If the column format needs changes and it is unavoidable, the project manager should change the name of the file (e.g., adding a version to the file name) or inform the admin to set the status of the file as Updated (New structure) in DMF, so affected users can update their codes and apply changes accordingly.

Each word in the column name should all be lower case letters unless it is an abbreviation. The acceptable characters are case sensitive alphanumeric (A–Z, a-z, 0–9) and “\_” (underscore). There should not be any duplicates in column names.

For the date\_time field, the “YYYY-MM-DD HH:MM:SS” format should be used. If the date\_time field has information about the date only, the HH:MM:SS part should be 00:00:00. This approach reduces the complexity and errors of the codes. Project\_managers should double-check the files’ data structure and make sure there is no structural change in data.

##### File Submission

As mentioned earlier, after creating a new file (report, paper, data), the user should inform the appropriate project manager and then copy the file into Public\_Folder. The project manager will move the file to its appropriate folder. Each file should be accompanied by a readme file and a code (if applicable). The readme/code file name should be the same as the main file with the Readme/Code added before the date. Example:

*   Main file: SAH\_Mortality\_Demographic\_20190110.csv
    
*   Readme file: SAH\_Mortality\_Demographic\_Readme\_20190110.docx
    
*   Code for the file: SAH\_Mortality\_Demographic\_Code\_20190110.R
    

The user should use the standard file submission form in the appendix as a template for the readme file.

### 2.6.3 User Management

#### User Groups

There are four user groups defined for this framework ([Figure 2.8](#ch02.xhtml#fig2_8)):

1.  **Super Admin:** Head of our research unit or center (e.g., CBD-HS Director). Have all of the admin privileges + can add/remove admin accounts. This is usually a legal entity.
    
2.  **Admin:** Have all of the project managers privileges + can create project\_manger\_group and add user to these groups + can add/remove new groups (e.g., Cerner, UK biobank). Main responsibility is Run/Update/Maintenance of DMF and associated files and user management.
    
3.  **Project managers:** Can create project-specific folders and files. The main responsibility (other than general project manager duties) is keeping the file’s name and structure consistent and report the changes to admin if necessary.
    
    Each project has a separate project manager user group. For example, Cerner\_SAH\_Project\_Manager is the user group for the SAH project in the Cerner group. The members of this group are managing files and folders in the CBD\_HS/Cerner/SAH folder.
    
4.  **Regular users:** Are responsible for different aspects of projects.
    

![Figure 2.8 User groups hierarchy.](images/fig2_8.jpg)

**Figure 2.8**  
User groups hierarchy.

The access management to each folder has been discussed in the previous section (Section 2.6.1).

### 2.6.4 Data Management Framework

Now we have a reliable and secure server with a detailed convention for naming and organizing our files and folders, but still, a very important issue remains - the reproducibility. It is crucial to be able to reproduce the data files, reports, and results from the EHR research projects. It is not uncommon that other parts of your organization or other outside organizations want to see how you produced the specific results. Having messy data makes this task challenging or even impossible. The steps we described in the previous section lay the cornerstone in creating a data management framework. First, we should note that EHR data analysis is a multistep project and each step is usually dependent on the data from previous steps (see [Figure 2.1](#ch02.xhtml#fig2_1) and [Chapter 1](#ch01.xhtml#chapter1)). This means that each data file or report is dependent on some other data or report. We can use Directed Acyclic Graphs to visualize these dependencies and create a semiautomatic framework to reproduce the data and analysis results. To describe this framework, we begin with an example project ([Figure 2.9](#ch02.xhtml#fig2_9)).

![Figure 2.9 An example of data structure in DMF.](images/fig2_9.jpg)

**Figure 2.9**  
An example of data structure in DMF.

To keep things simple, we describe an imaginary sub-project (Mortality Prediction) from the SAH Project, that belongs to the Cerner EHR working group. The actual network is bigger and more complicated, but the framework functions will be the same for all of them. As you can see, we can arrange the data hierarchy in layers. Each shape in this figure is considered a node. The research Center (CBD\_HS), Groups (Cerner), Projects (SAH), and Sub-projects (Mortality Prediction) layers are not data nodes, but they are helping us to keep track of the changes and organize the downstream nodes (the nodes lower than a specific node). The Extracted Data (e.g., extracted lab table), Cleaned Data (cleaned lab table), Prepared Data (prepared lab table), Reports (reports 1 and 2), and Papers (paper 1) are considered as real data nodes in DMF. Each directional edge (arrow) shows the dependency relationship between the current node and upstream nodes (nodes at the same level or higher level). Using the proposed file and folder convention, a computer code can be written to scan all of the files and folders inside the main folder (CBD\_HS) and create this network. There are multiple visualization modules to visualize your network as a 2-dimensional (with concentric circles as layers) or a 3-dimensional (with concentric spheres as layers) graphs. As you can see this graph can be considered as a Directed Acyclic Graph. At the next step, we will describe the properties of nodes and edges in DMF ([Figure 2.10](#ch02.xhtml#fig2_10)).

![Figure 2.10 The edge and node properties in DMF.](images/fig2_10.jpg)

**Figure 2.10**  
The edge and node properties in DMF.

In [Figure 2.10](#ch02.xhtml#fig2_10), we show the part of the network downstream to the Mortality Prediction sub-project from the SAH project. In this network, each node and each edge have their specific properties. The edge property is the code that connects upstream nodes to a downstream node. For example, the edge connecting Cleaned Medication (upstream node) to the Prepared Medication (downstream node) has Preparation code 1(PC1) as its property. Some of the properties of the edges are inherent to the network, e.g., the nodes that are connected by the edge. We are not showing these essential properties in the figure. Another addition to the edge property can be the execution time, so in the future, the admin can calculate a rough estimate about how long it takes to update all of the nodes in the DMF.

Similarly, each node has the following property elements associated with it:

**Name:** Name of the file excluding the date part (last eight characters according to folder and file naming convention). It can be recorded by DMF during the scanning of the CBD\_HS folder.

**Type:** The layer that the node belongs to. Again, this element can be generated by DMF during the scanning of the CBD\_HS folder.

**Dependencies:** The nodes upstream that are needed to generate the current node. The user (users) who created the file should inform the project manager or admin about the dependencies. These dependencies should be included in the data submission form (appendix).

**Code** (if applicable): The code that needs to be executed on the dependencies to create the current node. The code or command to run the code should be submitted when the user creates a file and wants to place it in the DMF.

**Users:** The users involved in generating the current node. This property will be recorded according to the data submission form. The user (users) email address can be retrieved using the User ID.

**Date:** last eight characters of the file name according to folder and file naming convention. It can be recorded by DMF during the scanning of the CBD\_HS folder.

In [Figure 2.10](#ch02.xhtml#fig2_10), we show the property of one node in each layer. Every node in the DMF has a similar property structure and information.

You can set up the DMF to update the network in three different ways:

1.  Update the network as soon as a file added to the CBD\_HS folder or its sub-folders.
    
2.  Update Network on a pre-defined date and time (e.g., every midnight).
    
3.  Update the network when the DMF administrator runs the update command.
    

Now we will describe how the DMF behaves in the following scenarios:

**Scenario 1—adding a new file:** in this scenario, the DMF will scan the CBD\_HS folder and its sub-folders, and detect the new file. By using the convention, it can decide on which layer it should put the new file (new node) and can create the properties of the new node according to the file submission form as described above ([Figure 2.11](#ch02.xhtml#fig2_11)).

![Figure 2.11 Scenario 1: adding a newly extracted Procedure data to DMF.](images/fig2_11.jpg)

**Figure 2.11**  
Scenario 1: adding a newly extracted Procedure data to DMF.

**Scenario 2—updating a file (same data structure):** in this scenario, the DMF will scan the CBD\_HS folder and its sub-folders, and detect the updated date (the last eight characters of the file name) and marks it as “Updated” (same structure) node. Then the DMF will detect all downstream nodes that are affected by the new change and mark them as “Update needed”. If the downstream nodes are generated by code, it can regenerate the downstream node, otherwise, the node will remain in “Update needed” status ([Figure 2.12](#ch02.xhtml#fig2_12)). By using properties of affected nodes, the DMF will notify (by email or other messaging services) all of the affected users. In [Figure 2.12](#ch02.xhtml#fig2_12), the edges with a white circle on them have associated code.

![Figure 2.12 Scenario 2: updating a file (same data structure).](images/fig2_12.jpg)

**Figure 2.12**  
Scenario 2: updating a file (same data structure).

**Scenario 3—updating a file (new data structure):** in this scenario, the DMF will scan the CBD\_HS folder and its sub-folders, and detect the new file name. If it is submitted as a new file, then it will continue as scenario 1; but if it is an existing file with a new data structure according to the file submission form (i.e., the downstream codes cannot be applied to it), then it should be marked as “Updated” (new structure) node. Then the DMF will detect all downstream nodes that are affected by the new change and mark them as “Update needed” ([Figure 2.13](#ch02.xhtml#fig2_13)). By using affected nodes properties, the DMF will notify (by email or other messaging services) all of the affected users.

![Figure 2.13 Scenario 3: updating a file (new data structure).](images/fig2_13.jpg)

**Figure 2.13**  
Scenario 3: updating a file (new data structure).

This Data Management Framework (DMF) will be semi-automatic and updates the data files and reports if it is applicable. The DMF admin can add a function to create a unique ID for each file that stores the name and date of the file using a hashing function. Creating this type of ID can eliminate the need to use a long path in the coding and helps in keeping a well-organized data structure.

## ![image](images/inline1_1.jpg)  
2.7 Discussion and Summary

It is extremely important to efficiently manage the data, computer codes, files, reports and products for each of the EHR research projects so that the resources can be shared and leveraged, and the reproducibility of research results can be ensured. We summarize some tips for EHR project management as follows.

**Secure your data**. Take necessary measures to secure your data by the use of backups, Version Control Systems, and Antivirus and firewall hardware and software.

**Develop the conventions early**. As we have discussed in this chapter, it is better to develop file, folder, and coding conventions early. Reorganizing the files and rewriting the codes after you have collected a significant number of files can be a challenging task.

**Seek team members’ opinions about the conventions**. Every data scientist has his/her own habits in storing the files and coding (hence, some have messier habits). Adapting to new routines in coding, naming the variables, and naming of the files and folders can be hard for some and they may become hesitant to do so. It is important to involve as many team members as you can in developing the conventions at the beginning of a project. By doing so, first, you can develop a better convention, and second, adopting the new convention will be easier for your team members.

**Follow the convention**. After finalizing the convention, everyone must follow it. If some members do not follow the convention, it can be discouraging for other team members. Keep in mind, any project and data management framework relies on a pre-defined convention and creating unconventional files or folders can cause your project management framework to operate under sub-optimal conditions, or even worse, damage the project.

**Try to use OOP**. As we have discussed, try to use Object-Oriented Programming. It is easier to use object-oriented codes in the project and data management framework.

**Take Access Management seriously**. EHR data is sensitive. It is strongly recommended to restrict the access of users to the files they do not need. Furthermore, by keeping the write privilege only for project managers and administrators, you ensure that the data structure follows the finalized file and folder convention.

**Regularly check the file and folder structure**. The administrator should check the project manager’s ability to follow the convention. If a project manager has misunderstood the convention, it is better to fix it early before it becomes more prevalent.

**Check the codes rigorously**. Check all of the codes and make sure they will not change the data in an unwanted manner. Pay special attention to your DMF core and test it under different scenarios. If the DMF core makes errors, you may lose part or all of your data, and VCS or backups may become the only method to restore the data. Try to optimize the codes as much as possible.

**Make sure you have enough information**. You will frequently need to re-run the codes. Having a clear description of the codes and files will be extremely helpful when you need to come back and cannot remember what you have done before. EHR research teams are usually big and staff turnover is inevitable. By keeping detailed and well-organized documentation, you will save time and prevent unnecessary challenges.

**This is an example**. The Data Management Framework described above in this chapter is just an example and each organization may need to change this framework or even create their own from the beginning to fit their projects. The methods described in this chapter should be considered as a groundwork to create a more detailed and sophisticated Data Management Framework (DMF).

Project and data management are important issues especially in this era of Big Data. As the scope of big data research changes over time, the need for a better Data Management Framework becomes more evident. In the future, we may update this chapter to reflect the new challenges and present newly developed strategies.

## ![image](images/inline1_1.jpg)  
2.8 Appendix—File Submission Form

**Center for Big Data in Health Sciences**

File Submission Form version 1.1

***Title: Cleaned Medication Data for Mortality Prediction Sub-project,  
SAH Project***

**Main file:**

*   Filename: SAH\_Mortality\_Meds\_20200210.csv
    
*   File date: 2/10/2020
    
*   Type of file
    

![image](images/inline2_1.jpg)

DMF ID:

Users associated:

1- User-2 2- User-3

The files used to create this file:

| **No** || **File name** || **File address** || **MDF ID** |
| --- | --- | --- | --- |
| 1 || SAH\_Mortality\_Demographic\_20200203.csv || /CBD\_HS/Cerner/SAH/ Mortality\_Prediction/Cleaned\_Data/ Demographics/ || 12345678 |
| 2 || SAH\_Mortality\_Meds\_20200203.csv || /CBD\_HS/Cerner/SAH/ Mortality\_Prediction/Raw\_Data/Labs/ || 12345679 |
| 3 ||  ||  ||  |

**Code file:**

*   Did you use codes:
    
    ![image](images/inline2_2.jpg)
    
*   Coding environment Python
    
*   OS environment Windows
    
*   Non-standard packages/libraries used:
    

| **No** || **Package Name** || **Installation Command** || **Version** |
| --- | --- | --- | --- |
| 1 || P\`otly || pip install plotly || 3.4.1 |
| 2 || Python-docx || pip install python-docx || 0.8.9 |
| 3 ||  ||  ||  |

If the code is callable, put the command to generate the result:

***The brief description of the methods***

### ![image](images/inline1_1.jpg)  
**Note**

[1](#ch02.xhtml#Cen2_1) Redundant Array of Independent Disks

### ![image](images/inline1_1.jpg)  
References

1\. Statista - The Statistics Portal. *Statista*. [https://www.statista.com/statistics/551501/worldwide-big-data-business-analytics-revenue/](https://www.statista.com). Accessed August 8, 2019.

2\.  Global big data and business analytics revenue 2015–2022 | Statista. [https://www.statista.com/statistics/590054/worldwide-business-analytics-software-vendor-market/](https://www.statista.com). Accessed August 8, 2019.

3\. Shacklett, M. 4 ways to improve big data project management - TechRepublic. [https://www.techrepublic.com/article/4-ways-to-improve-big-data-project-management/](https://www.techrepublic.com). Accessed August 8, 2019.

4\. Soares, M. S., W. S. Paiva, E. Z. Guertzenstein, *et al* 2013. Psychosurgery for schizophrenia: History and perspectives. *Neuropsychiatric Disease and Treatment* 2013 (**9)**, 509–515. doi:[10.2147/NDT.S35823](http://dx.doi.org/10.2147/NDT.S35823).

5\. Hviid, A., J. V. Hansen, M. Frisch, and M. Melbye. 2019. Measles, mumps, rubella vaccination and autism a nationwide cohort study. *Annals of Internal Medicine* **170**((8)), 513–520. doi:[10.7326/M18-2101](http://dx.doi.org/10.7326/M18-2101).

6\. What is project management? | APM. [https://www.apm.org.uk/resources/what-is-project-management/](https://www.apm.org.uk). Accessed April 28, 2020.

7\. Project management - Wikipedia. [https://en.wikipedia.org/wiki/Project\_management](https://en.wikipedia.org). Accessed May 4, 2020.

8\. Munns, A. K., and B. F. Bjeirmi. 1996. The role of project management in achieving project success. *International Journal of Project Management* **14**((2)), 81–87. doi:[10.1016/0263-7863(95)00057-7](http://dx.doi.org/10.1016/0263-7863\(95\)00057-7).

9\. Oussous, A., F. Z. Benjelloun, A. Ait Lahcen, and S. Belfkih. 2018. Big data technologies: A survey. *Journal of King Saud University Computer and Information Sciences* **30**((4)), 431–448. doi:[10.1016/j.jksuci.2017.06.001](http://dx.doi.org/10.1016/j.jksuci.2017.06.001).

10\. Chacon, S., and B. Straub. 2014. *Pro Git.* 2nd edn ed. Apress. [https://git-scm.com/book/en/v2](https://git-scm.com).

11\. What is Git: become a pro at Git with this guide | Atlassian Git Tutorial. [https://www.atlassian.com/git/tutorials/what-is-git](https://www.atlassian.com). Accessed August 22, 2019.

12\. Potok, T., M. Vouk, and A. Rindos. 1999. Productivity analysis of object-oriented software developed in a commercial environment. *Software – Practice and Experience* **29**((10)), 833–847. doi:[10.1002/(SICI)1097-024X(199908)29:10<833::AID-SPE258>3.0.CO;2-P](https://www.doi.org/10.1002/\(SICI\)1097-024X\(199908\)29:10%3C833::AID-SPE258%3E3.0.CO;2-P).

13\. Tomasello, M. The ultra-social animal. *The European Journal of Social Psychology* 2014. **44**((3)), 187–194. doi:[10.1002/ejsp.2015](http://dx.doi.org/10.1002/ejsp.2015).

# [3 ](#contents.xhtml#toc1_50)![image](images/inline1_1.jpg)  

# [EHR Databases and Data Management: Data Query and Extraction](#contents.xhtml)  
               

Gen Zhu, Vi K. Ly, Michael Gonzalez, Leqing Wu, Hulin Wu and Ashraf Yaseen

## ![image](images/inline1_1.jpg)  
3.1 Introduction

Generally, data management refers to the administrative process of collecting, keeping and using data in a scientific and systematic way. Data management is a complex process with key ingredients including data governance, data standardization, data integration, data enrichment, data storage and data quality control. Historically, from mechanical-punched cards, sequential record processing to the modern computer, technology has been evolving rapidly in order to manage data in more effective ways ([Gray 1996](#ch03.xhtml#ref3_4)). In our modern era, technology can help people organize and utilize their data at different levels. However, when data becomes “bigger” and more complex, it poses new challenges and at the same time generates more opportunities. Examples of challenges include: how to deal with various types of data, how to integrate widely distributed data sources, and how to store and analyze data in real-time. On the other hand, data is gradually being regarded as a valuable asset for many organizations because it promises great opportunities. People are starting to realize the potential benefits that data can provide. Under such circumstances, data management, without a doubt, is essential in tackling the challenges and seizing opportunities for breakthroughs. Through effective data management, we can easily and efficiently extract useful insights.

Big data emerges in many fields such as social media, commercial markets, astronomy, biomedicine, healthcare, and many more fields. Among those, data in healthcare is one area that recently attracted attention from academia and industries. With the rapid development of information systems, clinical practices and healthcare providers generate terabytes of healthcare data in daily operations, which can come from clinical medical records, pharmacy systems, claim records, genomics and sensory devices. By mining a variety of healthcare data, an estimate of at least $300–$450 billion of healthcare expenses can be reduced (Groves et al. 2013).

Electronic medical records (EHR) data is one of the main healthcare data sources. EHR is a digital version of the paper-based medical charts. It contains detailed information about patients, including medical treatments, diagnoses, laboratory tests and so on. An efficient EHR system is necessary to facilitate the effective operation of healthcare providers and improve patient care. In this chapter, we will review EHR database systems and tools available for data query and extraction for the purpose of research and scientific discoveries.

## ![image](images/inline1_1.jpg)  
3.2 EHR/EMR Database Availability and Access

Many database systems for healthcare were developed in the past few decades. The main objective of such systems was to better manage the administrative and operational processes performed by healthcare staff and personnel. Nowadays, many of these database systems are managing large volumes of healthcare data, including EHR/EMR data, imaging, clinical notes, genomics, proteomics, and other kinds of healthcare-related data for hospitals, clinics, and healthcare facilities all over the world. Vendors of some healthcare database systems are making their data available for researchers. [Table 3.1](#ch03.xhtml#table3_1) provides examples of healthcare data providers:

**Table 3.1** Healthcare/Medical Observation Data Providers

| **Provider Name** || **Description** || **Data Type** || **Data Statistics** |
| --- | --- | --- | --- |
| Optum || Largest healthcare IT company in the world. || EHR, Claims, Pharmacy, Behavior  
Oncology, Integrate, Extended || 180&#160;M claims,  
160&#160;M claims patients,  
85&#160;M EHR data,  
40&#160;M EHR patients,  
35&#160;M consumers,  
2&#160;K data fields |
| --- | --- | --- | --- |
|  || [https://www.optum.com/solutions/prod-nav/data.html](https://www.optum.com) ||  ||  |
|  || [https://www.optum.com/solutions/prod-nav/claims-data.html](https://www.optum.com) ||  ||  |
| Cerner || Integrating existing laboratory, radiology and pharmacy data into a single enterprise clinical data repository. || Her || 69&#160;M patients |
|  || [https://www.cerner.com/ap/en/solutions/data-research](https://www.cerner.com) ||  ||  |
| Truven || The core databases—Commercial, Medicare Supplemental, and Medicaid—are huge, representing over 170 million patients since 1995. || EHR, Claims  
MarketScan Research Databases || 170&#160;M patients |
|  || [https://www.ibm.com/watson-health/learn/truven-health-analytics](https://www.ibm.com) ||  ||  |
| IQVIA || Pharmacy, hospital and medical claims at the anonymized patient level. || EHR, Pharmacy, Claims || 600 million non-identified patient records |
|  || [https://www.iqvia.com/solutions/real-world-evidence/real-world-data-and-insights](https://www.iqvia.com) ||  ||  |
| McKesson Technology Solutions || Distributing pharmaceuticals at a retail sale level and providing health information technology, medical supplies, and care management tools. iKnowMed EHR. || Oncology, EHR, Claims || HER—115 million patient visits, >2,200 providers across  
650 sites, Claims Data -2.5&#160;M patient records |
|  || [https://www.mckesson.com/biopharma/commercialization-data/](https://www.mckesson.com) ||  ||  |
| Epic || A privately-held healthcare software company. Its software is used by hospitals, organizations patients’ home and so on. According to KLAS report, large private hospitals and organizations prefer to choose Epic. || her || 250 million patients |
|  || [http://www.epic.com](http://www.epic.com%20) ||  ||  |
| InterSystems || Vendor of software systems and technology for high-performance database management, rapid application development, integration, and healthcare information systems. || EHR, IRIS ||  |
|  || [https://www.intersystems.com/](https://www.intersystems.com) ||  ||  |
| BSBC || Aggregate 2.3 billion procedures each year, from 96% of all hospitals in the country and 92% of doctors. || Claims  
BCBS Axis ||  |
|  || [https://www.bcbs.com/about-uscapabilities-initiatives/bcbs-axis](https://www.bcbs.com) ||  ||  |
| NCQA || NCQA makes its data available for purchase by health plans, provider organizations, states, pharmaceutical organizations, consultants and researchers to promote better understanding of key metrics in evaluating quality improvement. || Commercial, Medicaid  
Medicare  
Quality Compass || Current Year Data, or 3 years of trended data. Commercial, Medicare (HEDIS data, no CAHPS data), Medicaid |
|  || [http://www.ncqa.org/hedis-quality-measurement/quality-measurement-products/quality-compass](http://www.ncqa.org) ||  ||  |
| SEER || SEER collects cancer incidence data from population-based cancer registries covering approximately 34.6% of the US population. You have to have a specific protocol that includes SEER incidence and population data associated by age, sex, race, year of diagnosis, and geographic areas. || SEER 18 Databases  
SEER 21 Databases || 1975–2016 Data, 10 million cases |
|  || [https://seer.cancer.gov/data/](https://seer.cancer.gov) ||  ||  |
| PREMIER || 3,900 US hospitals and more than 150,000 other provider organizations. || Claims  
Premier Applied Sciences (PAS) || 530&#160;M outpatient visits, 50&#160;M visits per year since 2011. |
|  || [https://www.premierinc.com/wpdm-package/research/](https://www.premierinc.com) ||  ||  |
| NHANES || The National Health and Nutrition Examination Survey (NHANES) is a program of studies designed to assess the health and nutritional status of adults and children in the US. The survey is unique in that it combines interviews and physical examinations. NHANES is a major program of the National Center for Health Statistics (NCHS). NCHS is part of the Centers for Disease Control and Prevention (CDC) and has the responsibility for producing vital and health statistics for the nation. || Survey, Demographic, Dietary, Examination, Laboratory, Questionnaire data || NHANES—1999–2020, results of survey every 2 years |
|  || [https://www.cdc.gov/nchs/nhanes/new\_nhanes.htm](https://www.cdc.gov) ||  ||  |
| HCUP || The Healthcare Cost and Utilization Project (HCUP, pronounced “H-Cup”) is a family of healthcare databases and related software tools and products developed through a federal-state-industry partnership and sponsored by the Agency for Healthcare Research and Quality (AHRQ). HCUP databases bring together the data collection efforts of state data organizations, hospital associations, private data organizations, and the federal government to create a national information resource of encounter-level healthcare data (HCUP partners). HCUP includes the largest collection of longitudinal hospital care data in the United States, with all-payer, encounter-level information beginning in 1988. These databases enable research on a broad range of health policy issues, including cost and quality of health services, medical practice patterns, access to healthcare programs, and outcomes of treatments at the national, state, and local market levels. || Inpatient stays, emergency department visits, and ambulatory care || 1990–2015  
Pricing chart shows what datasets are available per year.  
Each year of the NIS includes over 7 million inpatient stays.  
KID—2 million to 3 million  
Pediatric inpatient records per year.  
NEDS—30.5 million ED visits at 953 hospitals that approximate a 20% stratified sample of US hospital-owned EDs. Weights are provided to calculate national estimates representative of 143 million ED visits in the US for calendar year 2015.  
NRD—the 2015 NRD contains about 85% of SID discharges from the participating states. Unweighted, the NRD contains approximately 17.2 million discharges in 2015. Weighted, it estimates roughly 36 million discharges in the US. |
|  || [https://www.hcup-us.ahrq.gov](https://www.hcup-us.ahrq.gov) ||  ||  |
| UKBioBank || UK Biobank is a national and international health resource with many research opportunities, open to all health researchers. UK Biobank aims to improve the prevention, diagnosis and treatment of a wide range of serious and life-threatening illnesses— including cancer, heart diseases, stroke, diabetes, arthritis, osteoporosis, eye disorders, depression and forms of dementia. It is following the health and well-being of 500,000 volunteer participants and provides health information which does not identify them, to approved researchers in the UK and overseas, from academia and industry. || Imaging, Demographics, Biological Samples, Genomics, Health-Related Outcomes || 0.5&#160;M patients |
|  || [http://www.ukbiobank.ac.uk](http://www.ukbiobank.ac.uk%20) ||  ||  |
| CPRD || Clinical Practice Research Datalink (CPRD) is a real-world research service supporting retrospective and prospective public health and clinical studies. CPRD is jointly sponsored by the Medicines and Healthcare Products Regulatory Agency and the National Institute for Health Research (NIHR), as part of the Department of Health and Social Care.  
CPRD collects de-identified patient data from a network of GP practices across the UK. Primary care data are linked to a range of other health-related data to provide a longitudinal, representative UK population health dataset. The data encompass 45 million patients, including 13 million currently registered patients. || EHR || CPRD data are sourced from a UK-wide network of over 1,700 primary care practices and include 45 million patients of which 13 million are currently registered active patients with at least 20 years of follow-up for 25% of the patients.  
The CPRD database contains coded and anonymized EHR data from primary care practices capturing information on demographic data, diagnoses and symptoms, drug exposures, vaccination history, laboratory tests, referrals to hospital and specialist care |
|  || [https://www.cprd.com/](https://www.cprd.com) ||  ||  |
| JMDC || The JMDC Claims Database is an epidemiological receipt database that has accumulated receipts (inpatient, outpatient, dispensing) and medical examination data received from multiple health insurance associations since 2005. The cumulative dataset is approximately 5.6 million subjects (as of June 2018), and it is possible to follow the prevalence rate and incidence under a general population, including healthy individuals. Even if a subject transfers hospitals or uses multiple facilities, the data can be tracked. The database is used by major pharmaceutical and medical device manufacturers, life insurance companies, non-life insurance companies, government offices, and more than 50 universities in Japan. || Claims (in-patient, out-patient, pharmacy) received from payers, annual health checkups data || The cumulative observed population of 5,600,000 with data from 2005 |
|  || [https://www.jmdc.co.jp/en/jmdc-claims-database](https://www.jmdc.co.jp) ||  ||  |
| MEDITECH || is a privately held IT vendor who provides software service for health care facilities. It started as a programming language company. But later, developing health care systems became the company’s core business. Their latest cloud-based EHR called Expanse focus on the entire continuum of care, with a focus on patient engagement. ||  ||  |
|  || [https://ehr.meditech.com/](https://ehr.meditech.com) ||  ||  |
| Allscripts Veradigm || Offering practice management, EHR and financial management systems primarily for medium to small-sized hospitals and physician practices. Allscripts products cover most areas of clinical care, including emergency department, surgery, anesthesia, population health, and more. Veradigm is a health information technology, analytics and intervention solutions company. Now the largest source of de-identified ambulatory patient records available. || Biopharma, health plans, healthcare providers, life sciences || 150 million patients |
|  || [https://veradigm.com/](https://veradigm.com) ||  ||  |
| eClinicalWorks || is a privately held health care service provider for many kinds of medical professionals, focused on a cloud-based platform. Patient engagement, population health, and revenue cycle management are its IT solutions. ||  ||  |
|  || [https://www.eclinicalworks.com/](https://www.eclinicalworks.com) ||  ||  |
| MedMining—Geisinger Health || Integrated health services organization widely recognized for innovative use of electronic health records and the development of innovative care delivery models. Geisinger serves millions of residents throughout Pennsylvania and New Jersey. || EHR || 3 million patients, over 20 years |
| THIN Database || The Health Improvement Network (THIN) database is a large UK primary care database. The THIN Database Research Team uses this database, containing data collected from over 550 general practitioners spread over the UK, for research into cardiovascular disease, mental health, pharmacoepidemiology and other fields of primary care research (publications). UK Primary Care database contains anonymized longitudinal patient records for approximately 6% of the UK Population. The data collection, which goes back to 1994, is nationally representative of the UK population. || EHR || ~7.5 million patients |
|  || [https://www.the-health-improvement-network.com/](https://www.the-health-improvement-network.com) ||  ||  |
| Amplity Health  
RealHealthData || RealHealthData networks with various Real World Evidence data sources to compile a database of information providing a unique perspective on patient conditions and provider interactions. || EHR || roughly 60% (inpatient) and 40% (outpatient) |
|  || [https://realhealthdata.com/](https://realhealthdata.com) ||  ||  |

In this book, we present the statistical methods and machine learning approaches based on our experience in exploring and mining the Cerner EHR database. Cerner is an American health technology company that provides various services to over 27,500 facilities around the world, supporting the clinical, financial and operational needs at different organizations. According to KLAS Research report ([Tate and Warburton 2019](#ch03.xhtml#ref3_8)) in 2018, Cerner holds nearly 26% market share in the EHR system market, while Cerner has more collaborations with public hospitals compared to other EHR companies. Its main product is Cerner Millennium, which is an EHR platform, allowing the clinicians or hospitals to view patient health data in real-time. Cerner Health Facts® EMR database comprises de-identified EHR data from over 700 participating Cerner client hospitals and clinics in the United States, including patients’ demographics, encounters, diagnoses, procedures, lab results, medications, vital signs, and other clinical observations. The version of the Cerner database that we acquired contains medical records for 69 million unique patients from 2000–2018, which is a good resource to conduct big data analysis for research and scientific discoveries.

## ![image](images/inline1_1.jpg)  
3.3 EHR/EMR Database Design and Structure: Database Queries

Most EHR/EMR database systems are based on relational database design. Oracle and Microsoft SQL server are among the most commonly used Database Management Systems (DBMS) employed by most EHR/EMR vendors. When healthcare data is acquired or purchased from vendors, the data format is usually in text files (or csv files). Similarly, publicly available and free healthcare data often exists in text file formats. For example, when we purchased the 2018 version of the Cerner Health Facts database, we received the EHR data in csv files. Furthermore, some vendors, including Cerner, provide design details of their database structure through data dictionaries and database schema diagrams. The data dictionary document that we received from Cerner explains the data sets and the data elements within the Health Facts, and the database schema defines the database tables, fields and relationships. Using the details of the database design, one can recreate a database system to host and manage healthcare data for research purposes.

### 3.3.1 Database Construction

In general, a database system development process can be divided into three stages: database design, implementation, and database maintenance. Database design starts with a conceptual data model and produces a specification of a logical schema. The output of this stage is a detailed relational specification, the logical schema, of all the tables and constraints needed to satisfy the description of the data in the conceptual data model. Implementation includes the construction of a database according to the specification of a logical schema. This will include the specification of an appropriate storage schema, security enforcement, external schema and so on. Finally, database maintenance, including operational maintenance, is to ensure that performance of the database system is maintained at an acceptable level, which requires effective communications among the team members to determine and implement changes as needed.

The design and construction of an EHR database system for research purposes should follow the description of the schema document received from the vendor. A traditional relational DB design is most common, but a distributed DB design is also an option for efficient data management.

### 3.3.2 Traditional Relational Database System

Database systems based on the relational data model are most commonly used in healthcare data management. In a relational model, data is organized in tables, linked with relationships, and controlled by constraints. Famous examples of relational database management systems include Oracle, Microsoft SQL server and PostgreSQL.

The steps for creating your own database system to manage healthcare data include,

*   Setup database environment (database server configuration)
    
*   Create schema and tables
    
*   Populate tables with data
    
*   Operate database server (run server process)
    

### 3.3.3 Distributed Database System

As database sizes keep rapidly increasing, in order to improve the performance of data manipulation, online analytical processing (OLAP) and online transaction processing (OLTP), the Apache Hadoop was developed as a framework for running applications on large clusters from commodity hardware. Hadoop provides a distributed file system (HDFS) that stores data on compute nodes, and implements a computational paradigm named Map/Reduce, where the application is divided into several small fragments of work, each may be executed or re-executed on any node in the cluster. The Apache HBase, established on Hadoop HDFS, provides the capability to read/write big data randomly in real-time. As an open-source, distributed non-relational database management system, HBase modeled after Google’s Bigtable: A Distributed Storage System for Structured Data, developed by Chang et al. ([Fay et al., 2008](#ch03.xhtml#ref3_2)).

Unlike traditional SQL databases (e.g., Oracle, Microsoft SQL, MYSQL, PostgreSQL), the NoSQL databases (e.g., HBase, MongoDB, Cassandra DB) provide more flexible solution on unstructured data (e.g., photos, videos, documents and articles). They are generally document-oriented. In this way, the unstructured data can be stored in a single document that can be easily found, but it is not necessarily categorized into fields in relational databases.

For the Cerner EHR database, we employed the HBase framework mainly for performance concern, since many tables are very large with billions of records. In an HBase Cluster, the query and analysis performance are significantly enhanced. The comparison shows ~7x speed improvement on a two-node cluster.

## ![image](images/inline1_1.jpg)  
3.4 Data Extraction

### 3.4.1 Define Inclusion/Exclusion Criteria for Data Extraction

EHR/EMR data present a wealth of valuable information for researchers. Tapping into this potential necessitates collaboration between domain experts (i.e., clinicians, healthcare experts and physicians) and data analysts as a starting point in EHR research. This collaboration should stimulate and produce some interesting topics to study, which is not trivial. Most of the time we, as statisticians and data scientists, do not have a clear scientific question in mind. On the other hand, domain experts may have enough scientific knowledge to identify important questions or hypotheses in a biomedical or clinical field, but they may not know whether the data are good enough or analytic methods are available to address the questions or hypotheses. It is essential for domain experts and statisticians/data scientists to closely work together to identify good and important questions and hypotheses. This process sometimes is not easy and may require multiple iterations until a good question or hypothesis can be identified. More discussions on this point can also be found in [Chapter 1](#ch01.xhtml#chapter1) (Section 1.2).

Once the questions or hypotheses are determined and the objective of the project is clear, initial data extraction and data exploration can begin. In order to extract the appropriate data for the targeted questions, we need to clearly define inclusion/exclusion criteria for data extraction. The initial inclusion/exclusion criteria for data extraction can be simple but must be refined later after further data exploration and data cleaning. If the identified question or hypothesis is regarding a disease, all the diagnosis codes (e.g., ICD-9 codes) related to this disease need to be identified so that all the relevant data from all the patients with these diagnosis codes can be extracted from the EHR/EMR database. Sometimes this may not be trivial since there are many disease diagnosis codes possibly related to the disease and it may not be easy to identify all the diagnosis codes or ICD-9 codes by keyword search. Some domain knowledge related to the disease is needed to identify all synonyms of the disease. In this case, some natural language processing (NLP) approaches can also be used for this purpose. Sometimes a patient is likely a confirmed case of disease by reviewing his/her records of medications, treatment procedures or lab test results, but the disease diagnosis code or ICD-9 code of the disease did not appear in the patient’s record due to missing data or other errors. In this case, more patients related to this particular disease can be possibly identified through medication, procedure and lab test tables. However, it needs domain knowledge to identify the medications, procedures and lab test results, which are almost uniquely related to this disease. Finally, it is necessary to use rigorous procedures and approaches to confirm the cases of disease diagnosis via formal disease phenotyping, which will be discussed in the next subsection.

Some other inclusion/exclusion criteria may also involve patient demographics such as age, gender or race, or the data from other EHR/EMR tables such as medication, procedure, lab test, clinical event, vital sign or microbiology tables. Some of these data or variables are quite accurate and complete, some others may have high uncertainty, high missing or error rate. It is quite challenging to accurately identify the targeted cohort of patients that meet all inclusion/exclusion criteria.

### 3.4.2 Phenotyping: Cohort Identification

One of the fundamental steps when extracting data from an EHR database is to define the cohort of patients. In particular, if the cohort is defined based on disease diagnosis, it is known as electronic “phenotyping”. Phenotyping has important applications across different study designs (such as cross-sectional studies, case-control studies, and experimental studies) to identify cohorts of patients with characteristics of interest. Moreover, phenotyping is also used in the field of bioinformatics. This application of linking genomic data with EHR-derived phenotypes is called phenomics and discussed in detail in the human phenome project ([Denny 2013](#ch03.xhtml#ref3_12); [Freimer and Sabatti, 2003](#ch03.xhtml#ref3_13)).

Nevertheless, due to input errors, biased billing codes, missingness, and many other factors, correctly identifying interested study cohort is not trivial. Depending on the EHR data types, electronic phenotyping algorithms can range from the basic rule-based methods on structured data to advanced methods using unsupervised models on unstructured data ([Table 3.2](#ch03.xhtml#table3_2)). Basically, the general methods of phenotyping include rule-based methods, machine learning (e.g., natural language processing (NLP), supervised learning methods, latent variable methods, unsupervised learning methods), and hybrid approaches combining different strategies (e.g., rule-based and machine learning).

1.  Rule-Based Methods  
    When we start data extraction, the most straightforward approach is to utilize the International Classification of Diseases (ICD) billing codes of the target disease to obtain data from the EHR database system. Since 1999, researchers have been using ICD-9 codes to identify patients with acute myocardial infarction ([Petersen et al. 1999](#ch03.xhtml#ref3_27)). But ICD codes are for billing purposes and they may not reflect the true status of more complicated chronic diseases which may lead to many unexpected misclassification errors. Hence, we need to consider more variables such as lab results, diagnosis codes, and medications when developing rules or definitions to identify the targeted cohort of patients. In reality, the process of developing phenotyping rules usually involves one or more clinicians specifying inclusion and exclusion criteria based on a structured EHR database that has clear diagnosis codes. Developing phenotype criteria is a tedious process that can take 6–8 months to complete ([Kirby et al. 2016](#ch03.xhtml#ref3_20)). Due to their complicated nature, it is important to share phenotypes publicly for validation and implementation by other healthcare organizations and research institutes. That was the reason for the creation of PheKB (Phenotype Knowledgebase). This is a repository of phenotypes that includes 44 open-sourced phenotypes of different diseases. A majority of phenotypes on PheKB comes from the eMERGE (Electronic Medical Records and Genomics) network. This network is a collaboration of multiple medical centers that focus on developing EHR phenotype definitions for genomic research ([Gottesman et al. 2013](#ch03.xhtml#ref3_14)). eMERGE is responsible for a large catalog of phenotypes, including type 2 diabetes, cardiovascular disease, and sclerosis ([Kho et al. 2012](#ch03.xhtml#ref3_19), [Ritchie et al. 2010](#ch03.xhtml#ref3_29)). For example, to identify patients with type 2 diabetes (T2DM), investigators at Northwestern University developed an eMERGE definition for type 2 diabetes (excluding T1DM cases) by taking into account an HbA1c above 6.5%, at least one T2DM diagnosis code and at least one hypoglycemic medication. This definition produces a 98% positive predictive value for the identification of T2DM patients compared with clinician review after validating at three different sites ([Kho et al. 2012](#ch03.xhtml#ref3_19)). Therefore, the eMERGE phenotype is considered a reliable algorithm for T2DM classification in many case-control/cohort studies.
    
2.  Machine Learning Methods  
    Due to the high missing rate of EHR data in many clinical settings, the rule-based approach may have low sensitivity. Furthermore, the rule-based approach is not generalizable to other diseases. For example, the definition of diabetes identification cannot be used on hyperthyroidism. With the enormous number of diseases and syndromes, the method of rule-based phenotyping is not efficient although it is more reliable with high specificity.
    
    In order to achieve high-throughput phenotyping, a growing number of studies have used machine learning methods to learn the pattern from the data and label the patients automatically. Since 2013 researchers started focusing more on adopting standardized terminologies in concept extraction and on developing phenotyping systems using unsupervised machine learning and deep learning methods. NLP analysis of unstructured clinical notes is another direction to determine the disease cohort. According to Martin-Sanchez et al., 80% of data captured in EHRs recorded are unstructured data (clinical notes, pathology reports, and discharge summaries). Clinical notes include rich information including diagnosis, medication, etc.. NLP is a useful technique for electronic phenotyping and often integrated with the rule-based method or machine learning methods. [Xu et al. (2010)](#ch03.xhtml#ref3_17) developed a new natural language processing system (MedEx), which helps in extracting medication information from clinical notes. [Soysal et al. (2017)](#ch03.xhtml#ref3_30) created CLAMP (Clinical Language Annotation, Modeling, and Processing Toolkit) as a multipurpose NLP tool. Open Health NLP Consortium (OHNLP) is a public resource where researchers can find these NLP tools including the ones we mentioned earlier. Using these NLP tools, [Carroll et al. (2011)](#ch03.xhtml#ref3_10) combined NLP-derived mentions of concepts and medications with structured data to create a support vector machine (SVM) classifier for rheumatoid arthritis. There are many other use cases of machine learning methods for phenotyping. Hubbard et al. (2019) introduced a Bayesian latent phenotyping approach that deals with imperfect and missing data when there are no gold-standard data available. [Huang et al. (2004)](#ch03.xhtml#ref3_18) used a process called FSSMC (feature selection via supervised model construction) to reduce 410 structured variables down to 47 variables, and then rank these features to determine the features that had the highest performance in identifying diabetes patients. [Glicksberg et al. (2018)](#ch03.xhtml#ref3_3) compared AUC performance using different machine learning methods to phenotype Hepatorenal Syndrome. [Beaulieu-Jones and Greene (2016)](#ch03.xhtml#ref3_1) applied the embedding method to define the disease cohort, and employed denoising autoencoders to achieve the goal of phenotyping.
    
    Besides standard ML models, deep learning was also adopted for the purpose of phenotyping. The advantage of deep learning methods is that it does not require any feature selection and can learn the patterns inside a big EHR dataset with a large feature space and a large number of patients. [Lipton et al. (2015)](#ch03.xhtml#ref3_23) used Recurrent Neural Networks (RNNs) for multilabel classification of 128 diagnoses. [Lasko et al. (2013)](#ch03.xhtml#ref3_21) performed a deep learning method on dirty longitudinal clinical data using Gaussian process regression, producing the final phenotyping model with AUC of 0.97. More use cases and reviews of deep learning methods in EHR can be found in [Alzoubi et al. (2019)](#ch03.xhtml#ref3_9).
    
    In the unsupervised learning approach, the unlabeled data are clustered into different groups of patients with unknown medical conditions using Limestone (a technique of nonnegative tensor factorization technique) ([Ho et al. 2014](#ch03.xhtml#ref3_16)). The authors of this method then asked medical experts to review and validate the conditions of top groups of phenotype candidates as explained in their study.
    
3.  Hybrid Methods  
    One good advantage of machine learning and other statistical methods equipped with model selection techniques for phenotyping is that they are generalizable to many diseases. But the shortcoming is a lack of efficient validation of the classification results. Researchers often use the rule-based method as the gold standard for labeling and then build ML-based phenotyping models based on the labeled training dataset. [Li et al. (2013)](#ch03.xhtml#ref3_22) used labeled data derived from eMERGE definitions for T2DM patients and then trained the Apriori algorithm on the labeled data to develop a phenotyping algorithm called ARM (association rule mining). This algorithm is considered a hybrid approach (combining the rule-based methods with machine learning methods) and shows a better performance against the rule-based performance alone. Similarly, Carroll, [Yu et al. (2015)](#ch03.xhtml#ref3_32) used medical concepts from two public sites Medscape and Wikipedia as the gold standards to select features from EHR. The proposed features are filtered by keeping only the features mentioned in existing clinical notes of EHRs using the NLP. Eventually, the authors added ICD-9 codes and additional notes into the feature space to build the final logistic regression model.
    

**Table 3.2** Phenotyping Methods and Data Types

| **Method** || **Structured Data** || **Unstructured Data** |
| --- | --- | --- |
| Rule-based || ✓ ||  |
| --- | --- | --- |
| Machine learning ||  ||  |
| NLP ||  || ✓ |
| Machine learning || ✓ || ✓ |
| Deep learning || ✓ || ✓ |
| Unsupervised learning || ✓ || ✓ |
| Hybrid || ✓ || ✓ |

Whether the phenotyping is rule-based, machine learning-based or hybrid approach, the final identification of the disease diagnosis should be validated by clinical expert reviewers. For further automation to reduce the manual review process from medical experts, [Henderson et al. (2017)](#ch03.xhtml#ref3_15) developed PheKnow–Cloud that allows researchers to automate the validation process of the output phenotypes using unsupervised learning of medical literature. Electronic phenotyping is an emerging field and an essential step for EHR research. Therefore, in the upcoming years, it is expected to see many more phenotyping methods and tools beyond the ones discussed in this section.

If the targeted cohort is defined not only by a disease diagnosis, the inclusion/exclusion criteria may also involve other variables in the EHR database such as patient demographics (age, gender or race), medications, procedures, lab tests, clinical events, vital signs or microbiology tests, similar approaches for disease phenotyping can be employed. However, uncertainties and data errors (including missing data issues) need to be carefully considered. The literature in this is sparse and more future work on this topic is warranted.

## ![image](images/inline1_1.jpg)  
3.5 Data Extraction Report

Once a cohort of patients are identified and relevant data are then extracted from the EHR database, it is essential to generate summary statistics with tables, plots and figures. A summary report is an efficient way to facilitate collaboration and communication among research collaborators. For that reason, a summary report is highly recommended. Below we share with the readers a summary report template to highlight the main components that a report should include.

**Purpose of this report:**

Serve to provide an initial communication with clinical or epidemiological domain-specific experts to identify scientific questions or hypotheses

**Data extraction criteria:**

Clearly specify initial inclusion/exclusion criteria that were used to extract the data based on which this report is generated.

**Basic summary statistics:**

Tables and figures with detailed captions

1.  Disease types or sub-types: patient distributions and by calendar year
    
2.  Race distribution and disease prevalence distribution
    
3.  Gender distribution and disease prevalence distribution
    
4.  Age distribution and disease prevalence distribution
    
5.  Spatial region distributions and disease prevalence distributions:
    
    *   Number of patients
        
    *   Number of hospitals
        
6.  Hospital distribution
    
7.  Number of encounters: distribution per patient and by calendar year
    
8.  Time length of data intervals (from the first time of any event to the last time of any event for a patient): distribution per patient
    
9.  Mortality rate distributions
    
10.  The number of following counts and distributions by patients and by calendar year
     
     *   Disease diagnosis (distinct ICD-9 and/or ICD-10 codes): comorbidity distributions
         
     *   Medications
         
     *   Procedures
         
     *   Surgical procedures
         
     *   Clinical events
         
     *   Lab tests
         
     *   Microbiology tests
         
11.  Patient type description distribution (inpatient or outpatient) and by calendar year
     

**Project-Specific summary statistics:**

Example 1: All SAH project—summary statistics for the following items

1.  CT-scan test
    
2.  Clipping and coiling treatments
    
3.  Vasopressor treatments
    
4.  Complications
    
    *   Cerebral Vasospasm (CV)
        
    *   Delayed cerebral ischemia (DCI)
        

Example 2: Diabetes

1.  Glucose level
    
2.  HbA1c level
    

**Research Plan:**

*   • Potential scientific questions or hypotheses if any
    
*   • Plan for next step
    

## ![image](images/inline1_1.jpg)  
3.6 Illustration Example: Subarachnoid Hemorrhage (SAH) Project

### 3.6.1 EHR Database Design and Construction

Below we share our experience in designing and constructing a database system to host and manage Cerner EHR data. Although most healthcare database systems, including the Cerner EHR system, are based on Oracle or Microsoft SQL server, one can choose any existing database tools to build your database management system. We employed PostgreSQL, an object-relational database system that is free and open-source with the features of traditional proprietary database systems \[distributed under a license similar to BSD and MIT\]. The installation binary can be downloaded from [https://www.postgresql.org/download/](https://www.postgresql.org) for the operating system of your choice.

Here are the steps needed to construct a database system to manage and query healthcare data:

*   Setup database: You can use a Docker container to deploy PostgreSQL. Containerization is popular because containers are flexible, lightweight, portable, scalable and secure.
    
*   Create schema and tables: EHR/EMR vendors may provide DB schema in SQL files to build the definitions of tables. However, you may need to make a few changes to the statements to match your choice of DBMS. For example, Cerner EHR system uses Oracle, if you use PostgreSQL, then you need to replace NUMERIC(P,S) with DECIMAL(P,S).
    
*   Upload data files: Once the SQL files are prepared, you can run them from a client tool such as, pgAdmin or DataGrip. The client tool can also be used to load csv files to the database table. However, if the csv file is very large or when there are many large csv files waiting for import, creating a batch script to do the job will be more efficient.
    
*   Query the database: When a database query is executed, a procedure usually fetches all the records from the server process and then transfers them to the client process. If the query returns a huge amount of data, a proportionally large amount of memory will be allocated by the client. If the dataset is too large to be practically handled on the client-side, it is possible to create a server-side procedure. This will make it possible to transfer only a controlled amount of data to the client, so that a large dataset can be examined without keeping it entirely in memory.
    

### 3.6.2 SAH Cohort Identification and Data Extraction

To illustrate the process of cohort identification and data extraction from an EHR database, we share the following example from our project, subarachnoid hemorrhage (SAH) treatment analysis and prediction.

Our cohort of patients with SAH was first defined using the traditional rule-based approach: all related pieces of data from the Cerner EHR database (i.e., patient encounters, diagnoses, medications, etc.) that are specific to one disease are obtained by identifying ICD-9/10 codes. We adopt two ways to get the ICD-9/10 codes: 1) keyword search in the diagnosis description; and 2) find corresponding ICD-9/10 codes online or from clinicians. Once we determined the ICD codes of SAH, then all information tables can be derived by utilizing the relationships between different identifiers and the ICD codes. For example, we can first extract all the encounters that contain those ICD codes of SAH. Then use the encounter IDs in the extracted encounters to extract all the tables with regard to medications, procedures, clinical events, lab procedures and so on.

Although some literature discussed and listed ICD codes for SAH, in order to extract as many relevant ICD codes as possible for our project, we conducted keyword searches against the diagnosis description in the EHR database. Eventually, 192 unique ICD-9/10 codes related to SAH are collected. The unique ICD codes are then categorized into six code groups based on causes, symptoms and characteristics. See [Table 3.3](#ch03.xhtml#table3_3) below.

**Table 3.3** Code Groups and Their Descriptions

| **ICD Codes** || **Description** |
| --- | --- |
| 800.X-804.X || Fracture of skull with subarachnoid, subdural, and extradural hemorrhage |
| --- | --- |
| 430/I60.X || Nontraumatic subarachnoid hemorrhage |
| P52.5/P10.3/772.2 || Baby-related subarachnoid hemorrhage |
| 852.0–852.2 || Subarachnoid hemorrhage following injury |
| S06.6X || Traumatic subarachnoid hemorrhage |
| I69.0X || Sequelae following nontraumatic subarachnoid hemorrhage |

After a discussion with clinicians, we classified ICD code group “800.X–804.X” and “852.0–852.2” as traumatic subarachnoid hemorrhage and deleted patients diagnosed with “P52.5/P10.3/772.2” because those codes are related to infants. So filtered ICD code groups and their descriptions are as follows (see [Table 3.4](#ch03.xhtml#table3_4)).

**Table 3.4** Combined ICD Code Groups and Their Descriptions

| **ICD Codes** || **Description** |
| --- | --- |
| 800.X-804.X/S06.6X/852.0–852.2 || Traumatic subarachnoid hemorrhage |
| --- | --- |
| 430/I60.X || Nontraumatic subarachnoid hemorrhage |
| I69.0X || Sequelae following nontraumatic subarachnoid hemorrhage |

However, traumatic SAH and nontraumatic SAH present different clinical symptoms and complications. To treat the two types of SAH as the same disease by doing subsequent analysis will generate biased results. We also are interested in patients who were admitted to hospitals with SAH, instead of sequelae following SAH. To further refine the cohort for analysis, we also dropped the patients with the sole diagnosis code of sequelae following nontraumatic subarachnoid hemorrhage. One problem showed up after checking the historical SAH diagnosis for individual patients. A specific patient may have different combinations of SAH ICD code groups listed in [Table 3.4](#ch03.xhtml#table3_4). Here historical SAH diagnosis means SAH diagnosis records presented in the patient’s historical encounters. See [Figure 3.1](#ch03.xhtml#fig3_1) for the number of patients falling into different combinations of SAH ICD code groups.

![Figure 3.1 Patient count for different combinations of SAH ICD code groups.](images/fig3_1.jpg)

**Figure 3.1**  
Patient count for different combinations of SAH ICD code groups.

From [Figure 3.1](#ch03.xhtml#fig3_1) we can see that most patients had only one type of SAH diagnosis. But there are still a significant number of patients with both traumatic SAH diagnosis and nontraumatic SAH diagnosis or other combinations of SAH diagnosis codes. If the targeted cohort is just one type of SAH, can we simply drop the patients with over two types of SAH diagnosis? We believe that simply dropping patients from the analysis will introduce bias or produce misleading results for cohort studies. To better address this problem, we may consider using the first SAH encounter data for all patients. See [Figure 3.2](#ch03.xhtml#fig3_2) for the number of patients whose first SAH diagnosis fell into different combinations of SAH ICD code groups.

![Figure 3.2 Patient count for different combinations of SAH ICD code groups for the first encounter of a patient.](images/fig3_2.jpg)

**Figure 3.2**  
Patient count for different combinations of SAH ICD code groups for the first encounter of a patient.

In this SAH project, we finally restricted our analysis of patients whose first SAH diagnosis was nontraumatic SAH. We treated patients with both a diagnosis code group of sequelae following nontraumatic SAH and a diagnosis code group of nontraumatic SAH as nontraumatic SAH patients. In this project, we also focused on adult SAH patients (>17 years old) and patients’ age was used to define the cohort. Finally, we obtained our initial cohort with a sample size of 29,889 nontraumatic SAH adult patients.

We extracted the data for adult patients who had at least one SAH diagnosis in the record, which was crude, since a patient with one SAH code in his/her medical record may not be a confirmed SAH patient. A gold standard for a confirmed SAH diagnosis is to review CT scan data that we were not able to access. Thus, it is possible that this initial cohort may contain patients who were not confirmed SAH patients or even those who were not adults (17 years or younger) due to errors. A formal phenotyping approach described in [Section 3.4.2](#ch03.xhtml#sec3_004_002) above can be used to further refine the cohort. In order to do this, a training dataset needs to be available. As we discussed above, first a rule-based algorithm can be developed by collaborations with clinicians and SAH experts so that a training dataset can be established. Then a machine learning approach can be employed to confirm all the patients in the cohort.

### 3.6.3 Data Extraction Report

We can automate the generation of data extraction reports (see Section 3.5 above), which will make it reproducible. Examples of programming tools that one can use to write reproducible reports include R Markdown and Python Jupyter notebook. Below we share our own experience in producing the summary statistics report automatically.

The first step is to install nbconvert package and related environment settings under your operation system. You can refer to [https://nbconvert.readthedocs.io/en/latest/](https://nbconvert.74readthedocs.io) for more details. In order to make the figures and tables displayed nicely in the report, you can copy the following codes into the Jupyter notebook cell.

![image](images/inline3_1.jpg)

Once you finish the coding and get the outputs, you can input “jupyter nbconvert –to pdf –no-input ‘ipynb file location’” in the commend interface, like Anaconda Prompt or Server Bash. Since your collaborators might not be interested in the codes, set the configuration argument to “–no-input” is useful in hiding the codes from the report. Please make sure that your nbconvert is most updated. You can update the package by typing “conda update nbconvert” in your Anaconda prompt or Server Bash. nbconvert has many other functions. It can help convert the Jupyter notebook into other formats, such as html, slides and etc. Also, it can convert the Jupyter notebook into a report template that you have developed. Language Jinja will be utilized to write the template. Readers could learn more from [https://www.datacamp.com/community/tutorials/jinja2-custom-export-templates-jupyter](https://www.datacamp.com).

### 3.6.4 Potential Data Extraction Pitfalls and Errors with Solutions

We have experienced some problems and encountered some errors while working on our SAH project. We share some of these experiences here.

Errors found in the EHR database: It is unavoidable to contain errors in any database. For example,

*   One encounter may map to multiple patient identifiers, which is clearly an error.
    
*   One patient identifier may have multiple races or genders due to errors.
    

Mistakes we made in the process of data extraction include:

*   When extracting the first encounter of SAH patients based on the admission time, the admission time of some encounters may be the same due to errors. The first encounter cannot be distinguished. Similarly, the time stamps for medications, lab tests or procedures may contain errors or possibly missing, we should be cautious to extract the data specified by time stamps.
    

### ![image](images/inline1_1.jpg)  
References

Beaulieu-Jones, Brett K., and Casey S., Greene. 2016. Semi-supervised learning of the electronic health record for phenotype stratification. *Journal of Biomedical Informatics* **64**, 168–178. [https://doi.org/10.1016/j.jbi.2016.10.007](https://doi.org/10.1016/j.jbi.2016.10.007).

Chang, Fay, Jeffrey, Dean, Sanjay, Ghemawat, Wilson C., Hsieh, Deborah A., Wallach, Mike, Burrows, Tushar, Chandra, Andrew, Fikes, and Robert E., Gruber. 2008. “ *Bigtable: A distributed storage system for structured data.*” *ACM Transactions on Computer Systems (TOCS)* 26(2), 1–26.

Glicksberg, Benjamin S., Riccardo, Miotto, Kipp W., Johnson, Khader, Shameer, Li, Li, Rong, Chen, and Joel T., Dudley. 2018. Automated disease cohort selection using word embeddings from electronic health records. *Pacific Symposium on Biocomputing* **23**, 145–156. [https://doi.org/10.1142/9789813235533\_0014](https://doi.org/10.1142/9789813235533_0014).

Gray, Jim. 1996. Data management: Past, present, and future. *IEEE Computer* **29**((10)), 38.

Groves, Peter, Basel, Kayyali, David, Knott, and Steve Van, Kuiken. 2013. “ *The ‘big data revolution in healthcare*.” 2(8), 1–13.

Hubbard, Rebecca A., Jing, Huang, Joanna, Harton, Arman, Oganisian, Grace, Choi, Levon, Utidjian, Ihuoma, Eneli, L., Charles Bailey, and Yong, Chen. A Bayesian latent class approach for EHR-based phenotyping.” *Statistics in Medicine* **38**((1)), 74–87. [https://doi.org/10.1002/sim.7953](https://doi.org/10.1002/sim.7953).

Tate, Coray, and Paul, Warburton. 2019. “ *U.S. hospital EMR market share 2019.*” [https://klasresearch.com/report/us-hospital-emr-market-share-2019/1454](https://klasresearch.com).

Alzoubi, H., R., Alzubi, N., Ramzan, D., West, T., Al-Hadhrami, and M. A., Alazab. 2019. Review of automatic phenotyping approaches using electronic health records. *Electronics* **8**, 1235.

Carroll, R. J., A. E., Eyler, and J. C., Denny. 2011. Na¨‡‡‡‡‡‡ıve electronic health record phenotype identification for rheumatoid arthritis. *Proceedings of AMIA Annual Symposium* **2011**, 189–196.

Denny, J. C., D. C., Crawford, M. D., Ritchie, S. J., Bielinski, M. A., Basford, *et al* 2011. Variants near FOXE1 are associated with hypothyroidism and other thyroid conditions: using electronic medical records for genome- and phenome-wide studies. *American Journal of Human Genetics* **89**((4)), 529–542.

Denny, J., L., Bastarache, M., Ritchie, *et al* 2013. Systematic comparison of phenome-wide association study of electronic medical record data and genome-wide association study data. *Nature Biotechnology* **31**((12)), 1102–1111. [https://doi.org/10.1038/nbt.2749](https://doi.org/10.1038/nbt.2749).

Freimer, N., and C., Sabatti. 2003. The human phenome project. *Nature Genetics* **34**((1)), 15–21.

 Gottesman, O., H., Kuivaniemi, G., Tromp, W. A., Faucett, R., Li, *et al* 2013. The electronic medical records and genomics (eMERGE) network: past, present, and future. *Genetics in Medicine* **15**((10)), 761–771.

Henderson, J., R., Bridges, J. C., Ho, B. C., Wallace, and J., Ghosh. 2017. PheKnow-cloud: a tool for evaluating high-throughput phenotype candidates using online medical literature. *Proceedings of AMIA Joint Summits on Translational Science* **2017**, 149–157.

Ho, J. C., J., Ghosh, S. R., Steinhubl, W. F., Stewart, J. C., Denny, *et al* 2014. ” Limestone: high-throughput candidate phenotype generation via tensor factorization. *The Journal of Biomedical Informatics* **52**, 199–211.

Xu, H., Stenner, S. P., Doan, S., Johnson, K. B., Waitman, L. R., & Denny, J. C. (2010). MedEx: a medication information extraction system for clinical narratives. *Journal of the American Medical Informatics Association*, [**17**, 19–24](http://doi.org/10.1197/jamia.m3378) .

Huang, Y., P. J., McCullagh, and N. D., Black. 2004. *Feature selection via supervised model construction*. In: *Proceedings of the IEEE International Conference On Data Mining, 4th*, Brighton, U.K., 1–4 November, ed. and R. Rastogi, K. Morik, M. Bramer, X. Wu, pp. 411–414. New York: IEEE.

Kho, A. N., M. G., Hayes, L., Rasmussen-Torvik, J. A., Pacheco, W. K., Thompson, *et al* 2012. Use of diverse electronic medical record systems to identify genetic risk for type 2 diabetes within a genome-wide association study. *Journal of the American Medical Informatics Association* **19**((2)), 212–218.

Kirby, J. C., P., Speltz, L. V., Rasmussen, M. Basford, O., Gottesman, *et al* 2016. PheKB: A catalog and workflow for creating electronic phenotype algorithms for transportability. *Journal of the American Medical Informatics Association* **23**((6)), 1046–1052.

Lasko, T. A., J. C., Denny, and M. A., Levy. 2013. Computational phenotype discovery using unsupervised feature learning over noisy, sparse, and irregular clinical data. *PLoS ONE* **8**, e66341.

Li, D., G., Simon, C. G., Chute, and J., Pathak. 2013. Using association rule mining for phenotype extraction from electronic health records. *Proceedings of AMIA Joint Summits on Translational Science* **2013**, 142–146.

Lipton, Z. C., D. C., Kale, C., Elkan, and R., Wetzel. 2015. Learning to diagnose with LSTM recurrent neural networks. arXiv 2015, arXiv:1511.03677.

Martin-Sanchez, F., and K., Verspoor. 2014. Big data in medicine is driving big changes. *Yearbook of Medical Informatics* **9**, 14–20.

OHNLP (Open Health Nat. Lang. Process. Consort.). *Main Page. User Guide, updated* Nov. 18, 2013. [http://ohnlp.org/](http://ohnlp.org).

Pacheco, J. A., and W., Thompson. 2011. Type 2 diabetes mellitus. Type 2 diabetes mellitus electronic medical record case and control selection algorithms (from Northwestern University) PheKB website. *Vanderbilt University*, **2011**.

Petersen, L. A., S., Wright, S. L., Normand, and J., Daley. 1999. Positive predictive value of the diagnosis of acute myocardial infarction in an administrative database. *Journal of General Internal Medicine* **14**((9)), 555–558.

Richesson, R. L., M. M., Horvath, and S. A., Rusincovitch. 2014. Clinical research informatics and electronic health record data. *Yearbook of Medical Informatics* **9**, 215–223.

Ritchie, M. D., J. C., Denny, D. C., Crawford, A. H., Ramirez, J. B., Weiner, *et al* 2010.  Robust replication of genotype-phenotype associations across multiple diseases in an electronic medical record. *American Journal of Human Genetics.* **86**((4)), 560–572.

Soysal, E., J., Wang, M., Jiang, Y., Wu, S. V., Pakhomov, H., Liu, and H., Xu. 2017. CLAMP – a toolkit for efficiently building customized clinical natural language processing pipelines. *Journal of the American Medical Informatics Association* **25**, 331–336.

Xu, Hua, Shane, Stenner, Son, Doan, Kevin, Johnson, Lemuel, Waitman, and Joshua, Denny. 2010. MedEx: A medication information extraction system for clinical narratives. *Journal of the American Medical Informatics Association: JAMIA* 19–24. [10.1197/jamia.M3378](http://dx.doi.org/10.1197/jamia.M3378).

Yu, S., K. P., Liao, S. Y., Shaw, V. S., Gainer, S. E., Churchill, *et al* 2015. Toward high-throughput phenotyping: Unbiased automated feature extraction and selection from knowledge sources. *Journal of the American Medical Informatics Association* **22**((5)), 993–1000.

# [4 ](#contents.xhtml#toc1_67)  
![image](images/inline1_1.jpg)

# [EHR Data Cleaning](#contents.xhtml)  
               

Yashar Han Yuefan Vahed TalebiFengHuangMaroufy

## ![image](images/inline1_1.jpg)  
4.1 Introduction

Data cleaning (also called data *cleansing* or *scrubbing*) is the process of detecting and fixing errors and inconsistencies in datasets to reduce heterogeneity and increase the quality of data. It is the second step, following data extraction, in the process of preparing data for statistical analysis and/or model building. Despite being labor-intensive and time-consuming, data cleaning is extremely important for any modeling and analysis based on EHR databases. However, it is sometimes overlooked by researchers, and in such cases, the inconsistencies and errors may have significant influence on the precision and accuracy of the results.

Cleaning EHR data is different from other cleaning methods for big data and small data studies. Unlike big data analysis based on EHR databases, in a traditional clinical research setting, such as experimental studies and clinical trials, the data collection is controlled, hence data cleaning, if required, is not a tedious task. On the other hand, cleaning the data from other big data management systems may not be as sensitive as EHR big data cleaning. For example, a movie recommendation algorithm (such as the algorithms used by online streaming services) has more flexibility to include or exclude outliers. The worst-case scenario for these algorithms is to recommend an unfavorable movie title to a viewer. In contrast, in EHR data analysis, the researchers do not have such freedom to drop or change the data. Excluding possible (but not probable) values from clinical research data may lead to biased results and, as a result, alters clinical decision making in a potentially harmful way.

As mentioned in the introduction chapter, until recent years, the use of EHR data as a source of scientific research has been overlooked, partly because the primary purpose of the EHR databases is not for research or clinical decision making. Instead, software developers optimize the database systems for legal and billing purposes with three main goals in mind: finances of health care management, user-friendliness for health care personnel, and usefulness to prepare legal documents. Moreover, since one database is used by hundreds of healthcare provider systems, the heterogeneity and the possibility of finding errors in the data are not negligible. Additionally, the Health Insurance Portability and Accountability Act (HIPAA law) requires the EHR data to be properly de-identified before making it available to researchers. This de-identification process makes detecting and fixing errors even more difficult. As a result, EHR data is not primarily research-friendly, making data cleaning and processing the most challenging steps in this type of research ([Nobles et al. 2015](#ch04.xhtml#ref4_1)).

In this chapter, we begin by reviewing existing methods and tools developed specifically for EHR data cleaning. We then list and discuss some common challenges and data cleaning issues in EHR databases and demonstrate methods on how to address them. Finally, we end the chapter with some general recommendations on data cleaning strategies tailored for EHR data.

The main goal of data cleaning is finding and correcting errors and reducing data heterogeneity. EHR includes a wide variety of data such that a single database can be used for multiple types of research. Therefore, it is helpful to develop a data cleaning procedure that is reproducible and, more importantly, repeatable for different datasets corresponding to different research projects. Developing generalized project-independent approaches for data cleaning can be expensive in terms of time and effort, but the payoff will be significant.

## ![image](images/inline1_1.jpg)  
4.2 Review of Current Data Cleaning Methods and Tools

There are many published papers and packages on EHR data cleaning, most of which focus on datasets from a single or a limited number of health care facilities. In addition, some are quite limited and address a single task in data cleaning, such as unifying the measurement unit of some lab results. Also, we should emphasize that there is a narrow margin between data cleaning and data preparation. Some existing tools presented as data cleaning tools are in fact data preparation tools. For example, *IntelliClean* uses a knowledge-based system to create a measure of similarity between two records and merge them if their similarity is more than a predefined threshold ([Lee et al. 2000](#ch04.xhtml#ref4_2)). This approach is quite challenging when applied to a big EHR database as it is highly sensitive to the selected threshold. *IntelliClean* might be more reliable if applied in a project-specific manner to a narrower cohort and make use of domain knowledge. In this chapter, however, we address general data cleaning which can be applied to an entire database regardless of the goal and purpose of the process and the cohort of interest. The existing data cleaning tools can be divided into two main categories: general data wranglers, and data cleaning tools for specific EHR datasets.

### 4.2.1 Data Wranglers

These tools usually are the product of research groups working on data cleaning. One of the earliest examples of data wranglers is the “DataWrangler” originally developed by Stanford Visualization Group, then published by the Stanford/Berkeley Wrangler research project ([Kandel et al. 2011](#ch04.xhtml#ref4_3)). The free version of the tool was completed in 2012 and a commercialized version of the tool, called Trifacta data wrangler ([Wrangler Editions 2019](#ch04.xhtml#ref4_4)), was developed later.

Another example is Potter’s wheel, developed by UC Berkley ([Apers et al. 2001](#ch04.xhtml#ref4_5)). This tool has a Graphical User Interface, which minimizes coding and makes data manipulation easier for users without professional computational skills. This tool has a spreadsheet-like interface in which the user can define different types of transformations and then create a pipeline of these transformations. Potter’s wheel was optimized for working with large datasets. The fast visualization (even before loading the entire data), some type of data quality metric and automatic discrepancy detection, are the main features of this tool ([Apers et al. 2001](#ch04.xhtml#ref4_5)).

There are other data wrangler tools that are both commercially and publicly available, each with their own strengths and weaknesses ([Adu-ManuSarpong et al. 2013](#ch04.xhtml#ref4_6)). These tools were developed to handle a wide variety of different data types. Their main function is to reformat or transform the data. This kind of procedure is especially helpful in handling date/time fields and geolocation information. Both of these types of data can have a different or complex format and transforming them into a more uniform and convenient format is important. Furthermore, some tools offer data extraction functions as well. Detecting patterns and regular expressions and reformatting is another field that these tools are tailored to handle. Some more developed (and usually paid) tools can help in dealing with missing value issues and even clean the data by dropping outliers. Another strong property of these tools is their ability to handle and visualize the big size of data rapidly with their well written and optimized codes.

Although the generalizability of these tools is one of their main selling points, it is also their main drawback. Although working with EHR data has its own complexity, and wrangler tools would leave some inconsistencies in the data, it is still required to be dealt with specifically. Hence, data cleaning tools developed specifically for EHR data may be a better choice in most scenarios.

### 4.2.2 Data Cleaning Tools for Specific EHR Datasets

EHR database systems may have different designs and implementations. They may use different data dictionaries and their schema, as a relational database, can be different from one to another. For example, one database may use the World Health Organization ICD-10 code list with around 14,000 different codes and another may use the ICD-10-CM code list with more than 70,000 entries. Date may be entered in European style (dd/mm/yyyy) or USA format (mm/dd/yyyy). Different countries have different formats for their postal addresses; therefore, geolocation data can be another challenging task for data cleaning teams. Because of these discrepancies among EHR database systems, data cleaning tools are usually developed to perform on specific EHR database systems and may not be applied directly to other databases. However, a study for the methods and experience of research groups and their tools will always be beneficial and informative to researchers developing their own data cleaning tools.

One example of this type is “rEHR” package, developed by UK researchers using “r” statistical software. The UK has developed a near-universal deployment of EHRs in general practice performed by general practitioners for over 20 years ([Springate et al. 2017](#ch04.xhtml#ref4_7)). The following databases were used to create this universal EHR database:

*   The Clinical Practice Research Datalink (CPRD, previously known as the General Practice Research Database, GPRD)
    
*   The Health Improvement Network (THIN)
    
*   QResearch
    
*   The Doctors’ Independent Network (DIN-LINK)
    
*   Research One
    

This database is completely de-identified and made available for research ([Springate et al. 2017](#ch04.xhtml#ref4_7)).

rEHR package is a wrapper of SQL queries to interact with the underlying database easily and rapidly with some additional features. It can extract data from the database and convert the longitudinal data to a cohort dataset suitable for survival analysis. rEHR can create data that have matched control and case groups and can cut cohort data by time-varying covariates. An additional feature is the code’s ability to unify the measurement unit for HbA1c.

There are also some statistical methods for data cleaning in literature. For example, algorithms have been developed to detect and clean inaccurate adult height using median height during different stages of a patient’s life ([Muthalagu et al. 2014](#ch04.xhtml#ref4_8)). This approach is simple and easy to implement but drops surprising and dramatic information points from the patient’s history. For example, we neither expect a negative change in the patient’s height, nor a significant height gain after adolescence. However, we should keep in mind that, although with extremely small probability, there are exceptions to the above assumptions. For instance, if the patient undergoes a bilateral lower limb amputation surgery, the change in height will be negative, on the other hand, if the patient undergoes a spinal reconstructive surgery, he/she may gain height even after becoming an adult ([Spencer et al. 2014](#ch04.xhtml#ref4_9)). These situations are rare but, depending on the type of study and target population, ignoring them during the data cleaning process may remove some critical data points and add bias to the study.

### 4.2.3 Data Quality Assessment

One of the first challenges an investigator faces is if the available data is suitable and good enough for conducting the study of interest. The answer to this question is critical and the result usually becomes apparent during the initial steps of the data cleaning process. For example, we may be interested in studying a rare infectious disease using a Multi-central EHR database system. Initially, we may find that the database has enough records and subjects to conduct the study. However, in later data inspections, we may realize that majority of the records have been recorded improperly, and it includes an extremely high rate of missing data. These findings may force the research group to drop some blocks of records from the study which eventually may result in a significant decrease in the number of subjects available to continue the study. Kahn et al. proposed data quality metrics to assess the appropriateness of the available data ([Kahn et al. 2012](#ch04.xhtml#ref4_10)). They divided these metrics into five different categories:

1.  **Attribute domain constraints:** This metric measures the basic summary statistics of each of the desired attributes and assesses the distributions. If the clinical knowledge proposes a certain distribution with a definitive possible range of values for that attribute, we can estimate the level of error in the database for that specific attribute. For example, pulse oximetry values are usually above 95% and we know the possible range of values is from 0% to 100%. So if we find a large number of negative or more than 100% values for these attributes it can be indicative of poor data quality (high number of errors) ([Elder et al. 2015](#ch04.xhtml#ref4_11)).
    
2.  **Relational integrity rules:** This metric deals with the structure of the database from which we have extracted our data. For example, if we discover that the primary key for each patient (which is called Patient\_sk \[super\_key\] in Cerner) is not unique for some patients, we can conclude that the database has a structural problem, and a higher ratio of this discrepancy reveals a lower quality of the data.
    
3.  **Historical data rules:** This metric evaluates the quality of the time-varying attributes, such as the use of the same format for different time points.
    
4.  **State-dependent rules:** This metric assesses if the changes in the lifecycle of an object follow expected transitions. For example, if a patient is flagged as expired at one-time point, we shouldn’t have any records at later time points regarding his/her state of the living. An example is the measurement of blood pressure, recorded after the reported time of death. However, we should keep in mind that some results may become available and recorded in the database even after such occurrences such as toxicology reports.
    
5.  **Attribute dependency rules:** This metric measures the quality of dependent attributes. For example, if we observe pregnancy diagnosis for a patient with multiple male gender records in different encounters, we may question the quality of the data ([Kahn et al. 2012](#ch04.xhtml#ref4_10)).
    

This type of data quality assessment can guide us in addressing the following questions:

*   Is this specific research feasible using the available dataset?
    
*   How difficult and tedious will the data cleaning process be?
    
*   What areas should the data cleaning team prioritize?
    

Some studies used this framework to evaluate the data quality and clean their data mainly by dropping some of the records or attributes ([Dziadkowiec et al. 2016](#ch04.xhtml#ref4_12)), which although easy and straightforward, produced biases in the final results.

## ![image](images/inline1_1.jpg)  
4.3 Common EHR Data Errors and Fixing Methods

In this section, we provide a brief review of possible errors and inconsistencies in EHR databases with some examples. In each case, we describe methods for reducing the inconsistencies and resolving the issues.

Most EHR databases have tables to store information about patients’ encounters, lab results, clinical events, diagnoses, medications, procedures, and surgical procedures. Among all of the information, only the encounter (which includes demographic variables), lab results, and clinical events (include vital signs) tables have quantitative results, hence they will be the focus of our data cleaning tool. However, the remaining tables, which mostly include records as diagnosis codes (e.g., ICD-9, ICD10), medication codes/names (e.g., NDC, generic names), procedure codes (e.g., CPT), are not free of issues. We also address those problems and provide simple procedures to deal with them. Furthermore, we will use examples from SAH and AIDS cohort projects based on the Cerner database (as mentioned in [Chapter 2](#ch02.xhtml#chapter2)). Since we address general data errors that are not data/project-specific, the same methods (with some modifications) can be used for other databases. Finally, we describe our novel semi-automatic tool for dealing with major errors and inconsistencies in an EHR database.

### 4.3.1 List of Common Errors in an EHR Database

*   Demographics Table
    
    *   Inconsistent gender.
        
    *   Inconsistent ethnicity.
        
    *   Non-unique patient key field.
        
    *   Errors in recorded age.
        
*   Lab Table
    
    *   Multiple units of measurement for the same lab.
        
    *   Multiple date/time for a single record.
        
    *   Some units of measurement are impossible.
        
    *   Out of range errors.
        
    *   Assigning the wrong Lab ID.
        
*   Clinical Events
    
    *   Overlap with Lab Table.
        
    *   Multiple clinical event codes for the same feature.
        
    *   The same group of measurements has different time points.
        
    *   Assigning the wrong clinical event ID.
        
*   Medication, Diagnosis, Procedure Tables
    
    *   Multiple formats for the same medication.
        
    *   Too many categories for diagnosis codes.
        
    *   Multiple types of codes for procedures.
        

### 4.3.2 Demographics Table

Addressing concerns with the Demographic table is especially important because any data quality assessment is heavily dependent on this table. Furthermore, the demographics table is important in tracking down the errors and culprits of data cleaning in other tables.

#### Multiple Race and Gender

One of the issues that can be encountered is the inconsistency in the patient’s race and/or gender. This error is one of the commonly found errors in any EHR database. After the initial cleaning, the rates of gender and race inconsistencies are 0.3% and 22%, respectively, in the HIV-Cancer cohort. Besides mistakes made during data entry, we believe that the misreporting of transgender (estimated around 0.3% of the entire population in USA ([Gates 2011](#ch04.xhtml#ref4_13))) and multiracial patients (estimated around 6.9% in USA ([Parker et al. 2019](#ch04.xhtml#ref4_14))) could lead to these inconsistencies.

To understand the origin of the inconsistency, it is helpful to describe how the patient’s race and gender are recorded in the database. As presented in [Figure 4.1](#ch04.xhtml#fig4_1), each patient has a unique Patient SK in our database (it should be unique but as we will discuss later there are some errors in this part). Each Patient SK has one or more associated Patient IDs and each Patient ID has one or more Encounter IDs. Patient’s gender and race are recorded as a feature of Patient ID. There may be more than one Patient ID for the same Patient SK. If the person demographics change with a new encounter, a new record is added to the Patient Table which includes a new Patient ID. Although rare, the same “person” may have different records for race/gender over time across encounters. Typically, when this occurs it is due to a blank or unknown value in one record and this field will be filled out in another patient record.

![Figure 4.1 The structure of the example EHR database for patient SK, patient ID, and encounter ID.](images/fig4_1.jpg)

**Figure 4.1**  
The structure of the example EHR database for patient SK, patient ID, and encounter ID.

Our approach for fixing this error is:

1.  For each Patient SK, we select all the Patient IDs.
    
2.  We drop all of the NULL/null/Not Mapped values.
    
3.  If the patient has more than one value for gender or race, we get the majority vote for gender and race and set it as the correct patient gender and race.
    
4.  If the majority vote is inconclusive (i.e., an equal number for each category of gender/race) we select the first recorded gender and race as the correct patient’s gender and race.
    

#### Multiple Patient Keys for the Same Encounter ID

Another error that we may find is that multiple Patient SKs are linked to a single Encounter ID (it should be the other way around). If the ratio of this kind of error is high in any database, the database structure is unreliable and it will result in a significant reduction of the data quality. This type of error should be fixed before any further analysis/data cleaning. In our case study since we faced this error at only a 0.02% rate, we simply dropped them from our database.

#### Multiple Calculated Birth Date

In this example database, the patient age for each encounter is saved in multiple fields:

1.  Age in years
    
2.  Age in months
    
3.  Age in weeks
    
4.  Age in days
    
5.  Age in hours
    

In our case study we encountered three different scenarios for each recorded age ([Figure 4.2](#ch04.xhtml#fig4_2)):

*   First Scenario: All of the fields are blank (missing age)
    
*   Second Scenario: Only the *age in years* fields are populated (age in years)
    
*   Third Scenario: All of the age fields are populated (age in year/month/day)
    

![Figure 4.2 Different cases for selecting the birth date.](images/fig4_2.jpg)

**Figure 4.2**  
Different cases for selecting the birth date.

Each patient may have multiple encounters. By using the date of admission for that encounter and age from either first or second scenario we can calculate exact or approximate birthdate respectively.

If we get multiple exact or approximate birthdate for a single patient, we use the following procedure to decide which one is the potential correct birth date:

*   Case 1: If all of the patient ages are compatible with the first scenario, the patient’s birth date is missing.
    
*   Case 2: If all of the patient ages are compatible with the second scenario, the patient’s birth date is decided by majority vote (Case 2a) or first recorded age (Case 2b), similar to the patient’s gender/race approach.
    
*   Case 3: If a patient has one (Case 3a) or more than one (Case 3b) estimated birth date compatible with the third scenario, the patient’s birth date is calculated using the first recorded birth date.
    

### 4.3.3 Lab Table

As mentioned earlier, big EHR databases are used by multiple health care facilities (e.g., hospitals and clinics) each of which may use different kits or equipment to evaluate a lab measurement (e.g., serum potassium level). Some equipment may have different normal reference ranges for the same lab measurement, and it is possible that the EHR system provider allowed each entity to use a customized data entry structure. These two factors led to the use of multiple formats to report the same lab measurement. In our example database, the *Procedure ID* column includes the numeric code for a lab procedure. The results are recorded according to the numeric *Result Type ID* field and may be stored using different formats (e.g., alphanumeric, numeric, text, etc.). For example, [Table 4.1](#ch04.xhtml#table4_1) shows the different formats used in our example database to report serum potassium level (encoded as Procedure ID&#160;=&#160;24), with multiple *Result Type IDs* for the same *Procedure ID* (namely 1, 7, 9, 12). Furthermore, each *Result Type ID* has another sub-level that consists of different units; hence, the serum potassium level was reported using 18 different formats, in one of the datasets.

**Table 4.1** Different Report Formats for Serum Potassium Level in the Example Database

| **No.** || **Procedure ID** || **Procedure Name** || **Result Type ID** || **Result Type Description** || **Normal Range Low** || **Normal Range High** || **Unit** || **Unit Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 24 || Potassium, Serum || 1 || Alpha || 3.5 || 5.1 ||  ||  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || 24 || Potassium, Serum || 1 || Alpha || 3.5 || 5 || meq/L || Milliequivalents per Liter |
| 3 || 24 || Potassium, Serum || 1 || Alpha || 3.5 || 5.6 || mmol/L || Millimoles per Liter |
| 4 || 24 || Potassium, Serum || 1 || Alpha || 3.8 || 4.8 || Not Mapped || Not Mapped |
| 5 || 24 || Potassium, Serum || 7 || Numeric ||  ||  ||  ||  |
| 6 || 24 || Potassium, Serum || 7 || Numeric || 3.5 || 5 || meq/dL || Milliequivalents per Deciliter |
| 7 || 24 || Potassium, Serum || 7 || Numeric || 3.8 || 5.5 || meq/L || Milliequivalents per Liter |
| 8 || 24 || Potassium, Serum || 7 || Numeric || 1 || 3 || min || Minute |
| 9 || 24 || Potassium, Serum || 7 || Numeric || 3.5 || 5.3 || mm/L || Millimeters per Liter |
| 10 || 24 || Potassium, Serum || 7 || Numeric ||  ||  || mmol/L || Millimoles per Liter |
| 11 || 24 || Potassium, Serum || 7 || Numeric || 3.8 || 4.8 || Not Mapped || Not Mapped |
| 12 || 24 || Potassium, Serum || 9 || Text ||  ||  ||  ||  |
| 13 || 24 || Potassium, Serum || 9 || Text || 0 || 0 || meq/L || Milliequivalents per Liter |
| 14 || 24 || Potassium, Serum || 9 || Text || 3.5 || 5.1 || mmol/L || Millimoles per Liter |
| 15 || 24 || Potassium, Serum || 9 || Text ||  ||  || ng/mL || Nanograms per Milliliter |
| 16 || 24 || Potassium, Serum || 12 ||  ||  ||  ||  ||  |
| 17 || 24 || Potassium, Serum || 12 ||  || 3.6 || 5 || meq/L || Milliequivalents per Liter |
| 18 || 24 || Potassium, Serum || 12 ||  || 3.5 || 5.1 || mmol/L || Millimoles per Liter |

Another major issue with EHR data is inconsistency during data entry, which is also a significant cause for assigning different formats to similar fields. For example, the short description for “Millimeter per liter” in our example is “mm/L” ([Table 4.1](#ch04.xhtml#table4_1), row 9). We noticed some electrolyte concentration levels reported as “Millimeter per liter” (instead of common Millimoles per liter, [Table 4.1](#ch04.xhtml#table4_1) rows 3, 10, 14, 18). After careful examination of the values and the distribution, we determined that the operator selected “mm/L” by mistake. In this case, we simply adjusted the unit of measurement.

Another common mistake in data entry is mixing and confusing the lab IDs for count versus percentage lab results. This issue is more common in White Blood Cells (WBC) measurement. For example, Our database has different lab ID codes for Lymphocyte Percentage (as a percentage of the whole number of WBC) and Lymphocyte count. Due to operator misunderstanding or unawareness, sometimes the percentage of the lymphocytes reported in the lymphocyte count and the unit of measurement is selected as a percentage. Instead of simply deleting these values (increases missing and bias), we developed a mapping table to map this type of results to their appropriate lab ID. More specifically, we have developed a conversion map to consolidate the data and make the reporting format uniform. The strategy is discussed in the next section.

#### Developing Conversion Map

In this section, we explain our strategy for developing the conversion map and its structure. Throughout, we use the serum potassium level for example. [Figure 4.3](#ch04.xhtml#fig4_3) shows the flow chart of the lab unit unification algorithm.

![Figure 4.3 Flow chart of the lab unit unification algorithm.](images/fig4_3.jpg)

**Figure 4.3**  
Flow chart of the lab unit unification algorithm.

[Table 4.2](#ch04.xhtml#table4_2) presents an example of the conversion map. The first four columns are directly selected form our dataset extracted from EHR databases (including ID and units for potassium level), the rest of the columns are added in which we describe our data cleaning strategy. The description of each of these columns are as follows:

**Table 4.2** A Section of the Conversion Map used for Unifying Serum Potassium Level

| **No.** || **Procedure ID** || **Result Type ID** || **Unit** || **Conversion Map ID** || **Convert to** || **Conversion Equation** || **Lower Limit** || **Upper Limit** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 24 || 1 ||  || 24\_1\_ || 24\_7\_ mmol/L || *x* || 1 || 10 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || 24 || 1 || meq/L || 24\_1\_meq/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 3 || 24 || 1 || mmol/L || 24\_1\_mmol/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 4 || 24 || 1 || Not Mapped || 24\_1\_Not Mapped || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 5 || 24 || 7 ||  || 24\_7\_ || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 6 || 24 || 7 || meq/dL || 24\_7\_meq/dL || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 7 || 24 || 7 || meq/L || 24\_7\_meq/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 8 || 24 || 7 || min || 24\_7\_min || 24\_7\_ mmol/L || *omit* || 1 || 10 |
| 9 || 24 || 7 || mm/L || 24\_7\_mm/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 10 || 24 || 7 || mmol/L || 24\_7\_mmol/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 11 || 24 || 7 || Not Mapped || 24\_7\_Not Mapped || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 12 || 24 || 9 ||  || 24\_9\_ || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 13 || 24 || 9 || meq/L || 24\_9\_meq/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 14 || 24 || 9 || mmol/L || 24\_9\_min || 24\_7\_ mmol/L || *omit* || 1 || 10 |
| 15 || 24 || 9 || ng/mL || 24\_9\_mmol/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 16 || 24 || 12 ||  || 24\_9\_ng/mL || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 17 || 24 || 12 || meq/L || 24\_12\_meq/L || 24\_7\_ mmol/L || *x* || 1 || 10 |
| 18 || 24 || 12 || mmol/L || 24\_12\_mmol/L || 24\_7\_ mmol/L || *x* || 1 || 10 |

##### *Conversion Map ID*

This column is a concatenation of “Procedure ID\_Result type ID\_Unit” sections of each format. This specific field has been developed for making simplifying the programming section of our tool and better interpretation of the results.

##### *Convert To*

This column shows the final format that the values will be converted to. The purpose of this field is to unify the data to the most frequent format used in the database for that specific lab result or a unit suitable for the specific lab result according to professional knowledge. For the serum potassium level example, we select *24\_7\_mmol/L* as our unified version.

##### *Conversion Equation*

The data in the Conversion\_equation field will be used to calculate the target value (a value compatible with convert\_to characteristics). The code will capture the formula from this field, and use it for mathematical calculations.

The strategy for creating the conversion equation for each lab is:

1.  Check the distribution, lower limit, and upper limit of the current format and compare it to the convert\_to format distribution, lower limit, and upper limit. If they look the same, the conversion\_ equation will be *x* (i.e., *f*(*x*) = *x* and no mathematical manipulation needed). One important rule for the conversion map is to use *x* as the variable (same as *x* in *f*(*x*)). If we want to do mathematical computation on the data, we can use a standard equation like:
    
    $\\left. f(x) = (((x - 4)/8)\*5x) \\right.\\hat{}2.$
    
    In this phase of developing the tool, we compare distributions manually. It is also possible to develop an automatic method to evaluate the difference between the distributions and if it is not significant put *x* in the convertion\_equation field.
    
2.  If the distributions are different, first we try to find a conversion\_ equation according to the literature. If we fail to find a reliable method, we seek guidance from clinicians.
    
3.  If we are unable to find a suitable map for a record, our tool leaves the record in the current format. For instance, when the Unit was not known (Not mapped, unknown, null, etc.) we face conversion\_map\_IDs like *24\_7\_Not Mapped* for which we could not determine the conversion equation.
    
4.  If a format looks completely wrong and did not look valid, the conversion\_equation is set to *omit*. The code will delete the value and consider it as missing.
    

##### *The Lower Limit and Upper Limit*

According to literature in medical science journals, for some lab results, there are ranges of possible values that are compatible with life; that is, values beyond these ranges are not normal or even possible in a living person. To include the extreme cases, we can set an even wider range than the values reported in the literature. Our tool first calculates the value according to conversion\_equation and then if the result is between upper and lower limits, it records the result; otherwise, it reports the value as missing. [Table 4.3](#ch04.xhtml#table4_3) shows the possible values of some labs according to literature ([Clot-Silla et al. 2011](#ch04.xhtml#ref4_15)) and our assumptive upper and lower limits. We should emphasize that this optional step is a part of data processing, but we include it in our data cleaning tool to promote faster and less computationally intense data processing.

**Table 4.3** Values Incompatible with Human Life for Some Labs and Range Used in Conversion\_Map

| **Lab (Plasma)**  || **Values Incompatible with Human Life or Impossible** ||  || **Conversion\_Map Range Limit** |
| --- | --- | --- | --- |
|  ||  || Lower || Upper |
| Chloride || <65 and > 138&#160;mmol/L || 60 || 140 |
| --- | --- | --- | --- |
| Ethanol || \>97.6&#160;mmol/L || 0 || 105 |
| pH || < 6.8 and >7.8 || 6 || 8 |
| Potassium || < 1.3 and >9.0&#160;mmol/L || 1 || 10 |
| Sodium || < 100 and >191&#160;mmol/L || 90 || 200 |
| FiO[2] || < 21 and >100% || 10 || 100 |
| SpO[2] || < 0 and > 100% || 0 || 100 |

#### Lab Date and Time

Often there are multiple time/date-stamps for some events, recording the event times from order to administration (or cancelation) of a medication, a procedure, or a lab procedure. For example, each record in the lab table may have one or several of the following seven date/time-stamps:

1.  Lab Drawn Date Time
    
2.  Lab Received Date Time
    
3.  Lab Performed Date Time
    
4.  Lab Completed Date Time
    
5.  Lab Verified Date Time
    
6.  Lab Ordered Date Time
    
7.  Lab Cancelled Date Time
    

For longitudinal analyses, we need a consistent time stamp for each recorded event. Some timestamps are clinically more reasonable to use, and none of the fields above have complete information (i.e., some of them have missing dates). Therefore, we can define the following strategy to provide a consistent time/date stamp for each event.

1.  If a date/time recorded as 01/01/1900 in the Lab Table it should be considered as missing date/time, and lab value with a valid date/time in the Lab Cancelled Date Time field is dropped from the records.
    
2.  The first valid date-time value will be selected out of the first six (according to the order 1–6 above) entries and recorded as the lab records time stamp.
    
3.  If the user provides two dates/times (e.g., admission and discharge time) as lower (*t*[0]) and upper (*t*[*e*]) limit for each patient encounter, the code will incorporate an extra validation step for selecting the correct timestamp. The details of the lab date time validation algorithm are presented in [Figure 4.4](#ch04.xhtml#fig4_4). Again, this optional process is a part of data processing and our tool is flexible to include/exclude this step in the data cleaning process.
    

![Figure 4.4 Flowchart of date/time validation algorithm; t0 and te are user-defined upper and lower limits for each patient encounter; optional steps have a dotted border.](images/fig4_4.jpg)

**Figure 4.4**  
Flowchart of date/time validation algorithm; *t*[*0*] and *t*[*e*] are user-defined upper and lower limits for each patient encounter; optional steps have a dotted border.

#### User Input Form and Report Generator

To facilitate the use of our data cleaning tool for scientists without professional programming skills we developed a user-friendly interface. [Figure 4.5](#ch04.xhtml#fig4_5) presents an example of the user interface.

![Figure 4.5 User input form for lab unit unifier.](images/fig4_5.jpg)

**Figure 4.5**  
User input form for lab unit unifier.

A study of descriptive statistics and basic graphic visualization of a dataset are primary steps to any statistical analysis for evaluating data quality and suggesting a suitable model for the data. However, based on our experience producing such a simple report can be extremely time-consuming even for researchers with a reasonable computational background. Therefore, we added a report generator function to our data cleaning tool to create an automatic generated report, although this step is optional and can be ignored. This tool can create a report in HTML, Microsoft Word, Acrobat pdf, or other formats. [Figure 4.6](#ch04.xhtml#fig4_6) is a screenshot of the first page from the example report generated by this tool.

![Figure 4.6 The first page of the result section of the report, generated by the tool.](images/fig4_6.jpg)

**Figure 4.6**  
The first page of the result section of the report, generated by the tool.

#### Output

Although each data cleaning team may have their own preferences, based on our experience we recommend following these strategies for organizing the output of the data cleaning report.

1.  Keep the unique identifiers in your output without any modifications, they are required to stay unchanged for merging data tables consistently.
    
2.  Do not drop any values unless you are 100% certain it is an error; for example, see the height data cleaning approach in [Section 4.2.2](#ch04.xhtml#sec4_002_002). Data cleaning should be a general procedure for EHR big data. The project-specific data modification is called data processing and it will be discussed in the next chapter.
    
3.  At each step of data cleaning or modification of algorithms, save your results and outputs in different files to keep track of different versions of the files. Based on our experience this is a useful strategy in the event of unfortunate mistakes in one part of the process.
    
4.  When you clean and process data for different teams or data analysis users, it will be helpful to flag any remaining issues in the data which could not be addressed using the data cleaning process to inform the analyst about the reliability of each record.
    

[Figure 4.7](#ch04.xhtml#fig4_7) presents an example of using flags for lab data. You may use other types of flags. The description of each flag presented in the figure follows:

*   Kept—there is a valid result and it has been unified and kept in the data.
    
*   Missing—the original data did not have a value.
    
*   Omitted—the field was wrong and dropped.
    
*   Out of range—the result was out of range of user-defined possible values and dropped.
    
*   Missing equation—there was no equation for this Conversion map ID in the conversion map. The Converted\_Result field will not have a value.
    
*   Canceled—the *lab Cancelled date/time* field has a valid date (i.e., the lab has been canceled). The Converted\_Result field will not have a value.
    

![Figure 4.7 Flowchart of populating the status column in the output file; optional steps have a dotted border.](images/fig4_7.jpg)

**Figure 4.7**  
Flowchart of populating the status column in the output file; optional steps have a dotted border.

The final result will be a more uniform distribution for the lab values. As an example, [Figure 4.8](#ch04.xhtml#fig4_8) shows the result of lab data cleaning on the D-dimer lab result. As you can see the range of lab results reduced dramatically and it looks more uniform.

![Figure 4.8 The result of lab data cleaning on D-dimer lab results. The top graph is the distribution of D-dimer for a cohort of patients before cleaning and the bottom graph is the distribution after data cleaning. Note the reduction of the range which has been achieved by removing impossible values and unifying the units.](images/fig4_8.jpg)

**Figure 4.8**  
The result of lab data cleaning on D-dimer lab results. The top graph is the distribution of D-dimer for a cohort of patients before cleaning and the bottom graph is the distribution after data cleaning. Note the reduction of the range which has been achieved by removing impossible values and unifying the units.

### 4.3.4 Clinical Event Table

The clinical event table, particularly the vital signs subgroup, has a similar structure as the lab table and all the steps of the data cleaning tool can be applied to it. However, there are other inconsistencies in this table, mostly project-specific that require clinical expertise, which we will discuss in this section.

#### Variable Combining

Since our example database is used by many health care facilities, there are often various extensions of a label or description used for the same event. We use a combination of statistical techniques and clinical expertise to deal with this issue, and propose combining codes describing the same events. For example, there are 46 distinct event code IDs for the Blood Gas test, some with very similar descriptions, e.g., Base Excess, Base Excess Arterial, Base Excess Venous. For a cohort of SAH patients, [Table 4.4](#ch04.xhtml#table4_4) gives the number of patients with each of the three result records and [Figure 4.9](#ch04.xhtml#fig4_9) shows that there is a small number of patients with two or all three of the records. In addition, [Figure 4.10](#ch04.xhtml#fig4_10) does not show a significant difference between the average values of the three record labels. Therefore, after confirming with expert clinicians we may decide to combine the three labels into one variable.

**Table 4.4** Summary of Three Test Components in the Blood Gas Test

| **Test** || **Number of Records** || **Number of Patients** |
| --- | --- | --- |
| Base Excess || 3029 || 310 |
| --- | --- | --- |
| Base Excess, Arterial || 7027 || 493 |
| Base Excess, Venous || 277 || 88 |

![Figure 4.9 Venn diagram for patients with records of Base Excess, Base Excess Arterial, and Base Excess Venous.](images/fig4_9.jpg)

**Figure 4.9**  
Venn diagram for patients with records of Base Excess, Base Excess Arterial, and Base Excess Venous.

![Figure 4.10 Box plot and histogram for the test result. (1) Base Excess, (2) Base Excess, Arterial, (3) Base Excess, Venous to one group Base Excess.](images/fig4_10.jpg)

**Figure 4.10**  
Box plot and histogram for the test result. (1) Base Excess, (2) Base Excess, Arterial, (3) Base Excess, Venous to one group Base Excess.

#### Information Recovery

Some clinical events produce multiple results at the same time with different descriptions and codes. However, not all results can be found in the database; some are missing. For example, the Blood Gas test produces multiple measurements (see [Figure 4.11](#ch04.xhtml#fig4_11)) including PO2 Arterial, pH Arterial, PCO2 Arterial, FiO2 Arterial, and CO2, but not all are recorded every time the test has been conducted.

![Figure 4.11 The calendar plot for a selected patient; each grayscale block means the patient has this specific measurement at the given time.](images/fig4_11.jpg)

**Figure 4.11**  
The calendar plot for a selected patient; each grayscale block means the patient has this specific measurement at the given time.

This issue can be categorized as a “missing” problem in EHR data which can potentially be handled using simple imputation methods when there is a strong correlation among records. The details of how to face this kind of problem will be presented in [Chapter 6](#ch06.xhtml#chapter6).

##### *A Case Study*

The Braden scale, used for predicting pressure ulcer risk, is composed of six categorical results: sensory perception, skin moisture, activity, mobility, friction and shear, and nutrition. Friction and shear are rated on a scale of 1 to 3, and all other categories are rated on a scale of 1 to 4 (see [Table 4.5](#ch04.xhtml#table4_5)), where higher scores represent a lower risk of developing the ulcer. Potentially all six records should be available for each patient at each measurement time point. However, the majority of patients have a total score for pressure risk or a combination of other records. As the only suitable solution available, here we decide to aggregate all the available records to recover the total pressure record for all the patients.

**Table 4.5** Braden Scale for Predicting Pressure Sore Risk

 
| **Component** || **Levels** |
| --- | --- |
| Sensory perception || 

1.  Totally limited
    
2.  Very limited
    
3.  Slightly limited
    
4.  No impairment
    

 |
| --- | --- |
| Skin moisture || 

1.  Constantly moist
    
2.  Very moist
    
3.  Occasionally moist
    
4.  Dry
    

 |
| Activity || 

1.  Bedfast
    
2.  Chairfast
    
3.  Walks occasionally
    
4.  Walks frequently
    

 |
| Friction and shear || 

1.  Frequently sliding
    
2.  Feeble correction
    
3.  Independent correction
    

 |
| Mobility || 

1.  Completely immobile
    
2.  Very limited
    
3.  Slightly limited
    
4.  Full mobility
    

 |
| Nutrition || 

1.  Very poor
    
2.  Probably inadequate
    
3.  Adequate
    
4.  Excellent
    

 |

#### Overlap of Different Tables

While comparing the clinical event and lab tables we may notice that there is a certain level of overlap between the two tables. This could be because some of the lab workups are performed in the clinical wards and the database records any data produced by these centers in the clinical event table, although in nature these are lab procedures. To overcome this issue, we can create a mapping table to map similar results from the clinical event table to the lab table after cleaning the overlap variables using our data cleaning tool.

#### Correction of Misinformation

We may find many cases of inconsistent labeling of events in the clinical event and lab tables which most likely occurred during the data entry process. For example, the two variables associated with coma scores are Pediatric Coma Score, for non-adults, and Glasgow Coma Score, for adults. However, occasionally adult patients are labeled with pediatric event codes, Pediatric Coma Score, instead of the Glasgow Coma Score. We can use the encounter table and history of patients' records to fix this issue.

### 4.3.5 Diagnosis and Medication Table

Other tables in Our database such as Diagnosis and Medication table are mostly codes and labels rather than values. Although the data cleaning approach described above (for lab and clinical event tables) is neither required nor applicable to them, these tables have their own specific inconsistencies and issues that need to be resolved. In the remainder of this chapter, we share the important issues we faced during data preparation for a couple of specific projects: Subarachnoid Hemorrhage (SAH) cohort and HIV-Cancer cohort studies.

For medication, we found that working with the generic names would be more robust and efficient compared to medication codes (NDC codes^([1](#ch04.xhtml#en4_1))). However, we realized (possibly among different care facilities) there are some inconsistencies in spelling, upper/lower case, and using multiple words (via “-”, “/”, etc.). We used a combination of screening and clinical intuition to fix these inconsistencies and unify the generic name for similar medications.

The major issues we face with the diagnosis table are the large number of diagnosis codes (ICD-9, ICD-10) and the fact that there are no specific dates associated with each record (all of the diagnosis codes recorded with the discharge date-time stamp in the database). When using statistical models, we may decide to use higher-level codes, i.e., the first 3 digits of ICD-9 codes. Because of the ICD-10’s better design, this approach is more appropriate in handling ICD-10 codes. Reducing the number of unique diagnosis codes is not an issue when using Recurrent Neural Network (RNN) models. In fact, we have compared the same model based on both code levels and noticed no significant differences. To understand the order of diagnosis, in terms of chronology or importance, we used the information provided in two columns “Present-at-admission” and “disease-priority”. The first gives us a way to cluster the diagnoses before a certain time, which is necessary when casual inference and propensity models are used.

### 4.3.6 Procedure Table

#### Introduction to the Procedure Code Data

Procedure codes are a sub-type of medical classification used to identify specific surgical, medical, or diagnostic interventions. They should be compatible with the diagnosis codes (ICD-9 or ICD-10) to prevent a denial of payment by insurance companies like BC/BS^([2](#ch04.xhtml#en4_2)) or Medicare. In our example database, data files use three types of procedure codes. We begin this section with a brief description of each of the classification code types common in EHR databases:

*   ICD-9 procedure codes
    
    *   They are two numeric digits followed by a decimal, which is then followed by another one or two digits (in contrast with ICD-9 diagnosis codes which begins with 3 alphanumeric characters).
        
    *   They are categorized according to the anatomical region or body system.
        
    *   They have broader categories than CPT^([3](#ch04.xhtml#en4_3)) and HCPCS^([4](#ch04.xhtml#en4_4)). (There are considerably fewer ICD-9 procedure codes than there are CPT procedure codes).
        
    *   They can only be used for the inpatient setting.
        
*   CPT codes
    
    *   They are also known as the Level 1 HCPCS coding system.
        
    *   CPT is a medical code set that is used to report medical, surgical, and diagnostic procedures and services to entities such as physicians, health insurance companies, and accreditation organizations.
        
    *   They are used in conjunction with ICD-9-CM or ICD-10-CM. Numerical diagnostic coding during the electronic medical billing process.
        
    *   They are made up of five numbers.
        
    *   Unlike ICD, each number in a CPT code does not correspond to a particular procedure or technology.
        
*   HCPCS level II codes
    
    *   Level II of the HCPCS is a standardized coding system that is used primarily to identify products, supplies, and services not included in the CPT codes, such as ambulance services and durable medical equipment when used outside a physician’s office.
        
    *   Level II codes are also referred to as alpha-numeric codes because they consist of a single alphabetical letter followed by 4 numeric digits, while CPT codes are identified using 5 numeric digits.
        

#### Procedure Table Data Cleaning

The data cleaning team can try to convert some of the CPT or HCPCS Level II codes to equivalent ICD-9 procedure codes but usually, this cannot be easily done, i.e., the CPT codes and HCPCS level II codes do not fit in any of the ICD-9 procedure codes. Because of this, we can decide not to perform any data manipulation on the procedure table and the data cleaning for the procedure table may not be necessary.

## ![image](images/inline1_1.jpg)  
4.4 Discussion

Here are the key points in this chapter:

**Check the database structure.** The first step of data cleaning is to ensure that the database has the correct relational database schema. This step is crucial if the researchers are working on a copy of the database and not the original functional database. The original database should have mainly correct database structure, otherwise, it cannot be operational, but the deployment of the copy of the data is prone to structural problems. If there is any issue with the database schema it should be fixed first, otherwise, any other data cleaning procedure will introduce more errors in the data or can be unnecessarily difficult.

**Seek field expert’s guidance.** As in any other research area, it is recommended to have professionals with sufficient knowledge of the field to be included in the data cleaning team. In EHR data, we recommend including team members with clinical knowledge and health care management background in the data cleaning field.

**Do preliminary/exploratory analyses early in the study.** As we discussed in the previous sections of this chapter, in any EHR based research project, the first two questions that should be answered are:

 

1.  Does the data have enough number of patients to address the main purpose of the study?
    
2.  Is the data of good quality for conducting the study and will it yield good results?
    

 

For this purpose, we propose to write a data cleaning summary statistics report. Creating this report in the early stages of the study will answer the above questions and will help the research team to decide if the data is good enough for the study. This is crucial to prevent wasting time on the data cleaning for a data set that is not useful for that specific study.

**Data cleaning is (usually) a never-ending process.** Data cleaning begins with identifying errors. Usually, you develop a strategy for addressing the errors for a specific cohort of patients and during the advanced phases of the study, you discover more errors. Furthermore, as you move on to other patient cohorts you will probably identify new errors, specific to that population. Be prepared to return to the data cleaning step frequently.

**Document every step of data cleaning.** Data cleaning is often an iterative procedure and may need to returning to if for modifying some steps. Document every step and every procedure. This will be extremely helpful when you need to come back and possibly cannot remember what you have done before. Also, EHR research teams are usually big and staff turnover is inevitable. By keeping detailed and well-organized documentation of the data cleaning procedure you will save time and prevent unnecessary challenges.

**Be focused and efficient.** Keep in mind that you do not need to clean the whole database. It is good if you are capable of that, but usually, it will take years and by the time you are done, the database will be updated with new errors. Your data cleaning procedure should be focused based on the current study. For example, you do not need to clean the data about the history of previous joint dislocation if the research is focused on Alzheimer’s disease. Furthermore, when you see some data records are seldom present for your cohort of patients, if it is clinically justified, you may want to drop those records. As an example, let us assume you want to study the effect of weight on the development of osteoarthritis, during the First Summary Statistics Report you realized only 2% of the patients have records about the history of fungal infection of the skin. Since fungal infection of the skin is not clinically related to the development of osteoarthritis and it is sparse in your data, it may be better to drop these records. Doing this kind of initial variable selection will reduce the computational and person/time costs. On the other hand, including that in the data will probably add more noise to your data and will make future model building and/or statistical interpretation more challenging.

**There is no universal solution.** Unfortunately, there is no universal solution for data cleaning. Each EHR database has unique errors and it is almost impossible to develop a universal tool to clean every type of EHR data. But strategies such as the methods we provided in this section can be implemented to handle the data cleaning effort.

The first data cleaning for EHR data will be time-consuming, but if the focus is on developing a more generalized method for data cleaning, the data cleaning step for future projects will be easier and faster. This happens because first, the data cleaning team members will become familiar with the database structure and common errors, and second if you have fixed a lot of errors in the first data cleaning then the next project will just add a few more errors. It is beneficial to look at data cleaning as a long-term investment. As the EHR research team conducts more projects, the data cleaning team will become more efficient and the time spent on the data cleaning step will be reduced. No EHR research can be done without data cleaning and spending time on developing a generalized, efficient, and accurate data cleaning framework is justified with the potential gains in the timely conducting of future projects.

As we have discussed, data cleaning rarely ends. The data cleaning teams often find new strategies to handle data cleaning more efficiently and accurately. Your data cleaning team can focus on applying the developed general methods on the whole database when it is applicable and computationally doable. Furthermore, each project brings new challenges. In the future, we may update this chapter to reflect these new errors and present newly developed strategies.

## ![image](images/inline1_1.jpg)  
Acknowledgments

The authors of this chapter would like to thank Frances Brito, Yuxuan Gu, Michael Gonzalez, Xueying Wang, and Leqing Wu for their great work and effort in helping shape this chapter. None of this would have been possible without their unconditional support and help.

### ![image](images/inline1_1.jpg)  
**Notes**

[1](#ch04.xhtml#Cen4_1) National Drug Code

[2](#ch04.xhtml#Cen4_2) Blue Cross/Blue Shield

[3](#ch04.xhtml#Cen4_3) Current Procedural Terminology

[4](#ch04.xhtml#Cen4_4) Healthcare Common Procedure Coding System

### References

1\. Nobles A. L., K. Vilankar, H. Wu, and L. E. Barnes. 2015. Evaluation of data quality of multisite electronic health record data for secondary analysis. In: *Proceedings - 2015 IEEE International Conference on Big Data, IEEE Big Data 2015. Institute of Electrical and Electronics Engineers Inc.* 2612–2620. doi:[10.1109/BigData.2015.7364060](http://dx.doi.org/10.1109/BigData.2015.7364060)

2\. Lee M. L., T. W. Ling, and W. L. Low. 2000. *IntelliClean*. In: *Proceedings of the Sixth ACM SIGKDD International Conference on Knowledge Discovery and Data Mining - KDD ’00*. New York, New York, USA: ACM Press 290–294. doi:[10.1145/347090.347154](http://dx.doi.org/10.1145/347090.347154)

3\. Kandel S., A. Paepcke., J. Hellerstein, and J. Heer. 2011. *Wrangler: Interactive Visual Specification of Data Transformation Scripts*. [http://vis.stanford.edu/files/2011-Wrangler-CHI.pdf.](http://vis.stanford.edu) Accessed August 4, 2019.

4\. Wrangler Editions | Trifacta. [https://www.trifacta.com/products/wrangler-editions/](https://www.trifacta.com). Accessed August 3, 2019.

5\.  Apers P. M. G., M. G. Petrus, and J. M. Hellerstein. 2001. Potter’s wheel: An interactive data cleaning system. In: *Proceedings of the Twenty-Seventh International Conference on Very Large Databases, Roma, Italy, 11-14 September, 2001. Morgan Kaufmann* 381–390. [https://dl.acm.org/citation.cfm?id=672045](https://dl.acm.org). Accessed August 3, 2019.

6\. Adu-ManuSarpong K., and J. Kingsley Arthur. 2013. Analysis of data cleansing approaches regarding dirty data a comparative study. *International Journal of Computer Applications* **76**((7)): 14–18. doi:[10.5120/13258-0736](http://dx.doi.org/10.5120/13258-0736)

7\. Springate D. A., R. Parisi, I. Olier, D. Reeves, and E. Kontopantelis. 2017. rEHR: An R package for manipulating and analysing electronic health record data. and Harezlak J., ed. *PLoS One* **12**((2)): e0171784. doi:[10.1371/journal.pone.0171784](http://dx.doi.org/10.1371/journal.pone.0171784)

8\. Muthalagu A., J. A. Pacheco, S. Aufox, *et al* 2014. A rigorous algorithm to detect and clean inaccurate adult height records within EHR systems. *Applied Clinical Informatics* **5**((1)): 118–126. doi:[10.4338/ACI-2013-09-RA-0074](http://dx.doi.org/10.4338/ACI-2013-09-RA-0074)

9\. Spencer H. T., M. E. Gold, L. I. Karlin, D. J. Hedequist, and M. T. Hresko. 2014. Gain in spinal height from surgical correction of idiopathic scoliosis. *The Journal of Bone and Joint Surgery - Series A* **96**((1)): 59–65. doi:[10.2106/JBJS.L.01333](http://dx.doi.org/10.2106/JBJS.L.01333)

10\. Kahn M. G., M. A. Raebel, J. M. Glanz, K. Riedlinger, and J. F. Steiner. 2012. A pragmatic framework for single-site and multisite data quality assessment in electronic health record-based clinical research. *Medical Care* **50** Suppl (0): S21–S29. doi:[10.1097/MLR.0b013e318257dd67](http://dx.doi.org/10.1097/MLR.0b013e318257dd67)

11\. Elder J. W., S. B. Baraff, W. N. Gaschler, and L. J. Baraff. 2015. Pulse oxygen saturation values in a healthy school-aged population. *Pediatric Emergency Care* **31**((9)): 645–647. doi:[10.1097/PEC.0000000000000331](http://dx.doi.org/10.1097/PEC.0000000000000331)

12\. Dziadkowiec O., T. Callahan T., M. Ozkaynak, B. Reeder, and J. Welton. 2016. Using a data quality framework to clean data extracted from the electronic health record: A case study. *EGEMS (Washington, DC)* **4**((1)): 1201. doi:[10.13063/2327-9214.1201](http://dx.doi.org/10.13063/2327-9214.1201)

13\. Gates G. J. 2011. *“How Many People are Lesbian, Gay, Bisexual and Transgender?”* UCLA: The Williams Institute. Retrieved from [https://escholarship.org/uc/item/09h684x2](https://escholarship.org). Accessed August 2, 2019.

14\. Parker K., J. M. Horowitz, R. Morin, and M. H. Lopez. *Multiracial in America: Proud, Diverse and Growing in Numbers | Pew Research Center. Pew Research Center*. [https://www.pewsocialtrends.org/2015/06/11/multiracial-in-america/](https://www.pewsocialtrends.org). Published 2015. Accessed August 2, 2019.

15\. Clot-Silla E., A. Argudo-Ramirez, and X. Fuentes-Arderiu. 2011. Letter to the editor: Measured values incompatible with human life. *EJIFCC* **22**((2)): 52. [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4975288/](https://www.ncbi.nlm.nih.gov). Accessed July 25, 2019.

# [5 ](#contents.xhtml#toc1_83)  
![image](images/inline1_1.jpg)

# [EHR Data Pre-Processing and Preparation](#contents.xhtml)  
               

Duo Yu, Xueying Wang and Hulin Wu

## ![image](images/inline1_1.jpg)  
5.1 Introduction

Data pre-processing and preparation are the steps after data cleaning and before statistical analyses, which are critical for statistical analysis and modeling. Given a statistical analysis method, a certain format of inputs is required, some forms of data pre-processing and preparation are necessary for different data analysis purposes. On the other hand, different data pre-processing and preparation methods may produce different datasets for final analysis, which may yield different analysis results. Thus, it is important to standardize and document the data pre-processing and preparation methods in order to ensure the reproducibility of the data analysis results.

As discussed in [Chapter 1](#ch01.xhtml#chapter1) (Section 1.2), the multiple steps from EHR data extraction to data analysis may need to be performed iteratively. In particular, the steps of data pre-processing and preparation may need to be iteratively done with the steps immediately before and after it, i.e., the data cleaning step and the data analysis step ([Figure 5.1](#ch05.xhtml#fig5_1)). In general, different data pre-processing and preparation methods may be used to wrangle the data from different perspectives and for different analysis purposes. We may also need to further perform more project-specific data cleaning using the methods discussed in [Chapter 4](#ch04.xhtml#chapter4). Different purposes of data analyses may require the data to be pre-processed or prepared differently, which are usually project-specific. For example, different analysis purposes for different projects may require to define or re-define the outcomes or predictors differently, and more specific data cleaning and processing may be necessary to better determine the outcome or predictor variables.

![Figure 5.1 The data analysis framework which involves multiple steps iteratively.](images/fig5_1.jpg)

**Figure 5.1**  
The data analysis framework which involves multiple steps iteratively.

Data pre-processing and data processing are often used interchangeably. Here we will distinguish between the data pre-processing/processing and data preparation although these two steps are sometimes difficult to distinguish.

### 5.1.1 Definition of Data Pre-Processing/Processing

Before we perform formal data analyses to address a clinical or scientific question, we need to process the data, summarize it or extract useful features from it. Data pre-processing or processing may include the following tasks:

*   Summarize the data into new data variables or generate derived variables from the original data
    
*   Deal with data issues: e.g., missing data imputation or redundant data combination
    
*   Derive different features based on the repeated measurements of some variables
    
*   Extract features using dimension reduction or other feature engineering methods
    

The data pre-processing step is project-specific. Different projects may require processing the data in different ways. Usually, the data processing step may need to be iteratively performed with data preparation, and these two steps may not have a clear boundary in some cases. Ideally, we should extract as many features as possible from the raw data so that the signals and information buried in the raw data can be identified for downstream analyses.

### 5.1.2 Definition of Data Preparation

After data cleaning and data processing, we must prepare the data in different formats for different analysis purposes. The data preparation is purpose-driven, and different objectives for a project may require to prepare the data in different ways. Thus, even for a particular project, many versions of the datasets may need to be prepared for different analysis purposes. Data preparation may include, but are not limited to, the following tasks:

*   Project-specific data cleaning for data preparation: For example, if some encounters for a patient may overlap with each other or be very close in time, then we may need to combine or separate the overlapping encounters to meet the goals of a particular data analysis
    
*   Define, classify and label the patients for different outcomes, treatments or conditions
    
*   Define the encounters or time intervals to prepare the data for different analysis purposes
    
*   Prepare the data for different scenarios or cases, including for sensitivity analysis purposes
    

As aforementioned, data preparation and data processing need to be iteratively performed. Many versions of the prepared data may be created in this step. It is crucial to document or label the latest version of the prepared data and ensure that all the team members use the correct version of the prepared data for final data analyses, which is critical for the reproducibility of the analysis results.

## ![image](images/inline1_1.jpg)  
5.2 Data Pre-Processing

### 5.2.1 Tidy Data Principles

Variable encoding is a basic data pre-processing method to transform the raw data into the “tidy” format to facilitate statistical analysis. There are three principles of tidy data ([Wickham 2014](#ch05.xhtml#ref5_27)):

*   Each variable has one column
    
*   Each observation has one row
    
*   Each cell has a value
    

For structured EHR data, different variables are stored in different tables. To create a tidy dataset, we need to merge the variables from those tables into one dataset based on their relationships. In [Figure 5.2](#ch05.xhtml#fig5_2), a diagram is shown on how to create a tidy dataset base on the structured EHR data. Note that the encounter table in the EHR database is already in a tidy format, i.e., it meets all the above three principles of tidy data. However, many other tables, such as the medication table, may not be in the tidy data format, instead it may be the long data format, in which each observation has multiple rows. For example, in the top-left table in [Figure 5.2](#ch05.xhtml#fig5_2), the treatment variable is in the long data format in the medication table. In this case, each treatment of a observation need to be transformed as a single variable and to be re-formatted as an individual column. Thus, a total of 4 treatments will generate 4 columns after transformation. After merging the medication and encounter tables by encounter IDs, each row of the tidy data represents all the treatment records for one encounter of one patient in EHR data; and each column represents a single variable ([Figure 5.2](#ch05.xhtml#fig5_2) bottom) that will be included in the analysis model in the next step.

![Figure 5.2 A diagram to create tidy data from the structured EHR data. Here we treat the medication variables as binary variables.](images/fig5_2.jpg)

**Figure 5.2**  
A diagram to create tidy data from the structured EHR data. Here we treat the medication variables as binary variables.

#### Variable Encoding

The main aim of variable encoding is to transform raw data into the format of values that is appropriate for statistical analysis. Traditionally, one may group the variables into three categories based on the clean data and corresponding codebook, i.e., continuous, binary and categorical variables. For example, generally we treat age as a continuous variable, sex is considered as a binary variable, and race will be treated as a categorical variable. Sometimes, a continuous variable can be transformed to a binary or categorical variable using discretization methods if needed.

An EHR dataset may contain records of different medications, diagnoses and procedures for individual patients. We can process the data in two ways: 1) Treat them as binary variables based on whether a patient has the record of a particular medication, diagnosis, or procedure; 2) Treat them as a continuous variable by counting the frequency of the occurrence of these events, see [Figure 5.3](#ch05.xhtml#fig5_3) for details.

![Figure 5.3 Medication variables can be converted into binary or numerical variables. A medication or treatment can be transformed into a binary variable by coding whether a patient took a medication or received a treatment. However, we can also convert a medication or treatment as a numeric variable by counting the frequency of a patient who took the medication or received the treatment.](images/fig5_3.jpg)

**Figure 5.3**  
Medication variables can be converted into binary or numerical variables. A medication or treatment can be transformed into a binary variable by coding whether a patient took a medication or received a treatment. However, we can also convert a medication or treatment as a numeric variable by counting the frequency of a patient who took the medication or received the treatment.

Here we provide a concrete example of variable encoding from an EHR project, the vasopressor treatment evaluation and mortality prediction for subarachnoid hemorrhage (SAH) patients. Subarachnoid hemorrhage (SAH) is an uncommon and life-threatening stroke that accounts for approximately 5% to 10% of all strokes in the United States. A particularly serious and common complication following SAH is delayed cerebral ischemia, and the development of delayed cerebral ischemia results in even higher mortality and disability among SAH patients. When delayed cerebral ischemia is clinically suspected, induced hypertension is often recommended to maintain cerebral perfusion unless the blood pressure is already elevated ([Connolly Jr et al. 2012](#ch05.xhtml#ref5_9)). While treatment with vasopressors is often initiated to maintain cerebral perfusion, it is not known which vasopressor is most effective in improving outcomes. In this project, we evaluated the initial use of different vasopressors among patients with nontraumatic subarachnoid hemorrhage using mortality as the endpoint. A mortality prediction model was developed based on the available variables and potential predictors in the EHR database for this patient population. We will use this project as an example to illustrate the data processing and preparation principles and methods in this chapter.

In this SAH study, we used generic names of medications and the medication variables were treated as binary predictors, i.e., “1” if a patient has ever received the medication and “0” otherwise. The diagnoses, lab tests, and clinical events were also treated as binary variables. At the same time, some of these variables such as lab tests and vital signs in the clinical event table can also be treated as categorical or continuous variables. For example, glucose measurements or blood pressures have numerical values and can be treated as continuous variables.

### 5.2.2 Feature Extraction: Derived Variables

In EHR data, some variables, such as lab test results, clinical events and vital signs, were measured repeatedly in irregular time intervals and some others were only measured once for a patient. Some vital signs such as blood pressure or heart rate are measured or monitored intensively. In some cases, we need to combine those repeatedly measured variables with the ones with single measurement for a patient for predictions and other statistical models. It is necessary to either summarize each of these variables (i.e., variables with repeated measurement into summary statistics) or use some feature extraction or feature engineering approaches to extract features from it so that “tidy data” can be created for downstream analysis.

First, we may extract simple and meaningful features from the repeated measurements for a variable for an individual. These features can be simple summary statistics such as mean, median, minimum, maximum, range, quantiles, standard deviation or variance of the repeated measurements for each variable. Some other simple features may be related to the measurement time, such as the first measurement, last measurement, or the measurement immediately following a treatment. Each of these simple features reflects partial information of multiple measurements of a variable and are interpretable. If we can collect all the possible features, hopefully all the information of a variable with repeated measurements can be included in the analysis model and the information loss is minimized. As an example, [Table 5.1](#ch05.xhtml#table5_1) provides a list of features that were extracted from a lab test variable in an EHR database. [Figure 5.4](#ch05.xhtml#fig5_4) shows the feature extraction results for a lab test variable with repeated measurements.

**Table 5.1** Examples for Derived Features for a Lab Test With Repeated Measurements

| **Feature Name** || **Description** |
| --- | --- |
| Lab\_FirstTime\_1 || The first time of lab 1 test for a patient |
| --- | --- |
| Lab\_LastTime\_1 || The last time of lab 1 test for a patient |
| Lab\_TimeDuration\_1 || Lab\_last\_time\_1 - Lab\_first\_time\_1(unit: day) |
| Lab\_Counts\_1 || The total counts of lab 1 test for a patient |
| Lab\_Frequency\_1 || LabTime\_Duration\_1/ Lab\_counts\_1 (How many days it takes to do a test? Unit: day/test) |
| Lab\_FirstTime\_to\_T0\_1 || Lab\_first\_time\_1 – T0 |
| Lab\_LastTime\_to\_Te\_1 || Te - Lab\_last\_time\_1 |
| Lab\_Mean\_1 || The mean value of lab 1 for a patient |
| Lab\_Median\_1 || The median value of lab 1 for a patient |
| Lab\_Min\_1 || The minimum value of lab 1 for a patient |
| Lab\_Min\_time\_1 || The time label for Lab\_min\_1 |
| Lab\_Max\_1 || The maximum value of lab 1 for a patient |
| Lab\_Max\_time\_1 || The time label for lab\_max\_1 |
| Lab\_Var\_1 || The variance of lab 1 for a patient (Nan if there is no variance) |
| Lab\_Mode\_1 || The mode of lab 1 for a patient |
| Lab\_1Quartile\_1 || The 1st quartile of lab 1 for a patient |
| Lab\_3Quartile\_1 || The 3nd quartile of lab 1 for a patient |
| Lab\_IQR\_1 || The IQR of lab 1 for a patient |
| Lab\_QCD\_1 || The quartile coefficient of dispersion of lab 1 for a patient, which measures dispersion |
| Lab\_STdev\_1 || The standard deviation of lab 1 values for a patient |
| Lab\_CV\_1 || The coefficient of variation of lab 1 for a patient |
| Lab\_Skew\_1 || The skewness of lab 1 for a patient |
| Lab\_Kurt\_1 || The kurtosis of lab 1 values for a patient |
| Lab\_Peaks\_1 || The count of peaks of the distribution of lab 1 values for a patient |

![Figure 5.4 Simple features such as mean, variance, lab test frequency and test time can be extracted from a lab test variable with repeated measurements.](images/fig5_4.jpg)

**Figure 5.4**  
Simple features such as mean, variance, lab test frequency and test time can be extracted from a lab test variable with repeated measurements.

In this example, we further demonstrate how to extract features for lab test variables with repeated measurements in an EHR database. First, we must get a complete list of all the lab test identification numbers (IDs) and their total counts (total number of unique lab tests) for a targeted population. For our example from the subarachnoid hemorrhage (SAH) study described above, we provide our R code and results below, which shows that the total counts of 6 lab tests are 3358, 4231, 6994, 1811, 559, and 329 respectively.

![image](images/inline5_1.jpg)

Second, we need to determine the number of tests for each lab test variable for each patient so that we can summarize these multiple test results into features. As the R code shown below, for lab k (k&#160;=&#160;1 to 10), we obtain the list of patient IDs and the number of measurements that patient had for this lab test. Table TestTimes\_Patient in the example code contains the patient IDs and the counts of this lab test for all patients. Then we generate several features using summary statistics ([Table 5.1](#ch05.xhtml#table5_1)) for each lab test variable with repeated measurements for each patient. See the R code below for details. If needed, you may add more summary statistics or other features in a similar manner.

![image](images/inline5_2.jpg)

![image](images/inline5_3.jpg)

After the features are generated for all variables and all patients, some of the variables and their features may be missing for some patients due to the missing data problem. We need to label the missing data appropriately so that the missing data approaches (to be discussed below and in [Chapter 6](#ch06.xhtml#chapter6)) can be used to handle this issue in the next step. Since we want to distinguish different missing types in our dataset, we labeled the lab test results, including missing data types, into 5 categories (see the R code below and results in [Table 5.2](#ch05.xhtml#table5_2)).

**Table 5.2** Labels for Missingness

| **Label** || **Description** |
| --- | --- |
| LMV || There is at least one measured value |
| --- | --- |
| Lab0 || There is no any lab data uploaded for this patient |
| NM || Not measured |
| MM || Measured with missing values |
| FM || Measured but no feature derived |

![image](images/inline5_4.jpg)

Here we only discussed the derived variables and features extracted from a single variable. Some features can be derived from two or more variables. For example, body mass index (BMI) is a well-known derived variable from body weight and height. Similar features can be derived from multiple variables. Once the features are generated for all variables and all patients, these features can be renamed as new variables or potential predictors for downstream data analysis.

### 5.2.3 Dimension Reduction

Dimension reduction approaches can be used to generate features although most of the features generated by these methods may not be easily interpretable. In particular, it may not be easy to use for intervention or prevention purposes in clinical and population health practice. However, the dimension reduction methods are still popular to extract features from high-dimensional data for prediction and clustering purposes. It is also useful to reduce the number of predictors to improve prediction accuracy and interpretability.

#### Variable Grouping or Clustering

The curse of dimensionality is one of the EHR data problems that we need to address. This is because many of the EHR variables such as disease diagnoses, medications, lab tests, clinical events, vital signs, and procedures are high-dimensional. If we can group or cluster these variables into higher-level groups, the dimension can be significantly reduced.

For example, for the disease diagnosis, the ICD-9-CM system consists of more than ten thousand codes. Based on the hierarchical structure of the ICD-9-CM coding system, we can use the higher-level ICD-9-CM with only three digits (<1000 disease groups). Besides, the phenome-wide association studies (PheWAS) grouped the ICD-9 codes into <2000 disease groups (phecodes) and the Agency for Healthcare Research and Quality Clinical Classification Software for ICD-9-CM (CCS) grouped all ICD-9-CM codes into <300 categories. Wei et al conducted a study to evaluate the ICD-9-CM, CCS, and phecode coding systems for phenome wide association studies using the electronic health record (EHR) data ([Wei et al. 2017](#ch05.xhtml#ref5_26)). Their results suggested that, although all ICD-9-CM, CCS and phecodes can be used for PheWas studies, the phecodes system produces superior analysis results ([Wei et al. 2017](#ch05.xhtml#ref5_26)). In addition, phecodes are more consistent with the disease categories that are generally used in clinical practice. The latest version of the phecodes groups 15,558 ICD-9-CM codes (including both three- and five-digit codes) into 1,866 disease categories ([Denny et al. 2013](#ch05.xhtml#ref5_11)). Similarly, we can group other types of EHR variables such as medications, lab tests and procedures into higher-level categories so that the dimension of the variables can be reduced. In addition, some categorical variables may have too many categories that can also be grouped or combined into bigger categories so that the sample size for each category is not too small for downstream analysis. For example, race has more than 9 categories and small categories have very few subjects. In this case, we may combine some of these small categories in order to obtain a sufficient sample size for further analysis. However, we have to consider the balance between the resolution of the analysis results and the sample size when we try to reduce the dimension by combining the variables and categories into larger categories. This needs to be considered on a case-by-case basis.

#### Principle Component Analysis (PCA)

Principal component analysis (PCA) is a multivariate technique that analyzes a data matrix, denoted by X, in which observations are described by several inter‐correlated quantitative dependent variables. Its goal is to reduce the dimensionality of a dataset while maintaining the variations in the data. It uses an orthogonal transformation to convert the correlated variables in the dataset to a new set of uncorrelated and ordered variables called principal components (PCs). Mathematically, PCA is an orthogonal linear transformation that rotates the original data to a new coordinate system such that the X lies along the direction of the greatest variation of the data, the second greatest variance lies on the second coordinate, and so on ([Abdi and Williams 2010](#ch05.xhtml#ref5_1)).

Suppose we have a data matrix X&#160;=&#160;(X[1],&#160;…,&#160;X[p]) with measurements of p random variables, the first several PCs are the linear combinations of the original variables that explain the majority of the variance of the data. We can obtain the PCs from the ordered eigenvalues of the correlation matrix for the standardized X matrix. The first PC is obtained from the eigenvector corresponding to the largest eigenvalue. The p PCs can be written as,

$\\begin{matrix} {Y\_{1} = e\_{1}^{\\prime}X = e\_{11}X\_{1}\\ + \\ \\cdots\\ + \\ e\_{1p}X\_{p}} \\\\ {Y\_{2} = e\_{2}^{\\prime}X = e\_{21}X\_{1}\\ + \\ \\cdots\\ + \\ e\_{2p}X\_{p}} \\\\ \\vdots \\\\ {Y\_{p} = e\_{1}^{\\prime}X = e\_{p1}X\_{1}\\ + \\ \\cdots\\ + \\ e\_{pp}X\_{p}} \\\\ \\end{matrix}$

For the purpose of dimension deduction, we may keep the first q PCs (q&#160;<&#160;p) so that the majority of the information or variation in X can still be explained with these q components or PCs. We can calculate the percentage of variance explained for the ith PC by the formula:$PC = \\frac{\\lambda\_{i}}{\\sum\_{k = 1}^{p}\\lambda\_{k}}$

In many cases, around 80% of the total variance for large p can be attributed to the first few PCs, which helps us to reduce the dimension of our dataset by using these components to replace the original data without incurring much loss of information ([Jolliffe 2011](#ch05.xhtml#ref5_17)). However, if we use the PCs as predictors in a prediction model, it may not be easy to explain the results and the PC predictors from a clinical perspective, which is a drawback in using the PCA for dimension reduction. Here we only discussed the PCA approach under the linear model and Gaussian assumption. For other dimension reduction methods, see the book by Li ([Li 2018](#ch05.xhtml#ref5_19)).

#### Embedding and Deep Learning

EHR data has high dimensional and sparse medical codes, such as medications, diagnoses and procedures. Efficiently reducing the data dimension may improve the performance of the data analysis and predictions. Embedding is a dimension reduction method which transforms the binary and categorical variables into continuous feature vectors. With binary or categorical variables, the basic encoding method is the one-hot encoding or dummy encoding: each variable is represented as a vector with one “1” and multiple “0”. However, there are some drawbacks for one-hot encoding. In high dimensional settings, it gets over-fitting easily, resulting in poor performance for the generalization of prediction models. In [Figure 5.5](#ch05.xhtml#fig5_5), we illustrate the difference between one-hot encoding and embedding vectors. With 6 medical codes, one hot encoding requires a vector with a length of 6 to represent each code, whereas, the embedding vector only needs 3 dimensions. In real-world applications, one can choose the dimension of the embedding vector as needed in order to achieve better performance.

![Figure 5.5 A diagram to illustrate the embedding methods.](images/fig5_5.jpg)

**Figure 5.5**  
A diagram to illustrate the embedding methods.

Some efforts were made on the developments of embedding methods to improve the prediction accuracy using EHR data. Some methods have largely borrowed ideas from Natural Language Processing (NLP) techniques word embedding, like Continuous Bag of Words Model (CBOW) and Skip-gram ([Mikolov et al. 2013](#ch05.xhtml#ref5_21)). CBOW is the model with a goal to predict the current word based on surrounding words. On the contrary, Skip-gram is used to predict the surrounding words given the current word. Choi et al proposed **Med2vec** which can be used to learn distributed representations for both medical codes and visits from a large EHR dataset (Choi, Bahadori, Searles, et al. 2016).

### 5.2.4 Missing Data Imputation

It is important to deal with the missing data in the data processing step. The EHR database is usually designed for practical operation or billing purposes, instead of data analysis or research purposes, and the missing data issues are highly prevalent for EHR data. The likelihood-based approach via the expectation-maximization (EM) method ([Dempster, Laird, and Rubin 1977](#ch05.xhtml#ref5_10)) and Bayesian approach via MCMC techniques ([Andrieu et al. 2003](#ch05.xhtml#ref5_2)) have been proposed to deal with the missing data directly under the variety of regression models, but these methods are computationally expensive for big EHR data analysis. An alternative strategy is to use the “missing data imputation” approaches to generate a “complete data set” which can be used for data analyses in the next step. Missing data imputation methods include the Multiple Imputation by Chained Equation (MICE) ([Azur et al. 2011](#ch05.xhtml#ref5_3)), MissForest ([Stekhoven and Bühlmann 2012](#ch05.xhtml#ref5_25)) and Matrix/Tensor Completion (MC/TC) ([Phien et al. 2016](#ch05.xhtml#ref5_24)) methods such as spectral regularization algorithms ([Mazumder, Hastie, and Tibshirani 2010](#ch05.xhtml#ref5_20)), and Structural Matrix Completion (SMC) ([Zhang et al. 2016](#ch05.xhtml#ref5_29)) among others. The performance and efficiency of these methods depend on many factors including the type of missing (MCAR, MAR, MNAR), correlation structures of the data, missing percentage and the type of variables. We will discuss the details of these methods in the next chapter.

## ![image](images/inline1_1.jpg)  
5.3 Data Preparation

### 5.3.1 Define the Endpoint or Outcome

For a specific project, it is crucial to determine the endpoint or outcome variable. For example, if the goal of a project is to predict mortality of patients under some conditions or treatments, “mortality” needs to be defined based on the discharge status of a patient at the end of an encounter. It is possible that the mortality or death may not be clearly labeled in the encounter discharge disposition. For example, in the SAH project, a total of 24 types of patient discharge disposition were found in the cohort of SAH patients who received at least one of the three vasopressors (phenylephrine, norepinephrine, and dopamine), see [Table 5.3](#ch05.xhtml#table5_3) below. We defined the mortality of a patient if any one of the following 5 categories of discharge disposition was assigned ([Williams et al. 2020](#ch05.xhtml#ref5_28)):

${Death}{indicators}\\begin{cases} {1.} & {Expired} \\\\ {2.} & {{Hospice}/{medical}{facility}.} \\\\ {3.} & {{Expired}{in} a{medical}{facility}.{Medicaid}{only}{hospice}} \\\\ {4.} & {{Expired}{at}{home}.\\mspace{1mu}{Medicaid}{only},{hospice}} \\\\ {5.} & {{Hospice}/{home}} \\\\ \\end{cases}$

**Table 5.3** The List of Patient Discharge Disposition Descriptions and Corresponding Number of Patients in the Cohort of SAH Patients Who Received at Least One of Three Vasopressors

| **Index** || **Patient Discharge Disposition Description** || **\# of Patients** |
| --- | --- | --- |
| 1 || Expired || 1803 |
| --- | --- | --- |
| 2 || Discharged/transferred to another rehab fac including rehab units of a hospital || 884 |
| 3 || Discharged to home || 800 |
| 4 || Discharged/transferred to SNF || 366 |
| 5 || Discharged/transferred to a long-term care hospital || 217 |
| 6 || Discharged/transferred to home with home health service || 115 |
| 7 || Discharged/transferred to another short-term hospital || 110 |
| 8 || Discharged/transferred to another type of inpatient care institution || 59 |
| 9 || Discharged/transferred to another type of health care institution not defined elsewhere || 54 |
| 10 || Hospice/medical facility || 49 |
| 11 || Discharged/transferred to ICF || 49 |
| 12 || Expired in a medical facility; Medicaid only, hospice || 21 |
| 13 || Discharged/transferred to a designated cancer center or childrens hospital || 19 |
| 14 || Expired at home; Medicaid only, hospice || 19 |
| 15 || Admitted as an inpatient to this hospital || 18 |
| 16 || Hospice/home || 13 |
| 17 || Discharged/transferred to a nursing facility certified under Medicaid but not certified under Medicare || 10 |
| 18 || Left AMA || 8 |
| 19 || Discharged/transferred to a federal health care facility || 8 |
| 20 || Discharged/transferred/referred to a psychiatric hospital of psychiatric distinct part unit of a hospital || 6 |
| 21 || Still patient or expected to return for outpatient services || 3 |
| 22 || Discharged to court/law enforcement/jail || 2 |
| 23 || Discharged/transferred within this institution to Medicare approved swing bed || 1 |
| 24 || Discharged/transferred to a Critical Access Hospital (CAH) || 1 |

In another example, a project aims to predict heart failure for patients with hypertension or diabetes. The endpoint is the “heart failure”, which needs to be defined based on the disease diagnosis code. In the ICD-9 or ICD-10 coding system, we need to identify all the codes that correspond to “heart failure”. In addition, we need to consider whether one heart failure code is good enough to confirm this patient as a “heart failure” patient ([Choi, Schuetz et al. 2016b, a](#ch05.xhtml#ref5_8)). In literature, three heart failure disease codes within 12 months were necessary to declare a confirmed “heart failure” case ([Gurwitz et al. 2013](#ch05.xhtml#ref5_14), [Ng et al. 2016](#ch05.xhtml#ref5_22), Choi, Bahadori, Sun et al. 2016). Sometimes, formal phenotyping methods ([Banda et al. 2018](#ch05.xhtml#ref5_4), [Glicksberg et al. 2018](#ch05.xhtml#ref5_12), [Hubbard et al. 2019](#ch05.xhtml#ref5_16), [Gronsbell et al. 2019](#ch05.xhtml#ref5_13)) may be needed to formally confirm the disease diagnosis (See Section 3.4 for more details on disease phenotyping). The endpoint or outcome can also be defined based on laboratory test results, clinical events, vital signs or microbiology tests. We need to carefully evaluate the reliability and uncertainty of these variables that will be used to derive the endpoint or outcome. If the endpoint or outcome variable is not well and reliably defined, it may result in bias and misleading conclusions.

### 5.3.2 Process Medical Record Timestamps

EHR consists of patients’ various temporal clinical information such as procedures, medications, lab tests, and clinical measures. Given a specific treatment or condition of interest, we may expect to evaluate the clinical situation or outcome before and after the treatment or condition for a patient; or we may want to compare the clinical situation or outcome for patients with and without a particular treatment/condition based on EHR data. In this case, it is important to accurately determine the timestamps of treatments and other clinical records to build a prediction model or conduct a causal inference analysis. However, the timestamps in the raw EHR data are usually noisy and incomplete. We need to carefully process and clean the timestamps of medical records so that different temporal modeling tasks and analyses can be done based on the cleaned timestamps.

Generally, multiple timestamps for one medical record are available in the EHR database. For example, a lab test record is usually labeled with several timestamps, such as lab ordered time, drawn time, received time, performed time, completed time, verified time, and canceled time. For most projects and data analysis, only one timestamp for each medical record is needed. Intuitively, we may use the time that an intervention, treatment or lab test sample were actually performed on or drawn from the patient. Thus, we prefer “drawn time” out of the aforementioned seven timestamps as the time label for a lab test record. However, for some lab test records, the drawn time might be missing or wrong. In this case, we may need to deal with the missing and wrong timestamps. If the “drawn time” for a lab test is missing or wrong due to typos or errors, other timestamps for the lab test can be used to approximate the drawn time. For example, we may approximate the drawn time of a lab test with the following priority order, performed, completed, received, verified, and ordered time, whichever was available first and valid. We may need to evaluate whether any of the above timestamps are beyond the reasonable time interval or an outlier due to typos or errors (e.g., some timestamps that were outside of the encounter time interval or even outside of time window of all other medical records of the patient). Sometimes it is not trivial to determine a timestamp to be an outlier or error, which may require a complicated algorithm for this purpose. Fortunately, error due to an outlier is quite rare. A simple strategy for dealing with this is to predefine a rule for the validity of a timestamp. That is, labeling a timestamp as invalid if it is completely missing or it is an outlier (we also need a clear rule for the definition of an outlier). For example, in the SAH study, we processed and imputed the lab test timestamps as follows.

*   Remove the lab records from the analysis if they were labeled with a canceled time, since these lab tests were likely canceled.
    
*   Use the “drawn time” as the lab test timestamp if it is available and valid. Otherwise, use other available and valid timestamps to approximate the drawn time with the following priority order: performed, completed, received, verified, and ordered time.
    
*   The lab test timestamp is labeled as missing if all the timestamps are missing or invalid.
    

Similarly, we can process and clean the timestamp for clinical events. The timing for each clinical event record was originally labeled with the performed time, event start time, event end time, and verified time. Ideally, we prefer to use the performed time as the timestamp for the clinical event. If the performed time is not available, we may follow the priority order to sequentially use the event start time, event end time and verified time to approximate the performed time. We can also process and clean the timestamps for medications, procedures, and other medical records using a similar strategy.

### 5.3.3 Define the Encounter Time Interval

An encounter is defined as an interaction between a patient and healthcare provider(s) for the purpose of providing healthcare service(s) or assessing the health status of a patient (HL7®). Generally, there are well-defined admission and discharge times for each encounter in the EHR system. Ideally, all the medical records or events with the same encounter ID are within the time interval between the admission and discharge times, see [Figure 5.6](#ch05.xhtml#fig5_6) for a good example.

![Figure 5.6 An encounter with well-defined encounter start and end times (the admission time and discharge time). All the time stamped medical records are within the admission (dashed line) and discharge time (black line) interval.](images/fig5_6.jpg)

**Figure 5.6**  
An encounter with well-defined encounter start and end times (the admission time and discharge time). All the time stamped medical records are within the admission (dashed line) and discharge time (black line) interval.

However, in reality, there are many problems in accurately determining the time interval for an encounter. We noticed that it might not be accurate if the encounter admission and discharge times were used as the encounter starting time and ending time since we found that some medical records and events with the same encounter ID were outside of the time interval between the encounter admission and discharge times. In this case, we may need to redefine the encounter starting time and ending time. First, we may need to deal with the following issues:

*   Some encounter admission or discharge time is missing; see [Figure 5.7(a)](#ch05.xhtml#fig5_7) below.
    
*   There are some errors and outliers in the encounter admission or discharge times; see [Figure 5.7(b)](#ch05.xhtml#fig5_7) below.
    
*   Some medical records or events of an encounter are outside of the encounter admission and discharge time interval due to various reasons; see [Figure 5.7(c–d)](#ch05.xhtml#fig5_7) below.
    

![Figure 5.7 Encounters with problematic starting and ending times: (a) the encounter discharge time was missing; (b) the encounter admission time was earlier than the medical records; (c) The encounter admission time was later than those medical records with the same encounter ID; (d) the encounter discharge time was earlier than many medical records with the same encounter ID.](images/fig5_7.jpg)

**Figure 5.7**  
Encounters with problematic starting and ending times: (a) the encounter discharge time was missing; (b) the encounter admission time was earlier than the medical records; (c) The encounter admission time was later than those medical records with the same encounter ID; (d) the encounter discharge time was earlier than many medical records with the same encounter ID.

In order to deal with the above issues, we may need to extract all medical records or events with timestamps, such as medications, laboratory tests, procedures, and clinical events (including vital signs). Intuitively, the time for the first medical record or event with the same encounter ID can be defined as the starting time (T[o]) of the encounter, while the time for the last medical record or event can be defined as the ending time (T[e]) of the encounter. However, this can be challenging due to the errors and outliers of timestamps for the medical records and events in the EHR database. We may need to develop an algorithm to deal with the errors and outliers in the medical records.

To illustrate, in the SAH study, we developed an ad hoc method to use two parameters to screen the outliers, one was the time difference threshold (*d*) between two consecutive medical records/events which were used to divide medical records/events into clusters, and another was the size of the cluster (*p*) which is the proportion of medical records/events in a cluster relative to the total number of records in the encounter. For example, if *d* is fixed as 10 days and only two medication records/events have consecutive time difference to be greater than 10 days, then all medical records/events are split into two clusters in this encounter. If *d* increases, then the number of clusters will be smaller, and the size of clusters will be more unbalanced (some clusters will have very large or very few medical records or events). We assume that the consecutive time difference between two medical records is small within the same encounter. When *p* is small enough and *d* is large enough, we may consider the smaller cluster of medical records or events as outliers that can then be excluded from this encounter. In practice, we need to carefully determine the appropriate values of *d* and *p* based on initial data exploration and experience. Once *d* and *p* are determined, we propose the following algorithm to exclude the outliers of medical records or events from an encounter:

Given consecutive record times for an encounter, *t*[0], *t*[1], *t*[2]⋯*t*[*n*],the consecutive time differences can be calculated as *d*[1] = *t*[1] − *t*[0], *d*[2] = *t*[2] − *t*[1], ⋯, *d*[*n*] = *t*[*n*] − *t*[*n* − 1].

*   **Outliers at the beginning of an encounter**: Assume that the index of *d*[*i*] such that *d*[*i*] > *d* day are *i*[1], *i*[2], ⋯ *i*[*b*], the records in \[*t*[0], *t*[*i*[*j*]]\] are considered as outliers, if the number of records in \[*t*[0], *t*[*i*[*j*]]\] is less than *p* of total number of records in \[*t*[0], *t*[*n*]\], *i*[*j*] ∈ {*i*[1],*i*[2],⋯*i*[*b*]};
    
*   **Outliers at the end of an encounter:** Assume that the index of *d*[*i*] such that *d*[*i*] > *d* days are *i*[1], *i*[2], ⋯ *i*[*e*]. Records in \[*t*[*i*[*j*]],*t*[*n*]\] are considered as outliers if the number of records in \[*t*[*i*[*j*]],*t*[*n*]\] is less than *p* of total number of records in \[*t*[0], *t*[*n*]\], *i*[*j*] ∈ {*i*[1],*i*[2],⋯*i*[*e*]}.
    

After excluding the outliers of the medical records for an encounter, the ordered timestamps of the remaining records from the smallest to the largest are *t*[0]′, *t*[1]′, *t*[2]′⋯*t*[*n*]′, then the encounter starting time *T*[0] is defined as *T*[0]\= *t*[0]′, while the encounter ending time *T*[*e*] is defined as *T*[*e*] = *t*[*n*]^′⋅

To cite an example, in the project of mortality prediction for SAH patients, we needed to redefine (T[0], T[e]) for each SAH encounter. Although each encounter has its admission time and discharge time in the EHR database, we cannot use these to define the encounter time interval due to all the aforementioned problems. In this SAH cohort, some encounters' admission time or discharge time was missing. In fact, the admission time was missing for 6 encounters (patients) and the discharge time was missing for 41 encounters (patients), see [Figure 5.7(a)](#ch05.xhtml#fig5_7) for an example. Simultaneously, we found that some encounters' admission time was one day earlier than any of the medical records or events in this encounter, see [Figure 5.7(b)](#ch05.xhtml#fig5_7) for example. We also found that at least one medication record was earlier than the admission time among 41% of the encounters (patients) in this SAH cohort; while at least one medication record was later after the discharge time among 20% of the encounters (patients), see [Figure 5.7(c–d)](#ch05.xhtml#fig5_7) for examples.

In this SAH study, we set *d* = 3 days and *p* = 10% based on our initial data exploration. We redefined the starting and ending times for each encounter before further data processing and data analysis.

### 5.3.4 Encounter Combination

In an EHR database, all the medical records and events of each patient are organized into encounters in a longitudinal and hierarchical way. Each patient may have multiple encounters in the EHR database, and during each encounter, multiple medical records or events were recorded, including diagnoses, medications, and lab test results, and procedures, which are usually stored in separate tables but can be linked by encounter IDs. However, sometimes the encounters are not clearly separated and may overlap across the time recorded, see [Figure 5.8](#ch05.xhtml#fig5_8) below for examples:

![Figure 5.8 The encounters in an EHR database.](images/fig5_8.jpg)

**Figure 5.8**  
The encounters in an EHR database.

To address a specific scientific question for a particular project, we may not need to use all the data from all encounters. Sometimes, we need to focus on the data from one encounter or a fixed number of encounters within some time periods under some pre-defined conditions. In this case, we need to deal with the encounter overlapping problem and determine the data from which encounter(s) should be included and excluded for analysis. For example, in our SAH study, we only considered one encounter with a SAH diagnosis and we applied a “24 hour–rule” to combine the encounters, i.e., combine the two encounters if the time gap between the two encounters is less than 24&#160;hours. The combined encounters were considered as one encounter or one clinical visit. In this project, we implemented this by reading in the encounter table using the following Python codes first, from which a total of 4850 SAH patients were extracted from the EHR database. However, we found that these patients had 4881 SAH encounters, which indicates that some patients might have multiple SAH encounters.

![image](images/inline5_5.jpg)

Then we used the following Python codes and identified 30 patients with multiple SAH encounters (29 of them had 2 SAH encounters and one of them had 3 SAH encounters):

![image](images/inline5_6.jpg)

Based on the “24 hour–rule”, we identified 28 encounters that need to be combined into 14 new encounters or clinical visits (we may call the combined encounters as “clinical visits”). The following Python codes were used to implement this step (notice that the encounter admission and discharge times were used to combine the encounters in the following illustration; although, ideally, the cleaned (T[0],&#160;T[e]) from the above subsection should be used in practice).

![image](images/inline5_7.jpg)

In addition, 17 SAH encounters were identified as the second SAH encounters for 17 patients. In this study, we decided to focus on the first SAH encounter or clinical visit for each patient, thus, the data from these 17 encounters were dropped from further analyses.

![image](images/inline5_8.jpg)

Finally, the EHR data from 4850 combined encounters or clinical visits, derived from the original 4864 SAH encounters for 4850 SAH patients were included for further analyses. The following Python codes were used to finalize the encounter combination:

![image](images/inline5_9.jpg)

Different projects may need to combine these encounters in different ways. Encounter combination and processing are also important to determine what data should be included or excluded for further data analyses. Thus, this is a critical data preparation step for any project.

### 5.3.5 Define Comparison Groups

If the goal of a project is to compare the outcomes between two or more groups of patients under different conditions or treatments, we may need to classify the patients into these comparison groups. However, sometimes this is not trivial. In general, the groups of patients we want to compare are usually selected based on some specific clinical exposures or conditions, e.g., patients with different treatments. To define the comparison groups, we must use clinical knowledge or involve domain experts. In light of this, we propose the following procedure to define the comparison groups:

STEP 1: Obtain a full list of possible treatments or conditions for comparison from domain experts and/or literature;

STEP 2: Extract the data based on pre-defined inclusion/exclusion criteria;

STEP 3: Define and create initial comparison groups based on the extracted data;

STEP 4: Generate summary statistics and perform initial data exploration based on the comparison groups;

STEP 5: Evaluate the summary statistics and preliminary data to identify problems and issues for group comparisons if any;

STEP 6: Discuss and resolve the problems and issues identified in Step 5 by collaborations among statisticians, data scientists and clinical experts. If necessary, iterate Steps 2–6;

STEP 7: Refine and finalize the comparison groups.

In the SAH study, our objective was to compare the effect of commonly used vasopressors on the clinical outcome of SAH patients. The list of candidate vasopressor treatments for SAH patients was proposed by experienced clinicians on SAH treatments, i.e., dopamine, phenylephrine or norepinephrine. We decided to use the mortality, defined as above, as the outcome (or endpoint) for this study since it is relatively reliable for SAH patients. In order to establish the comparison groups for SAH patients with different vasopressor treatments, first, we extracted the data for patients with a SAH diagnosis code and at least one of the above three vasopressor treatments (we also checked that the dose of the vasopressor must be bigger than zero). More details on EHR data extraction can be found in [Chapter 3](#ch03.xhtml#chapter3). Based on the extracted data, we proceed to group patients into the three vasopressor treatment groups. Since a patient might be treated with multiple vasopressors, it is not trivial to classify the patients into one of the three treatment groups. We have multiple options to define the comparison groups in this case. One option is that we consider all the possible combinations of three vasopressor treatments, including the sequential order of the three vasopressors. In this case, we have 15 comparison groups. If we label each of the three vasopressors by dopamine—1, phenylephrine—2, and norepinephrine—3 respectively, the total 15 comparison groups are: {1, 12, 13, 123, 132, 2, 21, 23, 213, 231, 3, 31, 32, 312, 321}. In this case, there are too many comparison groups and the sample size for some groups is very small. Thus, we decided to redefine the treatment comparison groups by the first vasopressor use, i.e., we group patients into the following three groups:

*   Dopamine group: {1, 12, 13, 123, 132}
    
*   Phenylephrine group: {2, 21, 23, 213, 231}
    
*   Norepinephrine group: {3, 31, 32, 312, 321}
    

By following this procedure, we reduced the number of groups to three vasopressor groups. Then, we classified each patient into one of the three vasopressor treatment groups based on the first vasopressor use. However, after this was done, we found that 40 patients started multiple vasopressors at the same time, which was possibly caused by recording errors. Thus, we did not know how to classify these 40 patients. Since the purpose of this project is to compare the effect of three vasopressor treatments, we excluded these 40 patients from our comparative analysis. We used the following Python codes to implement this step.

![image](images/inline5_10.jpg)

To summarize, sometimes it may not be trivial to define and identify the comparison groups from the EHR database. Domain expertise is needed for this purpose. Due to noise, errors and uncertainties of the EHR data, caution should be exercised in order to appropriately group patients into different comparison groups.

### 5.3.6 Cohort Refining

At the beginning of a project, the patient population or cohort should be well defined based on the proposed study objective or purpose. Then, the inclusion and exclusion criteria can be established for initial data extraction (See [Chapter 3](#ch03.xhtml#chapter3) for details). However, due to errors and data problems, not all patients who satisfy the initial inclusion and exclusion criteria are eligible for final data analysis. We need to explore the initially extracted data and further assess the eligibility of all the subjects for final data analysis. Some subjects may be ineligible for downstream analysis due to the data uncertainty, errors and other data problems. For example, some patients cannot be classified into any comparison groups of interest due to missing data or errors as demonstrated in the above subsection. In this case, the patients may need to be excluded from further analysis. In another example, if the endpoint or outcome of a patient is not well-defined or missing, we may need to drop this patient from further data analysis, unless some missing data methods are used to deal with the missing data problem for the response variable. Thus, not all the patients in the study cohort who are extracted from the EHR database, based on the initial inclusion and exclusion criteria, are eligible for final data analysis. Further assessment based on the extracted data or data exploration is needed to further refine the cohort in the data preparation step.

As an example, in the SAH project discussed above, 40 patients were excluded from the comparative analysis of vasopressor treatments due to the fact that they had multiple initially assigned vasopressors and we did not know which treatment groups these patients should be assigned. A small number of patients whose outcome (mortality) was missing were also excluded from further data analysis (although an alternative strategy is to resolve the missing data problem to make them eligible as participants). In this SAH study, one of the inclusion/exclusion criteria was patients aged 17 years or older. After we extracted the data from the patients who satisfied this age criterion, we found that two patients’ diagnosis records were all pediatric diseases. After consulting with a clinical expert, we suspected that this might be caused by an error in recording the age. Thus, these two patients were not eligible and were excluded from further analysis. Thus, this SAH cohort that was initially extracted from the EHR database based on the initial inclusion/exclusion criteria was 4850 patients. After the cohort refining, a total of 247 patients were excluded which resulted in 4603 patients who were included for final data analysis. See [Figure 5.9](#ch05.xhtml#fig5_9) below for the workflow of the cohort refining for the SAH project.

![Figure 5.9 Cohort refining for the SAH project.](images/fig5_9.jpg)

**Figure 5.9**  
Cohort refining for the SAH project.

### 5.3.7 Leakage Detection

Information or data leakage is deemed as “one of the top ten data mining mistakes” ([Nisbet, Elder and Miner 2009](#ch05.xhtml#ref5_23)). When the information from outside the training dataset or the partial information for the response variable (which is not available in the real prediction situation) is used to develop or train the predictive model, the established predictive model is often overly optimistic. Particularly, in a structured EHR database, in which medical records or data are stored in separate tables, the leakage variables or predictors, such as the immediate triggers of the outcome and the potential consequences of the outcome, might be buried among the large number of variables and predictors in different tables. Sometimes it is hard to identify the leakage variables. It is impossible to evaluate or review every single potential variable from the tremendous number of candidates in the EHR database. Kaufman et al. proposed several ways to detect leakage candidates, including exploratory data analysis (EDA), the examination of modeling results, and early in-the-field testing of initial models ([Kaufman et al. 2012](#ch05.xhtml#ref5_18)). A suspiciously high prediction accuracy may indicate possible information leakage or data leakage, and a thorough investigation is needed.

Another goal of the SAH study is to develop a predictive model for SAH patient mortality, which is defined by the discharge disposition of the SAH encounter (see details in [Section 5.3.1](#ch05.xhtml#sec5_003_001) above). We may use the variables such as diagnoses at admission, medications, procedures, clinical events and lab test variables to predict the risk of mortality for SAH patients. After determining the encounter time interval, combined the encounters, and refined the cohort (See [Sections 5.3.3](#ch05.xhtml#sec5_003_003)–[5.3.6](#ch05.xhtml#sec5_003_006) above), we must identify potential leakage variables and predictors in order to establish a realistic predictive model. To screen out the potential leakage variables or predictors from a large number of medical record variables in the EHR database, we conducted exploratory data analysis and leakage variable screening iteratively. For example, in the SAH study, we first calculated the mortality rates for each of the conditions or categories for all binary or categorical predictors. If the mortality rate of one condition or category for a binary or categorical predictor is close to 100%, this predictor is considered as a potential leakage predictor and further investigation is recommended to confirm the case by consulting with clinical experts. The predictive modeling approaches, in particular those predictive models with capabilities to rank the importance of predictors, can also be used to screen the potential leakage predictors. For example, we first implemented an L1-penalized logistic regression (LASSO) model to predict mortality in the SAH project, then all the significant predictors were ranked based on the odds ratio. The highly ranked predictors are potential leakage variables that we must study further.

In addition, some disease diagnoses, medications or clinical conditions are almost equivalent to the prediction outcome although they may not be easily detected using the above screening approaches due to a small size of cases. For example, in the SAH study, we found out that the brain death (ICD-9-CM, 348.82) and encounter for palliative care (ICD-9-CM, V66.7) were also among the potential predictors for mortality, but these two diagnoses are almost equivalent to death and should be excluded from the list of predictors for mortality. In the diagnosis table, the donors of other specified organ or tissue (ICD-9-CM, V59.8), donors of unspecified organ or tissue (ICD-9-CM, V59.9), liver donors (ICD-9-CM, V59.6), and cornea donors (ICD-9-CM, V59.5) are potential signifiers of death and should also be excluded from the predictors. The length of stay in the hospital was strongly correlated with SAH mortality and was not available to use for future predictions in the real world, thus, any variables related to the length of stay such as the procedure variables, including continuous invasive mechanical ventilation for less than 96 consecutive hours and continuous invasive mechanical ventilation for 96 consecutive hours or more, should be excluded from the predictors.

In summary, data or information leakage is an important problem that must be addressed in developing machine learning predictive models when using the EHR data. Otherwise, the established model performs well during testing may fail to achieve the same level of performance in real-world situations. Due to the high dimensionality of the EHR data, this problem may not be easy to handle. Caution must be exercised when a predictive model's performance seems too good to be true.

### 5.3.8 Data Preparation for Different Analysis Purposes

For a project dealing with a particular scientific question or with different objectives, different statistical methods and predictive models may need to be used. Different statistical methods or models may require different input formats of data. For a project, we may need to prepare multiple versions of the same data in several formats to meet these different needs. For example, we can use either the traditional logistic regression model or the time-to-death survival model for mortality predictions, but the input formats of the logistic regression model and survival model are different. Thus, we need to prepare the data in different formats for different analysis purposes. Data preparation is both project- and method-specific.

In general, EHR data can be prepared in two ways, cross-sectional and longitudinal formats. For the cross-sectional data format, it can be prepared based on the tidy data principle (see [Section 5.2.1](#ch05.xhtml#sec5_002_001) above), i.e., each row is one patient or one encounter for a patient and each column is one variable. For the longitudinal data format, each patient or encounter may have multiple rows of observations and each column is one variable.

We use the mortality prediction for the SAH project as an example to demonstrate the data preparation step for different data analysis purposes. The primary aim of mortality prediction in the SAH project was to predict death in two scenarios: Scenario 1, predict the risk of mortality for SAH patients using the EHR data from the first 24&#160;hours after hospital admission; Scenario 2, predict the death for SAH patients using the EHR data up to 24&#160;hours prior to hospital discharge or death. Thus, the length of the observational window was fixed at 24&#160;hours in Scenario 1; whereas the length of the prediction window was fixed at 24&#160;hours in Scenario 2. To explore the effect of length of observational and predictive windows on mortality prediction accuracy, we also predicted the risk of mortality for SAH patients who were admitted into hospital after 48 and 72&#160;hours in Scenario 1, and the probability of death after next 48 and 72&#160;hours in Scenario 2, see [Figure 5.10](#ch05.xhtml#fig5_10) below for details.

![Figure 5.10 The observational window and prediction window in the two prediction scenarios; T\_{0} and T\_{e} denote the starting and ending times of an encounter or clinical visit.](images/fig5_10.jpg)

**Figure 5.10**  
The observational window and prediction window in the two prediction scenarios; *T*[0] and *T*[*e*] denote the starting and ending times of an encounter or clinical visit.

For this SAH mortality prediction project, we need to prepare six datasets, i.e., three cases for each of the two scenarios:

*   Prediction with the first 24&#160;hours’ EHR records after admission
    
*   Prediction with the first 48&#160;hours’ EHR records after admission
    
*   Prediction with the first 72&#160;hours’ EHR records after admission
    
*   Prediction with up to last 24&#160;hours’ EHR data before discharge or death
    
*   Prediction with up to last 48&#160;hours’ EHR data before discharge or death
    
*   Prediction with up to last 72&#160;hours’ EHR data before discharge or death
    

Denote *R*[*t*] as the time of records that were used for prediction, *V*[*t*]as the time that the first vasopressor was assigned, *T*[0] as the SAH visit starting time, and *T*[*e*] as the SAH visit ending time. The records that were used for SAH mortality prediction satisfied the following three conditions in Scenario 1, where the threshold was 24, 48, or 72&#160;hours respectively in this case:

*   *T*[0] ≤ *R*[*t*] ≤ *T*[0] + *t**h**r**e**s**h**o**l**d*
    
*   *T*[0] ≤ *V*[*t*] ≤ *T*[0] + *t**h**r**e**s**h**o**l**d*
    
*   *T*[*e*] − *T*[0] > *t**h**r**e**s**h**o**l**d*
    

In Scenario 2, the records that were used for SAH mortality prediction satisfied the following two conditions, where the threshold was also set as 24, 48, and 72&#160;hours respectively in this case:

*   *T*[0] ≤ *R*[*t*] ≤ *T*[*e*] − *t**h**r**e**s**h**o**l**d*
    
*   *T*[0] ≤ *V*[*t*] ≤ *T*[*e*] − *t**h**r**e**s**h**o**l**d*
    

In the EHR database, the variables from medication, lab test, clinical event, and procedure tables have timestamps, from which we could determine whether a variable was measured within the observational window. Thus, these variables could be considered as candidate predictors for mortality. [Table 5.4](#ch05.xhtml#table5_4) shows the sample size (the number of patients) available for different cases for the two scenarios after data preparation.

**Table 5.4** Sample Size for Different Prediction Cases

| **Scenarios** || **Prediction Cases** || **Sample Size** |
| --- | --- | --- |
| Scenario 1 || Predict with first 24 hrs || 1810 |
| --- | --- | --- |
| Predict with first 48 hrs || 2356 ||  |
| Predict with first 72 hrs || 2376 ||  |
| Scenario 2 || Predict for next 24 hrs || 3958 |
| Predict for next 48 hrs || 3527 ||  |
| Predict for next 72 hrs || 3272 ||  |

The sample size was 1810 for the first case for Scenario 1, using the first 24&#160;hours’ EHR data to predict SAH mortality. Note that we had 4603 patients after the cohort refining step in [Section 5.3.6](#ch05.xhtml#sec5_003_006). A total of 2793 (61%) patients were excluded from this case. This is because the requirements of eligibility for a patient to be included in this case were: 1) the patient’s records or data should be longer than 24&#160;hours (patients who died or were discharged within 24&#160;hours of admission were excluded), and 2) the vasopressor was administered for the patient after 24&#160;hours of admission (see the three conditions in Scenario 1 above). This also explains why the sample size was larger when the observation window was bigger for different prediction cases.

For a particular project, preparing the analysis data in different ways with multiple versions may be necessary. Sometimes, the data may need to be prepared for different cases or scenarios, including for the purpose of sensitivity analysis. Here we just provided some examples to illustrate this data preparation principle.

## ![image](images/inline1_1.jpg)  
5.4 Data Processing/Preparation Errors and Pitfalls with Solutions

Data processing and preparation, like data re-organization, exploration, checking, further data or subject screening, and cohort refining, are project-specific. They are time consuming but essential for any data analysis projects, especially for the projects of secondary analysis of EHR data. In this case, investigators are not involved in the data collection process and the learning curve is usually steeper for the investigators, particularly for data scientists, to get familiar with a specific EHR database. Data processing and preparation errors are not avoidable. We summarize the errors and pitfalls that we have encountered and learned from our experience with a data processing and preparation project based on a large EHR database as follows:

*   In the medication table, the generic names of medications are mixed with lower and capital letter cases, which need to be unified and cleaned before further data cleaning, processing and preparation.
    
*   For some projects or studies, it is required to extract the data based on the inclusion/exclusion criteria related to “encounters,” which is defined as an interaction between a patient and healthcare provider(s) for the purpose of providing healthcare service(s) or assessing the health status of a patient. However, the multiple encounters for a patient may not be clearly separated in the variable of time. It is quite common that two encounters are overlapping or very close to each other. In this case, it is confusing to consider these two encounters as “two interactions” between health providers and patients. Thus, it is necessary to process and clean the encounter IDs appropriately based on project-specific needs. For example, in the SAH project, we combined the overlapping encounters or closely timed encounters into a bigger encounter or a clinical visit based on the 24-hour rule (see [Section 5.3.4](#ch05.xhtml#sec5_003_004) for details).
    
*   Some of the records, including medications, lab tests and procedures, were ordered but were later canceled, all these canceled records should be removed from the analysis. For example, in the medication table of the EHR database that we are working with, we used the “order status” to filter out the canceled orders. We removed the medications with order status ID=2 or 14, which indicated as “canceled medication orders”. In addition, we used the “consumed quantity” of a medication to filter out the medications with the consumed quantity labeled as zero. The consumed quantity can be calculated as the charge quantity minus the credit quantity. It is very important to remove the canceled medications for a project with a focus on treatment evaluations. Similarly, in the lab procedure table, we used the lab “cancellation time” to filter out the canceled order for lab procedures. If the lab cancellation time is a valid time, we removed the corresponding lab record from downstream data analysis.
    
*   Although the interpretation of prediction results from a black-box machine learning model may not be easy and feasible, we still need to interpret the results for many EHR data analysis projects. Thus, it is important to name the variables and predictors from different EHR tables appropriately during the data preparation step so that we could conveniently find the description of these variables and predictors for result interpretation. For example, the variables from different EHR tables such as the diagnosis table, medication table, procedure table, lab procedure table, and clinical event table are usually labeled by coded IDs (the unique identifier of a variable in each table), which require researchers to map to the description of the variables via a vocabulary dictionary. When we combine these variables from different EHR tables to prepare the data for final data analysis and modeling, we may need to rename these variables (or IDs) so that we can easily identify which table a variable comes from for later interpretation purposes. For simplicity, we could just rename these variables or IDs by adding an appropriate “prefix” such as DIAG\_\*\*\*\*, MED\_\*\*\*\*, PROC\_\*\*\*\*, LAB\_\*\*\*\*, and CLIN\_\*\*\*\* (where \*\*\*\* indicates the original names or IDs of the variables from each table), for the variables from diagnosis, medication, procedure, lab procedure, and clinical event tables respectively. In this way, we can easily identify or map the variable with its description from different EHR tables.
    
*   There is no timestamp for diagnosis codes in the disease diagnosis table. However, some disease diagnoses are labeled as the encounter admission or discharge. Thus, the encounter admission or discharge time can be used to approximate the disease diagnosis time.
    

These pitfalls and lessons that we have learned so far are still quite limited. We expect to expand this list in the future. Based on our experience, we realize that data processing and preparation need to be iteratively performed with other steps, including data extraction, cleaning and data analysis steps. The data processing and preparation are tedious and sometimes need to be done repeatedly several times. Thus, it is critical and important to document and track all the changes during the data processing and preparation steps, so that the reproducibility and scientific rigors of the secondary analysis of the EHR data can be guaranteed.

## ![image](images/inline1_1.jpg)  
5.5 Data Pre-Processing and Preparation Report

A detailed report is important and necessary to document and track all the data processing procedures, methods, changes and justifications during the data processing and preparation step. We developed a template for data pre-processing and data preparation reporting for the EHR project based on our experience. A data pre-processing and preparation report should include several key components, such as the background and the objectives of the EHR project, a summary of data extraction and data cleaning steps, data pre-processing and preparation details, the prepared data files with descriptions and computer codes for data processing and preparation. The report template we designed is as follows.

A template for data pre-processing and preparation report

**EHR Project: Title of the Project  
Data Pre-Processing and Preparation Report  
Version 1.0**

Your name  
Affiliation  
Date

### Background and the Objectives of the Project

Data pre-processing and preparation are project-specific and different objectives may also require to process and prepare the data in different ways. Thus, it is important to provide a clear description of the project background and objectives. Sometimes it is also necessary to formulate the scientific or clinical objectives into a statistical framework so that we could justify our data processing and preparation procedures and methods appropriately based on different data analysis methods for different objectives.

### Data Extraction and Data Cleaning Summary

Data processing and preparation usually are performed after data extraction and data cleaning steps. To summarize the data extraction and data cleaning results and key points, including inclusion/exclusion criteria for data extraction, is important to preclude the data processing and preparation step. It is essential to specify which version of the cleaned data (from the data cleaning step) is used for data processing and preparation. It may reference the report of the data extraction and data cleaning steps (if available) for more details.

### Data Pre-Processing and Preparation

Need to describe each step of data pre-processing and preparation in detail so that the final version of the prepared data is reproducible. If multiple versions of the datasets are prepared for different analysis methods for different objectives, this should also be well documented here. Here is an example of what may be included:

1.  Define the encounter starting and ending time
    
2.  Encounter combination
    
3.  Label the outcome if applicable
    
4.  Label the treatment or exposure if needed
    
5.  Cohort screening or refining
    
6.  Leakage detection if needed
    
7.  Variable encoding
    
8.  Feature extraction and dimension reduction
    
9.  Final cohort summary statistics
    
    *   Number of patients
        
    *   Number of encounters per patient
        
    *   Duration of the clinical visit
        
    *   Mortality rate
        
    *   Race distribution and disease prevalence distribution
        
    *   Gender distribution and disease prevalence distribution
        
    *   Age distribution and disease prevalence distribution
        
    *   Number of variables per medical table, i.e., number of medications, diagnoses or procedures
        
    *   Patient type description distribution (inpatient or outpatient) and by calendar year
        
    *   Disease-specific importance clinical variables summary
        

### Prepared Data Files

Data\_file 1: Description

Data\_file 2: Description

……

### Data Processing and Preparation Codes

Since data processing and preparation may need to be performed many times, iteratively with other steps, it is critical to have good version control so that the latest version of the prepared data are used by all the investigators or data analysts. We also suggest that the report should include all the computer codes for data processing and preparation with appropriate documentation in order for another person to easily repeat and reproduce the prepared data. This is also essential for others to reuse the prepared data for different purposes.

## ![image](images/inline1_1.jpg)  
5.6 Summary

In this chapter, we have discussed the EHR data pre-processing and preparation principles and demonstrated some methods using practical examples based on our experience in processing and preparing EHR data for several EHR data analysis projects. Here we provided a clear definition and specified the tasks that must be done in the data pre-processing step (See [Section 5.1](#ch05.xhtml#sec5_1)), which is important to facilitate better communication among the team members and to the general community at large. Some of the EHR data pre-processing tasks such as missing data imputation, feature extraction and data dimension reduction may need sophisticated statistical methods and advanced computational techniques. Data pre-processing is usually performed after the data cleaning step and before the data preparation step, but it is also quite often that these steps need to be iteratively performed.

After the data pre-processing is done, we need to prepare the data for different data analysis purposes. The data preparation step may need to undergo more project-specific and purpose-driven data cleaning, variable or subject grouping, subject labeling or relabeling, data analysis window specification, and data formatting. This step also needs to be iteratively performed with other steps, including steps of data cleaning, pre-processing and data analysis. The data preparation step does not require complicated statistical methods, but it requires more knowledge and familiarity with the EHR system and the scientific or clinical question. The person who performs the data preparation should also understand the next step, i.e., the data analysis very well. He/she may need to make efforts to understand the data analysis methods to prepare the data appropriately in the right format. Ideally, the same person or the same group of people should do both data preparation and data analysis.

It is important to clearly define and distinguish between the data pre-processing/processing and data preparation steps for EHR data analysis projects in order to better manage the project and efficiently communicate among team members since the EHR data analysis project usually requires close collaborations of a big multidisciplinary team. This chapter is written based on our initial attempt to harness the big EHR data for scientific discoveries. Both the data pre-processing and data preparation steps are project-specific and need to be purpose-driven. We expect that more contents and tasks could be added to these two steps, and more principles and methods could be developed in the future after more experiences are accumulated from more EHR projects.

### References

Abdi, Hervé, and Lynne J. Williams. 2010. “Principal component analysis. *Wiley Interdisciplinary Reviews: Computational Statistics* **2** ((4)): 433–459.

Andrieu, Christophe, Nando De Freitas, Arnaud Doucet, and Michael I. Jordan. 2003. An introduction to MCMC for machine learning. *Machine Learning* **50** ((1–2)): 5–43.

Azur, Melissa J., Elizabeth A. Stuart, Constantine Frangakis, and Philip J. Leaf. 2011. Multiple imputation by chained equations: what is it and how does it work? *International Journal of Methods in Psychiatric Research* **20** ((1)): 40–49.

Banda, Juan M., Martin Seneviratne, Tina Hernandez-Boussard, and Nigam H. Shah. 2018. Advances in electronic phenotyping: From rule-based definitions to machine learning models. *Annual Review of Biomedical Data Science* **1**, 53–68.

Choi, Edward, Mohammad Taha, Bahadori, Elizabeth, Searles, Catherine Coffey, Michael Thompson, James, Bost, Javier, Tejedor-Sojo, and Jimeng, Sun. 2016. ”Multi-layer representation learning for medical concepts. *Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*. pp. 1495–1504

Choi, Edward, Mohammad Taha, Bahadori, Jimeng, Sun, Joshua, Kulas, Andy, Schuetz, and Walter, Stewart. 2016. Retain: An interpretable predictive model for healthcare using reverse time attention mechanism. *Advances in Neural Information Processing Systems*: 3504–3512

Choi, Edward, Andy Schuetz, Walter F. Stewart, and Jimeng Sun. 2016a. “Medical concept representation learning from electronic health records and its application on heart failure prediction. *arXiv preprint arXiv:1602.03686*.

Choi, Edward, Andy Schuetz, Walter F. Stewart, and Jimeng Sun. 2016b. Using recurrent neural network models for early detection of heart failure onset. *Journal of the American Medical Informatics Association* **24** ((2)), 361–370.

Connolly Jr, E. Sander, Alejandro A. Rabinstein, J. Ricardo Carhuapoma, Colin P. Derdeyn, Jacques Dion, Randall T. Higashida, Brian L. Hoh, Catherine J. Kirkness, Andrew M. Naidech, and Christopher S. Ogilvy. 2012. Guidelines for the management of aneurysmal subarachnoid hemorrhage: a guideline for healthcare professionals from the American Heart Association/American Stroke Association. *Stroke* **43** ((6)): 1711–1737.

 Dempster, Arthur P., Nan M. Laird, and Donald B. Rubin. 1977. Maximum likelihood from incomplete data vi the EM algorithm. *Journal of the Royal Statistical Society: Series B (Methodological)* **39** ((1)): 1–22.

Denny, Joshua C., Lisa Bastarache, Marylyn D. Ritchie, Robert J. Carroll, Raquel Zink, Jonathan D. Mosley, Julie R. Field, Jill M. Pulley, Andrea H. Ramirez, and Erica Bowton. 2013. Systematic comparison of phenome-wide association study of electronic medical record data and genome-wide association study data. *Nature Biotechnology* **31** ((12)): 1102.

Glicksberg, Benjamin S., Riccardo Miotto, Kipp W. Johnson, Khader Shameer, Li Li, Rong Chen, and Joel T. Dudley. 2018. Automated disease cohort selection using word embeddings from electronic health records. *PSB*. pp.  145–156

Gronsbell, Jessica, Jessica Minnier, Sheng Yu, Katherine Liao, and Tianxi Cai. 2019. Automated feature selection of predictors in electronic medical records data. *Biometrics* **75** ((1)): 268–277.

Gurwitz, Jerry H., David J. Magid, David H. Smith, Robert J. Goldberg, David D. McManus, Larry A. Allen, Jane S. Saczynski, Micah L. Thorp, Grace Hsu, and Sue Hee Sung. 2013. Contemporary prevalence and correlates of incident heart failure with preserved ejection fraction. *The American Journal of Medicine* **126** ((5)): 393–400.

Health Level Seven, Inc. “HL7®. FHIR.”Resource Encounter-Detailed Descriptions, accessed March 2020 [https://www.hl7.org/fhir/encounter-definitions.html](https://www.hl7.org).

Hubbard, Rebecca A., Jing Huang, Joanna Harton, Arman Oganisian, Grace Choi, Levon Utidjian, Ihuoma Eneli, L. Charles Bailey, and Yong Chen. 2019. A Bayesian latent class approach for EHR-based phenotyping. *Statistics in Medicine* **38** ((1)): 74–87.

Jolliffe, Ian. 2011. *Principal Component Analysis*, New York: Springer.

Kaufman, Shachar, Saharon Rosset, Claudia Perlich, and Ori Stitelman. 2012. Leakage in data mining: Formulation, detection, and avoidance. *ACM Transactions on Knowledge Discovery from Data (TKDD)* **6** ((4)): 15.

Li, Bing. 2018. *Sufficient Dimension Reduction: Methods and Applications with R*: Boca Raton: CRC Press.

Mazumder, Rahul, Trevor Hastie, and Robert Tibshirani. 2010. Spectral regularization algorithms for learning large incomplete matrices. *Journal of Machine Learning Research* **11** ((Aug)): 2287–2322.

Mikolov, Tomas, Ilya Sutskever, Kai Chen, Greg S. Corrado, and Jeff Dean. 2013. Distributed representations of words and phrases and their compositionality. *Advances in Neural Information Processing Systems*. pp.  3111–3119

Ng, Kenney, Steven R. Steinhubl, Christopher de Filippi, Sanjoy Dey, and Walter F. Stewart. 2016. Early detection of heart failure using electronic health records: Practical implications for time before diagnosis, data diversity, data quantity, and data density. *Circulation: Cardiovascular Quality and Outcomes* **9** ((6)): 649–658.

Nisbet, Robert, John, Elder, and Gary, Miner. 2009. *Handbook of Statistical Analysis and Data Mining Applications*: Cambridge, MA: Academic Press.

Phien, Ho N., Hoang D. Tuan, Johann A. Bengua, and Minh N. Do. 2016. Efficient tensor completion: Low-rank tensor train. arXiv preprint arXiv:1601.01083.

Stekhoven, Daniel J., and Peter Bühlmann. 2012. ”MissForest—non-parametric missing value imputation for mixed-type data. *Bioinformatics* **28** ((1)): 112–118.

 Wei, Wei-Qi, Lisa A. Bastarache, Robert J. Carroll, Joy E. Marlo, Travis J. Osterman, Eric R. Gamazon, Nancy J. Cox, Dan M. Roden, and Joshua C. Denny. 2017. Evaluating phecodes, clinical classification software, and ICD-9-CM codes for phenome-wide association studies in the electronic health record. *PloS One* **12** ((7)): e0175508.

Wickham, Hadley 2014. Tidy data. *Journal of Statistical Software* **59** ((10))

Williams, George, Vahed Maroufy, Laila Rasmy, Derek Brown, Duo Yu, Hai Zhu, Yashar Talebi, Xueying Wang, Emy Thomas, Gen Zhu, Ashraf Yaseen, Hongyu Miao, Luis Leon Novelo, Degui Zhi, Stacia DeSantis, Hongjian Zhu, Jose-Miguel Yamal, David Aguilar, and Hulin Wu. 2020. Vasopressor treatment and mortality following non-traumatic subarachnoid hemorrhage: A nationwide EHR analysis. *Neurosurgical Focus* ** 48** ((5)).

Zhang, Cai-Cai, Sheng-Hua Li, Cui-Fang Zhang, and Yu Liu. 2016. Size switchable supramolecular nanoparticle based on azobenzene derivative within anionic pillar \[5\] arene. *Scientific Reports* **6**, 37014.

# [6 ](#contents.xhtml#toc1_114)  
![image](images/inline1_1.jpg)

# [Missing Data Issues in EHR](#contents.xhtml)  
               

Chenguang Zhang, Vahed Maroufy, Baojiang Chen and Hulin Wu

## ![image](images/inline1_1.jpg)  
6.1 Introduction and Overview

One consequential challenge we need to address, before using any statistical inference and prediction tools with an EHR database, is the extensive missing data problem in EHR and claims datasets. These databases comprise several tables that include disease diagnoses, medications, clinical events, lab procedures, and more, all of which become complicated when data is missing. For instance, in the Cerner database, the lab results table and clinical events table, which are two of the largest tables, have intensive missing data due to various reasons. Specifically, in the lab table, the lab procedure table may be extremely sparse because some lab results may not have been entered properly, or certain lab procedures might have been ordered for a small percentage of patients, leading to the missing value for the rest of the subjects in the database.

In addition, the clinical event table may not include the records for all the patients. For example, based on our initial assessment of the Cerner database, approximately 60% of patients did not have even a single clinical event record, though this is likely a result of Cerner not recording clinical events until 2009. The clinical event table is crucial for inferential or predictive analysis because it includes patient vital signs and potentially important clinical events related to diseases. Another problem with this database is that the longitudinal information for patients covers different spans of time depending on their hospitalization status (inpatient or outpatient). As a result, any datasets that emerged from all tables in EHR and claims databases will be extremely sparse, with a missing rate as high as 10–99%.

There are a number of inference and estimation methods in the literature that can be applied directly to common statistical predictive models even with the presence of missing data. These include a likelihood-based approach via the expectation-maximization method \[[1](#ch06.xhtml#ref6_1)\], and a Bayesian approach via MCMC method \[[2](#ch06.xhtml#ref6_2)\]. However, these methods are only capable of handling relatively small missing percentages and are computationally intensive, especially for large and high-dimensional datasets. Therefore, in this chapter we will focus on imputation approaches to generate complete data sets when missingness is relatively greater or that are computationally less demanding in EHR datasets, allowing for the application of all standard statistical and machine learning or deep learning predictive models.

In this chapter, we first give a brief review of different types of missing data mechanisms. We then review commonly used imputation methods including Multiple Imputation by Chained Equation (MICE) \[[3](#ch06.xhtml#ref6_3)\], MissForest \[[4](#ch06.xhtml#ref6_4)\], Mean and Median imputation, and some novel machine learning and deep learning applications. Finally, we will apply these methods to an example extracted from the Cerner database to illustrate the performance and efficiency of these methods.

## ![image](images/inline1_1.jpg)  
6.2 Missing Data Mechanisms

Depending on the underlying causes of missingness, we may face different types of missing data, each with a particular missing mechanism. In addition, understanding the missing mechanism is curtailed to employ the right strategy and approach for missing data imputation. This section gives a brief overview of missing data mechanisms and common existing imputation methods in the literature.

Missing data mechanisms can be divided into three types: missing completely at random (MCAR), missing at random (MAR), and missing not at random (MNAR). MCAR, as the phrase itself suggests, refers to the situation when missing data is a random subset of the complete dataset \[[5](#ch06.xhtml#ref6_5)\]. That is, the missing data mechanism is independent of the missing data and the observed data. A typical example of MCAR is when a questionnaire is randomly lost or the experiment sample results are lost by accident. MAR occurs when the missing data depends on the observed data. For example, only females may have the tests for diagnosing breast cancer and males have the related test results for prostate cancers. Thus, the missingness depends on the observed variable gender. MNAR, or nonignorable missing, occurs when the missing trend depends on the unobserved data itself. For example, a person may decline to answer controversial or uncomfortable questions, such as individuals from low socioeconomic backgrounds not answering questions regarding income.

However, in practice, since EHR data always includes a large number of variables, we cannot identify missing data mechanisms without prior and follow-up information from patients \[[6](#ch06.xhtml#ref6_6)\]. In general, we can assume that EHR data has primarily MAR data, because there are thousands of variables available for each patient, and there is likely observed information that is highly correlated with the missing data. Fortunately, MAR can be imputed with simple and naïve imputations methods such as overall mean, single and multiple imputation methods \[[7](#ch06.xhtml#ref6_7)\].

## ![image](images/inline1_1.jpg)  
6.3 Methods for Incomplete EHR Data

### 6.3.1 Naïve Method

Naïve analysis methods include the “Complete-Case” and “Available-Data” approaches. In the complete-case method, subjects with any missing information are dropped from the dataset. This method is simple and efficient when the missing percentage is small, and the missing data is MCAR. If the missing data is not MCAR, this method will lead to bias in the statistical inference and prediction models of interest. Since EHR databases are extremely high dimensional, and the missing type is often not MCAR, this method may not be applicable to EHR data.

The available-data method is commonly used in longitudinal data analysis with missing observations and when missing data percentages differ from variable to variable because it uses the data available to impute missing values. For example, if a subject’s observation is missing at wave 2, wave 3, but observed at wave 1, wave 4, then we can find the missing data with the wave 1 and wave 4 data, using Generalized Estimating Equations (GEE) \[[8](#ch06.xhtml#ref6_8)\] \[[9](#ch06.xhtml#ref6_9)\] or Generalized Linear Mixed Models (GLMM) methods. Clearly these methods are only suitable for simple univariate analysis and will not be applicable to high-dimensional predictive modeling and regression analyses using EHR data.

### 6.3.2 Imputation Using Statistical Models

If we can assume that any missing data is MAR, observed data is utilized to estimate or predict missing values in the data set, often, by applying naïve simple descriptive statistics, linear or non-linear statistical models and machine learning models. Approaches include single imputation and multiple imputation methods; in the latter, we take the prediction variance into account by predicting a missing value m (>1) times. Methods used for imputation can also be categorized into parametric models, such as generalized linear models, and non-parametric models, such as kernel estimation models. Parametric models include linear regression, logistic regression, and regression models for count and multinomial data, which are selected according to the type of the missing value.

In the rest of this section, we briefly describe each of the imputation methods along with some of their advantages and disadvantages.

I. Single Imputation

Single imputation is computationally less expensive than multiple imputation, because it only uses one iteration for imputing missing values. However, using this method involves a risk of underestimating variance, because it assumes that the true model is available \[[10](#ch06.xhtml#ref6_10)\]. We describe different approaches for single imputations as described below.

a. Mean (Median) Imputation

The easiest way of a single imputation method is just to replace the missing units with the descriptive summary such as the mean, median or quantiles.

*   Advantages  
    It is straightforward to implement and can be used as long as there is at least one observation available for each variable.
    
*   Disadvantages  
    The method ignores the relationship between different variables; If the missing rate is high in a specific variable, the imputation might be biased.
    
*   In EHR dataset
    

This is the simplest imputation method and can be one of the first methods to be applied to an EHR dataset with missing data (often with high percentages). The method should be compared with more complex imputation methods to explore the extent of bias and when results are consistent, the simpler approach may be used.

b. Last Observation Carried Forward (LOCF)

This method, also sometimes called “last value carried forward”, uses the most recently observed response for the individual as the imputed value. This method is commonly used in dealing with incomplete longitudinal data.

*   Advantages
    
    Fewer subjects are dropped from the analysis since it uses the most recent non-missing value to fill in the blank cell and allows the use of a single endpoint to represent the data points over time.
    
*   Disadvantages
    
    This approach is not recommended as the primary method for dealing with missing data, as the required assumptions rarely hold. For instance, one assumption is that the subject’s result will keep the same trend after dropping out, an assumption we have no tool to examine or validate directly \[[11](#ch06.xhtml#ref6_11)\].
    
*   In EHR dataset
    

This method can be useful for within-subject data imputation for longitudinal variables. However, time stamps for EHR data are not standard and they themselves need a clear strategy to process it (See Chapter 4). For example, the last available blood pressure measurement can date back to an encounter one year earlier under a critical hospitalization. This measurement would not be a reasonable candidate for imputing a current missing blood pressure measurement within a regular checkup visit.

c. Other Imputation Methods

*Using Information from Related Observations:*

This method uses related observations to roughly impute the missing information. For example, if the missing information is about the children’s father, we would fill in the blank cells with the mother’s information. This is a plausible strategy, although these imputations may propagate measurement error, because we can reasonably assume a mother and father’s information, like lifestyle and habits, would be somehow similar.

Summary of Single Imputation Method:

*   Advantages  
    Single imputation methods can be easily understood and used.
    
*   Disadvantages  
    Since the imputed values are treated as known values, the model will underestimate the variance whether we know why the values are missing or not.
    
*   In EHR dataset
    

Single imputation models are the simplest methods that can be used in high dimensional and high missing rate EHR datasets. Although they have disadvantages, we can use their results as a reference in comparisons.

II. Multiple Imputation

Multiple imputation generates multiple single-imputed data sets based on different estimated underlying distributions \[[2,12](#ch06.xhtml#ref6_2)\]. Each imputed version can be treated as a complete dataset to which we can apply the standard statistical methods. If we assume the missing data mechanism is MAR, each estimate would be unbiased, so we can simply take the average of the estimates and get the pooled estimate of the association. The variance of the pooled estimate can be obtained using Rubin’s formula \[[2](#ch06.xhtml#ref6_2)\], discussed in detail in the following sections. Multiple imputation methods incorporate both the variance of sampling and the uncertainty about the regression parameters within the models employed for imputation.

Basic Procedure:

STEP 1: Generate m (>1) complete data sets.  
STEP 2: Apply the model selected to all m complete data sets.  
STEP 3: Combine and pool the results from m complete data sets.

 

In the rest of this section, we describe two common methods of multiple imputation methods, routine multivariate imputation and iterative regression imputation, along with their advantages and disadvantages.

a. Routine Multivariate Imputation

This method uses multivariate regression models to impute the missing values and can be used to impute missing values in multiple variables \[[13](#ch06.xhtml#ref6_13)\]. To build the multivariate model, we assume a distribution function for each variable, usually, a multivariate normal or t distribution for continuous outcomes, binomial and multinomial distribution for binary and categorical outcomes, and Poisson distribution for count data.

*   Advantages  
    This method is simple to implement and easy to interpret, and a good starting point for further imputation.
    
*   Disadvantages  
    It is often difficult to build a reasonable multivariate regression model.
    
*   In EHR Dataset
    

Since EHR data often have a large number of variables, assuming MAR is quite reasonable. Hence, this method can be a safe choice. However, because of the large missing rates in EHR data, finding and fitting a reasonable multivariate model is a significant challenge.

*   b. Iterative Regression Imputation
    

This method fits regression models iteratively for predicting missing observations taking each variable with missing values as the outcome at a time. It assumes variables *Y*[1], *Y*[2]…*Y*[*k*] are subject to missingness, and a design matrix X that includes all variables that are fully observed. Initially, it imputes *Y*[1], *Y*[2]…*Y*[*k*] one by one each using a set of randomly selected columns of X; then, it imputes each *Y*[*j*], using {*Y*[*i*]*;* *i* ≠ *j* & *X* } until we reach a complete dataset.

*   Advantages  
    Since it uses a univariate response model in each step, instead of a high-dimensional multivariate response model, this method is much easier to understand and interpret; and it is capable of allowing for interactions, compared to the earlier naïve methods.
    
*   Disadvantages  
    Each univariate model must be reasonable, and all models must be consistent.
    
*   In EHR dataset
    

While this method can be used in EHR datasets, it may not be computationally feasible or applicable to most EHR datasets, since they often have thousands of variables with missing values and no variable completely observed.

*   III. Statistical Models
    

To apply statistical regression and predictive models for imputing missing data, several assumptions need to be satisfied. First, the missing mechanism should be MAR, which means the missingness only depends on observed data; Second, the parameter of the data model and the parameter of the model for the missing data indicators are distinct. The regression methods for missing imputation include both parametric and nonparametric models, each described briefly below.

a. Basic Procedure of Parametric Model

Multiple Imputation by Chain Equation (MICE) is the most commonly used parametric method for imputing missing data. It uses multiple regression models iteratively to impute missing values for various variables that can be of different types (such as numerical, categorical, and count data). To impute the missing values in each variable, a regression model (a member of the Generalized Linear Models) is built according to the type of the selected response. Specifically, for continuous, count or binary response, MICE would use, respectively, an ordinary linear regression, log-linear or a logistic regression model. To build each imputation regression model, the set of covariates can be the other existing variables in the dataset or a selected list of variables based on their correlation with the outcome. We can summarize the MICE procedure to impute variable *Y*[*j*], assumed to be continuous in this example, as follows:

STEP 1: Fit a model

*E*(*Y*[*j*]|*Y*[1],…,*Y*[*j* − 1]) = *β*[0] + *β*[1]*Y*[1] + … + *β*[*j* − 1]*Y*[*j* − 1], *j* = 2, …, *p*,

using the ordinary least square (OLS) to get the estimate for the coefficient *β*, denoted as *β̂*, and covariance matrix of *β̂*,*σ̂*[*j*]²*V*[*j*], where *σ̂*[*j*]² is an estimate of the residual variance.

STEP 2: Simulate new regression parameters *β*[ \* 0], …, *β*[ \* (*j* − 1)] and *σ̂*[ \* *j*]² from the posterior predictive distribution of the parameters *β̂* and *σ̂*[*j*]².

STEP 3: Impute the missing values of *Y*[*j*] using

*β*[ \* 0] + *β*[ \* 1]*Y*[1] + … + *β*[ \* (*j* − 1)]*Y*[(*j* − 1)] + *z*[*i*]*σ*[ \* *j*]

where *Y*[1], *Y*[2], …, *Y*[*j* − 1] are the covariate values of the first *j&#160;*−&#160;1 variables and *z*[*i*] is a random value from a standard normal distribution.

Repeat steps 1 to 3 until all of the missing values are imputed. The multiple imputations are obtained by repeating these steps *m* times.

When the response is discrete, we can use generalized linear models instead of the linear regression models.

b. Basic Procedure of Nonparametric Model

STEP 1: Create an indicator variable *R*[*j*] = *I*(*Y*[*j*]*i**s* *o**b**s**e**r**v**e**d*)

STEP 2: Fit a logistic regression model

*l**o**g**i**t*(*p*[*j*]) = *β*[0] + *β*[1]*Y*[1] + … + *β*[*j* − 1]*Y*[*j* − 1]

where *p*[*j*] = *P*(*R*[*j*]\=0|*Y*[1],*Y*[2],…,*Y*[*j* − 1])

STEP 3: Create a propensity score (i.e., the probability that it is missing given other variables) for each observation to estimate

STEP 4: Divide the observations into a fixed number of groups (typically five) based on these propensity scores

STEP 5: Apply an approximate Bayesian bootstrap imputation to each group, in group *k*, suppose that *Y*[*o**b**s*] denotes the *n*[1] observations with non-missing *Y*[*j*] values and *Y*[*m**i**s*] denotes the *n*[0] observations with missing *Y*[*j*]. The approximate Bayesian bootstrap imputation first draws *n*[1] observations randomly with replacement from *Y*[*o**b**s*] to create a new data set *Y*^(\*)[*o**b**s*]. This is a nonparametric analog of drawing parameters from the posterior predictive distribution of the parameters. The process then draws the *n*[0] values for *Y*[*m**i**s*] randomly with a replacement from *Y*^(\*)[*o**b**s*]. \[[14](#ch06.xhtml#ref6_14)\].

Steps 1–5 are repeated sequentially for each variable with missing values.

*   Advantages  
    These methods are more flexible and require fewer assumptions than the parametric approaches such as linear models or GLMs to characterizes the relationship among the variables.
    
*   Disadvantages  
    When the dataset is high dimensional, the parametric method may require the estimation of many parameters, which may result in a lack of convergence.
    
*   In EHR Dataset
    

The nonparametric models can be used in EHR datasets. For example, we can apply commonly-used tree-based methods. The dependence among the clinical records may be more complicated, which cannot be modeled by just using linear parametric data; under this situation, nonparametric methods are useful. We will discuss the details in the following sections.

*   c. Combine Estimates from Multiple Imputations
    

Suppose *Q̂*[*i*] and *Ŵ*[*i*] (*i*&#160;=&#160;1, …, m) represent the point and the covariance matrix estimates for a p-dimensional parameter *Q* resulted from iteration *i*. Then the combined point estimate for *Q*, is $\\overline{Q} = \\frac{1}{m}\\sum\\limits\_{i = 1}^{m}{\\widehat{Q}}\_{i}$, and the pooled variance matrix is given by $T\_{0} = \\overline{W} + \\left( 1 + \\frac{1}{m} \\right)B$, where $\\overline{W} = \\frac{1}{m}\\sum\\limits\_{i = 1}^{m}{\\widehat{W}}\_{i}$ is the within-imputation variance, and $B = \\frac{1}{m - 1}\\sum\\limits\_{i = 1}^{m}{\\left( {\\widehat{Q}}\_{i} - \\overline{Q} \\right)\\left( {\\widehat{Q}}\_{i} - \\overline{Q} \\right)^{\\prime}}$ is the between-imputation variance.

### 6.3.3 Machine Learning and Deep Learning Models

*   1\. Tree-Based Methods
    

Decision tree learning is a method in predictive modeling, which uses decision trees to make decisions from observations to target values. Classification and regression trees can be used for statistical prediction without assuming a parametric regression model \[[15](#ch06.xhtml#ref6_15)\]. A tree is often created by clustering the subjects (response values) in a binary fashion according to covariates. This process is iterative wherein, at each iteration, a covariate is selected according to an objective function to cluster the response values into multiple (often two) clusters. Each leaf then represents the cluster of responses for a configuration of multiple covariates.

An example of a classification tree of open-source data “IRIS” \[[16,17](#ch06.xhtml#ref6_17)\] was shown in [Figure 6.1](#ch06.xhtml#fig6_1). The scatter plot (top panel) shows three species of iris flower, and (at the bottom) variables like petal width and sepal width were used to iteratively build the tree.

![Figure 6.1 Scatter plot and classification tree example on IRIS data.](images/fig6_1.jpg)

**Figure 6.1**  
Scatter plot and classification tree example on IRIS data.

A tree is a regression tree if the response variable is continuous, and is a classification tree if the response variable is categorical. The theory of tree-based models is to identify nodes with response homogeneity, separating the sample according to the values of predictors that generate the largest reduction in the variability of the response variable. Assuming that the outcome variable is *Y* and the vector of predictors is *X*, then the parameters in the model are *T* and *θ*, where *T* is the tree with *R* nodes or leaves. Thus, to predict the outcome category Y, the vector of parameters of the model can be represented as *θ* = {*θ*[1], …, *θ*[*R*]}, where *θ**i* a parameter for each leaf *i*. If the predictor *X* is in the leaf *r*, then *Y**|**X* is distributed based on probability *p*(*Y**|**θ*[*r*]) and the probability will be used to determine the predicted outcome.

*   Advantages  
    Tree-based imputation has become popular because it is a non-parametric method and does not require us to make any assumption about the distribution of data as we would need in parametric models. Also, it does not require a specified data structure or variable type. Therefore, we do not have to worry about model misspecification and outliers, because nonparametric models can have robust results even with outliers.
    
*   Disadvantages  
    Decision trees do not work well if datasets only have smooth boundaries and if data is not highly correlated. In addition, their flexibility translates into higher variance.
    
*   In EHR datasets
    

Since EHR datasets always contain mixed data types, including continuous or categorical variables, and the dependence among variables might often be miss-specified by a pre-assumed parametric model, we can consider using tree-based imputation methods to analyze EHR data.

*   II. Deep Learning Methods in Imputation
    

The traditional imputation methods described in Sections 1 and 2 have mostly been developed to apply to traditional clinical trial datasets which may not be high dimensional or have high missing rates. In EHR data sets, although traditional imputation has systematic and mature computing methods ready to be used, they may generate noise in the imputed result. Machine learning is an application of artificial intelligence, in which a system automatically gains new knowledge and improves by learning from experience. Deep learning is a subset of machine learning, one that seeks to mimic how the human brain processes data and learns new materials. They are extremely popular for prediction and recently have been applied to the missing data problems.

*   a. Autoencoder  
      
    Autoencoders are a specific type of neural networks \[[18](#ch06.xhtml#ref6_18)\] in which the input and the output are the same. They encode the input into a lower-dimensional code and use this representation to reconstruct the output. The basic idea behind an autoencoder is to have an AI learn from the input layers, wherein the number of hidden layers would be smaller than the number of input layers, forcing the model to compress knowledge from the input. Also, if there are some structures in the input data, the AI will learn the structure when we need to compress the input. However, since it is a process of learning, we need to consider the trade-off between accurately building the reconstruction and simply memorizing or overfitting the training data. The model will include two parts: 1) a loss function to let the model learn from the input; and 2) a regularization function to avoid memorizing the training data. A scaling parameter placed before the regularization function adjusts this trade-off.  
      
    *L*(*x*,*x̂*) + *r**e**g**u**l**a**r**i**z**a**t**i**o**n*  
      
    where *x* are the original input, and the *x̂* are the output data.
    
    Beaulieu-Jones, et al., implemented the autoencoder method for EHR missing imputation \[[19](#ch06.xhtml#ref6_19)\]. They used a tool named modified binary cross-entropy cost between reconstructed layer z and input x \[[20](#ch06.xhtml#ref6_20)\]. They used an indicator m, with value 1 when data is present and 0 when it is missing. Then, the average cost per present feature was estimated as follows  
      
    $\\mathit{cost} = - \\sum\\limits\_{k = 1}^{d}{\\left\\lbrack {x\_{k}\\log\\left( z\_{k} \\right)m\_{k} + \\left( {1 - x\_{k}} \\right)\\log\\left( {1 - z\_{k}} \\right)m\_{k}} \\right\\rbrack/\\mathit{count}\\left( m \\right).}$
    
    If the new minimum cost was not reached in 100 epochs, the training stopped.
    
    Beaulieu-Jones, et al. also compared multi-layer autoencoders with dropout with other imputation methods on spiked-in missing data, KNN, mean, median, SI and SVD, and experiments designed to be both MCAR and MNAR. The autoencoder with dropout showed the most robust imputation performance. Although these methods seem to be good solutions, they still have some problems. Autoencoders are computationally intensive, the computation time linearly increases with the number of observations, and their conclusions are limited by the sample size and the data structure.
    
*     
    b. Natural Language Processing (NLP)  
      
    Another branch of AI, Natural Language Processing (NLP) attempts to make computers to understand human language. Most NLP algorithms rely on machine learning methods to derive the rules of human languages. NLP is often referred to as a black box, but it is important to understand how it works. Usually, NLP identifies and extracts the natural language rules, then coverts the natural languages to computer language using syntactic analysis and semantic analysis. Syntax refers to the rules like word order and grammar that make the sentences convey consistent meanings, and NLP uses syntactic analysis to assess the natural language using grammatical rules. Semantics refers to the understanding of the components of a natural language sentence, and the problem of semantics analysis has not been completely solved yet.
    
    As an example of how NLP is used in EHR data, the Cleveland Clinic EHR system, grants patients access through a portal called “My Chart”. “MyChart” lets patients view medical records, schedule appointments, receive reminders, and freely write messages to their physicians and other members of their healthcare team \[[21](#ch06.xhtml#ref6_21)\]. Even though it may be considered a novel application of missing data solutions, we imagine that these text notes could provide some reliable information that may be missing from other parts of the patients’ records. Since NLP is still a difficult problem for computers because of the nature of human language, it may take some time before we can build NLP that reaches a comprehensive understanding of the human language, which is the ultimate goal of NLP.
    
*     
    c. Generative Adversarial Nets (GAN)  
      
    Generative Adversarial Nets (GAN) is a novel method that can be used to impute missing data. GAN was mentioned first time by Ian J. Goodfellow in his paper Generative Adversarial Nets \[[22](#ch06.xhtml#ref6_22)\] in 2014. GAN has since been used in image or audio generation. GAN is a method to estimate generative models via an adversarial process, including two models - generator model G, to capture the data distribution, and discriminator model D, which estimates the probability that a sample came from the training data rather than G. The process in the training procedure for G is to maximize the probability of D making a mistake \[[22](#ch06.xhtml#ref6_22)\], after which the generative network will learn to map data points from a latent space to some distribution, and the discriminative network will learn to distinguish these products from the true data distribution. For missing imputation using GAN, the generator imputes the missing values given the information learned from the observed values, and the discriminator aims at identifying observed and imputed values in a completed vector. \[[23](#ch06.xhtml#ref6_23)\]
    
    Although GAN is a novel method and especially new for dealing with missing data, several researchers have already experimented with applying GAN in real-world data and made comparisons with other existing imputation methods. An example of using GAN in missing data will be introduced in the next paragraph.
    
    Jinsung Yoon et al. \[[23](#ch06.xhtml#ref6_23)\] used GAN on various UCI datasets, evaluated its performances in various settings, and against other imputation algorithms, using Root Mean Square Error (RMSE) and area under the receiver operating characteristic curve (AUC). They call the method Generative Adversarial Imputation Nets (GAIN). Their results showed that, although RMSE increases with missing rate increases GAIN is more robust than MissForest and Autoencoder; and with the number of samples increase, the performance of GAIN improves. GAIN was also consistently implemented to datasets with various numbers of feature dimensions, which resolved the performance problem that MissForest faced when the number of feature dimensions was small. GAIN also achieved higher AUC values than the other two methods, particularly when the missing rate was high. Yonghong Luo et al. also used GAN in a comparative study and \[[24](#ch06.xhtml#ref6_24)\] showed that GAN has a better performance than the other three methods, (“filling last value”, “filling zero value” and “filling mean value”).
    
    In summary, GAN can manage complicated data structures, such as EHR datasets. There are improved variations of GAN methods \[[25](#ch06.xhtml#ref6_25)\] which can be explored alongside transfer learning (described below) and other methods in addressing missing data problems.
    
*     
    d. Transfer Learning
    

Transfer learning is a machine learning method that differs from traditional machine learning methods in that it uses models developed in a first task in a second task. Transfer learning includes selecting a source task, developing a source model and tuning the model. Currently, transfer learning has been used in image data, for example, as with the Oxford VGG model and Google inception model, and language data, for example, Google’s word2vec model and Stanford’s GloVe model. Even though there are a few articles about transfer learning in EHR researches, with the development of transfer learning, we believe this novel method will potentially offer more to different fields of research, including EHR data analysis. Because transfer learning models actually borrow information from the pre-trained models and generates new models, it seems that it can be used in dealing with missing data issues, but it still needs further study.

### 6.3.4 Choice of Best Method for EHR Data

As discussed earlier, single imputation methods, like mean or median imputation, can be used in EHR data analysis, as they are among the most straightforward ways to fill missing cells. However, these methods only exploit the information in one variable, and all are summarized in one value, independently from other variables, but do not consider the relationship among variables. In addition, multiple imputation methods, like MICE, have already been applied to many EHR studies \[[3](#ch06.xhtml#ref6_3)\]. These methods take into account the relationships among different variables. In addition to these conventional methods, the decision-tree model can also be considered for missing imputation in EHR datasets, and machine learning approaches are opening new horizons with high potential in dealing with missing issues and surpass the conventional methods.

EHR datasets have high dimensionality with extremely high missing rates, some up to 95%, making their imputation quite challenging. On the other hand, selecting a set of variables with a lower missing rate and ignoring the rest, may lead to a poor fit for statistical imputation models. In other words, there is a trade-off between keeping all the variables and/or running a more precise imputation. Nevertheless, with thousands of variables available, we can assume MAR and still have enough observations to build a model for imputation. Therefore, a missing rate threshold to include or exclude variables from an imputation model can help to balance the two sides. To choose such a threshold and an imputation method among all those described above, we suggest a step-by-step strategy here.

STEP 1: Choose the imputation method. If computationally feasible, we can choose multiple imputation methods.

STEP 2: Choose an initial missing rate threshold, any value in (0,1) close to 1, and remove all the variables with a missing rate greater than the threshold.

STEP 3: Do the imputation with the method chosen in step 1.

STEP 4: Fit a prediction model with imputed datasets (according to the purpose of the study), calculate the AUC.

STEP 5: Repeat step 2 to step 4, with a smaller threshold in step 2; for example, reduce the threshold by 5%.

STEP 6: Finally, select the threshold corresponding to the highest AUC. An example is shown in [Figure 6.2](#ch06.xhtml#fig6_2).

![Figure 6.2 AUC change with changes of thresholds using the MissForest method. Note that AUC is selected here because of the predictive nature of the problems of interest and for models with binary responses. However, other measures of accuracy can be used instead of AUC.](images/fig6_2.jpg)

**Figure 6.2**  
AUC change with changes of thresholds using the MissForest method. Note that AUC is selected here because of the predictive nature of the problems of interest and for models with binary responses. However, other measures of accuracy can be used instead of AUC.

## ![image](images/inline1_1.jpg)  
6.4 Case Study

In this section, we use a dataset extracted from the Cerner health fact database to do imputation using four different methods, MICE, Miss Forest, Mean and Median. The dataset we use was a high dimensional combined table, consisting of lab and clinical event tables (see Chapter 3), which are numeric tables, merged with demographic variables, medication, diagnosis and procedure table. The purpose of the original study was to predict in-hospital mortality, which is a binary response.

### 6.4.1 Missing Condition in EHR Data

In this section, we use the datasets prepared according to suggested rules in [Chapter 5](#ch05.xhtml#chapter5) Data Processing and Preparation, for predicting in-hospital mortality for SAH patients. We use all six versions of the prepared data, namely, Last24hrs, Last48hrs, Last72hrs, First24hrs, First48hrs, First72hrs, and run a comparative analysis among the four imputation procedures mentioned earlier. For the purposes of this chapter, however, we only used clinical events, lab results and some demographic variables here. [Table 6.1](#ch06.xhtml#table6_1) shows the original sample sizes of the six data frames. The cohort size and overall missing rate of each data frame ranges from 74–78% and are presented in [Table 6.2](#ch06.xhtml#table6_2).

**Table 6.1** Sample Sizes of Different Table Versions

| **Table Version** || **Cohort Size (No. of Subjects)** || **No. of Variables** |
| --- | --- | --- |
| Cut24hrs || 2153 || 195 |
| --- | --- | --- |
| Cut48hrs || 1941 || 195 |
| Cut72hrs || 1821 || 184 |
| First24hrs || 816 || 162 |
| First48hrs || 1139 || 167 |
| First72hrs || 1184 || 163 |

**Table 6.2** Overall Missing Rate before We Explore the Threshold

| **Table Version** || **Overall Missing Rate** |
| --- | --- |
| Cut24hrs || 0.78 |
| --- | --- |
| Cut48hrs || 0.75 |
| Cut72hrs || 0.76 |
| First24hrs || 0.78 |
| First48hrs || 0.74 |
| First72hrs || 0.75 |

With this dataset, we could confidently assume that some variables could, at least, partially explain the missing mechanism of data in other columns, so, in our study, we made the assumption that the missing mechanism was MAR. Many others have also made the same assumptions on the basis of sample size \[[21](#ch06.xhtml#ref6_21)\].

### 6.4.2 Missing Imputation in EHR Datasets

In this section, we will show our results from using one of the six table versions, Last24hrs, to explore the effect of choosing the best missing rate thresholds and then use four of the aforementioned imputation methods to find the “best way” to deal with missing data in real EHR data.

[Figure 6.3](#ch06.xhtml#fig6_3) visualizes the missing condition in Last24hrs dataset and changes in missing for different thresholds from 1 to 0.8. The original dataset (top panel) contains 2153 subjects and 195 variables including lab results and clinical event records and several demographic information variables. In each panel, rows and columns represent subjects and variables respectively, cells in black represent missing, and cells in grey represent non missing data?. For example, the second figure excludes all variables with a missing rate equal to 1 (variables with test records for some patients but without any numerical results), and the third figure excludes all variables with a missing rate of at least 0.95.

![Figure 6.3 The missing condition change of the Last24hrs dataset. For different values of the missing rate thresholds from 1 to 0.8.](images/fig6_3.jpg)

**Figure 6.3**  
The missing condition change of the Last24hrs dataset. For different values of the missing rate thresholds from 1 to 0.8.

As missing rate threshold decreases the number of variables remaining ([Table 6.3](#ch06.xhtml#table6_3)) and consequently the missing rate decrease, presented by diminishing black cells.

**Table 6.3** Number of Column Numbers after Dropping Variables Based on Thresholds

| **Threshold** || **Before Remove** || **Remove Missing Rate = 1** || **Remove Missing Rate&#160;>&#160;= 0.95** || **0.94** || **0.92** || **0.9** || **0.8** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| \# of variables left || 195 || 138 || 105 || 99 || 90 || 88 || 74 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Missing rate after remove || 0.78 || 0.65 || 0.55 || 0.53 || 0.49 || 0.47 || 0.40 |

[Table 6.3](#ch06.xhtml#table6_3) shows the numbers of columns remain and the missing rate after dropping variables based on the missing rate.

[Figure 6.4](#ch06.xhtml#fig6_4) presents the distribution of missing rate under each threshold value, it seems there is a large number of variables with missing rates than 95%. After dropping more variables using smaller thresholds, we found the distribution of missing rates for the remaining variables was closer to be random, which means the missing rates uniformly distributed between 0 to 1. The missing rates and distribution above, emphasize the intensity of the missing problem in EHR datasets, even in a relatively small dataset. These types of severe missing problems are not common in traditional datasets such as clinical trials.

![Figure 6.4 Missing rate distribution under different thresholds.](images/fig6_4.jpg)

**Figure 6.4**  
Missing rate distribution under different thresholds.

After revealing the missing situation and severity of the dataset, we now apply the selected imputation methods to our case study.

*   I. MICE Imputation
    

In our study, we used the MICE imputation method, however it failed to return a complete dataset partly because of the extremely high percentage of missing in some variables. A possible explanation for this may be the small number of the available responses (subjects) are not enough to estimate all the model parameters. For example, Aerosol O2, had an initial missing rate of 99%, and MICE failed just based on 1% available data, shown in [Figure 6.5](#ch06.xhtml#fig6_5).

*   II. MissForest Imputation
    

Unlike MICE, MissForest always returns a complete dataset, this is because it does not need any model training or parameter estimation.

*   III. Mean and Median Imputation
    

We consider mean and median imputation among the two naïve methods which both give complete datasets after imputation. We use these two as reference methods to compare AUC values.

![Figure 6.5 Missing in a clinical event “Oxygen & Aerosol Therapy” before and after imputation.](images/fig6_5.jpg)

**Figure 6.5**  
Missing in a clinical event “Oxygen & Aerosol Therapy” before and after imputation.

### 6.4.3 Evaluating the Performance of Imputation Methods and Thresholds

In-hospital mortality, which is a binary variable, is the response of interest in this study for which we use logistic regression with LASSO regularization applied to the imputed dataset under different thresholds and imputation methods. The performance of these models is evaluated by AUC.

[Table 6.4](#ch06.xhtml#table6_4) shows the results of AUC in different models: the AUC changes from 85% (for MICE applied before removing any variable) to 89% (Under MICE with threshold 0.8) showing a clear increase in average AUC (overall four methods) as the threshold decreases ([Figure 6.6](#ch06.xhtml#fig6_6)). This suggests that removing those variables not only retains any useful information for predicting mortality index, but it also reduces the noise in the data significantly. Now the question is that, can we find a cutoff threshold value after which any decrease would reduce useful information and AUC?

**Table 6.4** AUC Values in Each Model

|  || **Mean** || **Median** || **MICE** || **MissForest** |
| --- | --- | --- | --- | --- |
| Remove Missing Rate =1 || 0.8779 || 0.866 || 0.8513 || 0.8678 |
| --- | --- | --- | --- | --- |
| Remove Missing Rate > = 0.95 || 0.8779 || 0.866 || 0.8734 || 0.8764 |
| Remove Missing Rate > = 0.94 || 0.8843 || 0.8683 || 0.8773 || 0.8708 |
| Remove Missing Rate > = 0.92 || 0.8801 || 0.8678 || 0.8744 || 0.8657 |
| Remove Missing Rate > = 0.9 || 0.8801 || 0.8678 || 0.8679 || 0.8644 |
| Remove Missing Rate > = 0.8 || 0.8813 || 0.8678 || 0.8886 || 0.8657 |

![Figure 6.6 The AUC for predicting mortality using four different imputation methods and different missing rate thresholds are presented.](images/fig6_6.jpg)

**Figure 6.6**  
The AUC for predicting mortality using four different imputation methods and different missing rate thresholds are presented.

[Figure 6.7](#ch06.xhtml#fig6_7) also presents the overall changes in AUC among the four methods and different values of the threshold. The solid line indicates mean imputation method, the dotted line indicates median imputation method, the dashed line indicates MICE imputation and the dotdash line indicates MissForest imputation method.

![Figure 6.7 AUC changes with threshold.](images/fig6_7.jpg)

**Figure 6.7**  
AUC changes with threshold.

For MICE imputation, there is a clear decrease in the AUC value with the increase of the threshold. The reason is that, when the threshold value is close to 1, there will be many columns with high missing rates, for which MICE would face problems with fitting the regression models for predicting the missing values. For example, for a variable with sample size 2000 but has only 5 observed values, MICE would fail to estimate many coefficients for a multivariate regression model. MissForest imputation shows a robust performance among these four methods, and the AUC value is slightly increasing with increasing the threshold, which means we can keep more columns.

For the threshold, we can find small peaks in every method at around 0.9 to 0.95, this peak gives us results after we consider the trade-off between throwing high-missing-rate variables and keeping more information, only then can we get a satisfying result from the threshold.

## ![image](images/inline1_1.jpg)  
6.5 Discussion and Conclusion

Although dealing with missing data in statistical analyses (with regular datasets) is not a new challenge, studies and developing methodologies to address missing issues in EHR datasets are gaining more attention recently. This is partly because of the nature of the EHR datasets, e.g., they are extremely big with ultrahigh dimensionality, and their missing rate is extremely high; hence, most of the existing methodologies fail when applied to EHR datasets.

In this chapter, we illustrated the fundamental missing issues in EHR datasets and reviewed the existing methodologies in the literature for dealing with the missing data problem. Because of the size of most EHR datasets and their extreme high missing rates, sophisticated likelihood-based methods are quite inefficient or even impossible to implement. Instead, we proposed using common imputation methods. Of course, these methods require some underlying assumptions, such as MAR and strong correlation structure, which need to be carefully considered in each case. Since EHR datasets have a massive number of variables, it might be reasonable to assume an MAR mechanism so we could periodically find a few observed variables to explain the missing mechanism. In addition, we included examples of missing imputation on EHR datasets with truly large dimensions and extremely high missing rates and assessed the efficacy and precision of these methods.

We believe that there is still a big gap in the literature and massive opportunity for developing new methodologies specifically to address the missing data problem in EHR datasets. Combinations of statistical and machine learning (neural networks) approaches, coupled with clinical knowledge are one of the ways to begin these investigations.

### References

1\. Dempster, A. P., N. M. Laird, and D. B. Rubin. 1977. Maximum Likelihood from Incomplete Data Via the EM Algorithm. *Journal of the Royal Statistical Society: Series B (Methodological)* **39**((1)), 1–22. [https://doi.org/10.1111/j.2517-6161.1977.tb01600.x](https://doi.org/10.1111/j.2517-6161.1977.tb01600.x).

2\. Campion, S., M. William, and Donald B. Rubin. 1989. Multiple Imputation for Nonresponse in Surveys. *Journal of Marketing Research* **26**((4)), 485. [https://doi.org/10.2307/3172772](https://doi.org/10.2307/3172772).

3\.  van Buuren S., and K. Groothuis-Oudshoorn. 2011. Mice: Multivariate imputation by chained equations in R. *Journal of Statistical Software* **45**, 1–67.

4\. Stekhoven, Daniel J., and Peter Bühlmann. 2012. Missforest-non-parametric missing value imputation for mixed-type data. *Bioinformatics* **28**((1)), 112–118. [https://doi.org/10.1093/bioinformatics/btr597](https://doi.org/10.1093/bioinformatics/btr597).

5\. Donders A. R. T., G. J. M. G. van der Heijden, T. Stijnen, and K. G. M. Moons. 2006. Review: A gentle introduction to imputation of missing values. *Journal of Clinical Epidemiology* **59**, 1087–1091.

6\. Rubin D. B. 1976. Biometrika trust inference and missing data author(s): Donald B. Rubin published by: Oxford University Press on behalf of Biometrika Trust Stable. URL: [http://www.jstor.org/stable/2335739](http://www.jstor.org) Accessed: 12-06-2016 21, 34 UTC *Biometrika* **63**: 581–592.

7\. Rubin, Donald B., Hal S. Stern, and Vasja Vehovar. Handling ‘Don’t Know’ Survey Responses: The Case of the Slovenian Plebiscite. *Journal of the American Statistical Association* **90**, no. (431) (1995): 822. [https://doi.org/10.2307/2291315](https://doi.org/10.2307/2291315)..

8\. Liang K.-Y., and S. L. Zeger. 1986. Longitudinal data analysis using GLM. *Biometrika* **73**, 13–22.

9\. Wang M. 2014. Generalized estimating equations in longitudinal data analysis: A review and recent developments. *Advanced Statistics* **2014**, 1–11.

10\. Kattari S. K. 2019. The development and validation of the ableist microaggression scale. *Journal of Social Service Research* **45**, 400–417

11\. Little R. J., R. D’Agostino, M. L. Cohen, K. Dickersin, S. S. Emerson, J. T. Farrar, C. Frangakis, J. W. Hogan, G. Molenberghs, S. A. Murphy, J. D. Neaton, A. Rotnitzky, D. Scharfstein, W. J. Shih, J. P. Siegel, and H. Stern. 2012. The prevention and treatment of missing data in clinical trials. *The New England Journal of Medicine* **367**, 1355–1360.

12\. Knorr-Held L. 2000. *Analysis of incomplete multivariate data.* J. L. Schafer, London: Chapman & Hall, 1997. No. of pages: xiv+430. Price: £39.95. ISBN 0-412-04061-1 *Statistics in Medicine* **19**, 1006–1008.

13\. Royston P. 2005. Multiple imputation of missing values: Update of ICE. *The Stata Journal* **5**, 527–536.

14\. Siddique, Juned, and Thomas R. Belin. Using an approximate Bayesianbootstrap to multiply impute nonignorable missing data. *Computational Statistics & Data Analysis* **53**, no. (2) (2008), 405–415. [https://doi.org/10.1016/j.csda.2008.07.042](https://doi.org/10.1016/j.csda.2008.07.042).

15\. Moore II D. H. 1987. Classification and regression trees, by Leo Breiman, Jerome H. Friedman, Richard A. Olshen, and Charles J. Stone. Brooks/Cole Publishing, Monterey, 1984, 358 pages, $27.95. *Cytometry* **8**, 534–535.

16\. Fisher, R. A. 1936. The use of multiple measurements in taxonomic problems. *Annals of Eugenics* **7** ((2)): 179–188. [https://doi.org/10.1111/j.1469-1809.1936.tb02137.x](https://doi.org/10.1111/j.1469-1809.1936.tb02137.x).

17\. Anderson E. 1936. The species problem in Iris. *Annals of Missouri Botanical Garden*.

18\. Neapolitan R. E., and R. E. Neapolitan. 2018. Neural networks and deep learning. *Artificial Intelligence*

19\. Beaulieu-Jones B. K., and J. H. Moore. 2017. Missing data imputation in the electronic health record using deeply learned autoencoders. *Pacific Symposium on Biocomputing*. **0**, 207–218.

20\.  Beaulieu-Jones B. K., and C. S. Greene. 2016. Semi-supervised learning of the electronic health record for phenotype stratification. *Journal of Biomedical Informatics* **64**, 168–178.

21\. Wells B. J., A. S. Nowacki, K. Chagin, and M. W. Kattan. 2013. Strategies for handling missing data in electronic health record derived data. *eGEMs (Generating Evidence and Methods to Improve Patient Outcomes)* **1**, 7.

22\. Goodfellow I. J., J. Pouget-Abadie, M. Mirza, B. Xu, D. Warde-Farley, S. Ozair, A. Courville, and Y. Bengio. 2014. Generative adversarial nets. *Advances in Neural Information Processing Systems* **3**, 2672–2680.

23\. Yoon J., J. Jordon, and M. Van Der Schaar. 2018. GAIN: Missing data imputation using generative adversarial nets. *The 35th International Conference on Machine Learning: ICML 2018* **13**, 9042–9051.

24\. Luo Y., X. Cai, Y. Zhang, J. Xu, and X. Yuan. 2018. Multivariate time series imputation with generative adversarial networks. *Advances in Neural Information Processing Systems* **2018**, 1596–1607.

25\. Zhang J., K. Jia, J. Jia, and Y. Qian. 2018. Improved techniques for training GANs. *BMC Bioinformatics* **19**, 1–9.

# [7 ](#contents.xhtml#toc1_128)  
![image](images/inline1_1.jpg)

# [Causal Inference and Analysis for EHR Data](#contents.xhtml)  
               

Stacia M. DeSantis, Momiao Xiong, Jose-Miguel Yamal, Gen Zhu, Duo Yu, Xueying Wang, Chenguang Zhang and Vi K. Ly

## ![image](images/inline1_1.jpg)  
7.1 Introduction

### 7.1.1 Why Causal Inference

EHRs are a rich source of demographic and clinical information, including sociodemographics, medical visit times, diagnoses, medications, procedures, vital signs, and lab tests for a large population of patients. They can be an excellent data source from which to implement comparative effectiveness analyses to evaluate known treatments or discover new treatments. However, unbiased estimates of effect can be difficult to obtain from observational data like EHRs. The gold standard for unbiased estimation of treatment effects is the randomized clinical trial (RCT) ([Concato, Shah, and Horwitz 2000](#ch07.xhtml#ref7_11)), wherein treatment is randomly assigned to patients in the study. Effective randomizations alleviate the issue of bias due to confounding in the treatment effect estimation, as baseline confounders should be balanced across randomized groups. However, RCTs are expensive, time-consuming, and often infeasible or even unethical, depending on the clinical setting. An alternative to RCTs is to apply state-of-the-art causal inference techniques to EHR-derived studies.

EHR data analytics have unique challenges. Creating and integrating variables from EHR data to facilitate unbiased inference about the effects of treatments or exposures on health outcomes, remains both a challenge and a priority. In this chapter, we will first introduce several commonly used methods: propensity score method, instrumental variables estimator, and mediation analysis. Then, we will introduce deep learning methods such as generative adversarial networks for causal inference. Following that, we present a targeted minimum loss-based estimation, a modern causal inference method which is especially applicable for big data.

### 7.1.2 Overview of Causal Inference Methods: Rubin Causal Model (RCM)

A mainstream general framework for treatment effect estimation from observational data is the potential outcome framework where every individual has a set of “potential outcomes” corresponding to all possible treatment levels ([Rubin 1978](#ch07.xhtml#ref7_56), [Ray and Szabó 2019](#ch07.xhtml#ref7_49)). RCM is also called the Neyman-Rubin counterfactual framework of causality, which was originally created by Neyman ([Neyman 1923](#ch07.xhtml#ref7_46)) and Rubin ([Rubin 1974](#ch07.xhtml#ref7_55)) for studying observational data. The main idea behind the Rubin causal model is the concept of potential outcomes. A counterfactual is defined as the potential outcome that would have happened in the absence of the cause ([Shadish, Cook, and Campbell 2002](#ch07.xhtml#ref7_61)). An individual observes only one of the potential outcomes that correspond to the assigned treatment, which is called the factual outcome. The other potential outcomes are missing and unobserved. The unobserved potential outcomes are called counterfactual outcomes or simply counterfactuals. For example, when analyzing the effect of vasopressor on death for SAH patients, we want to know the difference in the potential outcome of a patient if he/she received the treatment (vasopressor) versus the potential outcome if he/she did not receive the treatment. A causal effect is defined as the difference between the two potential outcomes. The key assumption of the counterfactual framework is that each individual in the population of interest has a potential outcome under each treatment state. In reality, one can only observe one of the potential outcomes in one treatment state, as one patient can be assigned either in a treatment group or a control group. Within this framework, the estimation problem inherently becomes a missing data problem, whereby estimating treatment effects requires properly imputing the counterfactuals ([Ding and Li 2018](#ch07.xhtml#ref7_13)).

A plethora of statistical methods have been developed for causal inference under this counterfactual paradigm. One commonly used approach to estimating counterfactuals is simply matching patients on underlying risk factors, which is a systematic way to approximately impute the counterfactuals by borrowing information from the matched subjects (Paul [Rosenbaum and Rubin 1983](#ch07.xhtml#ref7_53), [Luo and Zhu 2019](#ch07.xhtml#ref7_42)). Matching methods that have been developed including Mahalanobis metric matching, propensity score matching ([Rosenbaum and Rubin 1985](#ch07.xhtml#ref7_52)), full matching ([Rosenbaum 1991](#ch07.xhtml#ref7_50)), genetic matching ([Diamond and Sekhon 2013](#ch07.xhtml#ref7_12)), and deep instrumental variables networks ([Hartford et al. 2017](#ch07.xhtml#ref7_25)).

### 7.1.3 Basic Framework in Causality: Potential Outcome Framework

In EHR databases, comparisons of treatments are often more complex than a simple two-group comparison. Consider, for example, when comparing drugs administered, there may be multiple drugs given, with varying doses, and various types of outcomes to evaluate the effectiveness or safety of those treatments. We introduce a general framework that allows for the consideration of multiple treatments, discrete and continuous treatments, and binary and continuous outcomes ([Ge et al. 2020](#ch07.xhtml#ref7_17)). Consider *K* treatments. Let *W*[*i*] = \[*W*[*i*]¹,….,*W*[*i*]^(*K*)\]^(*T*) be the treatment assignment vector for the *i*^(*t**h*) individual, where *W*[*i*]^(*k*) = 1 indicates that the *i*^(*t**h*) individual receives the *k*^(*t**h*) treatment and *W*[*i*]^(*k*) = 0 indicates that the *i*^(*t**h*) individual does not receive the *k*^(*t**h*) treatment. We assume that there is precisely one non-zero component of the vector *W*[*i*] and its index is denoted by *η*, *i*.*e*., *W*[*i*]^(*η*) = 1. Thus, we have $\\sum\_{k = 1}^{K}{W\_{i}^{k} = 1}$. Define the treatment vector *T*[*i*] = \[*T*[*i*]¹,…,*T*[*i*]^(*K*)\]^(*T*), where *T*[*i*]^(*k*) is the *k*^(*t**h*) treatment variable which the *i*^(*t**h*) individual receives. It can be binary, categorical, or continuous. Only, *T*[*i*]^(*η*) is given, other components of the treatment vector *T*[*i*] can be arbitrary. Let ${\\overline{Y}}\_{i} = \\left\\lbrack {\\overline{Y}}\_{i}^{1},\\ldots,{\\overline{Y}}\_{i}^{K}\\rbrack^{T} \\right.$ be the vector of potential outcomes for the *i*^(*t**h*) individual, where ${\\overline{Y}}\_{i}^{k}$ is the potential outcome if the *i*^(*t**h*) individual had received the *k*^(*t**h*) treatment. We only observe one component of the potential outcome vector ${\\overline{Y}}\_{i}$ that corresponds to the assigned treatment *W*[*i*]^(*η*), which is called the factual outcome and is denoted by ${\\overline{Y}}\_{i}^{f}$, where *f* = *η*. Other unobserved potential outcomes are called counterfactual outcomes, or simply counterfactuals, and denoted by ${\\overline{Y}}\_{i}^{\\mathit{cf}}$. The factual outcome ${\\overline{Y}}\_{i}^{f}$ can be expressed as ${\\overline{Y}}\_{i}^{f} = \\sum\_{k = 1}^{K}{W\_{i}^{k}{\\overline{Y}}\_{i}^{k}}$.

For example, if $W\_{i} = \\begin{bmatrix} 0 \\\\ 1 \\\\ 0 \\\\ \\end{bmatrix}$ , then *η* = 2 and ${\\overline{Y}}\_{i} = \\begin{bmatrix} {\\overline{Y}}\_{i}^{\\mathit{cf}} \\\\ {\\overline{Y}}\_{i}^{f} \\\\ {\\overline{Y}}\_{i}^{\\mathit{cf}} \\\\ \\end{bmatrix}$. Each individual is associated with *K* potential outcomes ${\\overline{Y}}\_{i}^{k}$ , but only one of them can be observed as ${\\overline{Y}}\_{i}^{f}$. We assume that a vector of *p* covariates *X*[*i*] = \[*x*[*i*1],…,*x*[*i**p*]\]^(*T*) is associated with the *i*^(*t**h*) individual, including the patient demographics and clinical variables. Suppose that *n* individuals are sampled.

We make the following assumptions ([Rubin 1980](#ch07.xhtml#ref7_57), [Rosenbaum and Rubin 1983](#ch07.xhtml#ref7_53)).

ASSUMPTION 1: For all covariates *X* and all treatment *k*, *k* = 1, …, *K*, we have

0 < *P*(*W*[*i*]^(*k*)\=1|*X*\=*x*) < 1.(7.1)

This assumption ensures that at every point in the feature space, there is a non-zero probability of being given treatment *W*[*i*]^(*k*) for every *i*.

ASSUMPTION 2: (Unconfoundedness). Conditional on the covariates *X*, the potential outcomes $\\overline{Y}$ and treatments *W* are independent:

$\\overline{Y}⫫W|X.$(7.2)

ASSUMPTION 3: (The standard stable unit treatment value assumption (SUTVA)). There is no interference between units and no different versions of treatment.

#### Average and Individual Treatment Effects

The most widely used measure of the treatment effect for multiple treatments is the pair-wise treatment effect. The individual effect *ξ*[*j**k*]^((*i*)) between the pairwise treatments: *T*[*i*]^(*j*) and *T*[*i*]^(*k*) is defined as $\\xi\_{\\mathit{jk}}^{(i)} = {\\overline{Y}}\_{i}^{j} - {\\overline{Y}}\_{i}^{k}$, the average pairwise treatment effect (ATE) is defined as *τ*[*j**k*] = *E*\[*ξ*[*j**k*]^((*i*))\]. The average pairwise treatmento effect *τ*[*j**k*|*T*[*j*]] on the patients treated with *T*[*j*] is defined as $\\tau\_{\\mathit{jk}|T\_{j}} = E{\\lbrack{\\xi\_{\\mathit{jk}}^{(i)}\\mspace{-4mu}|\\mspace{-4mu} T\_{j}}\\rbrack}$. The focus of this chapter is on the conditional distribution of treatment effect, given the feature vector *X*. Assume that *n* individuals are sampled. For the *i*^(*t**h*) individual, *T*^(*η*) treatment (*W*[*i*]^(*η*)\=1) is assigned. Let *X*[*i*] and ${\\overline{Y}}\_{i}^{\\eta} = {\\overline{Y}}\_{i}^{f}$ be the observed feature vector and the observed potential outcome of the *i*^(*t**h*) individual. Therefore, the observed dataset is given by $D = \\left( {X\_{i},T\_{i},{W\_{i},\\overline{Y}}\_{i}^{\\eta},i = 1,\\ldots,n} \\right)$. The factual and counterfactual outcomes of the *i*^(*t**h*) individual is denoted by ${\\overline{Y}}\_{i}^{f}$ and ${\\overline{Y}}\_{i}^{\\mathit{cf}}$, respectively. The observed outcome ${\\overline{Y}}\_{i}^{\\mathit{obs}}$ of the *i*^(*t**h*) individual is equal to ${\\overline{Y}}\_{i}^{f} = {\\overline{Y}}\_{i}^{\\eta} = \\sum\_{k = 1}^{K}{W\_{i}^{k}{\\overline{Y}}\_{i}^{k}}$ and the other potential outcomes (counterfactuals) ${\\overline{Y}}\_{i}^{\\mathit{cf}} = {\\overline{Y}}\_{i}^{\\mathit{mis}} = \\left( {1 - W\_{i}^{k}} \\right){\\overline{Y}}\_{i}^{k},k = 1,\\ldots,K$ are missing.

## ![image](images/inline1_1.jpg)  
7.2 Propensity Scoring

### 7.2.1 Brief Introduction

Propensity scoring methods are among the most commonly used causal inference methods. Propensity scoring seeks to eliminate the bias that results from the analysis of non-randomized observational studies by creating comparison groups that are similar to observed baseline confounders, but differ according to the treatment or exposure received ([Yanovitzky, Zanutto, and Hornik 2005](#ch07.xhtml#ref7_71)). It involves two steps: Step 1) fitting a propensity model to estimate the probability of being treated in order to obtain a balancing score, and Step 2) using the balancing score to adjust for bias to obtain causal inference. Adjustment methods include stratification, matching, and inverse probability weighting (IPW) in the outcome model, each with well-studied benefits and limitations ([Austin and Stuart 2015](#ch07.xhtml#ref7_4)).

Treatments derived from EHR-derived comparative effectiveness studies may be binary, ordinal, or nominal (i.e., mutually exclusive). Adaption of propensity scoring for EHR-derived studies requires an explanation of existing methods for multiple treatments ([Imai and Van Dyk 2004](#ch07.xhtml#ref7_28), [Brown et al. 2020](#ch07.xhtml#ref7_7), [Fong, Hazlettand, and Imai 2018](#ch07.xhtml#ref7_16)), high-dimensional confounders, and machine learning adaptations that have shown promise in the available literature ([Mccaffrey et al. 2013](#ch07.xhtml#ref7_44), [Burgette, Griffin, and Mccaffrey 2020](#ch07.xhtml#ref7_9), [Ju et al. 2019](#ch07.xhtml#ref7_33), [Brown et al. 2020](#ch07.xhtml#ref7_7)).

### 7.2.2 Propensity Scoring for Binary Treatments

For binary treatments, a propensity (or balancing) score may be estimated from a logistic, probit ([Rosenbaum and Rubin 1983](#ch07.xhtml#ref7_53)) or more recently, machine learning algorithms such as random forests, neural nets, and generalized gradient boosting methods (GBM) ([McCaffrey, Ridgeway, and Morral 2004](#ch07.xhtml#ref7_45), [Setoguchi et al. 2008](#ch07.xhtml#ref7_59), [Mccaffrey et al. 2013](#ch07.xhtml#ref7_44)). The resulting propensity score is then used to adjust for covariate imbalance ([Imbens 2000](#ch07.xhtml#ref7_31)). This enables estimation in Step 2, of the two causal estimands of interest, presented here for the K multiple treatments case.

The average treatment effect in the treated (ATT), *A**T**T*[*k**|**k*, *k*^′′] = *E*(*Y*[*i*](*k*)) − *Y*[*i*](*k*^′)|*Y*[*i*]\=*k*\], is the expected outcome between treatment *k* vs *k*^′ for people treated with k.McCaffrey et al. (2013) Unlike ATE, the ATT distinguishes who within the population is the reference (k). There are (*K*/2) ATEs and *K!* ATTs.

### 7.2.3 Propensity Scoring for Multiple Treatments

In a study of treatment effects on a disease outcome, multiple treatments would often be of interest, thus applying multiple treatments propensity scoring approaches would be the norm for EHR data. Multiple treatments propensity scoring is more complex than the binary case described above. In fact, in contrast to the binary setting, there is no proposed universal scalar balancing score that captures the complex relation of counterfactuals to balance confounders across all K treatments, which is required to produce ATE/ATTs defined above. That is because any multiple treatments propensity model will produce a vector (rather than a scalar) of “generalized propensity scores” (GPS), i.e., ${\\widehat{\\mathbf{P}}}\_{\\mathbf{i},\\mathbf{GPS}} = {({{\\widehat{p}}\_{i,1},\\ldots,{\\widehat{p}}\_{i,K}})}$, which may result from a multinomial regression or machine learning model, e.g., $\\mathit{\\log}{\\lbrack{P\\frac{Z\_{i} = \\mathit{k|}X\_{i} = x\_{i}}{Z\_{i} = k^{\\prime}|X\_{i} = x\_{i}}}\\rbrack}$ = *θ*[*k*] + *x*[*i*]′*β*[*k*], where the left side is a regression of treatment assignment, k, on covariate vector, X, *θ*[*k*] is a constant, and *β*[*k*] is a vector of K − 1 regression coefficients ([Joffe and Rosenbaum 1999](#ch07.xhtml#ref7_32), [Rassen et al. 2013](#ch07.xhtml#ref7_48), [Tu, Jiao, and Koh 2013](#ch07.xhtml#ref7_63), [Seya and Yoshida 2017](#ch07.xhtml#ref7_60), [Lopez and Gutman 2017](#ch07.xhtml#ref7_39), [Imbens 2000](#ch07.xhtml#ref7_31), [Imai and Van Dyk 2004](#ch07.xhtml#ref7_28)). Each GPS element is the conditional probability of receiving treatment k. Although how to reduce the GPS vector to a scalar in Step 2 remains ad hoc and understudied, recent work has used distance metrics and clustering tools to stratify or match it on the GPS vector. For example, once the GPS is obtained in Step 1, one can minimize Mahalonabis multivariate distance, ([Imbens 2000](#ch07.xhtml#ref7_31), [Imai and Van Dyk 2004](#ch07.xhtml#ref7_28), [Rassen et al. 2013](#ch07.xhtml#ref7_48), [Seya and Yoshida 2017](#ch07.xhtml#ref7_60)) conduct “within-trio” distance matching (for K = 3 only), [Rassen et al. (2013)](#ch07.xhtml#ref7_48) or use clustering techniques to group those with similar GPS vectors ([Tu, Jiao, and Koh 2013](#ch07.xhtml#ref7_63), [Lopez and Gutman 2017](#ch07.xhtml#ref7_39)) . These adjustment methods are basically extensions of the binary setting and are generally limited in the number of treatments and type of adjustment they allow (e.g., usually, matching on K = 3 treatments limited to an ATT outcome analysis, is supported). Reproducible research has also shown that distance-based approaches are not appropriate for higher-dimensional covariate vectors ([Gu and Rosenbaum 1993](#ch07.xhtml#ref7_21), [Stuart 2010](#ch07.xhtml#ref7_62)), which are common in EHR-based studies. One must be careful in selecting which approach to apply when estimating ATEs or ATTs—existing distance/clustering methods of adjustment typically estimate average potential outcomes separately for each treatment level rather than constructing balanced strata or matched pairs ([Yang et al. 2016](#ch07.xhtml#ref7_70)). In fact, several approaches are tailored to estimating ATTs (versus ATEs), which may or may not be the estimand of interest for a given comparative effectiveness study derived from EHRs (since ATT is only generalizable to the subjects in a treated reference group) ([Lopez and Gutman 2017](#ch07.xhtml#ref7_39)). Finally, some methods are computationally impractical, ([Huang et al. 2005](#ch07.xhtml#ref7_27), [Tu, Jiao, and Koh 2013](#ch07.xhtml#ref7_63)), only applicable to certain outcome types, may not produce good balancing scores, and/or do not apply when K > 3 ([Harder, Stuart, and Anthony 2010](#ch07.xhtml#ref7_24), [Fong, Hazlettand, and Imai 2018](#ch07.xhtml#ref7_16)). Propensity scoring methods that readily lend themselves to “big data” causal analysis from EHR-derived studies—i.e., studies that simultaneously examine multiple treatments with complex covariate spaces—should be further studied. While research has been and is continually being developed, there continues to be a gap in propensity scoring methodology for multiple treatments in the context of big data sets, where both multiple treatments and high-dimensional covariates are simultaneously of interest.

### 7.2.4 Propensity Scoring for Ordinal Treatments

Ordinal propensity scoring is a special instance of multiple-treatment propensity scoring, described above, which may arise in EHR data. For example, one may be interested in the effect of the dose of a second-generation serotonin selective reuptake inhibitor (SSRI) on remission of depression symptoms or a dose of a statin on prevention of heart failure, other cardiovascular outcomes, or death. Clearly, methods for ordinal propensity scoring would differ from the multiple treatment case; for example, they might exploit the natural underlying treatment structure such as the dose-response relationship between treatment and covariates. In ordinal propensity scoring, challenges occur both in Step 1.) choosing an appropriate propensity model and Step 2.) adjusting for the balancing/propensity score to obtain ATEs. While GPS methodologies from multinomial treatments are applicable here ([Imbens 2000](#ch07.xhtml#ref7_31), [Imai and Van Dyk 2004](#ch07.xhtml#ref7_28)). One could gain efficiency in causal estimates by exploiting the ordinal nature of the treatment/covariate relationship. Proportional odds (PO) regression model, an important extension of binary logistic regression for ordinal outcomes, is the most obvious way to do this—it can be used to produce a scalar balancing score, i.e., the linear predictor, $\\mathbf{X}\_{i}\\widehat{\\mathbf{\\beta}}$, for a given covariate vector, *X*[*i*], on which patients can be matched or stratified (B. [Lu et al. 2001](#ch07.xhtml#ref7_40), [Zanutto, Lu, and Hornik 2005](#ch07.xhtml#ref7_73), [Greene et al. 2017](#ch07.xhtml#ref7_19)). In Step 2, one can apply non-bipartite matching based on the value of this balancing score, and the value of the observed (actual) treatment level (B. [Lu et al. 2001](#ch07.xhtml#ref7_40)). This Mahalonobis-type metric facilitates matching patients who received different levels of ordinal treatment. If the PO assumption were correct for every variable in the propensity model such that a “good” balancing score could be produced, then *X*[*i*]*β̂* would be an excellent dimension reducing the scalar balancing score. However given the noisy big data challenges pertinent to contemporary statistical analysis, strict parametric propensity models are less useful ([McCaffrey, Ridgeway, and Morral 2004](#ch07.xhtml#ref7_45), [Mccaffrey et al. 2013](#ch07.xhtml#ref7_44)). Instead, machine learning propensity models are useful alternatives, ([Burgette, Griffin, and Mccaffrey 2020](#ch07.xhtml#ref7_9), [Ju et al. 2019](#ch07.xhtml#ref7_33), [Wyss et al. 2018](#ch07.xhtml#ref7_69), [Mccaffrey et al. 2013](#ch07.xhtml#ref7_44), Greene et al. 2020) as they accommodate high-dimensional covariate spaces, multi-order terms, and some incorporate implicit interactions in Step 1. Methods for propensity score adjustment in Step 2 must, therefore, be adapted for seamless use with machine learning propensity models fitted in Step 1 to facilitate big data causal analysis. Methods for adjustment for ordinal treatments in the context of many and complex covariate spaces are still under development.

### 7.2.5 Propensity Score Estimation for Complex Data Sets

Studies derived from EHR data are likely to result in “complex” confounder-treatment associations e.g., a high-dimensional covariate space, interactions, higher-order, and nonlinear terms are likely to simultaneously operate on the treatment assignment as well as the outcome. The class of non-parametric machine learning methods of propensity score estimation, including ensemble methods, random forests, GBM, recursive partitioning, and neural nets ([Setoguchi et al. 2008](#ch07.xhtml#ref7_59), F. [Li, Morgan, and Zaslavsky 2018](#ch07.xhtml#ref7_36), [McCaffrey, Ridgeway, and Morral 2004](#ch07.xhtml#ref7_45), [Mccaffrey et al. 2013](#ch07.xhtml#ref7_44), [Ju et al. 2019](#ch07.xhtml#ref7_33)) are all useful for the analysis of EHR data and should be considered for application in high-dimensional confounder settings. Specifically, GBM has very recently been adapted to the multiple treatments setting in order to capture complex treatment/covariate associations than cannot be captured by parametric models, and a newly published software package implements GBM propensity scoring in the freeware R ([Burgette, Griffin, and Mccaffrey 2020](#ch07.xhtml#ref7_9), [Brown et al. 2020](#ch07.xhtml#ref7_7)). The software also produces the requisite balance diagnostics required to assess the utility of the propensity score in balancing treated and control patients on confounders. Which machine learning method (e.g., super learners, random forests, or neural nets) is used in Step 1 is not usually of primary importance because the model selection and overparameterization are not as much an issue in propensity scoring as they are in typical association studies. Thus, it is generally well-accepted that these methods, which automatically incorporate variable selection, interactions, the decision to include higher-order terms and optimize covariate balance across k, probably produce at least equivalent propensity scores with respect to resultant covariate balance in high-dimensional settings such as EHR-derived studies, versus their parametric counterparts ([Imai and Ratkovic 2013](#ch07.xhtml#ref7_30), [Mccaffrey et al. 2013](#ch07.xhtml#ref7_44), F. [Li, Morgan, and Zaslavsky 2018](#ch07.xhtml#ref7_36), [Burgette, Griffin, and Mccaffrey 2020](#ch07.xhtml#ref7_9)).

Machine learning propensity models have typically been coupled with IPW in Step 2, where the ATE weight is the “inverse probability of the treatment the person actually received” ([Mccaffrey et al. 2013](#ch07.xhtml#ref7_44), [Austin and Stuart 2015](#ch07.xhtml#ref7_4), [Ju et al. 2019](#ch07.xhtml#ref7_33)), since IPW is most sensitive to misspecification of the propensity model. However, some research has shown that it can lead to biased estimates of the ATEs in the high-dimensional confounder settings especially since the propensity model (in addition to the outcome model) is likely to be misspecified (Rubin 2004; [Stuart 2010](#ch07.xhtml#ref7_62), [Imai and Ratkovic 2013](#ch07.xhtml#ref7_30), Greene et al. 2020, [Brown et al. 2020](#ch07.xhtml#ref7_7)). Alternatively, matching and stratification are less sensitive to misspecification, and the former may be a more useful adjustment method when there are a large number of control treatments available in the database, as is typically true of EHR-derived studies ([Brown et al. 2020](#ch07.xhtml#ref7_7)). Both matching and stratification, as opposed to weighting, are also easier methods for testing covariate balance even though methods for matching and stratification are yet to be developed.

In the EHR setting with complex covariate space, both propensity and outcome model misspecification are obviously most likely to be issues. It has been well-studied ([Feng et al. 2012](#ch07.xhtml#ref7_15), Greene et al. 2020, [Fong, Hazlettand, and Imai 2018](#ch07.xhtml#ref7_16), [Imai and Ratkovic 2013](#ch07.xhtml#ref7_30)) that when propensity and outcome models are both misspecified, biases in causal effects are large, even when applying what appears to be the latest state-of-the-art methods. Thus, the application of robust machine learning propensity models combined with appropriate adjustment procedures may help avoid biased effect sizes for big data analytics. To this end, ongoing research adapting machine learning methods for use with IPW, matching, and stratification (rather than solely IPW) may offer more robust, efficient, and versatile methods for big data causal analysis than are currently available.

### 7.2.6 Illustration Example: Subarachnoid Hemorrhage (SAH) Project

We present a study derived from the Cerner Health Facts database that determined the association between vasopressors and mortality in patients with non-traumatic and traumatic aneurysmal subarachnoid hemorrhage (SAH). The study population has been previously described ([Williams et al. 2020](#ch07.xhtml#ref7_68)). To summarize, the Cerner Health Facts EHR database was queried from years 2000 to 2015 to select adult patients (over age 17) with a new diagnosis of aneurysmal SAH based on ICD-9 code 430. Only patients who received infusions of dopamine, phenylephrine, or norepinephrine were included in the study population ([Williams et al. 2020](#ch07.xhtml#ref7_68)). Among the 4,850 patients that met the above study inclusion criteria, 40 patients presented with multiple first vasopressor treatments and were thus excluded from the cohort. Furthermore, patients whose diagnosis included a traumatic cause of SAH (based on ICD 9 codes: 800.2x, 800.7x, 801.2x, 801.7x, 803.2x, 803.7x, 804.2x, 804.7x, 852.x) or with unknown mortality status were also excluded from the study population leaving 2,634 patients in the final cohort.

The propensity score analysis presented here includes 2,417 patients with complete data for demographic variables (age, gender, race, and marital status) as well as 170 pretreatment medication variables. Of the patients included in the analysis, 492, 1,253, and 672 were administered dopamine, phenylephrine, and norepinephrine, respectively. All demographic and pretreatment variables were entered into a GBM model. More details on variable selection, as well as precise variables included in the propensity model, can be found in previous studies ([Williams et al. 2020](#ch07.xhtml#ref7_68), [Brown et al. 2020](#ch07.xhtml#ref7_7)).

As all patients were eligible for all three treatments, ATE is the estimand of interest. First, a visual representation of the covariate balance achieved after applying IPW is depicted in [Figure 7.1](#ch07.xhtml#fig7_1). Standardized mean difference (SMD) is a measure to compare the similarity of subjects in the matched sample ([Austin 2011](#ch07.xhtml#ref7_3)). In each comparison group, e.g., dopamine vs phenylephrine, SMD can be calculated for each covariate. The left plot shows maximum pairwise SMD for each potential pretreatment confounder. Similarly, the right plot shows the average pairwise SMD, which is calculated by averaging the SMD for each potential pretreatment confounder across treatment pairs. Literature suggests that values of average SMD less than 0.2 indicate small levels of covariate imbalance ([Mccaffrey et al. 2013](#ch07.xhtml#ref7_44)). Based on this cutoff, the balance was reasonably achieved for most covariates ([Figure  7.1](#ch07.xhtml#table7_1)).

![Figure 7.1 Graphical representation of covariate balance as measured by the standardized mean difference (SMD) within the unweighted and weighted data. In both plots, the balance achieved through inverse probability weighting is clearly better than the original unweighted data.](images/fig7_1.jpg)

**Figure 7.1**  
Graphical representation of covariate balance as measured by the standardized mean difference (SMD) within the unweighted and weighted data. In both plots, the balance achieved through inverse probability weighting is clearly better than the original unweighted data.

**Table 7.1** Association of Treatment with Mortality Using Inverse Probability Weighting for Non-Traumatic SAH Subjects in the Subgroup that had Vital Signs Data DBP, SBP, and HR, Adjusted for Age, Race, Marital Status, Gender, DBP, SBP, and HR

|  ||  || **Unweighted Model** ||  ||  || **Weighted Model** |
| --- | --- | --- | --- | --- | --- |
| **Comparison** || **Deaths/N (%)** || **OR (95% CI)** || **P-Value** || **OR (95% CI)** || **P-Value** |
| **Dopamine vs. Phenylephrine** |
| --- |
| **Dopamine** || 48/88 (55) || 3.66 (2.26–5.94) || <0.0001 || 3.79 (2.07–6.92) || <0.0001 |
| **Phenylephrine** || 129/569 (23) || Ref || Ref || Ref || Ref |
| **Norepinephrine vs. Phenylephrine** |
| **Norepinephrine** || 142/283 (50) || 2.83 (2.04–3.94) || <0.0001 || 2.01 (1.40–2.89) || 0.0002 |
| **Phenylephrine** || 129/569 (23) || Ref || Ref || Ref || Ref |
| **Dopamine vs. Norepinephrine** |
| **Dopamine** || 48/88 (55) || 1.29 (0.78–2.15) || 0.3229 || 1.88 (1.00–3.56) || 0.0512 |
| **Norepinephrine** || 142/283 (50) || Ref || Ref || Ref || Ref |

Due to the limitations of EHR, particularly, not being able to capture complete relevant clinical characteristics, we conducted a sensitivity analysis in the subset of subjects that had an important variable indicating patient severity: Glasgow Coma Scale (GCS) scores. Around 40% of the nontraumatic patients had at least one GCS record and GCS was not well-balanced using IPW. Therefore, we conducted propensity score matching instead and found GCS scores and demographic factors were well balanced between each pair of treatments. For example, for phenylephrine and dopamine treatment groups, from [Table 7.2](#ch07.xhtml#table7_2), the distributions of demographic variables and GCS after propensity matching are similar. For more details of other comparison groups, interested readers can review related literature ([Williams et al. 2020](#ch07.xhtml#ref7_68)).

**Table 7.2** Distribution Comparison of Demographic Variables and GCS after Propensity Matching between Phenylephrine and Dopamine Treatment Groups

|  || **Phenylephrine** || **Dopamine** || **p** |
| --- | --- | --- | --- |
| n || 96 || 96 ||  |
| --- | --- | --- | --- |
| AGE\_IN\_YEARS (mean (SD)) || 57.88 (15.75) || 59.06 (15.17) || 0.595 |
| RACE (%) ||  ||  || 0.557 |
| Afric || 20 (20.8) || 22 (22.9) ||  |
| Other || 8 (8.3) || 12 (12.5) ||  |
| White || 68 (70.8) || 62 (64.6) ||  |
| GENDER = Male (%) || 34 (35.4) || 33 (34.4) || 1 |
| MARITAL\_STATUS (%) ||  ||  || 0.938 |
| Divorced || 8 (8.3) || 9 (9.4) ||  |
| Married || 50 (52.1) || 49 (51.0) ||  |
| Single || 29 (30.2) || 27 (28.1) ||  |
| Unknown || 2 (2.1) || 4 (4.2) ||  |
| Widowed || 7 (7.3) || 7 (7.3) ||  |
| GCS\_score (mean (SD)) || 5.24 (3.79) || 5.51 (4.12) || 0.636 |

## ![image](images/inline1_1.jpg)  
7.3 Mediation Analysis

### 7.3.1 Introduction to Mediation Analysis

There are many ways to hypothesize the causal relationship between outcome and variables. For example, in the aforementioned example of the SAH study, we may hypothesize that the association between vasopressors and mortality are influenced by a mediator. The concept of mediation has been used in social science and psychology literature for many decades (e.g., [Rucker et al. 2011](#ch07.xhtml#ref7_58)). Mediation analysis attempts to characterize how the exposure or treatment affects an intermediate variable, and how the affected intermediate variable influences the outcome. This provides insight into biological mechanisms or pathways by which an exposure or treatment affects an outcome. In our SAH example, it is possible the vasopressor influences a patient outcome through a series of processes involving different intermediate stages. One could build and test such a mediation model, but this is beyond the scope of this chapter.

Like the methods above, meditation methods can be illustrated via a so-called “counterfactual” framework for causal inference, which is now widely being used as a tool in formal methodological work in causal inference, statistics, economics, etc. The framework serves as a formal and technical notation to describe the causation. In this section, we will not use the formal notation in the “counterfactual” framework to introduce the mediation analysis. Instead, we will describe the regression-based mediation intuitively, without resorting to the technical notation of the counterfactual ideology. For the interested reader, several texts give more details of the counterfactual framework.

### 7.3.2 The Product Method

The product method was greatly influenced by the work of Baron and Kenny ([Baron and Kenny 1986](#ch07.xhtml#ref7_5)). The causal diagram ([Figure 7.2](#ch07.xhtml#fig7_2)) used in ([Baron and Kenny 1986](#ch07.xhtml#ref7_5)) is a minimalist figure that illustrates the relationship between the cause, mediator, and outcome, in which A denotes an exposure variable, M denotes the mediator, and Y denotes the outcome variable. Let assume other baseline variables as C. Consider the case when the outcome and the mediator are continuous. The following regression models could help explain the effect of “with-the-mediator” and “without-the-mediator”.

![Figure 7.2 Mediation model.](images/fig7_2.jpg)

**Figure 7.2** Mediation model.

*E*(*M*|*A*\=*a*,*C*\=*c*) = *β*[0] + *β*[1]*a* + *β*[2]^′*c*(7.3)

*E*(*Y*|*A*\=*a*,*M*\=*m*,*C*\=*c*) = *θ*[0] + *θ*[1]*a* + *θ*[2]*m* + *θ*[4]^′*c*(7.4)

*θ*[1] can be used to access the direct effect which is a measure to see the influence of the cause *C* on the outcome that is not through the mediator. But here the effect of the mediator and other covariates should be controlled by directly pooling them together into one regression model. It can be understood as the treatment effect on the outcome at a specific level of the mediator. Or one can treat the estimated effect *θ*[1] to the outcome as the effect that is directly relative to the intermediate of interest. There will likely be other intermediates or mechanisms that account for other aspects of the effect of the cause on the outcome (T. [VanderWeele 2015](#ch07.xhtml#ref7_65)). The effect of cause on the outcome through the intermediate is the indirect effect. By this definition, *β*[1]*θ*[2] is the estimator to access the indirect effect, which is the coefficient of the exposure the model 7.3 times the coefficient of the mediator in model 7.4.

### 7.3.3 The Difference Method

The difference method has been widely applied in epidemiology and the biomedical sciences. We will continue to use two regression models for an explanation. Consider the following regression models:

*E*(*Y*|*A*\=*a*,*C*\=*c*) = *ϕ*[0] + *ϕ*[1]*a* + *ϕ*[4]^′*c*(7.5)

*E*(*Y*|*A*\=*a*,*M*\=*m*,*C*\=*c*) = *θ*[0] + *θ*[1]*a* + *θ*[2]*m* + *θ*[4]^′*c*(7.6)

If the exposure coefficient of model 7.5, *ϕ*[1], without the mediator, drops significantly when comparing it with the exposure coefficient of the model 7.4 with the mediator, *θ*[1], it may indicate the effect of mediation because it seems the mediator M has some impact on the effect of the exposure on the outcome (T. J. [VanderWeele 2016](#ch07.xhtml#ref7_66)). The difference *ϕ*[1] − *θ*[1] is commonly referred to as a mediated or indirect effect. Similar to the product method, the exposure coefficient in the model 7.6, *θ*[1], is interpreted as the direct effect.

For the two methods, when the outcome and mediator are continuous and we employ the linear regression model by ordinary least squares, the estimated direct effect and indirect effect are the same. But note that for other scenarios wherein the model is fitted by logistic regression, the product method and the difference method will generate different estimates for the effects.

### 7.3.4 Other Considerations

To ensure the conclusion drawn from the mediation analysis is reliable, four strong assumptions must be satisfied. Basically, all these assumptions are made for the confounding influence. First, it is essential to justify that the confounding factors have been adjusted in the process of mediation analysis. For the details of the assumptions, the reader can refer to (T. [VanderWeele 2015](#ch07.xhtml#ref7_65), T. J. [VanderWeele 2016](#ch07.xhtml#ref7_66)). Since the assumptions are strong and can be easily disregarded in practice, sensitivity analysis is necessary to examine the robustness of the conclusion in a situation where some of the assumptions are not met. Commonly used sensitivity analysis techniques for mediation can be found in the related literature ([Imai, Keele, and Tingley 2010](#ch07.xhtml#ref7_29), [Hafeman 2011](#ch07.xhtml#ref7_22), T. J. [VanderWeele 2016](#ch07.xhtml#ref7_66)).

When considering the interaction between the exposure and a mediator, the estimated direct effect and the estimated indirect effect formulae will change, and also the interpretation will be different. Fortunately, many studies have been done to account for the interaction in mediation analysis. For the interested reader, (T. [VanderWeele 2015](#ch07.xhtml#ref7_65), T. J. [VanderWeele 2016](#ch07.xhtml#ref7_66)) would be good materials.

In this section, we only talk about mediation analysis in the context of ordinary regression models. For other statistical models, such as the logistic regression model and survival models, the idea of the indirect effect and the direct effect can also be generalizable to these situations. Readers could review the paper ([Vanderweele and Vansteelandt 2010](#ch07.xhtml#ref7_67)) for further explanation.

## ![image](images/inline1_1.jpg)  
7.4 Instrumental Variables Networks for Treatment Effect Estimation in the Presence of Unmeasured Confounders

### 7.4.1 Instrumental Variables Frameworks

Instrumental variables (IV) framework is a popular class of methods for the estimation of treatment effects in the presence of unmeasured confounders ([Usaid Awan et al. 2020](#ch07.xhtml#ref7_64)). Consider a trio for treatment effect estimation ([Figure 7.3](#ch07.xhtml#fig7_3)). The trio intends to estimate a causal effect of a treatment *T* on an outcome *Y*. However, both treatment *T* and outcome *Y* can be affected by an observed confounder *U*. To remove the effect of confounder *U*, we use an instrumental variable *Z*. The only observed variables are *T*, *Y* and *Z*. The following three assumptions are essential to the success of the IV approach.

1.  The instrument variable *Z* is associated with the treatment *T*.
    
2.  The instrument variable *Z* is independent of the outcome *Y* given the treatment *T* and all confounders *U*, i.e, *Y* ⫫ *Z* *|*(*T*,*U*).
    
3.  The instrument variable *Z* is independent of factors (measured and unmeasured) that confound the treatment-outcome relationship, i.e, *Z* ⫫ *U*.
    

![Figure 7.3 Trio for treatment effect estimation and instrument variable.](images/fig7_3.jpg)

**Figure 7.3**  
Trio for treatment effect estimation and instrument variable.

Any violation of the three assumptions will lead to the failure of the instrument approach. The variation autoencoder (VAE) and principal component methods for dimension reduction can be used for finding instrument variables. However, the instrumental variables are problem-dependent. For example, they are commonly used to estimate exposure-outcome relationships in EHR studies where a proxy that serves as a semi-randomized variable (such as hospital volume) can be discerned from the records. The selection of appropriate instrument variables is key for the success of the treatment effect estimation in the presence of unmeasured confounders and additional details are beyond the scope of this chapter.

### 7.4.2 Two-Stage Least Square Methods with Linear Models

The methods for IV analysis include two-stage least squares (2SLS) ([Angrist, Graddy, and Imbens 2000](#ch07.xhtml#ref7_1)), generalized method of moments ([Hansen 1982](#ch07.xhtml#ref7_23), [Bennett, Kallus, and Tobias 2019](#ch07.xhtml#ref7_6)), the ratio of coefficients method ([Burgess, Small, and Thompson 2017](#ch07.xhtml#ref7_8)), and likelihood-based methods ([Hayashi 2000](#ch07.xhtml#ref7_26)). In this chapter, we focus on the most popular 2SLS method for IV analysis. The 2SLS method consists of two regression stages: the first-stage regression of the treatment variable on the IVs, and the second-stage regression of the potential outcome on the fitted values of the treatment from the first stage.

#### Simple Linear Models

Consider the causal model in [Figure 7.3.](#ch07.xhtml#fig7_3)

*T* = *β*[*T*|*G*]*G* + *β*[*T*|*U*]*U*(7.7)

*Y* = *β*[*Y*|*T*]*T* + *β*[*Y*|*U*]*U*,(7.8)

where *T* represents a treatment, *Y* is the outcome, *U* is the confounding variable and an instrument variable *G*. We assume that the instrument variable *G* is independent of the confounding variable *U* and is associated with the treatment *T*. The goal of the IV approach is the estimation of a causal effect of the treatment *T* on the outcome *Y*.

#### Covariance Analysis

Without loss of generality, we can assume that *V**a**r*(*G*) = 1 and *V**a**r*(*T*) = 1. By the assumption that the unconfounding variable *U* and the instrument variable *G* are independent, we conclude *c**o**v*(*G*,*U*) = 0. ([Figure 7.3](#ch07.xhtml#fig7_3))

Taking covariance with *G* on both sides of [equation (7.7)](#ch07.xhtml#eqn7_7) yields

*c**o**v*(*T*,*G*) = *β*[*T*|*G*].(7.9)

Similarly, taking covariance with *G* on both sides of [equation (7.8)](#ch07.xhtml#eqn7_8), we obtain

*c**o**v*(*Y*,*G*) = *β*[*Y*|*T*]*c**o**v*(*T*,*G*), which implies that

$\\beta\_{Y|T} = \\frac{\\mathit{cov}\\left( {Y,G} \\right)}{\\mathit{cov}\\left( {T,G} \\right)}.$(7.10)

Define the regression of *Y* on *G*:

*Y* = *β*[*Y*|*G*]*G*.(7.11)

Taking covariance with *G*, we obtain

*c**o**v*(*Y*,*G*) = *β*[*Y*|*G*].(7.12)

Substituting [equations (7.9)](#ch07.xhtml#eqn7_9) and [(7.12)](#ch07.xhtml#eqn7_12) into [equation (7.10)](#ch07.xhtml#eqn7_10) leads to

$\\beta\_{Y|T} = \\frac{\\beta\_{Y|G}}{\\beta\_{T|G}}.$

The causal effect of the treatment *T* on outcome *Y* is estimated by ${\\widehat{\\beta}}\_{\\mathit{Y|T}} = \\frac{\\beta\_{\\mathit{Y|G}}}{\\beta\_{\\mathit{T|G}}}$.

#### Generalized Least Square Estimator

Structural equations for modeling IV model in [equations (7.7)](#ch07.xhtml#eqn7_7) and [(7.8)](#ch07.xhtml#eqn7_8) are

 − *Y* + *β*[*Y*|*T*]*T* + *β*[*Y*|*U*]*U* + *ε*[1] = 0,(7.13) 

 − *T* + *β*[*T*|*G*]*G* + *β*[*T*|*U*]*U* + *ε*[2] = 0(7.14)

where *ε*[1], *ε*[2] are uncorrelated with *U*. Let

*β*[*Y*|*U*]*U* + *ε*[1] = *e*[1],(7.15)

*β*[*T*|*U*]*U* + *ε*[2] = *e*[2].(7.16)

Substituting [equations (7.14)](#ch07.xhtml#eqn7_13) and [(7.16)](#ch07.xhtml#eqn7_16) into [equations (7.13)](#ch07.xhtml#eqn7_13) and [(7.14)](#ch07.xhtml#eqn7_14), we obtain

 − *Y* + *β*[*Y*|*T*]*T* + *e*[1] = 0,(7.17)

 − *T* + *β*[*T*|*G*]*G* + *e*[2] = 0,(7.18)

where *y*, *T* are endogenous variables (its value is determined or influenced by one or more of the independent variables) and denoted by *W* = \[*y**T*\], *G* is an exogenous variable (a variable that is not affected by other variables) and *e*[1], *e*[2] are uncorrelated with *G*.

Let $\\Gamma = \\begin{bmatrix} {- 1} & 0 \\\\ \\beta\_{Y|T} & {- 1} \\\\ \\end{bmatrix}$, $B = {\\lbrack\\begin{matrix} 0 & \\beta\_{T|G} \\\\ \\end{matrix}\\rbrack},E = \\begin{bmatrix} e\_{1} & e\_{2} \\\\ \\end{bmatrix}$, Then $\\Gamma^{- 1} = \\begin{bmatrix} {- 1} & {- \\beta\_{Y|T}} \\\\ 0 & {- 1} \\\\ \\end{bmatrix}$.

Then, [Equations (7.17)](#ch07.xhtml#eqn7_17) and [(7.18)](#ch07.xhtml#eqn7_18) can be rewritten in a matrix form as

*W**Γ* + *G**B* + *E* = 0.(7.19)

Multiplying by *Γ*^( − 1) on both sides of [Equation (7.19)](#ch07.xhtml#eqn7_20), we obtain *W* + *G**B**Γ*^( − 1) + *E**Γ*^( − 1) = 0, which can be reduced to

*W* =  − *G**B**Γ*^( − 1) − *E**Γ*^( − 1) = *G**Π* + *V*(7.20)

where $\\Pi = - B\\Gamma^{- 1},\\Pi = \\begin{bmatrix} 0 & \\beta\_{T|G} \\\\ \\end{bmatrix}$ and *V* =  − *E**Γ*^( − 1).

Using least square methods to solve the optimization problem [(7.20)](#ch07.xhtml#eqn7_21), we obtain

*Π* = (*G*^(*T*)*G*)^( − 1)*G*^(*T*)*W*.(7.21)

Using the relation *Π**Γ* =  − *B*, we obtain (*G*^(*T*)*G*)^( − 1)*G*^(*T*)*W**Γ* =  − *B*, which implies *G*^(*T*)*W**Γ* =  − *G*^(*T*)*G**B* or

$G^{T}\\begin{bmatrix} Y & T \\\\ \\end{bmatrix}\\begin{bmatrix} {- 1} & 0 \\\\ \\beta\_{Y|T} & {- 1} \\\\ \\end{bmatrix} = {- G}^{T}\\begin{bmatrix} 0 & {G\\beta\_{T|G}} \\\\ \\end{bmatrix}.$(7.22)

Expanding [Equation (7.22)](#ch07.xhtml#eqn7_23), we obtain $G^{T}{\\lbrack\\begin{matrix} {- Y + T\\beta\_{\\mathit{Y|T}}} & {- T} \\\\ \\end{matrix}\\rbrack} = G^{T}{\\lbrack\\begin{matrix} 0 & {G\\beta\_{\\mathit{T|G}}} \\\\ \\end{matrix}\\rbrack}$. Therefore, we have

*G*^(*T*)*Y* = *G*^(*T*)*T**β*[*Y*|*T*],(7.23)

*G*^(*T*)*T* = *G*^(*T*)*G**β*[*T*|*G*].(7.24)

[Equations (7.23)](#ch07.xhtml#eqn7_23) and [(7.24)](#ch07.xhtml#eqn7_24) can be rewritten as

$G^{T}\\begin{bmatrix} Y \\\\ T \\\\ \\end{bmatrix} = G^{T}T\\begin{bmatrix} \\beta\_{Y|T} \\\\ \\beta\_{X|G} \\\\ \\end{bmatrix}.$(7.25)

[Equations (7.17)](#ch07.xhtml#eqn7_17) and [(7.18)](#ch07.xhtml#eqn7_18) can be rewritten as

$\\begin{bmatrix} Y \\\\ T \\\\ \\end{bmatrix} = \\begin{bmatrix} T & 0 \\\\ 0 & G \\\\ \\end{bmatrix}\\begin{bmatrix} \\beta\_{Y|T} \\\\ \\beta\_{T|G} \\\\ \\end{bmatrix} + \\begin{bmatrix} e\_{1} \\\\ e\_{2} \\\\ \\end{bmatrix} = Z\\delta + e,$(7.26)

where $Z = \\begin{bmatrix} T & 0 \\\\ 0 & G \\\\ \\end{bmatrix}$ , $\\delta = \\begin{bmatrix} \\beta\_{Y|T} \\\\ \\beta\_{T|G} \\\\ \\end{bmatrix}$ and $e = \\begin{bmatrix} e\_{1} \\\\ e\_{2} \\\\ \\end{bmatrix}$.

Multiplying both sides of [Equation (7.26)](#ch07.xhtml#eqn7_27) by *G*^(*T*), we obtain

*G*^(*T*)*W*^(*T*) = *G*^(*T*)*Z**δ* + *G*^(*T*)*e*.(7.27)

Note that

*Σ* = *c**o**v*(*G*^(*T*)*e*,*G*^(*T*)*e*) = *G*^(*T*)*Λ**G*,(7.28)

where$\\Lambda = \\begin{bmatrix} \\left( \\beta\_{Y|U})^{2}\\sigma\_{U}^{2} + \\sigma\_{\\varepsilon\_{1}}^{2} \\right. & {\\beta\_{Y|U}\\beta\_{T|U}\\sigma\_{U}^{2}} \\\\ {\\beta\_{Y|U}\\beta\_{T|U}\\sigma\_{U}^{2}} & {\\left( \\beta \\right.\_{T|U})^{2}\\sigma\_{U}^{2} + \\sigma\_{\\varepsilon\_{2}}^{2}} \\\\ \\end{bmatrix}$

Using weighted least square methods, we obtain the generalized least square estimator:

*δ̂* = \[*Z*^(*T*)*G*(*G*^(*T*)*Λ**G*)^( − 1)*G*^(*T*)*Z*\]^( − 1)*Z*^(*T*)*G*(*G*^(*T*)*Λ**G*)^( − 1)*G*^(*T*)*W*^(*T*).(7.29)

If we assume *Λ* = *σ*²*I*, then [Equation (7.29)](#ch07.xhtml#eqn7_29) is reduced to

*δ̂* = \[*Z*^(*T*)*G*(*G*^(*T*)*G*)^( − 1)*G*^(*T*)*Z*\]^( − 1)*Z*^(*T*)*G*(*G*^(*T*)*G*)^( − 1)*G*^(*T*)*W*^(*T*).(7.30)

#### Two-Stage Least Square Method

Now we study the relationship between the generalized least square estimator and two-stage least square estimator.

Let

$\\widehat{Z} = \\begin{bmatrix} \\widehat{T} & 0 \\\\ 0 & G \\\\ \\end{bmatrix},$(7.31)

where*X̂* = *G*(*G*^(*T*)*G*)^( − 1)*G*^(*T*)*X*.

[Equation (7.31)](#ch07.xhtml#eqn7_33) can be reduced to

$\\widehat{Z} = \\begin{bmatrix} {G\\left( G^{T}G)^{- 1}G^{T}X \\right.} & 0 \\\\ 0 & {GG^{T}G)^{- 1}G^{T}G} \\\\ \\end{bmatrix} = G\\left( G \\right.^{T}G)^{- 1}G^{T}Z.$(7.32)

Consider two-stage least square estimator:

Stage 1

Solving the regression

*T* = *G**β*[*T*|*G*] + *e*[*T*],(7.33)

we obtain

*β̂*[*T*|*G*] = (*G*^(*T*)*G*)^( − 1)*G*^(*T*)*T* and

*T̂* = *G*(*G*^(*T*)*G*)^( − 1)*G*^(*T*)*T*.(7.34)

Stage 2

Solving the regression*W*^(*T*) = *Ẑ**δ* + *e*[*w*],we obtain

*δ̂* = (*Ẑ*^(*T*)*Ẑ*)^( − 1)*Ẑ*^(*T*)*W*^(*T*).(7.35)

Substituting [Equation (7.32)](#ch07.xhtml#eqn7_32) into [Equation (7.35)](#ch07.xhtml#eqn7_35), we obtain

$\\begin{array}{l} {\\widehat{\\delta} = {\\lbrack Z^{T}G{(G^{T}G)}^{- 1}G^{T}G{(G^{T}G)}^{- 1}G^{T}Z\\rbrack}^{- 1}Z^{T}G{(G^{T}G)}^{- 1}G^{T}W^{T}} \\\\ {\\quad = {\\lbrack Z^{T}G{(G^{T}G)}^{- 1}G^{T}Z\\rbrack}^{- 1}Z^{T}G{(G^{T}G)}^{- 1}G^{T}W^{T},} \\\\ \\end{array}$(7.36)

which is the same as the [Equation (7.30)](#ch07.xhtml#eqn7_32).

#### Nonlinear Models for Two-Stage Least Squares Approach

Here we consider nonlinear models for the 2SLS approach to the treatment effect estimation where covariate variable *X* is included ([Figure 7.4](#ch07.xhtml#fig7_4)). Introducing the following nonlinear structural equation models with additive latent errors that include the confounders ([Mohamed et al. 2019](#ch07.xhtml#ref7_43), [Hartford et al. 2017](#ch07.xhtml#ref7_25)).

*Y* = *g*(*T*,*X*) + *e*,(7.37)

where *Y* is the outcome variable, *T*is the treatment variable, *X* is a vector of covariates, *g*(.,.) is a nonlinear function, *e* is the error including the unobserved confounders. We assume that *E*\[*e*\] = 0. We also assume that the treatment variable is endogenous and is correlated with the error, i.e., *E*\[*e*|*X*,*T*\] ≠ 0 and *E*\[*e**T*|*X*\] ≠ 0.

![Figure 7.4 A general graphical model for IV and treatment effect estimation.](images/fig7_4.jpg)

**Figure 7.4**  
A general graphical model for IV and treatment effect estimation.

Define the potential outcome prediction function ([Hartford et al. 2017](#ch07.xhtml#ref7_25))

*h*(*T*,*X*) = *g*(*T*,*X*) + *E*\[*e*|*X*\].(7.38)

Recall that we assume that the treatment variable is uncorrelated with the error, i.e.,

*E*\[*e*|*T*,*X*\] ≠ *E*\[*e*|*X*\],(7.39)

which implies that

*E*\[*Y*|*T*,*x*\] = *g*(*T*,*X*) + *E*\[*e*|*T*,*X*\] ≠ *g*(*T*,*X*) + *E*\[*e*|*X*\] = *h*(*T*,*X*).(7.40)

Since *E*\[*e*|*X*,*T*\] ≠ 0 and is unknown, [Equation (7.40)](#ch07.xhtml#eqn7_44) shows that *E*\[*Y*|*T*,*x*\] cannot be directly estimated and cannot be estimated by *h*(*T*,*X*). Two unknown quantities *g*(*T*,*X*) and *E*\[*e*|*T*,*X*\] require two equations to solve it. Similar to the 2SLS in the linear models, we introduce instrument variables that allow the establishing of two equations. The previous core assumptions for the IV approach need to be modified to take the covariates into consideration. The new three assumptions ([Hartford et al. 2017](#ch07.xhtml#ref7_25)) are

SETP 1:  
(Relevance): The distribution *F*(*T*|*X*,*Z*) of the treatment *T*, given *X* and *Z*, is not constant in *Z*, i.e, *F*(*T*|*X*,*Z*) depends on *Z*.

STEP 2:  
*Z* ⫫ *Y**|*(*X*,*T*,*e*).

STEP 3:  
**(Unconfounded Instrument**): Instrument variable *Z* is independent of the error, given the covariates *X*, i.e., $Z⫫\\mathit{e|X}\\mspace{-4mu}$ . Assumption implies

*E*\[*e*|*X*,*Z*\] = *E*\[*e*|*X*\].(7.41)

It follows from [Equation (7.37)](#ch07.xhtml#eqn7_41) that

*E*\[*Y*|*X*,*Z*\] = *E*\[*g*(*T*,*X*)|*X*,*Z*\] + *E*\[*e*|*X*,*Z*\].(7.42)

By definition of the conditional distribution, we obtain

*E*\[*g*(*T*,*X*)|*X*,*Z*\] = ∫*g*(*T*,*X*)*d**F*(*T*,*X*|*X*,*Z*) = ∫*g*(*T*,*X*)*d**f*(*T*|*X*,*Z*).(7.43)

By assumption 3, we obtain

$\\begin{array}{l} {E\\left\\lbrack e \\middle| X,Z \\right\\rbrack = \\int{edF\\left( e \\middle| X,Z \\right)}} \\\\ {\\quad = \\int{edF\\left( e,T \\middle| X,Z \\right)}} \\\\ {\\quad = \\int{edF\\left( e \\middle| X,Z7 \\right)dF\\left( T \\middle| X,Z \\right)}} \\\\ {\\quad = \\int{edF\\left( e \\middle| X \\right)dF\\left( T \\middle| X,Z \\right).}} \\\\ \\end{array}$(7.44)

Combining [Equations (7.42)](#ch07.xhtml#eqn7_42)–[(7.44)](#ch07.xhtml#eqn7_44), we obtain

$\\begin{array}{l} {E\\left\\lbrack Y \\middle| X,Z \\right\\rbrack = \\int{\\left\\lbrack {g\\left( {T,X} \\right) + E\\left\\lbrack e \\middle| X \\right\\rbrack} \\right\\rbrack dF\\left( T \\middle| X,Z \\right)}} \\\\ {\\quad = \\pm \\int{h\\left( {T,X} \\right)dF\\left( T \\middle| X,Z \\right)}} \\\\ \\end{array}$(7.45)

To solve [Equation (7.45)](#ch07.xhtml#eqn7_49) for *h*(*T*,*X*), we solve the following optimization problem:

$\\min\\limits\_{h{({T,X})} \\in H}{\\sum\_{i = 1}^{n}\\left( Y\_{i} - \\int{h\\left( {T,X} \\right)\\mathit{dF}\\left( T|X\_{i},Z\_{i})^{2} \\right.} \\right.},$(7.46)

where *H* is a function space.

To remove the correlation between the treatment and error (confounder), we divide the estimation into two stages. At the first stage, we estimate the conditional distribution *F̂*(*T*|*X*,*Z*) of the treatment *T*, given by the IV *Z* and covariates *X*. Then, after replacing *F*(*T*|*X*,*Z*) by *F̂*(*T*|*X*,*Z*), we solve the optimization problem [(7.46)](#ch07.xhtml#eqn7_50).

Under the linear model discussed at [Section 7.4.2](#ch07.xhtml#sec7_004_002):

*Y* = *α**T* + *β**X* + *ε*[*Y*],(7.47)

*T* = *τ**Z* + *γ**X* + *ε*[*T*],(7.48)

where assuming that *E*\[*ε*[*Y*]|*X*,*Z*\] = 0, *E*\[*ε*[*T*]|*X*,*Z*\] = 0.

Under the linear model, we obtain

$\\begin{array}{l} {\\int{\\widehat{h}\\left( {T,X} \\right)dF\\left( T \\middle| X,Z \\right) = \\int\\left. (g\\left( {T,X} \\right) + E\\lbrack e \\middle| X\\rbrack)dF\\left( T \\middle| X,Z \\right) \\right.}} \\\\ {\\quad = \\int\\left. (\\alpha T + \\beta X + E\\lbrack e \\middle| X\\rbrack)dF\\left( T \\middle| X,Z \\right) \\right.} \\\\ {\\quad = \\left. \\alpha E\\lbrack T \\middle| X,Z + E\\rbrack + {\\beta X}. \\right.} \\\\ \\end{array}$(7.49)

Substituting [Equation (7.48)](#ch07.xhtml#eqn7_52) into [Equation (7.49)](#ch07.xhtml#eqn7_53), we obtain

$\\begin{array}{l} {\\int{\\widehat{h}\\left( {T,X} \\right)dF\\left( T \\middle| X,Z \\right) = \\alpha E\\left\\lbrack \\tau Z + \\gamma X + \\varepsilon\_{T} \\middle| X,Z \\right\\rbrack + \\beta X}} \\\\ {\\quad = \\alpha\\left( {\\tau Z + \\gamma X} \\right) + \\beta X} \\\\ \\end{array}$(7.50)

Therefore, we first use least square methods to solve regression problem [(7.48)](#ch07.xhtml#eqn7_52), which results in the estimators *τ̂* and *γ̂*. Then, we substitute *τ̂* and *γ̂* into [Equation (7.50)](#ch07.xhtml#eqn7_54). Finally, we substitute [Equation (7.50)](#ch07.xhtml#eqn7_54) into the objective function in the optimization problem [(7.46)](#ch07.xhtml#eqn7_50) and use the least square methods to solve the resulting optimization problem. The solution to the optimization problem replicates the results in [Section 7.4.2](#ch07.xhtml#sec7_004_002).

Now we introduce some principles for solving the optimization problem [(7.46)](#ch07.xhtml#eqn7_50) with nonlinear models. Let

$L\\left( \\theta \\right) = \\sum\_{i = 1}^{n}\\left( Y\_{i} - \\int{h\\left( {T,X,\\theta} \\right)\\mathit{dF}\\left( T|X\_{i},Z\_{i}{))}^{2} \\right.} \\right.,$(7.51)

where nonlinear function *h*(*T*,*X*,*θ*) can be implemented by deep neural networks and *θ* are parameters in the neural networks. The gradient-based algorithms are often used to solve the optimization problem [(7.51)](#ch07.xhtml#eqn7_55). The gradient of *L*(*θ*) is

$\\left. \\frac{\\partial L\\left( \\theta \\right)}{\\partial\\theta} = 2\\sum\_{i = 1}^{n}\\left( Y\_{i} - \\int{h\\left( {T,X,\\theta} \\right)\\mathit{dF}\\left( T \\middle| {X\_{i},Z\_{i}} \\right)} \\right.\\int\\frac{\\partial h\\left( {T,X,\\theta} \\right)}{\\partial\\theta}\\mathit{dF}\\left( T \\middle| {X\_{i},Z\_{i}} \\right) \\right).$(7.52)

It can be calculated by Monte Carlo integration. The details are beyond the scope of this chapter. We refer the readers to [Mohamed et al. (2019)](#ch07.xhtml#ref7_43).

The conditional distribution *F*(*T*|*X*[*i*],*Z*[*i*]) can be generated by CGANs (Section 7.2.3.4) where *X* and *Z* are condition variables and *T* is a target variable. The generated (*T*,*X*,*Z*) will be substituted into the [Equation (7.52)](#ch07.xhtml#eqn7_56) to calculate the gradient $\\frac{\\partial L\\left( \\theta \\right)}{\\partial\\theta}$. After the solution *ĥ*(*T*,*X*) is calculated, we can estimate the treatment effect as follows.

*I**T**E*(*X*) = *ĥ*(*T*[1],*X*) − *ĥ*(*T*[0],*X*).(7.53)

## ![image](images/inline1_1.jpg)  
7.5 Learning Treatment Effect by Generative Adversarial Networks

### 7.5.1 Introduction

In this section we propose an alternative to using matching to impute counterfactuals and estimating treatment effects. Here, we introduce the generative adversarial networks (GANs) for estimating counterfactuals and treatment effects ([Goodfellow et al. 2014](#ch07.xhtml#ref7_18)). Unlike the classical non-neural network methods that estimate the average treatment effects from observational data, the GANs estimate the individualized treatment effects (ITEs) (Yoon, Jordon, and Schaar 2018), an important step towards “precision medicine”. A great challenge in estimating the ITE is to remove the bias of confounders on the treatment effect estimation, where confounders affect both treatment assignment and outcome. We present an extension of the GANs to the estimation of ITEs in the presence of latent confounders. The GANs and conditional GANs (CGANs) are powerful tools for imputing missing data. The next section will introduce the CGANs as a general framework for imputing the counterfactuals and estimating the ITEs.

### 7.5.2 CGANs as a General Framework for Estimation of Individualized Treatment Effects

A challenge in the estimation of ITEs is the unbiased estimation of counterfactuals. Counterfactuals will never be observed and cannot be tested by data because true counterfactuals are unknown. Recently proposed GANs and CGANs started a revolution in deep learning. GANs and CGANs offer a powerful tool for missing data imputation. GANs and CGANs have the potential to accurately produce the missing data distribution given partial observations and some other information in the data. Therefore, we can use GANs and CGANs to produce potential counterfactuals.

GANs and CGANs consist of two parts: the “generative” part that is called the generator and the “adversarial” part that is called the discriminator. Both generator and discriminator are implemented by neural networks. Typically, a K-dimensional noise vector that may be uniformly distributed or normally distributed is input to the generator network that transforms the noise vector to a new desired fake data instance using nonlinear transformation theory. Then the generated new fake data instance is input to the discriminator network to evaluate them for authenticity. The generator is constantly learning to produce better fake data instances while the discriminator constantly obtains both real and fake data and improves the accuracy of evaluation for authenticity.

#### The Architecture of CGANs for Generating Potential Outcomes

Observed factual and covariates provide basic information for the estimation of counterfactuals. Therefore, we use CGANs as a general framework for ITE estimation. The CGANs for ITE estimation consists of two blocks. The first block is to impute the counterfactuals, which is referred to as to the imputation block. The second ITE block is to estimate the distribution of the treatment effects using the predicted complete dataset produced in the imputation block. The architecture of CGANs is shown in [Figure 7.5](#ch07.xhtml#fig7_5).

*   **Imputation Block**
    
    A counterfactual generator in the imputation block is a nonlinear function of the covariate vector *x* , treatment vector *T*, treatment assignment indicator vector W, observed factual outcome *Y*^(*f*) and *K* dimensional random vector *z*[*G*] with uniform distribution *z*[*G*] ∼ *U*((−1,1)^(*K*)) where ${\\overline{Y}}^{f} = {\\overline{Y}}^{\\eta}$ . The produced potential outcomes by the generator are denoted by
    
    $\\widetilde{Y} = G{({X,{\\overline{Y}}\_{f},{T \\odot W,\\left( {1 - W} \\right) \\odot z}\_{G},\\theta\_{G}})},$(7.54)
    
    where output *Ỹ* represents a sample of *G*. It can take binary values, categorical values, or continuous values. 1 is a vector of 1, ⊙ denotes element-wise multiplication and *θ*[*G*] are the parameters in the generator. The generator is implemented by a neural network. We use *Y* to denote the complete dataset that is obtained by replacing *Ỹ*^(*η*) with ${\\overline{Y}}^{f}$.
    
    The distribution of *Ỹ* depends on the determinant of the Jacobian matrix of the nonlinear transformation function $G\\left( {X,{\\overline{Y}}^{f},\\mathit{T},W,z\_{G},\\theta\_{G}} \\right)$ using a transformation theorem (Ross, n.d.). Changing the transformation function can change the distribution of the generated counterfactuals. Let *P*[*Y**|**x*, *t*, *w*, *y*^(*f*)](*y*) be the conditional distribution of the potential outcomes, given *X* = *x*, *T* = *t*, *W* = *w*, *Y*^(*f*) = *y*^(*f*). The goal of the generator is to learn the neural network *G* such that *G*(*x*,*y*^(*f*),*t*,*w*,*z*[*G*],*θ*[*G*]) ∼ *P*[*Y**|**x*, *t*, *w*, *y*^(*f*)](*y*).
    
    Unlike the discriminator in the standard CGANs where the discriminator evaluates the input data for their authenticity (real or fake data), the counterfactual discriminator *D*[*G*] that maps pairs (*x*,*y*) to vectors in \[0,1\]^(*k*) attempts to distinguish the factual component from the counterfactuals. The output of the counterfactual discriminator *D*[*G*] is a vector of probabilities that the component represents the factual outcome. Let *D*[*G*](*x*,*ỹ*,*t*,*w*,*θ*[*d*])[*k*] represent the probability that the *i*^(*t**h*) component of *ỹ* is the factual outcome, i.e., *k* = *η*, where *θ*[*d*] denotes the parameters in the discriminator. The goal of the counterfactual discriminator is to maximize the probability *D*[*G*](*x*,*ỹ*,*t*,*w*,*θ*[*d*])[*k*] for correctly identifying the factual component *η* via changing the parameters in the discriminator neural network *D*[*G*].
    
*   **Loss Function**
    

![Figure 7.5 CGANs for estimating ITEs.](images/fig7_5.jpg)

**Figure 7.5**  
CGANs for estimating ITEs.

The imputation block attempts to impute counterfactuals by extending the loss function of binary treatment in ([Yoon et al. 2018](#ch07.xhtml#ref7_72)) to all types of treatments: binary, categorical or continuous treatments, we define loss function *V*(*D*[*G*],*G*,*θ*[*d*]) as*E*[(*x*, *t*, *w*, *y*^(*f*)) ∼ *P*[*d**a**t**a*](*x*, *t*, *w*, *y*^(*f*))]*E*[*z*[*G*] ∼ *u*(( − 1, 1)^(*K*))]\[*W*^(*T*)log*D*[*G*](*X*,*Ỹ*,*T*,*W*) + (1−*W*)^(*T*)log(1−*D*[*G*](*X*,*Ỹ*,*T*,*W*))\],

where the log is an element-wise operation.

The goal of imputation block is to maximize the counterfactual discriminator *D*[*G*] and then minimize the counterfactual generator *G*:

$\\min\\limits\_{G}{\\max\\limits\_{D\_{G}}{V\\left( {D\_{G},G,\\theta\_{d}} \\right)}}.$(7.55)

In other words, we train the counterfactual discriminator *D*[*G*] to maximize the probability of correctly identifying the assigned treatment *T*^(*η*) or *Y*^(*f*)(*Y*^(*η*)), and then train the counterfactual generator *G* to minimize the probability of correctly identifying *T*^(*η*). After the imputation block is performed, the counterfactual generator *G* produces the complete dataset $\\overline{D} = x,y$. Next, we use the imputed complete dataset $\\overline{D} = X,y$ to generate a distribution of potential outcomes and to estimate the individualized treatment effects via standard CGANs which is called the ITE block.

#### CGANs for Estimating ITEs

*   **ITE Block**
    
    The standard CGANs consist of three parts: generator, discriminator and loss function which is summarized as follows (Yoon, Jordon, and Schaar 2018); Ge et al. 2019)
    
*   **ITE Generator**
    
    The ITE generator *G*[*I*] is a nonlinear transform function of *X* and *Z*[*I*]:
    
    *Ŷ* = *G*[*I*](*X*,*Z*[*I*],*θ*[*g*[*I*]]),(7.56)
    
    where *Ŷ* is the generated *K*\-dimensional vector of potential outcomes, *X* is a covariant vector and *Z*[*I*] is a *K*\-dimensional vector of random variables and follow the uniform distribution *Z*[*I*] ∼ *u*((−1,1)^(*K*)). The ITE generator attempts to find the transformation *Ŷ* = *G*[*I*](*X*, *Z*[*I*,]*θ*[*g*[*I*]]) such that *Ŷ* ∼ *P*[*Y**|**X*](*y*).
    
*   **ITE Discriminator**
    
    Following the standard CGANs, we define a discriminator *D*[*I*] as a nonlinear classifier with a pair (*X*,*Y*^(\*)\=*Y*) or (*X*,*Y*^(\*)\=*Ŷ*) as input and a scalar that outputs the probability of *Y*^(\*) being from the complete dataset $\\overline{D}$.
    
*   **Loss Function**
    
    A loss function for the ITE block is defined as
    
    *V*[*I*](*D*[*I*],*G*[*I*]) = *E*[*X* ∼ *P*(*x*)]\[*E*[*Y*^(\*) ∼ *P*[*Y*|*X*]](*y*)\[log*D*[*I*](*X*,*Y*^(\*))\]+*E*[*Z*[*I*] ∼ *u*(( − 1, 1)^(*K*))]\[log(1−*D*[*I*](*X*,*Y*^(\*))\]\](7.57)
    
    where *D*[*I*](*X*,*Y*^(\*)) is a nonlinear classifier that determines whether *Y*^(\*) is from the complete dataset $\\overline{D}$ or from generator *G*[*I*].
    
    The goal of the ITE block is to maximize the probability of correctly identifying that *Y*^(\*) is from the complete dataset $\\overline{D}$ and to minimize the probability of correct classification. Mathematically, ITE attempts
    
    $\\min\\limits\_{G\_{I}}{\\max\\limits\_{D\_{I}}{V\_{I}\\left( {D\_{I},G\_{I}} \\right)}}.$(7.58)
    
    The algorithms for numerically solving the optimization problems (7.4) and (7.7) consist of the following steps.
    
    To solve the optimization problems (7.4) and (7.7), we need to use sampling formulas to approximate the expectations. Therefore, we first discuss the implementation of the imputation block.
    
*   **Imputation Block Optimization**
    
    Assume that *n* individuals are sampled. Sampling approximation of *V*(*D*[*G*],*G*) is given by
    
    $\\widehat{V}\\left( {D\_{G},G} \\right) \\approx \\frac{1}{n}\\sum\_{i = 1}^{n}{\\left\\lbrack W \\right.\_{i}^{T}\\log{\\left( {D\_{G}\\left( X\_{i},T\_{i},{\\widetilde{Y}}\_{i},W\_{i},\\theta\_{d} \\right.} \\right) + \\left( 1 - W\_{i})^{T}\\log{\\left( 1 - D\_{G}\\left( {X\_{i},T\_{i},{\\widetilde{Y}}\_{i},W\_{i},\\theta\_{d}} \\right) \\right)\\rbrack} \\right.}},$(7.59)
    
    where *Ỹ* = *G*(*X*,*Y*^(*f*),*T* ⊙ *W*, (1−*W*) ⊙ *Z*[*G*],*θ*[*G*]).
    
    To enforce that the estimated factual outcome *Ỹ*[*i*]^(*η*)should be as close to the observed factual outcome *Y*[*i*]^(*f*) as possible(Yoon, Jordon, and Schaar 2018), we post the following restriction:
    
    $l\\left( G \\right) = \\frac{1}{n}\\sum\_{i = 1}^{n}\\left( Y\_{i}^{f} - {\\widetilde{Y}}\_{i}^{\\eta})^{2} \\right..$(7.60)
    
    The optimization problem (7.4) can be implemented by
    
    $\\min\\limits\_{D\_{G}}{- \\widehat{V}\\left( {D\_{G},G} \\right)},$(7.61)
    
    $\\min\\limits\_{G}{\\widehat{V}\\left( {D\_{G},G} \\right) + \\lambda l\\left( G \\right)}.$(7.62)
    
    Optimization problems (7.10) and (7.11) can be solved by backpropagation (stochastic gradient descent) algorithms. The details for the algorithms are given in supplementary note A.
    
*   **ITE Block Optimization**
    

ITE block intends to estimate the counterfactuals using the observed outcomes and imputed counterfactuals. Its performance metrics are defined as$L\\left( G\_{I} \\right) = \\frac{1}{n}\\sum\_{i = 1}^{n}\\left| \\left| {Y\_{i} - {\\widehat{Y}}\_{i}} \\right| \\right|\_{2}^{2}.$

Sampling formula for *V*[*I*](*D*[*I*],*G*[*I*]) is${\\widehat{V}}\_{I}\\left( {D\_{I},G\_{I}} \\right) = \\frac{1}{n}\\sum\_{i = 1}^{n}\\left\\lbrack \\log{D\_{I}\\left( X\_{i},Y\_{i}^{\\ast} \\right) + \\log\\left( \\left. 1 - D\_{I}\\left( {X\_{i},Y\_{i}^{\\ast}} \\right) \\right) \\right)} \\right..$

The optimization problem (7.7) for ITE can be reformulated as

$\\min\\limits\_{D\_{I}}{- {\\widehat{V}}\_{I}\\left( {D\_{I},G\_{I}} \\right)},$(7.63)

$\\min\\limits\_{G\_{I}}{{\\widehat{V}}\_{I}\\left( {D\_{I},G\_{I}} \\right) + \\gamma}L\\left( G\_{I} \\right).$(7.64)

Again, stochastic gradient descent methods can be used to solve optimization problems (7.12) and (7.13). Algorithms for their numerical implementation are similar to the algorithms for the imputation block.

#### CGANs for Estimating ITEs in Survival Analysis

*   **Background in Survival Analysis**
    
    An essential issue for survival time analysis is how to deal with censoring time. Let ${\\overline{Y}}\_{i} = \\left\\lbrack {\\overline{Y}}\_{i}^{1},\\ldots,{\\overline{Y}}\_{i}^{K}\\rbrack^{T} \\right.$ be the vector of potential outcomes (survival time) for the *i*^(*t**h*) subject, where ${\\overline{Y}}\_{i}^{k}$ is the potential outcome (survival time) if the *i*^(*t**h*) subject had received the *k*^(*t**h*) treatment. We only observe the component of the potential outcome vector ${\\overline{Y}}\_{i}$ that corresponds to the assigned treatment, which is called the factual outcome and is denoted by ${\\overline{Y}}\_{i}^{f}$. Other unobserved potential outcomes (survival times) are called counterfactual outcomes (survival times), or simply counterfactuals, and denoted by ${\\overline{Y}}\_{i}^{\\mathit{cf}}$. The factual outcome (survival time) ${\\overline{Y}}\_{i}^{f}$ can be expressed as${\\overline{Y}}\_{i}^{f} = \\sum\_{k = 1}^{K}{W\_{i}^{k}{\\overline{Y}}\_{i}^{k}}.$
    
    Each subject is associated with *K* potential outcomes (survival times) ${\\overline{Y}}\_{i}^{k}$ , but only one of them can be observed as ${\\overline{Y}}\_{i}^{f}$. Let *X*[*i*] = \[*x*[*i*1],…,*x*[*i**p*]\]^(*T*) be a vector of covariates associated with the *i*^(*t**h*) subject, including miRNA, age, sex and other geographic and tumor feature variables. Assume that *n* subjects are sampled. For the sake of simplicity, the subscript *i* for indexing the subject is omitted when the context is clear.
    
    Next, we consider censoring. The reasons for censoring include: 1) loss to follow-up and 2) deaths from other causes. Let *L*[*i*] be an indicator variable for the censored event where *l*[*i*] = 1 denotes that the *i*^(*t**h*) subject is not censored and *l*[*i*] = 0 denotes that the *i*^(*t**h*) subject is censored. Let *C*[*i*] be the censoring time for the *i*^(*t**h*) subject. The potential time to event (death or censored) *Z* = \[*Z*¹,…,*Z*^(*K*)\]^(*T*)is defined as
    
    $Z^{k} = \\min{\\left\\{ {{\\overline{Y}}^{k},C} \\right\\},k = 1,\\ldots,K},$(7.65)
    
    and the factual (observed) time to event is
    
    $Z^{f} = \\sum\_{k = 1}^{K}{W^{k}Z^{k}}.$(7.66)
    
    Define the indicator variable for the *k*^(*t**h*) potential survival time censoring to indicate that it is less than the censoring time as
    
    $\\delta^{k} = I\\left( {C \\geq {\\overline{Y}}^{k}} \\right)$(7.67)
    
    and
    
    the indicator variable for the all potential survival time censoring as
    
    $\\delta = \\sum\_{k = 1}^{K}{W^{k}\\delta^{k}}.$(7.68)
    
    The data for the treatment effect estimation with censoring survival time is (*Y*,*W*,*T*,*X*,*δ*,*Z*). Assumption 2 (*Z* ⫫ *Y**|*(*X*,*T*,*e*) needs to be extended to censoring data.
    
    STEP 1: The treatment assignment is independent of censored and uncensored survival time given the covariates. Formally, we assume
    
    $\\left( \\overline{Y},Z \\right)⫫W|X.$(7.69)
    
    Similar to the assumption for the treatment assignment, we also make the following assumption about the independence of the censoring time from the survival times and covariates:
    
    STEP 2: $\\left( \\overline{Y},Z,X \\right)⫫C|W.$
    
*   ***Loss Function of the CGANs for Estimating ITEs in Survival Analysis***
    

The data in survival analysis consist of two parts: 1) noncensored data *D*[*n**c*] and 2) censored data *D*[*c*] . In survival analysis, the produced potential outcomes (survival time) by the generator in [Equation (7.3)](#ch07.xhtml#eqn7_3) should be changed to

$\\widetilde{Y} = G{({X,{\\overline{Y}}\_{f},{T \\odot W,\\left( {1 - W} \\right) \\odot z}\_{G},l,\\theta\_{G}})}.$(7.70)

The loss function for the uncensored data *D*[*n**c*] is given by

$\\begin{array}{l} {V\\left( {D\_{G}, G, D\_{nc}} \\right) = E\_{{({x,t,w,y^{f}})}\\sim P\_{D\_{nc}}{({x,t,w,y^{f}})}}E\_{z\_{G}\\sim u({({- 1,1)^{K}})}}\\left\\lbrack W \\odot \\log D\_{G}(X,\\widetilde{Y},T, W, l = 1) \\right\\rbrack} \\\\ {\\left. + (1 - W) \\odot \\log(1 - D\_{G}\\left( {X,\\widetilde{Y},T, W,l = 1} \\right)) \\right\\rbrack.} \\\\ \\end{array}$(7.71)

For the censored data *D*[*c*], we should introduce the second loss function *V*(*D*[*c*]) to enforce the constraints: $Z^{k} = \\min{\\left\\{ {{\\overline{Y}}^{k},C} \\right\\},\\mathit{k} = 1,\\ldots,\\mathit{K}}$:

$V\\left( {D\_{G},G,D}\_{c} \\right) = E\_{{({x,t,w,y^{f}})}\\sim P\_{D\_{c}(x,t,w,}y^{f})}\\left\\lbrack \\max\\left( 0, \\right.C - G{({X,{\\overline{Y}}\_{f},{T \\odot W,\\left( {1 - W} \\right) \\odot z}\_{G},l = 0,\\theta\_{G}})}. \\right.$(7.72)

Using the Lagrangian multiplier, we can incorporate the constraints into the loss function (7.20) to obtain the total loss function of CGANs for estimating ITEs in the survival analysis:

*V*(*D*[*G*],*G*,*D*[*n**c*],*D*[*c*]) = *V*(*D*[*G*],*G*,*D*[*n**c*]) + *λ**V*(*D*[*G*], *G*, *D*[*c*]),(7.73)

where *λ* is a tuning parameter that controls the trade-off between the censored and noncensored loss function. We often set *λ* = 1.

To obtain the ITEs in survival analysis, we solve the following optimization problems

$\\min\\limits\_{G}{\\max\\limits\_{D\_{G}}{V\\left( {D\_{G},G,D\_{\\mathit{nc}},D\_{c}} \\right)}}.$(7.74)

### 7.5.3 Wasserstein GANs for Estimation of Individualized Treatment Effects

It is well-known that training GAN is difficult because we often face limitations such as its convergence and model collapse problems. Wasserstein GANs (WGANs) can be used to overcome these limitations ([Arjovsky and Bottou 2019](#ch07.xhtml#ref7_2)). The major difference between WGANs and GANs is loss function. We only need to introduce a loss function for WGANs. The architectures of the neural networks are the same as those in [Section 7.2.3](#ch07.xhtml#sec7_002_003). The loss function *V*[*W*](*D*[*G*],*G*,*θ*[*d*]) of WGANs for imputation of the counterfactuals is given by

**V**[**W**](*D*[*G*],*G*,*θ*[*d*]) = *E*[*x*, *t*, *w*, *y*^(*f*)) ∼ *P*[*d**a**t**a*](*x*, *t*, *w*, *y*^(*f*))]*E*[*z*[*G*] ∼ *u*(( − 1, 1)^(*K*))]\[*W*⊙*D*[*G*](*X*,(*X*,*Ỹ*,*T*,*W*)− (1−*W*)⊙*D*[*G*](*X*,(*X*,*Ỹ*,*T*,*W*)\],(7.75)

where

*Ỹ* = *G*(*X*,*Y*^(*f*),*T* ⊙ *W*, (1−*W*) ⊙ *Z*[*G*],*θ*[*G*]) and *D*[*G*] is the set of 1-Lipschitz functions. We usually use the neural networks to implement *D*[*G*], which satisfies the 1-Lipschitz condition.

To impute the counterfactuals, we solve the following optimization problem:

$\\min\\limits\_{G}{\\max\\limits\_{D\_{G}}{V\\left( {D\_{G},G,\\theta\_{d}} \\right)}}.$(7.76)

The loss function of WGANs for the ITE block is

*V*[*I*](*D*[*I*],*G*[*I*]) = *E*[*X* ∼ *P*(*x*)]\[*E*[*Y*^(\*) ∼ *P*[*Y*|*X*]](*y*)\[*D*[*I*](*X*,*Y*^(\*))\]−*E*[*Z*[*I*] ∼ *u*(( − 1, 1)^(*K*))]\[*D*[*I*](*X*,*Y*^(\*))\]\],(7.77)

where *D*[*I*] is the set of 1-Lipschitz functions, other quantities are defined as in [Section 7.2.3](#ch07.xhtml#sec7_002_003).

### 7.5.4 MisCGANs for Estimation of Individualized Treatment Effects

#### The General Process for Incompletely Observed Data

The general process for incompletely observed data can be statistically described by two random vectors (S. C.-X. [Li, Jiang, and Marlin 2019](#ch07.xhtml#ref7_37), [Little and Rubin 2002](#ch07.xhtml#ref7_38)). Let *X* ∈ *R*^(*n*) be a vector of the complete data and *M* ∈ {0, 1}^(*n*) be a *n*\-dimensional binary mask vector to indicate whether the components in the data vector are missing or not. The statistical model for describing incompletely observed data is given by

*X* ∼ *P*[*θ*](*X*) and *M* ∼ *P*[*ω*](*M*|*X*).

To characterize the missing mechanism of the data, the complete dataset *X* is decomposed into the observed components *X*[*o**b**s*] of *X* and the missing components *X*[*m**i**s*] of *X*, i.e., *X* = \[*X*[*o**b**s*],*X*[*m**i**s*]\]. Therefore, the distribution of the mask vector can be expressed as *P*[*ω*](*M*|*X*[*o**b**e*],*X*[*m**i**s*]). Based on the relationships between the complete data *X* and the mask *M*, the missing mechanisms can be classified into three scenarios ([Little and Rubin 2002](#ch07.xhtml#ref7_38), S. C.-X. [Li, Jiang, and Marlin 2019](#ch07.xhtml#ref7_37)):

1.  If the mask is independent of the complete data, i.e, *P*[*ω*](*M*|*X*) = *P*[*ω*](*M*) , then missing mechanism is completely at random (MCAR);
    
2.  If the mask I independent of the missing data, i.e, *P*[*ω*](*M*|*X*) = *P*[*ω*](*M*|*X*[*o**b**s*]), then the missing is missing at random(MAR);
    
3.  If the missing depends on the complete dataset *X*, then there are no missing at random (NMAR).
    

In this chapter, we consider only MCAR. Then, the joint probability *P*(*x*,*m*) can be factorized into *P*(*X*,*M*) = *P*(*X*)*P*(*M*).

#### MisGAN for Counterfactual Imputation

In this section, we study how the MisGAN (S. C.-X. [Li, Jiang, and Marlin 2019](#ch07.xhtml#ref7_37)) is applied to the ITE estimation problem. The missing data in the ITE estimation problem is due to the counterfactuals. The complete data vector is ${\\overline{Y}}\_{i}$ and the partially observed data is ${\\overline{Y}}\_{i}^{f}$. The treatment assignment vector *W*[*i*] plays a mask role. In other words, if *W*[*i*]^(*k*) = 1 then the potential outcome (factual) is observed and if *W*[*i*]^(*k*) = 0 then a vector of counterfactuals ${\\overline{Y}}\_{i}^{\\mathit{cf}}$ is unobserved. Similar to the paper (S. C.-X. [Li, Jiang, and Marlin 2019](#ch07.xhtml#ref7_37)), an incomplete dataset is denoted $D = \\left( {{\\overline{Y}}\_{i},W\_{i}} \\right),i = 1,\\ldots,n$.

A masking operator that fills counterfactuals with a constant value *τ* is defined as

$f\_{\\tau}\\left( {\\overline{Y},W} \\right) = \\overline{Y} \\odot W + \\tau\\left( {1 - W} \\right),$(7.78)

where ⊙ represents elements-wise multiplication.

We first generate the distribution of the mask (treatment assignment) vector *W*. The architecture of the MisGAN for generating a distribution of the mask is shown in [Figure 7.6](#ch07.xhtml#fig7_6). We define *G*[*Y*] as

${\\overline{Y} = G}\_{Y}\\left( {X,{\\overline{Y}}^{f},T,Z\_{G}} \\right).$(7.79)

![Figure 7.6 The architecture of the MisGAN for generating a distribution of the mask.](images/fig7_6.jpg)

**Figure 7.6**  
The architecture of the MisGAN for generating a distribution of the mask.

The mask *Ŵ* (the treatment assignment) is generated by

*Ŵ* = *G*[*W*](*ε*).(7.80)

Both *G*[*Y*] and *G*[*W*] are implemented by neural networks.

Unlike the standard CGANs where there is only one generator-discriminator pair, the MisGANs have two generator-discriminator pairs (*G*[*W*],*D*[*W*]) and (*G*[*Y*],*D*[*Y*]) for the mask (treatment assignment indicator) and potential outcomes, respectively. Since we assume that the treatment assignment and potential outcomes are independent, we have two independent noises *Z*[*G*] and *ε* with distributions *P*[*Z*] and *P*[*ε*]. The loss functions, one for the masks and the other for the data (potential outcomes) are defined as follows.

*V*[*W*](*D*[*W*],*G*[*W*]) = *E*[(*Y*, *W*) ∼ *P*[*d**a**t**a*]]\[*D*[*W*](*W*)\] − *E*[*ε* ∼ *P*[*ε*]]\[*D*[*W*](*G*[*W*](*ε*))\],(7.81)

$V\_{Y}\\left( {D\_{Y},G\_{Y},G\_{W}} \\right) = E\_{{({Y,W})}\\sim P\_{\\mathit{data}}}\\left\\lbrack D\_{Y}{({f\_{\\tau}\\left( {\\overline{Y},W} \\right)})} - E\_{Z\\sim P\_{Z},\\varepsilon\\sim P\_{\\varepsilon}}\\left\\lbrack D\_{Y}\\left( f\_{\\tau}\\left( {G\_{Y}\\left( {X,{\\overline{Y}}^{f},T,Z\_{G}} \\right),G\_{W}\\left( \\varepsilon \\right)} \\right) \\right\\rbrack,\\quad \\right. \\right.$(7.82)

where *D*[*W*] and *D*[*Y*] are both 1-Lipschitz functions.

The loss functions in (7.30) and (7.31) follow W-GANs. To find *D*[*W*], *D*[*Y*] and *G*[*Y*], we solve the following optimization problems:

min[*G*[*Y*]]max[*D*[*Y*] ∈ *F*[*Y*]]*V*[*Y*](*D*[*Y*],*G*[*Y*],*G*[*W*]),(7.83)

min[*G*[*W*]]max[*D*[*W*] ∈ *F*[*W*]]*V*[*W*](*D*[*W*],*G*[*W*]) + *λ**V*[*Y*](*D*[*Y*],*G*[*Y*],*G*[*W*]),(7.84)

where *F*[*Y*], *F*[*W*] are the families of 1-Lipschitz functions, *λ* is often set to *λ* = 0.2.

Finally, we investigate the imputation of the counterfactuals. We will impute counterfactuals according to the conditional distribution $P\\left( {\\overline{Y}}^{\\mathit{cf}} \\middle| {\\overline{Y}}^{f} \\right)$ by adding an imputer *G*[*i*] and discriminator *D*[*i*] to [Figure 7.5](#ch07.xhtml#fig7_5). The formed new architecture of the MisGANs is shown in [Figure 7.7](#ch07.xhtml#fig7_7). The imputer *G*[*i*] is a nonlinear function of the covariates *X*, the potential outcomes (factual, the estimated counterfactuals in [Figure 7.5](#ch07.xhtml#fig7_5)), the treatment vector, the mask (treatment assignment vector) and noise and defined as

$G\_{i}\\left( {X,\\overline{Y},T,W,Z\_{\\omega}} \\right) = \\overline{Y} \\odot W + G\_{\\mathit{iy}}\\left( {X,{\\overline{Y}}^{f},T \\odot W,\\left( {1 - W} \\right) \\odot Z\_{\\omega}} \\right) \\odot \\left( {1 - W} \\right).$(7.85)

![Figure 7.7 The architecture of the MisGAN for estimating ITEs.](images/fig7_7.jpg)

**Figure 7.7**  
The architecture of the MisGAN for estimating ITEs.

The loss function for imputing the counterfactuals is defined as

$V\_{i}\\left( {D\_{i},G\_{i},G\_{Y}} \\right) = E\_{Z\_{G}\\sim P\_{Z}}\\left\\lbrack {D\_{i}\\left( {G\_{Y}\\left( {X,{\\overline{Y}}^{f},T,Z\_{G}} \\right)} \\right)} \\right\\rbrack - E\_{{({Y,W})}\\sim P\_{\\mathit{data}},,Z\_{\\omega}\\sim P\_{\\omega}}\\left\\lbrack {D\_{i}\\left( G \\right.}\_{i}\\left( {X,\\overline{Y},T,W,Z\_{\\omega}} \\right) \\right)\\rbrack.$(7.86)

To estimate ITEs, we jointly solve the following optimization problems:

min[*G*[*i*]]max[*D*[*i*] ∈ *F*[*i*]]*V*[*i*](*D*[*i*],*G*[*i*],*G*[*Y*]),(7.87)

min[*G*[*Y*]]max[*D*[*Y*] ∈ *F*[*Y*]]*V*[*Y*](*D*[*Y*],*G*[*Y*],*G*[*W*]) + *β**V*[*i*](*D*[*i*],*G*[*i*],*G*[*Y*]),(7.88)

min[*G*[*W*]]max[*D*[*W*] ∈ *F*[*W*]]*V*[*W*](*D*[*W*],*G*[*W*]) + *λ**V*[*Y*](*D*[*Y*],*G*[*Y*],*G*[*W*]).(7.89)

### 7.5.5 Optimal Treatment Selection

#### Sparse Techniques for Biomarker Identification

The LASSO (least absolute shrinkage and selection operator) that performs both variable selection and regularization to enhance the prediction accuracy and interpretability of the results can be used to select biomarkers for optimal treatment election ([Diamond and Sekhon 2013](#ch07.xhtml#ref7_12), [Ge et al. 2020](#ch07.xhtml#ref7_17)) Let *y*[*t*]^(*i*) and *X*^((*i*)) denote the estimated treatment effect and feature vector of the *i*^(*t**h*) individual, respectively. Let$Y\_{T} = \\begin{bmatrix} y\_{t}^{(1)} \\\\ \\vdots \\\\ y\_{t}^{(n)} \\\\ \\end{bmatrix},\\mathit{X} = \\begin{bmatrix} x\_{1}^{(1)} & \\cdots & x\_{q}^{(1)} \\\\ \\vdots & \\vdots & \\vdots \\\\ x\_{1}^{(n)} & \\cdots & x\_{q}^{(n)} \\\\ \\end{bmatrix},\\beta = \\begin{bmatrix} \\beta\_{1} \\\\ \\vdots \\\\ \\beta\_{q} \\\\ \\end{bmatrix}.$

The outputs of the neural networks are, in general, continuous functions even if the potential outcomes are binary. Therefore, we assume that the treatment effects are continuous regardless of the data types of the potential outcomes.

The LASSO estimators for the discovery of biomarkers that predict treatment effects are${\\widehat{\\beta}}\_{\\lambda} = \\underset{\\beta}{argmin}{{||}Y\_{T} - X\\beta||\_{2}^{2}} + \\lambda\\sum\_{j = 1}^{q}{|\\beta\_{j}|}.$

The correspondence *X*[*j*] of nonzero elements *β*[*j*] ≠ 0 represents the biomarkers for treatment effect prediction.

#### Biomarker Identification for Optimal Treatment Selection

Consider *K* treatments. Let *Ŷ*^(*i*) = \[*Ŷ*^(*i*)(*T*[1]^(*i*)),…,*Ŷ*^(*i*)(*T*[*K*]^(*i*))\]^(*T*) be the *K*\-dimensional vector of estimated potential outcomes for the *i*^(*t**h*) individual and *z*[*i*] = *a**r**g**m**a**x*[1, .., *K*]*Ŷ*^(*i*)(*T*[1]^(*i*)), …, *Ŷ*^(*i*)(*T*[*K*]^(*i*)) be the index of the optimal potential outcomes of the *i^(th)* individual. To select biomarkers for optimal treatment selection, we define the following LASSO:${||}{\\widehat{Y}}^{i}\\left( T\_{z\_{i}}^{i} \\right) - \\sum\_{j = 1}^{q}{x\_{j}^{(i)}\\beta\_{j}||^{2} + \\lambda\\sum\_{j = 1}^{q}{|\\beta\_{j}|}},i = 1,\\ldots,n.$

Solving the above LASSO problem, we obtain a set of non-zero coefficients that are denoted as *β̂*[*l*] ≠ 0, *l* = 1, …, *L*. The covariates that correspond to the non-zero coefficients of the LASSO solution are chosen as biomarkers for optimal treatment selection.

## ![image](images/inline1_1.jpg)  
7.6 Deconfounder in Estimation of Treatment Effects

### 7.6.1 Introduction

Dealing with confounders, which by definition affect both the treatment and outcomes, is a central problem in the estimation of treatment effects (T. [VanderWeele 2015](#ch07.xhtml#ref7_65), [Zhang et al. 2019](#ch07.xhtml#ref7_74), [Lee, Mastronarde, and van der Schaar 2018](#ch07.xhtml#ref7_35)) Consider an example, we assume that smoking is a treatment (*T*), mortality is the outcome (*Y*) and gender is the confounder (*X*) ([Figure 7.8(a)](#ch07.xhtml#fig7_8)). Assume that gender may affect smoking and mortality. We observe that males are more likely to smoke than females and are also more likely to die young due to other risk behaviors. A difference in mortality between smokers and non-smokers may be due to smoking, gender, or may be due to both. In this case, gender is a confounder. This example demonstrates that estimating treatment effect in the presence of confounders will be biased.

![Figure 7.8 (a) Causal diagram without confounder. (b) Causal diagram with confounder.](images/fig7_8.jpg)

**Figure 7.8**  
(a) Causal diagram without confounder. (b) Causal diagram with confounder.

If the confounders can be measured, we can take the measured confounders to adjust for other confounders. However, many confounders cannot be measured or are simply unknown. For example, a social-economic status that affects both the treatment the patients receive and the health conditions of the patients is an unmeasured confounder. The unadjusted confounders will seriously influence the estimation of the treatment effects. To estimate the treatment effects with little to no bias in the presence of unobserved confounders poses a great challenge. The methods for de-confounding include generative implicating models ([Lee, Mastronarde, and van der Schaar 2018](#ch07.xhtml#ref7_35)), data reduction methods ([Zhang et al. 2019](#ch07.xhtml#ref7_74)), confounder selection (T. VanderWeele 2015a), reinforcement learning (C. [Lu, Schölkopf, and Hernández-Lobato 2018](#ch07.xhtml#ref7_41)), and instrumental variable methods (Usaid Awan et al. 2019). In this section, we focus on generative adversarial learning ([Lee, Mastronarde, and van der Schaar 2018](#ch07.xhtml#ref7_35)).

### 7.6.2 Causal Models with Latent Confounders

We introduce causal models with unobserved confounders ([Lee, Mastronarde, and van der Schaar 2018](#ch07.xhtml#ref7_35)). We assume that a latent confounder *Z* affects both the treatment variable *T* (binary treatment) and outcome variable *Y*. Suppose that there exists a proxy variable *X* that approximates the latent variable *Z* ([Figure 7.8b](#ch07.xhtml#fig7_8)). The data which we collect are denoted by *D* = (*X*[*i*],*T*[*i*],*Y*[*i*]), *i* = 1, …, *n*. The outcome *Y* is a function of the treatment *T*, the feature vector (covariates) *X*, the confounder *Z*, and denoted by

*Y* = *G*(*X*,*T*,*Z*).(7.90)

The joint distribution of the variables *Y*, *Z*, *X*, *T* is denoted as *P*(*Y*,*Z*,*X*,*T*). Since confounder *Z* is not observed, to determine *Z*, we use two approximations to factorize the joint distribution *P*(*Y*,*Z*,*X*,*T*) as follows:

*P*(*Y*,*Z*,*X*,*T*) ≈ *q*[*E*](*Y*,*Z*,*X*,*T*) = *P*[*d**a**t**a*](*Y*,*X*,*T*)*q*[*E*](*Z*|*Y*,*X*,*T*),(7.91)

*P*(*Y*,*Z*,*X*,*T*) ≈ *q*[*P*](*Y*,*Z*,*X*,*T*) = *P*[*d**a**t**a*](*X*,*T*)*q*[*I*](*Z*|*X*,*T*)*q*[*P*](*Y*|*Z*,*X*.*T*).(7.92)

[Equation (7.39)](#ch07.xhtml#eqn7_43) shows that the joint distribution *P*(*Y*,*Z*,*X*,*T*) can be generated by an encoder-decoder where distribution *q*[*E*](*Z*|*Y*,*X*,*T*) is the distribution of the whole latent space mapped by all the original dataset (*Y*,*X*,*T*). Therefore, the generated latent space includes both the confounder and non-confounder parts. [Equation (7.40)](#ch07.xhtml#eqn7_44) implies that the joint distribution *P*(*Y*,*Z*,*X*,*T*) can be approximately generated by prediction principle where the generated latent space includes only the confounders. To determine the confounders, we can make the two distributions *q*[*E*](*Y*,*Z*,*X*,*T*) and *q*[*P*](*Y*,*Z*,*X*,*T*) equal. Adversarial learning networks can be used to implement it ([Lee, Mastronarde, and van der Schaar 2018](#ch07.xhtml#ref7_35), [Dumoulin et al. 2019](#ch07.xhtml#ref7_14), [Chen et al. 2019](#ch07.xhtml#ref7_10)).

The ITE for an individual is defined as

*I**T**E*(*X*) = *E*\[*Y*|*X*,*T*\=1\] − *E*\[*Y*|*X*,*T*\=0\].(7.93)

Since the confounder *Z* affect both *Y* and *T*, using the formula for the total probability, we can express the conditional probability *P*(*Y*|*X*,*T*) as

$\\begin{array}{l} {P\\left( Y \\middle| X, T \\right) = \\int{P\\left( Y,Z \\middle| X,T \\right)dz}} \\\\ {\\quad = \\int{P\\left( Z \\middle| X,T \\right)P\\left( Y \\middle| Z,X,T \\right)dz}.} \\\\ \\end{array}$(7.94)

Since we assume that *Z*→*T*, we then obtain

*P*(*Z*|*X*,*T*) = *P*(*Z*|*X*).(7.95)

Substituting [Equation (7.43)](#ch07.xhtml#eqn7_47) into [Equation (7.42)](#ch07.xhtml#eqn7_46), we obtain

*P*(*Y*|*X*,*T*) = ∫*P*(*Z*|*X*)*P*(*Y*|*Z*,*X*,*T*)*d**z*.(7.96)

Using [Equation (7.44)](#ch07.xhtml#eqn7_48), we can calculate *I**T**E*(*X*).

### 7.6.3 Adversarial Learning Confounders

The basic idea of the adversarial learning confounders is to match the joint distribution *q*[*E*](*Y*,*Z*,*X*,*T*) with the joint distribution *q*[*P*](*Y*,*Z*,*X*,*T*) via bidirectional model and adversarial learning ([Lee, Mastronarde, and van der Schaar 2018](#ch07.xhtml#ref7_35), [Chen et al. 2019](#ch07.xhtml#ref7_10), [Dumoulin et al. 2019](#ch07.xhtml#ref7_14)). The pair-domain joint distributions *q*[*E*](*Y*,*Z*,*X*,*T*) and *q*[*P*](*Y*,*Z*,*X*,*T*) will be produced by two generative models that are similar to autoencoders. The generative model that produces the joint distribution *q*[*E*](*Y*,*Z*,*X*,*T*) is called a reconstruction network, and the generative model that produces the joint distribution *q*[*P*](*Y*,*Z*,*X*,*T*) is called a prediction network. Adversarial learning inference is used to match the pair-domain joint distribution ([Figure 7.9](#ch07.xhtml#fig7_9)).

![Figure 7.9 The architecture of the adversarial learning inference network for confounder and ITE estimation.](images/fig7_9.jpg)

**Figure 7.9**  
The architecture of the adversarial learning inference network for confounder and ITE estimation.

A reconstruction network can produce the joint distribution *q*[*E*](*Y*,*Z*,*X*,*T*) that is factorized into two components: *P*[*d**a**t**a*](*Y*,*X*,*T*) and *q*[*E*](*Z*|*Y*,*X*,*T*). The sampled data (*Y*,*X*,*T*) from the distribution *P*[*d**a**t**a*](*Y*,*X*,*T*) is input to the encoders to generate the latent variables *Z* that follows a distribution *q*[*E*](*Z*|*Y*,*X*,*T*). The latent variables *Z̃* is denoted by *Z̃* = *G*[*E*](*Y*,*X*,*T*,*ε*[*E*],*θ*[*E*]). To ensure that the latent variables keep the original data information, we introduce the decoder *G*[*R*](*Z̃*) to reconstruct input of the encoder *G*[*E*](*Y*,*X*,*T*,*ε*[*E*],*θ*[*E*]).

A prediction network is developed to implement the factorization of the joint distribution *q*[*P*](*Y*,*Z*,*X*,*T*) in [Equation (7.40)](#ch07.xhtml#eqn7_44). To map the data (*X*,*T*) to the latent space, another encoder (inference network) is introduced. The output *Z* of the inference network is a nonlinear function of *X*, *T* and *ε*[*I*] with the transformed distribution *q*[*I*](*Z**|**X*,*T*) and is denoted by *Z* = *G*[*I*](*X*,*T*,*ε*[*I*],*θ*[*I*]). The joint distribution *q*[*P*](*Y*|*Z*,*X*.*T*) is generated by the prediction decoder *G*[*P*]. The prediction decoder inputs the data (*X*,*T*) sampled from the real data distribution *P*[*d**a**t**a*](*X*,*T*) and the latent variables *Z* ∼ *q*[*I*](*Z*|*X*,*T*) and predicts the outcome variable *Ỹ* ∼ *q*[*P*](*Y*|*Z*,*X*.*T*), denoted by *Ỹ* = *G*[*P*](*Z*,*X*,*T*,*θ*[*P*]). Therefore, the joint distribution *q*[*P*](*Y*,*Z*,*X*,*T*) in the prediction network is equal to*q*[*P*](*Y*,*Z*,*X*,*T*) = *P*[*d**a**t**a*](*X*,*T*)*q*[*I*](*Z*|*X*,*T*)*q*[*P*](*Y*|*Z*,*X*.*T*).

### 7.6.4 Loss Function and Optimization for Estimating ITEs in the Presence of Confounders

To match joint distributions, similar to GANs, we introduce the discriminator and a loss function, which play an adversarial game between the two distributions. When the game reaches equilibrium, the two distributions *q*[*E*](*Y*,*Z*,*X*,*T*) and *q*[*P*](*Y*,*Z*,*X*,*T*) are matched. Let *D*(*Z*,*X*,*T*,*Y*) be the probability that the tuple (*Z*,*X*,*T*,*Y*) is drawn from the joint distribution *q*[*E*](*Y*,*Z*,*X*,*T*) and 1 − *D*(*Z*,*X*,*T*,*Y*) be the probability that the tuple (*Z*,*X*,*T*,*Y*) is drawn from the joint distribution *q*[*P*](*Y*,*Z*,*X*,*T*). The discriminator attempts to distinguish two tuples $\\left( {\\widetilde{Z,}X,T,Y} \\right)$ and (*Z*,*X*,*T*,*Ỹ*) which are from *q*[*E*](*Y*,*Z*,*X*,*T*) and *q*[*P*](*Y*,*Z*,*X*,*T*), respectively. The loss function is defined as

*V*(*θ*[*D*],*θ*[*E*],*θ*[*I*],*θ*[*P*]) = *E*[*q*[*E*](*Y*, *Z*, *X*, *T*)]\[log*D*(*Z̃*,*X*,*T*,*Y*,*θ*[*D*])\] + *E*[*q*[*P*](*Z*, *X*, *T*, *Ỹ*)]\[log(1−*D*(*Z*,*X*,*T*,*Ỹ*,*θ*[*D*]))\].(7.97)

To match two joint distributions, we solve the following optimization problem:

min[(*θ*[*E*], *θ*[*I*], *θ*[*P*])]max[*θ*[*D*]]*V*(*θ*[*D*],*θ*[*E*],*θ*[*I*],*θ*[*P*]).(7.98)

To ensure that the encoded latent variables *Z* contain the original data information, we define the following loss function for the reconstruction decoder:

$\\left. V\_{R}\\left( {X,T,Y,\\overline{X},\\overline{T},\\overline{Y}} \\right) = \\middle| \\middle| X - \\overline{X} \\middle| |^{2} - T^{T}\\log\\overline{T} - {(1 - T)}^{T}\\log\\left( {1 - \\overline{T}} \\right) - Y^{T}\\log\\overline{Y}\\quad - {(1 - Y)}^{T}\\log\\left( {1 - \\overline{Y}} \\right). \\right.$(7.99)

## ![image](images/inline1_1.jpg)  
7.7 Targeted Maximum Likelihood Estimation

An alternative method to estimate the ATE is the targeted maximum likelihood estimation (TMLE). TMLE is doubly robust than other methods, based on maximum likelihood estimation and has a “targeting” step that optimizes the bias-variance tradeoff for the target parameter ([Laan and Rubin 2006](#ch07.xhtml#ref7_34)). Although TMLE is not widely used in causal inference studies, it has desirable statistical properties and has a lot of potential in EHR causal inference.

Consider a binary treatment and let *Y*[1] denote the outcomes with exposed factors, and *Y*[0] denote outcomes without exposed factors. To remove confounders, G-computation and propensity score methods use conditional probability to address confounding. G-computation relies on the conditional expectation of outcome given exposure and covariates, *E*\[*Y**|**A*,*X*\]. Propensity score methods estimate the conditional expectation of the exposure given the observed confounders X, *P*(*A*\=1*|**X*). TMLE includes both of them and will provide unbiased estimation if either *E*\[*Y**|**A*,*X*\] or *P*(*A*\=1*|**X*) is consistently estimated (doubly robust). If not, the final ATE can still be unbiased if the exposure mechanism can be consistently estimated. TMLE is an asymptotically efficient substitution estimator when both the outcome and exposure mechanisms are consistently estimated, and it is more robust to outliers and sparsity. Finally, many kinds of algorithms and machine learning methods can be incorporated in TMLE, and these methods can help with minimizing bias in comparison with the use of misspecified regressions.

[Figure 7.10](#ch07.xhtml#fig7_10) shows how the TMLE works. First, calculate the conditional expectation of the outcome given the exposure and covariates, *E*\[*Y**|**A*,*X*\]. This first estimation is used to represent the estimation of the outcome on both exposure levels. Then, the next step is the “targeting” step, which involves the estimation of exposure mechanism, *P*(*A*\=1*|**X*). This estimation is used to improve the estimation before the predefined working regression model. Finally, use the improved expectation value *E*\[*Y**|**A*,*X*\] to generate updated pairs of potential outcomes. The new estimation of ATE value will the average difference between the exposure pairs across individuals.

![Figure 7.10 Flow chart of TMLE works (Schuler et al. 2016).](images/fig7_10.jpg)

**Figure 7.10**  
Flow chart of TMLE works (Schuler et al. 2016).

In summary, the TMLE is a doubly robust estimator of the ATE, and the doubly robust prosperity ensures the unbiasedness of the estimator. TMLE unifies maximum likelihood estimation and estimating function based estimation and combines them to get an improved result. Finally, TMLE can be implemented using machine learning algorithms, which can make this method be used on complex datasets like EHR data.

TMLE method can be used with the “tmle” package ([Gruber and van der Laan 2012](#ch07.xhtml#ref7_20)) in R (R Foundation for Statistical Computing, Vienna, Austria).

## ![image](images/inline1_1.jpg)  
7.8 Supplementary Note A

### 7.8.1 Wasserstein GAN

#### A1 Different Distances

There are two approaches to learning generative models. One approach is to directly learn the probability density function *p*[*θ*] via maximum likelihood function. The second approach is to learn a function that transforms the existing distribution *z* into the density function *p*[*θ*] via *p*[*θ*] = *G*[*θ*](*z*). To elaborate, we first study the maximum likelihood estimator.

##### A1.1 Maximum Likelihood Estimation

Assume that real data samples {*x*[1], …, *x*[*n*]} with density function *p*[*r*](*x*) are given. We define a parametric family of density *p*[*θ*](*x*). The maximum likelihood estimator (MLE) is to maximize the likelihood of the data:

$\\mathit{\\max}\_{\\theta}\\frac{1}{n}\\sum\_{i = 1}^{n}\\left. \\log{p\_{\\theta}\\left( x\_{i} \\right.} \\right),$(A1)

which implies

$\\lim\\limits\_{n\\rightarrow\\infty}{\\max\\limits\_{\\theta}{\\frac{1}{n}\\sum\_{i = 1}^{n}\\left. \\log{p\_{\\theta}\\left( x\_{i} \\right.} \\right) = \\max\\limits\_{\\theta}\\int{p\_{r}\\left( x \\right)\\log{p\_{\\theta}\\left( x \\right)\\mathit{dx}}}}}.$(A2)

Recall that the KL distance between two distributions *p*[*r*](*x*) and *p*[*θ*](*x*) is defined as

$\\mathit{KL}\\left( p\_{r}|\\left( p\_{\\theta} \\right) = \\int{p\_{r}\\left( x \\right)\\log\\frac{p\_{r}\\left( x \\right)}{p\_{\\theta}\\left( x \\right)}}\\mathit{dx}. \\right.$(A2)

Therefore, Equation (A2) can be transformed to the following optimization problem:

$\\lim\_{n\\rightarrow\\infty}\\max\_{\\theta}\\frac{1}{n}\\sum\_{i = 1}^{n}{\\log p\_{\\theta}(x\_{i}) = \\max\\limits\_{\\theta}\\int{p\_{r}(x)\\log p\_{\\theta}\\left( x \\right)dx}} = - \\min\\limits\_{\\theta}\\int{p\_{r}\\left( x \\right)\\log p\_{\\theta}\\left( x \\right)dx}\\quad = \\min\\limits\_{\\theta}\\int{p\_{r}\\left( x \\right)\\log p\_{r}\\left( x \\right)dx - \\int{p\_{r}\\left( x \\right)\\log p\_{\\theta}\\left( x \\right)dx}}\\quad = \\min\\limits\_{\\theta}\\int{p\_{r}(x)\\log\\frac{p\_{r}(x)}{p\_{\\theta}(x)}dx}\\quad = \\underset{\\theta}{\\left. \\min KL(p\_{r} \\middle| \\middle| p\_{\\theta}) \\right.}.$(A3)

Equation (A3) shows that the MLE is equivalent to the minimization of KL distance. The major limitation of the MLE of the generative models is that when two distributions *p*[*θ*] and *p*[*r*] are not completely overlapped, for example, *p*[*θ*](*x*[0]) = 0 where *p*[*r*](*x*[0]) > 0, then KL distance goes to  + ∞. The general solution is to develop a nonlinear function map *g*[*θ*] *:* *Z*→*χ* that transforms a random variable *Z* with a known distribution *p*(*z*) (typically, uniform or normal distribution) to a certain distribution *p*[*θ*]. By varying *θ*, we can make the distribution *p*[*θ*] close to the real data distribution *p*[*r*]. To measure the degree of closeness, we need to develop various distance measures between two distributions *p*[*θ*] and *p*[*r*].

##### A1.2 Total Variation (TV) Distance

Assume that *p*[*r*] and *p*[*θ*] are two probability distributions defined on the space *Ω*. Then, total variation distance between two distributions is defined as

$\\delta\\left( {P\_{r},P\_{\\theta}} \\right) = \\sup\\limits\_{A \\in \\digamma}{|p\_{r}\\left( A \\right) - p\_{\\theta}\\left( A \\right)|},$(A4)

where ϝ ∈ *Ω* is a subset of *Ω*.

**Example 1.1**

Consider probability distributions defined over probability space *R*². Let *Z* ∼ *U*\[0,1\] be the uniform distribution on the unit interval. Let *p*[0] be the distribution defined on (0,*Z*) and *p*[*θ*] be the distribution defined on (*θ*,*Z*), where *θ* is a single real parameter. Define*A* = {(0,*z*), *z* ∈ \[0,1\]}.

Then, *p*[0](*A*) = *z* and *p*[*θ*](*A*) = 0 when *θ* ≠ 0. Thus, when *θ* ≠ 0, we have

*|**p*[*r*](*A*) − *p*[*θ*](*A*)| = *z*, which impliessup[*A* ∈ ϝ]|*p*[*r*](*A*) − *p*[*θ*](*A*)| = 1.

When, *θ* = 0, we obtain *p*[0](*A*) = *p*[*θ*](*A*). Therefore,$\\delta\\left( {p\_{0},p\_{\\theta}} \\right) = \\left\\{ \\begin{matrix} 1 & {\\theta \\neq 0} \\\\ 0 & {\\theta = 0} \\\\ \\end{matrix} \\right..$

##### A1.3 The Kullback-Leibler (KL) Divergence

The Kullback-Leibler (KL) divergence between two distribution is defined as

$\\mathit{KL}\\left( p\_{r}|\\left( p\_{\\theta} \\right) = \\int p\_{r}\\log\\frac{p\_{r}}{p\_{\\theta}}\\mathit{dx}. \\right.$(A5)

**Example 1.1 (continued)**

Since *p*[*θ*](*A*) = 0, ∀*θ* ≠ 0, therefore, we obtain$\\mathit{KL}\\left( p\_{r}|\\left( p\_{\\theta} \\right) = \\left\\{ \\begin{matrix} {+ \\infty} & {\\theta \\neq 0} \\\\ 0 & {\\theta = 0} \\\\ \\end{matrix} \\right.. \\right.$

##### A1.4 The Jenson-Shannon (JS) Divergence

Let $p\_{m} = \\frac{p\_{r} + p\_{\\theta}}{2}$. The Jenson-Shannon (JS) divergence is defined as

*J**S*(*p*[*r*]|(*p*[*θ*])=*K**L*(*p*[*r*]|(*p*[*m*])+*K**L*(*p*[*θ*]||*p*[*m*]).(A6)

**Example 1.1 (continued)**

When *θ* ≠ 0 where *p*[0] ≠ 0, which implies *p*[*θ*] = 0 . Thus, we have $p\_{m} = \\frac{p\_{r}}{2}$. Similarly, When *θ* ≠ 0 where *p*[*θ*]≠0, which implies *p*[*r*] = 0. Thus, we have $p\_{m} = \\frac{p\_{\\theta}}{2}$. Therefore, we obtain$\\mathit{JS}\\left( {p\_{0},p\_{\\theta}} \\right) = \\left\\{ \\begin{matrix} {\\log 2} & {\\theta \\neq 0} \\\\ 0 & {\\theta = 0} \\\\ \\end{matrix} \\right..$

##### A1.5 Earth Mover (EM) or Wasserstein Distance

When we consider discrete probability distributions, the Wasserstein distance is also illustratively referred to as the earth mover’s distance (EMD). Consider two discrete distributions *p*[*r*] and *p*[*θ*], each has possible *l* states *x* or *y*. The distribution *p*[*r*](*x*) is defined as the probability mass which each point has, and the distribution *p*[*θ*](y) can be similarly defined. Our goal is to move mass around to change the distribution *p*[*r*](*x*)into *p*[*θ*](*y*). The joint distribution *r*(*x*,*y*) can be viewed as a transportation plan that moves *r*(*x*,*y*) mass from *x* to *y*. The distance from *x* to *y* is denoted as ||*x*−*y*||. The cost moving *r*(*x*,*y*) mass from *x* to *y* is equal to *r*(*x*,*y*)||*x*−*y*||. The moving plan *r*(*x*,*y*) should satisfy the following constraints:*p*[*r*](*x*) = ∑[*y*]*r*(*x*,*y*)  *a**n**d*  *p*[*θ*](*y*) = ∑[*x*]*r*(*x*,*y*).

Let *Π*(*p*[*r*],*p*[*θ*]) be the set of all possible joint distributions with marginal distributions *p*[*r*](*x*) and *p*[*θ*](*y*). Then, the EMD is then defined as the minimum cost required to move *r*(*x*,*y*) mass from *x* to *y*:

*W*(*p*[*r*],*p*[*θ*]) = *inf* [*r* ∈ *Π*(*p*[*r*], *p*[*θ*])]∑[*x*]∑[*y*]*r*(*x*,*y*)||*x*−*y*|| = *inf* [*r* ∈ *Π*(*p*[*r*], *p*[*θ*])]*E*[(*x*, *y*) ∼ *r*]\[||*x*−*y*||\].(A7)

If the variables are continuous, Equation (A7) can be extended to

*W*(*p*[*r*],*p*[*θ*]) = *inf* [*r* ∈ *Π*(*p*[*r*], *p*[*θ*])]∫[*x*]∫[*y*]*r*(*x*,*y*)||*x*−*y*||*d**x**d**y*.(A8)

**Example 1.1 (continued)**

Consider two distributions *p*[0](*z*) and *p*[*θ*](*z*) where *Z* ∼ *U*(0,1). Let *x* = \[0,*z*\] and *y* = \[*θ*,*z*\]. It is clear that ||*x*−*y*|| = |*θ*| if we move along the line parallel to the *x* axis.

#### A2 Wasserstein GAN

Using the Kantorovich-Rubinstein Duality theory, we can show ([Rachev 1990](#ch07.xhtml#ref7_47))

*W*(*p*[*r*],*p*[*θ*]) = sup[||*f*||[*L* ≤ 1]]*E*[*x* ∼ *p*[*r*]]*f*(*x*) − *E*[*x* ∼ *p*[*θ*]]*f*(*x*),(A9)

where *f* is 1- Lipschitz function.

The optimization problem (A9) is a constrained optimization. Solving the optimization problem under Lipschitz constraints with constant 1 is intractable. To alleviate the problem, we release the Lipschitz constraints with constant 1 to Lipschitz constraints with constant *K*, i.e.,∥*f*(*x*[*i*])−*f*(*x*[*j*])∥≤*K*∥*x*[*i*]−*x*[*j*]∥.

Let $g\\left( x \\right) = \\frac{f\\left( x \\right)}{K}$. Then, we have ∥*g*(*x*[*i*])−*g*(*x*[*j*])∥≤∥*x*[*i*]−*x*[*j*]∥, i.e, *g*(*x*) is a Lipschitz function with constant 1.

The supremum over *K*\-Lipschitz constraints is still hard to implement, but it allows for easier approximation. Consider a parametrized function family {*f*[*w*]}[*w* ∈ *W*] where *W* is the set of all possible weights. These functions are also *K*\-Lipschitz functions. Then, we havesup[||*f*||[*L* ≤ *K*]]*E*[*x* ∼ *p*[*r*]]*f*(*x*) − *E*[*x* ∼ *p*[*θ*]]*f*(*x*) = *K**sup* [||*g*||[*L*] ≤ 1]*E*[*x* ∼ *p*[*r*]]*g*(*x*) − *E*[*x* ∼ *p*[*θ*]]*g*(*x*) = *K**W*(*p*[*r*],*p*[*θ*]),which impliesmax[*w* ∈ *W*]*E*[*x* ∼ *p*[*r*]]*f*[*w*](*x*) − *E*[*x* ∼ *p*[*θ*]]*f*[*w*](*g*[*θ*](*z*))≤sup[||*f*||[*L* ≤ *K*]]*E*[*x* ∼ *p*[*r*]]*f*(*x*) − *E*[*x* ∼ *p*[*θ*]]*f*(*x*) = *K**W*(*p*[*r*],*p*[*θ*]).

Therefore, the optimization problem (A9) can be approximated by

max[*w* ∈ *W*]*E*[*x* ∼ *p*[*r*]]*f*[*w*](*x*) − *E*[*x* ∼ *p*[*θ*]]*f*[*w*](*x*).(A10)

Let

*x* = *g*[*θ*](*z*).(A11)

Substituting Equation (A11) into Equation (A10), we obtain

*W*(*p*[*r*],*p*[*θ*]) ≥ max[*w* ∈ *W*]*E*[*x* ∼ *p*[*r*]]*f*[*w*](*x*) − *E*[*z* ∼ *p*(*z*)]*f*[*w*](*g*[*θ*](*z*)).(A12)

Both functions *f*[*w*](*x*) and *g*[*θ*](*z*) can be modeled by neural networks and parameters *w* and *θ* are the weights in the neural networks. Our goal is to find the generator *g*[*θ*](*z*), which makes the Wasserstein distance between the distribution *p*[*r*] of the real data and distribution *p*[*θ*] of the generator as small as possible, i.e.,

min[*θ*]*W*(*p*[*r*],*p*[*θ*]).(A13)

The Wasserstein distance is calculated by its lower boundary in Equation (A12). In summary, to find the generator *g*[*θ*](*z*), we solve the following optimization problem:

min[*θ*] max[*w* ∈ *W*]*E*[*x* ∼ *p*[*r*]]*f*[*w*](*x*) − *E*[*z* ∼ *p*(*z*)]*f*[*w*](*g*[*θ*](*z*)).(A14)

Numerically, the optimization problem (A13) can be solved by Algorithm 2 ([Arjovsky and Bottou 2019](#ch07.xhtml#ref7_2)).

#### A3 Algorithm (WGAN)

Input: *α*, the learning rate; *c*, the clipping parameter; *m*, the batch size; *n*[*d*], the number of iterations of the discriminator neural network update per generator iteration. *w*[0], initial weight parameters of the network for function *f*[*w*]; *θ*[0], initial generator’s parameters.

While *θ* has not converged do

for *t* = 0, …, *n*[*d*] do

Sample {*x*^((*i*))}[*i* = 1]^(*m*) ∼ *p*[*r*] a batch from the real data.

Sample {*z*^((*i*))}[*i* = 1]^(*m*) ∼ *p*(*z*), a batch from the noises.

$\\left. g\_{w}\\leftarrow\\nabla\_{w}\\left\\lbrack {\\frac{1}{m}\\sum\_{i = 1}^{m}{f\_{w}\\left( x^{(i)} \\right) - \\frac{1}{m}}\\sum\_{i = 1}^{m}{f\_{w}\\left( g\_{\\theta}\\left( z^{(i)} \\right) \\right)}} \\right\\rbrack \\right.$

*w*←*w*+*α**R**M**S**P**r**o**p*(*w*,*g*[*w*])

*w*←*c**l**i**p*(*w*,−*c*,*c*)

end for

Sample {*z*^((*i*))}[*i* = 1]^(*m*) ∼ *p*(*z*), a batch from the noises.

$\\left. g\_{\\theta}\\leftarrow - \\nabla\_{\\theta}\\frac{1}{m}\\sum\_{i = 1}^{m}{f\_{w}\\left( g\_{\\theta}\\left( z^{(i)} \\right) \\right)} \\right.$

*θ*←*θ*−*α**R**M**S**P**t**o**p*(*θ*,*g*[*θ*])

end while.

### References

Angrist, Joshua D., Kathryn Graddy, and Guido W. Imbens. 2000. The interpretation of instrumental variables estimators in simultaneous equations models with an application to the demand for fish.  *Review of Economic Studies* **67**. doi:((3) 499- –527[10.1111/1467-937X.00141](http://dx.doi.org/10.1111/1467-937X.00141).

Arjovsky, Martin, and Léon Bottou. 2019. Towards principled methods for training generative adversarial networks. In 5th International Conference on Learning Representations, ICLR 2017 - Conference Track Proceedings. arXiv: 1701.04862

Austin, Peter C. 2011. An introduction to propensity score methods for reducing the effects of confounding in observational studies. *Multivariate Behavioral Research* **46**((3)), Taylor & Francis: 399–424. doi:[10.1080/00273171.2011.568786](http://dx.doi.org/10.1080/00273171.2011.568786).

Austin, Peter C., and Elizabeth A. Stuart. 2015. Moving towards best practice when using inverse probability of treatment weighting (IPTW) using the propensity score to estimate causal treatment effects in observational studies. *Statistics in Medicine* **34**((28)). John Wiley and Sons Ltd: 3661–3679. doi: [10.1002/sim.6607](http://dx.doi.org/10.1002/sim.6607).

Baron, Reuben M., and David A. Kenny. 1986. The moderator-mediator variable distinction in social psychological research. conceptual, strategic, and statistical considerations. *Journal of Personality and Social Psychology* **51**((6)), 1173–1182. doi:[10.1037/0022-3514.51.6.1173](http://dx.doi.org/10.1037/0022-3514.51.6.1173).

Bennett, Andrew, Nathan Kallus, and Schnabel Tobias. 2019. Deep generalized method of moments for instrumental variable analysis. In: *Advances in Neural Information Processing Systems*, **32**. pp. 3559–3569.

Brown, Derek W., Stacia M. DeSantis, Thomas J. Greene, Vahed Maroufy, Ashraf Yaseen, Hulin Wu, George Williams, and Michael D. Swartz. 2020. A novel approach for propensity score matching and stratification for multiple treatments: Application to an electronic health record <scp>–Derived</Scp> study. *Statistics in Medicine*, April. John Wiley and Sons Ltd, sim.8540. doi:[10.1002/sim.8540](http://dx.doi.org/10.1002/sim.8540).

Burgess, Stephen, Dylan S. Small, and Simon G. Thompson. 2017. A review of instrumental variable estimators for mendelian randomization. *Statistical Methods in Medical Research*. **26**((5)): 2333–2355. doi:[10.1177/0962280215597579](http://dx.doi.org/10.1177/0962280215597579).

Burgette, Lane, Beth Ann Griffin, and Dan Mccaffrey. 2020. Propensity scores for multiple treatments: A tutorial for the mnps function in the twang package. [http://www.rand.org/statistics/twang/](http://www.rand.org).

Chen, Ziliang, Zhanfu Yang, Xiaoxi Wang, Xiaodan Liang, Xiaopeng Yan, Guanbin Li, and Liang Lin. 2019. Multivariate-information adversarial ensemble for scalable joint distribution matching.

Concato, John, Nirav Shah, and Ralph I. Horwitz. 2000. Randomized, controlled trials, observational studies, and the hierarchy of research designs. *New England Journal of Medicine* **342**((25)): 1887–1892. Massachusetts Medical Society. doi:[10.1056/NEJM200006223422507](http://dx.doi.org/10.1056/NEJM200006223422507).

Diamond, Alexis, and Jasjeet S. Sekhon. 2013. Genetic matching for estimating causal effects: A general multivariate matching method for achieving balance in observational studies. *Review of Economics and Statistics* **95**((3)): 932–945. The MIT Press. doi:[10.1162/REST\_a\_00318](http://dx.doi.org/10.1162/REST_a_00318).

Ding, Peng, and Fan Li. 2018. Causal inference: A missing data perspective. *Statistical Science* **33**((2)) , 214–237. doi:[10.1214/18-STS645](http://dx.doi.org/10.1214/18-STS645).

Dumoulin, Vincent, Ishmael Belghazi, Ben Poole, Olivier Mastropietro, Alex Lamb, Martin Arjovsky, and Aaron Courville. 2019. Adversarially learned inference. In: 5th International Conference on Learning Representations, ICLR 2017 – Conference Track Proceedings. International Conference on Learning Representations, ICLR. arXiv:1606.00704

Feng, Ping, Xiao-Hua Zhou, Qing-Ming Zou, Ming-Yu Fan, and Xiao-Song Li. 2012. Generalized propensity score for estimating the average treatment effect of multiple treatments. *Statistics in Medicine* **31**((7)): 681–697. John Wiley & Sons, Ltd. doi:[10.1002/sim.4168](http://dx.doi.org/10.1002/sim.4168).

Fong, Christian, Chad Hazlettand, and Kosuke Imai. 2018. Covariate balancing propensity score for a continuous treatment: Application to the efficacy of political advertisements. *Annals of Applied Statistics* **12**((1)), 156–177. doi:[10.1214/17-AOAS1101](http://dx.doi.org/10.1214/17-AOAS1101).

Ge Q, Fang S, Guo S, Liu Y, Lin W, Xiong MM (2020). Conditional generative adversarial networks and variational autoencoders for estimation of individualized treatment effects in high dimensional survival analysis. *JAMA Oncology*. To be submitted.

Goodfellow, Ian J, Jean Pouget-Abadie, Mehdi Mirza, Bing Xu, David Warde-Farley, Sherjil Ozair, Aaron Courville, and Yoshua Bengio. 2014. Generative adversarial nets. 2672–2680 [http://www.github.com/goodfeli/adversarial](http://www.github.com)

Greene, Thomas J., Stacia DeSantis, John Harvin, John Holcomb, and Michael Swartz. 2017. Utilizing propensity score methods for ordinal treatments and prehospitaltrauma studies. Texas Medical Center Dissertations (via ProQuest). AAI10681743.  [https://digitalcommons.library.tmc.edu/dissertations/AAI10681743](https://digitalcommons.library.tmc.edu).

 Gruber, Susan, and Mark J. van der Laan. 2012. TMLE: An R package for targeted maximum likelihood estimation. *Journal of Statistical Software* **51**((13)): 1–35. American Statistical Association. doi:[10.18637/jss.v051.i13](http://dx.doi.org/10.18637/jss.v051.i13).

Gu, Xing Sam, and Paul R. Rosenbaum. 1993. Comparison of multivariate matching methods: Structures, distances, and algorithms. *Journal of Computational and Graphical Statistics* **2**((4)): 405. JSTOR. doi:[10.2307/1390693](http://dx.doi.org/10.2307/1390693).

Hafeman, Danella M. 2011. Practice of epidemiology confounding of indirect effects: A sensitivity analysis exploring the range of bias due to a cause common to both the mediator and the outcome. *American Journal of Epidemiology* **174**((6)): 710–717. doi:[10.1093/aje/kwr173](http://dx.doi.org/10.1093/aje/kwr173).

Hansen, Lars Peter. 1982. "Large sample properties of generalized method of moments estimators. *Econometrica*. 1029–1054 doi:[10.2307/1912775](http://dx.doi.org/10.2307/1912775).

Harder, Valerie S., Elizabeth A. Stuart, and James C. Anthony. 2010. Propensity score techniques and the assessment of measured covariate balance to test causal associations in psychological research. *Psychological Methods* **15**((3)): 234–249. doi:[10.1037/a0019623](http://dx.doi.org/10.1037/a0019623).

Hartford, Jason, Greg Lewis, Kevin Leyton-Brown, and Matt Taddy. 2017. Deep IV: A flexible approach for counterfactual prediction. In: 34th International Conference on Machine Learning, ICML 2017. pp. 1414–1423

Hayashi F (2000). *Econometrics*. Princeton, NJ: Princeton University Press. pp. 60–69.

Huang, I. Chan, Constantine Frangakis, Francesca Dominici, Gregory B. Diette, and Albert W. Wu. 2005. Application of a propensity score approach for risk adjustment in profiling multiple physician groups on asthma care.  *Health Services Research* **40**((1)) doi:[10.1111/j.1475-6773.2005.00352.x](http://dx.doi.org/10.1111/j.1475-6773.2005.00352.x).

Imai, Kosuke, and David A. Van Dyk. 2004. Causal inference with general treatment regimes: Generalizing the propensity score. *Journal of the American Statistical Association* **99**((467)): 854–866. Taylor & Francis. doi:[10.1198/016214504000001187](http://dx.doi.org/10.1198/016214504000001187).

Imai, Kosuke, Luke Keele, and Dustin Tingley. 2010. A general approach to causal mediation analysis. *Psychological Methods* **15**((4)): 309–334. doi:[10.1037/a0020761](http://dx.doi.org/10.1037/a0020761).

Imai, Kosuke, and Marc Ratkovic. 2013. Covariate balancing propensity score. *Journal of the Royal Statistical Society: Series B*  **76**. doi:[10.1111/rssb.12027](http://dx.doi.org/10.1111/rssb.12027). 243- –263

Imbens, Guido W. 2000. The role of the propensity score in estimating dose-response functions. *Biometrika* **3**((706)): 706–710.

Joffe, M. M., and P. R. Rosenbaum. 1999. Invited commentary: Propensity scores. *American Journal of Epidemiology* **150**((4)). John Hopkins University School of Hygiene and Public Health: 327–333. doi:[10.1093/oxfordjournals.aje.a010011](http://dx.doi.org/10.1093/oxfordjournals.aje.a010011).

Ju, Cheng, Mary Combs, Samuel D. Lendle, Jessica M. Franklin, Richard Wyss, Sebastian Schneeweiss, and Mark J. van der Laan. 2019. Propensity score prediction for electronic healthcare databases using super learner and high-dimensional propensity score methods. *Journal of Applied Statistics* **46**((12)). Taylor and Francis Ltd.: 2216–2236. doi:[10.1080/02664763.2019.1582614](http://dx.doi.org/10.1080/02664763.2019.1582614).

Laan, Mark van der, and Daniel Rubin. 2006. Targeted Maximum Likelihood Learning. U.C. Berkeley division of biostatistics working paper series, October. [https://biostats.bepress.com/ucbbiostat/paper213](https://biostats.bepress.com).

Lee, Changhee, Nicholas Mastronarde, and Mihaela van der Schaar. 2018. Estimation of individual treatment effect in latent confounder models via adversarial learning. November. [http://arxiv.org/abs/1811.08943](http://arxiv.org).

 Li, Fan, Kari Lock Morgan, and Alan M. Zaslavsky. 2018. Balancing covariates via propensity score weighting. *Journal of the American Statistical Association* **113**((521)): 390–400. American Statistical Association. doi:[10.1080/01621459.2016.1260466](http://dx.doi.org/10.1080/01621459.2016.1260466).

Li, Steven Cheng-Xian, Bo Jiang, and Benjamin Marlin. 2019. MisGAN: Learning from incomplete data with generative adversarial networks. February. [http://arxiv.org/abs/1902.09599](http://arxiv.org).

Little, Roderick J. A., and Donald B. Rubin. 2002. *Wiley Series in Probability and Statistics: Statistical Analysis with Missing Data*. 2nd edn ed. Somerset, US: Wiley-Interscience. pp. 383–389

Lopez, Michael J., and Roee Gutman. 2017. Estimation of causal effects with multiple treatments: a review and new ideas. *Statistical Science* **32**((3)): 432–454. Institute of Mathematical Statistics. doi:[10.1214/17-STS612](http://dx.doi.org/10.1214/17-STS612).

Lu, Bo, Elaine Zanutto, Robert Hornik, and Paul R. Rosenbaum. 2001. Matching with doses in an observational study of a media campaign against drug abuse. *Journal of the American Statistical Association* **96**((456)):- 1245–1253. doi:[10.1198/016214501753381896](http://dx.doi.org/10.1198/016214501753381896).

Lu, Chaochao, Bernhard Schölkopf, and José Miguel Hernández-Lobato. 2018. " Deconfounding reinforcement learning in observational settings. December. [http://arxiv.org/abs/1812.10576](http://arxiv.org).

Luo, Wei, and Yeying Zhu. 2019. Matching using sufficient dimension reduction for causal inference. *Journal of Business and Economic Statistics. American Statistical Association*. doi:[10.1080/07350015.2019.1609974](http://dx.doi.org/10.1080/07350015.2019.1609974). pp. 1–13

Mohamed S., M. Rosca, M. Figurnov, A. Mnih. (2019). Monte Carlo gradient estimation in machine learning.  *Journal of Machine Learning* **21**((132)): 1–62. arXiv:1906.10652.

Mccaffrey, Daniel F., Beth Ann Griffin, Daniel Almirall, Mary Ellen Slaughter, Rajeev Ramchand, and Lane F. Burgette. 2013. A tutorial on propensity score estimation for multiple treatments using generalized boosted models. *Statistics in Medicine* **32**((19)): 3388–3414. doi:[10.1002/sim.5753](http://dx.doi.org/10.1002/sim.5753).

McCaffrey, Daniel F., Greg Ridgeway, and Andrew R. Morral. 2004. Propensity score estimation with boosted regression for evaluating causal effects in observational studies. *Psychological Methods* **9**((4)): 403–425. doi:[10.1037/1082-989X.9.4.403](http://dx.doi.org/10.1037/1082-989X.9.4.403).

Neyman, Jerzy. 1923. On the application of probability theory to agricultural experiments. essay on principles. Section 9. *Statistical Science* **5**((4)): 472–480

Rachev, Svetlozar Todorov. 1990. Duality theorems for Kantorovich–Rubinstein and Wasserstein functionals.

Rassen, Jeremy A., Abhi A. Shelat, Jessica M. Franklin, Robert J. Glynn, Daniel H. Solomon, and Sebastian Schneeweiss. 2013. Matching by propensity score in cohort studies with three treatment groups. *Epidemiology* **24**((3)): 401–409. doi:[10.1097/EDE.0b013e318289dedf](http://dx.doi.org/10.1097/EDE.0b013e318289dedf).

Ray, Kolyan, and Botond Szabó. 2019. Debiased Bayesian inference for average treatment effects.” In: *33rd Conference on Neural Information Processing System.* 11952- –11962.

Rosenbaum, Paul; 1991. A characterization of optimal designs for observational studies on JSTOR. *Journal of the Royal Statistical Society Series B* **53**((3)): 597–610. [https://www.jstor.org/stable/2345589?seq=1#metadata\_info\_tab\_contents](https://www.jstor.org/stable/2345589?seq=1#metadata_info_tab_contents).

Rosenbaum, Paul R., and Donald B. Rubin. 1983. The central role of the propensity score in observational studies for causal effects. *Biometrika* **70**((1)). JSTOR: 41. doi:[10.2307/2335942](http://dx.doi.org/10.2307/2335942).

 Rosenbaum, Paul R., and Donald B. Rubin. 1985. Constructing a control group using multivariate matched sampling methods that incorporate the propensity score. *The American Statistician* **39**((1)). JSTOR: 33. doi:[10.2307/2683903](http://dx.doi.org/10.2307/2683903).

Rosenbaum, Paul, and Donald Rubin. 1983. The central role of the propensity score in observational studies for causal effects. *Biometrika* **70**((1)). JSTOR: 41. doi:[10.2307/2335942](http://dx.doi.org/10.2307/2335942).

Ross, Sheldon M. n.d. 2014. A first course in probability.” Pearson

Rubin, Donald. 1974. Estimating causal effects of treatment in randomized and nonrandomized studies. *Journal of Educational Psychology*. **66** (5) 688

Rubin, Donald B. 1978. Bayesian inference for causal effects: the role of randomization. *Annals of Statistics* **6**((1)): 34–58. Institute of Mathematical Statistics. doi:[10.1214/AOS/1176344064](http://dx.doi.org/10.1214/AOS/1176344064).

Rubin, Donald B. 1980. Randomization analysis of experimental data: the fisher randomization test comment. *Journal of the American Statistical Association* **75**((371)): 591. JSTOR. doi:[10.2307/2287653](http://dx.doi.org/10.2307/2287653).

Rucker, Derek D., Kristopher J. Preacher, Zakary L. Tormala, and Richard E. Petty. 2011. Mediation analysis in social psychology: Current practices and new recommendations. Shrout & Bolger, 2002, Social and Personality Psychology Compass 5. Preacher & Hayes: **5**((6)) :359–371. doi:[10.1111/j.1751-9004.2011.00355.x](http://dx.doi.org/10.1111/j.1751-9004.2011.00355.x).

Setoguchi, Soko, Sebastian Schneeweiss, M. Alan Brookhart, Robert J. Glynn, and E. Francis Cook. 2008. Evaluating uses of data mining techniques in propensity score estimation: A simulation study. *Pharmacoepidemiology and Drug Safety* **17**((6)): 546–555. doi:[10.1002/pds.1555](http://dx.doi.org/10.1002/pds.1555).

Seya, Hajime, and Takahiro Yoshida. 2017. Propensity score matching for multiple treatment levels: A CODA-based contribution. Paper, arXiv: 1710.08558

Shadish, W., Cook, T., and Campbell, D. 2002. Statistical conclusions: Validity and internal validity. In: *Experimental and Quasi Experimental Designs for Generilized Causal Inference*. Boston: Houghton Mifflin

Stuart, Elizabeth A. 2010. Matching methods for causal inference: A review and a look forward. *Statistical Science* **25**. doi:((1))[10.1214/09-STS313](http://dx.doi.org/10.1214/09-STS313).

Tu, Chunhao, Shuo Jiao, and Woon Yuen Koh. 2013. Comparison of clustering algorithms on generalized propensity score in observational studies: a simulation study. *Journal of Statistical Computation and Simulation* **83**((12)): 2206–2218. Taylor & Francis. doi:[10.1080/00949655.2012.685169](http://dx.doi.org/10.1080/00949655.2012.685169).

Usaid Awan, M., Yameng Liu, Marco Morucci, Sudeepa Roy, Cynthia Rudin, and Alexander Volfovsky. 2020. Interp retable almost matching exactly with instrumental variables.” PMLR In: 35th Conference on Uncertainty in Artificial Intelligence, UAI 2019.  pp.  1116–1126

VanderWeele, Tyler. 2015. *Explanation in Causal Inference*. Oxford University Press [http://gbv.eblib.com/patron/FullRecord.aspx?p=1920742](http://gbv.eblib.com).

VanderWeele, Tyler J. 2016. Mediation analysis: A practitioner’s guide. *Annual Review of Public Health* **37**((1)): 17–32. doi:[10.1146/annurev-publhealth-032315-021402](http://dx.doi.org/10.1146/annurev-publhealth-032315-021402).

Vanderweele, Tyler J., and Stijn Vansteelandt. 2010. Odds ratios for mediation analysis for a dichotomous outcome. *American Journal of Epidemiology* **172**((12)): 1339–1348. doi:[10.1093/aje/kwq332](http://dx.doi.org/10.1093/aje/kwq332).

 Williams, George, Vahed Maroufy, Laila Rasmy, Derek Brown, Duo Yu, Hai Zhu, Yashar Talebi, *et al* 2020. Vasopressor treatment and mortality following non-traumatic subarachnoid hemorrhage: A nationwide ehr analysis. *Neurosurgical Focus* **48** In press. ((5))

Wyss, Richard, Sebastian Schneeweiss, Mark Van Der Laan, Samuel D. Lendle, Cheng Ju, and Jessica M. Franklin. 2018. Using super learner prediction modeling to improve high-dimensional propensity score estimation. *Epidemiology* **29**((1)). Lippincott Williams and Wilkins: 96–106. doi:[10.1097/EDE.0000000000000762](http://dx.doi.org/10.1097/EDE.0000000000000762).

Yang, Shu, Guido W. Imbens, Zhanglin Cui, Douglas E. Faries, and Zbigniew Kadziola. 2016. Propensity score matching and subclassification in observational studies with multi-level treatments. *Biometrics* **72**((4)). Blackwell Publishing Inc.: 1055–1065. doi:[10.1111/biom.12505](http://dx.doi.org/10.1111/biom.12505).

Yanovitzky, Itzhak, Elaine Zanutto, and Robert Hornik. 2005. Estimating causal effects of public health education campaigns using propensity score methodology. *Evaluation and Program Planning* **28**((2)): 209–220. Pergamon. doi:[10.1016/j.evalprogplan.2005.01.004](http://dx.doi.org/10.1016/j.evalprogplan.2005.01.004).

Yoon, Jinsung, James Jordon, and Mihaela van der Schaar. 2018. GANITE: Estimation of individualized treatment effects using generative adversarial nets. Undefined.

Zanutto, Elaine, Bo Lu, and Robert Hornik. 2005. Using propensity score subclassification for multiple treatment doses to evaluate a national antidrug media campaign. *Journal of Educational and Behavioral Statistics* **30**((1)): 59–73. SAGE Publications Inc. doi:[10.3102/10769986030001059](http://dx.doi.org/10.3102/10769986030001059).

Zhang, Linying, Yixin Wang, Anna Ostropolets, Jami J. Mulgrave, David M. Blei, and George Hripcsak. 2019. " The medical deconfounder: Assessing treatment effects with electronic health records. April. [http://arxiv.org/abs/1904.02098](http://arxiv.org).

# [8 ](#contents.xhtml#toc1_179)  
![image](images/inline1_1.jpg)

# [EHR Data Exploration, Analysis and Predictions: Statistical Models and Methods](#contents.xhtml)  
               

Gen Frances Stacia M. Vahed ZhuBritoDeSantisMaroufy

## ![image](images/inline1_1.jpg)  
8.1 Introduction

### 8.1.1 Statistical Challenges for EHR Data

Unlike traditional datasets attained from experimental studies and clinical trials, EHR datasets are big, messy, sparse, ultrahigh dimensional, and with high missing rates. These issues are often challenging to deal with during statistical data analysis and predictions. However, if the dataset is cleaned and processed, standard statistical methods may still be appropriate and possible to implement. In addition, because of ultrahigh dimensionality and potentially large sample sizes of EHR datasets, complicated and sophisticated statistical approaches are almost computationally impossible to implement. Therefore, in this chapter, we will focus on standard and computationally feasible statistical models for EHR data analysis such as general linear models, survival models, and linear mixed effect models. We hope to convince readers that these models, partnered with novel and efficient variable selection and dimensionality reduction methods, can effectively and precisely analyze EHR data.

### 8.1.2 Overview of Existing Methods

After data are extracted, cleaned, and processed, data exploration and visualization, by running exploratory data analysis (EDA), is suggested in selecting the most suitable statistical model for inference or prediction. In this section, we briefly introduce and review the common techniques and methods used to analyze EHR data.

Several statistical models have been used in EHR data analysis, but generalized linear models (GLM) have been proven to be more efficient and effective as they were also the most common algorithms to develop prediction models ([Goldstein et al. 2017](#ch08.xhtml#ref8_13)). GLMs are the foundation for many other advanced models and researchers have developed systemic theories and software toolkits making application GLMs fast and straightforward. There are many applications of GLMs to EHR data in recent literature. For example, by developing a novel hypothesis test of the high dimensional linear model, [Cai, Cai, and Guo (2019)](#ch08.xhtml#ref8_4) attempted to predict individualized treatment effects based on a given patient’s profile. [Wu et al. (2018)](#ch08.xhtml#ref8_42) implemented logistic regression and other machine learning methods to explore the risk factors associated with major depression disorder (MDD) recurrence. [Backenroth et al. (2017)](#ch08.xhtml#ref8_2) used logistic regression to determine the medications that are associated with hypertension.

On the other hand, although GLMs are commonly used to model EHR data, they are insufficient and often lacking when they encounter time-to-event questions. An example of these types of analyses can be predicting time to in-hospital death for patients with the subarachnoid hemorrhage diagnosis, using longitudinal clinical records such as lab results and clinical events measurements. Survival regression models are often better-suited choices to model these types of datasets. (see [Wu et al. 2019](#ch08.xhtml#ref8_44), [Vinzamuri and Reddy 2013](#ch08.xhtml#ref8_39), [Ranganath et al. 2015](#ch08.xhtml#ref8_29), [Hagar et al. 2014](#ch08.xhtml#ref8_16)). Of course, several important components of survival analysis need to be taken into account, such as the time to an event, study origin, and type of censoring. Furthermore, standard survival models cannot be directly applied to analyze EHR data due to the following limitations ([Ranganath et al. 2016](#ch08.xhtml#ref8_28), [Vinzamuri and Reddy 2013](#ch08.xhtml#ref8_39), [Hagar et al. 2014](#ch08.xhtml#ref8_16)):

*   Missingness of the covariates
    
*   Difficulty in determining study origin
    
*   Relationship between the covariates and the time to event is assumed to be linear
    
*   Difficulty in solving structured sparsity in high dimensional EHR data
    
*   Complexity of censoring
    

To overcome these limitations, several studies developed new survival models. For example, both [Dempsey and McCullagh (2018)](#ch08.xhtml#ref8_7) and [Ranganath et al. (2016)](#ch08.xhtml#ref8_28) have considered aligning the patients from the event of interest backward, rather than measuring time forward from an artificial starting time. [Ranganath et al. (2016)](#ch08.xhtml#ref8_28) also used latent process-deep exponential families to handle the missing data. [Vinzamuri and Reddy (2013)](#ch08.xhtml#ref8_39) proposed a new regularization linear model to solve structured sparsity in high dimensional EHR data.

Another characteristic of EHR data is its diversity of data formats. It contains both cross-sectional and longitudinal data. For traditional predictive modeling, ignoring this temporal information would result in biased models ([Singh et al. 2015](#ch08.xhtml#ref8_33)). Thus, it is essential to take advantage of existing statistical approaches capable of handling longitudinal data to model the temporal pattern of EHR data. In statistics, Analysis of Variance (ANOVA), Generalized Estimating Equations (GEE), and the mixed-effect models are often used to handle this problem (H. [Goldstein et al. 1995](#ch08.xhtml#ref8_14)). However, mixed effect models usually outperform ANOVA or GEE when handling complex missing data, irregularly timed data, and modeling the correlation of repeated measures ([Garcia and Marder 2017](#ch08.xhtml#ref8_11)). Additionally, mixed-effect models are the most frequently used technique in medical research in dealing with longitudinal data. Therefore, mixed-effect models will be our focus for addressing longitudinal data. Nevertheless, literature regarding the application of mixed-effect models to EHR data is sparse. To alleviate the high computation cost, a simulation study ([Rhodes et al. 2018](#ch08.xhtml#ref8_31)) provides different techniques to improve the efficiency of running mixed effect models on EHR data. Joint models of time-to-event and longitudinal data have also been applied to EHR data ([Gasparini et al. 2020](#ch08.xhtml#ref8_12), [Paige et al. 2018](#ch08.xhtml#ref8_25), [Maziarz et al. 2017](#ch08.xhtml#ref8_23)).

One question remains in dealing with longitudinal EHR data: how should we use the timestamps (event and record times)? [Hripcsak, Albers, and Perotte (2011)](#ch08.xhtml#ref8_20) illustrated that converting the clock time into sequence time is a good way to improve prediction performance. To characterize and take advantage of the time variable in EHR, many pre-processing and modeling approaches have been proposed, including time series construction, temporal parameterization, intrasubject normalization, differentiation of the temporal variables, as well as the introduction of explanatory variables, and regression models ([Levine, Albers, and Hripcsak 2018](#ch08.xhtml#ref8_22)). In this chapter, we will mainly focus on the regression models. In literature, many time series methods have been applied to clinical temporal data. [Levine, Albers, and Hripcsak (2016; 2018)](#ch08.xhtml#ref8_21) studied how lagged linear regression can be used to detect the physiological effects of drugs from lab tests. [Cheng et al. 2020](#ch08.xhtml#ref8_6), [Pimentel et al. (2013)](#ch08.xhtml#ref8_27) used Gaussian process models to reflect the temporal pattern of some clinical events or lab measurements. In the next section, lagged regression models and the Gaussian process will be reviewed.

Curse of dimensionality is another big challenge in using EHR data. Datasets including diagnoses, clinical events, labs, and medications easily pass thousands of variables. This is especially a concern with regard to predictive modeling and causal inference analysis. One strategy used to overcome the computation cost caused by high dimensionality involves determining which significant factors are associated with the outcome of interest (response). However, traditional variable selection methods do not work well for ultrahigh dimensional problems. [Fan and Lv (2007)](#ch08.xhtml#ref8_10) proposed a two-scale variable selection framework, Sure Independence Screening (SIS), which consists of large-scale screening followed by moderate-scale common variable selection methods. Here, common variable selection methods refer to regression models with different types of penalties on the coefficients. Least Absolute Shrinkage and Operation Selector (LASSO) ([Tibshirani 1996](#ch08.xhtml#ref8_35)) and Ridge regression ([Hoerl and Kennard 1970](#ch08.xhtml#ref8_18)) are the most popular penalized regression models used in the EHR prediction analysis to handle “big data” ([Zhang and Hong 2017](#ch08.xhtml#ref8_47); [Wu et al. 2017](#ch08.xhtml#ref8_43); [Stein et al. 2019](#ch08.xhtml#ref8_34)). Deciding how to eliminate the influence of confounding variables becomes a critical issue for causal inference in EHR. For example, to evaluate the treatment effects, [Shortreed and Ertefaie (2017)](#ch08.xhtml#ref8_32) proposed to combine variable selection methods with propensity score matching method to solve the high dimensionality issue.

Besides high dimensionality, EHR datasets often have large sample sizes as well. This then requires extra computation capacity and time to fit the models. Sophisticated statistical models such as joint molding, non-conjugate Bayesian approaches, and statistical models requiring numerical likelihood maximization are often too complicated and numerically slow. Moreover, most of these models are numerically impossible to implement on the big clinical data queried for EHR databases ([Chen and Xie 2014](#ch08.xhtml#ref8_5)). Divide and conquer approaches may provide a solution to apply these models to big EHR datasets. In fact, many novel methodologies have been proposed to deal with the scale problem. These include “divide and conquer” techniques and subsampling approaches ([Rhodes et al. 2018](#ch08.xhtml#ref8_31)). However, limited literature exists for handling the EHR data size problem, even though weighted regression and meta-analysis techniques were recently proposed and applied to EHR data ([Rhodes et al. 2018](#ch08.xhtml#ref8_31)).

Moreover, once the model fitting process is complete, an evaluation of whether the results are influenced by the uncertainty of the data or the calibration parameters should be considered. Thus, sensitivity analysis and model validation are necessary to examine the fitted model. In this chapter, we discuss some common techniques including the area under the curve (AUC) of the receiver operator characteristic curve (ROC) to give the readers a better understanding of the way they are used in analyzing EHR data.

## ![image](images/inline1_1.jpg)  
8.2 Data Exploration and Visualization

Exploratory data analysis (EDA) is a preliminary analysis of the data that often fosters our understanding of the data and complements the use of hypothesis tests and model building in subsequent analysis. In general, it emphasizes the graphic representation of data and some simple tests can be utilized to uncover the pattern hidden in the data. EDA can trace back to the work of [Tukey (1977](#ch08.xhtml#ref8_37)). Other classical works on EDA are ([Mosteller and Tukey 1977](#ch08.xhtml#ref8_24), [Velleman and Hoaglin 1981](#ch08.xhtml#ref8_38), [Behrens 1997](#ch08.xhtml#ref8_3)).

Most EDA techniques take advantage of graphs, including histograms, density plots, box plots, stem-and-leaf plots, and dot plots. In the modern era, with the rapid development of computers, researchers can explore data using different visualization tools. Now EDA is no longer restricted to conventional methods, rather, it has become a philosophy for data analysis. As [Grolemund (2016)](#ch08.xhtml#ref8_15) pointed out, EDA is an iterative cycle and it consists of generating questions, visualizing and transforming the data, and further refining questions. A wealth of software can help with EDA, such as Tableau, Infogram, Datawrapper, ggplot2 in R, matplotlib in Python, etc.

For EHR data analysis, the summary statistics report mentioned in [Chapter 3](#ch03.xhtml#chapter3) is the basic output of an EDA process. The report is EHR specific, which summarizes important and useful information from the extracted data. Although analysts can derive many other summaries from the data, those items in the report are believed to be more informative and meaningful, since they are refined based on our EDA experiments. For example, when investigating the most significant medications for SAH patients, we found that solely ranking the patient count by medications is not enough, because the medication frequency for SAH patients may follow the same medication frequency pattern for the general population, as shown in [Table 8.1](#ch08.xhtml#table8_1).

**Table 8.1** Top Medications Based on Frequencies in SAH Patients and Cerner General Population

| **Top Medications in Cerner General Population** || **Top Medications in SAH Patients** |
| --- | --- |
| Lvp Solution || Lvp Solution |
| --- | --- |
| Ondansetron || Ondansetron |
| Acetaminophen || Sodium Chloride |
| Sodium Chloride || Acetaminophen |
| Morphine || Potassium Chloride |
| Fentanyl || Fentanyl |
| Lidocaine || Labetalol |
| Midazolam || Morphine |
| Hydromorphone || Heparin |
| Acetaminophen/Hydrocodone || Midazolam |

Therefore, how to adjust the influence of the general population is also an interesting topic. Fortunately, many statistical tests can be used to generate significant medications for SAH patients. The p-value or risk ratio of each medication can serve as an index to rank the importance of the medications for SAH patients. Methodologies concerning the statistical tests will be discussed in [Section 8.3](#ch08.xhtml#sec8_3).

## ![image](images/inline1_1.jpg)  
8.3 Statistical Models for EHR Data

### 8.3.1 Contingency Tables

A contingency table (also known as a cross-tabulation or crosstab) summarizes the frequency of subjects classified by categorical variables. For example, [Table 8.2](#ch08.xhtml#table8_2) lists the two-by-two table of the number of subjects with/without SAH record versus dopamine/Non\_doapmine treatment. Here, Non-SAH patients represent the patients with at least one diagnosis or one medication record but without SAH diagnosis from the Cerner database. The contingency table reveals the relationship between different categorical variables and is an effective function to conduct preliminary statistical analyses for many problems.

**Table 8.2** Cross Counts of Dopamine by SAH Patients and Non-SAH Patients

|  || **Dopamine** || **Non-dopamine** |
| --- | --- | --- |
| SAH Patients || 991 || 27304 |
| --- | --- | --- |
| Non-SAH Patients || 210547 || 17448416 |

We briefly explain the mechanism of statistical tests on contingency tables. Suppose *X* and *Y* are categorical variables, each with two categories, and each row(column) of the table represents one category of *X* (*Y*). Then the intersection of each row and each column is called a cell. Therefore, the total four cells (*X*[1], *Y*[1]), (*X*[1], *Y*[2]), (*X*[2], *Y*[2]) and (*X*[2], *Y*[2]) in [Table 8.3](#ch08.xhtml#table8_3) present all the possible combinations between the two variables *X* and *Y*.

**Table 8.3** A Contingency Table

|  || *Y*[1] || *Y*[2] |
| --- | --- | --- |
| *X*[1] || *n*[11] || *n*[12] |
| --- | --- | --- |
| *X*[2] || *n*[21] || *n*[22] |

Assume that a randomly chosen subject from the population falls in one cell of the contingency table with probability *π*[*i**j*] = *P*(*X*\=*i*,*Y*\=*j*). Denote the marginal distributions *P*(*X*\=*i*) and *P*(*Y*\=*j*) by {*π*[*i*+]} and {*π*[ + *j*]}, respectively, where *π*[*i*+] = *π*[*i*1] + *π*[*i*2] and *π*[ + *j*] = *π*[1*j*] + *π*[2*j*]. Similarly, denote *n*[*i**j*] and *p*[*i**j*] as

the observed cell count and proportion from the samples, respectively. Then *n*[*i**j*] and *p*[*i**j*] follow

$p\_{\\mathit{ij}} = \\frac{n\_{\\mathit{ij}}}{n},$

where *n* = ∑[*I*, *j*]*n*[*i**j*] is the total sample size. For annotation, let *n*[*i*+] = *n*[*i*1] + *n*[*i*2] and *n*[ + *j*] = *n*[1*j*] + *n*[2*j*]. The variable *X* can be called the exposure, and the variable *Y* can be called the response or the outcome.

For the cohort study, researchers are often interested to know whether the exposure is associated with the outcome. For instance, based on [Table 8.2](#ch08.xhtml#table8_2), researchers want to know whether the prescribing dopamine for SAH patients is more likely than that for non-SAH patients is worth investigating. Here, the disease SAH is the exposure and the response is the administration of dopamine. In statistics, we tend to formulate this problem by comparing whether the distribution of *Y* given *X*[1]is the same as the distribution of *Y* given *X*[2]. This is also known as an independence test problem between two variables.

For two-by-two contingency tables, the distribution of *Y* given *X*[1] follows a binomial distribution. For a subject in row 1, let *π*[1] denote the probability of a success (say *Y*[1] represents the success), then (1-*π*[1]) would be the probability of a failure. Likewise, let *π*[2] denote the probability of a success for a subject in row 2. To answer the statistical independence question, the difference of proportions *π*[1] − *π*[2] is our target to test. We can use the Wald test to obtain the P-value, and confidence interval based on the sample difference *p*[1] and *p*[2] and its estimated standard error, where $p\_{i} = \\frac{n\_{i1}}{n\_{i +}}$. Readers can find more details of the Wald test in ([Agresti 1996](#ch08.xhtml#ref8_1)).

### 8.3.2 Chi-Square Test

An alternative test to the Wald test is the Chi-square test. If we are interested in assessing whether the probability of each cell is equal to the hypothesized values {*π*[*i**j*]} (we call it the null hypothesis *H*[0]), a straightforward way is to compare the observed cell counts {*n*[*i**j*]} and expected frequencies {*μ*[*i**j*] = *n**π*[*i**j*]} where n is the total sample size.

Karl Pearson fulfilled this idea by proposing the famous Chi-square statistic:

$X^{2} = \\frac{\\sum\\left( {n\_{\\mathit{ij}} - \\mu\_{\\mathit{ij}}} \\right)^{2}}{\\mu\_{\\mathit{ij}}}.$

It can be seen that greater differences {*n*[*i**j*] − *μ*[*i**j*]} lead to larger *X*² values; and stronger evidence against *H*[0]. The P-value can be obtained by calculating *P*(*X*²\>*o**b**s**e**r**v**e**d**X*²). In order to apply the Chi-square test, the values of {*μ*[*i**j*]} must be known. However, in reality, this may not always be the case. In two-way contingency tables, *π*[*i**j*] can be simplified through *π*[*i**j*] = *π*[*i*+]*π*[ + *j*] under the null hypothesis of statistical independence. We can estimate the unknown marginal probabilities *π*[*i*+] and *π*[ + *j*] with sample marginal proportions, $\\frac{n\_{i +}}{n}$ and $\\frac{n\_{+ j}}{n}$, respectively. Therefore, the estimated expected frequencies are

${\\widehat{\\mu}}\_{\\mathit{ij}} = n{\\widehat{\\pi}}\_{\\mathit{ij}} = n\\frac{n\_{i +}}{n}\\frac{n\_{+ j}}{n} = \\frac{\\left( {n\_{i1} + n\_{i2}} \\right)\\left( {n\_{1j} + n\_{2j}} \\right)}{n}.$

After plugging *μ̂*[*i**j*] into the Chi-square statistic, the P-value can be obtained because the Chi-square statistic *X*² approximately follows the Chi-square distribution. For every medication, this P-value can be used to indicate the importance of the medication.

Note that Chi-square tests of independence have limitations. The Chi-square approximation is often not precise when the expected frequencies of some cells are less than 5. The hypergeometric test (Fisher’s exact test) can be resorted to address this condition.

### 8.3.3 Hypergeometric Test

The chi-square test uses the laws of large numbers in the form of the central limit theorem. When the underlying assumptions of the chi-square test do not hold, the hypergeometric test (Fisher Exact test) can be used. Given the total sample size n, marginal row sizes *n*[1+] and *n*[2+], and the cell count *n*[11], the whole table can be determined, which means all the other cell counts can be calculated. The probability of the cell counts has the hypergeometric distribution. The probability of the table is expressed in terms of *n*[11] only, which is

$P\\left( n\_{11} \\right) = \\frac{\\begin{pmatrix} n\_{1 +} \\\\ n\_{11} \\\\ \\end{pmatrix}\\begin{pmatrix} n\_{2 +} \\\\ {n\_{+ 1} - n}\_{11} \\\\ \\end{pmatrix}}{\\begin{pmatrix} n \\\\ n\_{+ 1} \\\\ \\end{pmatrix}}.$

where $\\begin{pmatrix} a \\\\ b \\\\ \\end{pmatrix}$ is the binomial coefficient. The P-value is the sum of *P*(*n*^(\*)), where *n*[11] ≤ *n*^(\*) ≤ min (*n*[ + 1],*n*[1+]).

The P-value can be utilized as an indicator to rank the medications or diagnosis in EHR cohort studies.

For example, the top medications in SAH patients based on P-value in the hypergeometric test are listed in [Table 8.4](#ch08.xhtml#table8_4). The ranks are given by the significant degree of the P-value.

**Table 8.4** The Adjusted Ranks of Medications Using the Hypergeometric Test

| **Medication** || **p\_value** |
| --- | --- |
| Nicardipine || 0 |
| --- | --- |
| Mannitol || 0 |
| Glucagon || 0 |
| Enalapril || 0 |
| Alteplase || 0 |
| Polyethylene Glycol 3350 || 0 |
| Vasopressin || 0 |
| Esomeprazole || 0 |
| Thrombin Topical || 0 |
| Codeine || 0 |
| APAP/Butalbital/Caffeine || 0 |
| Calcium Gluconate || 0 |
| Magnesium Oxide || 0 |
| Nystatin || 0 |
| Thiamine || 0 |
| Papaverine || 0 |
| Aminocaproic Acid || 0 |
| Balsam Peru/Castor Oil/Trypsin Topical || 0 |
| Sorbitol || 0 |
| Nafcillin || 0 |
| Atropine Ophthalmic || 0 |
| Valproic Acid || 0 |
| Amantadine || 0 |
| Lacosamide || 0 |
| Prothrombin Complex || 0 |
| Minoxidil || 0 |
| Factor IX Complex || 0 |
| Citric Acid/Potassium Bicarbonate || 0 |
| Coagulation Factor VIIa || 0 |
| Vitamin E Topical || 0 |
| Amobarbital || 0 |
| Urea || 2.12E-11 |

However, because the number of non-SAH patients is large, compared with SAH patients, the P-values of many medications are 0. We can then take advantage of relative risks to readjust the ranks, which will be explained in Section 8.3.4.

In [Section 8.3.1](#ch08.xhtml#sec8_003_001), we mentioned the Wald test can be used to test the difference between the proportions *π*[1] and *π*[2]. Relative risk is another useful indicator to evaluate the difference, though no common statistical tests are available to test the significance of it. For a two-by-two table, relative risk (RR) is the ratio

$\\mathit{RR} = \\frac{\\pi\_{1}}{\\pi\_{2}}.$

where RR is 1, which means *π*[1] is equal to *π*[2], we can infer that the response is independent of the exposure. The further RR is away from 1, the larger the difference is between proportions *π*[1] and *π*[2]. Hence, it gives us more evidence suggesting the success probabilities within the two rows are more different. In practice, we often use sample proportions *p*[1] and *p*[2] to estimate the RR and obtain the sample relative risk $\\frac{p\_{1}}{p\_{2}}$. For example, in [Table 8.2](#ch08.xhtml#table8_2), the sample risk

ratio is 2.94. The sample proportion of dopamine in SAH patients is 194% higher than that in non-SAH patients. Based on the data, it indicates that dopamine may be a medicine that is particularly beneficial to SAH patients. Clinically, it is also true that dopamine is a commonly used vasopressor to increase blood pressure to prevent delayed cerebral ischemia (DCI) in SAH patients. Likewise, we can use the RR to rank all other medications.

## ![image](images/inline1_1.jpg)  
8.4 GLM

When determining which statistical models to use for EHR data, an ordinary linear regression (OLR) is a good starting place. It is simple and easy to implement; we can gain valuable information from the data, and provide a baseline result for other advanced models. Next, we will give a brief introduction to the OLR and GLMs.

In OLR, the relationship between the response variable *y*[*i*] and covariates *x*[*i*] is assumed as

*E*(*y*[*i*]|**x**[*i*]) = **x**[*i*]^(*T*)**β**.

A GLM is a generalization of an ordinary linear model, and it introduces the link function *f*(*x*) to extend the relationship as

*f*(*E*(*y*[*i*]|**x**[*i*])) = **x**[*i*]^(*T*)**β**.

Commonly used link functions include the identity, log, and logit functions. If we consider the identity function as the link function, the GLM is just an OLR. If the link function is the logit function,

$\\log\\left( \\frac{x}{1 - x} \\right),$

the GLM then becomes the familiar logistic regression model,

$\\begin{matrix} {\\log\\left( \\frac{\\pi\\left( \\mathbf{x}\_{i} \\right)}{\\left. 1 - {\\pi\\left( \\mathbf{x} \\right.}\_{i} \\right)} \\right) = \\mathbf{x}\_{i}^{T}\\mathbf{\\beta},} \\\\ \\end{matrix}$

where *π*(**x**[*i*]) = *E*(*y*[*i*]). Logistic regression is a useful tool to model data in which the response variable is binary. Because the expectation of the binary random variable following the Bernoulli distribution is equal to the probability of “success”, *π*(**x**[*i*]) can be interpreted as the probability of “success” at the value of **x**[*i*] for response variable *y*[*i*]. [Equation (8.1)](#ch08.xhtml#eqn8_1) implies that

$\\pi\\left( \\mathbf{x}\_{i} \\right) = {\\frac{\\exp\\left( {\\mathbf{x}\_{i}^{T}\\mathbf{\\beta}} \\right)}{1 + \\exp\\left( {\\mathbf{x}\_{i}^{T}\\mathbf{\\beta}} \\right)}.}$

Then the odds of “success” are

$\\begin{matrix} {\\frac{\\pi\\left( \\mathbf{x}\_{i} \\right)}{1 - \\pi\\left( \\mathbf{x}\_{i} \\right)} = \\exp\\left( {\\mathbf{x}\_{i}^{T}\\mathbf{\\beta}} \\right)} \\\\ \\end{matrix}$

Hence odds ratio (OR) of “success” equals exp (*β*[*p*]), which means that the odds of “success” when *X*[*p*]increases by one unit is exp (*β*[*p*]) times the odds at *X*[*p*] when adjusting for other covariates (staying unchanged). The odds ratio indicates the influence of one covariate on the odds given to the other covariates in the model. For most predictive modeling in EHR studies, logistic regression is more commonly used.

A generalization of logistic regression is multinomial logistic regression for categorical outcomes with more than two categories. These models can be used for both nominal and ordinal responses. Let us assume the number of categories is *J*. Let {*π*[1],…,*π*[*J*]} denote the probabilities of response *y*[*i*] falling into categories {1,…,*J*}, where ∑[*j*]*π*[*j*] = 1, and *i* denotes the *i*th subject. The most common model for nominal response is the baseline-category logits model, in which the last category *J* is selected as the baseline, and *J* − 1 logit models are built by pairing each response category with the reference category. Each logit model is the linear relationship between the $\\log⁡\\left( \\frac{\\pi\_{j}}{\\pi\_{J}} \\right)$ and predictors **x**[**i**]. Mathematically, it is

$\\log\\left( \\frac{\\pi\_{j}}{\\pi\_{J}} \\right) = \\alpha\_{j} + \\mathbf{x}\_{i}^{T}\\mathbf{\\beta}\_{j},j = 1,\\ldots,J - 1.$

If *J* is 2, then the multinomial logistic model will be reduced to a binary logistic model as described earlier.

For ordinal responses, we need models to reflect the ordinal nature of the response, hence, cumulative logit models are commonly used for this purpose. Assume the *J* categories are ordered from 1 to *J*. Similarly, let {*π*[1],…,*π*[*J*]} denote the probabilities of response *y*[*i*] falling into categories {1,…,*J*}, where ∑[*j*]*π*[*j*] = 1 and *i* denotes the *i*th subject. This model is established on the logits of the cumulative probabilities of the form (*y*[*i*] ≤ *j*) = *π*[1] + … + *π*[*j*] . It has the following form

${logit}{({P{({y\_{i} \\leq j})}})} = \\log\\left( \\frac{P\\left( {y\_{i} \\leq j} \\right)}{1 - p\\left( {y\_{i} \\leq j} \\right)} \\right) = \\alpha\_{j} + \\mathbf{x}\_{i}^{T}\\mathbf{\\beta}\_{j},j = 1,\\ldots,J - 1$

where **x**[*i*] represents the predictors of *i*th subject.

Besides binary and multinomial logistic regression, log-linear regression (Poisson regression) is another important type of generalized linear model. For more information, [Agresti (1996)](#ch08.xhtml#ref8_1) provides a detailed description of logistic regression.

## ![image](images/inline1_1.jpg)  
8.5 Survival Model

Survival analysis can be performed through a wide range of models, many of which focus on the estimation of hazard rate. The most popular survival model is the Cox proportional hazard regression model. Here we will briefly present some basic concepts of survival regression models and introduce the Cox model.

Suppose we are interested in one event, for example, death, recurrence of a disease, the development of one chronic disease. Let *T* be the time until the event of interest occurs. Two important functions characterize the distribution of *t*, survival function *S*(*t*) and hazard function *h*(*t*). The survival function is the probability that one subject is still alive at a specific time point *t*; the hazard function is the chance the subject experiences the event at the very short instant after time point *t*.

Mathematically, the survival function is defined as

*S*(*t*) = *P*(*T*\>*t*) = 1 − *F*(*t*),

where *F*(*t*) is the cumulative distribution function of *T*.

The hazard rate is defined by

$h\\left( t \\right) = \\lim\\limits\_{\\Delta t\\rightarrow 0}{\\frac{P\\left( {t \\leq T \\leq t + \\Delta t} \\middle| {T \\geq t} \\right)}{\\Delta t}.}$

Clearly *h*(*t*)*Δ**t* indicates the probability of the occurrence of an event in an infinitesimal time period.

In reality, we often want to relate the time-to-event to covariates **x**. In EHR, covariates ***x*** can include some demographic variables or other recorded variables such as lab tests. The Cox model provides a way to link the hazard function and covariates together. Specifically, its form is,

*h*(*t*|**x**) = *h*[0](*t*)exp (*β*^′**x**)

where *h*[0](*t*) is the hazard at baseline.

## ![image](images/inline1_1.jpg)  
8.6 Mixed-Effect Models

When the responses are not independent or we have longitudinal covariates, GLMs fail to fit the data and learn all the structure and information in the data. Here, we introduce mixed-effect models to handle longitudinal data commonly seen in EHR data. We briefly illustrate these models through an example related to blood pressure measurements as a clinical event record.

Assume we want to model blood pressure trends with a few explanatory variables for a specific group of *m* patients. Let *y*[*i**j*], *j* = 1, 2, …*n* represent the repeated measurement of blood pressure of *i**t**h* patient, where *j* stands for the measurement times. For simplicity, we assume the total measurement times for all patients are the same, namely *n*. Then the relationship between the response and the explanatory variables is modeled as

*y*[*i**j*] = **x**[*i**j*]^(*T*)**β** + **z**[*i**j*]^(*T*)**b**[*i*] + *ϵ*[*i**j*,]

where **x**[*i**j*]^(*T*) and **β**denote the fixed-effects covariates and fixed-effects coefficients respectively, **z**[*i**j*]^(*T*) and **b**[*i*] denote the fixed-effects covariates and random-effects vector respectively, **b**[*i*] follows *N*(0,**D**) and *ϵ*[*i**j*] denote the measurement error of the *j**t**h* measurement of the *i**t**h* patient. It can be seen that the mixed-effect model is an extension of the OLR model. We can interpret the fixed-effect component as the population mean and the random-effect component as the variation from the population mean for a specific subject. In our example, population mean could be general blood pressure patterns, such as one smooth curve centered at 90 and variation could be subject-specific fluctuation around the mean curve. By introducing the random effect, the correlation between repeated measurements of blood pressure becomes evident and is described. Readers may refer to ([Wu and Zhang 2006](#ch08.xhtml#ref8_41), [Diggle et al. 2002](#ch08.xhtml#ref8_8)), for more details regarding the mixed-effect model.

## ![image](images/inline1_1.jpg)  
8.7 Time Series Analysis

### 8.7.1 AR, MA and ARMA Model

One way of directly modeling the temporal pattern in EHR data is to use common time series models. Time series models are specific types of models for fitting correlated responses, in which the correlation structure deals with the repeated longitudinal measurements. For example, it is reasonable to assume the current value of one lab test, *y*[*t*], is related to previous measurements, *y*[*t* − 1], *y*[*t* − 2], …, *y*[*t* − *p*], which are called lagged values (within a certain time duration). Standard time series models are Autoregression (AR) and Moving Average (MA). AR reflects a linear relationship among the measurements of the response at different times, and has the following form,

*y*[*t*] = *ϕ*[0] + *ϕ*[1]*y*[*t* − 1] + *ϕ*[2]*y*[*t* − 2] + … + *ϕ*[*p*]*y*[*t* − *p*] + *a*[*t*]

where *a*[*t*] is the error term, and *p* is the order of lag of *y*[*t*].

MA models relate *y*[*t*] to a white noise series {*a*[*t*]}, which means a series of identical and independent distributed random variables with finite means and variance. An MA(q) model is

*y*[*t*] = *c*[*o*] + *a*[*t*] − *θ*[1]*a*[*t* − 1] − … − *θ*[*q*]*a*[*t* − *q*],

where *q* is the lag order of *a*[*t*].

In some scenarios, the AR or MA models may need high-order lag terms with many parameters to adequately describe the dynamic structure of the data ([Tsay 2010](#ch08.xhtml#ref8_36)). The autoregressive moving-average (ARMA) models are then introduced to solve this difficulty. Basically, an ARMA model incorporates both AR terms and MA terms so that fewer parameters will be used in the model. A general ARMA(p, q) model follows

$y\_{t} = \\phi\_{0} + \\sum\\limits\_{i = 1}^{p}{\\phi\_{i}y\_{t - i} + a\_{t} - \\sum\\limits\_{i = 1}^{q}{\\theta\_{i}a\_{t - i}}},$

where {*a*[*t*]} is a white noise series, and p and q are the lag orders.

Adopting the idea of the above models with lagged terms, [Levine et al. (2018)](#ch08.xhtml#ref8_22) used lagged linear regression to model the relationship between drugs and lab tests. Denote *y*[*t*] as a laboratory value at sequence time t, and *x*[*t* − *τ*] represents the drug value at time *t* − *τ*. The multivariate lagged drug model can be described as

$y\_{t} = c + \\sum\\limits\_{\\tau = 1}^{L}{\\beta\_{\\tau}x\_{t - \\tau} + \\epsilon}$

where *ϵ* is the error term. Variants of this model are discussed in ([Levine, Albers, and Hripcsak 2018](#ch08.xhtml#ref8_22)).

### 8.7.2 Gaussian Process

Often, because of temporal sparsity and high missing rates of medical data, conventional time series models, such as hidden Markov models and ARMA models are limited to apply. However, Gaussian processes are widely used to tackle irregular temporal observations (Cheng et al. 2017). We briefly introduce Gaussian processes.

A Gaussian process is a collection of random variables, any finite number of which have a joint Gaussian distribution. For the multivariate Gaussian distribution, it can be specified by its mean vector and covariance matrix. Likewise, a Gaussian process which can be represented by the mean function *m*(*x*) and the covariance function *k*(*x*,*x*^′) as

*m*(*x*) = *E*\[*f*(*x*)\]

*k*(*x*,*x*^′) = *E*\[(*f*(*x*)−*m*(*x*))(*f*(*x*^′)−*m*(*x*^′)).*k*

The Gaussian process then can be written as

*f*(*x*) ∼ 𝒢𝒫(*m*(*x*),*k*(*x*,*x*^′)).

The difference between a Gaussian process and a multivariate normal vector can be understood this way: the distribution of a Gaussian process is the joint distribution of infinitely many random variables, while the distribution of a multivariate normal vector is the joint distribution of the finite vector of random variables.

There are different forms of the covariance function, to illustrate, the squared exponential covariance function specifies the covariance of any pairs of random variables as

$\\mathit{cov}\\left( {f\\left( x\_{p} \\right),f\\left( x\_{q} \\right)} \\right) = k\\left( {x\_{p},x\_{q}} \\right) = \\mathit{\\exp}\\left( {- \\frac{1}{2}\\left| {x\_{p} - x\_{q}} \\right|} \\right).$

So the covariance will vary monotonously with the distance between the two time points *x*[*p*]*a**n**d**x*[*q*], More details regarding Gaussian processes can be found in ([Rasmussen and Williams 2005](#ch08.xhtml#ref8_30)).

Gaussian processes can be applied to times series variables in EHR. For example, [Pimentel et al. (2013)](#ch08.xhtml#ref8_26) used Gaussian processes to obtain the mean trajectories of systolic blood pressure and temperature for each patient. The mean trajectories from all patients were clustered to detect the abnormal physiological pattern of systolic blood pressure or temperature.

## ![image](images/inline1_1.jpg)  
8.8 Variable Selection Methods

The two main purposes for fitting a statistical model are interpretation and prediction. When building a predictive model, the bigger and more flexible the model is, the better and more precise the predicted values will be. However, bigger models and more flexibility compromises interpretation. Therefore, for fitting many of the models introduced in earlier sections, we need tools and methods to select the variables carefully, so that we avoid over-fitting. One particular circumstance where interpretation might turn out wrong or counter-intuitive is when many correlated variables are included in a regression model, known as multicollinearity.

Generally, variable selection methods fall into two classes. One class can be summarized as the variable subset selection with linear regression using ordinary least squares (OLS). In this approach, statistical hypothesis testing for model coefficients is used as a common criterion for selecting the final variables into the model. Approaches such as stepwise and purposeful variable selection are examples of this class. Although OLS can produce unbiased prediction results, it suffers from the high variance of the estimation and unsatisfactory interpretation, especially in high dimension problems. Penalization techniques have been suggested to improve the traditional OLS-based variable selection methods. There are many penalization-based methods, among which the most commonly used methods are LASSO and its extensions, smoothly clipped absolute deviation (SCAD), minimax convex penalty (MCP), etc. In this section, we briefly introduce these methods.

### 8.8.1 Stepwise Variable Selection

Stepwise variable selection can be classified as either forward stepwise selection or backward stepwise selection. Both methods follow the same strategy of variable selection: add or remove variables within iterative steps. The difference between them is the direction of adjusting the model. Forward stepwise selection starts with the intercept and building up the model, while backward stepwise selection begins with the full model and reduces redundant variables.

The algorithm for forward stepwise selection includes the following 4 steps.

STEP 1. Begin with the null model, contains no predictors and only the intercept (in this case, the mean of the outcome).

STEP 2. Consider all models that augment the previous model with one additional predictor that has not yet been selected.

STEP 3. Choose the model that shows an improvement of the previous model, typically determined by the residual sum of squares (RSS).

STEP 4. Repeat Step 2 through 3 until some stopping rule is achieved. The rule can be the number of variables required in the final model, for example.

Backward stepwise selection starts with a full model including all predictors. All models containing all but one of the predictors are created. The model having the smallest RSS is chosen which contains one less variable. The process is repeated until reducing any more variables from the model causes a statistically significant increase in RSS.

### 8.8.2 Purposeful Variable Selection

Both stepwise methods work solely based on statistical significance criteria, but are completely ignorant of the practical significance of covariates for regressing a response of interest. Therefore, sometimes variables with a clear clinical relationship with the response are omitted from the model. To overcome this issue, the purposeful variable selection procedure was suggested by ([Hosmer and Lemeshow 2000](#ch08.xhtml#ref8_19)). This methodology uses significance and change-in-estimate criteria for variable selection and allows the analyst to make variable selection decisions at each step of the modeling process.

STEP 1. Perform the univariate analysis to identify potential covariates. The variables that have the P-value < 0.25, as well as variables that are clinically significant, are included for further multivariable analysis in step 2.

STEP 2. A multivariate model is fitted with all variables selected from step 1. Further, the variables with a P-value >0.05 are eliminated from the multivariate model and a new smaller model is fitted. These two models are then compared using a partial likelihood ratio test.

STEP 3. Change-in-estimate criteria are used to identify the confounding variables. Thus, the larger model and the smaller model are compared to identify a change in the magnitude of any other coefficient estimates by 20%, in such cases each dropped variable is added back to the model. This process is repeated several times until all important variables are included in the model.

STEP 4. Each variable not selected in step 1 is added into the model from step 3. All the significant variables identified in step 4 are retained in the model.

STEP 5. The linearity assumption of continuous variables is checked, and appropriate correction is made.

STEP 6. Interaction effects are studied, and important interaction terms are included in the model.

STEP 7. The goodness of fit is performed on the final model.

### 8.8.3 Sis

All the models described in the earlier sections (except for shrinkage and penalized likelihood methods) assume that the number of observations is much bigger than the dimensionality (number of the covariates) of the model (*n* ≫ *p*).

However, in EHR datasets, with thousands of variables and clinical biomarkers available, this assumption is often ignored. This curse of dimensionality causes problems such as collinearity among the predictors, noise accumulation, and computation cost ([Fan and Lv 2007](#ch08.xhtml#ref8_10)). To solve this problem, one way is to use shrinkage methods such as LASSO and its variations. Another method for dealing with this issue is SIS ([Fan and Lv 2007](#ch08.xhtml#ref8_10)) which was claimed to be suitable for dealing with ultrahigh dimensional problems. For a linear regression model

**y** = **X****β** + **ϵ**

suppose **y** = (*y*[1],…,*y*[*n*]) is the response vector with dimension *n*, **X** = (**x**[(1)],…,**x**[(*p*)]) is the *n* × *p* design matrix and **x**[(*i*)] is the *i*th covariate among the total *p* covariates, **β** = (*β*[1], …, *β*[*p*])^(*T*) is the *p*\-dimensional regression coefficient vector, and **ϵ** = (*ϵ*[1],…,*ϵ*[*p*])^(**T**) is the *n*\-dimensional error vector. SIS is performed in two different steps. In the first step, it assumes there are a given number of covariates that influence the outcome while the rest are considered as noise. Let ℳ[\*] represent those significant variables. Then based on the magnitude of the marginal correlation $\\hat{\\textit{corr}}\\left( {\\mathbf{x}\_{(i)},\\mathbf{y}} \\right)$ of **x**[(*i*)] and **y**, SIS chooses the top *d* covariates to build the set $\\widehat{\\mathcal{M}}$; in other words,

$\\widehat{\\mathcal{M}} = {\\{{1 \\leq i \\leq p:{|{\\hat{\\mathit{corr}}\\left( {\\mathbf{x}\_{(i)},\\mathbf{y}} \\right)}|}{is\\ among\\ the\\ top\\ d\\ largest\\ ones}}\\}},$

where $\\hat{\\mathit{corr}}$ stands for the sample Pearson correlation. Next, common regularization variable selection methods including Ridge regression, LASSO, and its various extensions can be utilized to further screen the reduced set $\\widehat{\\mathcal{M}}$.

The key idea of SIS is to regress the response to each covariate. However, it may cause some issues if the assumptions of SIS are not satisfied. For example, some unimportant predictors that are highly correlated with the important predictors can have higher priority to be selected by SIS than other important predictors that are relatively weakly related to the response ([Fan and Lv 2007](#ch08.xhtml#ref8_10)). The iterative SIS (ISIS) is proposed to overcome the weak points of SIS. This contains two steps. In the first step, use an SIS based model selection method such as the SIS-LASSO to select a subset of variables **C**[1]. In the second step, it will treat the residuals from the step 1 as the new response and apply the same SIS based method in the step 1 to the remaining variables (**x**[(1)],…,**x**[(**p**)]) ∖ **C**[1] which results in a subset of variables **C**[2]. Implementing the previous two steps repeatedly until the union of the disjoint subsets **C**[1], …**C**[**l**] has a size less than **n**. Readers can view ([Fan and Lv 2007](#ch08.xhtml#ref8_10)) for more details.

### 8.8.4 Penalty-Based Methods

Penalty-based variable selection methods can be generalized into the following optimization problem:

$\\min\\limits\_{\\mathbf{\\beta}}\\left\\| {\\mathbf{y} - \\mathbf{X}\\mathbf{\\beta}} \\right\\|\_{2}^{2} + \\sum\\limits\_{i = 1}^{p}{P\_{\\lambda}\\left( \\beta\_{i} \\right).}$

where ∥•∥[2] denotes the L-2 norm, *P*[*λ*](*β*[*i*]) is the penalty function imposed on the coefficient *β*[*i*]. Different forms of the penalty function lead to two main types of penalty-based methods, norm-based regularization methods and concave function-based regularization methods.

Norm-based regularization methods include both LASSO, which uses an L1 penalty |*β*[*i*]|, and ridged regression which uses an *L*2 penalty ∥*β*[*i*]∥[2]². If *P*[*λ*](*β*[*i*]) are some specific concave functions, then the optimization problem can fall into one of the following common variable selection methods: smoothly clipped absolute deviation (SCAD) ([Fan and Li 2001](#ch08.xhtml#ref8_9)), and minimax convex penalty (MCP) (C.-H. [Zhang 2010](#ch08.xhtml#ref8_46)). Specifically, for SCAD,

$P\_{\\lambda}\\left( \\beta \\right) = \\left\\{ {\\begin{matrix} {\\lambda,} & {\\mathit{if}\\left| \\beta \\right| \\leq \\lambda} \\\\ {\\frac{a\\lambda - \\left| \\beta \\right|}{a - 1},} & {\\mathit{if}\\lambda < \\left| \\beta \\right| < a\\lambda} \\\\ {0,} & {\\mathit{if}\\left| \\beta \\right| \\geq a\\lambda} \\\\ \\end{matrix}.} \\right.$

For MCP,

$P\_{\\lambda}\\left( \\beta \\right) = \\left\\{ \\begin{matrix} {\\lambda\\left| \\beta \\right| - \\frac{x^{2}}{2\\gamma},} & {\\mathit{if}\\left| \\beta \\right| \\leq \\gamma\\lambda} \\\\ {0.5\\gamma\\lambda^{2},} & {\\mathit{if}\\left| \\beta \\right| > \\gamma\\lambda} \\\\ \\end{matrix} \\right.$

Among the regularization methods, LASSO is the most commonly used in various fields of science, including statistics, machine learning, econometrics, engineering, etc. One important advantage of LASSO that distinguishes it from Ridge regression is that LASSO has the advantage of shrinking some coefficients to exactly zero when the tuning parameter *λ* is sufficiently large, thus performing variable selection and reducing dimensionality. This is due to the form of the penalty function in [Equation (8.3)](#ch08.xhtml#eqn8_3). Specifically, for LASSO, [Equation (8.3)](#ch08.xhtml#eqn8_3) reduces to

$\\min\\limits\_{\\mathbf{\\beta}}\\left\\| {\\mathbf{y} - \\mathbf{X}\\mathbf{\\beta}} \\right\\|\_{2}^{2} + \\sum\\limits\_{i = 1}^{p}{\\lambda\\left| \\beta\_{i} \\right|.}$

|*β*[*i*]| will introduce the so-called “soft shrinkage” while ridge regression will shrink the coefficients proportionally ([Hastie, Tibshirani, and Friedman 2009](#ch08.xhtml#ref8_17)). Many extensions of LASSO have been proposed. For example, the Grouped LASSO is one method that addresses the problem where the covariates belong to predefined groups ([Yuan and Lin 2006](#ch08.xhtml#ref8_45)). The Adaptive LASSO adopts a weighted penalty of the form $\\sum\\limits\_{i = 1}^{p}{\\omega\_{j}\\left| \\beta\_{i} \\right|}$ which has oracle properties, namely consistent estimates of the coefficients and correct recovery of the true model ([Zou 2006](#ch08.xhtml#ref8_48)). The Elastic Net method was motivated by the desire to shrink correlated variables to zero and to achieve this goal, it introduces a flexible penalty function $\\sum\\limits\_{i = 1}^{p}{({\\alpha\\left| \\beta\_{i} \\right| + \\left( {1 - \\alpha} \\right)\\beta\_{i}^{2}})}$ ([Zou 2006](#ch08.xhtml#ref8_48)).

LASSO can also be extended to GLMs, generalized estimating equations, the Cox model, etc. Since many studies use a logistic model with an L1 penalty to do statistical analysis of EHR data, we present the extension of LASSO to the logistic model. In linear regression models, LASSO adds an L1 penalty to the least square function which is a type of loss function. Hence for logistic regression (8.1), once we determine the loss function, combining the L1 regularization with it leads to logistic regression with a LASSO penalty. The loss function for logistic regression is the negative log-likelihood function. The regularization mechanism for logistic regression (8.1) can be described as

$\\min\\limits\_{\\mathbf{\\beta}}{n^{- 1}\\sum\\limits\_{i = 1}^{n}\\left( {\\left. - y\_{i}\\left( \\mathbf{x} \\right.\_{i}^{T}\\mathbf{\\beta} \\right) + \\log⁡\\left( 1 + \\exp⁡\\left( \\mathbf{x}\_{i}^{T}\\mathbf{\\beta} \\right) \\right)} \\right)} + \\sum\\limits\_{i = 1}^{p}{\\lambda\\left| \\beta\_{i} \\right|.}$

If we change the penalty to $\\sum\\limits\_{i = 1}^{p}\\lambda\\left\\| \\beta\_{i} \\right\\|\_{2}^{2}$, the regularization gives ridge regression. This L2 regularization is also widely used in EHR data analysis. Similarly, the Grouped LASSO, the Adaptive LASSO, and the Elastic Net can also be generalized to GLMs. One major price paid for gaining the benefits of using regularization methods is compromising unbiased coefficient estimates for smaller variance. LASSO, unlike GLMs, does not guarantee unbiased estimates for coefficients however, the latter variations of LASSO such as adaptive LASSO address this issue. Readers may refer to ([Hastie, Tibshirani, and Friedman 2009](#ch08.xhtml#ref8_17)) for a further understanding of the LASSO.

## ![image](images/inline1_1.jpg)  
8.9 Divide-and-Conquer Method

All the methods described above are straightforward to apply to big EHR data if we are using well-developed computational packages. However, more complicated approaches such as non-linear models, and joint modes are computationally infeasible for big data. One way to overcome the computational issue is to pair statistical methods with parallel computational approaches and divide and concur methods. In the latter method, the big data is divided, often randomly, to smaller datasets, then the result of any statistical method on all of the methods will be pooled together.

## ![image](images/inline1_1.jpg)  
8.10 Validation

Combining the initial variable screening Iterative SIS with any of the proposed methods above (e.g., stepwise, LASSO, and adaptive LASSO) grants us with multiple models for prediction and identifying risk factors, and each of these models exploits a different mathematical and computational criterion for variable selection. However, it is important to compare and evaluate these different models and methods, so that a final predictive model can be selected and used in practice. In particular, for continuous outcomes, the mean squared error (MSE) is a common measure to evaluate the prediction performance. The formula of MSE is

$\\frac{1}{\\mathbf{n}}\\sum\\limits\_{\\mathbf{i} = 1}^{\\mathbf{n}}{\\left( {\\mathbf{Y}\_{\\mathbf{i}} - \\widehat{\\mathbf{Y}\_{\\mathbf{i}}}} \\right)^{2},}$

where **Y**[**i**] and $\\widehat{\\mathbf{Y}\_{\\mathbf{i}}}$ are observed and predicted responses respectively for the n observations. For binary outcomes, the (AUC) of the (ROC) curve is often used to compare the prediction accuracy of different models, which will be introduced in Section 8.10.1.

Many metrics are used to evaluate the performance of different models. For binary classifications, the AUC is the most commonly used measure. Take the logistic regression as an example: after we fit the model, the estimated coefficients of the model can be plugged into the formula of *π*(**x**[*i*]) (2) to obtain the estimated probability of “success” *π̂*(**x**[*i*]) for a new observation **x**[*i*]. Based on *π̂*(**x**[*i*]), we can classify subject *i* into Group 1 (namely, *ŷ*[*i*] = 1) or Group 0 (namely, *ŷ*[*i*]\=0). For this classification, a threshold value *π*[*T*] is assumed and if *π̂*(**x**[*i*]) is larger or equal to *π*[*T*], *ŷ*[*i*] = 1; Otherwise, *ŷ*[*i*] = 0. For a specific cutoff *π*[*T*], we can calculate sensitivity and specificity. Sensitivity is defined as *P*(*ŷ*\=1|*y*\=1), and specificity is defined as *P*(*ŷ*\=0|*y*\=0). For real data analysis, the proportion of captured positive samples by the positive predictions over the total positive samples is used to replace the true sensitivity probability, which sometimes is also called the true positive rate. The proportion of captured negative samples by the negative predictions over the total negative samples is then to estimate the true specificity probability, which is sometimes called the true negative rate. Here positive samples refer to subjects in Group 1 and negative samples refer to subjects in Group 0. So any value of *π*[*T*] threshold, both sensitivity and 1- specificity can be obtained. For a series of thresholds, we can plot a scatter curve using sensitivity and 1- specificity as the coordinates, as shown in [Figure 8.1](#ch08.xhtml#fig8_1) which is generated from the SAH study in which we used the patient information to predict the mortality status at discharge. The plotted curve is named the ROC. The area under the ROC is the AUC. For a given spe cificity, higher sensitivity means better predictive power. Hence, the bigger area under the ROC indicates the better predictive performance of the model.

![Figure 8.1 AUC of ROC in a SAH study to predict death.](images/fig8_1.jpg)

**Figure 8.1**  
AUC of ROC in a SAH study to predict death.

## ![image](images/inline1_1.jpg)  
8.11 Results and Examples

Here we use our SAH study as illustrations for logistic and multinomial logistic regression, stepwise, and LASSO. In one project of this study, we examined the first vasopressor administered to 4810 eligible SAH patients ([Williams et al. 2020](#ch08.xhtml#ref8_40)). Using an intention-to-treat approach, patients were grouped into specific treatment groups (either dopamine, phenylephrine or norepinephrine) based on the initial vasopressor received, regardless of whether they subsequently received a different vasopressor. The predictors include age, race, marital status, gender, 750 medications (generic names) administered before the vasopressor treatment, Charlson comorbidity index (CCI), and total IV-fluid administered throughout the encounter. The outcome is in-hospital mortality, which was defined as in-hospital death or discharge to hospice care.

Due to a large number of predictors, we implemented LASSO and stepwise separately to reduce the dimension of covariates and then the logistic regression. See [Table 8.5](#ch08.xhtml#table8_5) for the results.

**Table 8.5** OR between Different Vasopressors Using Dimension Reduction Methods and Logistic Regression Jointly

| **Methods**  ||  || **OR** |
| --- | --- | --- |
|  || **Dopamine vs. Phenylephrine** || **Dopamine vs. Norepinephrine** |
| LASSO + Logistic Regression || 2.00 (<0.001) || 0.86 (0.16) |
| --- | --- | --- |
| Stepwise + Logistic Regression || 1.98 (<0.001) || 0.86 (0.14) |

In another project of our SAH study, we aimed to predict the risk of mortality for non-traumatic SAH patients using information from the first 24&#160;hours after hospital admissions. The information contains baseline demographic variables, time-stamped medication records, and procedures in the model development process. Finally, a total of 816 patients are included and they are split into train data set and test data set. L1-regularized logistic regression (LASSO) was chosen to predict the risk of mortality due to its property of interpretability. We achieved AUC at 0.84. Altogether, 17 out of 113 variables were included in the prediction model with only the first 24&#160;hours EHR data, 2 increased the risk of mortality, and 15 protected from death, see [Figure 8.2](#ch08.xhtml#fig8_2).

![Figure 8.2 The predictors that were included in the model for predicting mortality with the first 24&#160;hours’ EHR data, and corresponding odds ratios.](images/fig8_2.jpg)

**Figure 8.2**  
The predictors that were included in the model for predicting mortality with the first 24&#160;hours’ EHR data, and corresponding odds ratios.

## ![image](images/inline1_1.jpg)  
8.12 Discussions and Conclusions

In this chapter, we reviewed common statistical methods that can be applied to EHR data and discussed the challenges and irregularities in EHR data which make the application of more sophisticated models subtle. For all the models, variable selection and validation methods were included in this chapter, and there are fast and efficient computational packages available, which made EHR analysis possible even for scientists without professional training in statistics. The examples provided in this section are the brief results of two papers based on EHR datasets extracted from Cerner. One investigating the effect of vasopressor on in-hospital mortality of SAH patients, and the other predicting in-hospital death using patients’ clinical records, validating our proposal that common statistical models are often sufficient for EHR data analysis.

Nevertheless, there are still big opportunities to develop new methodologies, because EHR datasets have many unique potentials and unique challenges required to be addressed.

### References

Agresti, Alan. 1996. *An Introduction to Categorical Data Analysis*. New York: Wiley.

Backenroth, Daniel, Herbert S. Chase, Ying Wei, and Carol Friedman. 2017. Monitoring prescribing patterns using regression and electronic health records. *BMC Medical Informatics and Decision Making* **17** ((1)):175. [https://doi.org/10.1186/s12911-017-0575-5](https://doi.org/10.1186/s12911-017-0575-5).

 Behrens, John T. 1997. Principles and procedures of exploratory data analysis. *Psychological Methods*, **no. 2**: 131–160.

Cai, Tianxi, Tony Cai, and Zijian Guo. 2019. Individualized treatment selection: An optimal hypothesis testing approach in high-dimensional models. [http://arxiv.org/abs/1904.12891](http://arxiv.org).

Chen, Xueying, and Min Ge Xie. 2014. A split-and-conquer approach for analysis of extraordinarily large data. *Statistica Sinica* **24** ((4)): 1655–1684. [https://doi.org/10.5705/ss.2013.088](https://doi.org/10.5705/ss.2013.088).

Cheng, Li-Fang, Gregory Darnell, Bianca Dumitrascu, Corey Chivers, Michael E Draugelis, Kai Li, and Barbara E Engelhardt. 2020. Sparse multi-output Gaussian processes for online medical time series prediction. *BMC Medical Informatics and Decision Making* 20 (152).

Dempsey, Walter, and Peter McCullagh. 2018. Survival models and health sequences. *Lifetime Data Analysis* **24** ((4)): 550–584. [https://doi.org/10.1007/s10985-018-9424-9](https://doi.org/10.1007/s10985-018-9424-9).

Diggle, Peter., Ptrick Heagerty, Kung-Yee Liang, and Scott L. Zeger. 2002. *Analysis of Longitudinal Data*. New York: Oxford University Press.

Fan, Jianqing, and Runze Li. 2001. Variable selection via nonconcave penalized likelihood and its oracle properties. *Journal of the American Statistical Association*. **96** ((456)): 1348–1360.

Fan, Jianqing, and Jinchi Lv. 2007. Sure independence screening for ultra-high dimensional feature space \*." Journal of the Royal Statistical Society 70(5):849–911.

Garcia, Tanya P, and Karen Marder. 2017. Neurodegenerative diseases: Huntington’ s disease as a model. *Current Neurology and Neuroscience Reports* **17** ((2)): 1–14. [https://doi.org/10.1007/s11910-017-0723-4.Statistical](https://doi.org/10.1007/s11910-017-0723-4.Statistical).

Gasparini, Alessandro, Keith R. Abrams, Jessica K. Barrett, Rupert W. Major, Michael J. Sweeting, Nigel J. Brunskill, and Michael J. Crowther. 2020. Mixed-effects models for health care longitudinal data with an informative visiting process: A Monte Carlo simulation study. *Statistica Neerlandica* **74** ((1)): 5–23. [https://doi.org/10.1111/stan.12188](https://doi.org/10.1111/stan.12188).

Goldstein, Benjamin A., Ann Marie Navar, Michael J. Pencina, and John P.A. Ioannidis. 2017. Opportunities and challenges in developing risk prediction models with electronic health records data: A systematic review. *Journal of the American Medical Informatics Association* **24** ((1)): 198–208. [https://doi.org/10.1093/jamia/ocw042](https://doi.org/10.1093/jamia/ocw042).

Goldstein, Harvey, P. J. Diggle, K.-Y. Liang, and S. L. Zeger. 1995. Analysis of longitudinal data. *Journal of the Royal Statistical Society. Series A (Statistics in Society)* **158** ((2)): 345. [https://doi.org/10.2307/2983303](https://doi.org/10.2307/2983303).

Grolemund, Hadley Wickham. Garrett. 2016. *R for Data Science*. O’Reilly Media, Inc.

Hagar, Yolanda, David Albers, Rimma Pivovarov, Herbert Chase, Vanja Dukic, and Noémie Elhadad. 2014. Survival analysis with electronic health record data: Experiments with chronic kidney disease. *Statistical Analysis and Data Mining* **7** ((5)): 385–403. [https://doi.org/10.1002/sam.11236](https://doi.org/10.1002/sam.11236).

Hastie, Trevor, Robert Tibshirani, and Jerome Friedman. 2009. *The Elements of Statistical LearningData Mining, Inference, and Prediction, Second Edition*. New York: Springer. [https://doi.org/10.1007/978-0-387-84858-7](https://doi.org/10.1007/978-0-387-84858-7).

Hoerl, Arthur E., and Robert W. Kennard. 1970. Ridge regression: Biased estimation for nonorthogonal problems. *Technometrics* **12** ((1)): 55–67. [https://doi.org/10.1080/00401706.1970.10488634](https://doi.org/10.1080/00401706.1970.10488634).

 Hosmer, David W., and Stanley Lemeshow. 2000. *Applied Logistic Regression.* Hoboken, NJ, USA: John Wiley and Sons, Inc. [https://doi.org/10.1002/0471722146](https://doi.org/10.1002/0471722146).

Hripcsak, George, David J. Albers, and Adler Perotte. 2011. "Exploiting time in electronic health record correlations. *Journal of the American Medical Informatics Association* **18** ((SUPPL. 1)): 109–115. [https://doi.org/10.1136/amiajnl-2011-000463](https://doi.org/10.1136/amiajnl-2011-000463).

Levine, Matthew E., David J. Albers, and George Hripcsak. 2016. Comparing lagged linear correlation, lagged regression, granger causality, and vector autoregression for uncovering associations in EHR data. *AMIA… Annual Symposium Proceedings. AMIA Symposium* **2016**: 779–788.

Levine, Matthew E., David J. Albers, and George Hripcsak. 2018. Methodological variations in lagged regression for detecting physiologic drug effects in EHR data. *Journal of Biomedical Informatics* **86** ((August)): 49–159. [https://doi.org/10.1016/j.jbi.2018.08.014](https://doi.org/10.1016/j.jbi.2018.08.014).

Maziarz, Marlena, Patrick Heagerty, Tianxi Cai, and Yingye Zheng. 2017. On longitudinal prediction with time-to-event outcome: Comparison of modeling options. *Biometrics* **73** ((1)): 83–93. [https://doi.org/10.1111/biom.12562](https://doi.org/10.1111/biom.12562).

Mosteller, Frederick, and John Wilder Tukey. 1977. *Data Analysis and Regression: A Second Course in Statistics*. Reading, Mass, Addison-Wesley Pub. Co.

Paige, Ellie, Jessica Barrett, David Stevens, Ruth H. Keogh, Michael J. Sweeting, Irwin Nazareth, Irene Petersen, and Angela M. Wood. 2018. Landmark models for optimizing the use of repeated measurements of risk factors in electronic health records to predict future disease risk. *American Journal of Epidemiology* **187** ((7)): 1530–1538. [https://doi.org/10.1093/aje/kwy018](https://doi.org/10.1093/aje/kwy018).

Pimentel, MAF, DA Clifton, L Clifton, and Lionel Tarassenko. 2013. Modelling patient time-series data from electronic health records using Gaussian processes. *Advances in Neural Information Processing Systems: Workshop on Machine Learning for Clinical Data Analysis*, 1–4.

Pimentel, Marco, David Clifton, Lei Clifton, and Lionel Tarassenko. 2013. Modelling patient time-series data from electronic health records using gaussian processes. [http://www.robots.ox.ac.uk/](http://www.robots.ox.ac.uk).

Ranganath, Rajesh, Adler Perotte, Noémie Elhadad, and David Blei. 2016. Deep survival analysis Proceedings of Machine Learning for Healthcare. JMLR W&C Track Volume 56.

Ranganath, Rajesh, Adler Perotte, Noémie Elhadad, and David M. Blei. 2015. The survival filter: Joint survival analysis with a latent time series. *Uncertainty in Artificial Intelligence - Proceedings of the 31st Conference, UAI 2015*, 742–751.

Rasmussen, Carl Edward, and Christopher K. I Williams. 2005. *Gaussian Processes for Machine Learning*. Cambridge, MA, USA:The MIT Press.

Rhodes, K. M., R. M. Turner, R. A. Payne, and I. R. White. 2018. Computationally efficient methods for fitting mixed models to electronic health records data. *Statistics in Medicine* **37** ((29)): 4557–4570. [https://doi.org/10.1002/sim.7944](https://doi.org/10.1002/sim.7944).

Shortreed, Susan M., and Ashkan Ertefaie. 2017. Outcome-adaptive LASSO: Variable selection for causal inference. *Biometrics* **73** ((4)): 111–1122. [https://doi.org/10.1111/biom.12679](https://doi.org/10.1111/biom.12679).

Singh, Anima, Girish Nadkarni, Omri Gottesman, Stephen B. Ellis, Erwin P. Bottinger, and John V. Guttag. 2015. Incorporating temporal EHR data in predictive models for risk stratification of renal function deterioration. *Journal of Biomedical Informatics* **53** ((February)): 220–228. [https://doi.org/10.1016/j.jbi.2014.11.005](https://doi.org/10.1016/j.jbi.2014.11.005).

 Stein, Joshua D., Moshiur Rahman, Chris Andrews, Joshua R. Ehrlich, Shivani Kamat, Manjool Shah, Erin A. Boese, *et al* 2019. Evaluation of an algorithm for identifying ocular conditions in electronic health record data. " *JAMA Ophthalmology* **137** ((5)): 491–497. [https://doi.org/10.1001/jamaophthalmol.2018.7051](https://doi.org/10.1001/jamaophthalmol.2018.7051).

Tibshirani, Robert. 1996. Regression shrinkage and selection via the LASSO. *Journal of the Royal Statistical Society: Series B (Methodological)* **58** ((1)): 267–288. [https://doi.org/10.1111/j.2517-6161.1996.tb02080.x](https://doi.org/10.1111/j.2517-6161.1996.tb02080.x).

Tsay, Ruey S. 2010. *Analysis of Financial Time Series*. 3rd edn ed. Hoboken N.J: Wiley-Interscience.

Tukey., John W. 1977. *Exploratory Data Analysis*. Reading, Mass: Addison-Wesley.

Velleman, Paul, and David Hoaglin. 1981. *The ABC’s of EDA: Applications, Basics, and Computing of Exploratory Data Analysis*. Duxbury.

Vinzamuri, Bhanukiran, and Chandan K. Reddy. 2013. Cox regression with correlation based regularization for electronic health records. *Proceedings - IEEE International Conference on Data Mining, ICDM*, 757–766. [https://doi.org/10.1109/ICDM.2013.89](https://doi.org/10.1109/ICDM.2013.89).

Williams, George, Vahed Maroufy, Laila Rasmy, Derek Brown, Duo Yu, Hai Zhu, Yashar Talebi, *et al* 2020. Vasopressor treatment and mortality following non-traumatic subarachnoid hemorrhage: A nationwide EHR analysis. *Neurosurgical Focus* 48 (5):E4

Wu, Hulin., and Jin-Ting Zhang. 2006. *Nonparametric Regression Methods for Longitudinal Data Analysis: Mixed-Effects Modeling Approaches*. Hoboken N.J: WileyWiley-Interscience.

Wu, Qian, Weiling Zhao, Xiaobo Yaang, Hua Tan, Lei You, Hua Xu, Yujia Zhou, and Xiaobo Zhou. 2018. Assessment of the risk factors of MDD recurrence using machine learning and deep learning approaches. *SSRN Electronic Journal*, November. [https://doi.org/10.2139/ssrn.3294125](https://doi.org/10.2139/ssrn.3294125).

Wu, Yirong, Elizabeth S. Burnside, Jennifer Cox, Jun Fan, Ming Yuan, Jie Yin, Peggy Peissig, Alexander Cobian, David Page, and Mark Craven. 2017. Breast cancer risk prediction using electronic health records. *Proceedings - 2017 IEEE International Conference on Healthcare Informatics, ICHI 2017*, 224–228. [https://doi.org/10.1109/ICHI.2017.62](https://doi.org/10.1109/ICHI.2017.62).

Wu, Yonghui, Jeremy L. Warner, Liwei Wang, Min Jiang, Jun Xu, Qingxia Chen, Hui Nian, *et al* 2019. Discovery of noncancer drug effects on survival in electronic health records of patients with cancer: A new paradigm for drug repurposing. *JCO Clinical Cancer Informatics*, **no. 3**: 1–9. [https://doi.org/10.1200/cci.19.00001](https://doi.org/10.1200/cci.19.00001).

Yuan, Ming, and Yi Lin. 2006. Model selection and estimation in regression with grouped variables. *Journal of the Royal Statistical Society: Series B* **68 , no. 1: 49–67**.

Zhang, Cun-Hui. 2010. Nearly unbiased variable selection under minimax concave penalty. *The Annals of Statistics* **38** ((2)): 894–942. [https://doi.org/10.1214/09-AOS729](https://doi.org/10.1214/09-AOS729).

Zhang, Zhongheng, and Yucai Hong. 2017. Development of a novel score for the prediction of hospital mortality in patients with severe sepsis: The use of electronic healthcare records with LASSO regression. *Oncotarget* **8** ((30)): 49637–49645. [https://doi.org/10.18632/oncotarget.17870](https://doi.org/10.18632/oncotarget.17870).

Zou, Hui. 2006. The adaptive LASSO and its oracle properties. *Journal of the American Statistical Association* **101** ((476)): 1418–1429. [https://doi.org/10.1198/016214506000000735](https://doi.org/10.1198/016214506000000735).

# [9 ](#contents.xhtml#toc1_204)  
![image](images/inline1_1.jpg)

# [Neural Network and Deep Learning Methods for EHR Data](#contents.xhtml)  
               

Duo Ashraf Xi YuYaseenLuo

This chapter reviews the recent and emerging literature on deep learning methods in EHR data analysis. It covers a select list of methods related to structural data and discusses their advantages and disadvantages in various application scenarios and research goals. Two examples and scripts are employed to illustrate our applications of deep learning techniques for analyzing EHR data.

## ![image](images/inline1_1.jpg)  
9.1 Introduction

Deep learning (DL) is a class of machine learning modeling techniques that employs several hierarchical layers of artificial neurons forming a network, often referred to as an artificial neural network (ANN), to learn the complex “rules” between inputs and outputs. The number of layers can range from a few to several folds larger, resulting in a deeply connected neural network. Thus, such models are referred to as deep learning. The history of deep learning can be found in many resources online or in journal articles. Examples of recent reviews include publications by leading researchers in this field ([LeCun, Bengio, and Hinton 2015](#ch09.xhtml#ref9_14), [Hinton 2018](#ch09.xhtml#ref9_11), [Esteva et al. 2019](#ch09.xhtml#ref9_6)). This chapter will first present a light overview of DL before shifting the focus to the applications of DL in some aspects of EHR data analysis related to our own applications. Please see ([Shickel et al. 2018](#ch09.xhtml#ref9_23), [Miotto et al. 2018](#ch09.xhtml#ref9_18)) for more detailed and comprehensive reviews of DL in EHR analysis.

The types of DL model structures have evolved rapidly in the past few years. Though there are an exploding number of types being added to literature, the basic underlying model structure can be characterized in [Figure 9.1](#ch09.xhtml#fig9_1) as follows.

![Figure 9.1 Artificial neural network model with a single hidden layer.](images/fig9_1.jpg)

**Figure 9.1**  
Artificial neural network model with a single hidden layer.

As shown in the figure example, we use four input variables (shown in light gray), say *x*[1] to *x*[4], to predict a single output variable *y* (gray). The prediction is achieved in two steps. First, four input variables are mapped to a hidden layer of five hidden variables (dark gray), say *z*[1] to *z*[5], using the following linear function:

*z* = *σ*(*w*[*z*]*x*+*θ*[*z*])

where *x* and *z* are vectors, *w*[*z*] is the weight matrix, and *θ*[*z*] is a vector of intercepts.

*σ*(⋅) represents an activation function that can take various forms, including linear, sigmoid, or hyperbolic tangent (tanh) functions. The sigmoid function is defined as

$\\sigma(x) = sig(x) = \\frac{1}{1 + e^{- x}}.$

and the hyperbolic tangent function is defined as

$\\sigma(x) = \\tanh(x) = \\frac{e^{2x} - 1}{e^{2x} + 1}.$

Finally, in the last layer, these hidden variables are mapped to a single output variable *y* using a similar form as

*y* = *σ*(*w*[*y*]*z* + *θ*[*y*]).

There is no restriction on choosing the same activation function across layers, though typically they are chosen to be the same, except in the last layer where the activation function is chosen to be compatible with the outcome. A multilayer perceptron (MLP) is a class of feedforward artificial neural network (ANN) which utilizes a supervised learning technique called backpropagation for training. Its multiple layers and non-linear activation distinguish MLP from a linear perceptron. An MLP usually contains more hidden layers than one single hidden layer shown in [Figure 9.1](#ch09.xhtml#fig9_1). An advantage of choosing non-linear activation functions is to allow MLP to capture non-linear relationships between the input and output. More choices of activation functions will be discussed later. An example on how to implement MLPs will also be presented later.

In general, DL approaches can be divided into three categories depending on their goals:

 

1.  *supervised learning* aims to find patterns in a set of predictors that forecast outcome variables accurately. Examples include recognizing numbers/texts from images, predicting patient diagnoses, and treatment outcomes. DL techniques in this category achieve the same goal as other classical machine learning techniques, such as logistic regression and random forests.
    
2.  *reinforcement learning* employs computer-based agents to carry out certain tasks in repeated trials with rewards and penalties until computer algorithms perform the tasks well. A prominent example is probably AlphaGo, a DL based algorithm that has beaten top human GO masters ([Silver et al. 2016](#ch09.xhtml#ref9_24)).
    
3.  *unsupervised learning* aims to search for important patterns in a set of variables without a direct goal to forecast outcomes stored in other variables. The “learned” patterns can also be fed into supervised learning algorithms. This is considered an area that still needs more future development.
    

 

In the analysis of EHR data, the first category is probably the most developed as in many other DL supervised learning applications, and our example project later will focus on this category. We will also review the advantages and disadvantages of various DL techniques in the next section.

There are several challenges in EHR data analysis that pose, sometimes, lighter burdens on DL techniques than classical machine learning methods.

First, EHR data typically consist of structured (e.g., demographics, diagnosis codes, medications, lab tests) and unstructured data (e.g., doctor’s notes, images), and sometimes the second type can account for the majority volume in terms of storage size. Classical machine learning methods can be effective in modeling the first type of data because they can be effectively computed based on matrix/vector inputs with relatively smaller dimensions. For EHR data with images and texts, DL methods have been well developed with promising results. For example, DL was applied to classifying clinical notes ([Weng et al. 2017](#ch09.xhtml#ref9_26)) and analyzing medical images ([Lundervold and Lundervold 2019](#ch09.xhtml#ref9_16), [Suzuki 2017](#ch09.xhtml#ref9_25), [Lee et al. 2017](#ch09.xhtml#ref9_15)).

Second, EHR data contain a huge collection of variables captured by hospital EMR systems. The number of variables to be analyzed could be further increased if considered in conjunction with time variables or medical encounters. Such variables are heterogeneous in nature, including binary, categorical and continuous variables in demographics or encounter tables, diagnosis tables, medication tables, and lab test tables. Classical approaches would require domain experts and statisticians to work together to design and extract important features based on raw EHR data, for example, blood pressure increases or decreases on sequential visits. This step is sometimes called feature engineering in classical machine learning domains. However, due to the complexity of EHR data, this task can be daunting and time-consuming, not to mention that experts can overlook many complex patterns buried in tons of medical encounters. On the other hand, DL can learn useful features from data directly, sometimes surpassing existing features using state-of-the-art machine learning prediction algorithms ([LeCun, Bengio, and Hinton 2015](#ch09.xhtml#ref9_14)).

Third, the EHR data collected from an individual patient are sparse in time and variables. For example, a patient can have no medical encounters for months and then several encounters in a week. Taking the diagnosis outcome as another example, one patient can have only a few ICD diagnosis codes out of thousands in one encounter. These characteristics make EHR unique from traditional study designs where limited pre-defined variables are measured at roughly regular time intervals (at least for predictors). One existing DL technique to handle this challenge is to embed these sparse coded data in a common space that yields promising results ([Rajkomar et al. 2018](#ch09.xhtml#ref9_21)).

Fourth, it is conceivable that there might be complex temporal dependence in medical encounters, because earlier life health (even in childhood) can have long-lasting effects on later life health ([Bijker and Agyemang 2016](#ch09.xhtml#ref9_2)). With this in mind, constructing classical machine learning algorithms with a long-term dependency could be challenging and hard to tune, while several DL techniques have already been developed for modeling long or short-term temporal dependencies ([Hochreiter and Schmidhuber 1997](#ch09.xhtml#ref9_12), [Chung et al. 2014](#ch09.xhtml#ref9_5)).

Last, EHR is primarily designed for billing and management purposes, and sometimes the detailed medical information (e.g., blood testing results) can be missing or error-prone. DL methods, specially designed with robust modeling techniques (e.g., dropouts), can be less sensitive to these issues than classical methods. One positive implication of deploying DL is that researchers may not need to spend a lot of time cleaning and correcting EHR data, and such efforts can represent the overwhelming majority of the efforts in EHR research.

In the meantime, there are also several limitations of DL methods. One big issue is its limited interpretability. Despite its success in superior prediction performance, DL models may still lack the power to unravel the mechanisms. Some progress has been made to address this challenge, for example ([Choi et al. 2016](#ch09.xhtml#ref9_4)). Another issue is related to model training, wherein one needs to be careful about overfitting and proper choices of model structures and hyper-parameters. Sometimes, good choices come from empirical trial-and-error techniques and experiences. To deal with overfitting, one may also need to resort to training on fairly large data with carefully crafted models.

The remainder of this chapter is organized as follows. We will review existing DL methods for EHR data analysis and describe our DL applications in two examples. Due to the focus of our applications, we will limit our review to those structured data and leave out other applications on non-structured data (e.g., clinical notes) and laboratory measures (e.g., CT, MRI). We will end the chapter with discussions and future directions.

## ![image](images/inline1_1.jpg)  
9.2 Deep Learning Methods for EHR Data

DL techniques can be characterized according to their network structures. We will briefly explain a few common DL network structures and present some successful applications.

The basic type of DL model is the multiple layer perceptron (MLP) ([Hastie, Tibshirani, and Friedman 2001](#ch09.xhtml#ref9_10)), which was popular in the 1980s. As the name suggests, it consists of multiple layers of artificial neurons such that the input passes forward through the layers. MLP is usually used for predictions, see ([Shickel et al. 2018](#ch09.xhtml#ref9_23)) for MLP applications in EHR.

The first modern DL method is probably deep convolutional networks (CNN) ([LeCun, Bengio, and Hinton 2015](#ch09.xhtml#ref9_14)). CNN usually employs convolutional layers on input data such that the correlations between neighboring inputs are accounted for in the model, and the data dimension is further reduced by pooling layers such that the output is robust against location shifts in inputs. Applications of CNN include predictions of disease risks ([Goldstein, Navar, and Pencina 2016](#ch09.xhtml#ref9_7)), diagnosis ([Haenssle et al. 2018](#ch09.xhtml#ref9_9)), and readmissions ([Nguyen et al. 2017](#ch09.xhtml#ref9_20)). A CNN model can also be applied in disease prediction by semantic understanding of EHR texts, [Figure 9.2](#ch09.xhtml#fig9_2).

![Figure 9.2 A CNN architecture that was used for diseases prediction.](images/fig9_2.jpg)

**Figure 9.2**  
A CNN architecture that was used for diseases prediction.

To deal with temporal inputs, recurrent neural network (RNN) was developed to learn from sequential inputs, usually collected at different time points. To adapt to possible long or short temporal dependence of inputs, long short-term memory (LSTM) ([Hochreiter and Schmidhuber 1997](#ch09.xhtml#ref9_12)) and Gated Recurrent Unit (GRU) ([Chung et al. 2014](#ch09.xhtml#ref9_5)) were developed to allow automatic “memory”-like capability of linking the past and current inputs together ([Figure 9.3](#ch09.xhtml#fig9_3)). Example applications of RNN include predicting disease onsets ([Rasmy et al. 2018](#ch09.xhtml#ref9_22), [Maragatham and Devi 2019](#ch09.xhtml#ref9_17)) and readmissions ([Rajkomar et al. 2018](#ch09.xhtml#ref9_21)). Some GRUs ([Che et al. 2018](#ch09.xhtml#ref9_3)) also addressed missing values in EHR time series data.

![Figure 9.3 Basic architectures of RNN, GRU and LSTM.](images/fig9_3.jpg)

**Figure 9.3**  
Basic architectures of RNN, GRU and LSTM.

Another exciting technique in DL is probably generative adversarial networks (GAN). This technique trains two competing neural networks together. One network (generator) aims to simulate as genuine as possible to real data, while the other (discriminator) aims to distinguish simulated and real data points. The applications of GAN in EHR include synthesizing data ([Baowaly et al. 2019](#ch09.xhtml#ref9_1)) and disease predictions ([Hwang, Choi, and Yoon 2017](#ch09.xhtml#ref9_13)) ([Figure 9.4](#ch09.xhtml#fig9_4)).

![Figure 9.4 A basic Generative Adversarial Network (GAN) framework.](images/fig9_4.jpg)

**Figure 9.4**  
A basic Generative Adversarial Network (GAN) framework.

Choosing DL architectures should depend on the data and modeling goals, different architectures have their own advantages and disadvantages. CNN is helpful for handling spatial and temporal dependence of data, and thus it is a natural choice for images and texts where such dependence is strong. In general, CNN training is fast but it also is restricted to local dependence structures. RNN is good for handling long-range and short-range dependencies. It enables better modeling of long time series with complex dependencies, though computationally it is slower to converge. GAN incorporates two sub-architectures (generator and discriminator) in one framework, and thus choosing GAN may allow users to accomplish more tasks than predictions. For the sub-architectures, CNN, RNN, or others can be employed. In general, however, GAN is much harder to train, and sub-optimal constructs and implementations may lead to poor performance in simulations and predictions partly due to failed convergence. We recommend that users choose the DL architecture based on their goals, complexity of data structures (e.g., dependencies), computational infrastructure, data size, and experience with DL training.

## ![image](images/inline1_1.jpg)  
9.3 Deep Learning Software Tools and Implementation

Many software tools for constructing and implementing DL networks are now widely available and often open-sourced. Some popular packages include TensorFlow, Torch/Pytorch, CNTK, Keras, Caffe (2), Theano, MXNet, and H2O. Usually, these packages are being continuously refined over time as they are also being used in many large high-tech companies. There are plenty of tutorials available online or in books. For example, TensorFlow provides online tutorials ([https://www.tensorflow.org/tutorials](https://www.tensorflow.org)) for users at different levels. These definitely make it possible to quickly develop new DL algorithms for EHR data analysis and predictions.

Based on our own experience, we find that the python packages, TensorFlow and Pytorch, are good choices for EHR data analysis. The most recent version of TensorFlow also includes Keras. Both pros and cons of these two software tools are summarized as follows:

*   TensorFlow is continuously being developed by Google with contributions from the community. It is a mature framework with much community support and can be deployed for production across different platforms (e.g., mobile, servers).
    
    *   Pros: mature, easy-to-use (especially based on integrated Keras in TensorFlow 2), large community support, easy deployment, production-ready, visualization interface (Tensor Board)
        
    *   Cons: less pythonic (especially using basic TensorFlow without Keras), not backward compatible (TensorFlow 2 versus 1, though conversion scripts available), hard-to-install on certain OS platforms with GPU support
        
*   Pytorch development is led by Facebook and with community contributions.
    
    *   Pros: mature, easy to learn (mostly just like regular python codes and thus pythonic), easy to install, easy to debug, more detailed control
        
    *   Cons: more coding effort (if not using Keras), varying speed depending on customizations
        

## ![image](images/inline1_1.jpg)  
9.4 Application Examples

### Case Study 1: Application of MLP for Mortality Prediction

We illustrate deep learning techniques using the application example of the subarachnoid hemorrhage (SAH) project as described in previous chapters. In this application, we aim to explore the performance of MLP for predicting mortality. Mortality here is defined as death in the next 24&#160;hours. The predictors include demographics, first vasopressor use, medication, procedure, baseline diagnosis, all aggregated from an observational time window on and before admission. In this example, the MLP model was implemented in R using the H2O package, and the model parameters were tuned using the Auto-ML platform built in H2O. The tuning parameters include activation function, number of hidden layers, number of epochs, number of neurons, learning rate, dropout rate, and so on.

First step, we need to import the training and testing data sets into R and check the dimension of each data set:

![image](images/inline9_1.jpg)

We then start to use H2O package in R:

![image](images/inline9_2.jpg)

The original data are stored using R data.frame. To implement the MLP in H2O, we further transform the training and testing data sets into H2OFrame, and then label the outcome and predictors respectively:

![image](images/inline9_3.jpg)

After cleaning and preprocessing the data (see [Chapters 4](#ch04.xhtml#chapter4) and [5](#ch05.xhtml#chapter5) for more details), we have 3956 patients with 1475 predictors extracted from our EHR database. A one-hidden layer neural network model was selected by Auto-ML, and the AUC was 0.94 (95% CI: 0.92–0.95) for the testing data set. The R code for implementation and corresponding results are shown below:

![image](images/inline9_4.jpg)

### Case Study 2: Application of RNN for Heart Failure Prediction for Hypertension Patients

For patients with chronic diseases, EHR data with multiple encounters and long-term follow up are available. RNN is then a good choice of ANN models to take advantage of the rich information coded in longitudinal encounters. However, we should point out that it is not straightforward to apply classical longitudinal models (e.g., mixed-effects regression models), because the outcome variables and predictors were measured at irregular times and the time intervals can be informative of the outcome as well. In this example, we present a project of predicting heart failure (HF) with recurrent neural network (RNN) model.

#### Experimental Setting

The aim of this study is to combine dynamic variables (variables from diagnosis, medication, procedure, lab test procedure and surgical procedure tables) and static predictors (e.g., age, gender, race, number of visits, time span and visit density) to predict HF onset for hypertension patients. The inclusion criteria of patients in this study are: patients who were diagnosed as unspecified essential hypertension, i.e., at least one of the following ICD-9 codes: “401”, “401.0”, “401.1”, “401.9”. To save computation time, we randomly sampled 40,000 hypertension patients for modeling and prediction of HF onset in this illustration example.

Definition of Heart Failure Cases: The criteria for HF onset was adopted from previous HF prediction studies ([Gurwitz et al. 2013](#ch09.xhtml#ref9_8), [Ng et al. 2016](#ch09.xhtml#ref9_19), Choi et al.). To confirm an HF case of a patient, the HF-related ICD-9 codes should appear at three or more clinical visits within 12 months in the patient’s records. The date that the first HF related ICD-9 codes appeared was set to be the onset date of HF for this patient.

Definition of Heart Failure Controls: The hypertension patients who satisfied inclusion criteria, but were not classified as HF cases.

We used Python to process and prepare the EHR data for this project, and we label each patient either an HF case or a control first using the following code:

![image](images/inline9_5.jpg)

We define the observation window and prediction window as follows: Observation Window: From the first diagnosis time of unspecified essential hypertension to the time of the last visit before HF onset visit (for HF patients) or the last second visit in records (for control patients), see [Figure 9.5](#ch09.xhtml#fig9_5).

![Figure 9.5 The observation and prediction windows for HF cases and controls.](images/fig9_5.jpg)

**Figure 9.5**  
The observation and prediction windows for HF cases and controls.

Prediction Window: Time interval between the end of the observation window and next visit.

The unique identifier of patients in the EHR database, “patientSK”, was used to merge all the variables including discharge date, age, diagnosis, medication, race, heart\_failure, HF\_time, sex, marital\_status, procedure, surgical procedure, and lab test procedure into one data frame. Each patient in this data frame has multiple rows (one row for each encounter). This data frame is referred to as *long\_version8.* To prepare the data for predictions, we remove all the data before the first diagnosis of hypertension. The hypertension diagnosis ICD-9 codes are 401, 401.0, 401.1, 401.9.

![image](images/inline9_6.jpg)

Since we intend to use historical EHR data to predict the future HF onset in this project, the patients with only one visit of records are dropped from the cohort. To do this, we ran the following Python codes:

![image](images/inline9_7.jpg)

We also removed the data after heart failure diagnosis, which is defined as the HF cases. Python code for this is shown below:

![image](images/inline9_8.jpg)

Based on the inclusion criteria and definition of HF cases, we identified 1827 HF cases (4.57%) among 40,000 hypertension patients. Various variables and factors were extracted for different EHR data tables. We extracted discharge time, age, gender, race, and marital status from the encounter table, diagnosis codes and diagnosis identifiers from the diagnosis table, medication codes and medication identifiers from the medication table, procedure identifiers from the procedure table, lab procedure identifiers from the lab procedure table, and surgical procedure identifiers from the surgical procedure table. [Table 9.1](#ch09.xhtml#table9_1) lists the types of variables included in our model.

**Table 9.1** Predictor Variables and Corresponding Data Types

| **Variables** || **Type** |
| --- | --- |
| Age || Continuous, Longitudinal |
| --- | --- |
| Gender || Binary, Cross-Sectional |
| Race || Categorical, Cross-Sectional |
| Marital Status || Categorical, Longitudinal |
| Number of Visits || Integral, Cross-Sectional |
| Time Span || Continuous, Cross-Sectional |
| Average Duration between Visits || Continuous, Cross-Sectional |
| Diagnosis Identifiers || Binary, Longitudinal |
| Medication Identifiers || Binary, Longitudinal |
| Lab Test Identifiers || Binary, Longitudinal |
| Procedure Identifiers || Binary, Longitudinal |
| Surgical Procedure Identifiers || Binary, Longitudinal |

Data from different data tables were linked together using the unique patient ID, longitudinal variables were also further coded with the time of corresponding discharge date. After data cleaning and pre-processing, 29441 patients, including 953 HF cases, were included for final data analysis and modeling. The summary statistics of the prediction window were shown in [Table 9.2](#ch09.xhtml#table9_2). Some patients’ prediction window is small (only one day) and some patients’ prediction window is as large as 4453 days with a median of 63 days and a mean of 185 days. Control patients have a longer prediction window than those of HF patients.

**Table 9.2** The Summary Statistics of Prediction Window (Days) for HF Cases and Controls

| **Statistics (Days)** || **All Patients** || **HF Cases** || **HF Controls** |
| --- | --- | --- | --- |
| Minimum || 1 || 2 || 1 |
| --- | --- | --- | --- |
| Maximum || 4453 || 3164 || 4453 |
| Median || 63 || 41 || 65 |
| Mean || 185 || 143 || 186 |
| Wald Test P-value: **<0.001** ||  ||  ||  |

#### RNN Prediction Results

We trained the RNN model based on the source code from Choi E et al.⁴ The RNN model was referred to as RETAIN which is an interpretable predictive model for healthcare application. Using the ratio of 7:1:2, we randomly divided 29441 patients into training, validation, and test data sets: there were 20609 patients (670 cases) in training data set; 2944 patients (96 cases) in the validation data set, 5888 patients (187 cases) in test data set. We set the mini-batch size as 50 and 100 respectively to train the RNN model. The prediction results from the RNN model are shown in [Table 9.3](#ch09.xhtml#table9_3).

[**Table 9.3** The Prediction Accuracy When the Batch Size was Set as 50 and 100](#ch09.xhtml#table9_3)

| **Mini-Batch Size** || **AUC (%)** || **TP (%)** || **FP (%)** || **Training Time/Epoch (Minutes)** |
| --- | --- | --- | --- | --- |
| 50 || 64.06 || 64.17 || 40.75 || 13 |
| --- | --- | --- | --- | --- |
| 100 || 60.75 || 73.80 || 53.08 || 13 |

The tutorial of RETAIN implementation can be found at [https://github.com/mp2893/retain](https://github.com). In this experiment, we implemented RETAIN to predict HF onset for hypertension patients using EHR data. Before implementing RETAIN, we need to prepare the data in the format required by the input of source code from ([Choi et al. 2016](#ch09.xhtml#ref9_4)). The inputs were required to be Python cPickled list, see the code below:

![image](images/inline9_9.jpg)

The standard command for RETAIN implementation is`python retain.py <visit file> <# codes in the visit file> <label file> <output path>`

In this experiment, we implemented as`python retain.py med_seq.pkl 33704 label.pkl output.txt --time_file duration_seq.pkl --age_file age_seq.pkl --interval_file interval_seq.pkl --visit_file visit_seq.pkl --simple_load --n_epoch 30 --batch_size 50 --embed_finetune 0`

In this application example, it is noticed that RNN prediction model only produced moderate prediction performance. There could be several reasons, one is that the prediction window is quite large, which is not easy to predict HF. Some tuning parameters such as the mini-batch size and other hyper-parameters could be further optimized.

## ![image](images/inline1_1.jpg)  
9.5 Discussion

Our application experiments demonstrated that DL is flexible in handling various types of EHR data for outcome predictions. This flexibility makes DL a promising and powerful tool for analyzing heterogeneous and time-coded data scattered in different EHR data tables. Such a task can be daunting for constructing traditional statistical models, especially in the early stages of EHR research with limited prior insight for guiding traditional statistical or probabilistic model building.

Despite recent rapid progress in DL application in EHR data analysis, there are still several limitations. Limited interpretability of DL models is one major concern for clinical researchers. As such, one may not translate successful DL models into a mechanistic understanding of the science behind it. This further makes DL models less comprehensible among clinicians and may deter its adoption in clinical practice. On the technical side, the reasons for DL successes and failures remain to be investigated. Though software implementation is less cumbersome, thanks to high-level DL packages, DL models are not off-the-shelf packages like classical machine learning methods where users do not need to adjust or tune the parameters and models on a case-by-case bases. Some critical tasks, such as how to choose the optimal model structures and parameters, may still rely on users’ practical experience, intuition, and some mathematical reasoning. Computing efficiency for DL models is another important issue that requires further research.

### ![image](images/inline1_1.jpg)  
References

Baowaly, M. K., C. C. Lin, C. L. Liu, and K. T. Chen. 2019. Synthesizing electronic health records using improved generative adversarial networks. *Journal of the American Medical Informatics Association* **26**((3)): 228–241. doi: [10.1093/jamia/ocy142](http://dx.doi.org/10.1093/jamia/ocy142).

Bijker, R., and C. Agyemang. 2016. The influence of early-life conditions on cardiovascular disease later in life among ethnic minority populations: A systematic review. *Internal and Emergency Medicine* **11**((3)): 341–353. doi: [10.1007/s11739-015-1272-y](http://dx.doi.org/10.1007/s11739-015-1272-y).

Che, Z., S. Purushotham, K. Cho, D. Sontag, and Y. Liu. 2018. Recurrent neural networks for multivariate time series with missing values. *Scientific Reports* **8** ((1)): 6085. doi: [10.1038/s41598-018-24271-9](http://dx.doi.org/10.1038/s41598-018-24271-9).

 Choi, Edward, Mohammad Taha Bahadori, Jimeng Sun, Joshua Kulas, Andy Schuetz, and Walter Stewart. Retain: An interpretable predictive model for healthcare using reverse time attention mechanism. 2016. pp. 3504- –3512

Chung, Junyoung, Caglar Gulcehre, KyungHyun Cho, and Yoshua Bengio. 2014. "Empirical evaluation of gated recurrent neural networks on sequence modeling. *arXiv preprint arXiv:1412.3555*.

Esteva, A., A. Robicquet, B. Ramsundar, V. Kuleshov, M. DePristo, K. Chou, C. Cui, G. Corrado, S. Thrun, and J. Dean. 2019. A guide to deep learning in healthcare. *Nature Medicine* **25**((1)): 24–29. doi: [10.1038/s41591-018-0316-z](http://dx.doi.org/10.1038/s41591-018-0316-z).

Goldstein, B. A., A. M. Navar, and M. J. Pencina. 2016. Risk Prediction With Electronic Health Records: The importance of model validation and clinical context. *JAMA Cardiology* **1**((9)): 976–977. doi: [10.1001/jamacardio.2016.3826](http://dx.doi.org/10.1001/jamacardio.2016.3826).

Gurwitz, J. H., D. J. Magid, D. H. Smith, R. J. Goldberg, D. D. McManus, L. A. Allen, J. S. Saczynski, M. L. Thorp, G. Hsu, S. H. Sung, and A. S. Go. 2013. Contemporary prevalence and correlates of incident heart failure with preserved ejection fraction. *The American Journal of Medicine* **126**((5)): 393–400. doi: [10.1016/j.amjmed.2012.10.022](http://dx.doi.org/10.1016/j.amjmed.2012.10.022).

Haenssle, H. A., C. Fink, R. Schneiderbauer, F. Toberer, T. Buhl, A. Blum, A. Kalloo, A. B. H. Hassen, L. Thomas, A. Enk, L. Uhlmann, I. Reader study level, and I. I. Groups level. 2018. Man against machine: Diagnostic performance of a deep learning convolutional neural network for dermoscopic melanoma recognition in comparison to 58 dermatologists. *Annals of Oncology* **29**((8)): 1836–1842. doi: [10.1093/annonc/mdy166](http://dx.doi.org/10.1093/annonc/mdy166).

Hastie, T., R. Tibshirani, and J. Friedman. 2001. *The Elements of Machine Learning: Data Mining, Inference and Prediction*. New York: Springer.

Hinton, G. 2018. Deep learning-a technology with the potential to transform health care. *JAMA* **320**((11)): 1101–1102. doi: [10.1001/jama.2018.11100](http://dx.doi.org/10.1001/jama.2018.11100).

Hochreiter, S., and J. Schmidhuber. 1997. Long short-term memory. *Neural Computation* **9**((8)): 1735–1780. doi: [10.1162/neco.1997.9.8.1735](http://dx.doi.org/10.1162/neco.1997.9.8.1735).

Hwang, Uiwon, Sungwoon Choi, and Sungroh Yoon. 2017. Disease prediction from electronic health records using generative adversarial networks. *arXiv preprint arXiv:1711.04126*.

LeCun, Y., Y. Bengio, and G. Hinton. 2015. Deep learning. *Nature* **521**((7553)): 436–444. doi: [10.1038/nature14539](http://dx.doi.org/10.1038/nature14539).

Lee, J. G., S. Jun, Y. W. Cho, H. Lee, G. B. Kim, J. B. Seo, and N. Kim. 2017. Deep learning in medical imaging: general overview. *Korean Journal of Radiology* **18** ((4)): 570–584. doi: [10.3348/kjr.2017.18.4.570](http://dx.doi.org/10.3348/kjr.2017.18.4.570).

Lundervold, A. S., and A. Lundervold. 2019. An overview of deep learning in medical imaging focusing on MRI. *Zeitschrift für Medizinische Physik* **29** ((2)): 102–127. doi: [10.1016/j.zemedi.2018.11.002](http://dx.doi.org/10.1016/j.zemedi.2018.11.002).

Maragatham, G., and S. Devi. 2019. LSTM model for prediction of heart failure in big data. *Journal of Medical Systems* **43**((5)): 111. doi: [10.1007/s10916-019-1243-3](http://dx.doi.org/10.1007/s10916-019-1243-3).

Miotto, R., F. Wang, S. Wang, X. Jiang, and J. T. Dudley. 2018. Deep learning for healthcare: review, opportunities and challenges. *Briefings of Bioinformatics* **19** ((6)): 1236–1246. doi: [10.1093/bib/bbx044](http://dx.doi.org/10.1093/bib/bbx044).

Ng, K., S. R. Steinhubl, C. deFilippi, S. Dey, and W. F. Stewart. 2016. Early detection of heart failure using electronic health records: practical implications for time before diagnosis, data diversity, data quantity, and data density. *Circulation: Cardiovascular Quality and Outcomes* **9**((6)): 649–658. doi: [10.1161/CIRCOUTCOMES.116.002797](http://dx.doi.org/10.1161/CIRCOUTCOMES.116.002797).

Nguyen, P., T. Tran, N. Wickramasinghe, and S. Venkatesh. 2017. $\\mathtt {Deepr}$: A convolutional net for medical records. *IEEE Journal of Biomedical and Health Informatics* **21** ((1)): 22–30. doi: [10.1109/JBHI.2016.2633963](http://dx.doi.org/10.1109/JBHI.2016.2633963).

Rajkomar, A., E. Oren, K. Chen, A. M. Dai, N. Hajaj, M. Hardt, P. J. Liu, X. Liu, J. Marcus, M. Sun, P. Sundberg, H. Yee, K. Zhang, Y. Zhang, G. Flores, G. E. Duggan, J. Irvine, Q. Le, K. Litsch, A. Mossin, J. Tansuwan, Wang, J. Wexler, J. Wilson, D. Ludwig, S. L. Volchenboum, K. Chou, M. Pearson, S. Madabushi, N. H. Shah, A. J. Butte, M. D. Howell, C. Cui, G. S. Corrado, and J. Dean. 2018. Scalable and accurate deep learning with electronic health records. *NPJ Digital Medicine* **1**: 18. doi: [10.1038/s41746-018-0029-1](http://dx.doi.org/10.1038/s41746-018-0029-1).

Rasmy, L., Y. Wu, N. Wang, X. Geng, W. J. Zheng, F. Wang, H. Wu, H. Xu, and D. Zhi. 2018. A study of generalizability of recurrent neural network-based predictive models for heart failure onset risk using a large and heterogeneous EHR data set. *Journal of Biomedical Informatics* **84**: 11–16. doi: [10.1016/j.jbi.2018.06.011](http://dx.doi.org/10.1016/j.jbi.2018.06.011).

Shickel, B., P. J. Tighe, A. Bihorac, and P. Rashidi. 2018. Deep ehr: a survey of recent advances in deep learning techniques for electronic health record (ehr) analysis. *IEEE Journal of Biomedical and Health Informatics* **22**((5)): 1589–1604. doi: [10.1109/JBHI.2017.2767063](http://dx.doi.org/10.1109/JBHI.2017.2767063).

Silver, D., A. Huang, C. J. Maddison, A. Guez, L. Sifre, G. van den Driessche, J. Schrittwieser, I. Antonoglou, V. Panneershelvam, M. Lanctot, S. Dieleman, D. Grewe, J. Nham, N. Kalchbrenner, I. Sutskever, T. Lillicrap, M. Leach, K. Kavukcuoglu, T. Graepel, and D. Hassabis. 2016. Mastering the game of Go with deep neural networks and tree search. *Nature* **529**((7587)): 484–489. doi: [10.1038/nature16961](http://dx.doi.org/10.1038/nature16961).

Suzuki, K. 2017. Overview of deep learning in medical imaging. *Radiological Physics Technology* **10** ((3)): 257–273. doi: [10.1007/s12194-017-0406-5](http://dx.doi.org/10.1007/s12194-017-0406-5).

Weng, W. H., K. B. Wagholikar, A. T. McCray, P. Szolovits, and H. C. Chueh. 2017. Medical subdomain classification of clinical notes using a machine learning-based natural language processing approach. *BMC Medical Informatics and Decision Making* **17**((1)): 155. doi: [10.1186/s12911-017-0556-8](http://dx.doi.org/10.1186/s12911-017-0556-8).

# [10 ](#contents.xhtml#toc1_215)  
![image](images/inline1_1.jpg)

# [EHR Data Analytics and Predictions: Machine Learning Methods](#contents.xhtml)  
               

Yuxuan Gu, Yuefan Huang, Vi K. Ly, Ashraf Yaseen and Hongyu Miao

## ![image](images/inline1_1.jpg)  
10.1 Machine Learning Overview

The meaning of machine learning (ML) might be different for people from different research and application fields. To simplify, here ML refers to a broad range of statistical and computational methods, theories, and tools for data exploration and analytics. In comparison with traditional statistical methods, ML approaches are primarily data-driven and may not rely on a pre-specified mechanistic model. With the goal of extracting hidden knowledge from data, usually the larger the number of samples available for learning tasks, the better the performance of ML algorithms. Thanks to its power and flexibility, ML becomes a popular choice for researchers and scientists in solving a variety of complex problems involving large datasets with a huge number of variables. In general, ML methods may be classified into several categories: supervised learning, unsupervised learning, semi-supervised learning, and reinforcement learning.

As described in [Shobha and Rangaswamy (2018)](#ch10.xhtml#ref10_18), supervised learning mainly adopts two types of techniques: 1) classification techniques, which are used to predict discrete responses (binary or multi-classes); e.g., the risk category of a patient to develop a certain disease or condition, and 2) regression techniques, which are mostly used to predict continuous responses; e.g., changes in a patient’s vital signs (like blood pressure or body temperature). Examples of ML algorithms commonly used for classification and/or regression include k-nearest neighbor (KNN), Naïve Bayes, linear models, bagged and boosted decision trees, random forests, support vector machine (SVM), and neural networks.

Nowadays, supervised learning has been broadly employed in the healthcare fields such as the diagnosis of diseases, disease risk prediction, or mortality/outcome prediction. A few examples include researchers using the rich information in EHR database to predict hospitalization due to heart diseases ([Dai et al. 2015](#ch10.xhtml#ref10_4)), forecasting the risk of type 2 diabetes ([Mani et al. 2012](#ch10.xhtml#ref10_14)), or predict 6-month mortality among cancer patients ([Parikh et al. 2019](#ch10.xhtml#ref10_16)). In the previous two chapters, we have discussed statistical methods, neural networks, and deep learning approaches for EHR data analysis and predictions. In this chapter, we focus on some select supervised learning techniques. We briefly describe these supervised learning techniques and then illustrate their usefulness via an EHR application project on mortality prediction for subarachnoid hemorrhage (SAH) patients. We will also compare the performance of these ML methods based on the SAH dataset.

## ![image](images/inline1_1.jpg)  
10.2 Machine Learning Methods

### Random Forest

In order to understand random forest, we need to start by defining the concept of a decision tree. Briefly, a decision tree is a decision-making tool that utilizes a branching, tree-like graph. Let S be the training set of n samples (x[1], y[1]), …, (x[n], y[n]), where x[i] ∈ X is the input instances, y[i] ∈ Y are the class labels associated with each x[i]. A decision tree is a classifier, *h*: X → Y, that predicts the label y of x by making a series of decisions along a tree structure. A typical decision-tree starts with the root node, the algorithm then assigns this node a label according to the majority vote among all attributes over the training set. As we move from the root node to the leaf node, a series of tests must be performed. For each test, we examine the effect of splitting a single branching node. The entropy (or gain) is used to help the algorithm find the best numerical or categorical feature to split from. The algorithm then looks at the improvement associated with the gain from each split; among all possible splits, we choose the one that maximizes the gain or we just stop if further splitting does not result in an increase in the gain. This process can also end if a pre-specified maximum depth of the tree is reached.

An example of a simple decision tree is shown in [Figure 10.1](#ch10.xhtml#fig10_1). In order to check if a given patient has a certain disease or not, the decision tree first examines the lab result of that patient. If this result is in the normal range, then the tree immediately predicts that the patient does not have the disease and stops there. Otherwise, the tree moves to examine the medication that the patient is taking. If that patient takes a medication related to the disease, the tree predicts that the patient has the disease.

![Figure 10.1 A simplified example of a decision tree modified from Shalev-Shwartz and Ben-David, 2014.](images/fig10_1.jpg)

**Figure 10.1**  
A simplified example of a decision tree modified from [Shalev-Shwartz and Ben-David, 2014](#ch10.xhtml#ref10_17).

Many algorithms for learning decision trees have been developed, such as ID3 and C4.5 and CART algorithm. For additional reading, we refer the readers to the work by [Hastie, Tibshirani, and Friedman (2009)](#ch10.xhtml#ref10_8). Here we will look into ID3, which is a commonly used decision tree algorithm ([Figure 10.2](#ch10.xhtml#fig10_2)). Specifically, ID3 is built upon the concept of recursive calls as follows:

![Figure 10.2 Pseudocode of ID3 algorithm modified from Shalev-Shwartz and Ben-David (2014).](images/fig10_2.jpg)

**Figure 10.2**  
Pseudocode of ID3 algorithm modified from [Shalev-Shwartz and Ben-David (2014)](#ch10.xhtml#ref10_17).

ID3 takes a training set S and a feature subset A as input. The algorithm calculates the Gain(S, i), which measures the probability of incorrectly classifying a randomly-chosen element in the dataset if it was randomly labeled according to the class distribution in the dataset. Then, the algorithm evaluates the gain of a split of the tree according to the ith feature and chooses the best split by maximizing the gain. In classification, we calculate the gain using the Gini impurity or entropy.

The decision tree is good for a dataset with a small number of features. However, for a dataset with a large feature space, algorithms like ID3 can return a large size and highly complex tree. Such a tree may predict a training data set well but perform poorly on a testing set, and thus incur the overfitting problem. To address this problem, the random forest (RF) algorithm was introduced by [Breiman (2001)](#ch10.xhtml#ref10_1). RF works by constructing an ensemble of trees. The prediction of the random forest is obtained by a majority vote over the predictions of the individual trees ([Shalev-Shwartz and Ben-David 2014](#ch10.xhtml#ref10_17)) ([Figure 10.3](#ch10.xhtml#fig10_3)).

![Figure 10.3 A simplified structure of random forest algorithm modified from Subramaniam and Kaur (2019).](images/fig10_3.jpg)

**Figure 10.3**  
A simplified structure of random forest algorithm modified from [Subramaniam and Kaur (2019)](#ch10.xhtml#ref10_19).

Specifically, given a training data set *S* = *(x*[*1*]*, y*[*1*]*), …, (x*[*m*]*, y*[*m*]*)*, we will implement a random forest algorithm as follows: First, we sample with a replacement on the training set S to get smaller subsets; then, we train a classification tree algorithm (such as ID3) on all those extracted subsets; Eventually, after we get all the predictions from individual trees, we take the majority vote to get the final prediction. Therefore, the training algorithm for random forests applies the general technique of bagging, or by bootstrapping sampling from the training set uniformly and with the replacement, to decision trees. (James, Witten, and Tibshirani 2013) This bagging method decreases the variance of the model and does not increase the bias. Hence, it helps in preventing the problem of overfitting from decision trees as mentioned earlier.

### Extremely Randomized Tree

Extremely randomized tree (ERT) has been introduced by [Geurts, Ernst and Wehenkel (2006)](#ch10.xhtml#ref10_6). ERT is a new tree-based algorithm that introduces randomness totally or partially on splits. In terms of computational cost, ERT can be more efficient than the random forest. When a large number of attributes are involved, the computational efficiency of ERT is even attractive and thus might be a suitable tool for EHR data analysis (for instance, one patient could have hundreds or even thousands of laboratory tests, clinical procedures, and/or medications; therefore, the data dimension is often extremely high). There are two main differences that distinguish random forest from ERT: i) for the ERT algorithm, each split is chosen at random, while each split is optimal in the random forest method. Consecutively, the trees built in ERT are more diverse. ii) each tree in ERT is built by using the entire learning sample while in the random forest, each decision tree is built by a bootstrapped learning sample.

The variance of a single tree can be high and using ensemble methods could reduce such variance. Among the ensemble methods, the amount of reduction in variance introduced by bagging is less than that of random forest and ERT because averaging highly correlated trees (as in the bagging approach) will have less variance reduction than averaging uncorrelated trees. The ERT has a tendency to strongly reduce variance at the cost of increasing bias. In practice, one needs to find the best balance between variance and bias, which is called bias and variance trade-off. Overfitting is a common problem for decision tree models, especially when a tree has many levels. To address this issue, the recommended approach is to use the bagging method described earlier in the section of random forest.

### Gradient Boosting

What is boosting? Simply put, it is a committee-based procedure like bagging. In the bagging approach, we calculate the average of all the predictions from bootstrap sampling. Therefore, bagging is parallelizable. However, boosting is a sequential method and cannot be parallelized in the same way as bagging (i.e., the residuals from the previous iteration are inputs to the current iteration). It takes the outputs of many weak classification models (usually decision trees) and combines them to form a more powerful “committee”.

In gradient boosting, we build an ensemble of decision trees in a stage-wise fashion and use a functional gradient descent (FGD) procedure to minimize the loss. In FGD, we parametrize the trees and reduce the residual loss at each step by moving in the direction suggested by the gradient descent algorithm. ([Hastie, Tibshirani and Friedman 2009](#ch10.xhtml#ref10_8)).

In the pseudo-code in [Figure 10.4](#ch10.xhtml#fig10_4), it can be seen that by inserting different loss criteria *L(y, f(x))L(y, f(x)),* we can do a customized implementation for gradient boosting.

![Figure 10.4 Pseudocode of gradient boosting modified from Hastie, Tibshirani, and Friedman (2009).](images/fig10_4.jpg)

**Figure 10.4**  
Pseudocode of gradient boosting modified from [Hastie, Tibshirani, and Friedman (2009)](#ch10.xhtml#ref10_8).

### XgBoost

Boosting is a very popular and effective machine learning method and is usually employed as a benchmark approach. Recall that boosting is an ensemble method, but instead of training all models parallelly, it builds models in a sequential manner such that the new models are built to correct the errors made by its predecessor.

Before getting into the details, it is necessary to point out that gradient tree boosting is the same as Gradient Boosting Machine (GBM) or gradient boosted regression tree (GBRT), and XGBoost is the nickname for eXtreme Gradient Boosting. XGBoost was proposed by Tianqi Chen in a research project as part of the Distributed (Deep) Machine Learning Community (DMLC) group ([Chen et al. 2015](#ch10.xhtml#ref10_2)). Boosting can be very slow in training time because it needs to sequentially train and build models; hence, such methods are not easily scalable. Thus, XGBoost focuses on both execution speed and model performance. XGBoost can do parallel tree construction and out-of-core computation for big datasets that do not even fit in available memory. Technically, XGBoost is a regularized method so it can control overfitting and may have better performance. In addition, XGBoost introduces a new sparsity aware algorithm, learning from the data in the optimal way to deal with missing values and to handle different kinds of sparsity patterns in a unified manner (e.g., the sparsity due to missing values, frequent zero entries, or artifacts caused by one-hot encoding). With many attractive features introduced into regular gradient boosting, XGBoost provides a parallel tree boosting solution to many data science problems in an efficient way.

### Support Vector Machine (SVM)

The SVM algorithm was introduced for the first time in the “Statistical learning theory frameworks” paper by [Vapnik (1995)](#ch10.xhtml#ref10_20). [Cortes and Vapnik (1995)](#ch10.xhtml#ref10_3) later used SVM for binary classification problems. Later, the SVM framework has been significantly extended to various problems, including regression, ranking and clustering.

In many machine learning tasks, we often face the problem of sample complexity as the dimensionality of the feature space goes higher. The SVM algorithm tackles the sample complexity problem by finding the half-space separators.

We can look at the simple example in [Figure 10.5, from which](#ch10.xhtml#fig10_5) we can tell that the blue and red hyperplanes together separate the example data points of two different clusters (in green and yellow colors, respectively). We call those hyperplane lines the half-space separators.

![Figure 10.5 A simplified example of SVM modified from Shalev-Shwartz and Ben-David (2014).](images/fig10_5.jpg)

**Figure 10.5**  
A simplified example of SVM modified from [Shalev-Shwartz and Ben-David (2014)](#ch10.xhtml#ref10_17).

In order to pick the optimal half-space, we need to maximize the margin of two clusters. From the example above, we would prefer the blue hyperplane since the blue line has a larger margin which means better separation. The margin is defined to be the minimal distance between a point in the training set and the hyperplane.

Hard-SVM is the learning algorithm that will run through the training set to find and return a half-space with the largest margin (a hyperplane that best separates the training set into predefined classes). The pseudo-code for hard SVM is described in [Figure 10.6](#ch10.xhtml#fig10_6).

Intuitively, *w* is the margin and *b* is the bias, hard-SVM searches for the *w* of a minimal norm among all the vectors that separate the data, for which |⟨*w*,*x*[*i*]⟩ + *b* | ≥ 1 for all *i*. From there, the output of hard-SVM is indeed the separating hyperplane with the largest margin. In other words, finding the largest margin half-space becomes the problem of finding *w* whose norm is minimal.

Hard-SVM formulation requires a strict condition that the training set is linearly separable, which is usually not the case for real-world data. When the training set is homogenous but not linearly separable, soft-SVM is more suitable. We can view soft-SVM as a less restrictive version of Hard-SVM that can work even if the training set is not linearly separable.

As described in [Shalev-Shwartz, and Ben-David (2014)](#ch10.xhtml#ref10_17), the optimization function in Equation (10.1) in [Figure 10.6](#ch10.xhtml#fig10_6) enforces the hard constraint *y*[*i*](⟨*w*,*x*[*i*]⟩+*b*) ≥ 1 for all *i*. To address this, soft-SVM allows this constraint to be relaxed at some data points in the training set. This can be modeled by introducing non-negative slack variables, *ξ*[*i*]*w**i**t**h* *i* = 1, …, *m*, which measures to what extent the constraint *y*[*i*](⟨*w*,*x*[*i*]⟩+*b*) ≥ 1 is being violated. Then, the algorithm replaces each constraint *y*[*i*](⟨*w*,*x*[*i*]⟩+*b*) ≥ 1 by *y*[*i*](⟨*w*,*x*[*i*]⟩+*b*) ≥ 1 − *ξ*[*i*] as in function (10.2) in [Figure 10.7](#ch10.xhtml#fig10_7). Soft-SVM jointly minimizes the norm of *w* (e margin) and the average of ξ[*i*] (the violations of the constraints). A parameter λ controls the tradeoff between these two terms. The pseudo-code for soft-SVM is as in Figure 10.7.

![Figure 10.6 Pseudocode of hard SVM modified from Shalev-Shwartz and Ben-David (2014).](images/fig10_6.jpg)

**Figure 10.6**  
Pseudocode of hard SVM modified from [Shalev-Shwartz and Ben-David (2014)](#ch10.xhtml#ref10_17).

![Figure 10.7 Pseudocode of soft SVM modified from Shalev-Shwartz and Ben-David (2014).](images/fig10_7.jpg)

**Figure 10.7**  
Pseudocode of soft SVM modified from [Shalev-Shwartz and Ben-David (2014)](#ch10.xhtml#ref10_17).

We see that a Soft-SVM algorithm uses regularized loss minimization for Equation (10.2) in [Figure 10.7](#ch10.xhtml#fig10_7) so that it can penalize not only training errors. Therefore, soft-SVM is often used to deal with a homogenous half-space. For further details, please refer to [Shalev-Shwartz and Ben-David (2014)](#ch10.xhtml#ref10_17).

For non-linear and inseparable data, we need to use the Kernel trick to help SVM’s to form nonlinear boundaries. How does the Kernel trick work? First, the original data are passed through non-linear maps to form new data in a high-dimensional space. Then, we perform a function to take a dot product of the data after doing non-linear mapping on it. This function is the kernel function ([Jakkula 2011](#ch10.xhtml#ref10_10)). Different SVM algorithms use different types of kernel functions such as *linear, nonlinear, sigmoid, polynomial, and radial basis function (RBF).* The most popular one **is** RBF since it localizes and limits the response along the entire x-axis. ([Hill and Lewicki 2006](#ch10.xhtml#ref10_9)).

## ![image](images/inline1_1.jpg)  
10.3 Machine Learning Software Tools

There exist numerous software packages that implement the machine learning models and computing algorithms described in the previous section. While we are not able to illustrate all such packages in this chapter, we select several representative packages and demonstrate how to employ them to achieve machine learning tasks using different ML methods such as Least Squares Support Vector Machine with Radial Basis Function Kernel, Random Forest, Stochastic Gradient Boosting, Xgboost, or Extremely Randomized Tree.

### H2O

H2O.ai is a visionary open-source software company committed to providing novel scalable machine learning technologies. Besides its web interface, H2O.ai also provides interfaces to R, Python, Scala, Java, JSON, and CoffeeScript/JavaScript. H2O supports commonly used machine learning algorithms, such as random forest, gradient boosting, generalized linear model, deep learning, and more. We use R interface here, which happens to be very flexible when tuning hyperparameters and defining customized constraints (e.g., training time, optimization of hyperparameter search, maximum models to be trained, and stopping metric). The available models are listed in [Table 10.1](#ch10.xhtml#table10_1).

**Table 10.1** Available Models of H2O

| **Supervised** || **Unsupervised** |
| --- | --- |
| • Cox Proportional Hazards (CoxPH) || • Aggregator |
| --- | --- |
| • Deep Learning (Neural Networks) || • Generalized Low Rank Models (GLRM) |
| • Distributed Random Forest (DRF) || • Isolation Forest |
| • Generalized Linear Model (GLM) || • K-Means Clustering |
| • Gradient Boosting Machine (GBM) || • Principal Component Analysis (PCA) |
| • Naïve Bayes Classifier || **Miscellaneous** |
| • Stacked Ensembles || • Word2vec |
| • Support Vector Machine (SVM) || **MOJO Models** |
| • XGBoost || • MOJO Models |

Here we give some example code for H2O-based machine learning methods. First, we load the H2O library in R and prepare the training and testing datasets.

![image](images/inline10_1.jpg)

One important step is to convert the training and testing datasets into H2O objects:

![image](images/inline10_2.jpg)

We then perform parameter tuning by random search, which is indicated by “RandomDiscrete” in the search criteria. H2O has a grid search strategy as well, and we just need to specify the search strategy as “Cartesian”. The evaluation metric we use is AUC; of course, there are other metrics available as well, for example, MSE, MAE, RMSE, and deviance.

![image](images/inline10_3.jpg)

### Caret

The Caret package (Classification and Regression Training) in R is a versatile library that can handle multiple tasks. So far, 238 statistical or machine learning models are available in this package, both classification and regression models included (e.g., AdaBoost Classification Trees, k-Nearest Neighbors, etc.).

The basic process of creating predictive models is,

*   data splitting
    
*   pre-processing
    
*   feature selection
    
*   model tuning using resampling
    
*   variable importance estimation
    

Here is the code example of data splitting and preprocessing, using the example data “Sonar” from “mlbench”.

![image](images/inline10_4.jpg)

Split dataset to training and testing data sets via the following code:

![image](images/inline10_5.jpg)

Here is an example of 10-fold repeated cross-validation parameter tuning:

![image](images/inline10_6.jpg)

After we decided to use the cross-validation method, here is an example of a simple boosted tree model, where the “method” option can be changed to many other methods and the “trControl” was defined as the 10-fold repeated cross-validation described before. After the model fitting with the training dataset, the prediction model was fitted for the testing data set.

![image](images/inline10_7.jpg)

Sometimes, we also want to identify the important variables that are related or most predictive to the outcome, the following code below can be used to evaluate the variable importance and a plot of top 20 important variables is produced.

![image](images/inline10_8.jpg)

More details on the package of Caret can be found in the book Applied Predictive Modeling ([Kuhn and Johnson 2013](#ch10.xhtml#ref10_13)) and a paper in the Journal of Statistical Software ([Kuhn 2008](#ch10.xhtml#ref10_12)).

### Tpot

The Tree-Based Pipeline Optimization Tool (TPOT) is an open-source AutoML software package in Python built on the scikit-learn library. The goal of TPOT is to automate the design and implementation of machine learning pipelines using a stochastic optimization process to make machine learning more friendly and accessible to non-experts ([Olson et al. 2016](#ch10.xhtml#ref10_15)).

TPOT optimizes a pipeline by starting from several simple and randomly chosen pipelines (the population). For every iteration of the optimization process (a generation), TPOT makes several copies of the current best-performing pipelines in the population and then applies random changes to them (e.g., adding or removing an operation or tuning a parameter setting of one operation). At the end of every generation, the worst-performing pipelines are removed from the population, and TPOT proceeds to the next generation. After a fixed number of generations, TPOT recommends the best performing pipeline that it has created during the optimization process. TPOT is very user-friendly, even people with no data analysis experience can easily learn and use it. You only need to specify the generations and populations you want to generate.

### Auto-sklearn

Auto-sklearn is also an open-source AutoML toolkit, built upon the scikit-learn library. The main goal of this package is to automatically select algorithms and tune parameters. There are 4 data preprocessing methods, 14 preprocessing methods, and 15 classification algorithms included in this package ([Feurer et al. 2015](#ch10.xhtml#ref10_5)).

In our application example, the algorithms we used are logistic regression, SVM, random forest, gradient boosting, and Xgboost. We used 5-fold cross-validation and the same tuning time to compare the AUC between different machine learning algorithms (see next section below). Auto-sklearn is pretty flexible in defining training time and tuning options, and the code is easy to understand, as you can tell from the following example:

![image](images/inline10_9.jpg)

This example also shows how to use 5-fold cross-validation. One more thing to mention is that you have to reload the data and use refit function before calculating AUC in order to make cross-validation work properly.

![image](images/inline10_10.jpg)

## ![image](images/inline1_1.jpg)  
10.4 Application Example: SAH Project

In this section, we share our experience and evaluate the performance of different machine learning methods and packages based on the application example on mortality prediction for subarachnoid hemorrhage (SAH) patients from an EHR (Cerner) database.

### Prediction Scenarios

For the SAH project, we intend to develop a prediction model for SAH mortality for the following six cases (see [Chapter 5](#ch05.xhtml#chapter5) for more details):

1.  Use of first 24 hours EHR data after admission: 1263 patients for training, 545 for testing, 917 dummy variables (predictors)
    
2.  Use of first 48 hours EHR data after admission: 1665 patients for training, 689 for testing, 930 dummy variables (predictors)
    
3.  Use of first 72 hours EHR data after admission: 1661 patients for training, 714 for testing, 975 dummy variables (predictors)
    
4.  Use of EHR data up to 24 hours before discharge or death: 2773 patients for training, 1183 for testing, 1473 dummy variables (predictors)
    
5.  Use of EHR data up to 48 hours before discharge or death: 2486 for training, 1058 for testing, 1421 dummy variables (predictors)
    
6.  Use of EHR data up to 72 hours before discharge or death: 2284 for training, 987 for testing, 1375 dummy variables (predictors)
    

### Predictors and Outcome Data

For this prediction, we included variables from medication, procedure, diagnosis, and demographics tables. In the k-fold cross-validation, we chose the specific value k to 5, then we randomly divided our training data into 5 sets, use one of the folds as the validation set and the rest four as training sets to train our model, and do this iteratively until we have used each fold as a validation set once. In this manner, we would have 5 performance measures, one for each fold, and the final performance is the mean of the 5 performance measures. In this project, we will focus on the mortality prediction: ‘death’ coded as 1 and ‘survived’ coded as 0.

### Model Training

Training machine learning models can be very tricky and different hyperparameters may yield very different results. Here we list the hyperparameters that need to be fine-tuned and the tuning ranges that were used to train our prediction models ([Figures 10.8](#ch10.xhtml#fig10_8)–[10.10](#ch10.xhtml#fig10_10)).

![Figure 10.8 Random forest hyperparameter range.](images/fig10_8.jpg)

**Figure 10.8**  
Random forest hyperparameter range.

![Figure 10.9 GBM hyperparameter range.](images/fig10_9.jpg)

**Figure 10.9**  
GBM hyperparameter range.

![Figure 10.10 XGBoost hyperparameter range.](images/fig10_10.jpg)

**Figure 10.10**  
XGBoost hyperparameter range.

### Result of Outcome Prediction

In our example, we ran six different methods in total and chose from four software packages we mentioned at the beginning of this section. At each time, we set a specific machine learning model in one package, and we used 5-fold cross-validation and reported the area under the curve (AUC) for validation purposes. The results are shown below ([Table 10.2](#ch10.xhtml#table10_2)).

**Table 10.2** AUC (%) from Four Different Software Packages for Non-Trauma SAH Patients with Six Different Prediction Windows

![image](images/tbl10_2.jpg)

<table id="Tbl29"><tgroup cols="9"><colspec colname="col1" colnum="1"/><colspec colname="col2" colnum="2"/><colspec colname="col3" colnum="3"/><colspec colname="col4" colnum="4"/><colspec colname="col5" colnum="5"/><colspec colname="col6" colnum="6"/><colspec colname="col7" colnum="7"/><colspec colname="col8" colnum="8"/><colspec colname="col9" colnum="9"/> <thead> <tr><td/> <td>TPOT</td> <td>Caret</td> </tr> <tr> <td>Logistic Regr.</td> <td>SVM</td> <td>Random Forest</td> <td>Xgboost</td> <td>Logistic Regr.</td> <td>SVM</td> <td>Random Forest</td> <td>GBM</td> </tr> </thead> <tbody> <tr> <td>First 24&#160;Hours</td> <td>86.38</td> <td>86.29</td> <td>85.58</td> <td>86.04</td> <td>85.37</td> <td>78.63</td> <td>85.86</td> <td>84.23</td> </tr> <tr> <td>First 48&#160;Hours</td> <td>84.91</td> <td>85.10</td> <td>82.85</td> <td>84.87</td> <td>83.99</td> <td>82.88</td> <td>84.32</td> <td>83.59</td> </tr> <tr> <td>First 72&#160;Hours</td> <td>83.53</td> <td>83.57</td> <td>83.11</td> <td>82.13</td> <td>81.25</td> <td>78.99</td> <td>81.61</td> <td>81.12</td> </tr> <tr> <td>Cutoff Last 24 Hours</td> <td>93.86</td> <td>93.85</td> <td>91.58</td> <td>93.45</td> <td>92.95</td> <td>87.48</td> <td>91.19</td> <td>93.36</td> </tr> <tr> <td>Cutoff Last 48 Hours</td> <td>92.07</td> <td>92.06</td> <td>89.77</td> <td>92.04</td> <td>91.20</td> <td>89.24</td> <td>88.53</td> <td>91.81</td> </tr> <tr> <td>Cutoff Last 72 Hours</td> <td>90.64</td> <td>90.53</td> <td>87.86</td> <td>89.86</td> <td>89.20</td> <td>85.58</td> <td>86.79</td> <td>89.75</td> </tr> <tr><td/> <td><b>H2O</b></td> <td><b>Auto-sklearn</b></td> </tr> <tr><td/> <td><b>Logistic Regr.</b></td> <td><b>GBM</b></td> <td><b>Random Forest</b></td> <td><b>Xgboost</b></td> <td><b>ERT</b></td> <td><b>SVM</b></td> <td><b>Random Forest</b></td> <td><b>GBM</b></td> </tr> <tr> <td>First 24&#160;Hours</td> <td>84.50</td> <td>87.25</td> <td>86.72</td> <td>87.27</td> <td>85.35</td> <td>87.34</td> <td>84.24</td> <td>86.23</td> </tr> <tr> <td>First 48&#160;Hours</td> <td>84.71</td> <td>85.40</td> <td>84.15</td> <td>86.05</td> <td>83.51</td> <td>84.01</td> <td>82,79</td> <td>79.53</td> </tr> <tr> <td>First 72&#160;Hours</td> <td>82.03</td> <td>84.12</td> <td>82.97</td> <td>85.04</td> <td>82.84</td> <td>83.40</td> <td>82.81</td> <td>81.82</td> </tr> <tr> <td>Cutoff Last 24 Hours</td> <td>92.11</td> <td>93.88</td> <td>91.77</td> <td>94.11</td> <td>91.26</td> <td>93.45</td> <td>90.65</td> <td>91.28</td> </tr> <tr> <td>Cutoff Last 48 Hours</td> <td>90.28</td> <td>91.97</td> <td>89.65</td> <td>92.34</td> <td>89.36</td> <td>90.81</td> <td>88.62</td> <td>90.03</td> </tr> <tr> <td>Cutoff Last 72 Hours</td> <td>87.83</td> <td>90.48</td> <td>87.83</td> <td>90.84</td> <td>87.45</td> <td>90.07</td> <td>86.24</td> <td>87.76</td> </tr> </tbody></tgroup> </table> 

### Evaluation of Model Performance

We use the AUC to evaluate the performance of different prediction models and algorithms. The higher the AUC is, the better the model is. When AUC is equal to 0.5, it indicates that the model works just like the random guess.

[Figure 10.11](#ch10.xhtml#fig10_11) gives a rough idea about how AUC for different models looks like. Ideally, if the model is considered good, then the curve has to approach the upper left corner, if the curve is around the diagonal line from lower left to upper right, then the AUC for the model is roughly 0.5 indicating the model is not performing well. For our model, the results are generally considered good. Most of the AUCs are higher than 0.8, and some of the results are even higher than 0.9. Comparing the results between the six cases, the conclusion indicates that the more data we use, the more accurate the prediction is, which is reasonable ([Figure 10.12](#ch10.xhtml#fig10_12)).

![Figure 10.11 AUC for comparing six models.](images/fig10_11.jpg)

**Figure 10.11**  
AUC for comparing six models.

![Figure 10.12 Dotplot of model performance by comparing six cases.](images/fig10_12.jpg)

**Figure 10.12**  
Dotplot of model performance by comparing six cases.

The comparison between packages and methods are more complicated ([Figure 10.13](#ch10.xhtml#fig10_13)). From what we observed in our specific problem, the performances of GBM and the Xgboost (regularized version of gradient boosting) in H2O are consistently better than those of the other three packages, except for the data version “first 24 hours” wherein the performance of SVM in Auto-sklearn is the best. Also, logistic regression does not yield the best performance. H2O also generates better results than the other three packages for random forest except for the data version “first 48”, where the caret model is slightly better than H2O. TPOT gives higher AUC than the other three packages for the logistic regression model except for the data version “cut off last 72 hours”. TPOT also gives higher AUC than the other three packages for SVM model except for the data version “first 24 hours”. From what is shown above, there is no universally best package and the performance of a package will vary by models and by data input. We have to make a tradeoff between running time and performance metrics. Our recommendation is that if you have enough time to try all the packages, then it can give you a better estimate of the best model performance. With that said, any of the packages above may generate reasonable results for your particular projects.

![Figure 10.13 Dotplot of model performance by comparing six models using four different packages.](images/fig10_13.jpg)

**Figure 10.13**  
Dotplot of model performance by comparing six models using four different packages.

## ![image](images/inline1_1.jpg)  
10.5 Conclusion and Recommendation

From what is shown above, there is no universally best package and the performance of a package will vary by models as well as by data input. We have to make a trade-off between running time and performance metrics. TPOT, H2O, and Caret give the results relatively faster, and it takes more time to train models by Auto-sklearn (the default running time is one hour). TPOT is recommended if you want to see the result quickly, and the performance is relatively good. If you have enough time to train the model, it could be better to use GBM and XGBoost in the H2O package to get the best performance. Tree-based models like extra tree and random forest do not perform well in our EHR dataset, and H2O is our recommendation if you want to use tree-based models for your specific project. For R users, H2O and Caret are well documented and easy to use. For Python users, TPOT and Auto-sklearn would be familiar to use if you have experience on scikit-learn. In general, if you have enough time to try all packages, then it can give you a better estimate of the best model performance, but any of the packages above may generate reasonable results for your particular projects.

### ![image](images/inline1_1.jpg)  
References

Breiman, L. 2001. Random forests. *Machine Learning* **45**((1)), 5–32. doi: [10.1023/A:1010933404324](http://dx.doi.org/10.1023/A%3A1010933404324).

Chen, T., Tong He, M. Benesty, V. Khotilovich, and Y. Tang. 2015. *Xgboost: Extreme Gradient Boosting. R Package Version* **0.4–2** ((2015)), 1–4.

Cortes, C., V. Vapnik. 1995. Support-vector networks. *Machine Learning* **20**, 273–297. [https://doi.org/10.1007/BF00994018](https://doi.org/10.1007/BF00994018).

Dai, W., T. S. Brisimi, W. G. Adams, T. Mela, V. Saligrama, and I. Paschalidis. 2015. Prediction of hospitalization due to heart diseases by supervised learning methods. *International Journal of Medical Informatics* **84**((3)), 189–197. [https://doi.org/10.1016/j.ijmedinf.2014.10.002](https://doi.org/10.1016/j.ijmedinf.2014.10.002).

Feurer, M., A. Klein, K. Eggensperger, J. Springenberg, M. Blum, and F. Hutter. 2015. Efficient and robust automated machine learning. In: *Advances in Neural Information Processing Systems* 2962–2970.

Geurts, P., D. Ernst, and L. Wehenkel. 2006. Extremely randomized trees.” *Machine Learning*. **63** (1), 3–42. [10.1007/s10994-006-6226-1](http://dx.doi.org/10.1007/s10994-006-6226-1).

Hastie, T., R. Tibshirani, and J. H. Friedman. 2009. *The Elements of Statistical Learning* (2nd edn ed.). New York: Springer.

Hill, T., and P. Lewicki. 2006. *Chapter 23: Machine learning. Statistics: Methods and Applications: A Comprehensive Reference Fro Science, Industry, and Data Mining* 317–327. Tulsa: Statsoft.

Jakkula, V. R. 2011. “ *Tutorial on Support Vector Machine* (SVM).” *School of EECS, Washington State University*, 1–13.

James, G., D. Witten, T. Hastie, and R. Tibshirani. 2013. *An Introduction to Statistical Learning*. New York: Springer, pages 316–321.

Kuhn, M. 2008. Building predictive models in R using the caret package. *Journal of Statistical Software* **28**((5)), 1–26.

Kuhn, M., and K. Johnson. 2013. *Applied Predictive Modeling* (Vol. **26**). New York: Springer.

Mani, S., Chen, W., Elasy, Clayton, and J. Denny. 2012. Type 2 diabetes risk forecasting from EMR data using machine learning. *AMIA Annual Symposium proceedings. AMIA Symposium* **2012**, 606–615.

Olson, R. S., N. Bartley, R. J. Urbanowicz, and J. H. Moore. 2016, July. Evaluation of a tree-based pipeline optimization tool for automating data science. In: *Proceedings of the Genetic and Evolutionary Computation Conference* **2016**, 485–492.

Parikh, R. B., C. Manz, C., Chivers, S. H. Regli, J. Braun, M. E. Draugelis, N. R. O’Connor. 2019. Machine learning approaches to predict 6-month mortality among patients with cancer. *JAMA Network Open* **2**((10)), e1915997. doi:[10.1001/jamanetworkopen.2019.15997](http://dx.doi.org/10.1001/jamanetworkopen.2019.15997).

 Shalev-Shwartz, S., and S. Ben-David. 2014. *Understanding Machine Learning: From Theory to Algorithms*. Cambridge: Cambridge University Press.

Shobha, G., and S. Rangaswamy. 2018. *Section 1.1 Supervised Learning.* In: *Computational Analysis and Understanding of Natural Languages: Principles, Methods and Applications* (1st edn ed.). **38**, 197–228. Amsterdam: North Holland, an imprint of Elsevier.

Subramaniam, P. and M. Kaur. 2019. *“Review of Security in Mobile Edge Computing with Deep Learning.” 2019 Advances in Science and Engineering Technology International Conferences, ASET 2019.*[](http://dx.doi.org/10.1109/ICASET.2019.8714349)

V. N. Apnik. 1995. *The Nature of Statistical Learning Theory*. Springer, New York.

# [11 ](#contents.xhtml#toc1_236)  
![image](images/inline1_1.jpg)

# [Use of EHR Data for Research: Future](#contents.xhtml)  
               

Hulin Wu

## ![image](images/inline1_1.jpg)  
11.1 Future EHR Research

In previous chapters, we have focused on the approaches and methodologies for structured EHR data for research and scientific discoveries. However, it is more powerful if unstructured EHR data, such as clinical notes, pathological or diagnosis images, and high-frequency data from medical devices and monitoring equipment (EEG, ECG etc.), can be integrated with the structured data for analysis and prediction. In general, unstructured data are more difficult to access since it is not as easy to de-identify and share. Additionally, unstructured data are more challenging to analyze because of their complexity and large volume.

Another trend of EHR research is to integrate other types of data from different sources with the EHR data to improve disease risk predictions, disease diagnosis, and patient care quality. Other types of data may include genomics data, real-time monitoring data from wearable devices, social determinants of health (SDoH) from census, population or community studies, public or government databases, and data from other research projects including laboratory experiments, observational studies and clinical trials. Since these types of data are from different sources or studies, it is challenging to integrate or standardize them with EHR data. These other types of data are typically only available for a subset of patients in the EHR system, selection bias may also need to be considered in the analysis and integration process. Ideally, if any of the data from other sources can help with clinical decision-making for patient care improvement, those data should be used and integrated, and a clinical decision support (CDS) system should be developed to improve patient management. This will also allow for rapid translation of research results into healthcare benefits.

UK Biobank ([https://www.ukbiobank.ac.uk/](https://www.ukbiobank.ac.uk)), is a large and openly accessible de-identified database that enables integration of health outcomes (including EHR data from primary care, hospital inpatients, death registry and cancer registry) from 500,000 volunteer participants, recruited in the UK between 2006–2010, with genomic, imaging, biological, physical activity, cognitive, behavioral and mental health, 24-hour dietary recall, and environmental data. This large database that enables the consolidation of EHR data with other data types is an excellent resource for researchers to integrate heterogeneous data for biomedical and health science research. However, this large cohort also has its limitations. In particular, the UK Biobank study is not designed to represent the general population and follow-up visits are sparse. In order to improve healthcare through research, the National Institutes of Health (NIH) of the USA recently initiated a similar research program, “The All of Us” program ([https://allofus.nih.gov/](https://allofus.nih.gov)) which aims to recruit one million participants and collect many of the above-mentioned data types. However, these data may not be available for analysis until after a few more years.

Patient privacy and data security present major challenges for using EHR data for research and scientific discoveries. To deal with this important issue, in addition to the development of efficient and reliable approaches and methods for data de-identification, the use of simulation technologies to generate synthetic EHR data can help ensure data privacy and protect against data security issues. While it would not be easy to justify the scientific discoveries based on synthetic EHR data, the simulation approach is useful for training, education, EHR methodology testing purposes, and to simulate and investigate the effect of new healthcare policies and intervention strategies. EHR simulation systems have been proposed and developed by collaborations between industry and academic partners. Earlier efforts for EMR simulations used real EMR data to identify patient care models or patterns and generated the patient identities and basic information so that complete EMR data could be synthesized ([Moniz et al. 2009](#ch11.xhtml#ref11_13), [Buczak, Babin, and Moniz 2010](#ch11.xhtml#ref11_3)). Another simulated EHR data system, termed “Synthea”, was developed using public data ([McLachlan, Dube, and Gallagher 2016](#ch11.xhtml#ref11_11), [Walonoski et al. 2018](#ch11.xhtml#ref11_18)) such as demographics data from the US Census Bureau, disease prevalence and incidence rates from the Centers for Disease Control and Prevention, health incidence statistics, NIH reports, Clinical Practice Guidelines (CPGs) and protocols, and medical coding dictionaries. Actual EHR data were not used for Synthea development. This system can be used to simulate the entire lifespans of synthetic patients, but it may not reflect patients’ records in a real EMR or EHR system. Recently, generative adversarial networks (GAN) have been proposed to synthesize EHR data ([Choi et al. 2017](#ch11.xhtml#ref11_5), [Baowaly et al. 2019](#ch11.xhtml#ref11_1)); however, this model is not used to generate raw EHR data, which are irregular and noisy, instead, it is used to generate a regular data matrix that mimics the variables and factors derived from EHR databases. One obvious challenge is how to evaluate whether a simulated EHR database is good or not since there is no quantitative standard or evaluation method to define a “good” synthetic EHR dataset. To this end, different EHR simulation systems may need to be developed for different purposes. Generally, a good synthetic EHR dataset should be realistic and applicable to achieve the targeted goals, although it is difficult to evaluate the quality of the simulated EHR data.

One of the EHR data sharing approaches is to use the Observational Medical Outcomes Partnership (OMOP) Common Data Model (CDM) developed by the Observational Health Data Sciences and Informatics (OHDSI) organization ([https://www.ohdsi.org/](https://www.ohdsi.org)). The idea behind this approach is to transform data from different EHR databases into a common format (data model) as well as a common representation (terminologies, vocabularies, coding schemes) from which summary statistics and analyses can be derived and performed systematically using a library of standard analytic routines that are developed based on the common format. These summary statistics and analysis results from different EHR databases could then be shared without sharing the original raw data at individual patient levels, avoiding patient privacy and data security issues. However, one challenge of this approach is that it is not trivial to efficiently integrate the summary statistics and analysis results from different EHR databases and new statistical approaches may need to be developed for this purpose. One approach consists of distributed statistical inference and analysis methods ([Zhang, Duchi, and Wainwright 2013](#ch11.xhtml#ref11_20), [Chen and Xie 2014](#ch11.xhtml#ref11_4), [Neiswanger, Wang, and Xing 2013](#ch11.xhtml#ref11_14), [Lee et al. 2015](#ch11.xhtml#ref11_10), [Wang and Dunson 2013](#ch11.xhtml#ref11_19), [Battey et al. 2018](#ch11.xhtml#ref11_2), [Jordan, Lee, and Yang 2019](#ch11.xhtml#ref11_9), [Fan et al. 2019](#ch11.xhtml#ref11_8)) which utilize distributed computing and divide-and-conquer strategies to handle the aforementioned Big Data analytic challenge. These methods could be further adapted to combine and integrate the analysis results from different EHR databases in order to make effective statistical inferences, which is recommended for future research.

Cutting-edge artificial intelligence (AI) technologies have recently played an important role in solving healthcare problems. For example, AI technologies have been used in supporting disease diagnosis, identifying disease risk factors, predicting treatment outcomes, recommending treatment, patient engagement, and healthcare administration ([Davenport and Kalakota 2019](#ch11.xhtml#ref11_6)). For some of these tasks, AI performs as well as, or even better, than humans. Most of the AI technologies that are used in healthcare are statistical methods, traditional machine learning approaches, and new deep learning techniques that have been discussed in the previous chapters of this book. These statistically-based machine learning or AI technologies use the existing EHR and other relevant healthcare data to train or fit prediction or classification models to identify the risk factors or best treatment for a disease so that the disease diagnosis can be more efficient and treatment outcomes can be improved ([Rajkomar et al. 2018](#ch11.xhtml#ref11_15), [Shimabukuro et al. 2017](#ch11.xhtml#ref11_16)). In particular, the deep learning approach was shown to perform better than humans in identifying patterns from medical images for disease diagnosis ([Fakoor et al. 2013](#ch11.xhtml#ref11_7), [Vial et al. 2018](#ch11.xhtml#ref11_17)). Other AI technologies that we have not discussed in this book include the traditional rule-based clinical expert systems and natural language processing (NLP) techniques. In particular, both semantic and statistical or machine learning-based (including deep learning) NLP techniques are very useful to process the unstructured EHR data such as the clinical notes, clinical practice guidelines (CPG), medical literature and documents. The NLP is still an active research field ([Mehta and Devarakonda 2018](#ch11.xhtml#ref11_12)). The AI technologies could also be employed to automate the EHR data extraction, cleaning, processing, preparation and analysis. In addition, the NLP techniques could be used to automatically generate the analysis report. We expect that this will greatly speed up our effort to translate the EHR Big Data into knowledge and healthcare benefits. However, due to many implementation barriers, ethical issues and regulation problems, there still is a long way to go before AI technologies can replace clinicians and human caregivers.

## ![image](images/inline1_1.jpg)  
11.2 Post-Research Practice

The ultimate goal of biomedical and health science research is to improve the health of people. In previous chapters, we presented detailed methodologies for each of the steps of the research procedure (see [Chapter 1, Section 1.2](#ch11.xhtml#sec11_2)) based on the EHR data. From a research perspective, the research cycle is concluded after the results are published. However, we believe that this is not the end of EHR research since the research results must be evaluated to determine their practical benefit on patient care and improvement in health. In order to further promote the practical use of the real-world evidence based on the EHR data, we propose the following “post-research practice”:

 

1.  Design a randomized trial for further validation and confirmation if feasible: Randomized controlled trials (RCT) are still the gold standard in evaluating the effect of a treatment, medication and other interventions. If it is feasible, ideally, the results and conclusions derived from the retrospective EHR data should be validated and confirmed by a well designed, randomized and prospective clinical trial. The EHR data and data analysis results can be used to inform the design of the RCTs and some methodologies may need to be developed for this purpose. We also recognize that sometimes it is not practical or feasible to perform a clinical trial due to many reasons such as ethical issues, difficulty in patient recruitment, and implementation barriers.
    
2.  Design and develop user-friendly tools for implementation and practice: To allow clinicians and patient caregivers to use the research results based on the EHR data in clinical practice and to improve patient care outcomes, it is necessary to develop a user-friendly tool or clinical decision support (CDS) system to implement the analysis, modeling and prediction algorithms for clinical practice. This may also require the involvement of professional software tool developers in order to make the tools follow the industry standard.
    
3.  Deployment and practical use: After the software tool or clinical decision support system is developed, one may need to find a hospital or clinic to test the software tool or CDS system in a practical setting.
    
4.  User feedback and further evaluation: User feedback and evaluation need to be collected to further improve the design of the software tool or CDS system. Any bugs or problems can be fixed based on the user’s feedback. If necessary, a formal randomized trial may be designed and performed to evaluate the effectiveness of the CDS system in terms of clinical outcomes.
    
5.  Iterative improvement: The above research and post-research practice procedures may need to be iteratively updated so that continuous improvement can be done during clinical practice.
    

 

We expect that the results and clinical evidence derived from EHR data can be quickly translated into impactful benefits for patient care. In order to shorten the time delay from research to clinical practice, a close collaboration among researchers, clinical investigators, caregivers, industry partners, and government regulatory agencies is required.

## ![image](images/inline1_1.jpg)  
11.3 Summary

The use of EHR data for research and scientific discoveries is still in its infancy. It is not only very challenging from a privacy perspective to make the data available for scientific research, many data integration and statistical methodology issues still need to be addressed. State-of-the-art data science approaches, computational algorithms and AI technologies are also necessary to harness and translate the EHR Big Data into accessible practical knowledge. Many investigators, including the authors of this book, are actively developing these cutting-edge methods and technologies to meet the needs and challenges in interrogating the EHR data.

### ![image](images/inline1_1.jpg)  
References

Baowaly, Mrinal Kanti, Chia-Ching Lin, Chao-Lin Liu, and Kuan-Ta Chen. 2019. Synthesizing electronic health records using improved generative adversarial networks. *Journal of the American Medical Informatics Association* **26**((3)), 228–241.

 Battey, Heather, Jianqing Fan, Han Liu, Junwei Lu, and Ziwei Zhu. 2018. Distributed testing and estimation under sparse high dimensional models. *Annals of Statistics* **46**((3)), 1352.

Buczak, Anna L., Steven Babin, and Linda Moniz. 2010. Data-driven approach for creating synthetic electronic medical records. *BMC Medical Informatics and Decision Making* **10**((1)), 59.

Chen, Xueying, and Min-ge Xie. 2014. A split-and-conquer approach for analysis of extraordinarily large data. *Statistica Sinica*: 24(2014), 1655–1684.

Choi, Edward, Siddharth Biswal, Bradley Malin, Jon Duke, Walter F. Stewart, and Jimeng Sun. 2017. Generating multi-label discrete patient records using generative adversarial networks. *arXiv preprint arXiv:1703.06490*.

Davenport, Thomas, and Ravi Kalakota. 2019. The potential for artificial intelligence in healthcare. *Future Healthcare Journal* **6**((2)), 94.

Fakoor, Rasool, Faisal Ladhak, Azade Nazi, and Manfred Huber. 2013. Using deep learning to enhance cancer diagnosis and classification. Proceedings of the International Conference on Machine Learning.

Fan, Jianqing, Dong Wang, Kaizheng Wang, and Ziwei Zhu. 2019. Distributed estimation of principal eigenspaces. *Annals of Statistics* **47**((6)), 3009.

Jordan, Michael I., Jason D. Lee, and Yun Yang. 2019. Communication-efficient distributed statistical inference. *Journal of the American Statistical Association* **114**((526)), 668–681.

Lee, Jason D., Yuekai Sun, Qiang Liu, and Jonathan E. Taylor. 2015. Communication-efficient sparse regression: a one-shot approach. *arXiv preprint arXiv:1503.04337*.

McLachlan, Scott, Kudakwashe Dube, and Thomas Gallagher. 2016. Using the caremap with health incidents statistics for generating the realistic synthetic electronic healthcare record. 2016 IEEE International Conference on Healthcare Informatics (ICHI).

Mehta, Neil, and Murthy V. Devarakonda. 2018. Machine learning, natural language programming, and electronic health records: The next step in the artificial intelligence journey? *Journal of Allergy and Clinical Immunology* **141**((6)), 2019–2021. e1.

Moniz, Linda, Anna L. Buczak, Lang Hung, Steven Babin, Michael Dorko, and Joseph Lombardo. 2009. Construction and validation of synthetic electronic medical records. *Online Journal of Public Health Informatics* **1** (1).

Neiswanger, Willie, Chong Wang, and Eric Xing. 2013. Asymptotically exact, embarrassingly parallel MCMC. *arXiv preprint arXiv:1311.4780*.

Rajkomar, Alvin, Eyal Oren, Kai Chen, Andrew M. Dai, Nissan Hajaj, Michaela Hardt, Peter J. Liu, Xiaobing Liu, Jake Marcus, and Mimi Sun. 2018. Scalable and accurate deep learning with electronic health records. *NPJ Digital Medicine* **1**((1)), 18.

Shimabukuro, David W., Christopher W. Barton, Mitchell D. Feldman, Samson J. Mataraso, and Ritankar Das. 2017. Effect of a machine learning-based severe sepsis prediction algorithm on patient survival and hospital length of stay: a randomised clinical trial. *BMJ Open Respiratory Research* **4**((1)), e000234.

Vial, Alanna, David Stirling, Matthew Field, Montserrat Ros, Christian H. Ritz, Martin G. Carolan, Lois C. Holloway, and Andrew Alexis Miller. 2018. The role of deep learning and radiomic feature extraction in cancer-specific predictive modelling: a review. ” 7(3), 803–816.

 Walonoski, Jason, Mark Kramer, Joseph Nichols, Andre Quina, Chris Moesel, Dylan Hall, Carlton Duffett, Kudakwashe Dube, Thomas Gallagher, and Scott McLachlan. 2018. Synthea: An approach, method, and software mechanism for generating synthetic patients and the synthetic electronic health care record. *Journal of the American Medical Informatics Association* **25**((3)), 230–238.

Wang, Xiangyu, and David B. Dunson. 2013. Parallelizing MCMC via Weierstrass sampler. *arXiv preprint arXiv:1312.4605*.

Zhang, Yuchen, John C. Duchi, and Martin J. Wainwright. 2013. Communication-efficient algorithms for statistical optimization. *The Journal of Machine Learning Research* **14**((1)), 3321–3363.

# ![image](images/inline1_2.jpg)

# [Index](#contents.xhtml)  
               

**A**

Adaptive LASSO [244](#ch08.xhtml#page_244)

Adversarial learning confounders [210](#ch07.xhtml#page_210)–[211](#ch07.xhtml#page_211)

Algorithms

decision-tree [274](#ch10.xhtml#page_274), [*275*](#ch10.xhtml#page_275)

ID3 [274](#ch10.xhtml#page_274)–[275](#ch10.xhtml#page_275), [*275*](#ch10.xhtml#page_275)

support vector machine [279](#ch10.xhtml#page_279)–[281](#ch10.xhtml#page_281)

Allscripts Veradigm [**59**](#ch03.xhtml#table3_1)–[**60**](#ch03.xhtml#table3_1)

AlphaGo [255](#ch09.xhtml#page_255)

Amazon Web Services [25](#ch02.xhtml#page_25)

Amplity Health RealHealth Data [**60**](#ch03.xhtml#table3_1)

Analysis of variance [227](#ch08.xhtml#page_227)

ANN see [Artificial neural network](#index.xhtml#ie16)

ANOVA see [Analysis of variance](#index.xhtml#ie8)

Apache Hadoop [62](#ch03.xhtml#page_62)

Area under the curve [228](#ch08.xhtml#page_228), [245](#ch08.xhtml#page_245), [289](#ch10.xhtml#fig10_11), [*290*](#ch10.xhtml#fig10_13)

ARMA see [Autoregressive moving-average model](#index.xhtml#ie23)

AR model see [Autoregression model](#index.xhtml#ie22)

Artificial intelligence [297](#ch11.xhtml#page_297)

Artificial neural network [253](#ch09.xhtml#page_253)–[254](#ch09.xhtml#page_254), [*254*](#ch09.xhtml#page_254)

Attribute dependency rules [84](#ch04.xhtml#page_84)

Attribute domain constraints [83](#ch04.xhtml#page_83)

AUC see [Area under the curve](#index.xhtml#ie12)

Autoencoders [159](#ch06.xhtml#page_159)–[160](#ch06.xhtml#page_160)

AutoML [262](#ch09.xhtml#page_262)

Autoregression model [238](#ch08.xhtml#page_238)

Autoregressive moving-average model [238](#ch08.xhtml#page_238)

Auto-sklearn [285](#ch10.xhtml#page_285)–[286](#ch10.xhtml#page_286)

AWS see [Amazon Web Services](#index.xhtml#ie6)

**B**

Backpropagation [254](#ch09.xhtml#page_254)

Backward stepwise selection [240](#ch08.xhtml#page_240)–[241](#ch08.xhtml#page_241)

Bayesian latent phenotyping [66](#ch03.xhtml#page_66)

Big Data

description of [1](#ch01.xhtml#page_1)–[2](#ch01.xhtml#page_2), [298](#ch11.xhtml#page_298)

in healthcare [53](#ch03.xhtml#page_53)

research on [20](#ch02.xhtml#page_20), [26](#ch02.xhtml#page_26)

value of [19](#ch02.xhtml#page_19)

Binary treatments, propensity scoring for [179](#ch07.xhtml#page_179)

Biomarkers [207](#ch07.xhtml#page_207)–[208](#ch07.xhtml#page_208)

Boosting, gradient [277](#ch10.xhtml#page_277)–[278](#ch10.xhtml#page_278)

Box plot [*102*](#ch04.xhtml#page_102)

Braden scale [**103**](#ch04.xhtml#page_103)

BSBC [**56**](#ch03.xhtml#table3_1)

**C**

Calendar plot [*102*](#ch04.xhtml#page_102)

Caret [283](#ch10.xhtml#page_283)–[285](#ch10.xhtml#page_285)

Case-control study [6](#ch01.xhtml#page_6)

Case report [6](#ch01.xhtml#page_6)

Case study [6](#ch01.xhtml#page_6)

Causal inference

counterfactuals framework for [185](#ch07.xhtml#page_185)

framework in [176](#ch07.xhtml#page_176)–[178](#ch07.xhtml#page_178)

propensity scoring see [Propensity scoring](#index.xhtml#ie346)

reasons for [175](#ch07.xhtml#page_175)

Rubin causal model [176](#ch07.xhtml#page_176)

statistical methods for [176](#ch07.xhtml#page_176)

targeted maximum likelihood estimation in [212](#ch07.xhtml#page_212)–[214](#ch07.xhtml#page_214)

Causality, framework in [176](#ch07.xhtml#page_176)–[178](#ch07.xhtml#page_178)

CBOW see [Continuous bag of words model](#index.xhtml#ie72)

CDM see [Common Data Model](#index.xhtml#ie64)

CDS system see [Clinical decision support system](#index.xhtml#ie53)

Centralized Version Control system [24](#ch02.xhtml#page_24)

Cerner Health Facts database [3](#ch01.xhtml#page_3), [14](#ch01.xhtml#page_14), [54](#ch03.xhtml#page_54), [69](#ch03.xhtml#page_69)

CGANs see [Conditional generative adversarial networks](#index.xhtml#ie68)

Chi-square test [231](#ch08.xhtml#page_231)–[232](#ch08.xhtml#page_232)

CLAMP [66](#ch03.xhtml#page_66)

Classical machine learning [255](#ch09.xhtml#page_255)

Clinical event table [100](#ch04.xhtml#page_100)–[104](#ch04.xhtml#page_104)

Clinical decision support system [295](#ch11.xhtml#page_295), [298](#ch11.xhtml#page_298)–[299](#ch11.xhtml#page_299)

Clinical event table [149](#ch06.xhtml#page_149)

Clinical practice guidelines [296](#ch11.xhtml#page_296)

Clinical Practice Research Datalink [**58**](#ch03.xhtml#table3_1)

Clinical professionals [27](#ch02.xhtml#page_27)

Clustering [119](#ch05.xhtml#page_119)–[120](#ch05.xhtml#page_120)

CNNs see [Convolutional networks](#index.xhtml#ie74)

Coding conventions [25](#ch02.xhtml#page_25)

Coding systems [28](#ch02.xhtml#page_28)

Cohort refining [134](#ch05.xhtml#page_134)–[135](#ch05.xhtml#page_135), [*135*](#ch05.xhtml#page_135)

Cohort study [6](#ch01.xhtml#page_6), [231](#ch08.xhtml#page_231)

Common Data Model [8](#ch01.xhtml#page_8), [297](#ch11.xhtml#page_297)

Comparison groups [132](#ch05.xhtml#page_132)–[134](#ch05.xhtml#page_134)

Complex data sets, propensity scoring for [181](#ch07.xhtml#page_181)–[182](#ch07.xhtml#page_182)

Concave function-based regularization methods [243](#ch08.xhtml#page_243)–[244](#ch08.xhtml#page_244)

Conditional generative adversarial networks

description of [196](#ch07.xhtml#page_196)–[197](#ch07.xhtml#page_197)

imputation block [197](#ch07.xhtml#page_197)–[200](#ch07.xhtml#page_200)

individual treatment effects estimation using [197](#ch07.xhtml#page_197)–[203](#ch07.xhtml#page_203)

MisCGANs [204](#ch07.xhtml#page_204)–[207](#ch07.xhtml#page_207)

Confounders

adversarial learning [210](#ch07.xhtml#page_210)–[211](#ch07.xhtml#page_211)

description of [208](#ch07.xhtml#page_208)

individual treatment effects and [212](#ch07.xhtml#page_212)

latent [209](#ch07.xhtml#page_209)–[210](#ch07.xhtml#page_210)

Confounding factors [1](#ch01.xhtml#page_1)

Contingency tables [*230*](#ch08.xhtml#page_230), [230](#ch08.xhtml#page_230)–[231](#ch08.xhtml#page_231)

Continuous bag of words model [121](#ch05.xhtml#page_121)

Conversion map [89](#ch04.xhtml#page_89)–[94](#ch04.xhtml#page_94)

Convolutional networks [257](#ch09.xhtml#page_257), [*257*](#ch09.xhtml#page_257), [259](#ch09.xhtml#page_259)

Counterfactuals

conditional generative adversarial networks for production of [196](#ch07.xhtml#page_196)–[197](#ch07.xhtml#page_197)

framework of [185](#ch07.xhtml#page_185)

generative adversarial networks for production of [196](#ch07.xhtml#page_196)–[197](#ch07.xhtml#page_197)

MisGAN for imputation of [205](#ch07.xhtml#page_205)–[207](#ch07.xhtml#page_207)

Covariance analysis [189](#ch07.xhtml#page_189)

Covariance function [239](#ch08.xhtml#page_239)

Cox proportional hazard regression model [236](#ch08.xhtml#page_236)

CPGs see [Clinical practice guidelines](#index.xhtml#ie55)

CPRD [**58**](#ch03.xhtml#table3_1)–[**59**](#ch03.xhtml#table3_1)

CPT codes [105](#ch04.xhtml#page_105)

Cross-sectional study [6](#ch01.xhtml#page_6)

CVS see [Centralized Version Control system](#index.xhtml#ie46)

**D**

Data

dimensionality of [119](#ch05.xhtml#page_119), [163](#ch06.xhtml#page_163), [227](#ch08.xhtml#page_227)

handling of [*27*](#ch02.xhtml#page_27)

incomplete [151](#ch06.xhtml#page_151)

inconsistency during entry of [89](#ch04.xhtml#page_89)

intentional manipulation of [23](#ch02.xhtml#page_23)

leakage of [136](#ch05.xhtml#page_136)–[137](#ch05.xhtml#page_137)

loss of [22](#ch02.xhtml#page_22)–[23](#ch02.xhtml#page_23)

missing see [Missing data](#index.xhtml#ie271)

multidisciplinary team involvement in [14](#ch01.xhtml#page_14)–[15](#ch01.xhtml#page_15)

patient privacy issues [296](#ch11.xhtml#page_296)

real-world [1](#ch01.xhtml#page_1)–[4](#ch01.xhtml#page_4)

security of [296](#ch11.xhtml#page_296)

sensitivity of [26](#ch02.xhtml#page_26)

sharing of [14](#ch01.xhtml#page_14), [297](#ch11.xhtml#page_297)

statistical challenges for [225](#ch08.xhtml#page_225)

statistical models for see [Statistical models](#index.xhtml#ie411)

tidy [113](#ch05.xhtml#page_113)–[115](#ch05.xhtml#page_115)

unintentional manipulation of [23](#ch02.xhtml#page_23)

variables in [255](#ch09.xhtml#page_255)

Data analysis

challenges associated with [175](#ch07.xhtml#page_175), [255](#ch09.xhtml#page_255)

exploratory see [Exploratory data analysis](#index.xhtml#ie148)

Gaussian process for [239](#ch08.xhtml#page_239)–[240](#ch08.xhtml#page_240)

generalized linear models for [226](#ch08.xhtml#page_226)

mixed-effect models for [237](#ch08.xhtml#page_237)

statistical models used in [226](#ch08.xhtml#page_226)

survival models for [236](#ch08.xhtml#page_236)–[237](#ch08.xhtml#page_237)

time series analysis [238](#ch08.xhtml#page_238)–[240](#ch08.xhtml#page_240)

variables for [175](#ch07.xhtml#page_175)

Data analysis, modeling, and prediction [11](#ch01.xhtml#page_11)–[12](#ch01.xhtml#page_12)

Data analysis report [12](#ch01.xhtml#page_12), [25](#ch02.xhtml#page_25)–[26](#ch02.xhtml#page_26)

Database

distributed [62](#ch03.xhtml#page_62)

EHR/EMR see [EHR/EMR database](#index.xhtml#ie132)

relational [61](#ch03.xhtml#page_61)–[62](#ch03.xhtml#page_62)

Data cleaning

data quality assessment [83](#ch04.xhtml#page_83)–[84](#ch04.xhtml#page_84)

definition of [79](#ch04.xhtml#page_79)

description of [9](#ch01.xhtml#page_9)–[11](#ch01.xhtml#page_11), [106](#ch04.xhtml#page_106)

documenting of [107](#ch04.xhtml#page_107)

efficiency in [107](#ch04.xhtml#page_107)

of EHR data [79](#ch04.xhtml#page_79)

for EHR datasets [82](#ch04.xhtml#page_82)–[83](#ch04.xhtml#page_83)

focusing during [107](#ch04.xhtml#page_107)

methods and tools for [80](#ch04.xhtml#page_80)–[84](#ch04.xhtml#page_84)

procedure table [105](#ch04.xhtml#page_105)–[106](#ch04.xhtml#page_106)

project-specific [112](#ch05.xhtml#page_112)

solution for [107](#ch04.xhtml#page_107)

Data exploration and visualization [225](#ch08.xhtml#page_225), [228](#ch08.xhtml#page_228)–[229](#ch08.xhtml#page_229)

Data extraction

description of [8](#ch01.xhtml#page_8)–[9](#ch01.xhtml#page_9)

inclusion/extraction criteria for [62](#ch03.xhtml#page_62)–[63](#ch03.xhtml#page_63)

phenotyping [64](#ch03.xhtml#page_64)–[67](#ch03.xhtml#page_67)

pitfalls in [74](#ch03.xhtml#page_74)–[75](#ch03.xhtml#page_75)

in Subarachnoid Hemorrhage Project [70](#ch03.xhtml#page_70)–[75](#ch03.xhtml#page_75)

Data extraction report

structure of [68](#ch03.xhtml#page_68)–[69](#ch03.xhtml#page_69)

for Subarachnoid Hemorrhage Project [73](#ch03.xhtml#page_73)–[74](#ch03.xhtml#page_74)

Data extraction summary statistics report [7](#ch01.xhtml#page_7)

Data formats [227](#ch08.xhtml#page_227)

Data management

definition of [53](#ch03.xhtml#page_53)

elements of [53](#ch03.xhtml#page_53)

technological advances in [53](#ch03.xhtml#page_53)

Data management framework

data structure in [*43*](#ch02.xhtml#fig2_9)

example of [31](#ch02.xhtml#page_31)–[48](#ch02.xhtml#page_48)

file management in [38](#ch02.xhtml#page_38)–[41](#ch02.xhtml#page_41)

folder management in [32](#ch02.xhtml#page_32)–[38](#ch02.xhtml#page_38)

user management in [41](#ch02.xhtml#page_41)–[42](#ch02.xhtml#page_42)

Data managers [27](#ch02.xhtml#page_27)

Data modeling

description of [11](#ch01.xhtml#page_11)–[12](#ch01.xhtml#page_12)

generalized linear models for [226](#ch08.xhtml#page_226)

Data preparation see also [Data pre-processing and preparation](#index.xhtml#ie100)

for analysis purposes [137](#ch05.xhtml#page_137)–[140](#ch05.xhtml#page_140), [144](#ch05.xhtml#page_144)

cohort refining [134](#ch05.xhtml#page_134)–[135](#ch05.xhtml#page_135), [*135*](#ch05.xhtml#page_135)

comparison groups in [132](#ch05.xhtml#page_132)–[134](#ch05.xhtml#page_134)

cross-sectional format [137](#ch05.xhtml#page_137)

definition of [112](#ch05.xhtml#page_112)–[113](#ch05.xhtml#page_113)

description of [10](#ch01.xhtml#page_10)–[11](#ch01.xhtml#page_11)

encounters [126](#ch05.xhtml#page_126), [129](#ch05.xhtml#page_129)–[132](#ch05.xhtml#page_132)

encounter time interval [126](#ch05.xhtml#page_126)–[129](#ch05.xhtml#page_129)

endpoint for [123](#ch05.xhtml#page_123)–[124](#ch05.xhtml#page_124)

errors [140](#ch05.xhtml#page_140)–[142](#ch05.xhtml#page_142)

leakage detection [136](#ch05.xhtml#page_136)–[137](#ch05.xhtml#page_137)

longitudinal format [137](#ch05.xhtml#page_137)

medical record timestamps [124](#ch05.xhtml#page_124)–[126](#ch05.xhtml#page_126)

outcome for [123](#ch05.xhtml#page_123)–[124](#ch05.xhtml#page_124)

summary of [144](#ch05.xhtml#page_144)–[145](#ch05.xhtml#page_145)

Data pre-processing and preparation

definition of [111](#ch05.xhtml#page_111), [112](#ch05.xhtml#page_112)

derived variables [115](#ch05.xhtml#page_115)–[119](#ch05.xhtml#page_119)

description of [10](#ch01.xhtml#page_10)

dimension reduction [119](#ch05.xhtml#page_119)–[122](#ch05.xhtml#page_122)

errors [140](#ch05.xhtml#page_140)–[142](#ch05.xhtml#page_142)

iterative completion of [111](#ch05.xhtml#page_111), [*112*](#ch05.xhtml#page_112)

missing data imputation [122](#ch05.xhtml#page_122)

project-specific nature of [112](#ch05.xhtml#page_112)

report [142](#ch05.xhtml#page_142)–[144](#ch05.xhtml#page_144)

summary of [144](#ch05.xhtml#page_144)–[145](#ch05.xhtml#page_145)

tidy data [113](#ch05.xhtml#page_113)–[115](#ch05.xhtml#page_115)

variable encoding [113](#ch05.xhtml#page_113)–[115](#ch05.xhtml#page_115)

Data processing [10](#ch01.xhtml#page_10)

Data quality assessment [83](#ch04.xhtml#page_83)–[84](#ch04.xhtml#page_84)

Data queries [8](#ch01.xhtml#page_8)–[9](#ch01.xhtml#page_9), [61](#ch03.xhtml#page_61)–[62](#ch03.xhtml#page_62), [70](#ch03.xhtml#page_70)

Data results

dissemination of [13](#ch01.xhtml#page_13)

interpretation of [13](#ch01.xhtml#page_13)

publication of [13](#ch01.xhtml#page_13)

validation of [13](#ch01.xhtml#page_13)

Data scientists [27](#ch02.xhtml#page_27)

Data splitting [284](#ch10.xhtml#page_284)

Data wranglers [81](#ch04.xhtml#page_81)

Date/time validation algorithm [*96*](#ch04.xhtml#fig4_4)

Decision tree [274](#ch10.xhtml#page_274)–[276](#ch10.xhtml#page_276), [*275*](#ch10.xhtml#page_275)

Decision tree learning [157](#ch06.xhtml#page_157)

Deconfounders, in treatment effects estimation [208](#ch07.xhtml#page_208)–[212](#ch07.xhtml#page_212)

Deep convolutional networks [257](#ch09.xhtml#page_257), [259](#ch09.xhtml#page_259)

Deep learning

convolutional networks [257](#ch09.xhtml#page_257), [259](#ch09.xhtml#page_259)

definition of [253](#ch09.xhtml#page_253)

description of [121](#ch05.xhtml#page_121)–[122](#ch05.xhtml#page_122)

flexibility of [269](#ch09.xhtml#page_269)

limitations of [256](#ch09.xhtml#page_256), [269](#ch09.xhtml#page_269)

methods of [257](#ch09.xhtml#page_257)–[259](#ch09.xhtml#page_259)

in missing data imputation [159](#ch06.xhtml#page_159)–[162](#ch06.xhtml#page_162)

multilayer perceptron [254](#ch09.xhtml#page_254)–[255](#ch09.xhtml#page_255), [257](#ch09.xhtml#page_257)

reinforcement learning [255](#ch09.xhtml#page_255)

software tools [259](#ch09.xhtml#page_259)–[260](#ch09.xhtml#page_260)

supervised learning [255](#ch09.xhtml#page_255)

unsupervised learning [255](#ch09.xhtml#page_255)

Demographics table [85](#ch04.xhtml#page_85)–[88](#ch04.xhtml#page_88)

Derived variables [115](#ch05.xhtml#page_115)–[119](#ch05.xhtml#page_119)

Descriptive statistics [95](#ch04.xhtml#page_95)

Diagnosis and Medication table [104](#ch04.xhtml#page_104)

Dimensionality of data [119](#ch05.xhtml#page_119), [163](#ch06.xhtml#page_163), [227](#ch08.xhtml#page_227)

Dimension reduction [119](#ch05.xhtml#page_119)–[122](#ch05.xhtml#page_122)

Distributed database systems [62](#ch03.xhtml#page_62)

Distributed machine learning community [278](#ch10.xhtml#page_278)

Distributed Version Control System [24](#ch02.xhtml#page_24)

Divide-and-conquer method [228](#ch08.xhtml#page_228), [245](#ch08.xhtml#page_245)

DMLC see [Distributed machine learning community](#index.xhtml#ie122)

Document management [25](#ch02.xhtml#page_25)–[26](#ch02.xhtml#page_26)

Dummy encoding [121](#ch05.xhtml#page_121)

DVCS see [Distributed Version Control System](#index.xhtml#ie123)

**E**

Earth mover's distance [216](#ch07.xhtml#page_216)

eClinicalWorks [**60**](#ch03.xhtml#table3_1)

EDA see [Exploratory data analysis](#index.xhtml#ie148)

EHR/EMR database

client event table [100](#ch04.xhtml#page_100)–[104](#ch04.xhtml#page_104)

construction of [61](#ch03.xhtml#page_61)

data analysis, modeling, and prediction [11](#ch01.xhtml#page_11)–[12](#ch01.xhtml#page_12)

data cleaning [9](#ch01.xhtml#page_9)–[11](#ch01.xhtml#page_11)

data extraction [8](#ch01.xhtml#page_8)–[9](#ch01.xhtml#page_9)

data preparation [10](#ch01.xhtml#page_10)–[11](#ch01.xhtml#page_11)

data pre-processing [10](#ch01.xhtml#page_10)

data processing [10](#ch01.xhtml#page_10)

data queries [8](#ch01.xhtml#page_8)–[9](#ch01.xhtml#page_9), [61](#ch03.xhtml#page_61)–[62](#ch03.xhtml#page_62)

demographics table [85](#ch04.xhtml#page_85)–[88](#ch04.xhtml#page_88)

design of [61](#ch03.xhtml#page_61)

Diagnosis and Medication table [104](#ch04.xhtml#page_104)

encounters in [*129*](#ch05.xhtml#page_129), [129](#ch05.xhtml#page_129)–[132](#ch05.xhtml#page_132)

errors in [8](#ch01.xhtml#page_8)–[9](#ch01.xhtml#page_9), [12](#ch01.xhtml#page_12), [74](#ch03.xhtml#page_74)–[75](#ch03.xhtml#page_75), [84](#ch04.xhtml#page_84)–[106](#ch04.xhtml#page_106)

implementation of [61](#ch03.xhtml#page_61)

lab table [88](#ch04.xhtml#page_88)–[100](#ch04.xhtml#page_100)

maintenance of [61](#ch03.xhtml#page_61)

overview of [4](#ch01.xhtml#page_4)–[5](#ch01.xhtml#page_5)

procedure table [104](#ch04.xhtml#page_104)–[106](#ch04.xhtml#page_106)

querying of [8](#ch01.xhtml#page_8)

for research and scientific discoveries [4](#ch01.xhtml#page_4)–[13](#ch01.xhtml#page_13), [79](#ch04.xhtml#page_79)

research questions [5](#ch01.xhtml#page_5)–[7](#ch01.xhtml#page_7)

sample size [6](#ch01.xhtml#page_6)

structure of [106](#ch04.xhtml#page_106)

for Subarachnoid Hemorrhage Project [69](#ch03.xhtml#page_69)–[70](#ch03.xhtml#page_70)

EHRs see [Electronic health records](#index.xhtml#ie135)

Elastic Net method [244](#ch08.xhtml#page_244)

Electronic health records

billing and management uses of [256](#ch09.xhtml#page_256)

clinical information in [175](#ch07.xhtml#page_175)

data see [Data](#index.xhtml#ie84)

database see [EHR/EMR database](#index.xhtml#ie132)

definition of [vii](#preface.xhtml#page_vii), [4](#ch01.xhtml#page_4), [54](#ch03.xhtml#page_54)

demographic information in [175](#ch07.xhtml#page_175)

phenotyping approaches [9](#ch01.xhtml#page_9)

project management see [Project management](#index.xhtml#ie343)

simulation systems [296](#ch11.xhtml#page_296)

Electronic medical records

database see [EHR/EMR database](#index.xhtml#ie132)

definition of [vii](#preface.xhtml#page_vii), [4](#ch01.xhtml#page_4)

Electronic phenotyping [67](#ch03.xhtml#page_67)

Embedding [121](#ch05.xhtml#page_121)–[122](#ch05.xhtml#page_122), [*122*](#ch05.xhtml#page_122)

eMERGE [65](#ch03.xhtml#page_65), [67](#ch03.xhtml#page_67)

EM method see [Expectation-maximization method](#index.xhtml#ie147)

EMRs see [Electronic medical records](#index.xhtml#ie136)

Encounters [126](#ch05.xhtml#page_126), [129](#ch05.xhtml#page_129)–[132](#ch05.xhtml#page_132)

Encounter time interval [126](#ch05.xhtml#page_126)–[129](#ch05.xhtml#page_129)

Entropy [274](#ch10.xhtml#page_274), [276](#ch10.xhtml#page_276)

Epic [**55**](#ch03.xhtml#table3_1)–[**56**](#ch03.xhtml#table3_1)

Errors

database [8](#ch01.xhtml#page_8)–[9](#ch01.xhtml#page_9), [12](#ch01.xhtml#page_12)

data preparation [140](#ch05.xhtml#page_140)–[142](#ch05.xhtml#page_142)

data pre-processing [140](#ch05.xhtml#page_140)–[142](#ch05.xhtml#page_142)

Expectation-maximization method [122](#ch05.xhtml#page_122), [149](#ch06.xhtml#page_149)

Exploratory data analysis

data exploration and visualization using [225](#ch08.xhtml#page_225), [228](#ch08.xhtml#page_228)–[229](#ch08.xhtml#page_229)

definition of [228](#ch08.xhtml#page_228)

description of [136](#ch05.xhtml#page_136)

graphs used in [229](#ch08.xhtml#page_229)

software used in [229](#ch08.xhtml#page_229)

summary statistics report [229](#ch08.xhtml#page_229)

Extremely randomized tree [277](#ch10.xhtml#page_277)

**F**

Feature selection via supervised model construction [66](#ch03.xhtml#page_66)

Feedback [299](#ch11.xhtml#page_299)

FGD see [Functional gradient descent](#index.xhtml#ie158)

Files

naming conventions for [23](#ch02.xhtml#page_23)–[24](#ch02.xhtml#page_24), [32](#ch02.xhtml#page_32)–[33](#ch02.xhtml#page_33), [38](#ch02.xhtml#page_38)–[40](#ch02.xhtml#page_40)

sharing of [31](#ch02.xhtml#page_31)

submission form for [49](#ch02.xhtml#page_49)–[50](#ch02.xhtml#page_50)

Version Control [24](#ch02.xhtml#page_24)–[25](#ch02.xhtml#page_25)

Fisher exact test [232](#ch08.xhtml#page_232)

Folders

Admin [35](#ch02.xhtml#page_35)–[36](#ch02.xhtml#page_36)

CBD\_HS [34](#ch02.xhtml#page_34)–[35](#ch02.xhtml#page_35)

group [36](#ch02.xhtml#page_36)

naming of [32](#ch02.xhtml#page_32)

project [36](#ch02.xhtml#page_36)–[37](#ch02.xhtml#page_37)

Public\_Folder [35](#ch02.xhtml#page_35)

structure of [33](#ch02.xhtml#page_33)–[38](#ch02.xhtml#page_38), [40](#ch02.xhtml#page_40)–[41](#ch02.xhtml#page_41)

Sub\_Project [37](#ch02.xhtml#page_37)–[38](#ch02.xhtml#page_38)

Useful\_Info [36](#ch02.xhtml#page_36)

Forward stepwise selection [240](#ch08.xhtml#page_240)–[241](#ch08.xhtml#page_241)

FSSMC see [Feature selection via supervised model construction](#index.xhtml#ie150)

Functional gradient descent [277](#ch10.xhtml#page_277)

**G**

GAIN see [Generative adversarial imputation nets](#index.xhtml#ie174)

GANs see [Generative adversarial networks](#index.xhtml#ie175)

Gantt chart [29](#ch02.xhtml#page_29), [*30*](#ch02.xhtml#page_30)

Gated recurrent unit [258](#ch09.xhtml#page_258)

Gaussian process [239](#ch08.xhtml#page_239)–[240](#ch08.xhtml#page_240)

GBM see [Gradient boosting machine](#index.xhtml#ie183)

GBMs see [Gradient boosting methods](#index.xhtml#ie184)

GBRT see [Gradient boosted regression tree](#index.xhtml#ie181)

G-computation [213](#ch07.xhtml#page_213)

GEE see [Generalized estimating equations](#index.xhtml#ie169)

Generalized estimating equations [151](#ch06.xhtml#page_151), [227](#ch08.xhtml#page_227)

Generalized least square estimator [189](#ch07.xhtml#page_189)–[192](#ch07.xhtml#page_192)

Generalized linear mixed models [151](#ch06.xhtml#page_151)

Generalized linear models

data analysis uses of [226](#ch08.xhtml#page_226)

definition of [234](#ch08.xhtml#page_234)

link function in [234](#ch08.xhtml#page_234)

as logistic regression model [234](#ch08.xhtml#page_234)–[235](#ch08.xhtml#page_235)

Generalized propensity scores [179](#ch07.xhtml#page_179)

Generative adversarial imputation nets [162](#ch06.xhtml#page_162)

Generative adversarial networks

conditional see [Conditional generative adversarial networks](#index.xhtml#ie68)

data synthesis uses of [296](#ch11.xhtml#page_296)

description of [161](#ch06.xhtml#page_161)–[162](#ch06.xhtml#page_162)

electronic health report applications of [258](#ch09.xhtml#page_258)

framework of [*258*](#ch09.xhtml#page_258)

individual treatment effects estimation using [196](#ch07.xhtml#page_196)

Wasserstein [203](#ch07.xhtml#page_203)–[204](#ch07.xhtml#page_204), [214](#ch07.xhtml#page_214)–[219](#ch07.xhtml#page_219)

Gini impurity [276](#ch10.xhtml#page_276)

Git [24](#ch02.xhtml#page_24)

GLMM see [Generalized linear mixed models](#index.xhtml#ie171)

GLMs see [Generalized linear models](#index.xhtml#ie172)

GPS see [Generalized propensity scores](#index.xhtml#ie173)

Gradient boosted regression tree [278](#ch10.xhtml#page_278)

Gradient boosting [277](#ch10.xhtml#page_277)–[278](#ch10.xhtml#page_278)

Gradient boosting machine [278](#ch10.xhtml#page_278)

Gradient boosting methods [179](#ch07.xhtml#page_179), [181](#ch07.xhtml#page_181)

Grouped LASSO [244](#ch08.xhtml#page_244)

GRU see [Gated recurrent unit](#index.xhtml#ie162)

**H**

Hadoop distributed file system [62](#ch03.xhtml#page_62)

Hard-SVM [280](#ch10.xhtml#page_280)

Hardware failure [23](#ch02.xhtml#page_23)

Hazard rate [236](#ch08.xhtml#page_236)

HCPCS level II codes [105](#ch04.xhtml#page_105)

HCUP [**57**](#ch03.xhtml#table3_1)–[**58**](#ch03.xhtml#table3_1)

Health administrator [28](#ch02.xhtml#page_28)

Healthcare data

as Big Data [53](#ch03.xhtml#page_53)

providers of [**55**](#ch03.xhtml#table3_1)–[**60**](#ch03.xhtml#table3_1)

Health Insurance Portability and Accountability Act of 1996 [24](#ch02.xhtml#page_24), [80](#ch04.xhtml#page_80)

Heart failure prediction for hypertension patients, recurrent neural network for [263](#ch09.xhtml#page_263)–[269](#ch09.xhtml#page_269)

High-throughput phenotyping [65](#ch03.xhtml#page_65)

HIPAA see [Health Insurance Portability and Accountability Act of 1996](#index.xhtml#ie195)

Histogram [*102*](#ch04.xhtml#page_102)

Historical data [12](#ch01.xhtml#page_12)

Historical data rules [84](#ch04.xhtml#page_84)

H2O [260](#ch09.xhtml#page_260)–[261](#ch09.xhtml#page_261), [281](#ch10.xhtml#page_281)–[283](#ch10.xhtml#page_283), [**282**](#ch10.xhtml#page_282), [289](#ch10.xhtml#fig10_11)

Hypergeometric test [232](#ch08.xhtml#page_232)–[234](#ch08.xhtml#page_234)

**I**

ICD-9 [105](#ch04.xhtml#page_105), [119](#ch05.xhtml#page_119)

ICD-10 [82](#ch04.xhtml#page_82), [104](#ch04.xhtml#page_104)–[105](#ch04.xhtml#page_105)

ICD-9-CM [119](#ch05.xhtml#page_119)–[120](#ch05.xhtml#page_120), [137](#ch05.xhtml#page_137)

ID3 [274](#ch10.xhtml#page_274)–[275](#ch10.xhtml#page_275), [*275*](#ch10.xhtml#page_275)

Imputation block [197](#ch07.xhtml#page_197)–[200](#ch07.xhtml#page_200)

Individual treatment effects

adversarial learning inference network for estimation of [*211*](#ch07.xhtml#page_211)

conditional generative adversarial networks estimation of [197](#ch07.xhtml#page_197)–[203](#ch07.xhtml#page_203)

confounders and [212](#ch07.xhtml#page_212)

generative adversarial network estimation of [196](#ch07.xhtml#page_196)

MisCGANs for estimation of [204](#ch07.xhtml#page_204)–[207](#ch07.xhtml#page_207)

in survival analysis [201](#ch07.xhtml#page_201)–[203](#ch07.xhtml#page_203)

Wasserstein generative adversarial networks estimation of [203](#ch07.xhtml#page_203)–[204](#ch07.xhtml#page_204)

Information technology support [27](#ch02.xhtml#page_27)

Instrumental variables analysis

covariance analysis [189](#ch07.xhtml#page_189)

framework for [187](#ch07.xhtml#page_187)–[188](#ch07.xhtml#page_188)

generalized least square estimator [189](#ch07.xhtml#page_189)–[192](#ch07.xhtml#page_192)

two-stage least squares methods for [188](#ch07.xhtml#page_188)–[196](#ch07.xhtml#page_196)

*IntelliClean,* [80](#ch04.xhtml#page_80)

International Classification of Diseases [3](#ch01.xhtml#page_3), [64](#ch03.xhtml#page_64), [70](#ch03.xhtml#page_70)

InterSystems [**56**](#ch03.xhtml#table3_1)

Inverse probability weighting [178](#ch07.xhtml#page_178)

IPW see [Inverse probability weighting](#index.xhtml#ie215)

IQVIA [**55**](#ch03.xhtml#table3_1)

Iterative regression imputation [154](#ch06.xhtml#page_154)–[155](#ch06.xhtml#page_155)

Iterative SIS [243](#ch08.xhtml#page_243), [245](#ch08.xhtml#page_245)

ITEs see [Individual treatment effects](#index.xhtml#ie209)

IT support see [Information technology support](#index.xhtml#ie210)

**J**

Jenson-Shannon divergence [216](#ch07.xhtml#page_216)

JMDC Claims Database [**59**](#ch03.xhtml#table3_1)

Jupyter [73](#ch03.xhtml#page_73)–[74](#ch03.xhtml#page_74)

**K**

Kantorovich-Rubinstein Duality theory [217](#ch07.xhtml#page_217)

Kernel functions [281](#ch10.xhtml#page_281)

Kullback-Leibler divergence [216](#ch07.xhtml#page_216)

**L**

Lab table [88](#ch04.xhtml#page_88)–[100](#ch04.xhtml#page_100)

Lagged values [238](#ch08.xhtml#page_238)

LASSO [207](#ch07.xhtml#page_207)–[208](#ch07.xhtml#page_208), [228](#ch08.xhtml#page_228), [240](#ch08.xhtml#page_240), [244](#ch08.xhtml#page_244), [247](#ch08.xhtml#page_247)

Last observation carried forward method [152](#ch06.xhtml#page_151)–[153](#ch06.xhtml#page_153)

Latent confounders [209](#ch07.xhtml#page_209)–[210](#ch07.xhtml#page_210)

Leakage of data [136](#ch05.xhtml#page_136)–[137](#ch05.xhtml#page_137)

Least absolute shrinkage and selection operator see [LASSO](#index.xhtml#ie230)

Limestone [66](#ch03.xhtml#page_66)

Linear perceptron [255](#ch09.xhtml#page_255)

Lipschitz constraints [217](#ch07.xhtml#page_217)

LOCF method see [Last observation carried forward method](#index.xhtml#ie231)

Logistic regression model [234](#ch08.xhtml#page_234)–[235](#ch08.xhtml#page_235), [244](#ch08.xhtml#page_244)

Logit model [235](#ch08.xhtml#page_235)

Log-linear regression [236](#ch08.xhtml#page_236)

Long short-term memory [258](#ch09.xhtml#page_258)

L1-penalized logistic regression model [136](#ch05.xhtml#page_136)

LSTM see [Long short-term memory](#index.xhtml#ie242)

**M**

Machine learning

Auto-sklearn [285](#ch10.xhtml#page_285)–[286](#ch10.xhtml#page_286)

Caret [283](#ch10.xhtml#page_283)–[285](#ch10.xhtml#page_285)

classical methods of [255](#ch09.xhtml#page_255)

definition of [159](#ch06.xhtml#page_159), [273](#ch10.xhtml#page_273)

extremely randomized tree [277](#ch10.xhtml#page_277)

gradient boosting [277](#ch10.xhtml#page_277)–[278](#ch10.xhtml#page_278)

H2O [260](#ch09.xhtml#page_260)–[261](#ch09.xhtml#page_261), [281](#ch10.xhtml#page_281)–[283](#ch10.xhtml#page_283), [**282**](#ch10.xhtml#page_282), [289](#ch10.xhtml#fig10_11)

methods of [274](#ch10.xhtml#page_274)–[281](#ch10.xhtml#page_281)

non-parametric [181](#ch07.xhtml#page_181)

overview of [273](#ch10.xhtml#page_273)–[274](#ch10.xhtml#page_274)

for phenotyping [65](#ch03.xhtml#page_65)–[67](#ch03.xhtml#page_67)

propensity models [182](#ch07.xhtml#page_182)

random forest method of [274](#ch10.xhtml#page_274)–[276](#ch10.xhtml#page_276)

software tools for [281](#ch10.xhtml#page_281)–[286](#ch10.xhtml#page_286)

subarachnoid hemorrhage project application of [286](#ch10.xhtml#page_286)–[291](#ch10.xhtml#page_291)

support vector machine [279](#ch10.xhtml#page_279)–[281](#ch10.xhtml#page_281)

TPOT [285](#ch10.xhtml#page_285), [291](#ch10.xhtml#page_291)

transfer learning [162](#ch06.xhtml#page_162)

tree-based methods [157](#ch06.xhtml#page_157)–[159](#ch06.xhtml#page_159)

XgBoost [278](#ch10.xhtml#page_278)–[279](#ch10.xhtml#page_279), [289](#ch10.xhtml#fig10_11), [291](#ch10.xhtml#page_291)

Malware [23](#ch02.xhtml#page_23)

MA model see [Moving average model](#index.xhtml#ie279)

Management

data see [Data management](#index.xhtml#ie95)

project management versus [20](#ch02.xhtml#page_20)–[21](#ch02.xhtml#page_21)

task [29](#ch02.xhtml#page_29), [*30*](#ch02.xhtml#page_30)

team/people [26](#ch02.xhtml#page_26)–[30](#ch02.xhtml#page_30)

MAR see [Missing at random](#index.xhtml#ie269)

Masking operator [205](#ch07.xhtml#page_205)

Maximum likelihood estimator [214](#ch07.xhtml#page_214)–[215](#ch07.xhtml#page_215)

MCAR see [Missing completely at random](#index.xhtml#ie270)

McKesson Technology Solutions [**55**](#ch03.xhtml#table3_1)

MCMC method [149](#ch06.xhtml#page_149)

MCP see [Minimax convex penalty](#index.xhtml#ie267)

Mean squared error [245](#ch08.xhtml#page_245)

Mediation analysis

assumptions in [187](#ch07.xhtml#page_187)

description of [185](#ch07.xhtml#page_185)

difference method [186](#ch07.xhtml#page_186)

product method [185](#ch07.xhtml#page_185)–[186](#ch07.xhtml#page_186)

Medical professionals [27](#ch02.xhtml#page_27)

Medical record timestamps [124](#ch05.xhtml#page_124)–[126](#ch05.xhtml#page_126)

MEDITECH [**59**](#ch03.xhtml#table3_1)

MedMining—Geisinger Health [**60**](#ch03.xhtml#table3_1)

Med2vec [122](#ch05.xhtml#page_122)

MICE see [Multiple imputation by chained equation](#index.xhtml#ie285)

Microsoft Project [30](#ch02.xhtml#page_30)

Microsoft Teams [31](#ch02.xhtml#page_31)

MIMIC [14](#ch01.xhtml#page_14)

Minimax convex penalty [243](#ch08.xhtml#page_243)

MisCGANs [204](#ch07.xhtml#page_204)–[207](#ch07.xhtml#page_207)

Missing at random [150](#ch06.xhtml#page_150)

Missing completely at random [150](#ch06.xhtml#page_150)

Missing data

mechanisms of [150](#ch06.xhtml#page_150)–[151](#ch06.xhtml#page_151)

missing completely at random [150](#ch06.xhtml#page_150)

overview of [149](#ch06.xhtml#page_149)–[150](#ch06.xhtml#page_150)

Missing data imputation

autoencoder for [159](#ch06.xhtml#page_159)–[160](#ch06.xhtml#page_160)

case study of [163](#ch06.xhtml#page_163)–[170](#ch06.xhtml#page_170)

deep learning methods in [159](#ch06.xhtml#page_159)–[162](#ch06.xhtml#page_162)

description of [122](#ch05.xhtml#page_122)

in EHR datasets [164](#ch06.xhtml#page_164)–[167](#ch06.xhtml#page_167)

generative adversarial nets for [161](#ch06.xhtml#page_161)–[162](#ch06.xhtml#page_162)

iterative regression imputation [154](#ch06.xhtml#page_154)–[155](#ch06.xhtml#page_155)

last observation carried forward method [152](#ch06.xhtml#page_151)–[153](#ch06.xhtml#page_153)

multiple imputation [153](#ch06.xhtml#page_153)–[154](#ch06.xhtml#page_154)

multiple imputation by chained equation [122](#ch05.xhtml#page_122), [155](#ch06.xhtml#page_155)–[156](#ch06.xhtml#page_156), [167](#ch06.xhtml#page_167), [169](#ch06.xhtml#page_169)

natural language processing in [160](#ch06.xhtml#page_160)–[161](#ch06.xhtml#page_161)

regression models for [155](#ch06.xhtml#page_155)

routine multivariate imputation [154](#ch06.xhtml#page_154)

single imputation [152](#ch06.xhtml#page_151), [162](#ch06.xhtml#page_162)

statistical models for [151](#ch06.xhtml#page_151)–[157](#ch06.xhtml#page_157)

summary of [170](#ch06.xhtml#page_170)–[171](#ch06.xhtml#page_171)

tree-based imputation [157](#ch06.xhtml#page_157)–[159](#ch06.xhtml#page_159)

Missing not at random [150](#ch06.xhtml#page_150)

Mixed-effect models [227](#ch08.xhtml#page_227), [237](#ch08.xhtml#page_237)

MLE see [Maximum likelihood estimator](#index.xhtml#ie251)

MLP see [Multilayer perceptron](#index.xhtml#ie283)

MNAR see [Missing not at random](#index.xhtml#ie273)

Mortality prediction, multilayer perceptron for [260](#ch09.xhtml#page_260)–[263](#ch09.xhtml#page_263)

Moving average model [238](#ch08.xhtml#page_238)

MSE see [Mean squared error](#index.xhtml#ie256)

Multicollinearity [240](#ch08.xhtml#page_240)

Multidisciplinary team

description of [14](#ch01.xhtml#page_14)–[15](#ch01.xhtml#page_15)

management of [28](#ch02.xhtml#page_28)–[29](#ch02.xhtml#page_29)

Multilayer perceptron

description of [254](#ch09.xhtml#page_254)–[255](#ch09.xhtml#page_255), [257](#ch09.xhtml#page_257)

mortality prediction applications of [260](#ch09.xhtml#page_260)–[263](#ch09.xhtml#page_263)

Multiple imputation [153](#ch06.xhtml#page_153)–[154](#ch06.xhtml#page_154)

Multiple imputation by chained equation [122](#ch05.xhtml#page_122), [155](#ch06.xhtml#page_155)–[156](#ch06.xhtml#page_156), [167](#ch06.xhtml#page_167), [169](#ch06.xhtml#page_169)

Multiple treatments, propensity scoring for [179](#ch07.xhtml#page_179)–[180](#ch07.xhtml#page_180)

**N**

Naming conventions [23](#ch02.xhtml#page_23)–[24](#ch02.xhtml#page_24)

Natural language processing [63](#ch03.xhtml#page_63), [65](#ch03.xhtml#page_65)–[66](#ch03.xhtml#page_66), [121](#ch05.xhtml#page_121), [160](#ch06.xhtml#page_160)–[161](#ch06.xhtml#page_161), [297](#ch11.xhtml#page_297)–[298](#ch11.xhtml#page_298)

NCQA [**56**](#ch03.xhtml#table3_1)

Neural networks, recurrent

description of [3](#ch01.xhtml#page_3), [66](#ch03.xhtml#page_66), [258](#ch09.xhtml#page_258), [*258*](#ch09.xhtml#page_258)

heart failure prediction for hypertension patients using [263](#ch09.xhtml#page_263)–[269](#ch09.xhtml#page_269)

Neyman-Rubin counterfactual framework of causality [176](#ch07.xhtml#page_176)

NHANES [**56**](#ch03.xhtml#table3_1)–[**57**](#ch03.xhtml#table3_1)

NLP see [Natural language processing](#index.xhtml#ie288)

Non-parametric machine learning [181](#ch07.xhtml#page_181)

Norm-based regularization methods [243](#ch08.xhtml#page_243)

**O**

Object-oriented codes [25](#ch02.xhtml#page_25)

Object-oriented programming [25](#ch02.xhtml#page_25), [48](#ch02.xhtml#page_48)

Observational Health Data Sciences and Informatics [297](#ch11.xhtml#page_297)

Observational medical outcomes partnership common data model [297](#ch11.xhtml#page_297)

Observational studies [6](#ch01.xhtml#page_6)–[7](#ch01.xhtml#page_7)

Odds ratio [235](#ch08.xhtml#page_235)

OHDSI see [Observational Health Data Sciences and Informatics](#index.xhtml#ie298)

OLAP see [Online analytical processing](#index.xhtml#ie310)

OLR see [Ordinary linear regression](#index.xhtml#ie317)

OLS see [Ordinary least squares](#index.xhtml#ie316)

OLTP see [Online transaction processing](#index.xhtml#ie311)

OMOP CDM see [Observational medical outcomes partnership common data model](#index.xhtml#ie299)

OMOP Common Data Model [8](#ch01.xhtml#page_8)

One-hot encoding [121](#ch05.xhtml#page_121)

Online analytical processing [62](#ch03.xhtml#page_62)

Online transaction processing [62](#ch03.xhtml#page_62)

OOP see [Object-oriented programming](#index.xhtml#ie297)

Optum [**55**](#ch03.xhtml#table3_1)

OR see [Odds ratio](#index.xhtml#ie301)

Ordinal treatments, propensity scoring for [180](#ch07.xhtml#page_180)–[181](#ch07.xhtml#page_181)

Ordinary least squares [240](#ch08.xhtml#page_240)

Ordinary linear regression [234](#ch08.xhtml#page_234)

Organizational chart [26](#ch02.xhtml#page_26)

Outcome variable [123](#ch05.xhtml#page_123)–[124](#ch05.xhtml#page_124)

Outliers [128](#ch05.xhtml#page_128)

**P**

Pair-wise treatment effect [178](#ch07.xhtml#page_178)

Patient privacy [296](#ch11.xhtml#page_296)

PCA see [Principal component analysis](#index.xhtml#ie336)

PCs see [Principal components](#index.xhtml#ie337)

Penalty-based variable selection methods [243](#ch08.xhtml#page_243)–[244](#ch08.xhtml#page_244)

PheKB [65](#ch03.xhtml#page_65)

Phenotyping

applications of [64](#ch03.xhtml#page_64)

description of [9](#ch01.xhtml#page_9)

electronic [67](#ch03.xhtml#page_67)

high-throughput [65](#ch03.xhtml#page_65)

hybrid methods of [67](#ch03.xhtml#page_67)

machine learning methods for [65](#ch03.xhtml#page_65)–[67](#ch03.xhtml#page_67)

methods of [**64**](#ch03.xhtml#page_64), [64](#ch03.xhtml#page_64)–[67](#ch03.xhtml#page_67)

rule-based methods of [64](#ch03.xhtml#page_64)–[65](#ch03.xhtml#page_65)

Poisson regression [236](#ch08.xhtml#page_236)

Potential outcome framework [176](#ch07.xhtml#page_176)–[178](#ch07.xhtml#page_178)

Potter's wheel [81](#ch04.xhtml#page_81)

Precision medicine [196](#ch07.xhtml#page_196)

Prediction [11](#ch01.xhtml#page_11)–[12](#ch01.xhtml#page_12)

Prediction network [211](#ch07.xhtml#page_211)

Predictive models [283](#ch10.xhtml#page_283)

PREMIER [**56**](#ch03.xhtml#table3_1)

Principal component analysis [120](#ch05.xhtml#page_120)–[121](#ch05.xhtml#page_121)

Principal components [120](#ch05.xhtml#page_120)–[121](#ch05.xhtml#page_121)

Privacy [296](#ch11.xhtml#page_296)

Procedure codes [104](#ch04.xhtml#page_104)–[105](#ch04.xhtml#page_105)

Procedure table [104](#ch04.xhtml#page_104)–[106](#ch04.xhtml#page_106)

Product method [185](#ch07.xhtml#page_185)–[186](#ch07.xhtml#page_186)

Project

definition of [20](#ch02.xhtml#page_20)

endpoint for [123](#ch05.xhtml#page_123)–[124](#ch05.xhtml#page_124)

outcome variable for [123](#ch05.xhtml#page_123)–[124](#ch05.xhtml#page_124)

resources for [29](#ch02.xhtml#page_29)

Project management

challenges of [20](#ch02.xhtml#page_20)

definition of [20](#ch02.xhtml#page_20)

goals of [21](#ch02.xhtml#page_21)–[22](#ch02.xhtml#page_22)

management versus [20](#ch02.xhtml#page_20)–[21](#ch02.xhtml#page_21)

methods used in [30](#ch02.xhtml#page_30)–[31](#ch02.xhtml#page_31)

need for [21](#ch02.xhtml#page_21)

principles of [21](#ch02.xhtml#page_21)–[22](#ch02.xhtml#page_22)

questions associated with [20](#ch02.xhtml#page_20)–[21](#ch02.xhtml#page_21)

software tools for [30](#ch02.xhtml#page_30)–[31](#ch02.xhtml#page_31)

tips for [48](#ch02.xhtml#page_48)–[49](#ch02.xhtml#page_49)

Project manager

description of [21](#ch02.xhtml#page_21)

responsibilities of [26](#ch02.xhtml#page_26)–[27](#ch02.xhtml#page_27)

task management by [29](#ch02.xhtml#page_29), [*30*](#ch02.xhtml#page_30)

Project-specific data cleaning [112](#ch05.xhtml#page_112)

Propensity scoring

for binary treatments [179](#ch07.xhtml#page_179)

for complex data sets [181](#ch07.xhtml#page_181)–[182](#ch07.xhtml#page_182)

description of [178](#ch07.xhtml#page_178)

for multiple treatments [179](#ch07.xhtml#page_179)–[180](#ch07.xhtml#page_180)

for ordinal treatments [180](#ch07.xhtml#page_180)–[181](#ch07.xhtml#page_181)

in Subarachnoid Hemorrhage Project [182](#ch07.xhtml#page_182)–[185](#ch07.xhtml#page_185)

Purposeful variable selection [241](#ch08.xhtml#page_241)–[242](#ch08.xhtml#page_242)

P-value [231](#ch08.xhtml#page_231)–[232](#ch08.xhtml#page_232)

Python codes [130](#ch05.xhtml#page_130)–[131](#ch05.xhtml#page_131), [264](#ch09.xhtml#page_264)

Pytorch [259](#ch09.xhtml#page_259)–[260](#ch09.xhtml#page_260)

**R**

Radial basis function [281](#ch10.xhtml#page_281)

Random forest [274](#ch10.xhtml#page_274)–[276](#ch10.xhtml#page_276)

Randomized clinical trials [175](#ch07.xhtml#page_175)

Randomized controlled trials [1](#ch01.xhtml#page_1)–[2](#ch01.xhtml#page_2), [298](#ch11.xhtml#page_298)

Ransomware [23](#ch02.xhtml#page_23)

RBF see [Radial basis function](#index.xhtml#ie351)

RCM see [Rubin causal model](#index.xhtml#ie385)

RCS see [Revision Control System](#index.xhtml#ie375)

RCTs see [Randomized controlled trials](#index.xhtml#ie354)

Readme file [25](#ch02.xhtml#page_25)–[26](#ch02.xhtml#page_26)

Real-world data study [7](#ch01.xhtml#page_7)

Receiver operator characteristic curve [228](#ch08.xhtml#page_228)

Reconstruction network [211](#ch07.xhtml#page_211)

Recurrent neural networks

description of [3](#ch01.xhtml#page_3), [66](#ch03.xhtml#page_66), [258](#ch09.xhtml#page_258), [*258*](#ch09.xhtml#page_258)

heart failure prediction for hypertension patients using [263](#ch09.xhtml#page_263)–[269](#ch09.xhtml#page_269)

Regression models [186](#ch07.xhtml#page_186), [234](#ch08.xhtml#page_234)–[235](#ch08.xhtml#page_235)

rEHR [82](#ch04.xhtml#page_82)

Reinforcement learning [255](#ch09.xhtml#page_255)

Relational database systems [61](#ch03.xhtml#page_61)–[62](#ch03.xhtml#page_62)

Relational integrity rules [83](#ch04.xhtml#page_83)

Relative risk [233](#ch08.xhtml#page_233)–[234](#ch08.xhtml#page_234)

Reports

data extraction [68](#ch03.xhtml#page_68)–[69](#ch03.xhtml#page_69), [73](#ch03.xhtml#page_73)–[74](#ch03.xhtml#page_74)

data pre-processing and preparation [142](#ch05.xhtml#page_142)–[144](#ch05.xhtml#page_144)

Research

criteria for [19](#ch02.xhtml#page_19)

database application for [4](#ch01.xhtml#page_4)–[13](#ch01.xhtml#page_13), [79](#ch04.xhtml#page_79)

design of [298](#ch11.xhtml#page_298)

future [295](#ch11.xhtml#page_295)–[298](#ch11.xhtml#page_298)

goal of [298](#ch11.xhtml#page_298)

project in [22](#ch02.xhtml#page_22)

sub-project in [22](#ch02.xhtml#page_22)

Research questions [5](#ch01.xhtml#page_5)–[7](#ch01.xhtml#page_7)

Residual sum of squares [241](#ch08.xhtml#page_241)

Revision Control System [24](#ch02.xhtml#page_24)

Ridge regression [244](#ch08.xhtml#page_244)

R Markdown [73](#ch03.xhtml#page_73)

RMSE see [Root mean square error](#index.xhtml#ie381)

RNN see [Recurrent Neural Networks](#index.xhtml#ie364)

ROC see [Receiver operator characteristic curve](#index.xhtml#ie362)

Root mean square error [161](#ch06.xhtml#page_161)

Routine multivariate imputation [154](#ch06.xhtml#page_154)

RR see [Relative risk](#index.xhtml#ie370)

RSS see [Residual sum of squares](#index.xhtml#ie374)

Rubin causal model [176](#ch07.xhtml#page_176)

Rubin’s formula [153](#ch06.xhtml#page_153)

 S

Sample size [6](#ch01.xhtml#page_6), [139](#ch05.xhtml#page_139), [228](#ch08.xhtml#page_228)

SCAD see [Smoothly clipped absolute deviation](#index.xhtml#ie400)

Scientific discoveries, database application for [4](#ch01.xhtml#page_4)–[13](#ch01.xhtml#page_13)

SEER [**56**](#ch03.xhtml#table3_1)

Sensitivity [245](#ch08.xhtml#page_245)–[246](#ch08.xhtml#page_246)

Shrinkage methods [242](#ch08.xhtml#page_242)

Sigmoid function [254](#ch09.xhtml#page_254)

Simulation systems [296](#ch11.xhtml#page_296)

SIS [242](#ch08.xhtml#page_242)–[243](#ch08.xhtml#page_243), see [Sure independence screening](#index.xhtml#ie418)

Skip-gram [121](#ch05.xhtml#page_121)

Slack [30](#ch02.xhtml#page_30)–[31](#ch02.xhtml#page_31)

SMC see [Structural matrix completion](#index.xhtml#ie414)

SMD see [Standardized mean difference](#index.xhtml#ie408)

Smoothly clipped absolute deviation [243](#ch08.xhtml#page_243)

Social interaction [29](#ch02.xhtml#page_29)

“Soft shrinkage” [244](#ch08.xhtml#page_244)

Soft-SVM [280](#ch10.xhtml#page_280)

Software

deep learning [259](#ch09.xhtml#page_259)–[260](#ch09.xhtml#page_260)

exploratory data analysis [229](#ch08.xhtml#page_229)

machine learning [281](#ch10.xhtml#page_281)–[286](#ch10.xhtml#page_286)

project management [30](#ch02.xhtml#page_30)–[31](#ch02.xhtml#page_31)

Specificity [245](#ch08.xhtml#page_245)–[246](#ch08.xhtml#page_246)

SQL databases [62](#ch03.xhtml#page_62)

Staff turnover [26](#ch02.xhtml#page_26)

Standardized mean difference [183](#ch07.xhtml#page_183)

State-dependent rules [84](#ch04.xhtml#page_84)

Statista [19](#ch02.xhtml#page_19)

Statistical models

chi-square test [231](#ch08.xhtml#page_231)–[232](#ch08.xhtml#page_232)

contingency tables [*230*](#ch08.xhtml#page_230), [230](#ch08.xhtml#page_230)–[231](#ch08.xhtml#page_231)

hypergeometric test [232](#ch08.xhtml#page_232)–[234](#ch08.xhtml#page_234)

Statisticians [27](#ch02.xhtml#page_27)

Stepwise variable selection [240](#ch08.xhtml#page_240)–[241](#ch08.xhtml#page_241)

Structural matrix completion [122](#ch05.xhtml#page_122)

Subarachnoid Hemorrhage Project [246](#ch08.xhtml#page_246)–[247](#ch08.xhtml#page_247),

cohort identification [70](#ch03.xhtml#page_70)–[73](#ch03.xhtml#page_73)

cohort refining for [135](#ch05.xhtml#page_135), [*135*](#ch05.xhtml#page_135)

comparison groups in [133](#ch05.xhtml#page_133)

data extraction [70](#ch03.xhtml#page_70)–[75](#ch03.xhtml#page_75)

data extraction report for [73](#ch03.xhtml#page_73)–[74](#ch03.xhtml#page_74)

EHR database design and construction [69](#ch03.xhtml#page_69)–[70](#ch03.xhtml#page_70)

machine learning application to [286](#ch10.xhtml#page_286)–[291](#ch10.xhtml#page_291)

outliers in [128](#ch05.xhtml#page_128)

prediction model for [286](#ch10.xhtml#page_286)–[287](#ch10.xhtml#page_287)

propensity scoring in [182](#ch07.xhtml#page_182)–[185](#ch07.xhtml#page_185)

timestamps in [125](#ch05.xhtml#page_125)

Supervised learning [255](#ch09.xhtml#page_255), [273](#ch10.xhtml#page_273)

Support vector machine [279](#ch10.xhtml#page_279)–[281](#ch10.xhtml#page_281)

Sure independence screening [227](#ch08.xhtml#page_227)–[228](#ch08.xhtml#page_228)

Survival analysis

components of [226](#ch08.xhtml#page_226)

data in [202](#ch07.xhtml#page_202)–[203](#ch07.xhtml#page_203)

individual treatment effects in [201](#ch07.xhtml#page_201)–[203](#ch07.xhtml#page_203)

limitations of [226](#ch08.xhtml#page_226)

models for [236](#ch08.xhtml#page_236)–[237](#ch08.xhtml#page_237)

Survival function [236](#ch08.xhtml#page_236)

SVM see [Support vector machine](#index.xhtml#ie417)

Syntax [160](#ch06.xhtml#page_160)

“Synthea” [296](#ch11.xhtml#page_296)

**T**

Targeted maximum likelihood estimation [212](#ch07.xhtml#page_212)–[214](#ch07.xhtml#page_214), [*213*](#ch07.xhtml#page_213)

Task management [29](#ch02.xhtml#page_29), [*30*](#ch02.xhtml#page_30)

Team leader [26](#ch02.xhtml#page_26)–[27](#ch02.xhtml#page_27)

Team/people

management of [26](#ch02.xhtml#page_26)–[30](#ch02.xhtml#page_30)

members of [26](#ch02.xhtml#page_26)–[28](#ch02.xhtml#page_28)

multidisciplinary [14](#ch01.xhtml#page_14)–[15](#ch01.xhtml#page_15), [28](#ch02.xhtml#page_28)–[29](#ch02.xhtml#page_29)

organizational chart for [26](#ch02.xhtml#page_26)

TensorFlow [259](#ch09.xhtml#page_259)–[260](#ch09.xhtml#page_260)

THIN Database [**60**](#ch03.xhtml#table3_1)

Tidy data [113](#ch05.xhtml#page_113)–[115](#ch05.xhtml#page_115)

Time series analysis [238](#ch08.xhtml#page_238)–[240](#ch08.xhtml#page_240)

Timestamps [124](#ch05.xhtml#page_124)–[126](#ch05.xhtml#page_126), [227](#ch08.xhtml#page_227)

TMLE see [Targeted maximum likelihood estimation](#index.xhtml#ie424)

TPOT [285](#ch10.xhtml#page_285), [291](#ch10.xhtml#page_291)

Transfer learning [162](#ch06.xhtml#page_162)

Treatment

binary, propensity scoring for [179](#ch07.xhtml#page_179)

multiple, propensity scoring for [179](#ch07.xhtml#page_179)–[180](#ch07.xhtml#page_180)

Treatment effects

pair-wise [178](#ch07.xhtml#page_178)

randomized clinical trial of [175](#ch07.xhtml#page_175)

Treatment effects estimation

deconfounders in [208](#ch07.xhtml#page_208)–[212](#ch07.xhtml#page_212)

individual see [Individual treatment effects](#index.xhtml#ie209)

instrumental variables for see [Instrumental variables analysis](#index.xhtml#ie211)

Tree [157](#ch06.xhtml#page_157)–[159](#ch06.xhtml#page_159)

Tree-based pipeline optimization tool see [TPOT](#index.xhtml#ie434)

Truven [**55**](#ch03.xhtml#table3_1)

Two-by-two contingency tables [231](#ch08.xhtml#page_231)

Two-stage least squares methods [188](#ch07.xhtml#page_188)–[196](#ch07.xhtml#page_196)

**U**

UKBioBank [**58**](#ch03.xhtml#table3_1), [295](#ch11.xhtml#page_295)–[296](#ch11.xhtml#page_296)

Unsupervised learning [66](#ch03.xhtml#page_66), [255](#ch09.xhtml#page_255)

**V**

Validation [245](#ch08.xhtml#page_245)–[246](#ch08.xhtml#page_246)

Variable encoding [113](#ch05.xhtml#page_113)–[115](#ch05.xhtml#page_115)

Variable grouping [119](#ch05.xhtml#page_119)–[120](#ch05.xhtml#page_120)

Variable selection

methods of [240](#ch08.xhtml#page_240)–[244](#ch08.xhtml#page_244)

penalty-based methods [243](#ch08.xhtml#page_243)–[244](#ch08.xhtml#page_244)

purposeful [241](#ch08.xhtml#page_241)–[242](#ch08.xhtml#page_242)

SIS [242](#ch08.xhtml#page_242)–[243](#ch08.xhtml#page_243)

stepwise [240](#ch08.xhtml#page_240)–[241](#ch08.xhtml#page_241)

Variation autoencoder [188](#ch07.xhtml#page_188)

VCS see [Version Control system](#index.xhtml#ie454)

Venn diagram [*101*](#ch04.xhtml#page_101)

Version Control [24](#ch02.xhtml#page_24)–[25](#ch02.xhtml#page_25)

Version Control system [24](#ch02.xhtml#page_24)–[25](#ch02.xhtml#page_25)

Virus [23](#ch02.xhtml#page_23)

**W**

Wald test [231](#ch08.xhtml#page_231)

Wasserstein distance [216](#ch07.xhtml#page_216), [218](#ch07.xhtml#page_218)

Wasserstein generative adversarial networks [203](#ch07.xhtml#page_203)–[204](#ch07.xhtml#page_204), [214](#ch07.xhtml#page_214)–[219](#ch07.xhtml#page_219)

Weighted least square methods [191](#ch07.xhtml#page_191)

WGANs see [Wasserstein generative adversarial networks](#index.xhtml#ie458)

Wikipedia [20](#ch02.xhtml#page_20)

**X**

XgBoost [278](#ch10.xhtml#page_278)–[279](#ch10.xhtml#page_279), [289](#ch10.xhtml#fig10_11), [291](#ch10.xhtml#page_291)