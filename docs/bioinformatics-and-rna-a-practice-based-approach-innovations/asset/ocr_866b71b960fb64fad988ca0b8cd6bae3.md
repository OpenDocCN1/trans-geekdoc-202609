| | A | B | C | D |
|---|---|---|---|---|
| A | - | -37 | -33 | -33 |
| B | | - | -33 | -33 |
| C | | | - | -37 |
| D | | | | - |

FIGURE 3.13 Neighbor Joining Method Example (Step 2.2)

```
D_AB-u_A - u_B = 16 - 31 - 22 = -37
```

The resultant distance matrix is shown in Figure 3.13.
Select the nodes that are closest to each other. In this case, A, B and C, D are
equidistant. So, we randomly choose C, D as the closest neighbors.

Step 3. Calculate V_i and V_j as:

```
V_i = 0.5 D_ij + 0.5 (u_i-u_j)
V_j = 0.5 D_ij + 0.5 (u_j-u_i)
```

For example:

```
V_C = 0.5 D_CD + 0.5 (u_C-u_D) = 0.5 * 13 + 0.5 * (22 - 28) = 3.5
V_D = 0.5 D_CD + 0.5 (u_D-u_C) = 0.5 * 13 + 0.5 * (28 - 22) = 9.5
```

Step 4. The distance between nodes C and D is now divided into two parts – 3.5
and 9.5 –respectively. The phylogenetic tree construction may start now. The
generated tree is shown in Figure 3.14.

Step 5. Next step is to combine nodes C and D in distance matrix. Also distances
of other nodes from X need to be calculated as shown in Figure 3.15(a) and 3.15(b).

```
D_XA = (D_CA + D_DA - D_CD)/2
= (20 + 26 - 13)/2 = 16.5

D_XB = (D_CB + D_DB - D_CD)/2
= (11 + 18 - 13)/2 = 8
```

![](bbox=[0.12, 0.84, 0.88, 0.91])