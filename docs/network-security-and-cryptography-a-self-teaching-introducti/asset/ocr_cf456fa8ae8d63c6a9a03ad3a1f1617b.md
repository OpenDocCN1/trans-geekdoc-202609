Let private key x = 3
Public Key y = g^x \mod p = 2^3 \mod 19 = 8

# 8.8.2.8 Signing of Message by the Sender

Let $m = H(M) = 5$
Let $k = 7$
$r = g^k \mod \Phi(p)$
$= 2^7 \mod 18 = 128 \mod 18 = 20$
$s = k^{-1} (m - rx) \mod \Phi(p)$
$= 7^{-1} (5 - 2 \times 3) \mod 18$
$= 13 \times -1 \mod 18 = 5$

So, $(M, r, s) = (5, 2, 5)$ is transmitted to the intended recipient.

# 8.8.2.9 Verification of Signature by the Intended Recipient

$v = g^m \mod \Phi(p)$
$= 2^5 \mod 18 = 14$
$w = (y^r \times r^s) \mod \Phi(p)$
$= (8^2 \times 2^5) \mod 18$
$= (64 \times 32) \mod 18$
$= (10 \times 14) \mod 18$
$= 14$
W = W = 14$;

Signature stands verified.

# 8.8.3 Digital Signature Algorithm and Technology (NIST)

The National Institute of Standards and Technology (NIST) has published a Federal Information Processing Standard (FIPS 186), known as the Digital Signature Standard (DSS). It makes use of the Secure Hash Algorithm (SHA) and incorporates a Digital Signature Algorithm (DSA). The DSA is based on the difficulty of computing Discrete Logarithms on the scheme originally presented by ElGamal. The DSS approach is an improvement of the original scheme proposed by ElGamal and Schnorr