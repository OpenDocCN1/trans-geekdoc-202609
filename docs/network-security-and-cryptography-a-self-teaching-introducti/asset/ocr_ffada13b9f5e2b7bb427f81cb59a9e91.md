# 372 • NETWORK SECURITY AND CRYPTOGRAPHY

MD Register A:

| 6 | 7 |
| 4 | 5 |
| 2 | 3 |
| 0 | 1 |

MD Register B:

| E | F |
| C | D |
| A | B |
| S | 9 |

MD Register C:

| 9 | S |
| B | A |
| D | C |
| F | E |

MD Register D:

| 1 | 0 |
| 3 | 2 |
| 5 | 4 |
| 7 | 6 |

MD Register E:

| C | 3 |
| D | 2 |
| E | 1 |
| F | 0 |

# 4. Step 4: Process Message in terms of 512-bit (16-word) blocks.

The heart of one algorithm is a Compression Function that consists of 4 rounds of processing 20 steps each. Each round has an identical structure but uses a different primitive logical function, referred to as $f_1, f_2, f_3,$ and $f_4$. Each round takes as input the 512-bit buffer value ABCD and updates the contents of the buffer $Y$. Each round also makes use of an additive constant $K_r$, where $0 \le t \le 79$ indicates the step of the 80 steps across five rounds. In fact, only four distinct constants are used, as indicated in the following: