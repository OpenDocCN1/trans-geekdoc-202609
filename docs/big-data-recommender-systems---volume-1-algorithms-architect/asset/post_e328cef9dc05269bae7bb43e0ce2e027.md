
# 308 Big data recommender systems, volume 1

carry out attack rogue website. In this attack, unsolicited contents are displayed in the form of SQL injection, malware interception, phishing, etc. This leads to losing sensitive information in the hands of fraudsters. World Web is the largest platforms that attackers use. Attackers implement phishing code and broadcast it across the web [34].

This highlights the need for an efficient algorithm to circumvent these activities. Developing an effective phishing detection system will abate the increasing cyber threat. Blacklists database of phishing has to be updated continuously in order to handle new URLs. Attackers modify phishing URL through obfuscation so that it "seems" legitimate thereby fools users. Garera et al. [35] have mentioned four types obfuscation: IP-based obfuscation of host, domain-based obfuscation of host with misspelling and large host names. These obfuscation techniques act as layer to hide nature of URL. Blacklisting methods are easy to implement and at the same time easy to fail for new variants of phishing attacks and also require human involvement to update. The advance in ML techniques brought a new outlook to the problem [35-38]. ML techniques learn the behavior of phishing URLs. In addition to this, the advantage of ML-based method over blacklisting is the ability to generalize for new URLs. ML-based methods, choosing the right features is the tedious task. Some featured engineering techniques is to extract features for either benign or phishing. Kan and Thi [39] have used ML techniques for classification. The strength of deep learning over classical ML is the ability to learn from raw data. Feature engineering part is not necessary in deep learning.

## 14.3 Background

### 14.3.1 Deep neural network

Deep learning is a subset of ML. Conventional ML technique requires feature engineering, i.e., we have to choose right features in order to obtain results this purely depends on domain knowledge, whereas deep learning does not require feature engineering. It learns from raw data. Deep neural networks (DNNs) are distinguished from shallow networks by their depth, that is number of hidden layers neural network has. A shallow network is composed of one input and one output layer, whereas DNN contains input layer, several hidden layers and an output layer. These hidden layers help recognize more complex features. Deep learning architecture for big data analytics in URL detection

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_325_0.png)

classical ML is the ability of DNN to learn the features by itself. In any deep learning architecture, there is forward propagation, backward propagation and minimizing the loss function with respect to its parameters. These parameters are weights and bias. The activation function used plays a key role in training a neural network. One of the difficulty when activation function like sigmoid ($\sigma$) is used is the problem of vanishing gradient. As result, when the number of layers increases, it becomes difficult to tune the parameters of different layers in neural network, and the problem of vanishing gradient becomes more significant. In Figure 14.1, the derivative of sigmoid function ($\sigma$) is almost zero for high positive and negative values in domain. This leads to vanishing gradient.

This problem is overcome by using $ReLU$ activation function. The mathematical representation of $ReLU(x)$ is given below:

$f(x) = \max(0,x)$ (14.1)

The derivative of $ReLU$ function is 1 if $x > 0$ and 0 if $x < 0$. The gradient has a constant value for $x > 0$; this reduces the chance of the gradient to vanish. The gradient of $ReLU$ is constant, it boosts the learning during training the neural network. In $ReLU$ for $x \leq$ the gradient is 0, the zero gradient is an advantage since it allows sparsity. In the case of sigmoid function, the chance of generating nonzero values is more which makes the representation in neural network dense while training. Sparsity always has an advantage over dense representations. A three-layer neural network is represented in Figure 14.2.

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_326_0.png)
![](img/6d0ce7dba01af52e1c2fae47d5b04a05_326_1.png)

### 14.3.2 Recurrent neural network

Unlike classical feedforward networks [40], recurrent neural network (RNN) contains a self-recurrent connection which helps in sequence modeling by carrying out time-related information from one time-step to another. The architecture of simple RNN unit is shown in Figure 14.3. The self-recurrent connection in RNN helps in learning the temporal dependencies across time steps. This nature of the RNN network has been very useful in capturing dependencies in the data set. In general, RNN accepts the id which is transformed [2] as a vector as input $x=(x_1, x_2,...,x_t)$ (where $x_t \in R^d$) and maps to hidden input sequence $h = (h_1, h_2, \dots, h_T)$ and output sequence $o = (o_1, o_2, \dots, o_t)$ from $t = 1$ to $T$ by iterating the following equations recursively:

$h_t = SG(w_{sh}x_t + w_{hh}h_{t-1} + b_h)$
$o_t = SF(w_{ho}h_t)$

where $w$ represents weights, $b$ terms represents bias, $SG$ is elementwise sigmoid function, $SF$ is elementwise $softmax$ and $h$ is the hidden layer. Training an RNN faces two main problems. They are vanishing and exploding gradient. This problem of vanishing and exploding gradient in RNN is solved by short-term memory (LSTM). LSTM has a memory cell with constant error. The computation of recurrent hidden layer at time step $t$ can be defined as follows:

$i_t = \sigma(w_{si}x_t + w_{hi}h_{t-1} + w_{mi}m_{t-1} + b_i)$
$f_t = \sigma(w_{sf}x_t + w_{hf}h_{t-1} + w_{mf}m_{t-1} + b_f)$
$m_t = f_t \odot m_{t-1} + i_t \odot tanh(w_{cm}x_t + w_{hm}h_{t-1} + b_m)$
$o_t = \sigma(w_{so}x_t + w_{ho}h_t + b_o)$
$h_t = o_t \odot tanh(m_t)$

where $\sigma$ represents the sigmoid function; $i, f,$ and $m$ are input, forget gate and memory cell respectively; $h$ is the hidden layer vector; $w$ and $b$ terms denote the weights and biases, respectively. To alleviate vanishing and error gradient, research on RNN progressed on the three significant directions. One is toward introducing optimization methods in algorithms such as Hessian-free optimization methods beyond this category. Second one toward introducing complex components in recurrent hidden layer network structure as LSTM [42], a variant of LSTM with reduced parameters set gated recurrent (GRU) [43] and third one toward the appropriate weight initialization with an identity matrix called identity-RNN [44,45].

### 14.3.3 Convolutional neural network

Convolutional neural network (CNN) had shown promising results in the field of computer vision and image processing [46]. CNN has also shown its application in the field of NLP-like semantic classification [47]. The general architecture of CNN is composed of convolution 1D layer, pooling 1D layer and fully connected layer nonlinear activation function as $ReLU$. The unique id is transformed as a vector as input features $x = (x_1, x_2, \dots, x_{n-1}, x_n)$ to CNN, CNN uses
