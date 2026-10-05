SECURITY OF EMERGING TECHNOLOGY * 507

+   - Parameter b will be calculated. Just multiply private key in the initial message which has been sent by the sender:

```
$a = b \cdot f \cdot message \quad (14.7)$
```

```
$Decryption = \frac{(f_p \times b)}{x^2} \quad (14.8)$
```

+   - Whenever Decryption = Message, we will be sure that the message will reach security to the recipient without any disorder.

# D. Digital signature

+   - Digital signature is used for message validity and proof of identity and security.

+   - We must go from the sender to the receiver, so the receiver of the former step acts as the sender now and the sender of the former step acts as the receiver.

```
$Encryption sign = \frac{(message \times f)}{x^2} \quad (14.9)$
```

```
$Decryption = \left( \frac{h}{2} \times f_p \ Encryption sign \right) \times h \quad (14.10)$
```

# 14.4.10 Hybrid Encryption Algorithm Based on DES and DSA:

+   - Regroup 64-bit data according to blocks and put the output $L_o, R_o$ two parts, each of 32 bits, and its replacement rule is to exchange the $58^{th}$ bit with the second, $\dots$, and so on; and the last is one the original No. 7.

+   - $L_o$ and $R_o$ are the two parts after the transposition output; $L_o$ is the left 32 bits of the output, and $R_o$ is the right 32 bits.

+   - Sub-key generation algorithm: The $8^{th}, 16^{th} \dots 64^{th}$ bit is a parity bit according to the DES algorithm, and is not involved in the DES output. The key actual uses 56 bits; this 56 is Divided into two parts $C_o$ and $D_o$ each of 28 bits, and cycle left for the first time, to obtain $C_i$ and $D_i$ then the $C_i$ (28 bits), $D_i$ (28 bits) obtained are combined to form