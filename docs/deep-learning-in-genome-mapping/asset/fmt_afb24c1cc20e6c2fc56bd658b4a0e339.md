
Neural network models are powerful tools in fields like image recognition, machine translation, and NLP, learning complex patterns for applications in healthcare, finance, and transportation. Training requires large datasets, but human expertise can enhance model learning by incorporating domain knowledge through simulations, equations, and logic rules. Conditional statements, such as If-Then rules, help classify data and refine predictions. The training process, supported by manual rule selection, improves learning confidence and mitigates data shortages, ensuring robust neural network performance.

![Figure 4: Training process of neural network models.](images/fig6_4_B.jpg)

Figure 4: Training process of neural network models.

#### 1.4.4 Backpropagation and Loss Functions

Single-layer neural networks simplify training by directly calculating error or loss functions based on weights. This feature simplifies the process of training by making gradient calculation uncomplicated. Multi-layer networks, however, have complex composite loss functions dependent on layer weights. The backpropagation algorithm computes gradients using the chain rule of differential calculus, summing local gradients along paths, from a node to the output. Dynamic programming efficiently handles this summation despite its exponential complexity. Backpropagation consists of two phases: forward and backward. The forward phase calculates output values and local derivatives, while the backward phase accumulates these values from nodes to the output. During training, the neural network processes input data, propagates calculations through layers, and compares predicted results with training instances, to compute loss function derivatives for all layer weights.

![Figure 5: Chain rule for computation.](images/fig6_5_B.jpg)

Figure 5: Chain rule for computation.

The multivariable chain rule analyzes the gradient in a computational graph and identifies the existence of more than one path.

According to Figure \[4\]

(1)  

$$\\frac{\\partial o}{\\partial W} = \\frac{\\partial o}{\\partial P}\\frac{\\partial P}{\\partial W} + \\frac{\\partial o}{\\partial Q}\\frac{\\partial Q}{\\partial W}$$  

Equation 1 represents the Multivariate Chain rule.

(2)  

$$\\frac{\\partial o}{\\partial W} = \\frac{\\partial o}{\\partial P}\\frac{\\partial P}{\\partial X}\\frac{\\partial X}{\\partial W} + \\frac{\\partial o}{\\partial P}\\frac{\\partial Q}{\\partial Y}\\frac{\\partial Y}{\\partial W}$$  

Equation 2 represents the Univariate Chain rule.

(3)  

$$\\begin{matrix} {\\frac{\\partial K\\lbrack P,Q\\rbrack}{\\partial P} \\cdot g^{\\prime}(Y) \\cdot I^{\\prime}(W) + \\frac{\\partial K\\lbrack P,Q\\rbrack}{\\partial P} \\cdot h^{\\prime}(Z) \\cdot I^{\\prime}(W)} \\\\ {\\text{Ist~Path}\\quad\\text{IInd~Path}} \\\\ \\end{matrix}$$  

Equation 3 represents the derivative of weight (W) in relation to output (O).

In the above representation, only two paths are evident.

##### Mathematical Formulation Using the Chain Rule

The derivative of `y` with respect to `x`, denoted as $\\frac{dy}{dx},$ is calculated as follows:

First Layer Derivative:

(4)  

$$\\frac{du}{dx} = f^{\\prime}(x)$$  

where `f`′(`x`) is the derivative of `f` with respect to `x`.

Second Layer Derivative:

(5)  

$$\\frac{du}{dx} = g^{\\prime}(u)$$  

where `g`′(`u`) is the derivative of `g` with respect to `u`.

Third Layer Derivative:

(6)  

$$\\frac{dv}{dy} = h^{\\prime}(v)$$  

where `h`′(`v`) is the derivative of `h` with respect to `v`.

Applying the Chain Rule:

(7)  

$$\\frac{dy}{dx} = \\frac{dy}{dv}\\frac{dv}{du}\\frac{du}{dx} = h^{\\prime}(v) \\cdot g^{\\prime}(u) \\cdot f^{\\prime}(x)$$  

Equation 7 illustrates that the derivative at each layer depends on the previous layer’s derivative, propagating the estimated gradient backward. The local gradients (`h`′(`v`) . `g`′(`u`) . `f` ′(`x`)) collectively determine the total gradient of the network output with respect to the input.

#### 1.4.5 Activation and Loss Functions

In neural network design, selecting an appropriate activation function is a crucial consideration. If a binary class needs to be labeled, the sign activation function becomes a significant choice. Conversely, when predicting a real variable, it is essential to determine the appropriate activation function in conjunction with least-square algorithms. [Figure 6](#ch6.xhtml#fig6_6) illustrates various activation functions that are applicable to different scenarios.

![Figure 6: Activation functions.⏎](images/fig6_6_B.jpg)

Figure 6: Activation functions.[⏎](#ch6.xhtml#R_fig6_6)

Sign activation functions are used to predict binary values, while tanh functions are preferable for signed values ranging from \[–1 1\]. In modern neural networks, ReLU and hard tanh activation functions have replaced traditional sign and tanh functions due to their adaptability in training multilayered neural networks.

### 1.5 Deep Learning as an Extension of Neural Network

Deep learning is a significant advancement in machine learning that extends the capabilities of traditional neural networks by enabling computational models to learn through multiple layers of abstraction. These enhanced models excel in areas such as speech recognition, visual recognition, object recognition, and genomics. Deep learning uncovers complex structures in large datasets using the backpropagation algorithm, computing parameters layer by layer based on information from previous layers. Deep convolutional networks are well-suited for image, video, and audio processing, while recurrent networks are effective for sequential data such as text and speech processing (Diwakar et al. 2020).

#### 1.5.1 Deep Learning Networks and its Architecture

Deep learning models are applicable across various fields, with their success relying on the embedded architectural design. The layers, and parameters within the architecture vary depending on the application. This section explores commonly used deep learning architectures, along with applicationspecific designs and their features. Several architectures address challenges in different domains. Some of the most widely adopted architectural frameworks, such as CNN \[Convolutional Neural Network\], Genome Net, and LSTM \[Long Short-Term Memory\] can be selected based on the specific requirements of the application.

#### 1.5.2 Convolutional Neural Network and its Architecture

Convolutional Neural Networks (CNNs) are deep learning algorithms specifically designed for processing visual information. This unique capability is inspired by the human visual system, which performs spatial hierarchies in data. The convolutional layers in CNNs utilize filters to extract features from input images, sliding across the entire image to capture edge and texture details. Instead of operating within a single layer, this process progresses through multiple convolutional layers, where features obtained at each stage are combined to represent complex patterns. These patterns enable CNNs to recognize objects and scenes within an image. A key advantage of CNNs is their ability to autonomously learn features from input data, reducing the need for manual analysis, which can be time-consuming and complex. CNNs are well-suited for handling large and intricate datasets, making them ideal for applications such as object recognition, segmentation, and image classification. The basic architecture of a CNN is illustrated in [Figure 7](#ch6.xhtml#fig6_7).

![Figure 7: Simple CNN architecture.⏎](images/fig6_7_B.jpg)

Figure 7: Simple CNN architecture.[⏎](#ch6.xhtml#R_fig6_7)

CNN architecture consists of the following key components:
