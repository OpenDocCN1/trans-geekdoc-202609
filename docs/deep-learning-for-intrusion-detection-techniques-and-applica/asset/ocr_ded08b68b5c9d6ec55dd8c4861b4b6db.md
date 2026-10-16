# 10 Deep Learning-Based Intrusion Detection in Wireless Networks

across multiple time steps in a sequence. Unlike standard RNNs, which overwrite memory at each step, the memory cell in LSTM enables the model to retain crucial information across longer sequences. This helps to solve the vanishing gradient problem that standard RNNs experience. The memory cell uses three critical gates to control the flow of information:

+   - Forget gate: It determines which parts of the current memory should be kept or deleted. It enables the output of values between 0 and 1 through sigmoid activation. If the value is 1, everything is kept; if it is 0, everything is forgotten.
+   - Input gate: It determines how much new data should be written to memory from the current input. It collaborates with a candidate memory that is made with a tanh layer. The input gate determines how much of what could be added is actually added after the candidate memory suggests what could be added.
+   - Cell state update C(t): This is the memory's actual update where the part of the new information and part of the previous state are retained in the memory.
+   - The linear path promotes long-term dependencies by allowing gradients to pass through unhindered during backpropagation.
+   - Output gate: It determines how much of the memory should be provided during each step. It controls the hidden state, which is used for output and transferred to the next cell.

• Hidden State h(t): This is the LSTM’s short-term memory, which represents the network's current state. It is determined using the output gate's output as well as the cell state. It serves as the output for the current time step and acts as the input for the next step.

Autoencoder: Autoencoders are ANNs designed to develop efficient representations of input data. They work by compressing the input data into a lower-dimensional representation (known as a “latent space”), which is then used to reconstruct the original input. Essentially, an AE attempts to learn an identity function: it seeks to properly reconstruct the input from its compressed version. However, allowing the neural network to gain insight into this reconstruction through a bottleneck (the lower-dimensional representation) reveals incredible patterns and characteristics in the dataset. The main components of autoencoder are as follows:

+   - Encoder: This component of the network compresses the input information to form latent space. It is often made up of a succession of layers that gradually lower the size of the data.

```
Z = f(We · x + be)
where z is the latent representation, We is the weight matrix of the encoder, x is the input data, and b is the bias.
```