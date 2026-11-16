(Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT} |\psi'\rangle
= (Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT}((X^a Z^b \otimes X^c Z^d) |\psi\rangle)
= (Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT}(X^a \otimes X^c)(Z^b \otimes Z^d) |\psi\rangle
= (Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT}(X^a \otimes \mathbf{I})(\mathbf{I} \otimes X^c)(Z^b \otimes \mathbf{I})(\mathbf{I} \otimes Z^d) |\psi\rangle
= (Z^{b+d}X^a \otimes Z^d X^{a+c})(X^a \otimes X^a)(\mathbf{I} \otimes X^c)\text{CNOT}(Z^b \otimes \mathbf{I})(\mathbf{I} \otimes Z^d) |\psi\rangle
(since \text{CNOT}(X^a \otimes \mathbf{I}) = (X^a \otimes X^a)\text{CNOT and CNOT}(\mathbf{I} \otimes X^c)
= (\mathbf{I} \otimes X^c)\text{CNOT})
= (Z^{b+d}X^a \otimes Z^d X^{a+c})(X^a \otimes X^a)(\mathbf{I} \otimes X^c)(Z^b \otimes \mathbf{I})(Z^d \otimes Z^d)\text{CNOT} |\psi\rangle
(since \text{CNOT}(Z^b \otimes \mathbf{I}) = (Z^b \otimes \mathbf{I})\text{CNOT and CNOT}(\mathbf{I} \otimes Z^d)
= (Z^d \otimes Z^d)\text{CNOT})
= (Z^{b+d}X^a X^a Z^b Z^d \otimes Z^d X^{a+c} X^a X^c Z^d)\text{CNOT} |\psi\rangle = \text{CNOT} |\psi\rangle

where we have repeatedly used the identity \(AB \otimes CD = (A \otimes C)(B \otimes D)\). So, \(A\) gets \(\text{CNOT} |\psi\rangle\) as required. Note that we could use \(Z^{b \oplus d}X^a \otimes Z^d X^{a \oplus c}\) as well with the same outcome, replacing “+” with “\(\oplus\).”

What if \(A\) wanted \(B\) to perform a \(R\) gate instead? Note that the \(R\) gate is \(\begin{bmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{bmatrix}\), that is, \(R|0\rangle = |0\rangle\), and \(R|1\rangle = e^{i\pi/4}|1\rangle\). What if we used the approach we have been using with an appropriate operation to recover the result? Suppose \(A\) now has a one-qubit state \(|\psi\rangle\) and then sends the encrypted quantum state to \(B\), i.e. choosing \(a, b \in \{0, 1\}\) it sends \(|\psi'\rangle = X^a Z^b |\psi\rangle\), to get \(B\) to apply \(R\) on the state. \(B\) then sends back \(R|\psi'\rangle\) to \(A\). How can \(A\) recover the \(R|\psi\rangle\) from \(R|\psi'\rangle\)? As noted in Broadbent [2015], this is not so straightforward since we have:

\(R |\psi'\rangle = R X^a Z^b |\psi\rangle
= \begin{cases} R |\psi\rangle, & \text{if } a = 0, b = 0 \\ RZ |\psi\rangle = ZR |\psi\rangle, & \text{if } a = 0, b = 1 \\ RX |\psi\rangle = XZPR |\psi\rangle, & \text{if } a = 1, b = 0 \\ RXZ |\psi\rangle = XZPRZ |\psi\rangle = XZPZR |\psi\rangle \\ = XPZZR |\psi\rangle = XPR |\psi\rangle, & \text{if } a = 1, b = 1 \end{cases}\)

since \(RZ = ZR\), \(RX = XZPR\) (ignoring global phases), and \(ZP = PZ\), that is, \(R |\psi'\rangle = X^a Z^a Z^b P^a R |\psi\rangle\). This means that when \(a=0\), \(A\) can just apply \(Z^b\) to \(R |\psi'\rangle\) to obtain \(R |\psi\rangle\): \(Z^b (R |\psi'\rangle) = Z^b (Z^b R |\psi\rangle) = R |\psi\rangle\). But when \(a=1\), we have the additional \(P\) in front of the \(R\). One needs to apply \(ZP\) to \(XPR |\psi\rangle\) to remove the \(P\), e.g. when \(a=1, b=1\), one can apply \(ZPX\) to \(XPR |\psi\rangle\) to get \(ZPX(XPR |\psi\rangle) = ZPPR |\psi\rangle = ZZR |\psi\rangle = R |\psi\rangle\), since \(Z = PP\). However, recall that we have assumed that the client is limited and cannot perform \(P\) by itself (and so, it is using the more powerful \(B\) to do so!), and so cannot perform \(ZP\)