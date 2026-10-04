# 200 Quantum Artificial Intelligence with Qiskit

# 15.3 QUANTUM COUNTING ONES

In a binary string of the length $N$ we can represent the fraction of $k$ ones by the simple formula $k/N$ and the zeros as $(N - k)/N$ resulting in a linear relation. We can interpret these as probability values. We can map these linear relations into the sigmoid-like probability functions for the presence of ones using Euler's formula [111] in relation to trigonometry

```
$$\left(\sin\frac{\pi \cdot k}{2 \cdot N}\right)^2 = \frac{e^{\frac{\pi \cdot k}{N}} - e^{-\frac{\pi \cdot k}{N}}}{2} \in [0, 1] \quad (15.9)$
```

and of zeros with

```
$$\left(\cos\frac{\pi \cdot k}{2 \cdot N}\right)^2 = \frac{e^{\frac{\pi \cdot k}{N}} + e^{-\frac{\pi \cdot k}{N}}}{2} \in [0, 1] \quad (15.10)$
```

together with

```
$$\left(\sin\frac{\pi \cdot k}{2 \cdot N}\right)^2 + \left(\cos\frac{\pi \cdot k}{2 \cdot N}\right)^2 = 1$
```

In the Figure 15.5 the sigmoid-like probability functions for $N=8$ are indicated. To count the number of ones we introduced the control qubit in superposition $1/\sqrt{2} \cdot (|0\rangle + |1\rangle)$. For the superposition part represented by the control qubit $|0\rangle$, the phase $e^{i\pi/3}$ is applied for each one. For the superposition part represented by the control qubit $|1\rangle$, the phase $e^{-i\pi/3}$ is applied for each one.

```
$$\frac{1}{\sqrt{2}} \cdot (|e^{i\pi/3} \cdot |1\rangle \otimes |0\rangle \otimes e^{-i\pi/3} \cdot |1\rangle) +$
```

![](bbox=[0.233, 0.584, 0.735, 0.813])

Figure 15.5 Sigmoid-like probability functions for $N=8$ is indicated by continuous line, the linear relation by the dashed lines. The x-axis indicates the $k$ values, the y-axis the probabilities.