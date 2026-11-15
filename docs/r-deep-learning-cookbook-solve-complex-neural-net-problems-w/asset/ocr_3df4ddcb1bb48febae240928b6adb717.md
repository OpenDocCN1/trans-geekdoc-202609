# Recurrent Neural Networks

The current chapter will introduce Recurrent Neural Networks used for the modeling of sequential datasets. In this chapter, we will cover:

+   - Setting up a basic Recurrent Neural Network
+   - Setting up a bidirectional RNN model
+   - Setting up a deep RNN model
+   - Setting up a Long short-term memory based sequence model

# Setting up a basic Recurrent Neural Network

**Recurrent Neural Networks (RNN)** are used for sequential modeling on datasets where high autocorrelation exists among observations. For example, predicting patient journeys using their historical dataset or predicting the next words in given sentences. The main commonality among these problem statements is that input length is not constant and there is a sequential dependence. Standard neural network and deep learning models are constrained by fixed size input and produce a fixed length output. For example, deep learning neural networks built on occupancy datasets have six input features and a binomial outcome.