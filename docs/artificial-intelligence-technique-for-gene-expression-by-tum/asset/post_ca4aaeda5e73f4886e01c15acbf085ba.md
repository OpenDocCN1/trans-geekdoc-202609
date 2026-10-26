
TΨₜT⁻¹ and Φₛ = TΨₛT⁻¹, which satisfy the following equations

U₂ = U₁Φₜ and U₄ = U₃Φₛ  (21)

Let μₗ and νₗ for l = 1, 2, ···, L be the corresponding eigenvalues of Φₜ and Φₛ. Thus the estimates of ω and θ can be given as follows

ω̂ = 2/[L(L + 1)] Σₗ₌₁ᴸ μₗ,

θ̂ = arcsin( (2c Σₗ₌₁ᴸ νₗ) / (L(L + 1)ω̂ fₛ d) )  (22)

It can be seen from (20) that the estimation accuracy of θ̂ depends on that of ω̂.

## C. Spatio-temporal Signal Model in the Presence of Multi-pitch

To solve the problem of joint estimation of the DOA and pitch in the multi-pitch case, a multi-channel and multi-pitch harmonic multiple signal classification (MC-HMUSIC) method was presented in [34], where a two-dimensional search is required to obtain the estimates of the pitch and DOA. To further reduce the computational complexity of the 2-D search in the MC-HMUSIC method, a two-stage DOA and pitch estimation method based on a subspace approach, i.e., MCOW-HMUSIC, was recently proposed in [35]; however, the two 1-D searches and an iterative procedure for the refined estimation are still required for the MCOW-HMUSIC method. Furthermore, the coupling of the pitch and DOA parameters is still required and poses a significant problem. In this subsection, a generalization of the previously proposed ESPRIT method for joint DOA and pitch estimation of the single pitch case to the multi-pitch case is derived.

Following a procedure similar to the single pitch case, with model in (1), for a given integer M and satisfying RM > Σₚ₌₁ᴾ Lₚ, one can construct the following data vector

X(n) = S(n) + Q(n), n = 0, 1, ···, N − M,  (23)

where

X(n) = [ x₀(n) ··· x₀(n + M − 1); ⋮ ⋱ ⋮; xᴿ₋₁(n) ··· xᴿ₋₁(n + M − 1) ].  (24)

The part of the signal of interest S(n) in X(n) can be rewritten as

S(n) = Σₚ₌₁ᴾ Σₗ₌₁ᴸₚ βₚ,ₗ(n) aₛ(lϕₚ) aₜᵀ(lωₚ).  (25)

where

βₚ,ₗ(n) = αₚ,ₗeʲˡωₚⁿ,

aₛ(ϕₚ) = [1 eʲϕₚ ··· eʲ⁽ᴿ⁻¹⁾ϕₚ]ᵀ,

aₜ(ωₚ) = [1 eʲωₚ ··· eʲ⁽ᴹ⁻¹⁾ωₚ]ᵀ.  (26)

Stacking the columns of X(n) into a new vector model x(n) gives

x(n) = vec{X(n)}
= s(n) + q(n) = Az(n) + q(n),  (27)

with

A = [A⁽¹⁾(ω₁, ϕ₁), ···, A⁽ᴾ⁾(ωᴾ, ϕᴾ)],  (28)

A⁽ᵖ⁾ = [a(ωₚ, ϕₚ), ···, a(Lₚωₚ, Lₚϕₚ)], p = 1, ···, P,  (29)

a(lₚωₚ, lₚϕₚ) = aₜ(lₚωₚ) ⊗ aₛ(lₚϕₚ),  (30)

z(n) = [α₁,₁eʲω₁ⁿ, ···, α₁,ᴸ₁eʲᴸ¹ω₁ⁿ, ···, αᴾ,₁eʲωᴾⁿ, ···, αᴾ,ᴸᴾeʲᴸᴾωᴾⁿ]ᵀ

For n = 0, 1, ···, N − M, we first define the following vector with X(n),

Yᴿᴹ×⁽ᴺ⁻ᴹ⁺¹⁾ = [x(0) x(1) ··· x(N − M)]
= A[z(0) z(1) ··· z(N − M)]
  + [q(0) ··· q(N − M)].  (31)

Thus, the above spatio-temporal signal model for the multi-pitch case can be reduced to the case of a single pitch in the previous section when P = 1 in (23).

## D. Joint Estimation of DOA and Pitch in the Multi-pitch Case Using ESPRIT: Multichannel Multi-Pitch ESPRIT (MMP-ESPRIT)

To use the ESPRIT method for joint estimation of DOA and pitch in the multi-pitch case, the singular value decomposition (SVD) of the data matrix Y is expressed by

Y = UΣVᴴ = [Uₛ Uₙ] [Σₛ 0; 0 Σₙ] Vᴴ,  (32)

where the column vectors of Uₛ and Uₙ span the signal subspace and noise subspace, respectively. The diagonal elements of Σₛ are composed of the P₀ = Σₚ₌₁ᴾ Lₚ largest singular values of Y, and one also has that Uₛ = AT for a nonsingular position matrix T.

Using the shift invariance structure of a(lωₚ, lϕₚ) in A, we can obtain the following two equations,

A₁Ψₜ = A₂,  (33)
A₃Ψₛ = A₄,  (34)

where Aᵢ = WᵢᵀA, i = 1, 2, 3, 4. Ψₜ and Ψₛ are defined as

Ψₜ = diag(Ψₜ₁, ···, Ψₜᴾ)
Ψₜₚ = diag(eʲωₚ, ···, eʲᴸᴾωₚ)
Ψₛ = diag(Ψₛ₁, ···, Ψₛᴾ)
Ψₛₚ = diag(eʲϕₚ, ···, eʲᴸᴾϕₚ).  (35–36)

Accordingly, one can also obtain the following equations by the subspace property,

U₂ = U₁Φₜ and U₄ = U₃Φₛ,  (37)

where

U₁ = W₁Uₛ and U₂ = W₂Uₛ,

where

$$\Phi_s=\operatorname{diag}\{[e^{j\phi_1},\ldots,e^{j\phi_L}],e^{j\phi_P},\ldots,e^{j\phi_L\phi_P}\}.$$ (57)

Thus, the matrix $\mathbf{X}_{M,R_0}$ can be written as

$$\mathbf{X}_{M,R_0}=\mathbf{J}_1\mathbf{A}_M[\mathbf{B}_M,\Phi_s\mathbf{B}_M,\ldots,\Phi_s^{R-R_0+1}\mathbf{B}_M]+\mathbf{Q}_{M,R_0}.$$ (58)

where $\mathbf{J}_1=\mathbf{I}_M\otimes[\mathbf{I}_{R_0}\ 0]$.

## F. Joint DOA and Single Pitch Estimation Using ESPRIT in the presence of Multi-path Propagation: Multichannel Single-pitch Multi-path ESPRIT (MSP-MP-ESPRIT)

Based on the constructed spatio-temporal smoothed data matrix $\mathbf{X}_{M,R_0}$, the noise subspace and signal subspace can be obtained from the SVD of $\mathbf{X}_{M,R_0}$, which is defined as

$$\mathbf{X}_{M,R_0}=[\mathbf{U}_s\ \mathbf{U}_n]\mathbf{\Sigma}\mathbf{V}^H.$$ (59)

where the columns of $\mathbf{U}_s$ and $\mathbf{U}_n$ are the singular vectors associated with the $P_0(=LP)$ largest values and the remaining $MR_0-P_0$ least singular values, respectively. Using the noise subspace of $\mathbf{X}_{M,R_0}$, a MUSIC-based method for joint multi-pitch and DOA estimation was presented in [34], where a 2-D grid search is required to obtain the estimates of parameter pairs $(\omega,\theta_p)$, $p=1,2,\ldots,P$. In this section, using the spatio-temporal shift invariance structure of $\mathbf{A}_M^{(R_0)}$, the ESPRIT-based method is exploited to give the estimates of $\{\omega,\theta_p\}$. One can obtain the following two equations with the signal subspace matrix $\mathbf{U}_s$

$$\mathbf{U}_2=\mathbf{U}_1\Phi_t\quad\text{and}\quad\mathbf{U}_4=\mathbf{U}_3\Phi_s.$$ (60)

where

$$\mathbf{U}_1=\mathbf{W}_1\mathbf{U}_s\quad\text{and}\quad\mathbf{U}_2=\mathbf{W}_2\mathbf{U}_s,$$
$$\mathbf{U}_3=\mathbf{W}_3\mathbf{U}_s\quad\text{and}\quad\mathbf{U}_4=\mathbf{W}_4\mathbf{U}_s.$$ (61)

where the selection matrices $\mathbf{W}_i$, $i=1,2,3,4$, are defined as follows

$$\mathbf{W}_1=\begin{bmatrix}\mathbf{I}_{M-1}\\\mathbf{0}_{1\times(M-1)}\end{bmatrix}\otimes\mathbf{I}_{R_0},\quad
\mathbf{W}_2=\begin{bmatrix}\mathbf{0}_{1\times(M-1)}\\\mathbf{I}_{M-1}\end{bmatrix}\otimes\mathbf{I}_{R_0},$$
$$\mathbf{W}_3=\mathbf{I}_M\otimes[\mathbf{I}_{R_0-1}\ \mathbf{0}_{1\times(R_0-1)}],\quad
\mathbf{W}_4=\mathbf{I}_M\otimes[\mathbf{0}_{1\times(R_0-1)}\ \mathbf{I}_{R_0-1}].$$

Thus, the estimates of $\omega$ and $\theta_p$ can be obtained from the eigenvalues $\mu_l$ and $\nu_l^{(p)}$ of $\Phi_t$ and $\Phi_s$ as

$$\hat{\omega}=\frac{2}{L(L+1)}\sum_{l=1}^{L}\angle\mu_l,$$
$$\hat{\theta}_p=\arcsin\left(\frac{2c\sum_{l=1}^{L}\angle\nu_l^{(p)}}{L(L+1)\hat{\omega}f_s d}\right),\quad p=1,2,\ldots,P.$$ (62)

| Algorithm | Steps |
|---|---|
| **MSP-ESPRIT** | 1. Align the observed matrix $\mathbf{Y}$ in Eq. (16).<br>2. Compute the SVD of $\mathbf{Y}$.<br>3. Compute the eigenvalues of the two matrices $\Phi_t$ and $\Phi_s$ in Eq. (21).<br>4. Estimate the pitch and DOA using Eqs. (22). |
| **MMP-ESPRIT** | 1. Align the observed matrix $\mathbf{Y}$ in Eq. (31).<br>2. Compute the SVD of $\mathbf{Y}$ in Eq. (32).<br>3. Compute the eigenvalues of the two matrices $\Phi_t$ and $\Phi_s$ in Eq. (37).<br>4. Estimate the pitch and DOA using Eqs. (39). |
| **MSP-MP-ESPRIT** | 1. Align the observed matrix $\mathbf{X}_{M,R_0}$ in Eq. (58).<br>2. Compute the SVD of matrix $\mathbf{X}_{M,R_0}$ in Eq. (59).<br>3. Compute the eigenvalues of the two matrices $\Phi_t$ and $\Phi_s$ in Eq. (60).<br>4. Estimate the pitch and DOA using Eqs. (62). |

## IV. ALGORITHM SUMMARIZATION AND COMPUTATIONAL COMPLEXITY ANALYSIS

In this section we analyze the computational complexity of the proposed algorithms. To that end, Table I provides a detailed description of the three algorithms.

In contrast to the NLS-based method for single pitch and the available MC-HMUSIC method for multi-pitch case, the main computational load of the proposed method is dominated by the computation of both the SVD of data matrix $\mathbf{Y}$ and the EVDs of the matrix pair $(\Phi_s,\Phi_t)$, which is around $O((RM)^2(N-M+1)+(L_1+L_2+\cdots+L_P)^3)$ for the MMP-ESPRIT method and $O((RM)^2(N-M+1)+(LP)^3)$ for the MSP-MP-ESPRIT method, respectively, while the computation of the NLS-based method requires $O(NRL^2+L^3)$ for per point in the search grid of 2-D parameters. Therefore, the whole computational load of the 2-D searching computation in the NLS-based method for single-pitch case is $O((NRL^2+L^3)g_\omega g_\theta)$, where $g_\omega$ and $g_\theta$ are the numbers of searches conducted along the frequency axis and DOA axis. The first part of the computational load of the MC-HMUSIC method is about $O((RM)^2(N-M+1))$, which is similar to the SVD computation of the proposed MSP-MP-ESPRIT method, but in addition, it needs $P$ 2-D searching computations to obtain the estimates of pitch and DOA for multi-pitch case. The 2-D searches in the MC-MUSIC method are of orders $O((RM)^2g_\omega g_\theta)$. Thus, the proposed method without 2-D searching has a lower computational load than both the NLS-based method and the MC-HMUSIC method.

## V. ASYMPTOTIC PERFORMANCE ANALYSIS OF PITCH AND DOA ESTIMATES

In this section, the asymptotic performance of the proposed ESPRIT-based method for multi-pitch and DOA estimation is analyzed. With the similar results derived in [42], it is easily shown that the estimations of pitch and DOA parameters are unbiased. The derivation of this result is based on the same analysis procedure for DOA estimation using the ESPRIT method in [41], while it can be directly generalized to the case of multi-path propagation scenarios, therefore, The derivation of this result is based on the same analysis procedure for DOA estimation using the ESPRIT method in [41].

We provide the variances of the estimated pitch and DOA parameters for the multi-pitch case in the absence of multi-path propagation, which are denoted by $E\{(\delta\omega_p)^2\}$ and $E\{(\delta\theta_p)^2\}$.
