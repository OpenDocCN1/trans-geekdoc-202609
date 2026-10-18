# 14.2.3 Modern Machine Learning

Deep learning is modern machine learning with the capability to take raw inputs and learn the optimal feature representation implicitly. This has performed well in various long-standing artificial intelligence tasks [41]. The most commonly used deep learning architectures are discussed next in detail.

# 14.2.3.1 Deep Neural Network (DNN)

An artificial neural network (ANN) is a computational model influenced by the characteristics of biological neural networks. The family of ANN includes the feed-forward neural network (FFN), convolutional neural network, and recurrent neural network (RNN). FFN forms a directed graph in which a graph is composed of neurons group as a mathematical unit. Each neuron in the ith layer has a connection to all the neurons in i + 1th layer.

Each neuron of the hidden layer denotes a parameter h that is computed by

h_i(x) = f(w_i^T x + b_i),  (14.2.1)
h_ii: R^{d_{i-1}} → R^{d_i},  (14.2.2)
f: R → R,  (14.2.3)

where w_i ∈ R^{d×d_{i-1}}, b_i ∈ R^{d_i}, d_i denotes the size of the input, f is a nonlinear activation function ReLU.

The traditional examples of machine learning algorithms include linear regression, logistic regression, linear discriminant analysis, classification and regression trees, naïve Bayes, K-nearest neighbor (KNN, K means clustering), learning vector quantization (LVQ), support vector machines (SVM), random forest, Monte Carlo, neural networks and Q-learning.

+   - *Supervised Adaptation*: Adaptation is carried out in the execution of system at every iteration.