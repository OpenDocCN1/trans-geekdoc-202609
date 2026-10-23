It looks different from standard neural networks at a glance, but there's nothing special. If we intentionally draw the diagram of the input layer and the output layer separately, the mechanism is the same shape as the normal neural network:

![](bbox=[0.176, 0.208, 0.824, 0.502])

For a human, this action of *matching input and output* is not intuitive, but for a machine it is a valid action. If so, how it can learn features from input data by matching the output layer and input layer?

Need a little explanation? Let's think about it this way: in the algorithm of machine learning, including neural networks, learning intends to minimize errors between the model's prediction output and the dataset output. The mechanism is to remove an error by finding a pattern from the input data and making data with a common pattern the same output value (for example, 0 or 1). What would then happen if we turned the output value into the input value?

When we look at problems that should be solved as a whole through deep learning, input data is, fundamentally, a dataset that can be divided into some patterns. This means that there are some common features in the input data. If so, in the process of learning where each output value becomes respective input data, the weight of networks should be adjusted to focus more on the part that reflects the common features. And, even within the data categorized in the same class, learning should be processed to reduce weight on the non-common feature part, that is, the noise part.