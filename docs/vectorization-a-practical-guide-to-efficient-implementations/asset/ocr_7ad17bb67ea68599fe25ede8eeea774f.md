# Inputs

| | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| 0 | 1 | 2 | 3 | 4 |
| 1 | 5 | 6 | 7 | 8 |
| 2 | 9 | 10 | 11 | 12 |
| 3 | 13 | 14 | 15 | 16 |
| 4 | 17 | 18 | 19 | 20 |

# Indices

| Block | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| 1 | 8 | 15 | 20 | 2 |
| 2 | 10 | 8 | 19 | 2 |
| 3 | 5 | 1 | 6 | 2 |
| 4 | 2 | 10 | 13 | 6 |
| 5 | 8 | 15 | 19 | 6 |
| 6 | 7 | 13 | 12 | 2 |

**Figure 3.12** Illustration of tf.gather_nd with nonzero batch_dims argument. The initial two batch dimensions are unfolded into a 2 x 3 grid in this schematic representation.