
33\. Madhav, A.V.S. and Tyagi, A.K., The world with future technologies (Post-COVID-19): Open issues, challenges, and the road ahead. In: *Intelligent Interactive Multimedia Systems for e-Healthcare Applications*, A.K. Tyagi, A. Abraham, A. Kaklauskas (eds.), Springer, Singapore, 2022, [`https://doi.org/10.1007/978-981-16-6542-4\_22`](https://doi.org/10.1007/978-981-16-6542-4_22).

34\. Mishra, S. and Tyagi, A.K., The role of machine learning techniques in Internet of Things based cloud applications. AI-IoT book, Springer, 2021.

35\. Pramod, A., Naicker, H.S., Tyagi, A.K., Machine learning and deep learning: Open issues and future research directions for next ten years, in: *Computational Analysis and Understanding of Deep Learning for Medical Care: Principles, Methods, and Applications*, 2020, Wiley Scrivener, 2020.

36\. Nair, M.M. and Tyagi, A.K., Privacy: History, statistics, policy, laws, preservation and threat analysis. *J. Inform. Assur. Sec.*, 16, 1, 24–34, 11p, 2021.

37\. Tyagi, A.K., Fernandez, T.F., Mishra, S., Kumari, S., Intelligent automation systems at the core of industry 4.0. In: *Intelligent Systems Design and Applications. ISDA 2020. Advances in Intelligent Systems and Computing*, A. Abraham, V. Piuri, N. Gandhi, P. Siarry, A. Kaklauskas, A. Madureira (eds.), I, vol. 1351, Springer, Cham., 2021, [`https://doi.org/10.1007/978-3-030-71187-0\_1`](https://doi.org/10.1007/978-3-030-71187-0_1).

1.  [*](#c06.xhtml#aut1)*Corresponding author*: [`shreyas.madhav@gmail.com`](mailto:shreyas.madhav@gmail.com)

# Part 2  

# INTRODUCTION TO DEEP LEARNING AND ITS MODELS

# 7  

# Deep Learning Methods for Data Science

**K. Indira^([1](#c07.xhtml#aff1)), Kusumika Krori Dutta^([1](#c07.xhtml#aff1))[\*](#c07.xhtml#raut1), S. Poornima^([2](#c07.xhtml#aff2)) and Sunny Arokia Swamy Bellary^([3](#c07.xhtml#aff3))**

*^([1](#c07.xhtml#raff1))M.S. Ramaiah Institute of Technology, Bengaluru, India*

*^([2](#c07.xhtml#raff2))Anna University, Chennai, India*

*^([3](#c07.xhtml#raff3))Charlotte, NC, United States*

> ***Abstract***

> Deep learning network (DLN) is defined as the neural network characterized by complex connected layers to handle a large volume of data, automatic extraction of features, and representation learning for identification and regression problems. This concise chapter on deep learning (DL) methods for data science takes readers through a series of program-writing tasks that introduce them to the use of different DL techniques in various areas of artificial intelligence (AI). It covers zen and tao of the various types of DL methods such as convolutional neural network, recurrent neural network (RNN), denoising autoencoder (DAE), recursive neural network, deep reinforcement learning, deep belief networks (DBNs), and long short-term memory (LSTM), i.e., starting from architecture, learning rules, mathematical model to programing aspects explained in this chapter. The developed and emerging structures of DLN has been applied in applications according to the depth of computational graph, learning, and performance. The knowledge of merits and demerits of each method can train reader toward selection of best suited technique for a given problem statement. For example, the evolution of RNN-based DL architecture innovated many applications in time series, biological, speech-to-text conversion, which has sequence dependent data. RNN handles both real values (time series) and symbolic values of variable length inputs. This chapter covers varieties of application with example to give reader an overall learning. The formulation of this chapter highlights the improvement in applications (such as language, text, signal, and image processing) by modifications in network configuration. This AI technique summarizes the necessity, development, strength, and weakness of DLN models used in data science which will integrate all the basic cores of engineering in near future.

> ***Keywords*:** Deep learning, RNN, CNN, DBN, LSTM, deep reinforment learning, recursive NN

## 7.1 Introduction

Artificial neural networks or ANNs are the computational systems modeled after the biological neural networks of physical brains and designed to mimic them. They consist of an input layer, multiple hidden layers in between, and an output layer. Each layer has numerous processing units called neurons.

A neuron, the basic unit of a neural network, takes multiple inputs and returns a single output. In a feedforward neural network, the neuron outputs in one layer are fed as input to the succeeding layer neurons. The input layer, the first layer of the chain, receives input signals from the user, and the output layer is the last layer in the chain which returns its outputs to the user. A neural network may have multiple inputs and multiple outputs.

Deep learning (DL) also known as deep neural networks \[1–3\] is based on ANN concept where more number of layers or more numbers of neurons in each layer or both, i.e., deeper layers, and more numbers of neurons are used. More number of layers provides more iteration and increases efficiency of the net but at the same time it increases complications in handling. Whereas, more number of neurons provides ability to extract more features from the given datasets.

In this chapter, some of the DL methods are discussed in details.

## 7.2 Convolutional Neural Network

Convolution generates a signal by combining two signals mathematically. For grayscale images (2D data), the convolution operation between a filter (kernel) `W^k[1]^(xk)[2]` and an image `X^(N1xN2)` is given by [Equation (7.1)](#c07.xhtml#eq7-1). This equation allows the kernel to be centered on pixel of interest.

[(7.1)](#c07.xhtml#req7-1)![](images/eq7-1.jpg)

Thus, if the image is 2D, a 2D filter is used to slide over the input image, and if the image is color (RGB), a 3D case, a 3D filter is used which is refereed as a volume, and to perform convolution, 3D filter will slide over the volume over the 3D input and the effect is that 2D convolution operation is performed on a 3D input as the filter is moved right or left and not along the depth. Thus, multiple filters can be used to get multiple feature maps. If the input is of dimension Width (`W[1]`) × Height (`H[1]`) × Depth (`D[1]`), the spatial filter is of size (`F × F`), with the depth of the filter is the same as depth of input. To apply the kernel at the corners, pad inputs appropriately (`P`) and use strides `S` which defines the interval at which the filter is applied. The dimensions of the output with Width (`W2`) × Height (`H2`) is given in [Equations (7.2)](#c07.xhtml#eq7-2) and [(7.3)](#c07.xhtml#eq7-3), respectively.

[(7.2)](#c07.xhtml#req7-2)![](images/eq7-2.jpg)[(7.3)](#c07.xhtml#req7-3)![](images/eq7-3.jpg)

The depth of the output layer depends on the quantity of filters used. If `K` such filters are used, then the output dimension will be `W[2] × H[2] × K`. In case of traditional machine learning, hand-crafted features such as `SIFT`, `HOG`, and `LBP` are extracted, whereas in `CNN` \[4–7\], there are multiple layers of meaningful filters/kernels for extracting the features. These kernels are treated as parameters and weights are learned through backpropagation.
