
# PHISHING URL Detection Based on DEEP LEARNING TECHNIQUES

in the above-mentioned search engine-based approach. The total number of search results obtained through search engine and the ranking of the suspected webpage are used to determine the results. The validation of this approach is carried out using different search engines namely Google, Yahoo and Bing. An approach by Lee et al. [8] proposed the features are gathered by Google’s suggestion, web page ranking and wary URL patterns. Approximately 98.23% of phishing websites are detected. An approach based on a weighted token in URL is proposed [9] by Tan et al. Identity keyword phrases are treated as signatures from the webpage. The experiment results achieved 99.20% true positive and 92.20% true negative.

Overall, a search engine-related approach is more effective in phishing detection. However, using a search engine for phishing detection has several disadvantages. It can work only with the webpage that contains in English language, time consuming because Google search engine is involved and bypass if the webpage is composed of image of textual content. Then, it is necessary to use the popularity of websites to support other heuristics for phishing detection. A rule-based approach is proposed by Mahmood and Ai [10]. The relationship between the content and URL of a page are extracted. Matching algorithm is used to test the address of a page resource element together with the URL. Attribute selection-based phishing detection is proposed by Carolin et al. [11].

Ping et al. [12] proposed a deep learning approach in detecting phishing web page where the deep belief networks is presented and the detection accuracy is found to be 89.2%. Wenchuan et al. [13] proposed text-based classification using Convolutional Gated Recurrent Unit Neural Network. In the study by Alejandro et al [14], the phishing URLs are detected using recurrent neural network with an accuracy of 98.7%. Liqun et al. [15] proposed the NOISEM approach where the surface level feature, topological, and the inheritance of the websites are used in detecting phishing webpages, and the accuracy is found to be 97.5.

A survey on detecting phishing is portrayed by Samanesh Mahdhavafir and Ali A. Ghorbani [16]. Ishita et al. [17] proposed a deep learning approach in detecting phishing webpages with an accuracy of 95%. Tomas Rysymas and Lauryn Dovydatis [18] proposed detection of phishing URL based on lexical features, word level embedding, and character level embedding using deep learning approach. Manuel et al. [19] proposed network traffic classifier using convolutional and recurrent neural network for Internet of Things. Zuguo et al. [20] proposed phishing URL detection using deep learning.

## 18.3 Feature Generation

The heuristic features are extracted from the URL. The detailed feature extraction step is given in jeeva et al. [2]. The architecture of the proposed work is portrayed in Figure 18.2. In our experiments, the data from Phishtank is considered with URLs that have 14 features and one class that specifies it is a phished or legitimate website. The dataset is preprocessed and all the null values are identified and converted to the average value of the neighbors. The distribution plot of the features is shown in Figure 18.3.

## 18.4 Convolutional Neural Network for Classification of Phishing vs Legitimate URLs

In deep learning, the convolutional neural network (CNN) belongs to the class of deep neural networks. The Convolutional Neural Network (CNN) has exposed exceptional performance in numerous computer vision and machine learning problems. The advantage of CNN is it inevitably detects the significant features without any human supervision. accommodates convolution and pooling operations and execute parameter sharing. This allows CNN models to execute on any device and building them universally compliant.

Figure 18.4 shows the traditional neural network with one or more hidden layers. Each circle represents a neuron, which has connection to every neuron in the next layer. CNN is a

![](img/081dc7f102a3793cb08980a6e19b8f17_411_0.png)

**Figure 18.2** System architecture.

| F1 | F2 | F3 | F4 |
|---|---|---|---|
| 1200 | 1000 | 800 | 800 |
| 800 | 800 | 600 | 600 |
| 600 | 400 | 400 | 400 |
| | | | |

| F5 | F6 | F7 | F8 |
|---|---|---|---|
| 1000 | 800 | 1000 | 1000 |
| 800 | 600 | 800 | 800 |
| 600 | 400 | 600 | 600 |
| 400 | 200 | 400 | 400 |

| F9 | F10 | F11 | F12 |
|---|---|---|---|
| 1000 | 800 | 1000 | 1000 |
| 800 | 600 | 800 | 800 |
| 600 | 400 | 600 | 600 |
| 400 | 200 | 400 | 400 |

| F13 | F14 |
|---|---|
| 1200 | 800 |
| 1000 | 600 |
| 800 | 400 |
| 600 | 200 |

Figure 18.3 Distribution plot of the features.

![](img/081dc7f102a3793cb08980a6e19b8f17_412_0.png)

Figure 18.4 Traditional neural network form of artificial neural network is most properly used in image analysis. CNN is also helps in data analysis for classification problems. The basis of CNN is the convolutional layer. The convolutional layer works like other layers, which accept input and transform the output to the feature map. For nonlinearity purposes, the result is passed on to activation function like Rectified Linear Units (ReLU). The ReLU activation function is given by $f(x)=\max(0, x)$ helps to lessen fading and exploding gradient concerns. It is more competent with respect to time and cost for training huge data in contrast to traditional non-linear activation functions, such as Sigmoid or Tangent. In this paper, we have stride to be the default value 1. Then padding can be performed to maintain the same dimensionality. Pooling reduces the dimensionality and reduces the number of parameters. The most used pooling is max pooling. We insert fully connected layers to complete the CNN architecture. Training of the network is done like backpropagation with gradient descent. During training, Dropout parameter can be tuned to prevent overfitting. Figure 18.5 shows the diagram of CNN, which uses multiple convolutional operations for feature extraction. The model constructed is given in Figure 18.6.

![](img/081dc7f102a3793cb08980a6e19b8f17_413_0.png)

Figure 18.5 Convolution network model.

| Layer (type) | Output Shape | Param # |
|---|---|---|
| input_2 (InputLayer) | (None, 14, 14) | 0 |
| dense_29 (Dense) | (None, 14, 14) | 210 |
| dense_30 (Dense) | (None, 14, 14) | 210 |
| dense_31 (Dense) | (None, 14, 12) | 180 |
| dense_34 (Dense) | (None, 14, 14) | 182 |
| dense_35 (Dense) | (None, 14, 14) | 210 |

Total params: 992
Trainable params: 992
Non-trainable params: 0

Figure 18.6 CNN model construction.

## 18.5 Results and Discussion

The dataset is divided into training and testing, where 80% of the data is used for training and 20% for testing. The result obtain from CNN is shown in Figure 18.7. After 19 epoch, it has been found to be 99.64%. The outcome of the trained and tested values are used to find out the accuracy of the

```
Epoch 1/100
Epoch 1/84 - 2ms/step - loss: 0.3664 - accuracy: 0.8679
Epoch 2/84 - 2ms/step - loss: 0.1022 - accuracy: 0.9667
Epoch 3/100
Epoch 3/84 - 2ms/step - loss: 0.0229 - accuracy: 0.9964
Epoch 4/100
Epoch 4/84 - 2ms/step - loss: 0.0113 - accuracy: 0.9976
Epoch 5/100
Epoch 5/84 - 2ms/step - loss: 0.0090 - accuracy: 0.9988
Epoch 6/100
Epoch 6/84 - 2ms/step - loss: 0.0072 - accuracy: 0.9988
Epoch 7/100
Epoch 7/84 - 2ms/step - loss: 0.0033 - accuracy: 1.0000
Epoch 8/100
Epoch 8/84 - 2ms/step - loss: 0.0018 - accuracy: 0.9998
Epoch 9/100
Epoch 9/84 - 2ms/step - loss: 0.0035 - accuracy: 0.9988
Epoch 10/100
Epoch 10/84 - 2ms/step - loss: 0.0025 - accuracy: 0.9988
Epoch 11/100
Epoch 11/84 - 2ms/step - loss: 0.0010 - accuracy: 1.0000
Epoch 12/100
Epoch 12/84 - 2ms/step - loss: 0.0010 - accuracy: 1.0000
Epoch 13/100
Epoch 13/84 - 2ms/step - loss: 7.8732e-04 - accuracy: 1.0000
Epoch 14/100
Epoch 14/84 - 2ms/step - loss: 7.7947e-04 - accuracy: 1.0000
Epoch 15/100
Epoch 15/84 - 2ms/step - loss: 7.0281e-04 - accuracy: 1.0000
Epoch 16/100
Epoch 16/84 - 2ms/step - loss: 4.2655e-04 - accuracy: 1.0000
Epoch 17/100
Epoch 17/84 - 2ms/step - loss: 3.2148e-04 - accuracy: 1.0000
Epoch 19/100
Epoch 18/84 - 1ms/step - loss: 0.0084 - accuracy: 0.9964
```

Figure 18.7 Experimental results obtained using CNN.

*
