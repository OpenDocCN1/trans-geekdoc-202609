
In the preceding equation, we applied ReLU over a ReLU, that is, \( G(G(z^{(l)}))\) and we got the same output. As ReLU is used to replace the negative value with zero and only retain positive value, for example, we have a value of \( z^{(l)} = 0.96 \) and then we apply ReLU over this, that is, \( G(z^{(l)}) = G(0.96) = 0.96 = say(a^l)\), that is, \( a^l = 0.96 \). Now if we again apply ReLU over this, that is, \( G(G(z^{(l)})) = G(a^l) = G(0.96) = 0.96 = a^l \). Therefore, \( a^{(l+2)} = a^l \).

So, by reducing the weights and biases, what we learnt at \( a^l \) reappears at \( a^{(l+2)} \), i.e., identity mapping. By adding more and more layers, we can achieve a good amount of non-linearity. In these types of residual blocks, we get more performance by adding more and more layers, or we will not get anything less than what we have achieved before. Also, there exists one more problem with respect to the dimension of \( z^{(l+2)} \) and \( a^l \) as both are added for getting residual connection output. As \( a^{(l+2)} = G(z^{(l+2)} + a^l) \) and we can see here that \( z^{(l+2)} + a^l \) are added by assuming the same dimensions. But they may have different dimensions say \( z^{(l+2)} = 256 \) and \( a^l = 128 \). So, to resolve this issue, we have to learn a matrix \( W_s \), in such a way that both dimensions can be same. For this, either we can do padding or reduce the size to fixed size so that both factors can be added easily. So, the equation for \( a^{(l+2)} \) gets modified as follows: \( a^{(l+2)} = G(z^{(l+2)} + W_s a^l) \)

Figure 4.185 shows the series residual connection among various convolutional layers:

![](img/7e519fee1b702b91799cdf1664598392_347_0.png)

Figure 4.185: Residual connections

Figures 4.186 and 4.187 show the architecture of a 34-layered plain neural network and the ResNet, respectively:

## 34 Layer Plain Neural Network

![](img/7e519fee1b702b91799cdf1664598392_348_0.png)

Figure 4.186: 34-layer plain deep neural network in figure 4.186, a 34-layer deep neural network with 7x7x3 and 3x3x3 convolutional filters with a number of filters as 64, 128, 256, and 512, whereas in 4.187 the same 34-layer deep neural network is represented using residual connections shown by solid arcs.

## 34 Layer ResNET

- Image
- 7*7 Conv, 64, /2
- Pool, /2
- 3*3 Conv, 64
- 3*3 Conv, 64
- 3*3 Conv, 64
- 3*3 Conv, 64
- 3*3 Conv, 64
- 3*3 Conv, 128, /2
- 3*3 Conv, 128
- 3*3 Conv, 128
- 3*3 Conv, 128
- 3*3 Conv, 128
- 3*3 Conv, 128
- 3*3 Conv, 256, /2
- 3*3 Conv, 256
- 3*3 Conv, 256
- 3*3 Conv, 256
- 3*3 Conv, 256
- 3*3 Conv, 256
- 3*3 Conv, 256
- 3*3 Conv, 256
- 3*3 Conv, 512, /2
- 3*3 Conv, 512
- 3*3 Conv, 512
- 3*3 Conv, 512
- 3*3 Conv, 512
- Average Pooling
- Fully Connected, 1000

Figure 4.187: 34 Layer ResNET

When we use the plain neural network, the real value of the training error increases significantly after a certain value of the number of layers, as shown in figure 4.188:

![](img/7e519fee1b702b91799cdf1664598392_350_0.png)

Figure 4.188: Plain deep neural network training error

If we use ResNet, the value of the training error reduces significantly with an increase in the number of layers, as shown in figure 4.189:

![](img/7e519fee1b702b91799cdf1664598392_350_1.png)

Figure 4.189: ResNET training errors

## Inception module

Inception modules in CNN use stacked (1*1) convolution to perform the computation more efficiently in deep neural networks. Along with the computational costs, these modules also solve the issue of overfitting effectively. Moreover, if we want to mix different-sized filters within a single convolutional layer, it gives different features like fine-level or coarse-level features. All the filters, such as 3*3, 5*5, and 1*1, are concatenated in a single module, and it reduces the number of computations also. Before moving to the inception module, first let us discuss (1*1) convolution.

## (1 * 1) Convolution

The convolution of size (1*1) means mapping the input pixel with all its channels to the output pixel. It is used to reduce the computation complexity by reducing the dimensionality of the feature map. The 1*1 convolutions reduce the depth of feature maps.

Suppose we have an input of size (12*12*480), and we want to perform a (5*5) convolution as follows:

![](img/7e519fee1b702b91799cdf1664598392_351_0.png)

If we observe figure 4.190, 48 filters of size (5*5) are used to convolve the input image of size (12*12*480). Then, the number of operations involved in convolution is given as (12*12*48)*(5*5*480) = 82.944 Million. But, if we use (1*1) convolution before using the (5*5) filter, then the number of activation maps gets reduced to 16, as shown in figure 4.191:

![](img/7e519fee1b702b91799cdf1664598392_351_1.png)

Now, observe figure 4.192:

![](img/7e519fee1b702b91799cdf1664598392_352_0.png)

Figure 4.192: Inception process

First, we have used 16 filters of size (1*1*480), and then 48 filters of size (5*5*16) are used to convolve on the feature maps got after (1*1) convolutions of size (12*12*16). So after applying 48 filters of (5*5*16) size, we get the final number of activation maps as (12*12*48) same as we got in figure 4.192, but with a reduced number of computations as follows. The size of the final feature map remains the same as in figure 4.192. Then, there is the number of operations involved in (1*1) convolution followed by (5*5) convolution.

The total number of operations required for (1*1*480) convolution:

(12 * 12 * 16) * (1 * 1 * 480) = 1.105 Million

And the total number of operations required for (5*5*16) convolution:

(12 * 12 * 48) * (5 * 5 * 16) = 2.76 Million

Adding these two, we get 1.105 + 2.76 = 3.865 Million. In total, 3.865 Million is much smaller as compared to 82.944 Million. Hence, adding (1*1) convolution helps in reducing the model size, which is good to handle overfitting problems:

![](img/7e519fee1b702b91799cdf1664598392_352_1.png)

Figure 4.193: Structure of the inception block

Figure 4.193 shows the basic structure of an inception block having four parallel paths. The convolution layers of window sizes of 1*1, 3*3, and 5*5 are used in the inception block. Two middle paths use 1*1 convolution followed by 3*3 and 5*5 to reduce the size of input channels (depth) before passing it to the next convolution layer. So, at the right side (fourth path) of the inception module, 3*3 max pooling is used with a stride of two. When we do max pooling, then depth does not get affected. In this inception module, we do pooling in such a way that the size of the input image remains the same. For getting the same size, we have to do padding such that the input image size will remain the same. For example, say my feature size from the previous layer is 12*12*480. Then, after applying max pooling with stride two, it gets reduced to, say, 6*6*480. So, to make it as 12*12*480 after applying max pooling, we have to do padding of two on all the sides. Furthermore, we have to apply 48 filters of size 1*1*480 so that we get the same output as 12*12*48 through the fourth path. So, the size of all the outputs from each and every path of the inception module is the same as 12*12*48, which are to be concatenated finally to get aggregated feature maps as shown in figure 4.193:

## GoogleNet

GoogleNet is another type of CNN architecture that uses a stack of nine inception modules, and finally, average pooling is done to predict the output. The use of max pooling initially before the inception module reduces the dimension size of the input image by a significant amount. The initial part of the GoogleNet is similar to AlexNet, and the stack of the multiple blocks is taken from the VGGNet.

In the architecture of GoogLeNet, as shown in figure 4.194, initially, we perform normal convolution to reduce the size of the input image by applying certain convolutions. As if we apply the inception module directly to the image, after applying 1*1 convolutions, we get a lot of feature maps, and that leads to a lot of computations and parameters.

**Role of side branches in GoogLeNet:** In figure 4.195, some side branches have evolved in the fourth and seventh inception modules. What is the role of these side branches? When we are concatenating **inception modules (IM)** in between, we are getting some features. With side branches, we take in between features and do some type of classification and check whether these features are worthy or not for the final classification. It is a type of regularization. We are regularizing our network and saying that not only do the final features have to be good, but whatever we are getting here with the side branches also has to do something related to my final classification. There also has to be some kind of understanding of what our classification problem
