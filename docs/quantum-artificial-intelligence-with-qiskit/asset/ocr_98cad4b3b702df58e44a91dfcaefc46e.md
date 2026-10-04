# 82 Quantum Artificial Intelligence with Qiskit

In the next step we represent the state vector with equally distributed amplitudes and mark the solution with a minus sign

```
a=1/np.sqrt(8)
x1=np.array([a,a,a,a,-a,a,a])
print("x1=\n", x1)
x1=
[ 0.3536 0.3536 0.3536 0.3536 -0.3536 0.3536 0.3536 0.3536]
```

and perform a step in Grover's amplification as the resulting amplitudes

```
x1=G.dot(x1)
print("x1=\n", x1)
x1=
[[-0.1768 0.1768 0.1768 0.1768 0.8839 0.1768 0.1768 0.1768]]
```

and the second iteration with the resulting amplitudes

```
x2=np.array([0.1768, 0.1768, 0.1768, 0.1768, -0.8839, 0.1768, 0.1768, 0.1768])
x2=G.dot(x2)
print("x2=\n", x2)
x2=
[[-0.0884 -0.0884 -0.0884 -0.0884 0.9723 -0.0884 -0.0884 -0.0884]]
```

With two rotations we achieved the maximal amplitude value that corresponds to the probability value 0.945367 = |0.9723|^2. After the third rotation the amplitudes diminish because of the periodic property of Grover's amplification (see Figure 5.1).

# 5.5 DECOMPOSITION

With the Grover's amplification we have

> $G_m = -(H_m \cdot \Lambda_m \cdot H_m)$

How can we decompose $\Lambda_m$ by quantum gates? We know that for

> $$\frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \ 1 & -1 \end{pmatrix} \cdot \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & -1 \ 1 & 1 \end{pmatrix} = \begin{pmatrix} 1 & 0 \ 0 & -1 \end{pmatrix}$

and

> $$\begin{pmatrix} 0 & 1 \ 1 & 0 \end{pmatrix} \cdot \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \ 1 & -1 \end{pmatrix} \cdot \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & -1 \ 1 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 1 \ 1 & 0 \end{pmatrix}$

For three qubits we can define $\Lambda_3$ accordingly with

> $X_3 = X \otimes X \otimes X$\n$H_0 = I \otimes I \otimes H$\n$\Lambda_3 = X_3 \cdot H_0 \cdot CCX \cdot H_0 \cdot X_3$