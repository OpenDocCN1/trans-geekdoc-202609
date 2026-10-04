# 260 ■ Quantum Artificial Intelligence with Qiskit

with

$$\sin^2 \theta = \frac{k}{n} \quad (20.13)$

and

$$\cos^2 \theta = \frac{n-k}{n} = 1 - \frac{k}{n}. \quad (20.14)$

We can represent the Grover's amplification matrix in the two-dimensional basis $|\tau_{solution}\rangle$ and $|\tau_{non}\rangle$

$G = \begin{pmatrix} \cos(\theta) & -\sin(\theta) \ \sin(\theta) & \cos(\theta) \end{pmatrix}$

The matrix $G$ has two eigenvectors

$u_1 = \begin{pmatrix} \frac{1}{\sqrt{2}} \ \frac{1}{\sqrt{2}} \end{pmatrix}; \quad u_2 = \begin{pmatrix} \frac{1}{\sqrt{2}} \ \frac{-1}{\sqrt{2}} \end{pmatrix}$

with two eigenvalues $\lambda_1 = e^{2i\theta}$ and $\lambda_2 = e^{-2i\theta}$. The eigenvectors are represented in $|\tau_{solution}\rangle$ and $|\tau_{non}\rangle$ as

$|\tau_1\rangle = \frac{1}{\sqrt{2}}|\tau_{solution}\rangle + \frac{1}{\sqrt{2}}|\tau_{non}\rangle$

$|\tau_2\rangle = \frac{1}{\sqrt{2}}|\tau_{solution}\rangle - \frac{1}{\sqrt{2}}|\tau_{non}\rangle \quad (20.15)$

$|\tau\rangle = e^{i\theta} \cdot \frac{1}{\sqrt{2}}|\tau_1\rangle + e^{-i\theta} \cdot \frac{1}{\sqrt{2}}|\tau_2\rangle \quad (20.16)$

In the original phase estimation algorithm, the required eigenvector is

$U|u\rangle = e^{2i\pi\theta}|u\rangle \quad (20.17)$

However, we do not need to prepare our register in either of these eigenvectors, the register is actually in a superposition of the Grover's operator

$G|\tau\rangle = G \cdot (e^{i\theta} \cdot \frac{1}{\sqrt{2}}|\tau_1\rangle + e^{-i\theta} \cdot \frac{1}{\sqrt{2}}|\tau_2\rangle) \quad (20.18)$

$G|\tau\rangle = \lambda_1 \cdot (e^{i\theta} \cdot \frac{1}{\sqrt{2}}|\tau_1\rangle) + \lambda_2 \cdot (e^{-i\theta} \cdot \frac{1}{\sqrt{2}}|\tau_2\rangle) \quad (20.19)$

Since our eigenvalues are $\lambda_1 = e^{2i\theta}$ and $\lambda_2 = e^{-2i\theta}$ and we have $m$ control qubits

$$\theta = \frac{x\pi}{2^m} \quad (20.20)$

and with $n$ being the number of state of Grover's amplification

$$\sin^2 \theta = \frac{k}{n} \quad (20.21)$

with

$k = \sin^2 \theta \cdot n = \sin^2(\frac{(x\cdot\pi)}{2^m}) \cdot n.$