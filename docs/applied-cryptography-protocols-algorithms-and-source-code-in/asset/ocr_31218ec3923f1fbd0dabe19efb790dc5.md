![](bbox=[0.175, 0.11, 0.602, 0.223])

Figure 18.10 Modified Davies-Meyer

# Preneel-Bosselaers-Govaerts-Vandewalle

This hash function, first proposed in [1266], produces a hash value twice the block length of the encryption algorithm: A 64-bit algorithm produces a 128-bit hash. With a 64-bit block algorithm, the scheme produces two 64-bit hash values, $G_i$ and $H_i$ which are concatenated to produce the 128-bit hash. Two adjacent message blocks, $L_i$ and $R_i$, each the size of the block is 64 bits. are hashed together.

```
$G_0 = I_0, \text{ where } I_0$ is a random initial value
$H_0 = I_H, \text{ where } I_H$ is another random initial value
$G_i = E_{L_i}(H_{i-1}) \oplus R_i \oplus G_{i-1} \oplus H_{i-1}$
$H_i = E_{R_i}(H_{i-1}) \oplus L_i \oplus G_{i-1} \oplus H_{i-1}$
```

Lai demonstrates attacks against this scheme. In some instances, the birthday attack trivially solvable [925, 926]. Preneel [1262] and Coppersmith [372] also have successful attacks against this scheme. Do not use it.

# Quisqu-Girault

This scheme, first proposed in [1279], generates a hash that is the block length and has a hash of 1. It has two hash values, $G_i$ and $H_i$, and two blocks, $L_i$ and $R_i$, which are hashed together.

```
$G_0 = I_0, \text{ where } I_0$ is a random initial value
$H_0 = I_H, \text{ where } I_H$ is another random initial value
$W_i = E_{L_i}(G_{i-1}) \oplus R_i \oplus H_{i-1}$
$G_i = E_{R_i}(W_{i-1}) \oplus G_{i-1} \oplus H_{i-1} \oplus L_i$
$H_i = W_i \oplus G_{i-1}$
```

This scheme appeared in 1989 draft standard [764], but was dropped in a later version [765]. Security problems with this scheme were identified in [1107, 925, 1262, 373]. [Actually, the version in the proceedings were strengthened after the version presented at the conference was attacked.] In some instances the birthday attack is solvable with a complexity of $2^{64}$, through brute force. Do not use this scheme.