= Z^{a \cdot y} Z^{y \cdot d} Z^{p \cdot a} X^{c \cdot a} Z^{a \cdot b} Z^{p \cdot b} P^{a \cdot R} | \psi \rangle
(since P^y P^y = Z^y, P^a Z^{y} = Z^{y'} P^a, \text{ and } P^a Z^d = Z^d P^a)
= Z^{a \cdot y \oplus y \oplus d} P^a X^{a \oplus c} Z^{a \oplus b} P^{a \cdot R} | \psi \rangle
\equiv Z^{a \cdot y \oplus y \oplus d} Z^{a - (a \oplus c)} X^{a \oplus c} P^a Z^{a \oplus b} P^{a \cdot R} | \psi \rangle
(since P^a X^{0 \oplus c} \equiv Z^{a \cdot (a \oplus c)} X^{a \oplus c} P^a \text{ by ignoring the global phase})
= Z^{a \cdot y \oplus y \oplus d} Z^{a - (a \oplus c)} X^{a \oplus c} P^a Z^{a \oplus b} P^{a \cdot R} | \psi \rangle
(since Z^{a \oplus b} P^a = P^a Z^{a \oplus b})
= Z^{a \cdot y \oplus y \oplus d} Z^{a - (a \oplus c)} X^{a \oplus c} Z^a Z^{a \oplus b} R | \psi \rangle
(since P^a P^a = P^{2a} = Z^a)
= X^{a \oplus c} Z^{a \cdot y \oplus y \oplus d} Z^{a - (a \oplus c)} Z^a Z^{a \oplus b} R | \psi \rangle
(since Z^{a \cdot (a \oplus c)} X^{a \oplus c} = -X^{a \oplus c} Z^{a \cdot (a \oplus c)} \text{ and } Z^{a \cdot y} \oplus y \oplus d X^{a \oplus c} = -X^{a \oplus c} Z^{a \cdot y \oplus y \oplus d})
= X^{a \oplus c} Z^{a - (c \oplus b) \oplus 1) \oplus b \oplus b \oplus d \oplus y} R | \psi \rangle

In Figure 5.1, if B sends \(|\psi''\rangle\) to A, note that A has \(a, b, y, d\), and \(c\) (also from B), and so, can obtain \(R |\psi\rangle\) from \(|\psi''\rangle\) as follows:

\(Z^{a \cdot (c \oplus 1) \oplus b \cdot d \oplus b \cdot d} Y X^{a \oplus c} |\psi''\rangle = R |\psi\rangle\)

We have seen how the client A can ask the server to perform quantum operations and decrypt the result from the server B. Table 5.1 summarizes the client's encrypted states and what is sent to the server, the operation performed on the server and computed state on the server (with the equivalent operation showing the corresponding encryption keys); in short, the idea is

\(| \psi \rangle \xrightarrow{enc_{a,b}} | \psi \rangle \xrightarrow{U} U(enc_{a,b}(| \psi \rangle)) = enc_{a',b'}(U | \psi \rangle) \xrightarrow{dec_{a',b'}} U | \psi \rangle\)

where we have \(enc\) using the quantum one-time pad, i.e. for randomly and uniformly chosen \(a, b \in \{0, 1\}\), \(enc_{a,b}(|\psi\rangle) = X^a Z^b |\psi\rangle\), and \(dec_{a',b'} = Z^{b'} X^{a'}\). A core idea for this to work is to have the equivalence: \(U (enc_{a,b}(|\psi\rangle)) = enc_{a',b'}(U |\psi\rangle) = X^{a'} Z^{b'} (U |\psi\rangle)\), with suitable values for \(a'\) and \(b'\), so that \(dec_{a',b'}(enc_{a',b'}(U |\psi\rangle)) = Z^{b'} X^{a'} (enc_{a',b'}(U |\psi\rangle)) = Z^{b'} X^{a'} X^{a'} Z^{b'} (U |\psi\rangle) = U |\psi\rangle\).

But in general, a quantum circuit would use more than just one gate. A general quantum circuit can be decomposed into a sequence of gates, where the gates are from the set \(\{X, Z, H, P, CNOT, R\}\), and hence, the reason for showing how each of these gates can be delegated to the server.

Assuming that qubits are prepared and held in a quantum register, the following protocol is used to delegate computations to a server: