![](bbox=[0.153, 0.148, 0.458, 0.593])

Blowfish is Feistel network [see Section 14.10] consisting of 16 rounds. The input is a 64-bit data element, x. To encrypt:

Divide x into two 32-bit halves: $x_L, x_R$
For $i = 1$ to 16:
$x_L = x_L \oplus P_i$
$x_R = F[x_L] \oplus x_R$
Swap $x_L$ and $x_R$
Swap $x_L$ and $x_R$ [Undo the last swap].
$x_R = x_R \oplus P_{17}$
$x_L = x_L \oplus P_{18}$

Recombine $x_L$ and $x_R$