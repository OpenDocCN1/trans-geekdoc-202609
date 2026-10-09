$$\begin{equation}p(S_{t}\vert S_{t-1}, S_{t-2}, \cdots, S_{1}, C_{t}) = g(h_{t}, S_{t-1}, C_{t})\tag{14}\end{equation}$$

where g represents the given activation function. The softmax is used as the activation function for this stage in the EGA model. The largest output value of $p(S_{t}\vert S_{t-1}, S_{t-2}, \cdots, S_{1}, C_{t})$ is treated as the output value of the $t$-th timestep. Ultimately, the output values of each timestep make up the output sequence of the model.

# **4. Data Experimental**

# 4.1. Experimental Data

The dataset used in this article comes from the Inner Mongolia Normal University and includes 9479 handwritten Mongolian characters, totalling 47,395 images. The dataset covers various handwriting styles and samples from different writers, with a wide variety of fonts, and each character has a clear shape, which is highly representative and can truly reflect the features of Mongolian handwriting styles. Furthermore, the dataset is balanced, i.e., the number of images per character is similar among them. All these characters are carefully handwritten and drawn by writers, closely related to practical application scenarios and are highly authentic and practical, making them suitable for data training and testing for handwriting character recognition tasks. Some offline Mongolian handwriting sample images of the dataset are shown in Figure 7.

![](bbox=[0.17, 0.39, 0.84, 0.64])

# 4.2. Model Training Platform

According to the training requirements of the Mongolian handwriting recognition model, the model training environment built in this paper is shown in Table 1.

Table 1. Model Training Platform Parameters.
| Name | Parameters |
|:---:|:---:|
| CPU | Intel Core i7-6700 CPU@3.40 GHz |
| GPU | Nvidia Tesla P100 + Huawei GPU Server |
| Operating system | Ubuntu 16.04.6 |
| Programming language | Python 3.7 |
| Deep learning framework | Pytorch 1.9.0 |

# 4.3. Indicators for Model Performance Evaluation

The quality of the Mongolian handwriting recognition model is primarily measured during the training process from two aspects: the recognition accuracy for the test set and the complexity of the trained model.