# 15.2 Triple Encryption

again. He suggested that the sender encrypts with the first key, decrypts with
the second key, and finally encrypts with the first key. The receiver decrypts with the
first key, then decrypts with the second key, and finally decrypts with the first key.

```
$C = E_{K_1}(D_{K_2}(E_{K_3}(|P|)))\n$P = D_{K_1}(E_{K_2}(D_{K_3}(C)))$
```

This is sometimes called **encrypt-decrypt-encrypt** (EDE) mode [55]. If the block
alalgorithm has an n-bit key, then this scheme is a 2n-1 key. The curious encrypt-
decrypt pattern was designed by IBM to preserve compatibility with-
conventional implementations of the algorithm: Setting the two keys to each
other is identical to encrypting with once key. There is no security inherent in
the encrypt-decrypt pattern, but this mode has been adopted to improve the
DES algorithm in the X.17 and ISO 8732 standards [55, 761].

Triple encryption with two keys is not susceptible to the meet-in-the-middle
attack described earlier. But Merkle and Hellman developed another time-\memory trade-off that could break this technique in $2^{n-1}$ steps using $2^n$ blocks of
memory [1075].

For each possible $K_2$, decrypt 0 and store in memory. Then, decrypt 0
with possible $K_1$ to get $P$. Triple-encrypt $P$ to get $C$, and then decrypt $C$ with $K_1$.
If that decryption of 0 with $K_3$ (stored in memory), the $K_1$ $K_2$ pair is
ana possible candidate. Check if it is right. If it is, not keep looking.

This is a chosen-plaintext attack, requiring an enormous amount of chosen-plaintext to mount. It requires $2^n$ time and memory, and $2^n$ chosen plaintexts. It is not
very practical, but it is a weakness.

Paul van Oorsch and Michael Wiener converted this to a known-plaintext
attack. This example assumes EDE mode.

+   (1) Guess the first intermediate value, a.
(2) Tabulate, for each possible $K_1$, the second intermediate value, $b$, when
first intermediate value is $a$, using known plaintext:

```
 

\n(3) Look up in the table, for each possible $K_2$, elements with a matching-\nintermediate value, $b$:\n$b = E_{K_3}(a)\n(4) The probability of success is $p/m$, where $p$ is the number of known plaintexts
m $m$ is the block size. If there is no match, then another $a$ and start again.
```

The attack requires $2^n * m/p$ time and $p$ memory. For DES, this is $2^{120}/p$ [1558]. For
pp$ greater than 256, this attack is faster than exhaustive search.