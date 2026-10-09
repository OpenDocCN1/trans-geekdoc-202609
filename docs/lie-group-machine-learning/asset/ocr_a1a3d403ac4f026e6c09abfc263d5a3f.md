# **Theorem 3.9.** *Let the Householder matrix* $H$ *be*

$$H = H(k, \mu) = \left[ \begin{array}{cc} P & 0 \\ 0 & P \end{array} \right]$$

*where*

$$P = I_n - \frac{2UU^*}{U^*U}, \;\; U = (0, \ldots, 0; u_k, \ldots, u_n)^T \neq 0 \, .$$

*Then, $H$ is a symplectic unitary matrix and* $U^*$ *is the conjugate transpose of $U$.*

*Proof.* *To prove that* $H$ *is a symplectic matrix, we only need to prove that* $H^*JH = J$ *is true.*

$$H^*JH = \left[ \begin{array}{cc} P & 0 \\ 0 & P \end{array} \right]^* \left[ \begin{array}{cc} P & 0 \\ 0 & P \end{array} \right] = \left[ \begin{array}{cc} 0 & P^*P \\ -P^*P & 0 \end{array} \right] \, .$$ (3.3)

*Because* $P = I_n - 2UU^*/U^*U$, $P^* = P$ *and*

$$egin{aligned} P^*P &= P^2 = \left( I_n - \frac{2UU^*}{U^*U} \right) \left( I_n - \frac{2UU^*}{U^*U} \right) \\ &= I_n - \frac{4UU^*}{U^*U} + \frac{4U(U^*U)U^*}{(U^*U)(U^*U)} = I_n \end{aligned}$$ (3.4)

*where* $U = (0, \ldots, 0; u_k, \ldots, u_n)^T \neq 0$*.* *Substituting (3.4) into (3.3) gives*

$$H^*JH = J \, .$$

*Therefore,* $H$ *is a symplectic matrix.*

$$H^*H = \left[ \begin{array}{cc} P & 0 \\ 0 & P \end{array} \right]^* \left[ \begin{array}{cc} P & 0 \\ 0 & P \end{array} \right] = \left[ \begin{array}{cc} P^*P & 0 \\ 0 & P^*P \end{array} \right] \, .$$

*Hence,* $H$ *is not only a unitary matrix but also a symplectic unitary matrix.*

*Let* $X$ *be an* $m \times n$-dimensional *real matrix and* $A = XX'$ *be a real symmetric matrix. $M$ can be constructed as a Hamiltonian matrix:*

$$M = \left[ \begin{array}{cc} A & 0 \\ 0 & -A' \end{array} \right] \, .$$

*Then, there is a* **Householder** *matrix* $H$, *which makes* $HM H'$ *an upper Hessenberg matrix*

$$HMH' = \left[ \begin{array}{cc} P & 0 \\ 0 & P \end{array} \right] \left[ \begin{array}{cc} A & 0 \\ 0 & -A' \end{array} \right] \left[ \begin{array}{cc} P & 0 \\ 0 & P \end{array} \right] = \left[ \begin{array}{cc} PAP' & 0 \\ 0 & -PA'P' \end{array} \right] = \left[ \begin{array}{cc} B & 0 \\ 0 & -B' \end{array} \right] \, .$$

*Therefore, the eigenvalue* $\lambda(A)$ *of* $A$ *is the eigenvalue* $\lambda(B)$ *of* $B$, *and the eigenvalue of* $X$ *is* $\sqrt{\lambda A}$, *such that the original* $2n$-dimensional *space is transformed into an* $n$-dimensional *space. In fact, for any real matrix* $X$, *the orthogonal matrix* $P$ *can be found directly by the* **Householder** *method such that* $PX P'$ *is the upper* **Hessenberg** *matrix, and the final principal component spectrum of* $X$ *is composed of the eigenvalues in*