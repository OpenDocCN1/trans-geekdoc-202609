# Figure 3. CRNN model

![](bbox=[0.258, 0.172, 0.765, 0.483])

# IMPLEMENTATION USING TENSORFLOW

The entire SCRNN architecture is implemented using TensorFlow deep learning framework. Keras is used for ease of programming. Keras is a high-level API for TensorFlow. TensorFlow and Keras provide a flexible and robust platform for developing, training, and deploying deep neural networks.

The Python code snippet for implementing ShuffleNetV2 using TensorFlow and Keras is shown in Figure 4. The ShuffleNetV2() function specifies the ShuffleNetV2 architecture as a whole. To construct the model, numerous parameters such as scaling factor, bottleneck ratio, and number of shuffle units at each step are required. Layer by layer, the model is built, using convolutional layers, shuffle units, and a final output layer. Channel splitting, channel shuffling, and max pooling are all part of the design.

Figure 5 shows a snippet of Python code for implementing a shuffle unit with TensorFlow and Keras. The ShuffleUnit() method defines a basic ShuffleNetV2 building block. Depthwise separable convolutions, bottleneck layers, and channel shuffling are all part of it. When necessary, it also supports strided convolutions for downsampling.

Figure 6 presents Python code snippet for implementation of CRNN using TensorFlow and Keras. It defines the function CRNN() that takes an input shape as an argument. The input layer is defined with the shape specified by the shape argument. A 1D convolutional layer (CNN) is applied to the input data. Output of CNN layers pass through a BiLSTM layer. A dense layer (outputs) is added for classification. CRNN model is compiled using a custom optimizer. The loss function and performance metrics are set.

Figure 7 presents Python code snippet for implementation of SCRNN using TensorFlow and Keras. The TrainSCRNN() function starts by creating an SCRNN model using the CRNN function. The model's