# Chapter 9 Wallets and Key Management | 275

![](bbox=[0.218, 0.098, 0.781, 0.358])

**Figure 9.7** Non-hardened child derivation with BIP32. Own graphics.

Continuing Pierre Wuille's specification, we assume the public cryptography used in Bitcoin below, namely the elliptic curve digital signature algorithm (ECDSA), described in Section 4.7, with curve secp256k1, but that the scheme may be extended to other curves and protocols. Variables below are either integers the order of the curve (referred to as n), coordinates of points on the curve, or byte sequences. Addition (+) of two coordinate pair is defined as application of the EC group operation; concatenation (|) is the operation of appending one sequence to another. As standard conversion functions, we define the following limits:

+   (1) point(p): returns the coordinate pair resulting from elliptic curve point multiplication (repeated application of the EC group operation) of the secp256k1 base point with the integer p.
(2) ser32(i): serializes a 32-bit unsigned integer i as a 4-byte sequence, most significant byte first.
(3) ser256(p): serializes the integer p as a 32-byte sequence, most significant byte first.
(4) serP(P): serializes the coordinate pair P = (x, y) as a byte sequence using SEC1's format: (0x02or0x3)|ser256(x), where the header depends on the parity of the omitted y coordinate.
(5) ser256(p): interprets a 32-byte sequence as a 256-bit, most significant byte first.

In order to prevent the key derivation scheme to only depend on the parent key itself, BIP32 introduces the notion of extended secret (sk, c) and extended public key (pk, c), where sk is a secret key, pk is a public key, and c is an additional 256-bit of entropy encoded chain code. The child key derivation CKD_mod((k, c), i) -> (k', c') takes an extended key and generates a new, extended key with index i, where i is a 32-bit integer defining the derivation branch and the derivation mode. We set mode to h when hardened derivation is used, and to nh when non-hardened derivation is used. The hardened function, which computes a child-extended secret based on a parent-extended secret