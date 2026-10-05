• These values are stored in the little-endian format, that is, the least significant byte is stored in the low-address byte position, as shown in the following:

MD Register A:

| | |
|---||
| 0 | 1 |
| 2 | 3 |
| 4 | 5 |
| 6 | 7 |

MD Register B:

| | |
|---||
| S | 9 |
| A | B |
| C | D |
| E | F |

MD Register C:

| | |
|---||
| F | E |
| D | C |
| B | A |
| 9 | S |

MD Register D:

| | |
|---||
| 7 | 6 |
| 5 | 4 |
| 3 | 2 |
| 1 | 0 |

# Step 4: Process the Message in terms of 512-bit blocks

+   • Heart of MD5 processing is a Compression Function $H_{MD5}$ that consists of 4 rounds of processing, and each round consist of sixteen steps. Inputs to each round.

+   • Current 512-bit message block ($S_{ij}$). The block is divided into sixteen 32-bit words. In each round, each of the sixteen words is used precisely once in one of the sixteen steps; the order in which the words are used depends on the round.

+   • Current 128-bit MD Buffer value, which is obtained from the processing of previous block of data. For the processing of the first block, MD Buffer will have its value as initialized previously in Step 3.