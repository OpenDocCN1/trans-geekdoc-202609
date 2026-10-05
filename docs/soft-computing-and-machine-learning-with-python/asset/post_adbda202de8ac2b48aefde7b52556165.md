
114 Soft Computing Machine Learning with Python

**Table 4:** Accuracy of Neural Network Model with Two, Three, and Four Layer

| variation | accuracy |
| :--- | :--- |
| two layer with dropout (dropout rate = 0.5) | 0.9933 with loss 0.0278 |
| three layer (added layer with dense 200) with dropout (dropout rate = 0.5) | 0.9933 with loss 0.0221 |
| four layer (added layer with dense 16) with dropout (dropout rate = 0.5) | 1.0000 with loss 0.0004 |

**Table 5:** Accuracy of Neural Network Model with Truncate 50 or 100 and With Four Layers

| variation | accuracy |
| :--- | :--- |
| truncate = 50 with four layers (added layer dense 16,200) with dropout rate 0.5 | 0.9950 with loss 0.0389 |
| truncate = 100 with four layers (added layer dense 16,200) with dropout rate 0.5 | 1.0000 with loss 0.0004 |

**Table 6:** Accuracy of Neural Network Model with SVM or With Decision Tree

| variation | accuracy |
| :--- | :--- |
| with SVM | 0.9867 |
| with decision tree | 0.9933 |

**Table 7:** Accuracy of Neural Network Model with Different models

| model | accuracy |
| :--- | :--- |
| Robust logistic regression | 0.6944 |
| inductive learning algorithms (decision tree) | 0.897 |
| genetic algorithms | 0.94 |

# Bankruptcy Prediction Using Machine Learning

| model | accuracy |
| :--- | :--- |
| neural networks without dropout | 0.903 |
| SVM truncate = 100 | 0.9933 |
| Truncate = 100 with four layers (added layer dense 16,200) with dropout rate 0.5 | 1.0000 with loss 0.0004 |
| autoencoder (with decision tree) | 0.9933 |

Also, if the data sample is not big enough, especially when outnumbered by the number of features, SVM is likely to give bad performance [4]. With dropout, the time to train the neural network will be 2 to 3 times longer than training a standard neural network. An autoencoder captures as much information as possible, not necessarily the relevant information. And this can be a problem when the most relevant information only makes up a small percent of the input.

![](img/e1ab17402154bec3fa9a7873fe3ee232_140_0.png)

**Figure 5**: Neural network-loss.

![](img/e1ab17402154bec3fa9a7873fe3ee232_141_0.png)

**Figure 6:** Neural network-accuracy.

The solutions to overcome these drawbacks are yet to be found.

# Bankruptcy Prediction Using Machine Learning

# REFERENCES

- 1. Hauser, R.P. and Booth, D. (2011) Predicting Bankruptcy with Robust Logistic Regression. Journal of Data Science, 9, 565-584.
- 2. Kim, M.-J. and Han, I. (2003) The Discovery of Experts’ Rules from Qualitative Bankruptcy Data Using Genetic Algorithms. Expert Systems with Application, 25, 637-646,
- 3. Pedregosa, et al. (2011) Scikit-Learn: Machine Learning in Python. Journal of Machine Learning Research, 12, 2825-2830.
- 4. Sirvastava, N., et al. (2014) Dropout: A Simple Way to Prevent Neural Networks from Overfitting. Journal of Machine Learning Research, 15, 1929-1938.
- 5. Dev, D. (2017) Deep Learning with Hadoop. Packet Publishing, Birmingham, 52.
- 6. Nielsen, F. (2001) Neural Networks—Algorithms and Applications. https://www.mendeley.com/research-papers/neural-networks-algorithms-applications-5/
- 7. Robinson, N. (n.d.) The Disadvantages of Logistic Regression. http://classroom.synonym.com/disadvantages-logistic-regression-8574447.html
- 8. Sima, J. (1998) Introduction to Neural Networks. Technical Report No. 755.
- 9. Baldi, P. (2012) Autoencoders, Unsupervised Learning, and Deep Architectures. Journal of Machine Learning Research, 27, 37-50.
- 10. Martin, A., Uthayakumar, J. and Nadarajan, M. (2014) Qualitative Bankruptcy Data Set, UCI. https://archive.ics.uci.edu/ml/datasets/qualitative_bankruptcy

# CHAPTER 6

# PREDICTION OF SOLAR IRRADIATION USING QUANTUM SUPPORT VECTOR MACHINE LEARNING ALGORITHM

Makhamisa Senekane¹, Benedict Molibeli Taele²
¹Faculty of Computing, National University of Maseru
²Department of Physics, National University of Maseru

ABSTRACT

Machine learning is at the intersection of computing and statistics, investigates and formulates algorithms which can be used to predict solar irradiation. The main focus of this paper is on machine learning, which is known as QML.

Citation: Senekane, M. and Taele, B. (2016), “Prediction of Solar Irradiation Using Quantum Support Machine Algorithm”. Renewable Energy, 7, 293–301. doi: 10.1016/j.renene.2016.05.022

Copyright © 2016 by authors. This work is licensed under the Creative Commons Attribution International License (CC BY). http://creativecommons.org/licenses/by/4.0

# Soft Computing Machine Learning with Python

The field of Information Processing (QIP) exploits quantum mechanical concepts such as superposition and entanglement for computation and communication. There are two approaches to QML. The first approach uses classical data as input, and transforms it into quantum data so that it could be processed on a quantum computer. In essence, this approach implements classical machine learning algorithms on a quantum computer. The second approach involves making use of quantum mechanical principles in order to design machine learning algorithms for classical computers. In the work reported in this paper, we used the first approach to model solar power using quantum SVM.

**Keywords:** Quantum, Machine Learning, Support Vector Machine, Solar Irradiation

# INTRODUCTION

Machine learning is a subfield of artificial intelligence. It is a set of techniques that are used to analyze and find patterns in data. It has applications in areas such as image recognition, natural language processing, robotics, spam filtering, drug discovery, medical diagnosis, financial analysis. Machine learning algorithms can be divided into three major categories, namely supervised learning, unsupervised learning and reinforcement learning, depending on the type of data to be used.

Recently, there been a concerted effort to explore the benefits of using QIP for machine learning applications. This results in the field of Quantum Machine Learning (QML). It has also demonstrated that QML techniques provide a speedup compared to their classical counterparts.

The remainder of this paper is structured as follows. The next section provides background information on machine learning, QIP and QML. This is followed by Section 3, which discusses the design and implementation of the solar power prediction model reported in this manuscript. Section 4 provides the results and discusses the results obtained. Finally, the last section concludes this paper.

# BACKGROUND INFORMATION

- Supervised learning: makes use of both training data and data label to make predictions about future points. Examples of supervised learning algorithms are logistic regression, artificial neural networks and support vector machines.
- Unsupervised learning: makes use of training data only to make a model that maps inputs to output. As opposed to supervised learning, unsupervised learning does not make use of data label. Examples of unsupervised learning is clustering and anomaly detection algorithms.
- Reinforcement learning: uses reinforcement in the form of reward or punishment. If the algorithm succeeds in making correct predictions, it is rewarded. If it fails, it is punished.
