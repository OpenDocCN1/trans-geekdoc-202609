Thus, the proof.

**Example 8.2:** (ElGamal Signature Scheme)
Let $p = 11$ and $g = 2$ be global parameters.

# 8.8.2.5 Determination of Keys

The signer determines its keys as follows:
Let $x = 3$ and $(x, g, p) = (3, 2, 11)$ be the private key of the signer
$y = g^x \pmod{p} = 2^3 \pmod{11} = 8$
.: Public key of the signer = $\langle y, g, p angle = (8, 2, 11)$

# 8.8.2.6 Signing of the Message

Let $m = H(M) = 5$
Suppose the signer chooses $k = 3$ (which is relatively prime to $\Phi(p) = 10)$)
Then $r = g^k \pmod{p}$
$r = 2^3 \pmod{10} = 8$
$s = (k^{-1}(m - rx)) \pmod{\Phi(p)}$n$s = (3^{-1}(5 - 8 	imes 3)) \pmod{10}$
$s = (7 	imes (-19)) \pmod{10}$
$s = (7 	imes 1) \pmod{10} = 7$
.: Digital Signature = $(r, s) = (8, 7)$

# 8.8.2.7 Signature Verification

$w = g^m \pmod{\Phi(p)} = 2^5 \pmod{10} = 2$
$w = (y^s 	imes r) \pmod{\Phi(p)} = (8^7 	imes 8) \pmod{10} = (8^8) \pmod{10}$
$w = (512)^5 \pmod{10} = (2)^5 \pmod{10} = (32) \pmod{10} = 2$
.: $v = w = 2$
.: The Digital Signature stands verified.

**Example 8.3:** (ElGamal Signature Scheme)
Let $p = 19, g = 2$