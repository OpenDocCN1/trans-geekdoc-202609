
# Training vs Serving Systems
A training system aims to reduce the time to train without sacrificing accuracy. A serving or inference system aims to maximize the throughput constrained by a latency requirement. Product recommendations, search results, voice assistant queries, and pedestrian identification in autonomous vehicles, require real-time (low latency) results. Typically, only one data sample or a micro-batch is used at a time to meet the particular application’s latency requirement. Given the fewer computations per byte read from memory, the operational intensity or compute efficiency in GPUs and CPUs is lower in serving than in training.

## Nomenclature
A nomenclature note: in this book, a batch (sometimes called `mini-batch` in the literature) refers to a subset of training samples ranging from 1 to the entire dataset. A `full-batch` refers to a batch composed of the entire training dataset. A `micro-batch` refers to a batch with 1–8 samples. A `large-batch` refers to a batch size greater than 1,000 samples but less than the entire training dataset. A `node-batch` refers to the batch processed in a single node during distributed training, discussed in [Chapter 5](#15_Chapter05.xhtml).

In the remainder of this section, we introduce some components of `NNs` and describe the training process using a simple example. The primary compute operations in training and serving a model are multiplications and additions, which are typically computed in groups and represented as matrices.

## Training Process
Once a topology is defined, training involves learning a good set of weight values. The training steps for supervised learning are typically as follows:

### Supervised Learning Steps
1. Initialize the weights or parameters of the model typically by sampling from a zero-mean Gaussian or uniform distribution.
2. Forward propagate a training sample or, more commonly, a batch of samples through the network to compute the output.
3. Evaluate the cost or penalty using a metric of difference between the expected outputs (known from the training labels) and the actual outputs.
4. Backpropagate the gradient of the cost with respect to each layer’s weights and activations.
5. Update the weights of the model using the computed gradients.
6. Return to Step 2, or stop if the validation error is less than some threshold or is not decreasing.

### Iteration and Epoch
During training, the dataset is processed in batches. The completion of a cycle through steps 2–6 for a batch is called an `iteration`, and each cycle through the entire training dataset is called an `epoch`. For instance, if the dataset has `1*M` samples and a batch has 100 samples, it takes `10*K` iterations to complete an epoch.

Training a model may require tens of epochs to learn a good set of weights. After training, the validation (also called out-of-sample) performance is measured using a validation dataset. The validation dataset contains labeled data not used during training and should be as similar as possible to the serving data the model encounters when deployed. The performance on this validation dataset is a good indicator of the performance in deployment and helps to determine if the model overfits the training dataset. Overfitting occurs when a model learns features unique to the training data and, therefore, does not generalize to data outside the training dataset. Regularization techniques to mitigate overfitting are discussed in [Section 4.1](#14_Chapter04.xhtml#sub4-1).

## Serving / Inference
During serving, the model processes a micro-batch. The data is propagated forward through the network to compute the output. Serving is also known as inference since the model is inferring the label of the data sample. Step 2 above is inference; that is, inference is a step in the training process but usually with a smaller batch size and some optimizations specific to serving.

## Example: MNIST Digit Classification
The following example illustrates the training process. The task is to classify handwritten digits from the MNIST dataset using an `MLP` model \[LBB+98\]. [Figure 1.13](#11_Chapter01.xhtml#fig1-13) shows a small subset of the 70,000 gray-scaled 28 × 28 pixel images in the MNIST dataset. Typically with MNIST, 60,000 images are used for training and 10,000 images are used for validation. In practice, a `CNN` model would be a better choice for image classification, but a simple `MLP` model is used to introduce some fundamental concepts.

Each layer in the `MLP` is composed of units (neurons) that linearly combine the weighted outputs or activations from the previous layer plus a bias weight, as shown in [Figure 1.14](#11_Chapter01.xhtml#fig1-14) for one unit. The output from this affine transformation is passed to a nonlinear activation function `g(·)`. An `activation function` refers to the nonlinear function, an `activation input` is the input to the activation function, and an `activation` (short for `activation output`) refers to the output of an activation function. Common activation functions are the rectified linear unit (`ReLU`) and variants of `ReLU`, the `sigmoid` and its generalization, the `softmax`, and the hyperbolic tangent (`tanh`), which are all detailed in [Section 2.1](#12_Chapter02.xhtml#sub2-1).

![image](images/fig1_13.png)
Figure 1.13: Examples from the MNIST dataset. Each digit image has 28 × 28 pixels. Source: \[Wik17\] (CC BY-SA 4.0).

![image](images/fig1_14.png)
Figure 1.14: A neural unit at layer (`l` + 1) applies a nonlinear transformation or function to the weighted sum of the activations from the previous layer (`l`).

## MLP Architecture
The `MLP` model used for this digit classification task, shown in [Figure 1.6](#11_Chapter01.xhtml#fig1-6), has 784 units in the input layer (`Layer 0`) corresponding to the number of pixel values in each image. The output layer has 10 units corresponding to the probability distribution of the possible 0–9 labels. This `MLP` has two hidden layers with 128 and 32 units, respectively. The choice for the number of hidden layers and the number of units in each layer requires experimentation. In [Section 4.5](#14_Chapter04.xhtml#sub4-5), we discuss techniques to choose an appropriate topology.

## Forward Pass Details
To train the model, the 28 × 28 image pixel values are reordered as a 784 × 1 vector and normalized to zero-mean and unit-norm (the benefits of normalization are explained in [Section 2.6](#12_Chapter02.xhtml#sub2-6)). This is the input to the `NN` and can be thought of as the activations of `Layer 0`. The input `z[i]^{(1)}` to unit `i` in `Layer 1` is the weighted sum of the activations of `Layer 0` plus a bias. The activation `a[i]^{(1)}` of unit `i` is a nonlinear transformation of the unit’s activation input `z[i]^{(1)}`:

![image](images/pg18_1.png)

where `g(·)` is the `ReLU` activation function, and

![image](images/pg19_1.png)

is the output of the affine transformation (also known as the activation input in `Layer 1`), where `x[k]` represents the `k` ϵ \[0,783\]th pixel value. In this example, the activation functions are `ReLU` for `Layer 1` and `Layer 2`, and `softmax` for the output layer. The `ReLU` function zeros out negative values and keeps the positive values unchanged. The `softmax` function is used in the output layer to map a vector of values to a probability distribution where the values are all between 0 and 1 and sum to 1. The `i` th output value can be computed as follows:

![image](images/pg19_2.png)

where `ŷ[i]` represents the probability the input image corresponds to class `i`. There is no bias term in a `softmax` layer.

This `softmax` output is compared with the ground truth. For this task, the ground truth is a one-hot vector with the nonzero index corresponding to the correct class label. The crossentropy loss is:

![image](images/pg19_3.png)
