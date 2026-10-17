
In recent years, the deep learning model, especially the deep convolution neural network (CNN), has been shown to yield competitive performance image \[13–15\], speech \[16\], and language \[17\]. However, most of the CNN network input data are original image without any preprocessing based on the prior knowledge. Such manner directly extends the CNN network training time and the feature extraction time \[18, 19\]. Besides, the traditional training algorithm based on gradient descend technique may lead to entrapment in local optimum and gradient dispersion. Moreover, there is little study on the convergence rate and smoothness improvement of CNN framework based on exponential momentum deep convolution neural network (EM-CNN). And an innovative method for updating parameters of the CNN on the basis of exponential momentum gradient descendent is proposed aiming at the problem of gradient diffusion of deep network.

The rest of the paper is organized into four sections. Section 2 describes the feature learning and deep learning. The proposed EM-CNN framework is introduced in Section 3, while Section 4 details the new way of exponential momentum gradient descent method, which yields the highest accuracy compared with homologous parameters momentum updating methods.

Section 5 is the experiment results. Section 6 summarizes the results and draws a general conclusion.

# FEATURE LEARNING

Feature extraction is necessary and useful in the real-world for that the data such as images, videos, and sensor measurement data is usually redundant, highly variable, and complex. Traditional handcrafted feature extraction algorithms are time-consuming and laborious and usually rely on the prior knowledge of certain visual task. In contrast, feature learning allows a machine to both learn at a specific task and learn the features themselves.

Deep learning is part of a broader family of machine learning based on learning representations of data. It attempts to model high-level abstractions in data by using a deep graph with multiple processing layers, composed of multiple linear and nonlinear transformations. Typical deep learning models include autoencoder (AE) \[20\], deep restricted Boltzmann machine (DRBM) \[21\], deep Boltzmann machines (DBM) \[22\], deep belief networks (DBN) \[23\], stacked autoencoder (SAE) \[24\], and deep convolutional neural networks (DCNN) \[25\].

The deep convolution neural network (DCNN), a kind of neural network, is an effective method for feature extraction, which can potentially lead to progressively more abstract and complex features at higher layers, and the learnt features are generally invariant to most local changes of the input.

as object detection \[13–15\], speech simultaneous interpretation \[16\], and depends on the features \[26\], we adopt deep convolution neural network (DCNN) framework.

# STRUCTURE DESIGN OF HYPERSPECTRAL DATA CLASSIFICATION FRAMEWORK

In deep convolutional neural network, input data, convolution kernel, and threshold parameter are the three most important issues \[27–29\]. The input tion performance.

The size of the convolution kernel determines the degree of abstraction of the feature. If convolution kernel size is too small, the effective local exceed the feature range that convolution kernel can express. Threshold parameter is mainly used to control the degree of response of characteristic submode. Besides, the network depth and dimension of output layer can also The deeper network layers indicate stronger feature expression ability, of output layer directly determines the convergence speed of network.

When the sample sets are limited, over lower dimension of the output layer cannot guarantee the validity of features, while over higher feature of the output layer will produce feature redundancy.

Since the traditional CNN input the original image directly into the deep \[28, 29\], three images obtained by image data preprocessing are used as performance. In order to obtain better extraction features, the sizes of con- network is seven according to the results of the experiments.

Besides, the lower sampling applies Max-pooling and the nonlinear mapping function is LREL function, which is shown in the following formula:

```
(1)
```

where ߝ is nonzero small constant and ݓ is the weight of neuron. The setting of ߝ ensures that inactive neurons receive a nonzero gradient value, so that the neuron has the possibility of being activated.

Based on the above analysis, a deep network framework for hyperspectral based on deep convolutional neural network is proposed in Figure 1.

In the proposed deep CNN model, the first layer, the third layer, and the fifth layer are convolution layers, which realized feature extraction from lower level to higher level. The second layer, the fourth layer, and the sixth layer are lower sampling layers, used for feature dimension reduction. The final layer is the output layer which is whole connection layer and output of the final extraction features.

# EXPONENTIAL MOMENTUM GRADIENT DESCENT ALGORITHM

## Error Transfer

Error transmission descends by two steps through forward propagation and reverse gradient, to conduct weight generation and adjustment. Using gradient descent method to update weight is shown in formula (2), and bias updating method is shown in formula (3) \[30\]:

```
(1)
(2)
```

**Figure 1**

In the formula, ߟ is the learning rate, is the gradient of error to weight, and is the gradient of error to bias, namely, the sensitivity of parameter adjustment. In order to achieve weight and bias optimizing, the gradient of error to weight and the gradient of error to bias must be first obtained.

For convolution layer, its output is shown as the following formula: (3)

where ܾ is the bias of ݆ is the block of in- ݆ ݆ put feature diagram, and is convolution kernel. According to derivation formula of sensitivity function, the sensitivity of convolution layer can be represented by the following formula:

```
(4)
```

where is the convolution kernel of ݈+1 sampling layer, up represents upper sampling, and is 1/4 of , so upper sampling should be conducted.لsymbol represents the multiplication of corresponding elements Thus, the gradient of convolution layer error to bias is shown in formula (6). In the formula, (ݑ, V) is the element location of sensitivity matrix: (5)

```
(5)
```

The gradient of convolution layer error to weight is shown in formula (7). In the formula, is the convolution block of and convolution kernel ܭ݆݅, (ݑ, V) is the element location of the block:

```
(6)
```

Substitute formula (5), (6) into formula (1), (2) and obtain the updated value of convolution layer’s weight.
