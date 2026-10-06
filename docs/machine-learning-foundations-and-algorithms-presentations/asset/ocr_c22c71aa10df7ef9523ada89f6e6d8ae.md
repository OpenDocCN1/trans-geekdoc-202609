# Example: 1 channel

"Convolution"

| 3 | 1 | 2 | 8 | 4 |
|---|---|---|---|--|
| 1 | 0 | 7 | 3 | 6 |
| 2 | 3 | 5 | 1 | 3 |
| 1 | 4 | 1 | 2 | 6 | 5 |
| 3 | 2 | 1 | 3 | 7 | 2 |
| 9 | 2 | 6 | 2 | 5 | 1 |

| 1 | 0 | -1 |
|---|---|--|
| 1 | 0 | -1 |
| 1 | 0 | -1 |

| -7 | ... | ... |
|---|---|--|
| ... | ... | ... |
| | | |

Filter 3x3

Output 4x4

Result of the element-wise product and sum of the filter matrix and the original image

Original image 6x6