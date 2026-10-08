
# 2.1. Compositions of fully-connected feedforward ANNs

Combining this with (2.34) proves that for all $k \in \{1, 2, \dots, L(\mathcal{R}_1 \bullet \mathcal{R}_2) \bullet \mathcal{R}_3\}$ it holds that

$$
\begin{aligned}
&(\mathcal{L}_{k, (\mathcal{R}_1 \bullet \mathcal{R}_2) \bullet \mathcal{R}_3}, \hat{\mathcal{H}}_{k, (\mathcal{R}_1 \bullet \mathcal{R}_2) \bullet \mathcal{R}_3}) \\
&\quad \begin{cases} 
(\mathcal{L}_{k, \mathcal{R}_3}, \hat{\mathcal{H}}_{k, \mathcal{R}_3}) & : k < L(\mathcal{R}_3) \\
(\mathcal{L}_{1, \mathcal{R}_2} \mathcal{L}^{L(\mathcal{R}_3), \mathcal{R}_3}, \mathcal{L}_{1, \mathcal{R}_2} \hat{\mathcal{H}}^{L(\mathcal{R}_3), \mathcal{R}_3} + \hat{\mathcal{H}}_{1, \mathcal{R}_2}) & : k = L(\mathcal{R}_3) \\
(\mathcal{L}_{k-L(\mathcal{R}_3)+1, \mathcal{R}_2}, \hat{\mathcal{H}}_{k-L(\mathcal{R}_3)+1, \mathcal{R}_2}) & : L(\mathcal{R}_3) < k < L(\mathcal{R}_2) + L(\mathcal{R}_3) - 1 \\
(\mathcal{L}_{1, \mathcal{R}_1} \mathcal{L}^{L(\mathcal{R}_2), \mathcal{R}_2}, \mathcal{L}_{1, \mathcal{R}_1} \hat{\mathcal{H}}^{L(\mathcal{R}_2), \mathcal{R}_2} + \hat{\mathcal{H}}_{1, \mathcal{R}_1}) & : k = L(\mathcal{R}_2) + L(\mathcal{R}_3) - 1 \\
(\mathcal{L}_{k-L(\mathcal{R}_3)-L(\mathcal{R}_2)+2, \mathcal{R}_1}, \hat{\mathcal{H}}_{k-L(\mathcal{R}_3)-L(\mathcal{R}_2)+2, \mathcal{R}_1}) & : k > L(\mathcal{R}_2) + L(\mathcal{R}_3) - 1
\end{cases} \quad (2.36)
\end{aligned}
$$

In addition, observe that (2.2), the fact that $L(\mathcal{R}_2 \bullet \mathcal{R}_3) = L(\mathcal{R}_2) + L(\mathcal{R}_3) - 1$, and the assumption that $L(\mathcal{R}_2) > 1$ demonstrate that for all $k \in \{1, 2, \dots, L(\mathcal{R}_1 \bullet (\mathcal{R}_2 \bullet \mathcal{R}_3))\}$ it holds that

$$
\begin{aligned}
&(\mathcal{L}_{k, \mathcal{R}_2 \bullet \mathcal{R}_3}, \hat{\mathcal{H}}_{k, \mathcal{R}_2 \bullet \mathcal{R}_3}) \\
&\quad \begin{cases} 
(\mathcal{L}_{k, \mathcal{R}_2 \bullet \mathcal{R}_3}, \hat{\mathcal{H}}_{k, \mathcal{R}_2 \bullet \mathcal{R}_3}) & : k < L(\mathcal{R}_2 \bullet \mathcal{R}_3) \\
(\mathcal{L}_{1, \mathcal{R}_1} \mathcal{L}^{L(\mathcal{R}_2 \bullet \mathcal{R}_3), \mathcal{R}_2 \bullet \mathcal{R}_3}, \mathcal{L}_{1, \mathcal{R}_1} \hat{\mathcal{H}}^{L(\mathcal{R}_2 \bullet \mathcal{R}_3), \mathcal{R}_2 \bullet \mathcal{R}_3} + \hat{\mathcal{H}}_{1, \mathcal{R}_1}) & : k = L(\mathcal{R}_2 \bullet \mathcal{R}_3) \\
(\mathcal{L}_{k-L(\mathcal{R}_2 \bullet \mathcal{R}_3)+1, \mathcal{R}_1}, \hat{\mathcal{H}}_{k-L(\mathcal{R}_2 \bullet \mathcal{R}_3)+1, \mathcal{R}_1}) & : k > L(\mathcal{R}_2 \bullet \mathcal{R}_3)
\end{cases} \\
&= \begin{cases} 
(\mathcal{L}_{k, \mathcal{R}_3}, \hat{\mathcal{H}}_{k, \mathcal{R}_3}) & : k < L(\mathcal{R}_3) \\
(\mathcal{L}_{1, \mathcal{R}_2} \mathcal{L}^{L(\mathcal{R}_3), \mathcal{R}_3}, \mathcal{L}_{1, \mathcal{R}_2} \hat{\mathcal{H}}^{L(\mathcal{R}_3), \mathcal{R}_3} + \hat{\mathcal{H}}_{1, \mathcal{R}_2}) & : k = L(\mathcal{R}_3) \\
(\mathcal{L}_{k-L(\mathcal{R}_3)+1, \mathcal{R}_2}, \hat{\mathcal{H}}_{k-L(\mathcal{R}_3)+1, \mathcal{R}_2}) & : L(\mathcal{R}_3) < k < L(\mathcal{R}_2) + L(\mathcal{R}_3) - 1 \\
(\mathcal{L}_{1, \mathcal{R}_1} \mathcal{L}^{L(\mathcal{R}_2), \mathcal{R}_2}, \mathcal{L}_{1, \mathcal{R}_1} \hat{\mathcal{H}}^{L(\mathcal{R}_2), \mathcal{R}_2} + \hat{\mathcal{H}}_{1, \mathcal{R}_1}) & : k = L(\mathcal{R}_2) + L(\mathcal{R}_3) - 1 \\
(\mathcal{L}_{k-L(\mathcal{R}_2)-L(\mathcal{R}_3)+2, \mathcal{R}_1}, \hat{\mathcal{H}}_{k-L(\mathcal{R}_2)-L(\mathcal{R}_3)+2, \mathcal{R}_1}) & : k > L(\mathcal{R}_2) + L(\mathcal{R}_3) - 1
\end{cases} \quad (2.37)
\end{aligned}
$$

This, (2.36), and (2.33) establish that for all $k \in \{1, 2, \dots, L(\mathcal{R}_1) + L(\mathcal{R}_2) + L(\mathcal{R}_3) - 2\}$ it holds that

$$
(\mathcal{L}_{k, (\mathcal{R}_1 \bullet \mathcal{R}_2) \bullet \mathcal{R}_3}, \hat{\mathcal{H}}_{k, (\mathcal{R}_1 \bullet \mathcal{R}_2) \bullet \mathcal{R}_3}) = (\mathcal{L}_{k, \mathcal{R}_1 \bullet (\mathcal{R}_2 \bullet \mathcal{R}_3)}, \hat{\mathcal{H}}_{k, \mathcal{R}_1 \bullet (\mathcal{R}_2 \bullet \mathcal{R}_3)}). \quad (2.38)
$$

Hence, we obtain that

$$
(\mathcal{R}_1 \bullet \mathcal{R}_2) \bullet \mathcal{R}_3 = \mathcal{R}_1 \bullet (\mathcal{R}_2 \bullet \mathcal{R}_3). \quad (2.39)
$$

The proof of Lemma 2.1.4 is thus complete.

**Corollary 2.1.5.** Let $\Phi_1, \Phi_2, \Phi_3 \in \mathbf{N}$ satisfy $\mathcal{I}(\Phi_1) = \mathcal{O}(\Phi_2)$ and $\mathcal{I}(\Phi_2) = \mathcal{O}(\Phi_3)$ (cf. Definition 1.3.1). Then

$$
(\Phi_1 \bullet \Phi_2) \bullet \Phi_3 = \Phi_1 \bullet (\Phi_2 \bullet \Phi_3) \quad (2.40)
$$

(cf. Definition 2.1.1).

*Proof of Corollary 2.1.5.* Note that Lemma 2.1.3 and Lemma 2.1.4 establish (2.40). The proof of Corollary 2.1.5 is thus complete. $\square$

## 2.1.4 Powers of fully-connected feedforward ANNs

**Definition 2.1.6** (Powers of fully-connected feedforward **ANNs**). *We denote by $(\cdot)^{\bullet n}$: $\{\Phi \in \mathbf{N}: \mathcal{I}(\Phi) = \mathcal{O}(\Phi)\} \rightarrow \mathbf{N}$, $n \in \mathbb{N}_0$, the functions which satisfy for all $n \in \mathbb{N}_0$, $\Phi \in \mathbf{N}$ with $\mathcal{I}(\Phi) = \mathcal{O}(\Phi)$ that*

$$
\Phi^{\bullet n} = \begin{cases} 
(\mathrm{I}_{\mathcal{O}(\Phi)}, (0,0,\dots,0)) \in \mathbb{R}^{\mathcal{O}(\Phi) \times \mathcal{O}(\Phi)} \times \mathbb{R}^{\mathcal{O}(\Phi)} & : n = 0 \\
\Phi \bullet (\Phi^{\bullet (n-1)}) & : n \in \mathbb{N}
\end{cases} \quad (2.41)
$$

(cf. Definitions 1.3.1, 1.5.5, and 2.1.1).

**Lemma 2.1.7** (Number of hidden layers of powers of **ANNs**). *Let $n \in \mathbb{N}_0$, $\Phi \in \mathbf{N}$ satisfy $\mathcal{I}(\Phi) = \mathcal{O}(\Phi)$ (cf. Definition 1.3.1). Then*

$$
\mathcal{H}(\Phi^{\bullet n}) = n\mathcal{H}(\Phi) \quad (2.42)
$$

(cf. Definition 2.1.6).

*Proof of Lemma 2.1.7.* Observe that Proposition 2.1.2, (2.41), and induction establish (2.42). The proof of Lemma 2.1.7 is thus complete. $\square$

## 2.2 Parallelizations of fully-connected feedforward ANNs

### 2.2.1 Parallelizations of fully-connected feedforward ANNs with the same length

**Definition 2.2.1** (Parallelization of fully-connected feedforward **ANNs**). *Let $n \in \mathbb{N}$. Then we denote by*

$$
\mathbf{P}_n: \{\Phi = (\Phi_1, \dots, \Phi_n) \in \mathbf{N}^n: \mathcal{L}(\Phi_1) = \mathcal{L}(\Phi_2) = \dots = \mathcal{L}(\Phi_n)\} \rightarrow \mathbf{N} \quad (2.43)
$$

*the function which satisfies for all $\boldsymbol{\Phi} = (\boldsymbol{\Phi}_1, \dots, \boldsymbol{\Phi}_n) \in \mathbf{N}^n$, $k \in \{1, 2, \dots, \mathcal{L}(\boldsymbol{\Phi}_1)\}$ with*  
$\mathcal{L}(\boldsymbol{\Phi}_1) = \mathcal{L}(\boldsymbol{\Phi}_2) = \cdots = \mathcal{L}(\boldsymbol{\Phi}_n)$ that

$$
\mathcal{L}(\mathbb{P}_n(\boldsymbol{\Phi})) = \mathcal{L}(\boldsymbol{\Phi}_1), \qquad \mathcal{W}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} = \begin{pmatrix}
\mathcal{W}_{k, \boldsymbol{\Phi}_1} & 0 & 0 & \cdots & 0 \\
0 & \mathcal{W}_{k, \boldsymbol{\Phi}_2} & 0 & \cdots & 0 \\
0 & 0 & \mathcal{W}_{k, \boldsymbol{\Phi}_3} & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & \mathcal{W}_{k, \boldsymbol{\Phi}_n}
\end{pmatrix}, \quad (2.44)
$$

and 

$$
\mathcal{B}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} = \begin{pmatrix}
\mathcal{B}_{k, \boldsymbol{\Phi}_1} \\
\mathcal{B}_{k, \boldsymbol{\Phi}_2} \\
\vdots \\
\mathcal{B}_{k, \boldsymbol{\Phi}_n}
\end{pmatrix}
$$

*(cf. Definition 1.3.1.)*

**Lemma 2.2.2** (Architectures of parallelizations of fully-connected feedforward ANNs). Let $n, L \in \mathbb{N}$, $\boldsymbol{\Phi} = (\boldsymbol{\Phi}_1, \dots, \boldsymbol{\Phi}_n) \in \mathbf{N}^n$ satisfy $L = \mathcal{L}(\boldsymbol{\Phi}_1) = \mathcal{L}(\boldsymbol{\Phi}_2) = \cdots = \mathcal{L}(\boldsymbol{\Phi}_n)$ (cf. Definition 1.3.1). Then

- (i) *it holds that*
  
  $$
  \mathbb{P}_n(\boldsymbol{\Phi}) \in \left(\bigtimes_{k=1}^L \left(\mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_{k}(\boldsymbol{\Phi}_j)) \times (\sum_{j=1}^n \mathbb{D}_{k-1}(\boldsymbol{\Phi}_j))} \times \mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_k(\boldsymbol{\Phi}_j))}\right)\right), \quad (2.45)
  $$

- (ii) *it holds for all $k \in \mathbb{N}_0$ that*
  
  $$
  \mathbb{D}_k(\mathbb{P}_n(\boldsymbol{\Phi})) = \mathbb{D}_k(\boldsymbol{\Phi}_1) + \mathbb{D}_k(\boldsymbol{\Phi}_2) + \cdots + \mathbb{D}_k(\boldsymbol{\Phi}_n), \quad (2.46)
  $$

- and (iii) *it holds that*
  
  $$
  \mathcal{D}(\mathbb{P}_n(\boldsymbol{\Phi})) = \mathcal{D}(\boldsymbol{\Phi}_1) + \mathcal{D}(\boldsymbol{\Phi}_2) + \cdots + \mathcal{D}(\boldsymbol{\Phi}_n) \quad (2.47)
  $$

*(cf. Definition 2.2.1.)*

*Proof of Lemma 2.2.2.* *Note that item (iii) in Lemma 1.3.3 and (2.44) imply that for all*  
*$k \in \{1, 2, \dots, L\}$ *it holds that*

$$
\mathcal{W}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} \in \mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_k(\boldsymbol{\Phi}_j)) \times (\sum_{j=1}^n \mathbb{D}_{k-1}(\boldsymbol{\Phi}_j))} \qquad \text{and} \qquad \mathcal{B}_{k, \mathbb{P}_n(\boldsymbol{\Phi})} \in \mathbb{R}^{(\sum_{j=1}^n \mathbb{D}_k(\boldsymbol{\Phi}_j))} \quad (2.48)
$$

*(cf. Definition 2.2.1.)* *Item (iii) in Lemma 1.3.3 therefore establishes items (i) and (ii). Note that item (ii) implies item (iii). The proof of Lemma 2.2.2 is thus complete.* $\square$

**Proposition 2.2.3** (Realizations of parallelizations of fully-connected feedforward $ANNs$). *Let $a \in C(\mathbb{R}, \mathbb{R})$, $n \in \mathbb{N}$, $\Phi = (\Phi_1, \dots, \Phi_n) \in \mathbf{N}^n$ satisfy $\mathcal{L}(\Phi_1) = \mathcal{L}(\Phi_2) = \dots = \mathcal{L}(\Phi_n)$ (cf. Definition 1.3.1). Then*

- (i) it holds that

$$
\mathcal{R}_{a}^{\mathbf{N}}(\mathbf{P}_{n}(\Phi)) \in C(\mathbb{R}[\sum_{j=1}^n \mathcal{I}(\Phi_j)], \mathbb{R}[\sum_{j=1}^n \mathcal{O}(\Phi_j)]) \quad (2.49)
$$

- and (ii) it holds for all $x_1 \in \mathbb{R}^{\mathcal{I}(\Phi_1)}$, $x_2 \in \mathbb{R}^{\mathcal{I}(\Phi_2)}$, $\dots$, $x_n \in \mathbb{R}^{\mathcal{I}(\Phi_n)}$ that

$$
\begin{align*} 
&\left(\mathcal{R}_{a}^{\mathbf{N}}(\mathbf{P}_{n}(\Phi))\right)(x_1, x_2, \dots, x_n) \\
&= \left((\mathcal{R}_{a}^{\mathbf{N}}(\Phi_1))(x_1), (\mathcal{R}_{a}^{\mathbf{N}}(\Phi_2))(x_2), \dots, (\mathcal{R}_{a}^{\mathbf{N}}(\Phi_n))(x_n)\right) \in \mathbb{R}[\sum_{j=1}^n \mathcal{O}(\Phi_j)] 
\end{align*} \quad (2.50)
$$

*(cf. Definitions 1.3.4 and 2.2.1).*

*Proof of Proposition 2.2.3*. Throughout this proof, let $L = \mathcal{L}(\Phi_1)$, for every $j \in \{1, 2, \dots, n\}$ let

$$
\begin{align*} 
X^j = \Big\{} &x = (x_0, x_1, \dots, x_L) \in \mathbb{R}^{\mathbb{D}_0(\Phi_j)} \times \mathbb{R}^{\mathbb{D}_1(\Phi_j)} \times \dots \times \mathbb{R}^{\mathbb{D}_L(\Phi_j)} : \\
&\left(\forall k \in \{1, 2, \dots, L\} : x_k = \mathfrak{M}^{\mathbf{a}^{\frac{1}{\mathbb{L}(\Phi_1)+\text{id}_{\mathbb{R}}\mathbb{1}(k), \mathbb{D}_k(\Phi_j)}}\left(\mathcal{W}_{k, \Phi_j}x_{k-1} + \mathcal{B}_{k, \Phi_j}\right)\right) \Big\}, 
\end{align*} \quad (2.51)
$$

and let

$$
\begin{align*} 
\mathfrak{X} = \Big\{} &\mathfrak{x} = (\mathfrak{x}_0, \mathfrak{x}_1, \dots, \mathfrak{x}_L) \in \mathbb{R}^{\mathbb{D}_0(\mathbf{P}_{n}(\Phi))} \times \mathbb{R}^{\mathbb{D}_1(\mathbf{P}_{n}(\Phi))} \times \dots \times \mathbb{R}^{\mathbb{D}_L(\mathbf{P}_{n}(\Phi))} : \\
&\left(\forall k \in \{1, 2, \dots, L\} : \mathfrak{x}_k = \mathfrak{M}^{\mathbf{a}^{\frac{1}{\mathbb{L}(\Phi_1)+\text{id}_{\mathbb{R}}\mathbb{1}(k), \mathbb{D}_k(\mathbf{P}_{n}(\Phi))}}\left(\mathcal{W}_{k, \mathbf{P}_{n}(\Phi)}\mathfrak{x}_{k-1} + \mathcal{B}_{k, \mathbf{P}_{n}(\Phi)}\right)\right) \Big\}. 
\end{align*} \quad (2.52)
$$

Observe that item **(ii)** in Lemma 2.2.2 and item **(ii)** in Lemma 1.3.3 imply that

$$
\mathcal{I}(\mathbf{P}_{n}(\Phi)) = \mathbb{D}_0(\mathbf{P}_{n}(\Phi)) = \sum_{j=1}^n \mathbb{D}_0(\Phi_j) = \sum_{j=1}^n \mathcal{I}(\Phi_j). \quad (2.53)
$$

Furthermore, note that item **(ii)** in Lemma 2.2.2 and item **(ii)** in Lemma 1.3.3 ensure that

$$
\mathcal{O}(\mathbf{P}_{n}(\Phi)) = \mathbb{D}_{\mathcal{L}(\mathbf{P}_{n}(\Phi))}(\mathbf{P}_{n}(\Phi)) = \sum_{j=1}^n \mathbb{D}_{\mathcal{L}(\Phi_j)}(\Phi_j) = \sum_{j=1}^n \mathcal{O}(\Phi_j). \quad (2.54)
$$

Observe that (2.44) and item **(ii)** in Lemma 2.2.2 show that for all $\mathcal{G} \in C(\mathbb{R}, \mathbb{R})$, $k \in \{1, 2, \dots, L\}$, $x^1 \in \mathbb{R}^{\mathbb{D}_k(\Phi_1)}$, $x^2 \in \mathbb{R}^{\mathbb{D}_k(\Phi_2)}$, $\dots$, $x^n \in \mathbb{R}^{\mathbb{D}_k(\Phi_n)}$, $\mathfrak{x} \in \mathbb{R}^{\sum_{j=1}^n \mathbb{D}_k(\Phi_j)}$ with $\mathfrak{x} =
