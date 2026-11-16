
speech recognition, and image processing. Its structure is mainly composed of an input layer, a convolutional layer, a pooling layer, a fully connected layer, and an output layer. The structure is shown below in Figure 1:

![](img/1752b062af2760b8561f6faaf183b3d0_371_0.png)

**Figure 1.** Structure of a classic convolutional neural network (Note: picture reference [10]).

As shown in Figure 1, taking short text as an example, the input layer is a vector representation of the input data, where the matrix is represented as:

```
\( e \in R^{n \times k} \)

(2)
```

Among them, n is the word length of the sentence and k is the dimension of the word vector.

Next, the convolution layer performs a convolution operation on the input matrix and vectorizes the input data to extract local features. The result can be expressed as:

```
\( c_i = f(W \cdot X_{i:i+h-1} + b) \)

(3)
```

Among them, c_i represents the i-th eigenvalue corresponding to the convolution operation; W represents the weight matrix; b represents the bias; f represents the activation function; \( X_{i:i+h-1} \) represents the length of the i to i + h - 1 words in the sentence. After performing the convolution operation on the input matrix, the convolution kernel feature vector map is obtained as:

```
\( C = [c_1, c_2, \cdots, c_{n-h+1}] \)

(4)
```

among them, \( C \in R^{n-h+1} \).

The pooling layer is an important layer in the network structure. It can extract important features from the feature vector map obtained from the previous layer. In more operations, the maximum pooling method is used for sampling. The obtained features are expressed as:

c = \max(c_1, c_2, \cdots, c_{n-h+1}) (5)

The convolution operation is used to obtain the vectorization of the sentence through the vectorization of the words, and then learn the vector representation of the sentence as a feature, which makes it more suitable as a way to deal with the sentiment analysis problem of short text. Not only can multiple channels be used for multi view feature extraction, but also the number of parameters can be reduced by sharing weights, but the main disadvantage is that the complexity is high when processing long text, and with the increase of convolution layer, there will be problems such as gradient disappearance.

## Based on RNN (Recurrent Neural Network Model)

Recurrent neural network mainly includes input layer, hidden layer and output layer. For some text data, there may be a relationship between the front and back, that is, there is a temporal relationship between the data. The “memory function” of the recurrent neural network is reflected here. Compared to ordinary fully connected neural networks, each neuron of the recurrent neural network will remember the output value of the previous moment, and affect the calculation of the output value of the current moment to a certain extent. The structure of the recurrent neural network is shown below in Figure 2.

Calculated as follows:

O_i = g(V \cdot S_i) (6)

S_i = f(U \cdot x_i + W \cdot s_{i-1}) (7)

Among them, x is the value of the input layer; s is the output of the hidden layer; U is the weight parameter when calculating from x to s; V is the weight parameter when calculating the hidden layer to the output layer; W represents the weight parameter of the influence of the value of the hidden layer before calculation on the value of the hidden layer at the current moment; O represents the value of the output layer.

But the recurrent neural network has its own shortcomings. During data training, if a longer sequence appears, the gradient will disappear or the gradient cannot be updated. Therefore, RNNs have a poor ability to capture long text information. Based on traditional RNNs, they are more suitable for sentence-level sentiment analysis problems (such as Weibo reviews).

Hochreiter [12] and others proposed long-short-term memory networks (LSTMs), and Cho [13] and others proposed gated recurrent units (GRU). These recurrent neural network variant structures effectively solve the problem of long-term dependence by introducing gate layers such as forget gates to process input data. Text sentiment analysis belongs to a type of natural language processing. Words are related to each other and depend on each other. Therefore, the “memory function” of the recurrent neural network shows its advantages. It can analyze the feature associations between the words before and after in the sentence to extract more accurate features. With the introduction of LSTM, GRU and other models, the problem of long text gradient disappearance has been solved, making recurrent neural networks widely used in the field of sentiment analysis.

## Based on FNN (Fuzzy Neural Network Model)

FNN networks, the initial text representations are generally BOW and VSM models with great sparsity, which is more suitable for processing text-level sentiment analysis problems at the chapter level. Because the text set of the same size will cause the initial representation of the short text to be too sparse, the problem will not be obvious. Therefore, the short text can be processed by controlling the size of the text set. Model training generally combines unsupervised pre-training and supervised parameter adjustment; accordingly it can use a large amount of unlabeled data, which is also its advantage.

![](img/1752b062af2760b8561f6faaf183b3d0_373_0.png)

Figure 2. RNN structure based on time. (Note: picture reference [11]).

## SUMMARY AND PROSPECT

This article briefly reviews and analyzes traditional methods of text sentiment analysis. It mainly introduces several different deep learning methods and text data for different categories, and further summarizes and analyzes their unique advantages and applicability. Deep learning method saves a lot of complicated process of complicated feature extraction compared with machine learning method, but it has its own shortcomings. If there is supervised deep learning, it still needs to label a large number of data sets for model training. In the case of unsupervised deep learning, the requirements for semantic association are very strict. But the understanding of semantics is diverse and often causes ambiguity, which affects the degree of relevance. Therefore, the sentiment analysis of text based on deep learning still needs further research, and the author will continue to work hard in this direction.

## REFERENCES

- 1. Zhu, X.X. (2019) Summarization of Text Sentiment Analysis Based on Topic Mining Technology.
- 2. Yang, L.G., Zhu, J. and Tang, S.P. (2013) A Review of Text Sentiment Analysis. Journal of Computer Applications, 33, 1574-1607. https://doi.org/10.3724/SP.J.1087.2013.01574
- 3. Turney (2002) Thumbs Up or Thumbs Down? Semantic Orientation Applied Unsupervised Classification of Reviews. Meeting on Association for Computational Linguistics. Association for Computational Linguistics, ACM Press, Philadelphia, PA, 417-424. https://doi.org/10.3115/1073083.1073153
- 4. Alistair, K. and Diana, I. (2006) Sentiment Classification of Movie Reviews Using Contextual Valence Shifters. Computational Intelligence, 22, 110-125. https://doi.org/10.1111/j.1467-8640.2006.00277.x
- 5. Jinan, F., Osama, M., Sabah, M., et al. (2012) Opinion Mining over Twitter Space Classifying Tweets Programmatically Using the R Approach. Proceedings of the 7th International Conference on Digital Information Management, Macau, China, 313-319.
- 6. Pang, B., Lee, L. and Vaithyanathan, S. (2002) Thumbs up? Sentiment Classification Using Machine Learning Techniques. In: Proceedings of Empirical Methods in Natural Language Processing, MIT Press, Cambridge, MA, 79-86. https://doi.org/10.3115/1118693.1118704
- 7. Hinton, G.E. and Salakhutdinov, R.R. (2006) Reducing the Dimensionality of Data with Neural Networks. Science, 313, 504-507. https://doi.org/10.1126/science.1127647
- 8. Socher, R., Cliff, C.L., Andrew, Y., et al. (2011) Parsing Natural Scenes and Natural Language with Recursive Neural Networks. In: Getoor, L. and Scheffer, T., Eds., Proceedings of the 28th International Conference on Machine Learning Bellevue, Omni Press, Madison, WI, 129-136.
- 9. Si, X.H. and Wang, Y. (2019) Analysis of Short Text Sentiment Orientation with CNN and BLSTM. Journal of Software, 18, 15-20.
- 10. Lu, C. (2017) Research on Sentiment Analysis Methods Based on Deep Learning. Hunan University, Changsha.
- 11. Ji, L.Z. (2019) Research on Text Sentiment Analysis Technology Based on Deep Learning. Beijing University of Posts and Telecommunications, Beijing.
