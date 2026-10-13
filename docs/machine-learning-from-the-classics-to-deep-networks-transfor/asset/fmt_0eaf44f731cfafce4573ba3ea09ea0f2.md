
# Graphical Models for Error Correcting Codes

Graphical models are extensively used for representing a class of error correcting codes. In the **block parity-check** codes (e.g., [31]), one sends *k* information bits (0, 1 for a binary code) in a block of *N* bits, *N* > *k*; thus, redundancy is introduced into the system to cope with the effects of noise in the transmission channel. The extra bits are known as parity-check bits.

For each code, a parity-check matrix, *H*, is defined; in order to be a valid one, for each code word, **x**, it must satisfy the parity-check constraint (modulo-2 operations), *H***x** = **0**.

Take as an example the case of *k* = 3 and *N* = 6. The code comprises 2³ (2^(*k*) in general) code words, each of them of length *N* = 6 bits.

For the parity-check matrix,

```
H = \begin{bmatrix}
{1\ } & {1\ } & {0\ } & {1\ } & {0\ } & 0 \\
{1\ } & {0\ } & {1\ } & {0\ } & {1\ } & 0 \\
{0\ } & {1\ } & {1\ } & {0\ } & {0\ } & 1 \\
\end{bmatrix},
```

the eight code words that satisfy the parity-check constraint are 000000, 001011, 010101, 011110, 100110, 101101, 110011, and 111000. In each one of the eight words, the first three bits are the information bits and the remaining ones the parity-check bits, which are uniquely determined in order to satisfy the parity-check constraint.

Each one of the three parity-check constraints can be expressed via a function, that is,

```
ψ₁(x₁, x₂, x₄) = δ(x₁ ⊕ x₂ ⊕ x₄),
ψ₂(x₁, x₃, x₅) = δ(x₁ ⊕ x₃ ⊕ x₅),
ψ₃(x₂, x₃, x₆) = δ(x₂ ⊕ x₃ ⊕ x₆).
```
