
$$
q(\mathbf{x}_{t - 1}|\mathbf{x}_{t},\mathbf{x}_{0}) = \frac{q(\mathbf{x}_{t}|\mathbf{x}_{t - 1},\mathbf{x}_{0})q(\mathbf{x}_{t - 1}|\mathbf{x}_{0})}{q(\mathbf{x}_{t}|\mathbf{x}_{0})} = \frac{q(\mathbf{x}_{t}|\mathbf{x}_{t - 1})q(\mathbf{x}_{t - 1}|\mathbf{x}_{0})}{q(\mathbf{x}_{t}|\mathbf{x}_{0})}
$$

![Equation](images/B9780443292385000251/si717.png)

1.  and the fact that all the involved pdfs in the previous ratio are Gaussians.

2.  19.8  Derive Eq. [(19.71)](#Chp019_997-1102_B9780443292385000251.xhtml#deq145).

### Computer exercises

1.  19.9  This exercise focuses on the original generative adversarial network (GAN) network, which is trained on the MNIST data set to learn to generate fake hand-written characters.

2.  To implement and train the network use the PyTorch framework.

    1.  **(a)**  Load the data set of 60000 to be used for training. Normalize image values so that all values are in the $[-1, 1]$ interval.

    2.  **(b)**  The generator is fed to its input with a noise vector and outputs an image. The dimension of the input noise vector is 100, and its elements are i.i.d. sampled from a normal distribution of zero mean and unit variance. The generator consists of three fully connected layers with 256, 512, 1024 neurons, respectively. The activation function used for the neurons in the hidden layers is the leaky ReLU with parameter $\alpha = 0.2$. The output layer comprises 784 nodes and the tanh is employed as the respective activation function.

    3.  **(c)**  The discriminator takes as input a $1 \times 784$ vector, corresponding to the vectorized form of the $28 \times 28$ MNIST images. The discriminator consists of three fully connected layers with 1024, 512, 256 neurons, respectively. The leaky ReLU activation function is also employed, with $\alpha = 0.2$. During training, use the dropout regularization method, with probability of discarding nodes equal to 0.3. The output layer consists of a single node with a sigmoid activation function.

    4.  **(d)**  To train the implemented network, use the two-class (binary) cross-entropy loss function. Adopt the Adam optimizer with step size (learning rate) equal to $2 \cdot 10^{-3}$, $\beta_1 = 0.5$ and $\beta_2 = 0.999$ as parameters for the optimizer. The recommended batch size is 100. Train the network for 400 epochs as follows: For each training loop: a) generate a random set of input noise and images, b) generate fake images via the generator, c) train only the discriminator, and d) then, train only the generator, according to [Algorithm 19.2](#Chp019_997-1102_B9780443292385000251.xhtml#enun0015). Play with the number of iterations, associated with the discriminator training.
