# 21.2 QUANTUM PERCEPTRON

The classical perceptron describes an algorithm for supervised learning that consists only linearly separable problems in groups which can be separated by a line or hyperplane. The quantum perceptron [96], [95] does usually include learning and instead it computes the binary representation of the function $net$ modulo $D$ with $w_0 = 1$

```
$$net := \left(\sum_{j=0}^{D} w_j \cdot x_j\right) \mod D = \left(\sum_{j=1}^{D} w_j \cdot x_j + w_0\right) \mod D = (|\mathbf{w}| + w_0) \mod D$$
```

with the constraint
$x_j \in \{0, 1\}, w_j \in [-1, 1]$

The value $w_0$ is called the "bias", it is a constant value that does not depend on any input value. Each dimension $j$ is represented by a controlled phase gate $CP_j$

```
$$\lambda = \pi \cdot \frac{w_j}{2(m-1)}$$$
```

and $D = 2^m - 2$ and $\log_2(D+2) = m$. For $D = 2$

```
$$net = w_0 + w_1 \cdot x_1 + w_2 \cdot x_2$$
```

will be represented by three controlled phase gate that performs the computation

```
$$e^{i\pi \cdot \frac{w_0}{2}} = e^{i\pi \cdot \frac{w_1 x_1}{2}} \cdot e^{i\pi \cdot \frac{w_2 x_2}{2}}$$
```

The estimated values of $net$ is represented by two qubits in the case $net$ is natural number the measured values are four possible values of the two qubits $|q_1q_0\rangle$

$[00], [01], [10], [11]$

In other rational number value of $net$ corresponds to a superposition of the four states. A nonlinear activation function

```
$$$\phi(net) := f(net) = \begin{cases} 1 & \text{if } net \geq \text{threshold} \ 0 & \text{if } net < \text{threshold} \end{cases}$$$
```

with $threshold = 10$ can be implemented reading the more important qubit, in the case qubit $q_1$ which can represent the output value of the Perceptron that is either one or zero. A quantum Perceptron can be used as building block of larger systems, it can process an arbitrary number of input vectors in parallel, when the input is presented in superposition $|\psi\rangle$ representing the whole data $DB$ of $s$ objects $\mathbf{x}_k$

```
$$\mathbf{x}_k \in DB \mid k \in \{..s\}$$$
```

with

```
$$|\psi\rangle = \frac{1}{\sqrt{s}}\sum_{k=1}^{s} |\mathbf{x}_k\rangle$$
```

and then can be further processed.