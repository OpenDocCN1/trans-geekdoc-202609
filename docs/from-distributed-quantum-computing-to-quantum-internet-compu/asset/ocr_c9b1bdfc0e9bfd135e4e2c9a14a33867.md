First, we observe that for each i:

$s_i^A \oplus s_i^B \oplus s_i^C = x_i^A \cdot x_i^B \cdot x_i^C$

This is because since $x^A \oplus x^B \oplus x^C = \mathbf{1}$, i.e. $x_i^A \oplus x_i^B \oplus x_i^C = 1$, there are only four possible combinations of values for $x_i^A, x_i^B, x_i^C$, which are 0, 0, 1 or 0, 1, 0 or 1, 0, 0 or 1, 1, 1 (only odd number of ones), and we can see from the following table, that, for each $i$, for each possible value of $x_i^A, x_i^B, x_i^C$, we have that $s_i^A \oplus s_i^B \oplus s_i^C = x_i^A \cdot x_i^B \cdot x_i^C$.

| $x_i^A \cdot x_i^B \cdot x_i^C$ | State after line 5 in the algorithm | $s_i^A \oplus s_i^B \oplus s_i^C$ |
|---|---|---|
| $0 \cdot 0 \cdot 1 = 0$ | $H \otimes H \otimes I(\rho_{ABC}) = \frac{1}{2}(|011\rangle + |101\rangle + |000\rangle - |110\rangle)$ | 0 |
| $0 \cdot 1 \cdot 0 = 0$ | $H \otimes I \otimes H(\rho_{ABC}) = \frac{1}{2}(|011\rangle + |110\rangle + |000\rangle - |101\rangle)$ | 0 |
| $1 \cdot 0 \cdot 0 = 0$ | $I \otimes H \otimes H(\rho_{ABC}) = \frac{1}{2}(|101\rangle + |110\rangle + |000\rangle - |011\rangle)$ | 0 |
| $1 \cdot 1 \cdot 1 = 1$ | $I \otimes I \otimes I(\rho_{ABC}) = \frac{1}{2}(|001\rangle + |010\rangle + |100\rangle - |111\rangle)$ | 1 |

Note that, for each $i$, the state of the triple of qubits after selectively applying the Hadamard gates (middle column in the table) depends on which of the four combinations of values for $x_i^A, x_i^B, x_i^C$ are present.

Following from above, we have:

$s^A \oplus s^B \oplus s^C = (s_1^A \oplus \cdots \oplus s_n^A) \oplus (s_1^B \oplus \cdots \oplus s_n^B) \oplus (s_1^C \oplus \cdots \oplus s_n^C)$
$= (s_1^A \oplus s_1^B \oplus s_1^C) \oplus \cdots \oplus (s_n^A \oplus s_n^B \oplus s_n^C)$
$= (x_1^A \cdot x_1^B \cdot x_1^C) \oplus \cdots \oplus (x_n^A \cdot x_n^B \cdot x_n^C)$
$= f(x^A, x^B, x^C)$

which is the value computed by $A$. As explained in Cleve and Buhrman [1997], without shared entangled bits, two classical bits of communication among $A$, $B$, and $C$ are insufficient for $A$ to compute $f(a,b,c)$, and three classical bits are required to be communicated. In an interesting way, the shared qubits seem to be “taking the place” of one classical bit of communication: $n$ entangled triples of qubits plus two classical bits of communication is equivalent to three classical bits of communication, for this problem!

# 3.1.1.2 The Distributed Deutsch–Jozsa Promise Problem

Let us consider another problem based on the one in Buhrman et al. [2010], related to another problem (and its solution/algorithm) called the Deutsch–Jozsa algorithm,$^1$ as follows. Suppose we have $A$ and $B$, and $A$ has an $n$-bit string $a = a_1 \dots a_n$

1 Note that the original Deutsch–Jozsa problem is to determine if a given function (say $f : \{0, 1\}^n \mapsto \{0, 1\}$) is constant (returns 0 on all its inputs or 1 on all its inputs) or balanced (returns 0 on half its inputs and 1 on the other half of its inputs) - and we are promised that the function is either one or the other. A solution is at https://en.wikipedia.org/wiki/Deutsch-Jozsa_algorithm.