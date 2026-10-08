# Example of 384-dimensional vector

| How | Are | You |
|---|---|--|
| Word embedding | [0.2, 0.3, 0.5, ... ] | [0.1, 0.4, 0.6, ... ] | [0.3, 0.2, 0.7, ...] |
| Positional encoding | [0.2, 0.3, 0.5, ...] + [0.1, 0.2, -0.3, ...] = [0.3, 0.5, 0.2, ...] ] | [0.1, 0.4, 0.6, ...] + [-0.1, 0.3, 0.2, ...] = [0.5, 0.7, 0.8, ...] | [0.3, 0.2, 0.7, ...] + [-0.2, -0.1, 0.4, ...] = [0.5, 0.1, 1.1, ...] |
| Self-attention | [0.3, 0.5, 0.2, ...] | [0.2, 0.8, 0.1, ...] | [0.5, 0.2, 0.3, ...] |
| FFNN | [0.4, -0.1, 0.6, ...] | [-0.6, 0.2, 0.4, ...] | [-0.3, 0.7, 1.1, ...] |
| Add and norm | [0.3, 0.5, 0.2, ...] + [0.4, -0.1, 0.6, ...] = [0.7, 0.4, 0.8, ...] | [0.0, 0.7, 0.8, ...] + [0.2, 0.8, 0.1, ...] = [-0.6, -0.2, 0.4, ...] = [0.8, 1.3, 1.3, ...] | [0.5, 0.2, 0.3, ...] + [-0.3, 0.7, 0.1, ...] = [0.7, 1.0, 1.5, ...] |

+   (c) Self-attention: Self-attention is a mechanism where how much attention in the input sentence decides how much attention to give to other words. This attention mechanism allows the model to focus on different parts of the input when encoding, enabling it to capture dependencies and relationships between words effectively.

+   (d) Feedforward neural network: Following self-attention, the output is processed through a feedforward neural network. This network consists of six linear layers, each followed by a Rectified Linear Unit (ReLU) activation function. The purpose of the feedforward network is to capture complex relationships within the data by transforming the representations learned from self-attention.

+   e Add and norm: After passing through the feedforward network, the output is combined with the original information using an "add" operation. Residual connection helps in mitigating vanishing gradient problems during training. The combined output is then normalized to ensure that the information is in a suitable state for further processing. This step, known as normalization, stabilizes and standards the output.

The sentence transformer utilizes the processed information to encode the input sentences into a 384-dimensional vector. This vector serves as a meaningful representation

For example, let's consider the sentence "How are you?". The process can be elaborated by the aforementioned five steps and is shown in Table 1 and depicted in the 384-dimensional vector transform of Fig. 2.

The 384-dimensional vector output from the sentence transformer is fed into a simple feedforward neural network. This network processes the vector through multiple layers, and it generates a vector representing the predicted output at the final layer (output layer). The predicted output is then passed through a SoftMax activation function which converts the raw output into a probability distribution assigning probabilities to different classes. This is crucial for identifying the most likely class or response. The class with the highest probability in the