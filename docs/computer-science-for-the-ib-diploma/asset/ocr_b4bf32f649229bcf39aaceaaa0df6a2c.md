The first group is entirely along the bottom row, meaning C stays the same (C = 1), so we keep it in the expression. A changes from 0 to 1 between the cells in the group, so we discard A. B remains 1 in both cells, so we keep B. Therefore, the first part of our final expression is:

\( B \cdot C \)

| C \ AB | AB 00 | AB 01 | AB 11 | AB 10 |
|---|---|---|---|---|
| C 0 | | | | |
| C 1 | | | 1 | 1 |

The second group, like the first, is located along the bottom row, meaning that C stays as 1 because it does not change across the group. In this case, A remains 1 in both cells, while B changes from 0 to 1. Since B changes, we discard B from this part of the expression. As a result, we keep A and C, giving us the second part of our expression:

\( A \cdot C \)

We then combine these expressions with an OR operator, giving us the final expression:

\( B \cdot C + A \cdot C \)

> # Common mistake
> 
> When setting up your K-map for three inputs, make sure to use Gray code for the headings, not standard binary. Gray code ensures that only one bit changes between adjacent cells, which helps when grouping 1s and simplifies the expression more effectively.

# Wrapping around edges in K-maps

Here is the K-map for the expression:

\( \bar{B} + A \cdot B \cdot C \)

| C \ AB | AB 00 | AB 01 | AB 11 | AB 10 |
|---|---|---|---|---|
| C 0 | 1 | | | 1 |
| C 1 | 1 | 1 | 1 | 1 |

To group these 1s, you may assume this is the answer:

| C \ AB | AB 00 | AB 01 | AB 11 | AB 10 |
|---|---|---|---|---|
| C 0 | | 1 | | 1 |
| C 1 | | 1 | 1 | 1 |

However, K-maps are considered three-dimensional, and groups can be formed from left to right and top to bottom (although only left to right is possible with three inputs). In this example, it is possible to build a larger group by combining the two groups on the edges, forming a square group of four 1s.

| C \ AB | AB 00 | AB 01 | AB 11 | AB 10 |
|---|---|---|---|---|
| C 0 | 1 | | | 1 |
| C 1 | 1 | | | 1 |