
## TENSORFLOW

(Springenberg et al., 2015) performs very well because it employs solely convolutional layers with a minimal number of parameters rather than alternating convolutional and max-pooling layers. Numerous tiny networks perform better on a few resources due to their simple network topology. They often use the similarity operator and global max pooling to maximize the capacity of small networks. SqueezeNet (Iandola et al., 2016) reduces the count of channels from 3x3 to 1x1 to simplify networks without impairing network capacity. MobileNets (Howard et al., 2017) construct lightweight networks that operate well on embedded devices by utilizing depth-wise separable convolutions. Additionally, important works such as ShuffleNet (Zhang et al., 2017) and SEP-Nets have demonstrated that residual structure may effectively reduce computing complexity on mobile devices. Numerous studies use various types of CNNs as part of their model to analyze large amounts of data, which enhances overall performance.

The design of TensorFlow is taught in such a manner that the reader understands why it is a necessity for learning Keras. TensorFlow, as well as its underlying Python libraries, are discussed in this context. It is necessary to comprehend the compatibility of these packages to comprehend TensorFlow. Therefore, prior to learning researching Keras, it is necessary to explore TensorFlow in depth. TensorFlow is Google's most renowned library for deep learning applications. The toolkit is designed to operate on CPU, GPUs, TPU processors, neural net devices, etc. This library first opened to the general public in 2015. In 2017, though, a stable version was made available under the Apache Open-sourced License. Libraries licensed under the Apache Open-sourced License may be used, modified, and transferred without paying a fee to Google. Tensors are indeed the multiple arrays that TensorFlow accepts as input. TensorFlow is named after the flow of multidimensional arrays. These Tensors enter the system from input at one end and undergo many processes before producing output.

TensorFlow's core algorithms are developed in C and CUDA, a parallel processing language. NVIDIA created a system and API. It offers APIs in multiple languages. Python's API is among the most robust and extensive.

TensorFlow (Abadi et al., n.d., 2016) script is divided into two phases constructing a computational graph and executing the computational graph. Inside the building phase, TensorFlow functions are often used to generate a computational graph that depicts a deep learning model. This graph consists of both edges and nodes. The edges represent tensor data that will flow through graphs, which gives the framework its name, TensorFlow. Operations are indeed the nodes that describe calculations on tensors. The input of an operation is zero or more tensors, and the output is zero or more tensors. TensorFlow offers fundamental building pieces, including fully-connected layers, a convolutional layer, an RNN module, and nonlinear activation units.

These operations are the significant elements of a computational graph that perform the calculation from model input to output. In addition, TensorFlow provides a variety of loss functions, including cross-entropy and mean squared error. With a forward pass of neural networks, the model is concluded by adding loss compute operations to the output tensor. The basic modules of TensorFlow are shown in Figure 4.

Keras is a Python-based Framework for neural networks that enables the execution of TensorFlow and Theano. tf.Keras is the syntax for using Keras in Python. It operates based on the following basic concepts: Customer interaction: Modularity, easiness of expansion, and Implementation in Python.

Figure 4. TensorFlow architecture

![](img/20813928ec98c7f6fbdbab0d52bde2f1_80_0.png)

Models represent the most significant data structures inside the Keras language. For example, sequential is an often-used model.

## TENSORBOARD

Models of neural nets are often extensive and complex, which may lead to misunderstanding. TensorBoard is a graphical device that makes TensorFlow applications simpler to comprehend and debug. Users may quickly see the computation graph of a network, learning metrics, and parameter settings using TensorBoard. The TensorFlow component tf.summary generates operations to capture training metrics and store graph definition. Additionally, it stores them on disk as an event collection in a manner that TensorBoard could read. When TensorBoard is started, those files will be displayed in a web browser. Deep learning algorithms tend to outperform conventional approaches as the number of data grows. However, this increases the algorithm’s complexity and, thus, its interpretability. In addition, the intricacy complicates hyperparameter adjustment. TensorBoard is the answer (Fasi et al., 2021). The TensorFlow team developed this visualization module to reduce the complexities of neural nets. It may be used to build several kinds of graphs. For profiling with TensorFlow, the prerequisites must be initially satisfied, and all required plugins must be added, as shown in Figure 5.

Figure 5. TensorBoard plugins

![](img/20813928ec98c7f6fbdbab0d52bde2f1_80_1.png)

## Components

It includes the following elements, notably:

- Scalars: Due to the high number of epochs, it is impossible to evaluate the accuracy and inaccuracy for each epoch, and there is a risk of becoming trapped in local minima rather than global ones. These two issues may be resolved by utilizing the information in this section. It provides accuracy and error graphs concerning epochs, as shown in Figure 6.

- Graphs: The subsection depicts the “model.summary()” findings using graphs as shown in Figure 7. In other words, it renders neural network design more attractive. This facilitates the process of architectural comprehension.

- Distributions: Typically, neural networks are constructed of many layers, each including a large number of biases and weights. This segment describes the distribution of various hyperparameters, as shown in Figure 8.

- Histograms: All hyperparameters are shown in the histograms, as shown in Figure 9.

- Time-Series: Contains the same values throughout time, as shown in Figure 10. By evaluating the trends of the hyperparameters, these parts are essential for regulating them.

Figure 6. Scalars in tensor board

![](img/20813928ec98c7f6fbdbab0d52bde2f1_81_0.png)

Figure 7. Graphs in tensor board

![](img/20813928ec98c7f6fbdbab0d52bde2f1_81_1.png)

## Understanding Convolutional Neural Network With TensorFlow

Figure 8. Distribution in tensor board

![](img/20813928ec98c7f6fbdbab0d52bde2f1_82_0.png)

Figure 9. Histogram in tensor board

![](img/20813928ec98c7f6fbdbab0d52bde2f1_82_1.png)

Figure 10. Time series in tensor board

![](img/20813928ec98c7f6fbdbab0d52bde2f1_82_2.png)

Figure 11. Tensor board CNN graph

![](img/20813928ec98c7f6fbdbab0d52bde2f1_83_0.png)

Figure 12. Hyperparameters in tensor board

### evaluation_accuracy_vs_iterations

![](img/20813928ec98c7f6fbdbab0d52bde2f1_84_0.png)

### evaluation_loss_vs_iterations

![](img/20813928ec98c7f6fbdbab0d52bde2f1_84_1.png)

Figure 13. Dataset used for model

```
fashion_mnist = tf.keras.datasets.fashion_mnist
(x_train, y_train),(x_test, y_test) = fashion_mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-labels-idx1-ubyte.gz
29515/29515 [==============================] - 0s 0us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-images-idx3-ubyte.gz
26421880/26421880 [==============================] - 1s 0us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-labels-idx1-ubyte.gz
5148/5148 [==============================] - 0s 0us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-images-idx3-ubyte.gz
4422102/4422102 [==============================] - 0s 0us/step
```

Figure 14. NN model

| Layer (type) | Output Shape | Param # |
|---|---|---|
| flatten_1 (Flatten) | (None, 784) | 0 |
| dense_2 (Dense) | (None, 512) | 401920 |
| dropout_1 (Dropout) | (None, 512) | 0 |
| dense_3 (Dense) | (None, 10) | 5130 |

Total params: 407,050
Trainable params: 407,050
Non-trainable params: 0

Figure 15. NN training

```
Train on 60000 samples, validate on 10000 samples
Epoch 1/5
60000/60000 [==============================] - 11s 184us/sample - loss: 0.4968 - accuracy: 0.8223 - val_loss: 0.4216 - val_accuracy: 0.8481
Epoch 2/5
60000/60000 [==============================] - 11s 176us/sample - loss: 0.3847 - accuracy: 0.8587 - val_loss: 0.4056 - val_accuracy: 0.8545
Epoch 3/5
60000/60000 [==============================] - 11s 176us/sample - loss: 0.3495 - accuracy: 0.8727 - val_loss: 0.3600 - val_accuracy: 0.8700
Epoch 4/5
60000/60000 [==============================] - 11s 179us/sample - loss: 0.3282 - accuracy: 0.8795 - val_loss: 0.3636 - val_accuracy: 0.8694
Epoch 5/5
60000/60000 [==============================] - 11s 176us/sample - loss: 0.3115 - accuracy: 0.8839 - val_loss: 0.3438 - val_accuracy: 0.8764
```

If you examine the graph, you can comprehend how the model operates. Add the data to that same model's queue: After every iteration, give the model the batch size in data, i.e., the number of information feeds. Load the Tensors with the data. Develop the model. Show the complete number of training
