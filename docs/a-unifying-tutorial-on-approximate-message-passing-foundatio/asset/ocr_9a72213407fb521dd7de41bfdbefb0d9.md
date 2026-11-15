# A
Proofs and Technical Remarks

In addition to the definitions in Section 1.1, we introduce the following notation. The Moore–Penrose pseudoinverse of a matrix \( A \in \mathbb{R}^{k \times \ell} \) will be denoted by \( A^+ \in \mathbb{R}^{\ell \times k} \). This satisfies \( A^+ = (A^\top A)^+ A^\top \) (e.g. Barata and Hussein, 2012, Proposition 3.2), and if \( k = \ell \) and \( A \) is invertible, then \( A^+ = A^{-1} \). For non-negative, real-valued functions \( f, g \), we write \( f \lesssim g \) if there exists a universal constant \( C > 0 \) such that \( f \le Cg \); more generally, given parameters \( \alpha_1, \dots, \alpha_N \), we write \( f \lesssim_{\alpha_1, \dots, \alpha_N} g \) if there exists \( C \equiv C_{\alpha_1, \dots, \alpha_N} > 0 \), depending only on \( \alpha_1, \dots, \alpha_N \), such that \( f \le Cg \).

# A.1 Technical Remarks on the Master Theorems in Section 2.1

In this subsection, we will make some general observations that unify Theorems 2.1 and 2.3 with other master theorems in the AMP literature (e.g., Bolthausen, 2014; Bayati and Montanari, 2011; Javanmard and Montanari, 2013). There are a number of respects in which our results are presented differently and/or in slightly greater generality, and we discuss each of these in turn.