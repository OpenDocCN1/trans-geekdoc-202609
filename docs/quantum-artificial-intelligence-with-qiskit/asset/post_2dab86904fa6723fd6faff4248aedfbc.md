
# 58 Quantum Artificial Intelligence with Qiskit

```
$= \left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right) \otimes \left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right),\
niv) = \frac{1}{2} \cdot (|01\rangle-|00\rangle+|10\rangle-|11\rangle) = \frac{1}{2} \cdot (-|00\rangle+|01\rangle+|10\rangle)
-\left(\frac{|0\rangle+|1\rangle}{\sqrt{2}}\right) \otimes \left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right) = -\left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right) \otimes \left(\frac{|0\rangle+|1\rangle}{\sqrt{2}}\right).$
```

In the third step a Hadamard gate is applied to the first qubit

```
$H_1 \cdot I_2 \cdot H_2 \cdot |01\rangle. \quad (3.7)$
```

There are four possible outcomes,

```
$i) |0\rangle \otimes \left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right),\
ii) -|0\rangle \otimes \left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right),\
iii) |1\rangle \otimes \left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right),\
vi) -|1\rangle \otimes \left(\frac{|0\rangle-|1\rangle}{\sqrt{2}}\right).$
```

In the fourth step the first qubit (that is in the base state) is measured. It is $|0\rangle$ if the function is constant, otherwise $|1\rangle$.

In our simulation, for simplicity we assume the unknown function is the identity mapping $f(x)=0$

```
$i \ U_f(00) = |0\rangle\otimes|0\rangle = |00\rangle, U_f(01) = |01\rangle,\
U_f(10) = |10\rangle, U_f(11) = |11\rangle$.
```

```python
qc = QuantumCircuit(2,1)
qc.x(0)
qc.barrier()
qc.h(0)
qc.h(1)
#constant function f(x)=0, do nothing
qc.barrier()
qc.h(1)
#Measure the qubit 1
qc.measure(1,0)
qc.draw()
```

```python
simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
print("\nTotal count are:",counts)
plot_histogram(counts)
```

# Qiskit ■59

![](img/52faec2d621d75e53089d939bb234a82_85_0.png)

**Figure 3.17** The quantum circuit representing the Deutsch algorithm for the unknown function identity mapping $f(x) = 0$.

see the Figures 3.17 and 3.18. For the non-constant function, $f(x) = x$ corresponds to a permutation of two elements.

- iii) $U_f(|0\rangle) = |0\rangle|0\rangle = |00\rangle, U_f(|1\rangle) = |01\rangle$,
$U_f(|10\rangle) = |11\rangle$

This operation can be achieved by the Controlled NOT gate. The CNOT gate flips the second qubit (the target qubit) if and only if the first qubit (control qubit) is one. In our case the control qubit is $q_1$ the target qubit $q_1.cx(1,0)$

```python
qc = QuantumCircuit(2,1)

```python
qc.x(0)
qc.barrier()
qc.h(0)
qc.h(1)
#identity function f(x)=x
qc.cx(1,0)
qc.barrier()
```

![](img/52faec2d621d75e53089d939bb234a82_85_1.png)

**Figure 3.18** In the fourth step the first qubit (that is in the basis state) is measured. It is $|0\rangle$, the function is constant. Total count are: $\{'0' : 1024\}$. By default the number of shots is 1024 if not specified.

Quantum Artificial Intelligence with Qiskit

![](img/52faec2d621d75e53089d939bb234a82_86_0.png)

Figure 3.19 The quantum circuit representing the Deutsch algorithm for the unknown function the non-constant function, $f(x)=x$.

```python
simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
print("\nTotal count are:",counts)
plot_histogram(counts)
```

```python
qc.h(1)
qc.measure(1,0)
qc.draw()
```

see the Figures 3.19 and 3.20.

# 3.9 DEUTSCH ALGORITHM ON A REAL QUANTUM COMPUTER

Richard Feynman asked in the early twenties whether a quantum system can be simulated on an imaginary quantum computer. Today, 40 years later first small quantum computers begin to appear. During recent years a huge progress was achieved in keeping the quits coherent, opening the road to a universal quantum computer and

![](img/52faec2d621d75e53089d939bb234a82_86_1.png)

Figure 3.20 In the first step the first qubit (that is in the basis state) is measured. It is |1>, the function is non-constant. Total count are: ("1": 1024). By default the number of shots is 1024 if not specified.

# Qiskit 61

![](img/52faec2d621d75e53089d939bb234a82_87_0.png)

**Figure 3.21** The quantum circuit representing the Deutsch algorithm for the unknown function identity mapping $f(x) = 0$.

see the Figures 3.17 and 3.18. For the non-constant function, $f(x) = x$ corresponds to a permutation of two elements.

- iii) $U_f(|0\rangle) = |0\rangle|0\rangle = |00\rangle, U_f(|1\rangle) = |01\rangle$,
$U_f(|10\rangle) = |11\rangle$

This operation can be achieved by the Controlled NOT gate. The CNOT gate flips the second qubit (the target qubit) if and only if the first qubit (control qubit) is one. In our case the control qubit is $q_1$ the target qubit $q_1.cx(1,0)$

```python
qc = QuantumCircuit(2,1)

```python
qc.x(0)
qc.barrier()
qc.h(0)
qc.h(1)
#identity function f(x)=x
qc.cx(1,0)
qc.barrier()
```

![](img/52faec2d621d75e53089d939bb234a82_85_1.png)

**Figure 3.18** In the fourth step the first qubit (that is in the basis state) is measured. It is $|0\rangle$, the function is constant. Total count are: $\{'0' : 1024\}$. By default the number of shots is 1024 if not specified.

Quantum Artificial Intelligence with Qiskit

![](img/52faec2d621d75e53089d939bb234a82_86_0.png)

Figure 3.19 The quantum circuit representing the Deutsch algorithm for the unknown function the non-constant function, $f(x)=x$.

```python
simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
print("\nTotal count are:",counts)
plot_histogram(counts)
```

```python
qc.h(1)
qc.measure(1,0)
qc.draw()
```

see the Figures 3.19 and 3.20.

# 3.9 DEUTSCH ALGORITHM ON A REAL QUANTUM COMPUTER

Richard Feynman asked in the early twenties whether a quantum system can be simulated on an imaginary quantum computer. Today, 40 years later first small quantum computers begin to appear. During recent years a huge progress was achieved in keeping the quits coherent, opening the road to a universal quantum computer and

![](img/52faec2d621d75e53089d939bb234a82_86_1.png)

Figure 3.20 In the first step the first qubit (that is in the basis state) is measured. It is |1>, the function is non-constant. Total count are: ("1": 1024). By default the number of shots is 1024 if not specified.

# Qiskit 61

![](img/52faec2d621d75e53089d939bb234a82_87_0.png)

**Figure 3.21** The quantum circuit representing the Deutsch algorithm for the unknown function identity mapping $f(x) = 0$.

see the Figures 3.17 and 3.18. For the non-constant function, $f(x) = x$ corresponds to a permutation of two elements.

- iii) $U_f(|0\rangle) = |0\rangle|0\rangle = |00\rangle, U_f(|1\rangle) = |01\rangle$,
$U_f(|10\rangle) = |11\rangle$

This operation can be achieved by the Controlled NOT gate. The CNOT gate flips the second qubit (the target qubit) if and only if the first qubit (control qubit) is one. In our case the control qubit is $q_1$ the target qubit $q_1.cx(1,0)$

```python
qc = QuantumCircuit(2,1)

```python
qc.x(0)
qc.barrier()
qc.h(0)
qc.h(1)
#identity function f(x)=x
qc.cx(1,0)
qc.barrier()
```

![](img/52faec2d621d75e53089d939bb234a82_85_1.png)

**Figure 3.18** In the fourth step the first qubit (that is in the basis state) is measured. It is $|0\rangle$, the function is constant. Total count are: $\{'0' : 1024\}$. By default the number of shots is 1024 if not specified.

## Quantum Artificial Intelligence with Qiskit

![](img/52faec2d621d75e53089d939bb234a82_86_0.png)

Figure 3.19 The quantum circuit representing the Deutsch algorithm for the unknown function the non-constant function, $f(x)=x$.

```python
simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
print("\nTotal count are:",counts)
plot_histogram(counts)
```

```python
qc.h(1)
qc.measure(1,0)
qc.draw()
```

see the Figures 3.19 and 3.20.

# 3.9 DEUTSCH ALGORITHM ON A REAL QUANTUM COMPUTER

Richard Feynman asked in the early twenties whether a quantum system can be simulated on an imaginary quantum computer. Today, 40 years later first small quantum computers begin to appear. During recent years a huge progress was achieved in keeping the quits coherent, opening the road to a universal quantum computer and

![](img/52faec2d621d75e53089d939bb234a82_86_1.png)

Figure 3.20 In the first step the first qubit (that is in the basis state) is measured. It is |1>, the function is non-constant. Total count are: ("1": 1024). By default the number of shots is 1024 if not specified.

# Qiskit 61

![](img/52faec2d621d75e53089d939bb234a82_87_0.png)

**Figure 3.21** The quantum circuit representing the Deutsch algorithm for the unknown function identity mapping $f(x) = 0$.
