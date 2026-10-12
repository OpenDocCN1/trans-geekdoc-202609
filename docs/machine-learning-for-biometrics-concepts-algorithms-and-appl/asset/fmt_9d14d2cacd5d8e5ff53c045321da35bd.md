
# Real-Time Emotion Engagement Tracking of Students using Human Biometric Emotion Intensities

Chapter “Real-Time Emotion Engagement Tracking of Students using Human Biometric Emotion Intensities” describes an automatic method to detect an absent-minded face present in a class using `FAU` (Facial Action Unit). Furthermore, this chapter covers multiple aspects of tracking, ranging from the student entering the classroom. Experimental results presented by the authors can achieve excellent results for emotion detection and recognition of students’ face images.

# Facial Identification Expression Based Attendance Monitoring and Emotion Detection—A Deep CNN Approach

Chapter “Facial Identification Expression Based Attendance Monitoring and Emotion Detection—A Deep CNN Approach” discusses the challenges of taking attendance and gauging emotions of the students in a new online classroom environment. In this chapter, with the help of advance machine learning approach, the authors introduce an automatic biometric-based attendance and facial expression recognition system.

# Contemporary Survey on Effectiveness of Machine and Deep Learning Techniques for Cyber Security

Chapter “Contemporary Survey on Effectiveness of Machine and Deep Learning Techniques for Cyber Security” reviews the practicality of biometrics in cyber security based on efficient machine learning and deep learning techniques. The objective of this survey is to provide an impact on readers to acquire the fundamental concepts of biometric authentication and identification using different machine learning techniques for cyber security systems.

# A Secure Biometric Authentication System for Smart Environment using reversible Data Hiding through Encryption Scheme

Chapter “A Secure Biometric Authentication System for Smart Environment using reversible Data Hiding through Encryption Scheme” introduces the notion of reversible data hiding (`RDH`) scheme to achieve a secure online biometric data communication. In a `RDH`-based encryption scheme, the biometric images are encrypted by hiding the important information in an image. In this chapter, the author presents a new model wherein the compressed fingerprint data is used as a secret message, and it will be embedded into the face image through a reversible data hiding-based encryption scheme. In order to maintain secure communication, encrypted image obtained after `RDH` scheme is transmitted to the cloud service provider in a secure manner.

# An Efficient and Untraceable Authentication Protocol for Cloud Based Healthcare System

Chapter “An Efficient and Untraceable Authentication Protocol for Cloud Based Healthcare System” provides `Telecare Medical Information System (TMIS)`, which is very important in pandemic situations, for example, Covid-19. In this technique, the patient’s mobile device has a major role for communicating with doctors. Furthermore, mutual authentication and key agreement scheme is required to protect vital information from any kind of mischief activities from adversaries in the insecure communication channel. In this chapter, the authors propose a biometric hashing technique to provide secure authentication and key agreement for communication between the patient and the doctor.

Finally, we hope that our readers including the graduate students, research scholars, young researchers, academicians, and industrial professionals find the contributed chapters in this book thought-provoking, and this piece of work will motivate future research breakthrough to progress further advances in the machine learning-based biometrics applications.

# Acknowledgments

The editors would like to gratefully acknowledge all of the contributors for continuous effort and timely submission of their chapters. This book would not have been feasible without the cooperation of the chapter authors. All the chapters have been reviewed for several rounds to facilitate the selection of final chapters in our book. Valuable suggestions and guidance from the reviewers helped the authors in refining individual chapters. Thanks also go to the reviewers in enhancing the quality of the chapters of this book.

The editors would like to extend gratitude to Sonnini Ruiz Yura from Elsevier for inspiration over the year. We would like to gratefully acknowledge Andrae Akeh and Judith Clarisse Punzalan (Elsevier) for their patience during the preparation of this book. In addition, we shall thank Swapna Srinivasan at Elsevier for her sincere help and patience during the final preparation of this book. Finally, we shall extend gratefulness to our family members and friends for all their support.

# Chapter 1: Machine learning approach for longitudinal face recognition of children

Vaishali H. Kamble^([a](#B9780323852098000110.xhtml#af0010)); Manisha P. Dale^([b](#B9780323852098000110.xhtml#af0015))  
^a AISSMS IOIT, Savitribai Phule Pune University, Pune, India  
^b MES College of Engineering, Savitribai Phule Pune University, Pune, India

## Abstract

The face of an individual is a popular and well-accepted biometric trait that can be used to perform identity recognition of adults as well as children. Children are the most valuable and jeopardy group in society; they should be under supervision continuously. According to a survey in India, children below 6 years of age comprise 13.12% of the total population. Security and healthcare of children is an important aspect of all countries. Automatic face recognition of children is a useful investigative tool to help identify the missing children. Though the development of the face of a child starts in the mother’s womb from 3 months, it is not proportional to the development of other parts of the body. Therefore, recognition of children below 6 year is still an open research problem. In this chapter, comparison of machine learning and deep learning techniques for the recognition of children is done. Highest recognition accuracy of 97% for the same-session and 94% for the cross-session database is achieved.

### Keywords

Biometrics; Children recognition; `CNN`; Face; Machine learning

## 1: Introduction

Face of an individual is a popular and well-accepted biometric trait that can be used to perform identity recognition of adults as well as children. Children are the most valuable and jeopardy group in society; hence they should be under supervision continuously. Security and healthcare of children is an important aspect of all countries [¹](#fn1)

Sahar Siddique studied longitudinal face recognition using the Extended Newborn Database and Children Multimodal Biometric Database. Identification accuracy achieved using `CNN` is 62.7% and 85.1% on both the databases, respectively [²](#fn2)

This chapter is presenting a machine learning and deep learning approach for face recognition of children. As per the literature review, the study of children recognition with the help of their face modality started in 2010 in India [³](#fn3)

The major contributions of the proposed work are as follows.

1.  Due to the nonavailability of reference databases for children below 6 years, the collection of longitudinal databases of children faces itself is a great challenge. In the proposed work, we have captured the face images of toddlers with the mobile camera of resolution 20 MP, with consent from their parents in two sessions. Time period between two sessions is 2 months to 1 year. In the same session, 730 images of 81 toddlers are taken. In the second session, 485 images of 48 toddlers are captured.

2.  In this chapter, we are proposing feature extraction using `PCA`, `LDA`, and `CNN` approaches on the facial images and their comparative study. In `PCA` and `LDA` approaches, we have applied different machine learning techniques for classification of subjects, such as Support Vector Machine (`SVM`), Logistic Regression (`LR`), Gaussian Naive Bayes, K-Nearest Neighbors (`KNN`), Decision Tree, and Random Forest. In `CNN`, feature extraction is done by convolution layers and classification is done by dense layers.

3.  In this work, we implemented `CNN` from basic level to optimized level. First, `CNN` is of three convolution layers for the same session and cross session. Further, the `CNN` is modified in terms of data augmentation, and six-layer convolution model is used with `L2` kernel regularization and batch normalization for enhancing the accuracy.
