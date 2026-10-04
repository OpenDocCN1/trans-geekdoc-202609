# 248 Quantum Artificial Intelligence with Qiskit

![](bbox=[0.245, 0.115, 0.755, 0.327])

**Figure 19.1** On a conventional computer we needed to compute around 10000 steps to determine the period of an unknown periodic function, on quantum computer we need only 9 to 10 steps (10000).

based [100], [99]. Shor's algorithm breaks conventional cryptographic codes efficiently. Such codes cannot be broken by conventional computers since the calculations would require an exponential amount of time.

The QFT on a state $|xangle$ of $m$ qubits in a n-dimensional Hilbert space $H_n = H_{2^m}$ can be represented as [47]

```
$|yangle = F_m \cdot |xangle = \frac{1}{\sqrt{n}} \sum_{y \in B^n} e^{2\pi i \frac{x \cdot y}{n}} \cdot |y\rangle. \quad (19.12)$
```

It is just the discrete inverse Fourier transform of $\alpha(t)$ in the bracket notation

```
$\omega_f = \frac{1}{\sqrt{n}} \sum_{t=1}^n \alpha_t \cdot e^{2\pi i \frac{(f-1)(t-1)}{n}}$
```

Conventions for the sign of the phase exponent vary; here the quantum Fourier transform has the same effect as the inverse DFT and follows the qiskit notation. For one qubit $m=1, n=2$

```
$\zeta_2 = e^{2\pi i \frac{1}{2}} = e^{\pi i} = -1$
```

and the QFT $F_1$

```
$F_1 = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \ 1 & -1 \end{pmatrix} \zeta_2 = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \ 1 & -1 \end{pmatrix} = H_1. \quad (19.13)$
```

For two qubits $m=2, n=4$

```
$\zeta_4 = e^{2\pi i \frac{1}{4}} = e^{\pi i \frac{1}{2}} = i$
```