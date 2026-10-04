# 240 Quantum Artificial Intelligence with Qiskit

After 1000 shots we measure $p[0]=0.956$ with (see [Figure 17.2 (b)](https://example.com))

$k(x,y)=\|0^mangle U_{\Phi(x,y)}|0^mangle|^2=0.956$.

# 17.2 Quantum Feature Maps

Quantum feature maps encodes classical data into quantum data via a parametrized quantum circuit that are hard to simulate classically and is an active area of research. Vch Havlick [40] and his collaborators propose a family of quantum Pauli feature maps that are believed to be hard to simulate classically, and can be implemented by circuit with few layers of gates. The Pauli feature maps of depth $d$ contains layers of Hadamard interleaved with a circuit that contains entangling gates (such as CNOTs). The Pauli feature maps of circuit $d$ is a data encoding circuit that transforms input x data of dimension $z=m$

$U_{\Phi}(x) = \prod U_{\Phi}(x) \otimes H^{\otimes m}, \ U_{\Phi}(x) = \exp\left(i \cdot \sum_{S\leq|m|} \phi_S(x) \prod_{j\in S} P_j\right) \quad (17.9)$

where $P_j$ corresponds to Pauli gates

$P_j \in \{I, X, Y, Z\}$

The index $S$ indicates connectivity between different qubits represented by combination

$S \in \begin{cases} m \cdot (m-1) \cdots \cdot (m-k+1) \ k \cdot (k-1) \cdots 1 \end{cases} \text{ for } k \leq m$$

with

$$\phi_S(x) = \begin{cases} x_i & \text{if } S=\{i\} \ (\pi-x_i) \cdot (\pi-x_j) & \text{if } S=\{i,j\} \end{cases}$$

Qiskit implements these as the *PauliFeatureMap*. A special case for $k=2$ using Z gates is called the *ZZFeatureMap*

$U_{\Phi}(x) = \exp\left(i \cdot \sum_{jk} \phi_{(jk)}(x) Z_j \otimes Z_k\right) \exp\left(i \cdot \sum_{j} \phi_j(x) Z_j\right) H^{\otimes m}^d \quad (17.10)$

represented by [Figure 17.3](https://example.com).

```
from qiskit.circuit.library import ZZFeatureMap
# 2 features, depth 1
map_zz = ZZFeatureMap(feature_dimension=2, reps=1)
map_zz.decompose().draw()
```