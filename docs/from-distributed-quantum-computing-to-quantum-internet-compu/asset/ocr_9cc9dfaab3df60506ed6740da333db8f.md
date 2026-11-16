In the above circuit, $|m\rangle_s$ denotes the state of the auxiliary qubit just before the Bell measurement, and $|\psi\rangle$ is used here to denote the state of the c1 and $s$ qubits after the $CZ$ gate, both of which we detail below.

The received encoded qubit (i.e. a cluster of qubits) $\tau'$, and the auxiliary qubit $s$ can be written as follows:

$|\tau'\rangle \otimes |0\rangle_s = \frac{\alpha}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$
$+ \frac{\alpha}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$
$+ \frac{\beta}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$
$- \frac{\beta}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes |0\rangle_s$

Then, looking at the circuit, after applying the $H$ gate to $|0\rangle_s$ and $CZ_{c1s}$, we get the state $|\psi\rangle$:

$|\psi\rangle = \frac{\alpha}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$
$+ \frac{\alpha}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$
$+ \frac{\beta}{2}|0\rangle_{c1}|++\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$
$- \frac{\beta}{2}|1\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$

Then, as in the circuit, an $X$ basis measurement is done; suppose the $X$ measurement is successful, and $|+\rangle$ is obtained, the above state becomes: $|\psi'\rangle = \frac{|+\rangle\langle +| \otimes I^{\otimes 6}|\psi\rangle}{\sqrt{1/2}}$, that is (recalling that $|0\rangle = (|+\rangle + |-\rangle)/\sqrt{2}$ and $|1\rangle = (|+\rangle - |-\rangle)/\sqrt{2}$:

$|\psi'\rangle = \frac{\alpha}{2}|+\rangle_{c1}|+++\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$
$+ \frac{\alpha}{2}|+\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$
$+ \frac{\beta}{2}|+\rangle_{c1}|+++\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)_s$
$- \frac{\beta}{2}|+\rangle_{c1}|--\rangle \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)_s$