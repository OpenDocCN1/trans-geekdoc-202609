# Quantum Machine Learning

# ### 3.2.2 Angle/parametric encoding

This method takes a different approach, using the relative phase between quantum states to hold information. In essence, data values are encoded in the angle of the quantum state's phase, allowing quantum algorithms to then manipulate these angles. It is akin to encoding information in the direction the quantum state points in a complex plane, providing another avenue for representing continuous data values. Angle encoding each component of $x$ to the rotation angle of a single-qubit gate:

```
$x_i \rightarrow R_{\sigma^\alpha}(x_i) = \exp(-\frac{x_i}{2}\sigma^\alpha), \quad \alpha \in \{x, y, z\};$
```

where $\sigma^\alpha$ denotes the corresponding Pauli matrix. Angle encoding is hardware-friendly and particularly suited for variational quantum algorithms implemented on noisy intermediate-scale quantum (NISQ) devices.

# ### 3.2.3 Basis encoding

In encoding, each classical data point corresponds to a particular quantum state in the computational basis. For instance, classical binary data as 01 can be mapped directly to the quantum state $|0\rangle$:

```
$x \in \{0, 1\}^n \rightarrow [x'] = |x_1\rangle \otimes \dots \otimes |x_n\rangle$;
```

This method provides a straightforward way to store classical information, in particular for data that already exists in binary format. This approach is efficient for qubit usage for binary strings but lacks expressivity for general learning tasks.

# ### 3.2.4 Hamiltonian encoding

Hamiltonian encoding refers to a class of quantum embedding strategies where classical or structured input data $(x)$ is used to define a Hamiltonian $H(x)$, and the quantum state is prepared through its unitary evolution. Formally, a parameter-dependent Hamiltonian $H(x)$, the embedding is implemented via the unitary operator $U(x) = e^{iH(x)}$ applied to some initial state $|0\rangle$ or another reference state. The result is a quantum state $|q(x)\rangle = U(x)|0\rangle$ that encodes the data implicitly in its time-evolved dynamics. This is sometimes referred to as *Hamiltonian simulation-based encoding*.

Hamiltonian encoding is particularly well-suited for structured data with a natural physical interpretation, as graphs, spin systems, or molecular structures, one can construct a meaningful Hamiltonian representation of the input. It is also used in quantum kernel methods, where the feature map corresponds to the evolution under data-dependent generators.

A common choice in practice is to decompose the Hamiltonian into a sum of Pauli terms, $H(x) = \sum_j x_j P_j$, where $(x_j)$ are real-valued coefficients derived from the classical input and $(P_j)$ are tensor products of Pauli operators (i.e., elements of the Pauli group). This form allows for efficient implementation of $(U(x))$

3-5