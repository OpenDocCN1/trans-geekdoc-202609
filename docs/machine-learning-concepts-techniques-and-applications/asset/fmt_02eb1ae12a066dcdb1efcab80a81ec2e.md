
Convolutional neural networks are neural networks that are mostly used in image classification, object detection, face recognition, self-driving cars, robotics, neural style transfer, video recognition, recommendation systems, and so on.

CNN classification takes any input image and finds a pattern in the image, processes it, and classifies it in various categories such as car, animal, or bottle. CNN is also used in unsupervised learning for clustering images by similarity. It is a very interesting and complex algorithm, which is driving the future of technology.

### 15.8.1 Biological Connection to CNN

When you first heard of the term `convolutional neural networks`, you may have thought of something related to neuroscience or biology, and you would be right. CNNs do take a biological inspiration from the visual cortex. The visual cortex has small regions of cells that are sensitive to specific regions of the visual field.

This idea was expanded upon by a fascinating experiment by Hubel and Wiesel in 1962 where they showed that some individual neuronal cells in the brain responded (or fired) only in the presence of edges of a certain orientation. For example, some neurons fired when exposed to vertical edges and some when shown horizontal or diagonal edges. Hubel and Wiesel found out that all of these neurons were organized in a columnar architecture and that together they were able to produce visual perception. This idea of specialized components inside of a system having specific tasks (the neuronal cells in the visual cortex looking for specific characteristics) is one that machines use as well and is the basis behind CNNs.

### 15.8.2 The Architecture of Convolutional Neural Networks (CNNs)

The term `convolution neural networks` indicates that these are simply neural networks with some mathematical operation (generally matrix multiplication) in between their layers called convolution.

It was proposed by Yann LeCun in 1998. It’s one of the most popular uses in image classification. A convolution neural network ([Figure 15.18](#ch15.xhtml#fig15_18)) can broadly be classified into these layers:

![Figure 15.18 Convolutional neural network.](`images/fig15_18_B.jpg`)

[Figure 15.18 Convolutional neural network.](#ch15.xhtml#R_fig15_18)

*   **`Convolutional layer`**: The `convolutional layer`’s main objective is to learn or extract all the features of the image which would help in object detection. As we know, the input layer will contain some pixel values with some weight and height; our `kernels` or `filters` will convolve around the input layer and give results which will retrieve all the features with fewer dimensions. This is done by `convolution filtering`, where a window representing the feature of the image is dragged over the input and the convolution product between the feature and each portion of the scanned image is calculated. We finally get a `feature map` that is an image and a filter giving the features of the image. This layer performs many tasks such as `padding`, `striding`, and applying the `kernels`, and hence this layer is considered as a building block of convolutional neural networks.

*   **`Pooling layer (optional layer)`**: A `pooling layer`, optionally placed between two layers of convolution, reduces the spatial volume of the input image after convolution while preserving the important characteristics. This layer improves the efficiency and avoids overfitting.

*   **`Output layer`**: The `fully connected layer` is the last layer of the CNN as is the case of any neural network. This layer applies a linear combination and then possibly an `activation function` to produce the output. This layer classifies the image and returns as output vector of size `N` where `N` is the number of classes of our task and each element of the vector indicates the probability of the input belonging to that particular class.

### 15.8.3 Convolutional Networks in the History of Deep Learning

A convolutional neural network (CNN) is a particular class of neural networks, used mainly for image analysis. CNN architectures have evolved, giving results that are comparable to those obtained via human execution/intervention. A wide variety of architectures are available and can be applied depending on the task to be carried out.

*   **`Neocognitron (1980)`**: `Neocognitron` was the originator of CNNs. It introduced the concepts of feature extraction, `pooling layers`, and using convolution in a neural network with the objective of recognition or classification. The configuration of the network is based on human visual perception. It is a hierarchical, multilayered neural network with layers of `S-cells` (simple cells) and `C-cells` (complex cells) arranged alternately and was designed for handwritten (Japanese) character recognition. The process of feature extraction by `S-cells` and toleration of positional shift by `C-cells` was alternatively repeated where local features extracted at lower stages were gradually integrated into more global features.

*   **`LeNet-5 (1989–1998)`**: `LeNet`, largely developed for handwritten digit recognition, was proposed by Yann LeCun and team and was responsible for the term “convolutional neural network.” It used `5 x 5` convolution filters with a `stride` of `1`. The `pooling` (subsampling) layers were `2 x 2` with a `stride` of `2` and had `60 K parameters`.

    The `ImageNet` (a data set) classification challenge started in 2010 and was mainly responsible for the newer architectures of CNN and led to research in machine learning and computer vision models, for image classification, using a common data set. In 2010, a system developed without using neural networks had a winning error rate of `28.2%`. In 2011, researchers improved the score from `28.2%` to `25.8%` error rate. In 2012, Alex Krizhevsky and Geoffrey Hinton introduced a CNN architecture, `AlexNet`, which reduced the error further to `16.4%`, marking a significant improvement in performance.

*   **`AlexNet (2012)`**: `AlexNet` was the first winner of the `ImageNet` challenge based on a CNN, and since then every year’s challenge has been won by a CNN-based system, significantly outperforming other deep as well as traditional machine learning methods. Here the normalization layer, called the `response normalization layer`, and a rectified linear unit (`ReLU`) as an `activation function` were first introduced.

*   **`ZFNet (2013)`**: In 2013, `ZFNet` (named after its designers Zeiler and Fergus), similar to `AlexNet`, with few changes in `hyper-parameters` was the winner of the `ImageNet` challenge. The careful selection of `hyper-parameters` resulted in a significant decrease in error from `16.4%` to `11.7%`.

*   **`VGGNet (2014)`**: The year 2014 saw the introduction of a new architecture known as the `VGGNet` by the Visual Geometry Group (at Oxford University). Problems could be solved better with lower error rate on the `ImageNet` classification challenge by increasing the depth of the network and hence handling nonlinearities in the function. The architecture won the runner-up in the `ImageNet` challenge in 2014.

*   **`GoogLeNet (2014)`**: In 2014, Google introduced `GoogLeNet`, where design of deeper networks with the objective of greater efficiency to reduce parameter count, memory usage, and computation was considered. There were `22 layers` but without any `FC layers` (fully connected layers), reducing the total number of parameters. `GoogLeNet` became the `ILSVRC-14` classification winner with `6.7%` error.
