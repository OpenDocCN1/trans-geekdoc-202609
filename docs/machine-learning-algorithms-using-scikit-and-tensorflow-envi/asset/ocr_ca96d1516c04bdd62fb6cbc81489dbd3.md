To evaluate the performance of our model, we calculate the accuracy by comparing the predicted labels y_pred with the actual labels y_test using the accuracy_score() function from scikit-learn. Running the code will output the accuracy of the Naive Bayes classifier on the test data.

# 4. TENSORFLOW

Tensorflow is an open-source software library which is developed by engineers at Google. Data low graphs are used, mathematical operations are represented by nodes and graph edges acts as a multi-dimensional array of data known as tensor. It is a library which provides various APIs for developing advanced applications. Construction of computational graph and running it are some fundamentals or main components of Tensorflow Core. It consists of various nodes which will be responsible for a specific task. These nodes are used to take tensor as an input data and generate output as a tensor.

An important difference between a variable and constant is that a constant is stored in the graph and gets loaded whenever we open the graph whereas the variable exists independently and may be stored in a parameter server.

Google created the open-source machine learning framework known as TensorFlow. It offers a platform for creating and honing machine learning models, such as deep neural networks, utilising a range of data sources, including time series data, pictures, and text.

TensorFlow supports distributed computing across a number of hardware platforms, including CPUs, GPUs, and TPUs, and employ a computational graph to describe the mathematical operations in a machine learning model. Python, C++, and Java are just a few of the programming languages supported by TensorFlow.

Tensorflow is used in a variety of domains like healthcare, in companies for prediction and analysis, in the stock market etc. It is used for image detection, voice recognition, text based application etc. Tensorflow for instance could be used to aid people with motor disabilities as their devices would be controllable just via text or a simple gesture. Microsoft in 2019 used tensorflow to make an app controllable just with your gaze, hands-free.

Tensors have a type of data structure like vectors and matrices and can be used for calculating arithmetic operators. Tensors can have a variety of dimensions and are often referred to as N dimensional arrays. It can be thought of as nested array of multiple dimensions, the number of dimensions a tensor has is called rank and the length in each dimension describes its shape.

Convolutional Neural Networks do processing over multiple layers. Its main features are convolution and pooling. tf.session starts the session and tf.placeholder is used to create a space to store variables which will be assigned later.

Recurrent Neural Networks are a class of neutral networks that are used in model sequencing of data such as time series or natural language. We can use tensorflow cloud to train RNN models made from keras.

Multiple layer perceptron is formed from as it says multiple layers of perceptron. It has an input layer, hidden layers and output layers. In image recognition we input into a neural network and it gets assigned a label which we get as output. We will input the sample images to the system lets say 4000, then we will do an 80:20 split and use 80% of them for training and leave the last 20% for testing purposes.

Dimensionality reduction can be used in both supervised and unsupervised learning. In unsupervised learning it is mainly used to preprocess the data by doing feature extraction on it. We do this with the