# Quantum Fourier Transform 249

and the QFT $F_2$ is

```
$F_2 = \frac{1}{\sqrt{4}} \begin{pmatrix} 1 & 1 & 1 & 1 \ 1 & \zeta_4 & \zeta_4^2 & \zeta_4^3 \ 1 & \zeta_4^2 & \zeta_4^4 & \zeta_4^6 \ 1 & \zeta_4^3 & \zeta_4^6 & \zeta_4^9 \end{pmatrix} = \begin{pmatrix} 1 & 1 & 1 & 1 \ 1 & -i & -1 & -i \ 1 & -1 & 1 & -1 \ 1 & i & -1 & -i \end{pmatrix} \quad (19.14)$
```

and the inverse QFT is

```
$IF_2 = F_2^T = \frac{1}{\sqrt{4}} \begin{pmatrix} 1 & 1 & 1 & 1 \ 1 & -i & -1 & -i \ 1 & -1 & 1 & -1 \ 1 & i & -1 & -i \end{pmatrix} \ \quad (19.15)$
```

For three qubits $m = 3, n = 8$

```
$\zeta_8 = e^{2\pi i/8} = \frac{1+i}{\sqrt{2}}$
```

```
$F_3 = \frac{1}{\sqrt{8}} \begin{pmatrix} 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \ 1 & e^{2\pi i/8} & e^{4\pi i/8} & e^{6\pi i/8} & e^{8\pi i/8} & e^{10\pi i/8} & e^{12\pi i/8} & e^{14\pi i/8} \ 1 & e^{4\pi i/8} & e^{8\pi i/8} & e^{12\pi i/8} & e^{16\pi i/8} & e^{20\pi i/8} & e^{24\pi i/8} & e^{28\pi i/8} \ 1 & e^{6\pi i/8} & e^{12\pi i/8} & e^{18\pi i/8} & e^{24\pi i/8} & e^{30\pi i/8} & e^{36\pi i/8} & e^{42\pi i/8} \ 1 & e^{8\pi i/8} & e^{16\pi i/8} & e^{24\pi i/8} & e^{32\pi i/8} & e^{40\pi i/8} & e^{48\pi i/8} & e^{56\pi i/8} \ 1 & e^{10\pi i/8} & e^{20\pi i/8} & e^{30\pi i/8} & e^{40\pi i/8} & e^{50\pi i/8} & e^{60\pi i/8} & e^{70\pi i/8} \ 1 & e^{12\pi i/8} & e^{24\pi i/8} & e^{36\pi i/8} & e^{48\pi i/8} & e^{60\pi i/8} & e^{72\pi i/8} & e^{84\pi i/8} \ 1 & e^{14\pi i/8} & e^{28\pi i/8} & e^{42\pi i/8} & e^{56\pi i/8} & e^{70\pi i/8} & e^{84\pi i/8} & e^{98\pi i/8} \ 1 & e^{16\pi i/8} & e^{32\pi i/8} & e^{48\pi i/8} & e^{64\pi i/8} & e^{80\pi i/8} & e^{96\pi i/8} & e^{112\pi i/8} \end{pmatrix} \ \quad (19.16)$
```

The first row of $F_3$ is the DC amplitude of the input state measured, the following rows represent the AC (difference) of the input state amplitudes.

# 19.3 DECOMPOSITION

The QFT can factored into the tensor product of $m$ single-qubit operations [47].

```
$|y\rangle = F_m \cdot |x\rangle = \frac{1}{\sqrt{n}} \sum_{y_B \in B^m} e^{2\pi i y_B \cdot x} \cdot |y\rangle =$
```

```
$$\frac{1}{\sqrt{n}} \cdot \left(\sum_{y_m \in \{0,1\}} e^{2\pi i y_m \cdot x_{x_1}}\right) \cdot \left(\sum_{y_{m-1} \in \{0,1\}} e^{2\pi i y_{m-1} \cdot x_{x_2}}\right) \cdot \dots$
```

```
$$\dots \cdot \left(\sum_{y_1 \in \{0,1\}} e^{2\pi i y_1 \cdot x_{x_1}}\right) \quad (19.17)$
```

```
$$\frac{1}{\sqrt{n}} \cdot \left(|0\rangle + e^{2\pi i \cdot x_{x_1}} |1\rangle\right) \ \otimes \left(|0\rangle + e^{2\pi i \cdot x_{x_2}} |1\rangle\right) \ \otimes \dots \ \dots$
```

```
$$\dots \cdot \left(|0\rangle + e^{2\pi i \cdot x_{x_m \dots x_1}} |1\rangle\right)$
```