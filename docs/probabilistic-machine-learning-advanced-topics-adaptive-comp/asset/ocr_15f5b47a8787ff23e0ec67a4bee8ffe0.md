![](bbox=[0.28, 0.09, 0.72, 0.33])

Figure 16.10: A feedforward neural network with D inputs, K1 hidden units in layer 1, K2 hidden units in layer 2, and C outputs. \( w_{jk}^{(l)} \) is the weight of the connection from node j in layer l-1 to node k in layer l.

For example, Figure 16.10 shows an MLP with 1 input layer of D units, 2 hidden layers of \( K_1 \) and \( K_2 \) units, and 1 output layer with C units. The k'th hidden unit in layer l is given by
\( h_k^{(l)} = \varphi_l \left( b_k^{(l)} + \sum_{j=1}^{K_{l-1}} w_{jk}^{(l)} h_j^{(l-1)} \right) \) (16.21)

where \( \varphi_l \) is the nonlinear activation function at layer l.

For a classification problem, the final nonlinearity is usually the softmax function. However, it is also common for the final layer to have linear activations, in which case the outputs are interpreted as logits; the loss function used during training then converts to (log) probabilities internally.

We can also use MLPs for regression. Figure 16.11 shows how we can make a model for **heteroskedastic** nonlinear regression. (The term "heteroskedastic" just means that the predicted output variance is input-dependent, rather than a constant.) This function has two outputs which compute \( f_\mu(x) = \mathbb{E}[y|x,\theta] \) and \( f_\sigma(x) = \sqrt{\mathbb{V}[y|x,\theta]} \). We can share most of the layers (and hence parameters) between these two functions by using a common "**backbone**" and two output "**heads**", as shown in Figure 16.11. For the \( \mu \) head, we use a linear activation, \( \varphi(a) = a \). For the \( \sigma \) head, we use a softplus activation, \( \varphi(a) = \sigma_+(a) = \log(1 + e^a) \). If we use linear heads and a nonlinear backbone, the overall model is given by
\( p(y|x,\theta) = \mathcal{N} \left( y | w_\mu^T f(x; w_{\text{shared}}), \sigma_+(w_\sigma^T f(x; w_{\text{shared}})) \right) \) (16.22)

# ## 16.3.2 Convolutional neural networks (CNNs)

A vanilla **convolutional neural network** or **CNN** consists of a series of convolutional layers, pooling layers, linear layers, and nonlinearities. See Figure 16.12 for an example. More sophisticated architectures, such as the **ResNet** model [He+16a; He+16b], add skip (residual) connections, normalization layers, etc. The **ConvNeXt** model of [Liu+22b] is considered the current (as of February 2022) state of the art CNN architecture for a wide variety of vision tasks. See e.g., [Mur22, Ch.14] for more details on CNNs.