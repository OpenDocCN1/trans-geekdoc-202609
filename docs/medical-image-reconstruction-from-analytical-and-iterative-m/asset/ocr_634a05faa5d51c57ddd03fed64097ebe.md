\(\sigma_{r+1} = \cdots = \sigma_m = 0.\) (6.121)

Since

\(\sigma_1 \ge \sigma_2 \ge \cdots \ge \sigma_l \ge \cdots \ge 0,\) (6.122)

Property 1 is equivalent to

\(\sigma_{r+1} = 0 \text{ and } \sigma_r > 0.\) (6.123)

Now let us look at Property 2:

\(A^+AA^+ = A^+,\) (6.124)

which is equivalent to

\(\text{diag} \left\{ \frac{1}{\sigma_1}, \frac{1}{\sigma_2}, \dots, \frac{1}{\sigma_r}, 0, \dots, 0 \right\} = \text{diag} \left\{ \frac{1}{\sigma_1}, \frac{1}{\sigma_2}, \dots, \frac{1}{\sigma_r}, 0, \dots, 0 \right\}.\) (6.125)

This property is always satisfied.

Property 3 \(A^+A^*A = A^*A\) and Property 4 \((AA^+)^* = AA^+\) both imply that

\(\text{diag} \{ 1, 1, \dots, 1, 0, \dots, 0 \} = \text{diag} \{ 1, 1, \dots, 1, 0, \dots, 0 \},\) (6.126)

which is always satisfied.

To summarize the above discussion, the condition under which \(A^+ = V\Sigma^*U^T\) is a generalized inverse of matrix \(A\) is

\(\sigma_{r+1} = 0 \text{ and } \sigma_r > 0.\) (6.127)

However, in practice, a cutoff index much smaller than this \(r\) is used to obtain a stable solution.

**Example 3:** None of the following images match the measured projections. Which one is the best solution among the three solutions in Figure 6.23? (Compare \(\chi^2\))

Solution

+   i) \(\chi^2 = 0^2 + 0^2 + 1^2 + 1^2 = 2, (\leftarrow \text{ Best})\)

+   ii) \(\chi^2 = 0^2 + 0^2 + 2^2 + 0^2 = 4,\)

+   iii) \(\chi^2 = 1^2 + 0^2 + 1^2 + 2^2 = 6.\)

**Example 4:** Find a least-squares reconstruction to the imaging problem shown in Figure 6.24.

Solution

The imaging matrix \(A\) for this problem \(AX = P\) is given as