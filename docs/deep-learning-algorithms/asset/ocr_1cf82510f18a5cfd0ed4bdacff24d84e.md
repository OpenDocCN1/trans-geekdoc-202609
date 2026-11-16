used is deep neural networks (DNNs). DNN is also performed online for slow cortical potentials (SCP) and motion-onset visual evoked potential (MVEP) which are not commonly used. The very first research conducted and paper was published on the P300-based BCI by Cicotte et al. Two convolutional layers were constructed followed by completely connected layer. One convolutional layer has a purpose to learn spatial filters and the second one was to learn temporal filters. The model was proven better than the P300 experiment, but the SVM model had more accuracy [2].

Deep extreme learning machine is used for Slow Cortical Potentials (SCP) classifications. This technique consists of multiple layers, and the last one was Kernal ELM. However, in this project, number of units, network structure, hyperparameter, and input features were not reasoned. This did not prove to be better than multilayer ELM or standard ELM [4].

# Miscellaneous Classifiers

In order to classify more than two mental tasks, two main approaches can be used to obtain a multiclass classification function. The first approach consists in directly estimating the class using multiclass techniques such as decision trees, multilayer perceptron, naive Bayes classifiers, or k-nearest neighbors. The second approach consists of decomposing the problem into several binary classification problems.

Multiclass and multilabel approaches therefore aim to recognize more than two commands. It is therefore necessary to choose carefully the mapping between mental commands and corresponding labels. However, the errors may be possible during the classification. In particular, the set of estimated labels, sometimes, may not correspond to any class, and several classes may be at equal distances, thus causing class confusion [13].

# METHODOLOGY

Here are some methods which are discussed in the research papers for the past few years in brain-computer interface systems, as shown in Table 3.

Table 3. Summary of various methodologies in BCI systems

| Classification methods | Input EEG pattern | Features | References |
| :--- | :--- | :--- | :--- |
| Adaptive classifiers | Motor imaginary-based | Frequency band power, EEG time | [10, 12, 14] |
| Matrix and tensor classifiers | Steady-state visual evoked potentials, P300 | Frequency band power, raw data | [2, 5, 7, 15] |
| Transfer learning and deep learning | Motor imaginary-based, P300, SSVEP | EEG time points, frequency band power, raw EEG data | [2, 4, 6, 7] |
| Miscellaneous classifiers | Motor imaginary-based, P300 | Not specified | [1, 4, 15] |