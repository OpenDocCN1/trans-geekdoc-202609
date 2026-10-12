
# Problem 11.1
Derive equation 11.5 from the network definition in equation 11.4.

# Problem 11.2
Unraveling the four-block network in [figure 11.4a](#c011.xhtml#c11-fig-0004) produces one path of length zero, four paths of length one, six paths of length two, four paths of length three, and one path of length four. How many paths of each length would there be if with (i) three residual blocks and (ii) five residual blocks? Deduce the rule for *K* residual blocks.

# Problem 11.3
Show that the derivative of the network in equation 11.5 with respect to the first layer **f**[1][**x**] is given by equation 11.6.

# Problem 11.4*
Explain why the values in the two branches of the residual blocks in [figure 11.6a](#c011.xhtml#c11-fig-0006) are uncorrelated. Show that the variance of the sum of uncorrelated variables is the sum of their individual variances.

# Problem 11.5*
The forward pass for batch normalization given a batch of scalar values ![c11-fig-5014.jpg](images/c11-fig-5014.jpg) consists of the following operations ([figure 11.15](#c011.xhtml#c11-fig-0015)):

![c11-fig-5015.jpg](images/c11-fig-5015.jpg)

 (11.10)

where ![c11-fig-5016.jpg](images/c11-fig-5016.jpg). Write Python code to implement the forward pass. Now derive the algorithm for the backward pass. Work backward through the computational graph computing the derivatives to generate a set of operations that computes ![c11-fig-5017.jpg](images/c11-fig-5017.jpg) for every element in the batch. Write Python code to implement the backward pass.

![Figure 11.15 Computational graph for batch normalization (see problem 11.10).](images/c11-fig-0015.jpg)

[Figure 11.15](#c011.xhtml#c11-fig-0015a) Computational graph for batch normalization (see problem 11.10).

# Problem 11.6
Consider a fully connected neural network with one input, one output, and ten hidden layers, each of which contains twenty hidden units. How many parameters does this network have? How many parameters will it have if we place a batch normalization operation between each linear transformation and ReLU?

# Problem 11.7*
Consider applying an L2 regularization penalty to the weights in the convolutional layers in [figure 11.7a](#c011.xhtml#c11-fig-0007), but not to the scaling parameters of the subsequent BatchNorm layers. What do you expect will happen as training proceeds?

# Problem 11.8
Consider a convolutional residual block that contains a batch normalization operation, followed by a ReLU activation function, and then a 3×3 convolutional layer. If the input and output both have 512 channels, how many parameters are needed to define this block? Now consider a bottleneck residual block that contains three batch normalization/ReLU/convolution sequences. The first uses a 1×1 convolution to reduce the number of channels from 512 to 128. The second uses a 3×3 convolution with the same number of input and output channels. The third uses a 1×1 convolution to increase the number of channels from 128 to 512 (see [figure 11.7b](#c011.xhtml#c11-fig-0007)). How many parameters are needed to define this block?

# Problem 11.9
The U-Net is completely convolutional and can be run with any sized image after training. Why do we not train with a collection of arbitrarily-sized images?

# Chapter 12

Transformers

Chapter 10 introduced convolutional networks, which are specialized for processing data that lie on a regular grid. They are particularly suited to processing images, which have a very large number of input variables, precluding the use of fully connected networks. Each layer of a convolutional network employs parameter sharing so that local image patches are processed similarly at every position in the image.

This chapter introduces transformers. These were initially targeted at natural language processing (NLP) problems, where the network input is a series of high-dimensional embeddings representing words or word fragments. Language datasets share some of the characteristics of image data. The number of input variables can be very large, and the statistics are similar at every position; it's not sensible to re-learn the meaning of the word dog at every possible position in a body of text. However, language datasets have the complication that text sequences vary in length, and unlike images, there is no easy way to resize them.

## 12.1 Processing text data

To motivate the transformer, consider the following passage:

> The restaurant refused to serve me a ham sandwich because it only cooks vegetarian food. In the end, they just gave me two slices of bread. Their ambiance was just as good as the food and service.

The goal is to design a network to process this text into a representation suitable for downstream tasks. For example, it might be used to classify the review as positive or negative or to answer questions such as "Does the restaurant serve steak?".

We can make three immediate observations. First, the encoded input can be surprisingly large. In this case, each of the 37 words might be represented by an embedding vector of length 1024, so the encoded input would be of length 37 × 1024 = 37888 even for this small passage. A more realistically sized body of text might have hundreds or even thousands of words, so fully connected neural networks are impractical.

Second, one of the defining characteristics of NLP problems is that each input (one or more sentences) is of a different length; hence, it's not even obvious how to apply a fully connected network. These observations suggest that the network should share parameters across words at different input positions, similarly to how convolutional networks share parameters across different image positions.

Third, language is ambiguous; it is unclear from the syntax alone that the pronoun it refers to the restaurant and not to the ham sandwich. To understand the text, the word it should somehow be connected to the word restaurant. In the parlance of transformers, the former word should pay *attention* to the latter. This implies that there must be connections between the words and that the strength of these connections will depend on the words themselves. Moreover, these connections need to extend across large text spans. For example, the word their in the last sentence also refers to the restaurant.

## 12.2 Dot-product self-attention

The previous section argued that a model for processing text will (i) use parameter sharing to cope with long input passages of differing lengths and (ii) contain connections between word representations that depend on the words themselves. The transformer acquires both properties by using *dot-product self-attention*.

A standard neural network layer **f**[**x**], takes a *D* × 1 input **x** and applies a linear transformation followed by an activation function like a ReLU, so:

![c12-fig-5001.jpg](images/c12-fig-5001.jpg)

 (12.1)

where ***β*** contains the biases, and **Ω** contains the weights.

A self-attention block **sa**[•] takes *N* inputs **x**[1], …, **x**[N], each of dimension *D* × 1, and returns *N* output vectors of the same size. In the context of NLP, each input represents a word or word fragment. First, a set of *values* are computed for each input:

![c12-fig-5002.jpg](images/c12-fig-5002.jpg)

 (12.2)

where ***β***[v] and **Ω**[v] represent biases and weights, respectively.

Then the *n*^(th) output **sa**[n][**x**[1], …, **x**[N]] is a weighted sum of all the values **v**[1], …, **v**[N]:

![c12-fig-5003.jpg](images/c12-fig-5003.jpg)

 (12.3)

The scalar weight *a*[**x**[m], **x**[n]] is the *attention* that the *n*^(th) output pays to input **x**[m]. The *N* weights *a*[•, **x**[n]] are non-negative and sum to one. Hence, self-attention can be thought of as *routing* the values in different proportions to create each output ([figure 12.1](#c012.xhtml#c12-fig-0001)).
