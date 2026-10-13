
## 3.2 Artificial Neural Network (ANN)

$$x \mapsto \sum_{i=0}^{n} w_i x_i + b = w_0 x_0 + w_1 x_1 + \ldots + w_n x_n + b = w \cdot x + b \tag{3.1}$$

There are many advantages associated with ANNs. ANN supports learning any non-linear function and considers it as a universal function approximator. The non-linear characteristics of the model are handled by the associated activation functions, which learn the complex relationship. Here, each node outputs a weighted sum of inputs. If a model does not associate with an activation function, then the model can learn only the linear relationships. Thus, the activation function gives power to ANN.

Let us consider the challenges in ANNs. Consider an image classification problem. Initially, the two-dimensional image is transformed into a one-dimensional vector before the training starts. However, when the image size increases, the required number of trainable parameters also increases. For example, consider an image of size `224×224`. In this case, the first hidden layer with four nodes will contain `602112` trainable parameters. Therefore, ANN drops the spatial features and the pixel arrangement of the image. Further, ANN may not capture the sequential data in the input space. This limitation is addressed using recurrent neural networks (RNNs).

## 3.3 Recurrent Neural Network (RNN)

Recurrent neural networks (RNNs) are derived from feed-forward networks and used to learn sequence data. RNN is a type of ANN, where the nodes are connected maintaining a temporal sequence. As shown in [Figure 3.5](#ch10.xhtml#f33), RNN has a looping connection in the hidden layers to capture the sequential information in the input. Here, the output of a given layer is fed back to the input as feedback, and then the output is predicted as shown in [Figure 3.6](#ch10.xhtml#f34). Generally, RNNs are used to solve problems related to time series data including both text and audio. RNN-based models are mainly used in speech recognition, natural language processing, language translation, stock forecasting, and image captioning.

![Figure 3.5 RNN vs ANN.](html/images/9781032473246_C003_005.jpg)

[Figure 3.5](#ch10.xhtml#f33b) RNN vs ANN.

![Figure 3.6 Recurrent neural network.](html/images/9781032473246_C003_006.jpg)

[Figure 3.6](#ch10.xhtml#f34b) Recurrent neural network.

Generally, the deep feed-forward models may need specific parameters in each element to handle sequence data and are not capable of generalizing to variable-length sequences. On the other hand, RNNs efficiently work with sequential data by memorizing part of the input data and using them to make accurate predictions. The advantage is that RNN attains the sequential information in the input space. Thus, as depicted using different color codes in [Figure 3.7](#ch10.xhtml#f35), it considers the dependency among the words in the prediction process. In this example, the outputs `o1`, `o2`, `o3`, and `o4` at each time step are based on both the previous and current words.

![Figure 3.7 Sequence data processing in RNN.](html/images/9781032473246_C003_007.jpg)

[Figure 3.7](#ch10.xhtml#f35b) Sequence data processing in RNN.

Generally, in sequential data processing, it is necessary to consider the order of elements in the sequential data. As an example, when considering sequential data, such as natural language processing, it has input data in a sequence form and maybe the output data also in the sequence of elements. In this case, the order of sequence elements is important to have good predictive results. If we are using MLP to process this data, one solution would be to have input layers that contain a set of units equal to the set of elements in the input sequence. However, this will not work with variable-length sequences. Additionally, these input elements need to be in the same order. Sometimes, the same sentence may be expressed in various ways with different word reordering. Therefore, without a dataset that contains all these orderings for similar meanings, it will not be effective to learn an accurate model.

Recurrent neural networks are mainly designed to overcome problems in dealing with sequential data. In RNN, we have element-level models that are finally used together to form the final predictive model. The speciality of these models is that all element-level models share the same parameters. Therefore, it does not matter where the element is present in the sequence, as all of them are processed in the same manner and remain in the order in the outputs. Thus, each of these element-level models takes input from each element and the output of the element-level model of the previous element in the input sequence. After progressing in this way and after processing the final element in the sequence, the sequence data can be encoded to output the final element-level model. These output data can also be decoded into sequential outputs, such as speech recognition, and language translation.

Consider the property of parameter sharing across different time steps. The recurrence relationship to obtain a full chain of input is known as unfolding the equation. This shows the hidden state at any given time `t` as a function of parameters and sequence. With this, we can use fewer parameters for training, hence reducing the computational cost. As shown in [Figure 3.8](#ch10.xhtml#f36), `U`, `W`, and `V` are the three weight matrices that are shared throughout the time steps. Thus, the same weight propagates forward direction over time and the weights get an update during backward propagation.

![Figure 3.8 RNN architecture.](html/images/9781032473246_C003_008.jpg)

[Figure 3.8](#ch10.xhtml#f36b) RNN architecture.

In order to train an RNN model, we need to infer the parameters. That means, during the forward pass, the gradients of the models need to be derived by calculating through all the hidden states. This is known as unrolling the computational graph to compute hidden states and then using it to compute the gradients. These gradients are calculated using backpropagation, by sequentially going backwards in time starting from the gradient of hidden variable `h^((t))` to `h^((1))`, which is known as backpropagation through time.

When we talk about the challenges, vanishing and exploding gradient problems occur in deep RNNs with many time steps. During the model training, the error is calculated using the cost function at each time step and used backpropagation to update the weights. Therefore, every single neuron is associated with updating its weights to minimize the error. This vanishing gradient problem occurs when the error is moving backwards through all the neurons to get their weights updated. In RNN, the cost function that is used in a given time state will be used by other shallow layers to update their weights. Thus, the gradient value that is calculated at each step will be multiplied back through the weights earlier in the network. This causes the gradient to vanish if the weight is too small as the gradient becomes less and less with each multiplication. Based on the value of the weight `W`, this causes two main problems as follows:

*   When `W` is too small, this will cause a vanishing gradient problem.
*   When `W` is too large, this will cause an exploding gradient problem.
