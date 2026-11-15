The standard Softmax function \(\sigma\): \(\mathbb{R}^K \to [0,1]^K\) is defin by following equation:

\(\sigma(z)_i = \frac{e^{z_i}}{\sum_{j=1}^K e^{z_j}} \text{ for i=1, ..., K and } z = (z_1, ..., z_K) \in \mathbb{R}^K\) (1)

Where z is the input vector.

# Rectified Linear Unit Function

Nair and Hinton created rectified linear unit (ReLU) activation function in 2010 (Nair et al., 2010). In terms of performance and generalisation, it leads the Sigmoid and Tanh activation functions in deep learning. As it is a faster learning activation function it is the most widely utilised function. The ReLU resembles to a linear function, keeping the characteristics of linear models that make gradient-descent optimization straightforward.

y = f(x) = max(0,x) (2)

Where x represents the input to the ReLU and y is the corresponding output value.

It removes the vanishing gradient problem occurring in the previous activation function by driving the negative input value to zero. Advantage of implementing ReLU units is they results in faster calculations as they don't compute divisions or exponentials which improves overall computation performance.

The ReLU also compresses the values between zero and maximum, resulting in sparsity in the hidden units. Because of its simplicity and dependability, ReLU has been employed in several architectures.

# Cost function

The cost function is used to calculate the difference between the estimated and true value of the CNN model's error (Ullah et al., 2020). The error function is minimized using an optimizer function. In neural network theory, various cost functions have been used. We employed the cross-entropy function using the equation as follows:

C = - \frac{1}{n} \sum_{i=1}^{y} (y_i * ln(a_i) + (1-y_i) * ln(1-a_i)) (3)