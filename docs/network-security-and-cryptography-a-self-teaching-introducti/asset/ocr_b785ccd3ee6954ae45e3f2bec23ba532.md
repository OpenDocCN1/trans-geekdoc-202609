# 374 • NETWORK SECURITY AND CRYPTOGRAPHY

![](bbox=[0.264, 0.118, 0.735, 0.423])

$a \leftarrow e + g(b

**FIGURE 8.16** A schematic diagram depicting the functionality of each step for SHA-1.

**Step 5: Output:** After the 512-bit block $Y_{L-1}$ has been processed, the output from the last stage forms the 160-bit Message Digest.
We can summarize the processing as follows:

**TABLE 8.1** Primitive Logical Functions Used in Various Rounds of SHA-1

| Round | Function | Logic $g(b, c, d)$ |
|---|---|--|
| 1 | $f_1$ | $(b \wedge c) \vee (
eg b \wedge d)$ |
| 2 | $f_2$ | $b \oplus c \oplus d$ |
| 3 | $f_3$ | $(b \wedge c) \vee (b \wedge d) \vee (c \wedge d)$ |
| 4 | $f_4$ | $b \oplus c \oplus d$ |

Where: $\oplus$: XOR, $\wedge$: AND, $\vee$: OR, $\leftarrow$: NOT