
model to be trained efficiently without having to process all the data at once.

A power of two is usually specified as the number of samples for a mini-batch. For example, 32, 64, and 128 are commonly used. Using minibatches can reduce the amount of memory required during the training process and parallelize computations. In many cases, a random selection of minibatches can help the model learn in a balanced manner.

The minibatch learning is often used when the stochastic gradient descent (SGD) method is used but can also be used with other optimization algorithms. Using minibatch learning enables efficient learning using a large dataset.

After five epochs, the model is expected to learn the entire training dataset and improve prediction performance. The output results are as follows:

```
< Start >
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/mnist.npz
11490434/11490434 [==========================================================] - 1s 0us/step
Epoch 1/5
1875/1875 [============================================================]- 16s 8ms/step
  - loss: 2.5951 - accuracy: 0.8703
Epoch 2/5
1875/1875 [============================================================]- 10s 5ms/step
  - loss: 0.3623 - accuracy: 0.9147
Epoch 3/5
1875/1875 [============================================================]- 8s 4ms/step
  - loss: 0.2840 - accuracy: 0.9276
Epoch 4/5
1875/1875 [============================================================]- 8s 4ms/step
  - loss: 0.2487 - accuracy: 0.9360
Epoch 5/5
1875/1875 [============================================================]- 7s 4ms/step
  - loss: 0.2324 - accuracy: 0.9419
313/313 - 1s - loss: 0.2557 - accuracy: 0.9429 - 813ms/epoch - 3ms/step
Test accuracy: 0.9429000020027161
< End >
```

These messages indicate that TensorFlow is used to download data from the MNIST dataset and that the downloaded data are used to train the NN model. The dataset contains images of handwritten digits and their corresponding labels (number classes).

This model was trained using five epochs. During one epoch, all the data in the training dataset are learned for one time. At the end of each epoch, the model returns a loss and a correct answer rate. The loss is a metric that measures the difference between model's predictions and actual labels. The correct answer rate indicates the percentage of data that the model predicted correctly.

Finally, it is indicated that the model has an accuracy of 0.9429, which means that the model can recognize handwritten digits with about 94.3% accuracy. This is a percentage at which the model can successfully classify digits accurately using the test dataset.

TensorFlow is an open-source machine learning library that provides low-level APIs for performing a variety of machine learning tasks. Keras is a high-level NN API for deep learning using TensorFlow as the back end. Keras is built on top of TensorFlow and hides TensorFlow's low-level operations, making it easier to build and train NNs.

### 1.3. Organization of this document

This book begins with the Basic, which describes data analysis methods using Excel. In the Basic, we will explain mean and variance testing, regression analysis using the Excel analysis tool, and how to implement an NN using the Excel solver. Furthermore, we will demonstrate automatic differentiation and introduce how to solve a simple PDE.

In the Practical Part that follows, we will explain how to create a spatiotemporal model using an NN. First, we will explain a method for visualizing page information from ancient literature data shot with a three-dimensional CT machine. Then, we will regard a magnetic line group calculated from the results of analyzing electromagnetic fields in a fusion reactor as physical data and explain how to visualize the plasma region using an NN. Up to this point, physical data irrelevant to time are handled.

As an advanced application, we will explain how to use an NN to derive a PDE that describes physical data and how to solve the PDE using the NN. Finally, we will demonstrate a surrogate model, together with some examples. The surrogate model streamlines what-if analysis by linking parameters, such as conditions from large-scale numerical simulations, with physical data.

## Chapter 2

## Basic

## 2.1. Background

### 2.1.1. Data analysis using NNs

This document describes the analysis of physical data primarily using NNs. An NN is a combination of mathematical models of neurons in the human cranial nervous system (Figure 2.1). The concept of NN is inspired by the mechanics of the human brain (all the interconnections between neurons). NN refers to a mathematical model created to represent some of the features of brain function on a computer. NN is one of the modeling methods in machine learning (ML) that mimics the workings of the human brain without the aim to model the billions of neurons in the brain accurately. It simply attempts to simplify it and make it operational. In NN, when one inputs data (numerical values), the numerical values are propagated with weights to the next layer. This is similar to the sequence of processes in the human brain, whereby synapses are connected with weights and neurons produce outputs, which are then connected to the next level.

Areas of use for NNs include pattern recognition and data mining (e.g., image recognition and recommendations).

NNs are widely used in video websites to analyze comments posted on videos. Specifically, NNs combine natural language processing techniques to perform sentiment analysis, topic classification, spam filtering, etc., of comments. The objective of sentiment analysis is to determine whether a comment falls into the positive, negative, or neutral category. NNs are useful for sentiment analysis because they can capture the meaning of words and sentences. Topic classification determines to which topic a comment relates. For example, to classify comments about a particular product or service, NNs can create a classifier using keywords related to that product or service. Spam filtering aims to detect automatically generated comments by spam and bots. By using NNs, characteristic patterns of spam comments can be detected and deleted automatically. Comment analysis using NNs can help video platforms control quality and improve products and services.

![](img/fa57e7010b16a211d5cf69ebb17e416e_34_0.png)

Figure 2.1. About NNs (https://ledge.ai/neural-network/).

The introduction of NN-based methods in machine translation has dramatically improved translation accuracy. In machine translation, NNs are mainly used in a method called NMT (Neural Machine Translation). NMT uses an NN architecture called the Sequence-to-Sequence (Seq2Seq) model to encode input sentences into a latent semantic space, which is then decoded to produce output sentences.

Specifically, NMT uses two NNs called encoders and “decoders”. The encoder receives input sentences as sequences of words or characters and converts them into a latent semantic space. The decoder receives as input the latent semantic space created by the encoder and decodes it to produce output sentences. In NMT, encoders and decoders use architectures such as RNN (Recurrent Neural Network), LSTM, and GRU. These architectures contribute to the accuracy of translation because they can handle long sequences and take into account the context needed for translation. NMT may also incorporate a mechanism called “attention” between the encoder and decoder. Attention is a mechanism that uses the output of the encoder to determine which part of the encoder’s input sentence should correspond to which part of the decoder-generated sentence, and thus is useful when translating long or complex sentences.

In stock price prediction in the financial field, NNs are used to predict future stock prices based on past stock price data, economic indicators, and other information. In general, NNs use deep learning models such as MLP (Multilayer Perceptron) and LSTM (Long Short-Term Memory). There are two main methods of stock price forecasting. One is to forecast time series data and the other is to predict future trends, such as the rise or fall of a stock price.

The objective of forecasting time series data is to use past stock price data and other information to train NNs to predict future stock prices. For example, LSTM can be used to predict future stock prices by learning patterns of past stock price fluctuations.

Conversely, NN is used primarily as a classification problem in predicting trends such as rising or falling stock prices. The objective is to predict whether stock prices will rise or fall, based on past stock price fluctuations and other economic indicators. In this case, classifiers such as MLP (Multilayer Perceptron) and CNN (Convolutional Neural Network) are used.

However, since many factors affect stock price forecasts, it is difficult to make forecasts using only a single NN model. For this reason, ensemble learning, which combines multiple models to make forecasts, is often used.

Image recognition has become an indispensable technology in automated driving development. Image recognition systems using NNs are already in use to recognize surrounding objects faster and more accurately on behalf of the driver. In automated driving, NNs are used to recognize surrounding objects. A typical approach is to collect data from cameras, radar, lidar, and sensors and feed that information as input data to the NN. The NN then extracts feature values from the input data and uses them to recognize objects and extract information such as position, speed, and direction. In general, CNN (Convolutional Neural Network) is widely used for object detection and segmentation. Deep learning-based object detection models such as YOLO (You Only Look Once), SSD (Single Shot Detection), and Faster R-CNN are also used. These models can provide fast and accurate object detection. NNs are also used in other aspects of automation, such as vehicle tracking, lane recognition, and traffic sign recognition.

NNs can detect gastric cancer from endoscopic images, which allows them to be used in practice. NNs have achieved excellent results in image analysis and are used in various fields.

To detect gastric cancer, endoscopic images are input into NNs to identify regions where cancer is most likely to be present. Specifically, NNs can now automatically identify regions on a gastric endoscopic image where cancer is most likely to be present and detect gastric cancers 6 mm or larger.
