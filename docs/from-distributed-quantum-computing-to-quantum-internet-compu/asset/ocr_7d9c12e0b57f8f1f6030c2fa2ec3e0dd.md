To see this, note that the output of the circuit is (n + 1) qubits with a state of the form:

$\alpha |0\rangle \otimes |x\rangle \otimes |0\rangle^{\otimes(n-1)} + \beta |1\rangle \otimes |x\rangle \otimes |1\rangle^{\otimes(n-1)}$

(where $x$ is either “0” or “1” depending on the measurement outcome on the second line), and leaving out the second qubit \(|x\rangle\), we have the cat-like state:

$\alpha |0\rangle |0\rangle^{\otimes(n-1)} + \beta |1\rangle |1\rangle^{\otimes(n-1)} = \alpha |0\rangle^{\otimes n} + \beta |1\rangle^{\otimes n}$

And a cat-disentangler is of the form:

![](bbox=[0.4, 0.29, 0.61, 0.54])

where the measurement outcomes from the lines are summed (mod 2) and the sum used as control to determine if the \( Z \) gate will be applied. The circuit will take a \( (n+1) \) qubit state: \( \alpha |0\rangle \otimes |x\rangle \otimes |0\rangle^{\otimes(n-1)} + \beta |1\rangle \otimes |x\rangle \otimes |1\rangle^{\otimes(n-1)} \) (only the position of \(|x\rangle\) indicated above) and output: \( (\alpha |0\rangle + \beta |1\rangle) \otimes |x\rangle \otimes |s\rangle \), where \( s \) is an \( (n-1) \) bit string, i.e. \(|s\rangle\) is an \( (n-1) \) qubit state due to the measurements from line 3 onwards – the effect is to disentangle the top qubit from the other qubits.

To illustrate these modules being used in circuits, we highlight in Figure 4.6 the cat-entangler and cat-disentangler modules as they were used in the circuits we have seen (i.e. Figures 4.2–4.5).

Note that we could replace the \( X \) gate in the circuits we have seen with some other operation, say \( U \), and so, generalize to a distributed controlled-\( U \) operation.

# 4.3 Distributing Quantum Circuits and Compilation for Distributed Quantum Programs

Based on the ideas we have seen, a number of distributed versions of quantum algorithms have been developed, such as a distributed Shor algorithm