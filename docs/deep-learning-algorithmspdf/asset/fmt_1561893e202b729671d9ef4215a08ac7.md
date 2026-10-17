
As shown in Figure 1, taking short text as an example, the input layer is a vector representation of the input data, where the matrix is represented as: (2)

Among them, n is the word length of the sentence and k is the dimension of the word vector.

Next, the convolution layer performs a convolution operation on the input matrix and vectorizes the input data to extract local features. The result can be expressed as:

(3)

Among them, c represents the i-th eigenvalue corresponding to the i convolution operation; W represents the weight matrix; b represents the bias; f represents the activation function;

represents the length of the i to words in the sentence. After performing the convolution operation on the input matrix, the convolution kernel feature vector map is obtained as:

(4)

among them, .

The pooling layer is an important layer in the network structure. It can extract important features from the feature vector map obtained from the previous layer. In more operations, the maximum pooling method is used for sampling. The obtained features are expressed as:

本书版权归Arcler所有

![Image 1711](index-373_1.jpg)

![Image 1712](index-373_2.jpg)

![Image 1713](index-373_3.jpg)

![Image 1714](index-373_4.png)

![Image 1715](index-373_5.png)

![Image 1716](index-373_6.png)

Review of Research on Text Sentiment Analysis Based on Deep Learning 347

(5)

The convolution operation is used to obtain the vectorization of the sentence through the vectorization of the words, and then learn the vector representation of the sentence as a feature, which makes it more suitable as a way to deal with the sentiment analysis problem of short text. Not only can multiple channels be used for multi view feature extraction, but also the number of parameters can be reduced by sharing weights, but the main disadvantage is that the complexity is high when processing long text, and with the increase of convolution layer, there will be problems such as gradient disappearance.

***Based on RNN (Recurrent Neural Network Model)***

Recurrent neural network mainly includes input layer, hidden layer and output layer. For some text data, there may be a relationship between the front and back, that is, there is a temporal relationship between the data.

The “memory function” of the recurrent neural network is reflected here.

Compared to ordinary fully connected neural networks, each neuron of the recurrent neural network will remember the output value of the previous moment, and affect the calculation of the output value of the current moment to a certain extent. The structure of the recurrent neural network is shown below in Figure 2.

Calculated as follows:

(6)

(7)

Among them, x is the value of the input layer; s is the output of the hidden layer; U is the weight parameter when calculating from x to s; V is the weight parameter when calculating the hidden layer to the input layer; W

$

layer before calculation on the value of the hidden layer at the current moment; O represents the value of the output layer.

But the recurrent neural network has its own shortcomings. During data training, if a longer sequence appears, the gradient will disappear or the gradient cannot be updated. Therefore, RNNs have a poor ability to capture long text information. Based on traditional RNNs, they are more suitable for sentence-level sentiment analysis problems (such as Weibo reviews).

本书版权归Arcler所有

![Image 1717](index-374_1.png)

![Image 1718](index-374_2.png)

![Image 1719](index-374_3.png)

![Image 1720](index-374_4.png)

Deep Learning Algorithms

348

Hochreiter \[12\] and others proposed long-short-term memory networks (LSTMs), and Cho \[13\] and others proposed gated recurrent units (GRU).

These recurrent neural network variant structures effectively solve the problem of long-term dependence by introducing gate layers such as forget gates to process input data. Text sentiment analysis belongs to a type of natural language processing. Words are related to each other and depend on each other. Therefore, the “memory function” of the recurrent neural network shows its advantages. It can analyze the feature associations between the words before and after in the sentence to extract more accurate features.

With the introduction of LSTM, GRU and other models, the problem of long text gradient disappearance has been solved, making recurrent neural

.

***Based on FNN (Fuzzy Neural Network Model)***

FNN networks, the initial text representations are generally BOW and VSM

models with great sparsity, which is more suitable for processing text-level sentiment analysis problems at the chapter level. Because the text set of the same size will cause the initial representation of the short text to be too sparse, the problem will not be obvious. Therefore, the short text can be processed by controlling the size of the text set. Model training generally combines unsupervised pre-training and supervised parameter adjustment; accordingly it can use a large amount of unlabeled data, which is also its advantage.

**Figure 2**. RNN structure based on time. (Note: picture reference \[11\]).

**SUMMARY AND PROSPECT**

< # $ ! ' -

ment analysis. It mainly introduces several different deep learning methods 本书版权归Arcler所有

![Image 1721](index-375_1.png)

![Image 1722](index-375_2.png)

![Image 1723](index-375_3.png)

Review of Research on Text Sentiment Analysis Based on Deep Learning 349

and text data for different categories, and further summarizes and analyzes their unique advantages and applicability. Deep learning method saves a lot of complicated process of complicated feature extraction compared with machine learning method, but it has its own shortcomings. If there is supervised deep learning, it still needs to label a large number of data sets for model training. In the case of unsupervised deep learning, the requirements for semantic association are very strict. But the understanding of semantics is diverse and often causes ambiguity, which affects the degree of relevance.

Therefore, the sentiment analysis of text based on deep learning still needs further research, and the author will continue to work hard in this direction.

本书版权归Arcler所有

![Image 1724](index-376_1.png)

![Image 1725](index-376_2.png)

![Image 1726](index-376_3.png)

Deep Learning Algorithms

350

**REFERENCES**

1.

Zhu, X.X. (2019) Summarization of Text Sentiment Analysis Based on Topic Mining Technology.

2.

Yang, L.G., Zhu, J. and Tang, S.P. (2013) A Review of Text Sentiment Analysis. Journal of Computer Applications, 33, 1574-1607. https://

doi.org/10.3724/SP.J.1087.2013.01574

3.

Turney (2002) Thumbs Up or Thumbs Down? Semantic Orientation

~

Association for Computational Linguistics. Association for Computational Linguistics, ACM Press, Philadelphia, PA, 417-424.

https://doi.org/10.3115/1073083.1073153

4\. \`| ~

Reviews Using Contextual Valence Shifters. Computational Intelligence, 22, 110-125. https://doi.org/10.1111/j.1467-8640.2006.00277.x 5.

Jinan, F., Osama, M., Sabah, M., et al. (2012) Opinion Mining over Twitter Space Classifying Tweets Programmatically Using the R

Approach. Proceedings of the 7th International Conference on Digital Information Management, Macau, China, 313-319.

6.

Pang, B., Lee, L. and Vaithyanathan, S. (2002) Thumbs up? Sentiment

~ < \*

of Empirical Methods in Natural Language Processing, MIT Press, Cambridge, MA, 79-86. https://doi.org/10.3115/1118693.1118704

7\. Hinton, G.E. and Salakhutdiony, R.R. (2006) Reducing the Dimensionality of Data with Neural Networks. Science, 313, 504-507.

https://doi.org/10.1126/science.1127647

8.

Socher, R., Cliff, C.L., Andrew, Y., et al. (2011) Parsing Natural Scenes and Natural Language with Recursive Neural Networks. In: Getoor, L.

and Scheffer, T., Eds., Proceedings of the 28th International Conference on Machine Learning Bellevue, Omni Press, Madison, WI, 129-136.
