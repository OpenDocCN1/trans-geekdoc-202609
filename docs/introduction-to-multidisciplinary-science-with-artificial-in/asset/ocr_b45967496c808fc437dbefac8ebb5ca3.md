# **The quantum Fourier transform (QFT)**

works in the same way as the classical Fourier transform. However it has a very elegant implementation that is exponentially faster than its classical counterpart. The classical Fourier transform maps the vector $\boldsymbol{x} = [x_1, x_2, ..., x_N]^T$ into $\boldsymbol{y} = [z_1, z_2, ..., z_N]^T$ as follows:

$$z_k = \frac{1}{\sqrt{N}} \sum_{j=0}^{N-1} x_j \exp\left(\frac{2\pi j k}{N}\right), \tag{4.111}$$

where $N$ is the number of evenly spaced samples of $\boldsymbol{x}$ with $x_j = j\Delta x$; $x_j$ are complex numbers, with $j = 0, ..., N-1$ and $y_k$ are complex numbers, with $k = 0, ..., N-1$. The QFT does pretty much the same thing. However it acts on quantum states. In other words, QFT works directly on qubits. We assume that we have a $n$-qubit computer with $N = 2^n$. Thus a quantum basis vector

$$|x\rangle = |2^{n-1}x_1 + 2^{n-2}x_2 + ... + 2^0 x_n\rangle$$ $$= \underbrace{|x_1 x_2 x_3 ... x_n\rangle}_{n-\text{qubits}} = |x_1\rangle \otimes |x_2\rangle \otimes |x_3\rangle \otimes ... \otimes |x_n\rangle, \tag{4.112}$$

where $x_k \in \{0,1\}$. In addition to the multi-qubit notations introduced in the previous section, we have added the decimal representation through the first equality. This equality allows us to switch from binary representations to decimal representations and vice versa. So we have, in a 3-qubit computer for example, $|5\rangle = |2^2 \times 1 + 2^1 \times 0 + 2^0 \times 1\rangle = |101\rangle = |1\rangle \otimes |0\rangle \otimes |1\rangle$. From the definition of multi-qubits in the previous section, we can map $|x\rangle$ into $|z\rangle$, as follows:

$$|z\rangle = \text{QFT}|x\rangle = \frac{1}{\sqrt{N}} \sum_{y=0}^{N-1} \exp\left(\frac{2\pi i x y}{N}\right) |y\rangle$$ $$= \frac{1}{\sqrt{N}} \sum_{y=0}^{N-1} \exp\left(2\pi i x \sum_{k=1}^{n} \frac{y^k}{2^k}\right) |y_1 y_2 y_3 ... y_n\rangle$$ $$= \frac{1}{\sqrt{N}} \sum_{y=0}^{N-1} \prod_{k=1}^{n} \exp\left(2\pi i \frac{x y^k}{2^k}\right) |y_1 y_2 y_3 ... y_n\rangle$$ $$= \frac{1}{\sqrt{N}} \left(|0\rangle + \exp\left(2\pi i \frac{x}{2^1}\right) |1\rangle\right) \otimes \left(|0\rangle + \exp\left(2\pi i \frac{x}{2^2}\right) |1\rangle\right)$$ $$\otimes \left(|0\rangle + \exp\left(2\pi i \frac{x}{2^3}\right) |1\rangle\right) \otimes ... \otimes \left(|0\rangle + \exp\left(2\pi i \frac{x}{2^n}\right) |1\rangle\right)$$ $$= \frac{1}{\sqrt{N}} \bigotimes_{j=1}^{n} \left(|0\rangle + \exp\left(2\pi i \frac{x}{2^j}\right) |1\rangle\right). \tag{4.113}$$

Here, the larger tensor product symbol functions as an indexed product of the Kronecker tensor product. In this form, QFT can be described as multiple tensor