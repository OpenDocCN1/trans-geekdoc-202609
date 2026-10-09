
$W_z$ and $U_z$ are the weights learned in the update gate.

(2) The hidden state of the current timestep $t$ is calculated by Equation (11):

$$h^t = zh^{t-1} + (1-z)\tilde{h}^t \tag{11}$$

where $\tilde{h}^t$ contains the input of the current timestep and at the same time, the hidden state of the hidden unit of the previous timestep is added into the current hidden state; the calculation formula is shown in (12):

$$\tilde{h}^t = \phi\left(Wx^t + U\left(r\bigcirc h^{t-1}\right)\right) \tag{12}$$

where $W$ represents the weight of the current input and $U$ represents the weight of the hidden state of the hidden unit in the previous timestep.

In the GRU, when the update gate approaches 0, the hidden state ignores the previous hidden state and updates only with the current input, which ensures that the hidden state selectively retains relevant important information and that the information can be expressed more compactly.

In summary, in the model training process, the hidden state $h^{t-1}$ passed down from the previous timestep and the input $x^t$ of the current timestep are used as the input of BiGRU. On one hand, it obtains the two gating states of the reset gate and the update gate and normalizes the obtained information through the sigmoid function to make it act as a gating signal. On the other hand, the image feature sequence is converted into a context vector $C_t$ as the output.

This work introduces an attention mechanism to the encoder-decoder structure to give weights to the output of the encoder. The main implementation details of the attention mechanism are as follows: first, the input data are fed through a feedforward neural network to generate query vectors and key vectors. Then, the similarity between the query vectors and key vectors is calculated and the resulting scores are normalized to obtain the final attention weights. Finally, the attention weights are applied to the value vectors and summed up to obtain the weighted sum as the output feature vector. Through this process, the attention mechanism can learn the importance of different parts of the input data and enable the decoder to better utilize the information from the encoder. It also has strong interpretability and generalization ability.

Specifically, the attention mechanism learns a special attention weight by adding an additional feedforward neural network to the network structure $\alpha_{t_E,t_D}$ where $t_E$ and $t_D$ represents the $t$-th timestep of the encoder and decoder, respectively. The introduction of this weight into the neural network helps to further reconcile the relationship between the hidden states in the encoder and decoder to highlight the focus of model training. The context vector $C_t$ of the output of the $t$-th timestep encoder can be assigned by Equation (13):

$$C^t = \sum_{t_E=1}^{T} \alpha_{t_E,t_D}h_{t_E} \tag{13}$$

At the $t$-th timestep of the decoder, $C_t$ is the weighted sum containing all encoder hidden states and their corresponding attention weights.

The structure of the decoder BiLSTM is similar to that of the encoder. When calculating the prediction sequence, the input values accepted by the decoder are the context vector $C_t$ weighted by the attention mechanism, the system state $S_{t-1}$ of the output of the decoder at the previous timestep, and the hidden state $S_{t-1}$ of the decoder at the previous timestep. With the help of such information, the decoder can calculate the hidden state $h_t$ of the current time node and the probability distribution of the output sequence of the node according to the probability calculation formula, as shown in (14).

$$p(S_{t}\vert S_{t-1}, S_{t-2}, \cdots, S_{1}, C_{t}) = g(h_{t}, S_{t-1}, C_{t})\tag{14}$$

where $g$ represents the given activation function. The softmax is used as the activation function for this stage in the EGA model. The largest output value of $p(S_{t}\vert S_{t-1}, S_{t-2}, \cdots, S_{1}, C_{t})$ is treated as the output value of the $t$-th timestep. Ultimately, the output values of each timestep make up the output sequence of the model.

## 4. Data Experimental

### 4.1. Experimental Data

The dataset used in this article comes from the Inner Mongolia Normal University and includes 9479 handwritten Mongolian characters, totalling 47,395 images. The dataset covers various handwriting styles and samples from different writers, with a wide variety of fonts, and each character has a clear shape, which is highly representative and can truly reflect the features of Mongolian handwriting styles. Furthermore, the dataset is balanced, i.e., the number of images per character is similar among them. All these characters are carefully handwritten and drawn by writers, closely related to practical application scenarios and are highly authentic and practical, making them suitable for data training and testing for handwriting character recognition tasks. Some offline Mongolian handwriting sample images of the dataset are shown in Figure 7.

![](img/e4200cc4308edaf8913e513b0f96dbb6_29_0.png)

### 4.2. Model Training Platform

According to the training requirements of the Mongolian handwriting recognition model, the model training environment built in this paper is shown in Table 1.

Table 1. Model Training Platform Parameters.

| Name | Parameters |
|:---:|:---:|
| CPU | Intel Core i7-6700 CPU@3.40 GHz |
| GPU | Nvidia Tesla P100 + Huawei GPU Server |
| Operating system | Ubuntu 16.04.6 |
| Programming language | Python 3.7 |
| Deep learning framework | Pytorch 1.9.0 |

### 4.3. Indicators for Model Performance Evaluation

The quality of the Mongolian handwriting recognition model is primarily measured during the training process from two aspects: the recognition accuracy for the test set and the complexity of the trained model.

(1) Accuracy is the primary criterion to measure the effectiveness and practicality of Mongolian handwriting recognition models and it can be calculated by the confusion matrix, in which the prediction accuracy of the classification algorithm is evaluated by the relationship between the true category of the sample and the predicted value of the model, as shown in Table 2.

**Table 2.** Confusion Matrix.

| | | | Forecast Category | | | |
|:---|:---|:---|:---:|:---:|:---:|:---:|
| | | | | | | |
| **Real category** | | | **Positive category** | | **Negative category** | |
| | | | **True Positive (TP)** | | **False Negative (FN)** | |
| **Positive** | | | | | | |
| **Negative** | | | **False Positive (FP)** | | **True Negative (TN)** | |

In the confusion matrix, TP and TN represent the situation where the predicted category matches the real category and the classification if the predicted value is correct; FP and FN represent the situation where the predicted category does not match the real category and the classification is wrong. The accuracy is defined by the proportion of correctly classified data to the total test set and calculated by Equation (15).

$$\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN} \tag{15}$$

In Mongolian handwriting recognition, predicted value classification is more diverse and not limited to positive and negative categories, and the correct classification represents the situation where the sequence output of the model is consistent with the sequence of image labels.

(2) Model complexity is another important criterion for measuring model quality. Under the condition of the same test platform and data, the model training time, the number of model parameters generated during the training process, and the size of the trained model are used as indicators to evaluate the model's complexity in this work.

### 4.4. Data Test of the Dual Data Augmentation Method and Result Analysis

The dual data augmentation algorithm combines random erasing with horizontal wave transformation, and its parameters also need to be uniformly initialized. The test parameters of dual data augmentation are listed in Table 3. The optimal hyperparameter values mentioned above were used to ensure the sample quality of the proposed data augmentation.

**Table 3.** Dual Data Augmentation Hyperparameter.

| Hyperparameter Name | Hyperparameter Meaning | Hyperparameter Value |
|:---:|:---|:---:|
| *p* | A random value that determines the image data augmentation method | [0, 1] |
| *W* | Image width | 800 |
| *H* | Image height | 1500 |
| $S_l$ | For random erasing, the minimal erasing area ratio | 0.01 |
| $S_h$ | For random erasing, the maximal erasing area ratio | 0.06 |
| $r_a$ | The minimal ratio of the major to minor axes of the erasing area | 0.5 |
| $r_b$ | The maximal ratio of the major to minor axes of the erasing area | 2 |
