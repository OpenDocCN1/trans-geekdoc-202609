There are two classes:

+   * No permutation *i)* or permutation of all elements *ii)* indicates that the function is constant.

+   * Permutation of two elements *iii)* indicates that the function is non-constant.

The algorithm to determine if $f(x)$ is constant or not is composed of four steps. In the first step of the algorithm we build a superposition of two qubits

```
$H_2 \cdot |01\rangle = H_1 \cdot |00\rangle \otimes |1\rangle = \frac{|0\rangle+|1\rangle}{\sqrt{2}} \otimes \frac{|0\rangle-|1\rangle}{\sqrt{2}} = \nH_2 \cdot |01\rangle = \frac{1}{2} \cdot ((00) - |01| + |10| - |11)).$.
```

```
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram

qc = QuantumCircuit(2)
qc.x(0)
qc.h(0)
qc.h(1)
```

```
simulator = Aer.get_backend('statevector_simulator')
final_state = execute(qc, simulator).result().get_statevector()
from qiskit.visualization import array_to_latex
array_to_latex(final_state, prefix="\text{Statevector}") = "
```

with the output

```
$Statevector = \frac{1}{2} - \frac{1}{2} - \frac{1}{2} - \frac{1}{2}.$
```

In the second step we apply the $U_f$, gate.

```
$U_f \cdot |01\rangle = U_f \cdot \frac{1}{2}((00) - |01| + |10| - |11)) = \frac{1}{2} \cdot ((00) - |01| + U_f \cdot |10| - U_f \cdot |11|)).
```

There are four possible outputs. For constant function

```
$i) \frac{1}{2} \cdot ((00) - |01| + |10| - |11|) = \frac{|0\rangle+|1\rangle}{\sqrt{2}} \otimes \frac{|0\rangle-|1\rangle}{\sqrt{2}},$
```

```
$ii) \frac{1}{2} \cdot (-(01) + |00| + |10])) = \frac{1}{2} \cdot ((-|01\rangle + |00\rangle + |10\rangle) + |11\rangle) = (-\frac{|0\rangle-|1\rangle}{\sqrt{2}}) \otimes (\frac{|0\rangle-|1\rangle}{\sqrt{2}}) - (\frac{|0\rangle+|1\rangle}{\sqrt{2}}) \otimes (\frac{|0\rangle-|1\rangle}{\sqrt{2}}).$
```

and for non-constant function

```
$iii) = \frac{1}{2} \cdot ((00) - |01| + |10| - |11|) = \frac{1}{2} \cdot ((00) - |01| + |10| + |11)).$
```