Let public key $e = 13$

Private Key $d \equiv e^{-1} \mod \Phi(n) = 13^{-1} \mod 60 = 37$

# 8.8.1.3.1 Signing

Let $m = H(M) = 2$

$Sign = m^d \mod n = 2^{37} \mod 77 = 51$

$2^{10} \mod 77 = 1024 \mod 77 = 23$

$2^{30} \mod 77 = (23)^3 \mod 77 = (67 \times 23) \mod 77$

$= (-10 \times 23) \mod 77 = 1$

$2^{37} \mod 77 = (1 \times 128) \mod 77 = 51$

# 8.8.1.3.2 Signature Verification at the Recipient End

$(Sign) \mod 77 = (51)^{13} \mod 77 = 2 = m$

$(51)^2 \mod 77 = (2601) \mod 77 = 60$

$(51)^4 \mod 77 = (60)^2 \mod 77 = (-17)^2 \mod 77 = 58$

$(51)^3 \mod 77 = (58)^2 \mod 77 = (-19)^2 \mod 77$

$= 361 \mod 77 = 53$

$(51)^{13} \mod 77 = (53 \times 58 \times 51) \mod 77$

$= (-24 \times -19 \times -26) \mod 77$

$= (624 \times -19) \mod 77$

$= (8 \times -19) \mod 77$

$= -152 \mod 77 = 2$

Since $(Sign) \mod 77 = m = H(M)$; the signature is verified.

# 8.8.2 ElGamal's Digital Signature Scheme

Figure 8.18 illustrates ElGamal's Digital Signature Scheme.