**3.45** Note that \(\|\langle X,x\rangle\|_{\psi_2}\le K\|x\|_2\) and write down what it means by definition of the subgaussian norm.

**3.46 (b)** Combine Exercise **3.45** with the identity \(\mathbb{E}\|X\|_2^2=n\), which follows from isotropy.

**3.47 (a)⇒(b):** for any fixed \(x\), the function \(y\mapsto x^T Ay\) is linear and thus convex. Now recall (1.5) and Exercise **1.4**.

**3.49 (b)** First, check that the function \(f(z)=z^T Az\) is convex, and so it must attain its maximum in \([-1,1]^n\) on the vertices of the cube. Now fix any \(x,y\in\{-1,1\}^n\), use polarization identity to bound the bilinear form \(|x^T Ay|\) by these maximums, and bound these two quadratic forms using the fact above. Finally, apply the classical Grothendieck inequality (Theorem **3.5.1**).

**3.50 (b)** Check that \(f(z)=|z^T Az|\) is separately convex. Then proceed as in Exercise **3.49**.

**3.52 (a)** Express the objective function as \(\frac12\operatorname{tr}(\widetilde A ZZ^T)\), where \(\widetilde A=\begin{bmatrix}0&A\\A^T&0\end{bmatrix}\) is called the *Hermitian dilation* of the matrix \(A\), and \(Z=\begin{bmatrix}X\\Y\end{bmatrix}\) where \(X\) and \(Y\) are the matrices with rows \(X_i^T\) and \(Y_j^T\), respectively. Note that \(ZZ^T\) is the Gram matrix of the unit vectors \(X_1,\ldots,X_m,Y_1,\ldots,Y_n\). Proceed as in the proof of Proposition **3.5.6**. **(b)** Use Grothendieck inequality.

**3.53** Use the rotation invariance of the standard normal distribution to reduce the problem to \(\mathbb{R}^2\). Once in the plane, apply rotation invariance again to show that the probability of \(\{\langle g,u\rangle\) and \(\langle g,v\rangle\) having opposite signs\}\) is \(\alpha/\pi\), where \(\alpha\in[0,\pi]\) is the angle between \(u\) and \(v\). A picture might help!

**3.54** Consider cutting \(G\) repeatedly. To find a lower bound on the probability of a success (finding a large cut), use Paley–Zygmund inequality (Exercise **1.16**). Express the expected number of experiments until success in terms of this probability.

+   **3.56**
+   - **(a)** Argue that we can assume that \(v=(1,0,\ldots,0)\) and \(u=(u_1,u_2,0,\ldots,0)\).
+   - **(b)** Expand \(\mathbb{E}\,Z_uZ_v\) into four terms, and use Exercise **3.9** and part **(a)**.

**3.57** Sum up the identities from Exercise **3.56(b)** for \(u=u_i\) and \(v=u_j\) with weights \(a_{ij}\).

**3.58** Use randomized rounding (3.34).

+   **4.4**
+   - **(a)** Use the spectral representation of both norms (Lemma **4.1.11**).
+   - **(b)** Use Proposition **3.2.1(b)**.
+   - **(c)** Use (b) to write \(\|BA\|_F^2=\mathbb{E}\|BAg\|_2^2\) where \(g\sim N(0,I_n)\).

**4.5** In fact, any nonnegative, weakly decreasing numbers \(s_k\) whose squares sum to \(a^2\) satisfy \(s_k\le a/\sqrt{k}\).

**4.6** Express \(\|A^k x\|_2^2\) in terms of the SVD of \(A\). Show that the first term of the sum dominates.

+   **4.7**
+   - **(a)** Write \(Ax=\sum_{i=1}^n x_iA_i\).
+   - **(b)** For a contradiction, assume that \(\|A\|=\|A_1\|_2\) but \(A_1\) is not orthogonal to \(A_2\). Take \(x=(1,\varepsilon,0,0,\ldots,0)\) and show that the function \(f(\varepsilon)=\|Ax\|_2^2-\|A\|^2\|x\|_2^2\) can take positive values, contradicting the definition of the operator norm.

**4.8** To bound \(|x^T Ay|\) for unit vectors \(x\) and \(y\), use the triangle inequality: \(|x^T Ay|=|\sum_{ij}A_{ij}x_i y_j|\le\sum_{ij}|A_{ij}x_i y_j|\). Now apply the Cauchy–Schwarz inequality, splitting \(|A_{ij}|\) between the two terms.

**4.10** To prove achievability, consider a matrix whose all entries equal 1, and on the other hand Walsh matrix (Exercise **4.9**).

**4.11** For a unit vector \(x\), find \(\|Px-x/2\|_2^2\) and \(\|Qx-x/2\|_2^2\), then apply the triangle inequality.

**4.12 (a)** A neat trick: block-diagonalize \(P-Q\). Take an orthogonal matrix \(\widetilde U=[U\ U_\perp]\) whose first columns form \(U\) and span \(\operatorname{Im}P\). Similarly, take an orthogonal matrix \(\widetilde V=[V\ V_\perp]\) whose first columns form \(V\) and span \(\operatorname{Im}Q\). Then compute \(\widetilde U^T(P-Q)\widetilde V\) and realize that it is a block matrix whose norm is the maximal norm of the two blocks.

**4.13** Use Exercise **4.12** and Lemma **4.1.16**; follow the Davis–Kahan proof (Theorem **4.1.15**).