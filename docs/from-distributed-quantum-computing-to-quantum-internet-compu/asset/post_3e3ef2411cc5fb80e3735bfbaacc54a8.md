
In the above circuit, $|m\rangle_s$ denotes the state of the auxiliary qubit just before the Bell measurement, and $|\psi\rangle$ is used here to denote the state of the c1 and $s$ qubits after the $CZ$ gate, both of which we detail below.

The received encoded qubit (i.e. a cluster of qubits) $\tau'$, and the auxiliary qubit $s$ can be written as follows:

$$|\tau'\rangle \otimes |0\rangle_s = \frac{\alpha}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$$
$$+ \frac{\alpha}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$$
$$+ \frac{\beta}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$$
$$- \frac{\beta}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$$

Then, looking at the circuit, after applying the $H$ gate to $|0\rangle_s$ and $CZ_{c1s}$, we get the state $|\psi\rangle$:

$$|\psi\rangle = \frac{\alpha}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$$
$$+ \frac{\alpha}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$$
$$+ \frac{\beta}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$$
$$- \frac{\beta}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$$

Then, as in the circuit, an $X$ basis measurement is done; suppose the $X$ measurement is successful, and $|+\rangle$ is obtained, the above state becomes: $|\psi'\rangle = \frac{|+\rangle\langle +| \otimes I^{\otimes 6}|\psi\rangle}{\sqrt{1/2}}$, that is (recalling that $|0\rangle = (|+\rangle + |-\rangle)/\sqrt{2}$ and $|1\rangle = (|+\rangle - |-\rangle)/\sqrt{2}$):

$$|\psi'\rangle = \frac{\alpha}{2}|+\rangle_{c1}|+++\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$$
$$+ \frac{\alpha}{2}|+\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$$
$$+ \frac{\beta}{2}|+\rangle_{c1}|+++\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$$
$$- \frac{\beta}{2}|+\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$$
which can be simplified, including leaving out the measured first qubit c1, so that we now write:

$$|\psi'\rangle = \frac{\alpha}{2} |++\rangle \otimes (|0\rangle_{c2} |++\rangle + |1\rangle_{c2} |--\rangle) \otimes |+\rangle_s$$ $$+ \frac{\alpha}{2} |--\rangle \otimes (|0\rangle_{c2} |++\rangle + |1\rangle_{c2} |--\rangle) \otimes |-\rangle_s$$ $$+ \frac{\beta}{2} |++\rangle \otimes (|0\rangle_{c2} |++\rangle - |1\rangle_{c2} |--\rangle) \otimes |+\rangle_s$$ $$- \frac{\beta}{2} |--\rangle \otimes (|0\rangle_{c2} |++\rangle - |1\rangle_{c2} |--\rangle) \otimes |-\rangle_s$$

Suppose this is successful, then the right branch qubits (i.e. “(|0⟩c2 |++⟩ + |1⟩c2 |--⟩)” above) can be measured out. Let’s see what we are then left with. We write the state for \(|\psi''\rangle\), leaving out the (measured out) right branch qubits⁶:

$$|\psi''\rangle = \frac{\alpha}{\sqrt{2}} |++\rangle \otimes |+\rangle_s + \frac{\alpha}{\sqrt{2}} |--\rangle \otimes |-\rangle_s$$ $$+ \frac{\beta}{\sqrt{2}} |++\rangle \otimes |+\rangle_s - \frac{\beta}{\sqrt{2}} |--\rangle \otimes |-\rangle_s$$ $$= \frac{\alpha + \beta}{\sqrt{2}} |++\rangle \otimes |+\rangle_s + \frac{\alpha - \beta}{\sqrt{2}} |--\rangle \otimes |-\rangle_s$$ $$= \frac{\alpha + \beta}{2\sqrt{2}} (|00\rangle + |01\rangle + |10\rangle + |11\rangle) \otimes |+\rangle_s$$ $$+ \frac{\alpha - \beta}{2\sqrt{2}} (|00\rangle - |01\rangle - |10\rangle + |11\rangle) \otimes |-\rangle_s$$ $$= |00\rangle \otimes \left( \frac{\alpha + \beta}{2\sqrt{2}} |+\rangle_s + \frac{\alpha - \beta}{2\sqrt{2}} |-\rangle_s \right) + |01\rangle \otimes \left( \frac{\alpha + \beta}{2\sqrt{2}} |+\rangle_s - \frac{\alpha - \beta}{2\sqrt{2}} |-\rangle_s \right)$$ $$+ |10\rangle \otimes \left( \frac{\alpha + \beta}{2\sqrt{2}} |+\rangle_s - \frac{\alpha - \beta}{2\sqrt{2}} |-\rangle_s \right) + |11\rangle \otimes \left( \frac{\alpha + \beta}{2\sqrt{2}} |+\rangle_s + \frac{\alpha - \beta}{2\sqrt{2}} |-\rangle_s \right)$$

Now we measure the first two qubits shown above, and suppose the measurement of these second-level qubits (associated with c1) in the Z basis yielded \(|00\rangle\) with probability 1/4, we obtain \(\frac{1}{\sqrt{1/4}}(\frac{\alpha+\beta}{2}|+\rangle_s + \frac{\alpha-\beta}{2}|-\rangle_s) = \frac{\alpha+\beta}{\sqrt{2}}|+\rangle_s + \frac{\alpha-\beta}{\sqrt{2}}|-\rangle_s = \alpha|0\rangle_s + \beta|1\rangle_s\), i.e. \(|m\rangle_s = \alpha|0\rangle_s + \beta|1\rangle_s\), which is used in the subsequent Bell measurement to be encoded in the new tree-cluster state. This is similar if $|11\rangle$ was obtained. But if the measurement yielded $|01\rangle$, we obtain $\beta|0\rangle_s + \alpha|1\rangle_s$, and then applying an X gate would yield $\alpha|0\rangle_s + \beta|1\rangle_s$ which can be used in the Bell measurement (and similarly, for $|10\rangle$). Note that this is similar to how we dealt with $|i\rangle$ earlier.

6 Note that measuring out the right branch qubits, suppose the measurement yielded $|0\rangle_{c2} |++\rangle$ (with probability 1/2), we then have the state: \(\frac{(I \otimes I \otimes |0++\rangle \langle 0++| \otimes I) |\psi'\rangle}{\sqrt{1/2}}\).

Note that if measuring c1 is not successful (i.e. the X measurement failed), then the same process is retried for the other first-level qubit, c2. A Bell measurement is then done with the qubit denoted by $|m\rangle_s$ in the circuit and the root of a new tree-cluster state, i.e. reencoding the state in a new tree-cluster state for further transmission.

Three generations of quantum repeaters have been identified in Yan et al. [2021] and Muralidharan et al. [2016], and the above illustrates the idea of a third-generation quantum repeater, where “redundant” qubits are used when transmitting entangled qubits (e.g. one qubit from a pair of entangled qubits) in order to be fault tolerant.

## 6.2 Entanglement with Higher Fidelity

### 6.2.1 Fidelity

We first consider a precise model of fidelity, of what it means for a quantum state to be close to some ideal.7 Due to noise, an entangled state may not be what exactly we want it to be. The consequences of noisy distributed entanglement include failure of particular nonlocal quantum gate operations and problems in quantum protocols, e.g. in QKD, an imperfect entangled state produces a partially correlated key. There is a need to evaluate the quality of a distributed entanglement and then think of how to improve the quality of the entanglement. One way to measure the quality of entanglement is to use the notion of fidelity. Given a reference (ideal) state |ψ⟩ and the actual state ρ shared by two nodes, the fidelity, denoted by the function F, between the reference and actual state is F(ρ, |ψ⟩) = ⟨ψ|ρ|ψ⟩. There are

7 Our discussions are based on the lectures at https://www.youtube.com/watch?v=MD9uDrly4Ms and https://www.youtube.com/watch?v=GSz6a8Mp-9w [last accessed: 16/11/2022].
