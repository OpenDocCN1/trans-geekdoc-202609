# Exercises 2.2

2.2.1. *Follow through all stages of block coding for the input string 00101110 when transmission errors occur in coordinates 3, 7, 14.*

# 2.3 The effect of coding

on the error probability of decoding.

Let us compare the error probabilities with and without coding in a special case, based on the BSC (Section 1.5). The bit error probability is a (small) number $p$. Use block coding with blocks of length $k = 4$. We want to compute (or bound) the probability $P$ that a given 4-tuple is **not** received correctly after coding and decoding.

Without coding ($n = k = 4$) the probability of correct transmission is $(1 - p)^4 = 1 - 4p + 6p^2 - 4p^3 + p^4 \approx 1 - 4p$, so $P \approx 4p$.

Using our code $[7,4,3]_2$ the message will be correctly decoded if not more than 1 bit error occurs. The probability of correct transmission is therefore

$\ge (1 - p)^7 + 7p(1 - p)^6 \approx (1 - 7p + 21p^2) + (7p - 42p^2) = 1 - 21p^2$.

In this case we have $P \le 21p^2$. We pay for this smaller error probability with an information rate $R = 4/7$ (meaning that $3/7$ of transmission time is redundant).

Compare this to our very first code, the repetition code of length 3. We leave it as an exercise to check that, seen as a block code with $k = 4, n = 12$, its error probability is $P \le 12p^2$. This is a decrease by about a factor 2 with respect to the $[7,4,3]_2$, but the information rate has gone down to $1/3$.

There is a code $[11,4,5]_2$. If we use it, the probability of correct transmission is

$\ge (1 - p)^{11} + 11p(1 - p)^{10} + \binom{11}{2}p^2(1 - p)^9$

$\approx \left(1 - 11p + 55p^2 - \binom{11}{3}p^3\right) + \left(11p - 110p^2 + 495p^3\right) + \left(55p^2 - 495p^3\right)$

$\approx 1 - \binom{11}{3}p^3$.