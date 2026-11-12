The user will need to spend extra time labeling the classes after classification. Moreover, the spectral features can change with time that may result in some inaccurate classification.

In the medical field, unsupervised learning is very effective in tissue differentiation. It can be used to decern different types of tissues at a certain place in the body. This is very helpful for treating people who have muscle injuries.

# ## 2.2.3 Other Methods

Many other methods are different from traditional methods and take very different approaches. Here we will discuss a few of the most popular ones.

+   - Semi-Supervised Learning: In supervised learning, a ML engineer or data scientist has to hand-label the data individually. This entire process gets very tedious, time-consuming, and costly as the number of data increases. On the other hand, real-life application for unsupervised learning is limited. To tackle these disadvantages of both worlds, semi-supervised learning comes in handy.

The main target of unsupervised learning is to cluster a set of data into homogeneous subgroups. In a certain group, all the data are similar to each other and different from the rest of the data. It is required to have any previous information to achieve the final goal that is to find similarities and dissimilarities among the data points. But, there may be cases where a some of the data is labeled and the rest are not. This is when semi-supervised learning is effective.

Semi-supervised learning uses a technique called pseudo-labeling. It can train data with less labeled data compared to supervised learning. It usually uses a combination of different neural network models and training methods.

Semi-supervised learning starts by training the labeled data similar to supervised learning. Then it predicts the output for unlabeled data. These outputs are called pseudo-labels and may not be very accurate. Then a link is created between the labels from labeled training data and the pseudo-labels created by the model. Then the inputs of both the labeled training data and unlabeled data are linked. Finally, the model is trained again to decrease the error and improve the accuracy of the model.

The assumptions on the data for semi-supervised learning can be of different types—continuity assumption (outputs are more likely to have the same output label if the points are close to each other), cluster assumption (discrete clusters are used to divide the data points and points inside a single cluster are prone to have the same output label) and manifold assumption (the distance and densities of the data are used inside a manifold which has a much lower dimension compared to the input space).

In the medical sector, protein sequence classification is a significant emerging field as it can help understand and solve diseases. It can help change the way we view any disease and understand even better than ever before. Generally, DNA strands are very large. This is where semi-supervised makes things easy to understand the protein sequence of DNA.