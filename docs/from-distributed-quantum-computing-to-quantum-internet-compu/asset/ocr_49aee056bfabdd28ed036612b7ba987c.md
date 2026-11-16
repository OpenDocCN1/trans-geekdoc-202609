![](bbox=[0.108, 0.108, 0.905, 0.345])

Figure 4.3 Distributed CNOT with single control qubit (on A) for multiple target qubits (one on B and one on C).

Then, the second qubit (from the top) is measured, and

+   1) if we get a 0, and this is sent from A to B and C, and since it is 0, the X gate is not applied at both B and C, then, at slice 3, we have:

at slice 3 : \(\sqrt{2} \cdot \left( \frac{\alpha}{\sqrt{2}} |0000\rangle + \frac{\beta}{\sqrt{2}} |1011\rangle \right) \otimes |t\rangle \otimes |s\rangle = (\alpha |0000\rangle + \beta |1011\rangle) \otimes |t\rangle \otimes |s\rangle\)

since \(\frac{1}{\sqrt{\text{prob(0) in second qubit}}} = \frac{1}{\sqrt{|\frac{\alpha}{\sqrt{2}}|^2 + |\frac{\beta}{\sqrt{2}}|^2}} = \frac{1}{\sqrt{1/2}} = \sqrt{2}\), and then applying the CNOT between the two qubits at B and at C, both locally:

at slice 4 : \(\alpha |0000\rangle |t\rangle |s\rangle + \beta |1011\rangle (X |t\rangle)(X |s\rangle)\)

and then applying gate H in the third line and fifth line (from the top):

at slice 5 : \(\alpha |00\rangle (H |0\rangle)(H |0\rangle) |t\rangle |s\rangle + \beta |10\rangle (H |1\rangle)(H |1\rangle)(X |t\rangle)(X |s\rangle)\)
\(= \frac{\alpha}{2} |0000\rangle |t\rangle |s\rangle + \frac{\alpha}{2} |0001\rangle |t\rangle |s\rangle\)
\(+ \frac{\alpha}{2} |0010\rangle |t\rangle |s\rangle + \frac{\alpha}{2} |0011\rangle |t\rangle |s\rangle\)
\(+ \frac{\beta}{2} |1000\rangle (X |t\rangle)(X |s\rangle) - \frac{\beta}{2} |1001\rangle (X |t\rangle)(X |s\rangle)\)
\(- \frac{\beta}{2} |1010\rangle (X |t\rangle)(X |s\rangle) + \frac{\beta}{2} |1011\rangle (X |t\rangle)(X |s\rangle)\)