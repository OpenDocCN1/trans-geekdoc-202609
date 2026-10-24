loss, each data point should be normalized into [0, 1]. Compare them with PCA on the MNIST data set, which can be found at http://yann.lecun.com/exdb/mnist/, in terms of classification accuracy and the visualization of reconstructed images. For the classification task, first use the autoencoder or PCA to obtain the features of the data and then train a linear SVM or logistic regression model using the features.

10.5. Dropout. (a) Explain why dropout can be used to mitigate the overfitting problem. (b) Suppose we have a simple two-layer neural network y = W2(W1x + b1) + b2 where x ∈ R3, W1 ∈ R2×3, b1 ∈ R2, W2 ∈ R2 and b2 ∈ R. How many possible dropout networks are there that are not disconnected?

10.6. Pretraining on autoencoder.
a. Why pretraining helps the learning or converge?
b. How to pretrain an autoencoder?

10.7. Loss functions. Consider the following two loss functions, including (1) mean-squared error Loss(T, O) = 1/2(T - O)^2, and (2) cross-entropy Loss(T, O) = -T log O - (1 - T) log (1 - O) for binary classification. Assume the activation function is sigmoid.
a. Show the derivation of the error δ for the output unit in backpropagation process and compare the two loss functions (e.g., potential problems they might produce).
b. Now, we wish to generalize the cross-entropy loss to the scenario of multiclass classification. The target output is a one-hot vector of length C (i.e., the number of total classes), and the index of nonzero element (i.e., 1) represents the class label. The output is also a vector of the same length O = [O1, O2, ..., OC]. Show the derivation of the categorical cross-entropy loss and the error δ of the output unit. (hint: there are two key steps, including (1) normalizing the output values by scaling between 0 and 1, and (2) deriving the cross entropy loss following the definition for the binary case where the loss can be represented as Loss(T, O) = - \sum_{i=1}^C T_i log(O_i).)

10.8. What are the key differences between CNNs and feed-forward neural networks? Why are CNNs widely used on grid-like data?

10.9. 2-D convolution. Given the input and two kernels as shown in Fig. 10.43,
a. compute the feature maps by applying kernel K1, K2 (stride is defined as 1, and zeros are padded around I), respectively;
b. re-compute the feature maps if the stride is 2;
c. compute the new feature maps after we apply a downsampling process, max pooling, and average pooling (filter size is 2 x 2), respectively, to the obtained feature maps in (a).

10.10. Training LSTM. It is usually hard to train LSTM on long sequences, answer the following questions:
a. Why it is hard to train LSTM?
b. How to mitigate the problem?

10.11. LSTM and GRU Compare LSTM with GRU, and answer the following questions:
a. What are they have in common?
b. What are the differences between them?
c. What are the pros and cons of them?

10.12. Suppose we apply graph convolutional networks (GCNs) on grid-like graphs (e.g., images) without normalizing adjacency matrix (i.e., removing Steps 2–3 in Fig. 10.38). Explain why it is essentially a 2-D convolution with a special type of filters.