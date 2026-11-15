![](bbox=[0.29, 0.092, 0.705, 0.285])

# FIGURE 2.3 Global Sequence Alignment-Step 3

Resultant Value = value from bottom box + gap value
= -1 + (-1)
= - 2

Step 9. Finally, the resultant value coming diagonally is calculated as:

Resultant Value = value from diagonal box + match/mismatch value
= 0 + 0
= 0

As G and A letters are mismatched, the score of the mismatch i.e. zero will be added to the value from the diagonal box.

Step 9. Now consider the highest out of these three resultant values i.e. 2, 0, and 0. The maximum value is zero so zero is saved as the final value for the highlighted cell. Also, the direction, from which the final value came, is also saved for the trace-back step. The resultant matrix is shown in Figure 2.4.

Step 10. Steps 5 to 9 are repeated to fill the matrix completely, as shown in Figure 2.5.

| C | -6 | | | | | |
|---|---|---|---|---|---|---|
| A | -5 | | | | | |
| T | -4 | | | | | |
| C | -3 | | | | | |
| A | -2 | | | | | |
| G | -1 | 0 | | | | |
| ⌒ | 0 | -1 | -2 | -3 | -4 |
| ⌒ | ⌒ | A | C | G | C |

# FIGURE 2.4 Global Sequence Alignment-Step 4