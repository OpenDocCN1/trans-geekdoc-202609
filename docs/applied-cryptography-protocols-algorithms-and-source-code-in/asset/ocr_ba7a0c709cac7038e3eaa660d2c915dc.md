# CHAPTER 13 Other Block Ciphers

$x_i = x_i \oplus k_i$, for $i = 0$ to $3$
$f(x_0,x_1,x_2,x_3)$

$x_i = x_i \oplus k_{i+1}$, for $i = 0$ to $3$
$f(x_0,x_1,x_2,x_3)$

$x_i = x_i \oplus k_{i+2}$, for $i = 0$ to $3$
$f(x_0,x_1,x_2,x_3)$

$x_i = x_i \oplus k_i$, for $i = 0$ to $3$
$f(x_0,x_1,x_2,x_3)$

$x_i = x_i \oplus k_{i+1}$, for $i = 0$ to $3$
$f(x_0,x_1,x_2,x_3)$

$x_i = x_i \oplus k_{i+2}$, for $i = 0$ to $3$
$f(x_0,x_1,x_2,x_3)$

The function $f$ has three steps:

+   (1) $x_i = x_i \cdot x_i$, for $i = 0$ to $3$ (If the multiplication is all 1s, the output is also all 1s).
(2) If the least significant bit of $x_0$ is 1, then $x_0 = x_0 \oplus C$. If the least significant byte of $x_3$ is 0, then $x_3 = x_3 \oplus C$.
(3) $x_i = x_{i-1} \oplus x_i \oplus x_{i+1}$, for $i = 0$ to $3$

All index operations are 4. The multiplication operation in step [1] is $2^{32}-1$. For purposes of the algorithm, if the second operand is $2^{32}-1$, then the result is $2^{32}-1$. The various constants are:

$C = 2aaaaaa$
$c_0 = 025fcdb$
$c_1 = 2 \cdot c_0$
$c_2 = 2^3 \cdot c_0$
$c_3 = 2^7 \cdot c_0$

The constant $C$ is the "simplest" constant with a high ternary weight, a least-significant bit of zero, and no symmetry. The constant $c_0$ has certain other characteristics. The constants $c_0, c_1, c_2$ and $c_3$ are shifted versions of $c_0$, preventing attacks based on symmetry. See [405] for more details.

Decryption is the reverse process. Steps [2] and [3] are their own inverse. Step [1] uses $c^{-1}$ instead of $c_0$. The value of $c_0^{-1}$ is 0odad4694.

# Security of MMB

The design of MMB ensures that each round has considerable diffusion independent of the key. In IDEA, the amount of diffusion is to some extent dependent on the particular subkeys. MMB was also designed not to have weak keys as IDEA.