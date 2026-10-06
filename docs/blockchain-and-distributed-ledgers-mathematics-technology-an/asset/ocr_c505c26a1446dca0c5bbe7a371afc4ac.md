Let a message be $m = 66$. Choose random $l = 83$. It is easy to check that:

$l^{-1} = 101,
B = l \times G = (122, 3),
s = (m + kr) l^{-1} = 79 \pmod{127},
s^{-1} = 82,
ms^{-1} = 78 \pmod{127},
P_1 = ms^{-1} \times G = (85, 77),
rs^{-1} = 98 \pmod{127},
P_2 = rs^{-1} \times A = (18, 88),
P_3 = P_1 + P_2 = (122, 3) = B.$

Since $P_{3,x} = B_x$, the signature is valid.

# 4.7.10 Elliptic Schnorr digital signature algorithm

EC Schnorr DSA has some convenient properties and can potentially replace the ECDSA for the Bitcoin blockchain protocol.

Visualization of the EC Schnorr DSA is presented in Figure 4.16.

![](bbox=[0.145, 0.517, 0.854, 0.898])

**Figure 4.16** Visualization of the EC-Schnorr DSA. Own graphics.