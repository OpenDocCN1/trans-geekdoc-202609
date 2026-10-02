
## 3.1.2. Text Preprocessing

Text preprocessing converts natural language into vector form. The comments in the training set are first segmented in the text processing process, and the segmented result is loaded into the thesaurus. All the words appeared in the training set together to be a thesaurus. In the thesaurus, the first word is coded 0, and the second word is coded 1, and so on. The thesaurus holds a series of correspondences between words and codes. Therefore, the sentence corresponding to each audio can be expressed as $\vec{S} = (S_1, S_2, ..., S_n)$. Where $S_x$ represents the $x^{th}$ word's code in a sentence. When the model performs natural language to vector conversion, the corresponding content can be retrieved by directly accessing the thesaurus.

## 3.2. Neural Audio Caption Model

The model is based on the neural audio caption method. The basic idea of the model is: input the audio MFCC feature sequence $\mathbf{A} = (\vec{a}_1, \vec{a}_2, ..., \vec{a}_n)$ and encode it into a fixed-length $\vec{K}$, then decode the fixed-length vector and output the predicted evaluation $\mathbf{R} = (\vec{R}_1, \vec{R}_2, ..., \vec{R}_n)$. The encoder of the model encodes MFCC features into learnable feature vectors. Then, these feature vectors are used to learn the correspondences with the training comments. Afterwards, the decoder of the model decodes the feature vector into comments. The complete structure of the neural audio caption method is shown in Figure 2. The model is divided into an encoder part and a decoder part.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_258_0.png)

Figure 2. Neural Audio Caption Model. The encoder of the model encodes the MFCC feature sequence into a learning representation. Because one oral audio corresponds to multiple comments, a random vector with a Gaussian distribution is added after audio information encoding. The decoder model gets the input learnable audio features and corresponding comment vectors, and finally outputs comments.

### 3.2.1. Encoder

The feature encoder part in Figure 2 shows that the information encoding of the NACM model uses our Bi-GRU model. The Bi-GRU model is composed of GRU cells. Given the audio MFCC feature token sequence $\mathbf{A} = (\vec{a}_1, \vec{a}_2, ..., \vec{a}_n)$, we use the encoder to encode the sequence information and generate a single representation $\vec{K}$. A GRU unit takes each token as input and outputs a hidden state computed by Equations (1)–(4). Then, a hidden state sequence is generated after the GRU network has computed from left to right along the input sequence. Meanwhile, a counterpart is calculated by another GRU unit computing in the reverse direction. By concatenating the last hidden state vectors and connecting the fully connected layer with activation, we finally get the encoded audio feature $\vec{K}$ with a dimension of 256. In this way, we obtain the holistic information of the sequence forward and backward. This process can be represented by Equation (5).

```
$$\vec{r}_t = \sigma(\mathbf{W}_r \cdot [\vec{h}_{t-1}, \vec{a}_t]) \tag{1}$$ $$\vec{z}_t = \sigma(\mathbf{W}_z \cdot [\vec{h}_{t-1}, \vec{a}_t]) \tag{2}$$ $$\vec{\tilde{h}}_t = tanh(\mathbf{W}_h \cdot [\vec{r}_t \circ \vec{h}_{t-1}, \vec{a}_t]) \tag{3}$$ $$\vec{h}_t = (1 - \vec{z}_t) \circ \vec{h}_{t-1} + \vec{z}_t \circ \vec{\tilde{h}}_t \tag{4}$$
```

The formula and output of GRU forward propagation are shown in Equations (1)–(4). Where $\vec{a}_t$ represents the current input vector at time $t$, $\vec{h}_{t-1}$ and $\vec{h}_t$ represent the hidden layer states at time $t-1$ and time $t$ respectively. In Equations (1)–(4), $\mathbf{W}$ terms denote weight matrices and the weight matrices are defined in Equation (13), $\sigma$ represents the sigmoid function and sigmoid is a non-linear function in neural network, $\vec{z}_t$ and $\vec{r}_t$ represent update gate and reset gate, $\vec{\tilde{h}}_t$ is the candidate hidden state at time $t$. $\circ$ indicates element-wise multiplication.

```
$$\vec{K} = tanh(\mathbf{W}_K \cdot \vec{h}_t + \vec{b}_K) \tag{5}$$
```

where $\mathbf{W}_K$ is weight matrix and $\vec{b}_K$ is bias vector. The bias vector is initialized to be 0. The weight matrices are defined in Equation (13).

### 3.2.2. Decoder

The decoder part designed in Figure 2 consists of LSTM cells. In practice, the same audio will be evaluated by different experts. In our training set, one audio corresponds to multiple evaluations. Thus, we concatenate a random vector $\vec{z}$ of a Gaussian distribution to the encoded audio feature $\vec{K}$ and use them as the initial hidden state to the LSTM network. Gaussian vector enables Decoder to generate multiple comments with the same input feature vector. During the training, Gaussian vector is initialized by standard normal distribution and we use the embedding of expected output from the training dataset as the input of LSTM network. The procedure can be formulated as Equations (6)–(11). Then we can get a hidden state sequence $\mathbf{h} = (\vec{h}_1, \vec{h}_2, ..., \vec{h}_n)$ after the LSTM unit has finished loop computing. Finally, we use a compositional operation to change the dimension to $N_{voc}$, and then getting the probability distribution for word in $R_n$. The calculation formula is shown in Equation (12).

```
$$\vec{f}_t = \sigma(\mathbf{W}_f \cdot [\vec{h}_{t-1}, \vec{x}_t] + \vec{b}_f) \tag{6}$$ $$\vec{i}_t = \sigma(\mathbf{W}_i \cdot [\vec{h}_{t-1}, \vec{x}_t] + \vec{b}_i) \tag{7}$$ $$\vec{\tilde{c}}_t = tanh(\mathbf{W}_c \cdot [\vec{h}_{t-1}, \vec{x}_t] + \vec{b}_c) \tag{8}$$ $$\vec{c}_t = \vec{f}_t \circ \vec{c}_{t-1} + \vec{i}_t \circ \vec{\tilde{c}}_t \tag{9}$$ $$\vec{o}_t = \sigma(\mathbf{W}_o \cdot [\vec{h}_{t-1}, \vec{x}_t] + \vec{b}_o) \tag{10}$$ $$\vec{h}_t = \vec{o}_t \circ tanh(\vec{c}_t) \tag{11}$$ $$\vec{R}_n = softmax(\mathbf{W}_R \cdot \vec{h}_t + \vec{b}_R) \tag{12}$$
```

The calculation formula and output of LSTM forward propagation are shown in Equations (6)–(11). Where $\sigma$ is the sigmoid function, $\vec{h}_{t-1}$ is the hidden layer output at time $t-1$, $\vec{x}_t$ is the input at time $t$, $\vec{c}_{t-1}$ is the cell state at time $t-1$, $\vec{\tilde{c}}_t$ is the candidate value of cell state at time $t$, $\vec{f}_t$, $\vec{i}_t$ and $\vec{o}_t$ are the forget gate, input gate and output gate respectively. In Equation (12), W_R is weight matrix and b_R is bias vector. The bias is initialized to be 0 and the weight is initialized as Equation (13).

$W \sim U\left[-\frac{1}{\sqrt{n}},\frac{1}{\sqrt{n}}\right]$ (13)

where U denotes the uniform distribution, n is the size of the previous layer.

According to the probability distribution for the output word in R = (R1, R2, ..., Rn) and the coding vector S~ = (S1, S2, ..., Sn) of the actual sample, we can calculate the loss via L Equation (14) and update the parameters of this model.

$L = \frac{1}{n}\sum_{i=1}^{n} -log(R_i[S_i])$ (14)

where vector S~ = (S1, S2, ..., Sn) represents real reviews from experts, each word is numbered. Si denotes the code of the word whose index is i in the sentence and R_i[Si] is the probability of the word whose index is Si in R_i.

## 3.3. Generative Adversarial Network-Based Neural Audio Caption Model

The neural audio caption method based on data transformation can generate understandable and appropriate evaluations. To make the generated comment closer to the expert comment, a Generative Adversarial Network (GAN) is combined [33,34].

GAN-Based Neural Audio Caption Model is composed of two neural networks, a generative neural network and a discriminative neural network. It uses the NACM as its generator, which generates comments. Meanwhile, the discriminator evaluates them for authenticity. The goal of the generator network is to generate comments that are as similar to the samples in the training set as possible. The input of the discriminator network is the real sample or the output of the generator network. Its purpose is to distinguish the output of the generator network from training data as much as possible. Thus, GAN builds a sort of feedback loop where the generator is helping to train the discriminator, and the discriminator is helping to train the generator. They both get better together. With this structure, the generated comment is closer to the real evaluation. The structure of the model is shown in Figure 3.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_260_0.png)

Figure 3. GAN-Based Neural Audio Caption Model. The model is divided into a generator and a discriminator. Among them, the generator follows the Neural Audio Caption Model. The discriminator uses an embedding layer, a deep LSTM layer and a fully connected layer.
