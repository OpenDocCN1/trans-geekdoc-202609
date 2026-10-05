# CHAPTER 23 Special Algorithms for Protocols

$x_0 = x^2 \pmod n$

Use $x_0$ as the seed of the BBS pseudo-random generator and use the output of the generator as a stream cipher. $XOR M$, one bit at a time, with the output of the generator. The generator spits out bits $b_i$ (the least-significant bit of $x_i$, where $x_i = x_{i-1}^2 \pmod n$), so

```
$M_1, M_2, M_3, \dots, M_i,\nC = M_1 \oplus b_1, M_2 \oplus b_2, M_3 \oplus b_3, \dots, M_i \oplus b_i$
```

Append the computed value, $x_i$, to the end of the message and you're done.
The only way to decrypt this message is to recover $x_0$ and then set up the BBS generator to XOR with the ciphertext. Because the BBS generator is secure to the value, $x_i$ is of no use to the cryptanalyst. Only who knows $p$ and $q$ can decrypt the message.

In C, the algorithm to recover $x_0$ from $x_i$, is:

```
int xo(int p, int q, int n, int t, int xt)

int a, b, u, w, z;

/* we already know that gcd(p, q) == 1 */
(void)extended_euclidian(p, q, &a, &b);
u = modexp((p)/4, t, p-1);
v = modexp((q)/4, t, q-1);
w = modexp(xtp, u, p);
z = modexp(xtq, v, q);
return (h*w + a*p) % n;
```

Once you have $x_0$, decryption is easy. Just set up the BBS generator and XOR out the ciphertext.
You can make this scheme even faster by using all the known bits of $x_i$, not just the least significant bits. With this improvement, Blum-Goldwasser probabilistic encryption is faster than RSA while leaving no partial information about the plaintext. You can also prove that the difficulty of breaking this scheme is the same as the difficulty of factoring $n$.

On the other hand, this scheme is totally insecure against a chosen-ciphertext attack. From the least significant bits of the right quadratic residues, it is possible to calculate the square root of any quadratic residue. If you can do this, then you can factor. For details, consult [1570,157,1.35,36].

# 23.16 QUANTUM CRYPTOGRAPHY

Quantum cryptography taps the natural uncertainty of the quantum world. With it, you can create a communications channel where it is impossible to eavesdrop without disturbing the transmission. The laws of physics ensure this quantum channel: even if the eavesdropper can do whatever he wants, even if the eavesdropper has