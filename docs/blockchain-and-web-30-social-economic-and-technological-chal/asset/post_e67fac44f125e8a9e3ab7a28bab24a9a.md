
## Table 16.3 Structural self-interactive matrix for blockchain-based crowdfunding success factors

| Success factor number | Success factor name | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Company characteristics | X | V | X | O | O | V | X | O | O | V | V | O | O | V |
| 2 | Strong partners |  | X | V | V | X | X | X | X | A | X | V | V | V | V |
| 3 | Strong early adopters |  |  | A | A | A | O | O | X | V | V | V | V | O | O |
| 4 | Project innovativeness |  |  |  | O | V | A | X | A | O | V | V | V | O | O |
| 5 | Product stage |  |  |  |  | X | O | X | A | O | V | V | V | O | O |
| 6 | Product quality |  |  |  |  |  | A | A | A | V | O | V | V | O | O |
| 7 | Team composition |  |  |  |  |  |  | X | A | V | V | V | V | V | V |
| 8 | Team experience |  |  |  |  |  |  |  | A | V | V | V | V | V | V |
| 9 | Founder dedication |  |  |  |  |  |  |  |  | V | O | V | V | V | V |
| 10 | Social media traction |  |  |  |  |  |  |  |  |  | X | V | V | A | A |
| 11 | Campaign design |  |  |  |  |  |  |  |  |  |  | V | V | V | O |
| 12 | Campaign traction |  |  |  |  |  |  |  |  |  |  |  | A | A |  |
| 13 | White paper quality |  |  |  |  |  |  |  |  |  |  |  |  |  | V |
| 14 | Campaign transparency |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

**Note:** V: Factor (row) i influences factor (column) j; A: Factor (row) i is influenced by factor (column) j;
X: Factors (row) i and (column) j influence each other; O: NO relation between Factors (row) i and (column) j

## 2 Development of the reachability matrix from the SSIM

In this step, the SSIM is converted into a binary matrix, called a reachability matrix (RM), by substituting V, A, X and O by 1 and 0 following the rules specified here:

```
**Rule I:** If the pair (i, j) is V, then replace it by 1 and make the (j, i) entry 0 in the initial RM;
**Rule II:** If the pair (i, j) is A, then replace it by 0 and make the (j, i) entry 1 in the initial RM;
**Rule III:** If the pair (i, j) is X, then replace it by 1 and make the (j, i) entry 1 in the initial RM;
**Rule IV:** If the pair (i, j) is O, then replace it by 0 and make the (j, i) entry 0 in the initial RM;
**Rule V:** If i = j, then make the (i, j) entry 1 in the initial RM.

_Note: i stands for the row number; j stands for the column number_
```

## Table 16.4 The initial reachability matrix

| Success factor number | Description | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Company characteristics | 1 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 |
| 2 | Strong partners | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 1 |
| 3 | Strong early adopters | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 |
| 4 | Project innovativeness | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 |
| 5 | Product stage | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 |
| 6 | Product quality | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 |
| 7 | Team composition | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 |
| 8 | Team experience | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 |
| 9 | Founder dedication | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 1 | 1 | 1 |
| 10 | Social media traction | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 0 |
| 11 | Campaign design | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 |
| 12 | Campaign traction | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| 13 | White paper quality | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 1 |
| 14 | Campaign transparency | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 1 |

The resulting initial reachability matrix is shown in Table 16.4.
The final reachability matrix is produced after including the transitivities.
The result is shown in Table 16.5 (highlighted cells are the relations derived using the transitivity rule). The driving power of each success factor is calculated as the sum of the column values and shown as the last column of Table 16.5, whereas the dependence power of each success factor is calculated as the sum of the row values and shown as the last row of Table 16.5.

## 3 Partitioning of the reachability matrix into different levels

In this step, the final reachability matrix will be used (Table 16.5), to develop adjacency reachability R(si) sets and adjacency antecedent A(si) sets. R(si) consists of constituent i itself and other constituents, i.e., constituents in the row that it may affect, whereas the antecedent A(si) consists of constituents i and the other constituents, i.e., constituents in the column that may affect it.

R(si) ∩ A(si) results in the common constituents in both R(si) and A(si).
Then a comparison between R(si) and R(si) ∩ A(si) is made. The success factor, for which R(si) and R(si) ∩ A(si) are equal, is judged as the topmost factor in the hierarchy and is assigned Level I. Once top-level constituents are identified, they are separated from the remaining constituents. This iterative procedure is continued until the levels of all variables are obtained.
In this study, the process is completed in five iterations, which are shown in Table 16.6.

## Table 16.5 The final reachability matrix

| Success factor number | Description | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | Driving power |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Company characteristics | 1 | - | - | - | - | - | 1 | - | - | - | - | - | - | 1 | 14 |
| 2 | Strong partners | - | - | - | - | - | - | - | - | - | - | - | - | - | - | 14 |
| 3 | Strong early adopters | - | - | - | 1 | - | - | - | - | 1 | - | - | 1 | 1 | - | 14 |
| 4 | Project innovativeness | 1 | - | - | - | - | - | - | - | - | 1 | - | - | - | 1 | 14 |
| 5 | Product stage | 1 | - | - | - | - | - | - | - | - | 1 | - | - | - | 1 | 14 |
| 6 | Product quality | 1 | - | - | - | - | - | 1 | - | - | 1 | - | - | - | 1 | 14 |
| 7 | Team composition | - | - | 1 | - | - | 1 | - | - | 0 | - | 1 | - | - | 1 | 13 |
| 8 | Team experience | - | - | - | 1 | - | - | - | - | 0 | - | 1 | - | - | 1 | 13 |
| 9 | Founder dedication | - | - | - | - | 1 | - | - | 1 | - | 1 | - | - | - | 1 | 13 |
| 10 | Social media traction | - | - | - | - | 1 | - | - | 1 | - | - | - | 1 | - | - | 13 |
| 11 | Campaign design | 0 | - | - | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 6 |
| 12 | Campaign traction | 0 | - | - | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 3 |
| 13 | White paper quality | 0 | - | - | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | - | 0 | 0 | 6 |
| 14 | Campaign transparency | 0 | - | - | 0 | 0 | 0 | 0 | 0 | 0 | 0 | - | - | 0 | 0 | 5 |
| | Dependence power | 10 | 0 | 0 | 0 | 0 | 10 | 10 | 10 | 7 | 13 | 14 | 14 | 14 | 13 | |

## Table 16.6 Iterations showing partitioned levels

| Success factor number | Reachability set R(si) | Antecedent set A(si) | Intersection set R(si) ^ A(si) | Level |
|---|---|---|---|---|
| 1 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9,10 | I |
| 2 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1 |
| 3 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9,10 | |
| 4 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9,10 | |
| 5 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9,10 | |
| 6 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9,10 | |
| 7 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9,10 | |
| 8 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9,10 | |
| 9 | 1,2,3,4,5,6,7,8,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9 | |
| 10 | 1,2,3,4,5,6,7,8,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10 | 1,2,3,4,5,6,7,8,9 | |
| 11 | 2,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 2,10,11,12,13,14 | I |
| 12 | 2,11,12 | 1,2,3,4,5,6,7,8,9,10,11,12,13,14 | 2,11,12 | |
| 13 | 2,10,11,12,13,14 | 1,2,3,4,5,6,7,8,9,10,11,13 | 2,10,11,13 | I |
| 14 | 2,10,11,12,14 | 1,2,3,4,5,6,7,8,9,10,11,13,14 | 2,10,11,14 | |

| Success factor number | Reachability set R(si) | Antecedent set A(si) | Intersection set R(si) ^ A(si) | Level |
|---|---|---|---|---|
| 1 | 1,3,4,5,6,7,8,9,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,9,10 | |
| 3 | 1,3,4,5,6,7,8,9,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,9,10 | |
| 4 | 1,3,4,5,6,7,8,9,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,9,10 | |
| 5 | 1,3,4,5,6,7,8,9,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,9,10 | |
| 6 | 1,3,4,5,6,7,8,9,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,9,10 | |
| 7 | 1,3,4,5,6,7,8,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,10 | |
| 8 | 1,3,4,5,6,7,8,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,10 | |
| 9 | 1,3,4,5,6,7,8,9,10,13,14 | 1,3,4,5,6,7,8,9,10 | 1,3,4,5,6,7,8,9 | II |
| 10 | 1,3,4,5,6,7,8,10,13,14 | 1,3,4,5,6,7,8,9,10,13,14 | 1,3,4,5,6,7,8,10,13,14 | II |
| 13 | 10,13,14 | 1,3,4,5,6,7,8,9,10,13,14 | 10,13,14 | II |
| 14 | 10,14 | 1,3,4,5,6,7,8,9,10,13,14 | 10,14 | II |
