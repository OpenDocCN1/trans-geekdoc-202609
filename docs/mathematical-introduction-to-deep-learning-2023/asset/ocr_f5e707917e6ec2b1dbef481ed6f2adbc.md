proves item **\(\mathbf{i i i}\)**. Next note that **\((\ref{eq:4.23})\)** implies item **\(\mathbf{i v}\)**. Moreover, note that the fact that \( \mathcal{W}_{2, \underline{\mathbf{L}}_1} = (1 \ 1) \) and the fact that \( \underline{\mathbf{L}}_d = \mathbf{S}_{1, d} \bullet \mathbf{P}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1) \) show that

\begin{equation}
\mathcal{W}_{2, \mathbf{L}_d} = \mathcal{W}_{1, \mathbf{S}_{1, d}} \mathcal{W}_{2, \underline{\mathbf{L}}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1)} \end{equation}

\begin{equation}
= \underbrace{\begin{pmatrix} 1 & 1 & \cdots & 1 \end{pmatrix}}_{\in \mathbb{R}^{1 \times d}} \underbrace{\begin{pmatrix} \mathcal{W}_{2, \underline{\mathbf{L}}_1} & 0 & \cdots & 0 \\ 0 & \mathcal{W}_{2, \underline{\mathbf{L}}_1} & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & \mathcal{W}_{2, \underline{\mathbf{L}}_1} \end{pmatrix}}_{\in \mathbb{R}^{d \times (2d)}}
\end{equation}

\begin{equation}
= \begin{pmatrix} 1 & 1 & \cdots & 1 \end{pmatrix} \in \mathbb{R}^{1 \times (2d)}.
\end{equation}

This establishes item **\(\mathbf{v}\)**. The proof of Lemma **\(\ref{lem:4.2.3}\)** is thus complete. \qquad\qquad\qquad\qquad\qquad\qquad \(\square\)

*Exercise* **4.2.1**. Let \( d = 9 \), \( S = \{ (1, 3), (3, 5) \} \), \( V = (V_{r, k})_{(r, k) \in S} \in \prod_{(r, k) \in S} \mathbb{R}^{d \times d} \) satisfy \( V_{1, 3} = V_{3, 5} = \mathbf{I}_d \), let \( \Psi \in \mathbb{N} \) satisfy

\begin{equation}
\Psi = \mathbf{J}_d \bullet \mathbf{P}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1) \bullet \mathbf{J}_d \bullet \mathbf{P}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1),
\end{equation}

and let \( \Phi \in \mathbf{R} \) satisfy

\begin{equation}
\Phi = (\Psi, (V_{r, k})_{(r, k) \in S})
\end{equation}

(cf. Definitions **1.3.1, 1.5.1, 1.5.5, 2.1.1, 2.2.1, 2.2.6**, and **4.2.1**). For every \( x \in \mathbb{R}^d \) specify

\begin{equation}
\mathcal{R}_t^\mathbf{R}(\Phi)(x)
\end{equation}

explicitly and prove that your result is correct (cf. Definitions **1.2.4** and **1.5.4**).!

# **4.2.2 ANN representations for maxima**

**Lemma 4.2.4** (Unique existence of fully-connected feedforward maxima **ANNs**). *There exist unique* \( (\phi_d)_{d \in \mathbb{N}} \subseteq \mathbb{N} \) *which satisfy that*

+   (i) it holds for all \( d \in \mathbb{N} \) that \( \mathcal{I}(\phi_d) = d \),

(ii) it holds for all \( d \in \mathbb{N} \) that \( \mathcal{O}(\phi_d) = 1 \),

(iii) it holds that \( \phi_1 = \mathbf{A}_{1, 0} \in \mathbb{R}^{1 \times 1} \times \mathbb{R}^1 \),

(iv) it holds that

\begin{equation}
\phi_2 = \left(
\begin{pmatrix}
1 & -1 \\
0 & 1 \\
0 & -1
\end{pmatrix},
\begin{pmatrix}
0 \\
0
\end{pmatrix}
\right),
\left(
\begin{pmatrix}
1 & 1 & -1
\end{pmatrix},
\begin{pmatrix}
0
\end{pmatrix}
\right)
\in \left(\mathbb{R}^{3 \times 2} \times \mathbb{R}^3\right) \times \left(\mathbb{R}^{1 \times 3} \times \mathbb{R}^1\right),
\end{equation}