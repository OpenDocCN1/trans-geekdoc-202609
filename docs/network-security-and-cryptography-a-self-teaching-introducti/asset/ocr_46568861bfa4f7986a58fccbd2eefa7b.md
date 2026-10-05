PUBLIC-KEY CRYPTOGRAPHY FOR DATA CONFIDENTIALITY * 305

The scheme can be better explained by the following schematic in Figure 7.2.

# User "A"

# User "B"

Chooses Random integer $X_a$
1 $< X_a < \Phi(p)$

A

Computes $Y_a = g^{X_a} \bmod p$
and Transmits $Y_a$ to 'B'
(but it is intercepted by 'C')

Adversary "C"

Receives $Y_a$ from 'C' as if
it is received from 'A'

Receives $Y_a$ from 'C' as if
it is received from 'B'

Chooses Random integer $X_b$
1 $< X_b < \Phi(p)$

Intercepts $Y_a$ from "A"

Computes Secret Key
$K_{ab} = Y_a^{X_b} \bmod p$

Chooses Random integer $X_c$
1 $< X_c < \Phi(p)$

Computes $Y_b = g^{X_b} \bmod p$
and Transmits $Y_b$ to "A"
(but it is intercepted by "C")

Sends message $M$ to "A" by
encrypting it with $K_{ab} = E_{K_{ab}}[M]$
(but cipher-text $C_a$ is
intercepted by 'C')

Computes Key $K_{bc}$ for sharing
with 'C': $K_{bc} = Y_b^{X_c} \bmod p$

Intercepts $Y_b$ from "C"
Computes Key $K_{bc}$ for sharing
with 'B': $K_{bc} = Y_b^{X_c} \bmod p$

Computes Secret Key
$K_{ba} = Y_b^{X_a} \bmod p$

Receives $C_a$ from 'C' as if
it is received from 'B'

Intercepts Cipher-text $C_a$

Decrypts $C_a$ using key $K_{ab}$
MM = D_{K_{ab}}[C_a] = E_{K_{ab}}[M]$

Decrypts $C_b$ using key $K_{ba}$
M' = D_{K_{ba}}[C_b] = E_{K_{ba}}[M]$

Modifies $M$ to $M'$, encrypts it
using $K_{bc}$ and sends it to "B"
$C_b = E_{K_{bc}}[M]$

"B" wrongly considers as if
message has been received
from "A"

7.2 A schematic diagram of the Man-in-the-Middle-Attack.

# 7.6 ELGAMAL ENCRYPTION SCHEME

ElGamal Encryption Scheme depends on its effectiveness on the
diculty of computing discrete logarithms. It is a Public-Key Encryption
Scheme, where each user has a Public Key, which is distributed to all
Users, and a Private Key, which is kept secret.

![](bbox=[0.175, 0.093, 0.825, 0.733])