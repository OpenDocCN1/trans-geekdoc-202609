# CHAPTER 16 Pseudo-Random-Sequence Generators

$B_i = [B_i - 57 + B_i - 7] \mod 2^{32}$
$C_i = [C_i - 58 + C_i - 19] \mod 2^{32}$

To generate the keystream word, look at the addition bits. If all three agree
(all are 0 or all are 1), then clock all three generators. If they do not, just clock the
two generators that agree. Save the carry bits for next time. The final output is
the XOR of the three generators.

Pike is from Fish, on the average 2.75 steps is required per per output
r than 3. It is far too new to trust, but looks good so far.

# Mush

$A_i = [A_i - 55 + A_i - 24] \mod 2^{32}$
$B_i = [B_i - 52 + B_i - 19] \mod 2^{32}$

On the average, three iterations are required to produce one output
word. And if the coefficients of the additive generators are chosen correctly and are
relatively prime, the output sequence will be maximal length. I know of no suc-
cessful attacks, remember that this algorithm is very new.

# 16.10 GIFFORD

David Gifford invented a stream cipher and used it to encrypt news reports in
the Boston area from 1984 until 1988 [608,607,609]. The algorithm has a single
8-byte register: $b_0, b_1, \dots, b_7$. The key is the initial state of the register. The algorithm
works in OFB, the plaintext does not affect the algorithm at all. [See Figure 16.17].

To generate a key $k_i$, concatenate $b_0$ and $b_1$ and concatenate $b_5$ and $b_7$. Multi-
ply the two together to get a 32-bit number.
To update the register, take $b_i$ and sticky right shift it 1. This means the left-
most is both shifted and remains in place. Take $b_7$ and shift it 1 to the
left, there should be a 0 in the right-most position. Take the XOR of the modified
$b_1$, and $b_0$. Shift the original register 1 to the right and put this
byte in the left-most position.

This algorithm remained secure throughout its life, but was broken in 1994 [287].
 turns out that the feedback polynomial is not primitive and can be attacked that
way—oops.