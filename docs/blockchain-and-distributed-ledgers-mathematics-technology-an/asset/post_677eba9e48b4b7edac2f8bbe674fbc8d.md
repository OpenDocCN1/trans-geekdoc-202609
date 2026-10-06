
# Chapter 9 Wallets and Key Management | 275

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_321_0.png)

**Figure 9.7** Non-hardened child derivation with BIP32. Own graphics.

Continuing Pierre Wuille's specification, we assume the public cryptography used in Bitcoin below, namely the elliptic curve digital signature algorithm (ECDSA), described in Section 4.7, with curve secp256k1, but that the scheme may be extended to other curves and protocols. Variables below are either integers the order of the curve (referred to as n), coordinates of points on the curve, or byte sequences. Addition (+) of two coordinate pair is defined as application of the EC group operation; concatenation (|) is the operation of appending one sequence to another. As standard conversion functions, we define the following limits:

- (1) point(p): returns the coordinate pair resulting from elliptic curve point multiplication (repeated application of the EC group operation) of the secp256k1 base point with the integer p.
- (2) ser32(i): serializes a 32-bit unsigned integer i as a 4-byte sequence, most significant byte first.
- (3) ser256(p): serializes the integer p as a 32-byte sequence, most significant byte first.
- (4) serP(P): serializes the coordinate pair P = (x, y) as a byte sequence using SEC1's format: (0x02or0x3)|ser256(x), where the header depends on the parity of the omitted y coordinate.
- (5) ser256(p): interprets a 32-byte sequence as a 256-bit, most significant byte first.

In order to prevent the key derivation scheme to only depend on the parent key itself, BIP32 introduces the notion of extended secret (sk, c) and extended public key (pk, c), where sk is a secret key, pk is a public key, and c is an additional 256-bit of entropy encoded chain code. The child key derivation CKD_mod((k, c), i) -> (k', c') takes an extended key and generates a new, extended key with index i, where i is a 32-bit integer defining the derivation branch and the derivation mode. We set mode to h when hardened derivation is used, and to nh when non-hardened derivation is used. The hardened function, which computes a child-extended secret based on a parent-extended secret key and a derivation index, $i \rightarrow CKD_H(sk, c), i \rightarrow (sk_i, c_i)$ for $i = 2^{31}, \dots, 2^{32}-1$, such that:

- (1) Let $I = HMAC-SHA512(Key = c, Data = 0x00|ser256(sk)|ser32(i))$, where $0x00$ pads the secret key to make it 33 bytes.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

The derived public key is trivially computed through the elliptic multiplication with the base point, where $pk_i = point(sk_i)$.
Non-hardened derivation requires a pair of functions to compute, respectively, a child extended key from the parent public key and its corresponding child extended secret key from the parent extended secret key. We denote the functions as:

```
$$CKD_{nh}((pk, c), i) \rightarrow (pk_i, c_i)$$
$$CKD_{nh}((sk, c), i) \rightarrow (sk_i, c_i)$$
```

for $i = 0, \dots, 2^{31}-1$, $CKD_{nh}$ guarantees that $pk_i = point(sk_i)$. In other words, $CKD_{nh}(pk, c), i$ is able to derive a child extended public key $(pk_i, c_i)$ from a parent extended public key $(pk, c)$ with no knowledge of the parent secret key $sk$ — and it guarantees that there exists a function $CKD_{nh}(sk, c), i$ that computes the child extended secret key $(sk_i, c_i)$ given the parent extended secret key $(sk, c)$.
$CKD_{nh}(pk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(pk)|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is defined as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid, and one proceeds with the next value for $i$.

The corresponding function for secret key derivation $CKD_{nh}(sk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(point(pk))|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

# Chapter 9 Wallets and Key Management | 277

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_321_0.png)

# 9.4.3 Purpose, Coin Type, Change and Index

In order to prevent the key derivation scheme to only depend on the parent key itself, BIP32 introduces the notion of extended secret (sk, c) and extended public key (pk, c), where sk is a secret key, pk is a public key, and c is an additional 256-bit of entropy encoded chain code. The child key derivation CKD_mod((k, c), i) -> (k', c') takes an extended key and generates a new, extended key with index i, where i is a 32-bit integer defining the derivation branch and the derivation mode. We set mode to h when hardened derivation is used, and to nh when non-hardened derivation is used. The hardened function, which computes a child-extended secret based on a parent-extended secret key and a derivation index, $i \rightarrow CKD_H(sk, c), i \rightarrow (sk_i, c_i)$ for $i = 2^{31}, \dots, 2^{32}-1$, such that:

- (1) Let $I = HMAC-SHA512(Key = c, Data = 0x00|ser256(sk)|ser32(i))$, where $0x00$ pads the secret key to make it 33 bytes.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

The derived public key is trivially computed through the elliptic multiplication with the base point, where $pk_i = point(sk_i)$.
Non-hardened derivation requires a pair of functions to compute, respectively, a child extended key from the parent public key and its corresponding child extended secret key from the parent extended secret key. We denote the functions as:

```
$$CKD_{nh}((pk, c), i) \rightarrow (pk_i, c_i)$$
$$CKD_{nh}((sk, c), i) \rightarrow (sk_i, c_i)$$
```

for $i = 0, \dots, 2^{31}-1$, $CKD_{nh}$ guarantees that $pk_i = point(sk_i)$. In other words, $CKD_{nh}(pk, c), i$ is able to derive a child extended public key $(pk_i, c_i)$ from a parent extended public key $(pk, c)$ with no knowledge of the parent secret key $sk$ — and it guarantees that there exists a function $CKD_{nh}(sk, c), i$ that computes the child extended secret key $(sk_i, c_i)$ given the parent extended secret key $(sk, c)$.
$CKD_{nh}(pk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(pk)|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is defined as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid, and one proceeds with the next value for $i$.

The corresponding function for secret key derivation $CKD_{nh}(sk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(point(pk))|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

# Chapter 9 Wallets and Key Management | 277

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_321_0.png)

# 9.4.3 Purpose, Coin Type, Change and Index

In order to prevent the key derivation scheme to only depend on the parent key itself, BIP32 introduces the notion of extended secret (sk, c) and extended public key (pk, c), where sk is a secret key, pk is a public key, and c is an additional 256-bit of entropy encoded chain code. The child key derivation CKD_mod((k, c), i) -> (k', c') takes an extended key and generates a new, extended key with index i, where i is a 32-bit integer defining the derivation branch and the derivation mode. We set mode to h when hardened derivation is used, and to nh when non-hardened derivation is used. The hardened function, which computes a child-extended secret based on a parent-extended secret key and a derivation index, $i \rightarrow CKD_H(sk, c), i \rightarrow (sk_i, c_i)$ for $i = 2^{31}, \dots, 2^{32}-1$, such that:

- (1) Let $I = HMAC-SHA512(Key = c, Data = 0x00|ser256(sk)|ser32(i))$, where $0x00$ pads the secret key to make it 33 bytes.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

The derived public key is trivially computed through the elliptic multiplication with the base point, where $pk_i = point(sk_i)$.
Non-hardened derivation requires a pair of functions to compute, respectively, a child extended key from the parent public key and its corresponding child extended secret key from the parent extended secret key. We denote the functions as:

```
$$CKD_{nh}((pk, c), i) \rightarrow (pk_i, c_i)$$
$$CKD_{nh}((sk, c), i) \rightarrow (sk_i, c_i)$$
```

for $i = 0, \dots, 2^{31}-1$, $CKD_{nh}$ guarantees that $pk_i = point(sk_i)$. In other words, $CKD_{nh}(pk, c), i$ is able to derive a child extended public key $(pk_i, c_i)$ from a parent extended public key $(pk, c)$ with no knowledge of the parent secret key $sk$ — and it guarantees that there exists a function $CKD_{nh}(sk, c), i$ that computes the child extended secret key $(sk_i, c_i)$ given the parent extended secret key $(sk, c)$.
$CKD_{nh}(pk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(pk)|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is defined as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid, and one proceeds with the next value for $i$.

The corresponding function for secret key derivation $CKD_{nh}(sk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(point(pk))|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

# 278 | Blockchain and Distributed Ledgers: Mathematics, Technology, and Economics

Table 9.3 Allocated coin types.
| Index | Hexa | Coin |
|---|---|---|
| 0 | 0x80000000 | Bitcoin |
| 1 | 0x80000001 | Testnet |
| 2 | 0x80000002 | Litecoin |
| 3 | 0x80000003 | Dogecoin |
| 4 | 0x80000004 | Redcoin |
| 5 | 0x80000005 | Dash |
| 6 | 0x80000006 | Peercoin |
| 7 | 0x80000007 | Namecoin |

# 9.4.3 Purpose, Coin Type, Change and Index

In order to prevent the key derivation scheme to only depend on the parent key itself, BIP32 introduces the notion of extended secret (sk, c) and extended public key (pk, c), where sk is a secret key, pk is a public key, and c is an additional 256-bit of entropy encoded chain code. The child key derivation CKD_mod((k, c), i) -> (k', c') takes an extended key and generates a new, extended key with index i, where i is a 32-bit integer defining the derivation branch and the derivation mode. We set mode to h when hardened derivation is used, and to nh when non-hardened derivation is used. The hardened function, which computes a child-extended secret based on a parent-extended secret key and a derivation index, $i \rightarrow CKD_H(sk, c), i \rightarrow (sk_i, c_i)$ for $i = 2^{31}, \dots, 2^{32}-1$, such that:

- (1) Let $I = HMAC-SHA512(Key = c, Data = 0x00|ser256(sk)|ser32(i))$, where $0x00$ pads the secret key to make it 33 bytes.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

The derived public key is trivially computed through the elliptic multiplication with the base point, where $pk_i = point(sk_i)$.
Non-hardened derivation requires a pair of functions to compute, respectively, a child extended key from the parent public key and its corresponding child extended secret key from the parent extended secret key. We denote the functions as:

```
$$CKD_{nh}((pk, c), i) \rightarrow (pk_i, c_i)$$
$$CKD_{nh}((sk, c), i) \rightarrow (sk_i, c_i)$$
```

for $i = 0, \dots, 2^{31}-1$, $CKD_{nh}$ guarantees that $pk_i = point(sk_i)$. In other words, $CKD_{nh}(pk, c), i$ is able to derive a child extended public key $(pk_i, c_i)$ from a parent extended public key $(pk, c)$ with no knowledge of the parent secret key $sk$ — and it guarantees that there exists a function $CKD_{nh}(sk, c), i$ that computes the child extended secret key $(sk_i, c_i)$ given the parent extended secret key $(sk, c)$.
$CKD_{nh}(pk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(pk)|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is defined as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid, and one proceeds with the next value for $i$.

The corresponding function for secret key derivation $CKD_{nh}(sk, c), i$ is defined as follows:

- (1) Let $I = HMAC-SHA512(Key = c, Data = serP(point(pk))|ser32(i))$.
- (2) Split $I$ into two 32-byte sequences, $I_L$ and $I_R$.
- (3) The returned secret key is set as $sk_i = parse256(I_L) + sk(modn)$.
- (4) The returned chain code is set as $c_i = I_R$.
- (5) In the improbable case $parse256(I_i) \geq n$ or $k_i = 0$, the resulting key is invalid and one proceeds with the next value for $i$.

# 9.4.5 Extensions to BIP32

Although BIP44 already supports the many cryptocurrencies with ECDSA on curve secp256k1, we note that some cryptocurrencies have opted for alternative digital signature algorithms. Table 9.4 illustrates the digital signature algorithms and curves used by some of the main cryptocurrencies in terms of market capitalization. It is apparent that for IOTA, which relies on custom cryptography, two additional elliptic curves have gained relevance in the cryptocurrency market, respectively secp256r1 and ed25519; see Bernstein et al. (2012). Consequently, there exist multiple extensions to BIP32 and BIP44 aiming to provide a unique hierarchical key derivation framework supporting multiple curves. We refer to SLIP-0010² and Khovratovich and Law (2017) as two possible extensions.

²Universal secret key derivation from the master key, by Jochen Hoenenicke and Pavel Rusnak.
