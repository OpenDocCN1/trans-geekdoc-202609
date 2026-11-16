transmission, say the first two qubits, we will then be left with either:

(i) \frac{\alpha}{\sqrt{2}} |+\rangle \otimes (|0\rangle |++\rangle + |1\rangle |--\rangle) + \frac{\beta}{\sqrt{2}} |+\rangle \otimes (|0\rangle |++\rangle - |1\rangle |--\rangle))

or

(ii) \frac{\alpha}{\sqrt{2}} |-\rangle \otimes (|0\rangle |++\rangle + |1\rangle |--\rangle) - \frac{\beta}{\sqrt{2}} |-\rangle \otimes (|0\rangle |++\rangle - |1\rangle |--\rangle))

with equal probability, since it is like measuring out the first two qubits.<sup>5</sup> Then, we can measure (in the X basis) the first qubit above to get \(|+\rangle\) or \(|-\rangle\), i.e. one of the two cases. Suppose we get the resulting state in case (i), which we denote by \(|(i)\rangle\):

\(|(i)\rangle = \frac{\alpha}{\sqrt{2}}(|0\rangle |++\rangle + |1\rangle |--\rangle) + \frac{\beta}{\sqrt{2}}(|0\rangle |++\rangle - |1\rangle |--\rangle)\)
\(= \frac{\alpha+\beta}{\sqrt{2}} |0\rangle |++\rangle + \frac{\alpha-\beta}{\sqrt{2}} |1\rangle |--\rangle\)
\(= \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle (|00\rangle + |01\rangle + |10\rangle + |11\rangle) + \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle (|00\rangle - |01\rangle - |10\rangle + |11\rangle)\)
(recalling that \(|+\rangle = (|0\rangle + |1\rangle)/\sqrt{2}\) and \(|-\rangle = (|0\rangle - |1\rangle)/\sqrt{2}\))
\(= \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |00\rangle + \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |01\rangle\)
\(+ \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |10\rangle + \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |11\rangle\)

Then, upon measuring the last two qubits in the Z basis, we get with probability 1/4 one of the following: \(|00\rangle\), \(|01\rangle\), \(|10\rangle\), or \(|11\rangle\). Suppose we get \(|00\rangle\), then we obtain:

\(\frac{(I \otimes |0\rangle \langle 0| \otimes |0\rangle \langle 0|) |(i)\rangle}{\sqrt{1/4}} = \left( \frac{\alpha+\beta}{\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{\sqrt{2}} |1\rangle \right) \otimes |00\rangle\)

Noting that \(\frac{\alpha+\beta}{\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{\sqrt{2}} |1\rangle = \alpha |+\rangle + \beta |-\rangle\), by applying the Hadamard (\(H\)) gate to \(\alpha |+\rangle + \beta |-\rangle\), we obtain the message qubit \(\alpha |0\rangle + \beta |1\rangle\). If we get \(|01\rangle\), we obtain \(\frac{\alpha+\beta}{\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{\sqrt{2}} |1\rangle\), which can be rewritten:

\(\frac{\alpha+\beta}{\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{\sqrt{2}} |1\rangle = Z(\alpha |+\rangle + \beta |-\rangle)\)

By applying HZ to \(Z(\alpha |+\rangle + \beta |-\rangle)\), we can then obtain \(\alpha |0\rangle + \beta |1\rangle\), and similarly, with \(|10\rangle\) and \(|11\rangle\). A similar reasoning with case (ii).

5 To get (i), for example, we compute \(\frac{\langle 0|\langle 0|\langle +| + \langle +| \otimes \langle +| \otimes \langle +| |-\rangle}{\sqrt{1/2}}\) and leave out writing the measured qubits \(|0\rangle |+\rangle\). Similarly, if measuring the first two qubits yields \(|1\rangle |-\rangle\).