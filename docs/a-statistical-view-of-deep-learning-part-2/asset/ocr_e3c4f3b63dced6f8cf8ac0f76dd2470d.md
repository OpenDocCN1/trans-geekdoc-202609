# Network structure

# ReLU (Recticulated Linear Unit) activation function

\(\sigma(x) = \max(0, x) = \left\{ \begin{array}{ll} 0 & \text{for } x < 0 \\ x & \text{for } x \ge 0 \end{array} \right.\)

# Softmax activation function

+   - Used for classification problems on the output layer
+   - Input: \( x \in \Re \), output: \( 0 \le \sigma(x_i) \le 1 \)

\(\sigma(x_i) = \frac{\exp(x_i)}{\sum_{j=1}^J \exp(x_j)} \quad \text{for } i = 1, \dots, J\)