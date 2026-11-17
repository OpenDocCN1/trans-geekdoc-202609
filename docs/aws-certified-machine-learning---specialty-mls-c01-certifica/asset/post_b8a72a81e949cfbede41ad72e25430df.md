
Finally, you should know that AWS has implemented K-Means as part of its list of built-in algorithms. In other words, you don’t have to use external libraries or bring your own algorithm to play with K-Means on AWS.

## Conclusion

That was a really good accomplishment: you just mastered the basics of clustering algorithms and you should now be able to drive your own projects and research about this topic! For the exam, remember that clustering belongs to the unsupervised field of machine learning, so there is no need to have labeled data.

Also, make sure that you know how the most popular algorithm of this field works – that is, K-Means. Although clustering algorithms do not provide the meaning of each group, they are very powerful for finding patterns in the data, either to model a particular problem or just to explore the data.

Coming up next, you will keep studying unsupervised algorithms and see how AWS has built one of the most powerful algorithms out there for anomaly detection, known as RCF.

## Anomaly detection

Finding anomalies in data is a very common task in modeling and data exploratory analysis. Sometimes, you might want to find anomalies in the data just to remove them before fitting a regression model, while other times, you might want to create a model that identifies anomalies as an end goal – for example, in fraud detection systems.

Again, you can use many different methods to find anomalies in the data. With some creativity, the possibilities are endless. However, there is a particular algorithm that works around this problem that you should definitely be aware of for your exam: RCF.

RCF is an unsupervised decision tree-based algorithm that creates multiple decision trees (forests) using random subsamples of the training data. Technically, it randomizes the data and then creates samples according to the number of trees. Finally, these samples are distributed across each tree.

These sets of trees are used to assign an anomaly score to the data points. To calculate the anomaly score for a particular data point, it is passed down each tree in the forest. As the data point moves through the tree, the path length from the root node to the leaf node is recorded for that specific tree. The anomaly score for that data point is then determined by considering the distribution of path lengths across all the trees in the forest.

If a data point follows a short path in most trees (i.e., it is close to the root node), it is considered a common point and will have a lower anomaly score.

On the other hand, if a data point follows a long path in many trees (i.e., it is far from the root node), it is considered an uncommon point and will have a higher anomaly score.

The most important hyperparameters of RCF are num_trees and num_samples_per_tree, which are the number of trees in the forest and the number of samples per tree, respectively.

## Dimensionality reduction

Another unsupervised algorithm that was implemented by AWS in its list of built-in algorithms is known as principal component analysis, or PCA for short. PCA is a technique that’s used to reduce the number of variables/dimensions in a dataset.

The main idea behind PCA is plotting the data points to another set of coordinates, known as Principal Components (PCs), which aims to explain the most variance in the data. By definition, the first component will capture more variance than the second component, then the second component will capture more variance than the third one, and so on.

You can set up as many PCs as you need, as long as it does not surpass the number of variables in your dataset. Figure 6.18 shows how these PCs are drawn:

![](img/87c29232224b00f5a8bba6a66a391700_177_0.png)

Figure 6.18 – Finding PCs in PCA

As mentioned previously, the first PC will be drawn in such a way that it will capture most of the variance in the data. That is why it passes near the majority of the data points in Figure 6.18.

Then, the second PC will be perpendicular to the first one, so that it will be the second component that explains the variance in the data. If you want to create more components (consequently, capturing more variance), you just have to follow the same rule of adding perpendicular components. Eigenvectors and eigenvalues are the linear algebra concepts associated with PCA that compute the PCs.

So, what is the story with dimension reduction here? In case it is not clear yet, these PCs can be used to replace your original variables. For example, consider you have 10 variables in your dataset, and you want to reduce this dataset to three variables that best represent the others. A potential solution for that would be applying PCA and extracting the first three PCs!

Do these three components explain 100% of your dataset? Probably not, but ideally, they will explain most of the variance. Adding more PCs will explain more variance but at the cost of adding extra dimensions.

## Using AWS's built-in algorithm for PCA

In AWS, PCA works in two different modes:

- Regular: For datasets with a moderate number of observations and features
- Randomized: For datasets with a large number of observations and features

The difference is that, in randomized mode, it is used as an approximation algorithm.

Of course, the main hyperparameter of PCA is the number of components that you want to extract, known as `num_components`.

## IP Insights

IP Insights is an unsupervised algorithm that is used for pattern recognition. Essentially, it learns the usage pattern of IPv4 addresses.

The modus operandi of this algorithm is very intuitive: it is trained on top of pairs of events in the format of entity and IPv4 address so that it can understand the pattern of each entity that it was trained on.

### IMPORTANT NOTE

*For instance, you can understand "entity" as user IDs or account numbers.*

Then, to make predictions, it receives a pair of events with the same data structure (entity, IPv4 address) and returns an anomaly score for that particular IP address, according to the input entity.

### IMPORTANT NOTE

*This anomaly score that is returned by IP Insights infers how anomalous the pattern of the event is.*

You might come across many applications with IP Insights. For example, you can create an IP Insights model that was trained on top of your application login events (this is your entity). You should be able to expose this model through an API endpoint to make predictions in real time.

Then, during the authentication process of your application, you could call your endpoint and pass the IP address that is trying to log in. If you got a high score (meaning this pattern of logging in looks anomalous), you can request extra information before authorizing access (even if the password was right).

This is just one of the many applications of IP Insights you could think about. Next, you will learn about textual analysis.

## Textual analysis

Modern applications use **Natural Language Processing (NLP)** for several purposes, such as text translation, document classifications, web search, **Named Entity Recognition (NER)**, and many others.

AWS offers a suite of algorithms for most NLP use cases. In the next few subsections, you will have a look at these built-in algorithms for textual analysis.

## BlazingText algorithm

BlazingText does two different types of tasks: text classification, which is a supervised learning approach that extends the **fastText** text classifier, and Word2Vec, which is an unsupervised learning algorithm.

BlazingText's implementations of these two algorithms are optimized to run on large datasets. For example, you can train a model on top of billions of words in a few minutes.

This scalability aspect of BlazingText is possible due to the following:

- Its ability to use multi-core CPUs and a single GPU to accelerate text classification
- Its ability to use multi-core CPUs or GPUs, with custom CUDA kernels for GPU acceleration, when playing with the Word2Vec algorithm

The Word2Vec option supports batch_skipgram mode, which allows BlazingText to do distributed training across multiple CPUs.

### IMPORTANT NOTE

The distributed training performed by BlazingText uses a mini-batching approach to convert level-1 BLAS (Basic Linear Algebra Subprograms) operations into level-3 BLAS operations. If you see these terms during your exam, you should know that they are related to BlazingText (Word2Vec mode).

Still in Word2Vec mode, BlazingText supports both the skip-gram and Continuous Bag of Words (CBOW) architectures.

Finally, note the following configurations of BlazingText, since they are likely to be present in your exam:

- In Word2Vec mode, only the train channel is available.
- BlazingText expects a single text file with space-separated tokens. Each line of the file must contain a single sentence. This means you usually have to preprocess your corpus of data before using BlazingText.

## Sequence-to-sequence algorithm

This is a supervised algorithm that transforms an input sequence into an output sequence. This sequence can be a text sentence or even an audio recording.

The most common use cases for sequence-to-sequence are machine translation, text summarization, and speech-to-text. Anything that you think is a sequence-to-sequence problem can be approached by this algorithm.

Technically, AWS SageMaker's Seq2Seq uses two types of neural networks to create models: an RNN and a Convolutional Neural Network (CNN) with an attention mechanism.

Latent Dirichlet allocation, or LDA for short, is used for topic modeling. Topic modeling is a textual analysis technique where you can extract a set of topics from a corpus of text data. LDA learns these topics based on the probability distribution of the words in the corpus of text.

Since this is an unsupervised algorithm, there is no need to set a target variable. Also, the number of topics must be specified up-front, and you will have to analyze each topic to find its domain meaning.

## Neural Topic Model algorithm

Just like the LDA algorithm, the Neural Topic Model (NTM) also aims to extract topics from a corpus of data. However, the difference between LDA and NTM is their learning logic. While LDA learns from probability distributions of the words in the documents, NTM is built on top of neural networks.

The NTM network architecture has a bottleneck layer, which creates an embedding representation of the documents. This bottleneck layer contains all the necessary information to predict document composition, and its coefficients can
