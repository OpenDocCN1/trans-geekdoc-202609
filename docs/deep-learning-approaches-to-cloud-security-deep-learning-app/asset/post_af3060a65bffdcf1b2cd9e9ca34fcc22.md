
CNN Neural structure works on CSV information and can give better execution over classification and prediction issues. The CNN Model is implemented in a consecutive manner which incorporates the way toward the input layer with a one-dimensional convolutional layer, followed by installing the thick layer with the activation function as softmax. The CNN model is incorporated and compiled by the enhanced agent adam class with a loss count of categorical cross entropy.

## 13.6.2 Recurrent Neural Network

A Recurrent Neural Network, or RNN Model, has a successive model structure like the CNN Model. A Recurrent Neural Network, or RNN, seems as though a classical neural system is an artificial neural network. In a conventional neural system, the model delivers the output by increasing the contribution of the weight and activation function. In the RNN, data can spread in the two bearings, including from deep layers to the main layers. In this, they are nearer to the true functioning of the sensory system which is not one way. These networks have recurring connectivity, as in they keep data in memory. In principle, RNN should transmit data on schedule.

The RNN Model involves a 3-layer structure that incorporates an input layer, moderate hidden layer with forward and backward propagation functionalities, and an output layer. The RNN Model is more compatible with tabular data and gives better outcomes over classification and prediction problems and regression prediction issues. RNN Models have an inward structure of Long Short-Term Memory (LSTM) usefulness which is proficient to deal with sequence prediction issues.

The RNN Model has been actualized in a successive manner which incorporates the way towards embedding the input layer with an LSTM layer, followed by coordinating the hidden layer with the activation function as a sigmoid. On continuation with the installing procedure, a thick layer is included with the hidden layer. The RNN Model is aggregated by utilizing the optimizing agent adam class with the loss computation of cross entropy.

## 13.6.3 Multi-Layer Perception Model

The Multi-Layer Perception Model or MLP Model, also called a regression classifier, empowers changes in the input data in a non-linear structure. This non-linear structure information is taken care of to the immediate hidden layer of perception and from it they prepare the output layer. The immediate hidden layer utilizes non-linear activation functions to perform regression predictions and classification issues [16]. The MLP model is viewed as the widespread approximator since its interior structure depends on XOR functions. MLP, also called a Feed-Forward Neural Network, utilizes a regulated (supervised) learning method called back-propagation for consistent functions and preparing the model shown in Figure 13.6.

The deep neural network is a feed-forward neural network and is a super set of multilayer perception. This perceptron methodology relies upon a backpropagation algorithm which works with the predicted error propagation technique. It involves couple phases: a Feed Forward phase and a Back Forward phase.

![](img/146f9a713528a3fbc62fcad0f0d5a352_241_0.png)

![](img/146f9a713528a3fbc62fcad0f0d5a352_241_1.png)

Figure 13.6 Model of RNN [16].

In the first step, data propagates over the network to finally get the output and contrasts it with the real values to get the error. Afterward, to be minimized, the error is backpropagated to the previous layer, and then the loads are balanced in a like manner. This procedure is repeated until the error is under a predetermined threshold.

## 13.7 KDD Dataset

To analyze the performance of an anomaly IDS, we use the KDDcup99 Dataset. It was first introduced in 1999 in academic research, specially used for a concept in machine learning, IDS. The KDD cup99 dataset is generally used to analyze the IDS algorithm. It has named assault tests that are learned by impartial observing. The assault can be of any one of the types discussed in the above section 4. The names of attacks are DoS, U2R, R2L, and probe. These datasets are viewed as appropriate to predict the assault type and its data values. Generally, the analysis of the algorithm depends on their properties. The properties are ordered under 5 variables:
- 7.1 Essential Highlights: In this, we considered the type of connection established was TCP/IP or UDP.
- 7.2 Repetitive Highlights: In this, we considered the duration, type of protocol, flag, land, source byte, in destination byte, etc.
- 7.3 Content Highlights: In this, we considered the number of logins, number of failed logins, number of files created, number of access files, whether login was as a host or guest, etc.
- 7.4 Traffic Highlights: In this, we considered the features of transmission between source to destination like sender error rate, receiver error rate, same server rate, different server rate, server count, etc.
- 7.5 Host Highlights: In this, we considered the features related to host like destination host count, destination host server count, destination host same server rate, etc.

## 13.8 Evaluation

We take an experiment for estimating the presentation of our model. To assess the presentation of a model, there are a number of ways to calculate the performance metrics, for example, precision-rate, efficiency-rate, false-positive rate (FPR), and true-positive rate (TPR), True Positive (TP), False Negative (FN), False Positive (FP), and True Negative (TN).

- True-positive Rate is the ratio when an actual attack happens and intrusion detection gives an alarm.
  \( TPR = \frac{TP}{(TP + FN)} \)

- True-negative Rate is the ratio when no attack happens and intrusion detection gives no alarm.
  \( TNR = \frac{TN}{(TN + FP)} \)

- False-positive Rate is the ratio when no attack happens and intrusion detection gives an alarm.
  \( FPR = \frac{FP}{(FP + TN)} \)

FP : False Positive
TN : True Negative

- False-negative rate is the ratio when an actual attack happens, but intrusion detection gives no alarm.
  \( FNR = \frac{FN}{(FN + TP)} \)

- Efficiency rate is the ratio between the actual intrusion detection versus overall detection.
  \( Efficiency - rate = \frac{(TP + TN)}{(TP + TN + FP + FN)} \)

- Precision rate is the ratio between the truly strange packets versus absolute packets that were set apart as intrusions.
  \( Precision - rate = \frac{TP}{TP + FP} \)

- F-Score is the uniform mean of the true-positive rate and precision.
  \( F - Score = \frac{2 * Precision - Rate * TPR}{TPR + Precision - Rate} \)

## 13.9 Conclusion

The principle target of our task work is to utilize the Deep Learning model to predict the sort of assaults dependent on the real time network assault dataset values and, furthermore, indicate the assault data which helps in rapid avoidance of the classified network assault type. The algorithm was based on 3 models: CNN, RNN, MLP. With the help of these models, inputs can calculate the true positive rate, false positive rate, true negative rate, false negative rate, precision rate, efficiency rate, and F-score. On the basis of their inputs, in these terms, we get that which model is more reliable. In this chapter, we are reviewing the algorithm, but in future we will practically explain the algorithm with the help of programming language.

## References

- 1. Abhishek Kumar & Jyotir Moy Chatterjee & Pramod Singh Rathore, 2020. “Smartphone Confrontational Applications and Security Issues,” International Journal of Risk and Contingency Management (IJRCM), IGI Global, vol. 9(2), pages 1–18, April.
- 2. Anand T, Rahul M, S. Vasantha Kumari, M, Narendran G (2020), Intrusion Detection Using Deep Learning Algorithms, journal of engineering, science.
- 3. Bhargava, N., Bhargava, R., Rathore, P. S., & Kumar, A. (2020). Texture Recognition Using Gabor Filter for Extracting Feature Vectors With the Regression Mining Algorithm. International Journal of Risk and Contingency Management (IJRCM), 9(3), 31-44. doi:10.4018/IJRCM.2020070103.
- 4. Farah Barika Kta (2020), A deep learning-based multi-agent system for intrusion detection, https://doi.org/10.1007/s42452-020-2414-z.
- 5. Jin Kim, Nara Shin, Seung Yeon Jo and Sang Hyun Kim (2017), Method of Intrusion Detection using Deep Neural Network, Published in IEEE.
- 6. Kaushik Roy and Albert Esterline (2020), Using a Long Short-Term Memory Recurrent Neural Network (LSTM-RNN) to Classify Network Attacks, doi:10.3390/info11050243.
