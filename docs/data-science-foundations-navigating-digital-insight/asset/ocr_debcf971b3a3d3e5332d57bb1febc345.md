$C_2 = (181.67, 81.67)

# Step 5: Repeat assignment and recalculation

Now we repeat Step 3 (assign students to the nearest cluster) and Step 4 (recalculate cluster centres) until the cluster centres stop moving significantly (this is called convergence).

Let's go through one more iteration of assigning students to clusters:

| Student | Height (cm) | Weight (kg) | Distance to new $C_1$ (165, 60) | Distance to new $C_2$ (181.67, 81.67) | Closest cluster |
|---|---|---|---|---||
| A | 160 | 55 | 7.07 | 36.53 | $C_1$ |
| B | 170 | 65 | 7.07 | 23.28 | $C_1$ |
| C | 165 | 60 | 0 | 27.21 | $C_1$ |
| D | 180 | 80 | 25.0 | 2.36 | $C_2$ |
| E | 175 | 75 | 18.03 | 8.33 | $C_2$ |
| F | 190 | 90 | 36.06 | 12.5 | $C_2$ |

+   * Cluster 1 ($C_1$): Students A, B, C
* Cluster 2 ($C_2$): Students D, E, F

Since the clusters haven't changed, we've reached convergence, and the algorithm stops.