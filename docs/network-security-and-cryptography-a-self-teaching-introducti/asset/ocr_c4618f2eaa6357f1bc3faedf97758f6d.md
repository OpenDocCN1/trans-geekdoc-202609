# MODERN SYMMETRIC CIPHERS · 255

![](bbox=[0.265, 0.125, 0.775, 0.335])

**FIGURE 6.17** Electronic Code Book (CBC) Mode encryption.

For the encryption algorithm, we do the following:
For $i=1$ to $n$ do
$C_i = E_K(P_i \oplus C_{i-1})$ with $C_0 = IV$
$IV$ is initial vector ($C_0$)
$P_i$ is plaintext block $i$
$K$ is secret key
$C_i$ is cipher-text block $i$

# **Decryption of CBC**

On decryption, the initial vector (IV) is XOR with the output of the decryption algorithm to recover the first block of plaintext. Each cipher block in decryption is passed through the decryption algorithm. The result is XOR with the proceeding cipher-text block to produce the plaintext block in the following:
For $i=1$ to $n$ do

```
Plaintext = D_K(C_i) \oplus C_{i-1} with $C_0 = IV$
$=D_K(E_K(P_i \oplus C_{i-1})) \oplus C_{i-1}$
$=P_i \oplus C_{i-1} \oplus C_{i-1}$
$=P_i$
```