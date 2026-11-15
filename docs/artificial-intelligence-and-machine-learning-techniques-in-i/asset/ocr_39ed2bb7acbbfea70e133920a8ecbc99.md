In Figure 7.4, \( R_H \) is calculated for the matrix that is the pair-wise representation of the neighboring (distance \( d = 1 \)) pixels in \( 0^\circ \) direction (horizontal). The rows from \( r_1 \) to \( r_4 \) in Figure 7.4 are showing the all pairwise combination of neighboring pixels of first row in the matrix. Now following the same procedure, we will calculate the \( R_H \) for \( 4 \times 4 \) matrix shown if Figure 7.2. The \( R_{HO} \) for Figure 7.2 is shown in Figure 7.5 in which row \( r1 \) is pairwise combination of horizontal neighboring pixels of the matrix shown in Figure 7.2. Similarly, \( r2 \) to \( r4 \) are the pairwise combination of neighboring pixels in the matrix in horizontal direction that is \( 0^\circ \).

Now for calculating GTDM for direction \( 0^\circ \) and distance \( d = 1 \) (\( P_{HO} \)), we will consider \( R_{HO} \) as shown in Figure 7.5. The first coordinate \( (0, 0) \) of \( P_{HO} \) will be the total count of \( (0, 0) \) in \( R_{HO} \), as it is 6 times. So, the value of first coordinate \( (0, 0) \) of \( P_{HO} \) will be 6. In the same way, the value of \( (0, 1) \) will be calculated and total number of \( (0, 1) \) are counted in \( R_{HO} \) which is 1 in this case. Now, if we want to calculate the value of coordinate \( (2, 1) \) in \( P_{HO} \) than again we will count the occurrence of \( (2, 1) \) in \( R_{HO} \).

A = 
| | | | |
|---|---|---|---|
| 0 | 0 | 2 | 2 |
| 0 | 0 | 2 | 3 |
| 0 | 0 | 1 | 1 |
| 3 | 2 | 2 | 2 |

FIGURE 7.2 4 × 4 matrix with gray tone values scaled in range of 0–3.