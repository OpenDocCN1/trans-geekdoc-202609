*the function which satisfies for all $\boldsymbol{\Phi} = (\boldsymbol{\Phi}_1, \dots, \boldsymbol{\Phi}_n) \in \mathbf{N}^n$, $k \in \{1, 2, \dots, \mathcal{L}(\boldsymbol{\Phi}_1)\}$ with*  
$\mathcal{L}(\boldsymbol{\Phi}_1) = \mathcal{L}(\boldsymbol{\Phi}_2) = \cdots = \mathcal{L}(\boldsymbol{\Phi}_n)$ that

$\begin{equation}
\mathcal{L}(\mathbb{P}_n(\boldsymbol{\Phi})) = \mathcal{L}(\boldsymbol{\Phi}_1), \qquad \mathcal{W}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} = \begin{pmatrix}
\mathcal{W}_{k, \boldsymbol{\Phi}_1} & 0 & 0 & \cdots & 0 \\
0 & \mathcal{W}_{k, \boldsymbol{\Phi}_2} & 0 & \cdots & 0 \\
0 & 0 & \mathcal{W}_{k, \boldsymbol{\Phi}_3} & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & \mathcal{W}_{k, \boldsymbol{\Phi}_n}
\end{pmatrix},
\tag{2.44}
\end{equation}

and $\begin{equation}
\mathcal{B}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} = \begin{pmatrix}
\mathcal{B}_{k, \boldsymbol{\Phi}_1} \\
\mathcal{B}_{k, \boldsymbol{\Phi}_2} \\
\vdots \\
\mathcal{B}_{k, \boldsymbol{\Phi}_n}
\end{pmatrix}
\end{equation}$

*cf. Definition 1.3.1.)*

# **Lemma 2.2.2 (Architectures of parallelizations of fully-connected feedforward ANNs).**  
Let $n, L \in \mathbb{N}$, $\boldsymbol{\Phi} = (\boldsymbol{\Phi}_1, \dots, \boldsymbol{\Phi}_n) \in \mathbf{N}^n$ satisfy $L = \mathcal{L}(\boldsymbol{\Phi}_1) = \mathcal{L}(\boldsymbol{\Phi}_2) = \cdots = \mathcal{L}(\boldsymbol{\Phi}_n)$ (cf. Definition 1.3.1). Then

+   (i) *it holds that*

$\begin{equation}
\mathbb{P}_n(\boldsymbol{\Phi}) \in \left(\bigtimes_{k=1}^L \left(\mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_{k}(\boldsymbol{\Phi}_j)) \times (\sum_{j=1}^n \mathbb{D}_{k-1}(\boldsymbol{\Phi}_j))} \times \mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_k(\boldsymbol{\Phi}_j))}\right)\right),
\tag{2.45}
\end{equation}$

(ii) *it holds for all $k \in \mathbb{N}_0$ that*

$\begin{equation}
\mathbb{D}_k(\mathbb{P}_n(\boldsymbol{\Phi})) = \mathbb{D}_k(\boldsymbol{\Phi}_1) + \mathbb{D}_k(\boldsymbol{\Phi}_2) + \cdots + \mathbb{D}_k(\boldsymbol{\Phi}_n),
\tag{2.46}
\end{equation}$

and

(iii) *it holds that*

$\begin{equation}
\mathcal{D}(\mathbb{P}_n(\boldsymbol{\Phi})) = \mathcal{D}(\boldsymbol{\Phi}_1) + \mathcal{D}(\boldsymbol{\Phi}_2) + \cdots + \mathcal{D}(\boldsymbol{\Phi}_n)
\tag{2.47}
\end{equation}$

*cf. Definition 2.2.1.)*

*Proof of Lemma 2.2.2.* *Note that item (iii) in Lemma 1.3.3 and (2.44) imply that for all*  
*$k \in \{1, 2, \dots, L\}$ *it holds that*

$\begin{equation}
\mathcal{W}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} \in \mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_k(\boldsymbol{\Phi}_j)) \times (\sum_{j=1}^n \mathbb{D}_{k-1}(\boldsymbol{\Phi}_j))} \qquad \text{and} \qquad \mathcal{B}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} \in \mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_k(\boldsymbol{\Phi}_j))}
\tag{2.48}
\end{equation}$

*cf. Definition 2.2.1.)* *Item (iii) in Lemma 1.3.3 therefore establishes items (i) and (ii). Note*  
*that item (ii) implies item (iii). The proof of Lemma 2.2.2 is thus complete.*  
$\square$