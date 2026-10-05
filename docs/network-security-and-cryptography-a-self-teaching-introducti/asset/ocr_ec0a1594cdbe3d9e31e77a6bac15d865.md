Each round also takes as input fourth of the 64-element Sine-Function Table T[1...64]. The 64-element Sine-Function table comprises 32-bit randomized values. The $i^{th}$ element of the table is determined as:

```
$T[i] = \text{TRUNC}(2^{32} \times \text{ABS}(\sin(i))), 1 < i < 64$
```

$i$ is in radians (One radian=180/Pi deg)
All values are distinct and each of the 64 steps takes a different value of the sine-function, as indicated as:

| Round | Subset of Sine-Table Used |
| 1 | T [1...16] |
| 2 | T [17...32] |
| 3 | T [33...48] |
| 4 | T [49...64] |

+   The processing of each round is identical, but it uses a different logical function in each round:
Round 1: Logical Function $F$
Round 2: Logical Function $G$
Round 3: Logical Function $H$
Round 4: Logical Function $I$

# Output

+   Each round has a 128-bit output that updates the contents of $MD$ Buffer.
The first-round input ($CV_{0}$) is added to the output of the fourth round. The addition is performed modulo $2^{32}$, independently for the four registers of the $MD$ Buffer. The 128-bit resulting output $CV_{q+1}$ updates the contents of the $MD$ Buffer. This goes as input for the processing of the next block of data.
The output resulting from the processing of the last block, is, $CV_{L}$, forms the final 128-bit Message Digest (or Hash Value).