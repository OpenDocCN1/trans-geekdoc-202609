# Quantum Physics and Quantum Computation ■ 37

$CX$ cannot be expressed as a tensor product of $2 \times 2$ matrices. Suppose we start with the state $|00angle$ and map the first qubit bit into the superposition using the Hadamard gate

```
$H_1 \otimes |00angle = (H_1|0angle) \otimes |0angle = \frac{|0angle+|1angle}{\sqrt{2}} \otimes |0angle = \frac{|00angle+|10angle}{\sqrt{2}}$
```

To this state represented by the two qubit we apply $CX$ gate

```
$CX \cdot \left(\frac{|00angle+|10angle}{\sqrt{2}}\right) = \frac{CX\cdot|00angle+CX\cdot|10angle}{\sqrt{2}} = \frac{|00angle+|11angle}{\sqrt{2}}$
```

A register of two qubit is decomposable if it can be represented as a direct product of two qubits. For example the

```
$\frac{|00angle+|10angle+|11angle}{2} = \left(\frac{|0angle+|1angle}{\sqrt{2}}\right) \otimes \left(\frac{|0angle+|1angle}{\sqrt{2}}\right)$
```

is decomposable. In vector notation it is represented as

```
$$\begin{pmatrix} 1/\sqrt{2} \ 1/\sqrt{2} \ 1/\sqrt{2} \ 1/\sqrt{2} \end{pmatrix} = \begin{pmatrix} 1/\sqrt{2} \ 1/\sqrt{2} \end{pmatrix} \otimes \begin{pmatrix} 1/\sqrt{2} \ 1/\sqrt{2} \end{pmatrix}$
```

However, the state of two qubits

```
$$\frac{|00angle+|11angle}{\sqrt{2}} \quad (2.35)$
```

is not decomposable. We preform a proof by contradiction. From the assumption the state is decomposable follows a contradiction.

```
$$\frac{|00angle+|11angle}{\sqrt{2}} = (a_0|0angle+a_1|1angle) \otimes (b_0|0angle+b_1|1angle) = \\n= a_0\cdot b_0|00angle+a_0\cdot b_1|01angle+a_1\cdot b_0|10angle+a_1\cdot b_1|11angle \\n\to a_0\cdot b_0=\frac{1}{\sqrt{2}}, a_0\cdot b_1=0, a_1\cdot b_0=0, a_1\cdot b_1=\frac{1}{\sqrt{2}} \quad (2.36)$
```

that is a contradiction.

A state that is not decomposable is called entangled. If two qubits are entangled in a state $\frac{|00angle+|11angle}{\sqrt{2}}$, observing one of them will result in either $|0angle$ or $|1angle$ with probability $\frac{1}{2}$. However, it is not possible to observe a different value on the other, unobserved qubit. Both qubits behave as one unit and are called an $ebit$. There are four $ebits$:

```
$$\frac{|00angle+|11angle}{\sqrt{2}}, \frac{|00angle-|11angle}{\sqrt{2}}, \frac{|01angle+|10angle}{\sqrt{2}}, \frac{|01angle-|10angle}{\sqrt{2}} \quad (2.37)$
```