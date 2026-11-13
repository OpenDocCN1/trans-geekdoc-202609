![](bbox=[0.1, 0.08, 0.85, 0.37])

Figure 5.6 Cost distance calculation.

Let \( R_{ij} \) be the cell at row \( i \) and column \( j \), \( c_{ij} \) be the accumulative cost value of \( R_{ij} \) and \( A \) be the accumulative cost cell list.

(except \( R_{i,1} \) and \( R_{i,4} \)) from \( R_{i,2} \) and \( R_{i,3} \) like so:

+   1 Assign 0 to the cells representing the source locations (labelled 1 and 2 in the source layer), as there is no accumulative cost to return to them, and then calculate the accumulative costs of their adjacent cells like so:

\( c_{i,2} = 0 + (1 + 2) / 2 = 1.5 \)  
\( c_{2,1} = 0 + (1 + 3) / 2 = 2 \)  
\( c_{2,2} = 0 + [(1 + 5) / 2] \times 1.414 = 4.24 \)

\( c_{i,3} = c_{i,2} + (2 + 4) / 2 = 1.5 + 3 = 4.5 \)  
\( c_{2,1} = c_{i,2} + [(2 + 3) / 2] \times 1.414 = 1.5 + 3.535 = 5.04 \)  
\( c_{2,2} = c_{i,2} + (2 + 5) / 2 = 5 \)  
\( c_{2,3} = c_{i,2} + [(2 + 3) / 2] \times 1.414 = 5.04 \)

Similarly, calculate \( c_{3,3} \), \( c_{3,4} \) and \( c_{4,3} \). Add all the accumulative cost values to \( A = \{(R_{i,2}, 1.5), (R_{2,1}, 2), (R_{2,2}, 4.24), (R_{3,3}, 4.95), (R_{3,4}, 3.5), (R_{4,3}, 1.5)\} \).

Similarly, calculate \( c_{3,2} \), \( c_{3,3} \), \( c_{3,4} \) and \( c_{4,2} \). Delete \( (R_{i,2}, 1.5) \) and \( (R_{4,3}, 1.5) \) from \( A \), and add all the newly calculated accumulative cost values to \( A \). If the new accumulative cost for a cell in \( A \) is equal to or greater than the value the cell currently has, the value is ignored; otherwise, the old accumulative cost value for the cell is replaced in \( A \) with the new value. So \( c_{2,1} \), \( c_{2,2} \), \( c_{3,3} \) and \( c_{3,4} \) are not updated. Now, \( A = \{(R_{i,1}, 4.5), (R_{2,1}, 2), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{3,4}, 3.5), (R_{4,2}, 4)\} \).

+   2 Select the lowest-cost cells from \( A \), which are \( R_{i,2} \) and \( R_{4,3} \), and assign the cost values to the cells in the output layer. Calculate the accumulative costs to move into the neighbouring cells

+   3 Select the lowest-cost cell from \( A \), which is \( R_{2,1} \), and assign its cost value