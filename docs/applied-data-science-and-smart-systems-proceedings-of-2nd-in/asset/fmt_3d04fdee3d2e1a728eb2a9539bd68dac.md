
The research aims to identify the algorithms and techniques that have been applied to the identification of heart disease. Since there are more and more occurrences of heart disease every day, it is important and difficult to anticipate any prospective problems. This diagnosis is a difficult task that demands precision and effectiveness. The early detection of cardiovascular diseases depends on heart sound analysis. Practically speaking, the advancement of computer-based heart sound analysis is appealing. This paper is the survey of different algorithms and approaches that can be used to find heart disease and there can be various attributes for the same like speed, accuracy. The suggested method focuses on automatically classifying phonocardiogram (PCG) data after removing noise using a convolution neural network in order to lessen the need on skilled medical professionals for heart sound detection. Algorithms that are compared in this paper are support vector machine (SVM), convolutional neural network (CNN) with and without augmentation. Because of their ability to analyze images accurately, CNN have quickly attracted the interest of researchers and medical professionals. In order to diagnose cardiovascular disease, this study sought to design a system that combines various machine learning techniques, such as K-nearest Neighbor, Naive Byes, linear regression, decision tree, Alex-Net, ensemble learning and random forest.

Hence this paper gives a relative study of numerous approaches that were used to classify and detect cardiac diseases.

Keywords: Cardiac diseases, SVM, Naïve-Bayes, Alex-Net, CNN with and without augmentation

Introduction

The management and retrieval of implicit, previously unknown, or known data files that may be important is called machine learning (ML). Machine learning is a complex and broad field, and its applications and evolution are continuous. Machine learning uses various classes of supervised, unsupervised, and relational learning to predict and evaluate the accuracy of given data. Today’s cardiovascular disorders include a wide range of conditions that could harm your heart. In year 2019, a total of 393.11 million individuals worldwide pass away from cardiovascular disease, according to the World Health Organization ([Tang et al., 2018](#ch45.xhtml#ref45_2)). It is the main reason why adults die. By examining a medical history of different person belonging to different demographic Location, technique used in the paper can identify who is most likely to be diagnosed with a heart condition ([Son et al., 2018](#ch45.xhtml#ref45_7)). It can assist in diagnosing disease with fewer medical tests and efficient treatments in order to appropriately treat patients. It can be used to recognize someone displaying any heart disease symptoms, such as chest pain or high blood pressure ([Figure 45.1](#ch45.xhtml#fig45_1)).

![Figure 45.1 2022 leading cause of death](images/fig45_1_C.jpg)

[Figure 45.1 2022 leading cause of death](#ch45.xhtml#R_fig45_1)

Heart diseases also known as cardiovascular diseases describe a range of conditions that can majorly affect the heart and they are:

*   Diseases related to blood vessels

*   Congenital heart effects Cardiac arrhythmias

*   Diseases of heart valves

*   Diseases of heart muscle

*   Infection in heart

The type of cardiac issue we have determines the heart disease symptom. Until we experience a heart attack, stroke, heart failure, or angina, we may not be identified with coronary artery disease. One type of heart disease, coronary artery disease (CAD), is characterized by the provision of oxygen and blood flow to the heart. Low blood flow to the heart is the primary cause of angina and heart attacks. Two different types of components are greatly impacted by cardiac ailments. Smoking, high blood pressure, high cholesterol, obesity, bad diet, diabetics, depression, and stress are among the altered factors. The second is constant risk variables, such as age, gender, genetics, and race. Various survey findings stated that heart illnesses cannot be identified just on their symptoms.

The numerous hospitals, medical facilities, and an organization generate and process a vast amount of data. The information cannot be used in a specific way, and the crucial information can be processed and managed in a clinical decision support system in the future. The hidden features in the data may be overlooked by the doctors when analyzing it. Unwanted biases and incorrect disease classification are the results. The cost of medical care and the standard of care given to patients may be impacted by this. Therefore, we must create a productive system for reducing human mistake and raising patient care quality. This is possible by fusing computer decision support systems with medical decision support systems ([Figures 45.2](#ch45.xhtml#fig45_2) and [45.3](#ch45.xhtml#fig45_3)).

![Figure 45.2 Number of deaths by cause, World 2019](images/fig45_2_C.jpg)

[Figure 45.2 Number of deaths by cause, World 2019](#ch45.xhtml#R_fig45_2)

![Figure 45.3 Share of total disease burden by cause, World 2019](images/fig45_3_C.jpg)

[Figure 45.3 Share of total disease burden by cause, World 2019](#ch45.xhtml#R_fig45_3)

Cardiac diseases are serious and need to be accurately recognized at an early stage utilizing routine auscultation tests. Heart auscultation is a crucial component of a heart examination used in medicine to detect early-stage cardiac disorders. Cardiac auscultation is a technique for listening and analyzing to heart sounds ([Baghel et al., 2020](#ch45.xhtml#ref45_1)). Human cardiac auscultations are examined with a stethoscope. A traditional stethoscope is used in clinical settings to examine the health of a human heart. It is a simple, effective method that also costs nothing computationally, but understanding and interpreting heart sounds requires medical training (Leatham, 1975).

Clinical interpretation of the cardiac auscultations may only be done by a qualified medical specialist. We will use ML-based automatic classification system based on heart sounds to diagnose cardiac disorders.

Computerized heart sound recording is known as a phonocardiogram, or PCG. phonocardiography (PCG). PCG is a non-invasive, cost-effective method of recording heart impulses.

A number of cardiovascular disease (CVD) signals, such as mitral stenosis (MS) aortic stenosis (AS) mitral regurgitation (MR) and mitral valve prolapse (MVP), can be diagnosed using PCG signals.

These PCG signals are shown visually in five different forms in the following example in [Figure 45.4](#ch45.xhtml#fig45_4).

![Figure 45.4 Utilizing a phonogram (Baghel et al., 2020) signals from the current CVD classes. (a) Aortic stenosis (AS), (b) Mitral regurgitation (MR), (c) Mitral stenosis (MS), (d) Mitral valve prolapse (MVP) and (e) Normal](images/fig45_4_C.jpg)

[Figure 45.4 Utilizing a phonogram (Baghel et al., 2020) signals from the current CVD classes. (a) Aortic stenosis (AS), (b) Mitral regurgitation (MR), (c) Mitral stenosis (MS), (d) Mitral valve prolapse (MVP) and (e) Normal](#ch45.xhtml#R_fig45_4)

The rest of the article is organized as follows: The related work in the field of cardiac diseases. Followed by conclusion and future work.

Related work in the field of cardiac diseases

In this section we define the objective and technique used, and accuracy achieved.

In paper by [Baghel et al., (2020](#ch45.xhtml#ref45_1)), convolutional neural network also knows as CNN model is used in the proposed system because of its excellent accuracy and robustness in autonomously diagnosing cardiac diseases from heart sounds. In order to improve precision in a noisy environment and make the system resilient. For multi-classification and training 2124qof various cardiac conditions, the proposed method has utilized data augmentation techniques.
