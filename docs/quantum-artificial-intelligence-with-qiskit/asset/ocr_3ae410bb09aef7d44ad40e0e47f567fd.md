# 74 Quantum Artificial Intelligence with Qiskit

# 4.6 UNIVERSALITY

Unitary decomposition is the process of translating an arbitrary unitary operator into a universal set of single and two-qubit gates. Unitary decomposition is necessary because it is not otherwise possible to execute an arbitrary quantum operator. The Z-Y decomposition theorem [72] provides a way of expressing an unitary operation $U$ on single qubits by parametrized rotation gates

Z-Y Decomposition Theorem: If $u$ is an unitary operation on single qubit, then there exist real numbers $\alpha$, $eta$, and $\gamma$ such that

```
$U = e^{\alpha R_z(eta)} \cdot R_y(\gamma) \cdot R_z(\delta) \quad (4.1)$
```

For example, in quantum machine learning a Hadamard-like transformation $S_p$ is used to store the patterns.

```
$S_p = \begin{pmatrix} \sqrt{\frac{p-1}{p}} & \frac{1}{\sqrt{p}} \ \frac{1}{\sqrt{p}} & -\sqrt{\frac{p-1}{p}} \end{pmatrix} \quad (4.2)$
```

and can be represented by the parametrized unitary $U$ with $\phi = \pi, \lambda = \pi$,

```
$U(\theta, \pi, \pi) = \begin{pmatrix} \cos(\frac{\theta}{2}) & \sin(\frac{\theta}{2})\\ \-\sin(\frac{\theta}{2}) & \cos(\frac{\theta}{2}) \end{pmatrix}$
```

With

```
$\sin(\frac{\theta}{2}) = \frac{1}{\sqrt{P}}$
```

```
$$\theta = \arcsin(\frac{1}{\sqrt{P}}) \cdot 2$
```

```
$$\cos(\frac{\theta}{2}) = \sqrt{\frac{p-1}{p}}$
```

```
$U(\arcsin(\frac{1}{\sqrt{P}}) \cdot 2, \pi, \pi) = \begin{pmatrix} \frac{1}{\sqrt{P}} & \sqrt{\frac{p-1}{p}}\\\-\sqrt{\frac{p-1}{p}} & \frac{1}{\sqrt{P}} \end{pmatrix} \quad (4.3)$
```

# 4.7 QUANTUM CIRCUITS

The depth of a quantum circuit indicates the quantum gates that can be executed in parallel throughout the entire circuit. The depth is related to the time to execute the circuit. The depth is indicated with the command $qc.size()$. We either simulate a quantum circuit or execute it on a real quantum computer. The defined quantum circuit is converted to the target quantum computer for execution. This process is called **transp** contrary to the compilation task in classical programming languages. It is a translation problem determined by the available set of operations and