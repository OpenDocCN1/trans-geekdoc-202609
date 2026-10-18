
21\. Li, M., Zhang, M., Luo, X., Yang, J., Combined long short-term memory based network employing wavelet coefficients for MI-EEG recognition. *2016 IEEE International Conference on Mechatronics and Automation*, Harbin, pp. 1971–1976, 2016.

22\. Sun, M., Wang, F., Min, T., Zang, T., Wang, Y., Prediction for High Risk Clinical Symptoms of Epilepsy Based on Deep Learning Algorithm. *IEEE Access*, 6, 77596–77605, 2018.

23\. Min, S., Lee, B., Yoon, S., Deep learning in bioinformatics. *Brief. Bioinform*. 18, 5, 851–869, 2017.

24\. Rim, B., Sung, N.J., Min, S., Hong, M., Deep Learning in Physiological Signal Data: A Survey. *Sensors*, 20, 4, 969, 2020.

25\. Ruffini, G., Ibanez, D., Castellano, M., Dubreuil-Vall, L., Soria-Frisch, A., Postuma, R., Gagnon, J.F., Montplaisir, J., Deep learning with EEG spectrograms in rapid eye movement behavior disorder. *Front. Neurol.*, 10, 806, 2019.

26\. Lee, S., Hussein, R., McKeown, M.J., A Deep Convolutional-Recurrent Neural Network Architecture for Parkinson’s Disease EEG Classification. *2019 IEEE Global Conference on Signal and Information Processing (GlobalSIP)*, Ottawa, ON, Canada, pp. 1–4, 2019.

27\. Hochreiter, S. and Schmidhuber, J., Long short term memory. *Neural Comput.*, 9, 8, 1735–1782, 1997.

28\. Tayeb, Z., Fedjaev, J., Ghaboosi, N., Richter, C., Everding, L., Qu, X., Wu, Y., Cheng, G., Conradt, J., Validating deep neural networks for online decoding of motor imagery movements from EEG signals. *Sensors*, 19, 1, 210, 2019.

29\. Tsiouris, Κ.Μ., Pezoulas, V.C., Zervakis, M., Konitsiotis, S., Koutsouris, D.D., Fotiadis, D.I., A Long Short-Term Memory deep learning network for the prediction of epileptic seizures using EEG signals. *Comput. Biol. Med.*, 99, 24–37, 2018.

30\. Hush, D., Abdallah, C., Horne, B., The recursive neural network and its applications in control theory. *Comput. Electr. Eng.*, 19, 4, 333–341, 1993. [`https://doi.org/10.1016/0045-7906(93)90054-U`](https://doi.org/10.1016/0045-7906\(93\)90054-U).

31\. Lu, Q. and Getoor, L., Link-based classification. *Proceedings of the 20th International Conference on Machine Learning*, vol. 3, pp. 496–503, 2003.

32\. Socher, R., Perelygin, A.Y., Wu, J., Chuang, J., Manning, C.D., Ng, A.Y., Potts, C., *Recursive Deep Models for Semantic Compositionality Over a Sentiment Treebank*, Emnlp, 2013.

33\. Xu, Q., Wang, Q., Xu, C., Qu, L., Collective Vertex Classification Using Recursive Neural Network, *Comput. Sci*., ArXiv, 2017.

34\. Geron, L.S., *Recursive Neural Networks for Semantic Sentence Representation*, Thesis and Dissertation, City University of New York, Sep 2018.

1.  [\*](#c07.xhtml#aut1)*Corresponding author*: [`kusumika@msrit.edu`](mailto:kusumika@msrit.edu)

# 8  

A Proposed LSTM-Based Neuromarketing Model for Consumer Emotional State Evaluation Using EEG

**Rupali Gill[\*](#c08.xhtml#raut1) and Jaiteg Singh**

*Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India*

> ***Abstract***

> 

> Contemporary marketing methodologies like television commercials, newspaper advertisements, and billboards are used by marketers to sell products because they do not understand the psychology of the consumer toward a point of purchase. The advancement in the field of technology during the last decade has allowed various researchers to measure neurophysiological parameters to predict human buying behavior for better marketing. This research study aims to bridge the gap between traditional market research and neuromarketing research. EEG-based emotional state assessment in neuromarketing has been widely used. The major gap of neuromarketing is the lack of research work in machine learning methods for predicting and classifying customer preferences. Various approaches to machine learning for predicting and classifying user preferences have been thoroughly studied. An LSTM-based approach is adopted to detect consumer emotional states by using DEAP EEG signals. The findings showed that the proposed LSTM model can be used for EEG-based emotion recognition.

> 

> ***Keywords*:** Neuromarketing, brain-computer interface, deep learning, deep neural networks, EEG (electroencephalograph)

## 8.1 Introduction

Emotions play a key role player in humans’ life, not only in interaction but also in crafting decisions. This has resulted in the phenomenal expansion of research domains like cognitive computing, human-computer interaction, sentiment analysis, user interface design, optimizing user experience, healthcare, and neuromarketing. These domains prominently compute and evaluate emotive responses to optimize results. User response can be recorded through numerous channels like subjective self-reports, facial expressions, speech analysis, physiological signals, and autonomic neurophysiological measurements. Techniques like functional Magnetic Resonance Imaging (fMRI), electroencephalography (EEG), eye gaze tracking, eye tracking using pupillometry, biometrics, and facial coding have been extensively used to understand the emotive state of respondents. This understanding is further used to trigger impulse decisions \[1, 2\]. Intrinsic connectivity within brain regions can help in predicting impulsivity of decision-making. Brain activity is considered to be a biomarker of the decision-making process \[3, 4\].

The process of decision-making involves the frontal lobe, insula, parietal lobe, and anterior cingulate cortex portions of the brain. Interactions within these regions of the brain are considered to be pivotal in the process of decision-making \[4–9\]. EEG and fMRI are best known for the unbiased natural feedback about any given stimulus and can be best used for decision assessment \[4, 10–12\]. These signals, being spontaneous and natural, cannot be faked; this makes them highly accurate in predicting decisions. EEG is easier to set up and because high temporal information recording can be used to develop a decision prediction system. In this chapter, an attempt has been made to develop an EEG and physiological information-driven intelligent framework to predict decisions. Measuring emotion states concerning any stimuli is highly demanding and may help in decision-making \[13\]. The same can be used to evaluate product designing strategies, packaging designing strategies, user interface design review, and marketing advertising assessments \[14\]. There is also a need to find advanced analytical methods for decision-making \[15, 16\]. The latest machine learning and deep learning approaches has led to the development of various predictions and planning analysis models. So, it can help us find an automatic method of extraction of features machine learning or deep learning to predict emotional state predictions \[17\].

The major research outlines of this work are as follows:

*   To study and compare machine learning techniques with deep learning techniques to predict emotional states.

*   To record the test dataset and find an appropriate feature extraction technique to be used for dimensionality reduction.

*   To propose an long short-term memory (LSTM)–based framework from emotional state evaluation using EEG
