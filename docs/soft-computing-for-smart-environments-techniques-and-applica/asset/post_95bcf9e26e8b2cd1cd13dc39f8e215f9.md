
## 5.2.1.1 Intuitionistic Fuzzy Sets (IFSs)

IFSs were first established by Atanassov in 1986 as an extension of fuzzy set theory. IFSs are separated from one another by the grade of membership and the grade of non-membership, the sum of which must be 1 or less than 1. This is addressed in detail in Explanation 5.1, which can be found in Atanassov (1999) and Alkan and Kahraman (2021).

### Explanation 5.1:
Let Y be a constant set. An IFS ~E in Y is an object having the formula specified by:

~E = { (Y, U~E(Y), v~E(Y)) | Y ∈ Y } (5.1)

where the function U~E: Y → [0, 1] designates the degree of membership of a component to the sets ~E, and v~E: Y → [0, 1] designates the degree of non-membership of a component to the sets ~E, with the condition that:

0 ≤ U~E(Y) + v~E(Y) ≤ 1, for ∀ Y ∈ Y (5.2)

The degree of uncertainty is computed as follows:

π~E(Y) = 1 - U~E(Y) - v~E(Y) (5.3)

### Explanation 5.2:
Let ~A = (U~A, v~A) and ~B = (U~B, v~B) be two intuitionistic fuzzy numbers (IFNs); then, the addition and multiplication procedures on these two IFNs are as follows:

~A ⊕ ~B = (U~A + U~B - U~A U~B, v~A v~B) (5.4)
~A ⊗ ~B = (U~A U~B, v~A + v~B - v~A v~B) (5.5)

## 5.2.1.2 Pythagorean Fuzzy Sets (PFSs)

In order to extend the capabilities of the IFSs, Yager created PFSs (Yager, 2013). It has two different membership degrees, which are referred to as membership and non-membership, respectively. In PFSs, the sum of the membership grade and the non-membership grade is considered; in IFSs, only the membership grade is considered. There is a possibility of having more than one membership grade and non-membership grade in PFSs. PFSs are clarified as specified in Explanation 5.3.

### Explanation 5.3:
Let Y be a constant set. A PFS ~P in Y is an object having the formula assumed by:

~P = { (Y, U_P(Y), v_P(Y)) | Y ∈ Y } (5.6)

where the function $\mathcal{U}_p: Y \to [0,1]$ designates the degree of membership of a component $Y \in Y$ to the sets $\tilde{P}$, and $\vartheta_p: Y \to [0,1]$ designates the degree of non-membership of a component $Y \in Y$ to the sets $\tilde{P}$, with the condition that:

$$0 \le (\mathcal{U}_p(Y))^2 + (\vartheta_p(Y))^2 \le 1, \text{ for } \forall \ Y \in Y \tag{5.7}$$

The degree of vagueness is calculated as follows:

$$\pi_p(Y)=\sqrt{1-\mathcal{U}_p(Y)^2-\vartheta_p(Y)^2} \tag{5.8}$$

### Explanation 5.4:
Let $\tilde{P}_1=(\mathcal{U}_{P_1},\vartheta_{P_1})$ and $\tilde{P}_2=(\mathcal{U}_{P_2},\vartheta_{P_2})$ be two Pythagorean fuzzy numbers (PFNs); then, the addition and multiplication procedures on these two PFNs are as follows:

$$\tilde{P}_1 \oplus \tilde{P}_2 = \left(\sqrt{\mathcal{U}_{P_1}^2+\mathcal{U}_{P_2}^2-\mathcal{U}_{P_1}^2\mathcal{U}_{P_2}^2},\vartheta_{P_1}\vartheta_{P_2}\right) \tag{5.9}$$

$$\tilde{P}_1 \otimes \tilde{P}_2 = \left(\mathcal{U}_{P_1}\mathcal{U}_{P_2},\sqrt{\vartheta_{P_1}^2+\vartheta_{P_2}^2-\vartheta_{P_1}^2\vartheta_{P_2}^2}\right) \tag{5.10}$$

## 5.2.1.3 q-Rung Orthopair Fuzzy Sets (q-ROFSs)

In 2018, Yager gave presentations on q-ROFSs, in which grades of membership and non-membership were given. When using q-ROFS, the sum of the q$^{th}$ powers of both the membership and non-membership grades must not be more than 1 (Yager, 2017). It is easy to see in Figure 5.1 that q-ROFSs have a membership degree extent that is much higher than that of IFSs and PFSs. q-ROFSs are clarified as specified in Explanation 5.5.

### Explanation 5.5:
A q-ROFS $\tilde{Q}$ in a finite universe of discourse $Y = Y_1,Y_2,...,Y_n$ is defined by Yager as follows (Yager, 2017):

$$\tilde{Q} = \{\left(Y,\mathcal{U}_Q(Y),\vartheta_Q(Y)\right) | Y \in Y\} \tag{5.11}$$

where the function $\mathcal{U}_Q: Y \to [0,1]$ describes the degree of membership of a component $Y \in Y$ to the sets $\tilde{Q}$, and $\vartheta_Q: Y \to [0,1]$ describes the degree of non-membership of a component $Y \in Y$ to the sets $\tilde{Q}$, with the condition that:

$$0 \le \mathcal{U}_Q(Y)^q + \vartheta_Q(Y)^q \le 1, \text{ for } \forall \ Y \in Y \tag{5.12}$$

![](img/601db3e97ac605d993053e21bf375150_173_0.png)

## FIGURE 5.1

Comparison of the geometric space of different fuzzy memberships.

The degree of vagueness is calculated as follows:

$\pi_{Q}(Y)=\sqrt[q]{1-\mathcal{U}_{Q}(Y)^{q}-\vartheta_{Q}(Y)^{q}}$ (5.13)

### Explanation 5.6:
Let $\tilde{Q}=(\mu_{Q},\vartheta_{\tilde{Q}})$, $\tilde{Q}_{1}=(\mu_{\tilde{Q}_{1}},\vartheta_{\tilde{Q}_{1}})$, and $\tilde{Q}_{2}=(\mu_{\tilde{Q}_{2}},\vartheta_{\tilde{Q}_{2}})$ be three q-ROFNs; then, their operations can be described as follows (Yager, 2017):

$\tilde{Q}_{1}\cap\tilde{Q}_{2}=(\min\{\mu_{\tilde{Q}_{1}},\mu_{\tilde{Q}_{2}}\},\max\{\vartheta_{\tilde{Q}_{1}},\vartheta_{\tilde{Q}_{2}}\})$ (5.14)
$\tilde{Q}_{1}\cup\tilde{Q}_{2}=(\max\{\mu_{\tilde{Q}_{1}},\mu_{\tilde{Q}_{2}}\},\min\{\vartheta_{\tilde{Q}_{1}},\vartheta_{\tilde{Q}_{2}}\})$ (5.15)
$\tilde{Q}_{1}\oplus\tilde{Q}_{2}=\left((\mu_{\tilde{Q}_{1}}^{q}+\mu_{\tilde{Q}_{2}}^{q}-\mu_{\tilde{Q}_{1}}^{q}\mu_{\tilde{Q}_{2}}^{q})^{\frac{1}{q}},\vartheta_{\tilde{Q}_{1}}\vartheta_{\tilde{Q}_{2}}\right)$ (5.16)
$\tilde{Q}_{1}\otimes\tilde{Q}_{2}=\left(\mu_{\tilde{Q}_{1}}\mu_{\tilde{Q}_{2}},(\vartheta_{\tilde{Q}_{1}}^{q}+\vartheta_{\tilde{Q}_{2}}^{q}-\vartheta_{\tilde{Q}_{1}}^{q}\vartheta_{\tilde{Q}_{2}}^{q})^{\frac{1}{q}}\right)$ (5.17)
$\lambda\tilde{Q}=\left((1-(1-\mu_{Q}^{q})^{\lambda})^{\frac{1}{q}},\vartheta_{Q}^{\lambda}\right),\lambda>0$ (5.18)

$\tilde{Q}^{\lambda} = \left( \mathcal{U}_{\tilde{Q}}^{\lambda}, \left(1 - \left(1 - \vartheta_{\tilde{Q}}^{q}\right)^{\lambda} \right)^{\frac{1}{q}} \right), \lambda > 0 \quad (5.19)$

### Explanation 5.7:
Let $\tilde{Q} = (\mathcal{U}_{\tilde{Q}}, \vartheta_{\tilde{Q}})$ be a q-ROFN; then, the score function S($\tilde{Q}$) of $\tilde{Q}$ can be stated by Wang et al. (2019), and accuracy function A($\tilde{Q}$) of $\tilde{Q}$ can be stated by Liu and Wang (2018) as in Eqs. (5.20) and (5.21), respectively.

S($\tilde{Q}$) = $\frac{1}{2}\left(1 + \mathcal{U}_{\tilde{Q}}^{q} - \vartheta_{\tilde{Q}}^{q}\right)$ \quad (5.20)

A($\tilde{Q}$) = $\mathcal{U}_{\tilde{Q}}^{q} + \vartheta_{\tilde{Q}}^{q}$ \quad (5.21)

### Explanation 5.8:
Let $\tilde{Q}_i = (\mathcal{U}_{\tilde{Q}_i}, \vartheta_{\tilde{Q}_i})$ (i=1, 2, ..., n) be set of q-ROFNs and $\omega = (\omega_1, \omega_2, ..., \omega_n)^T$ be weight vector of $\tilde{Q}_i$ with $\sum_{i=1}^n \omega_i = 1$ and $\omega_i \in [0,1]$. q-Rung orthopair fuzzy weighted average (q-ROFWA) and q-rung orthopair fuzzy weighted geometric (q-ROFWG) operators can be expressed by Liu and Wang (2018) as presented in Eqs. (5.22) and (5.23), respectively.

q-ROFWA($\tilde{Q}_1, \tilde{Q}_2, ..., \tilde{Q}_n$) = $\left( \left(1 - \prod_{i=1}^n \left(1 - \mathcal{U}_{\tilde{Q}_i}^q\right)^{\omega_i} \right)^{\frac{1}{q}}, \prod_{i=1}^n \vartheta_{\tilde{Q}_i}^{q \omega_i} \right)$ \quad (5.22)

q-ROFWG($\tilde{Q}_1, \tilde{Q}_2, ..., \tilde{Q}_n$) = $\left( \prod_{i=1}^n \mathcal{U}_{\tilde{Q}_i}^{\omega_i}, \left(1 - \prod_{i=1}^n \left(1 - \vartheta_{\tilde{Q}_i}^q\right)^{\omega_i} \right)^{\frac{1}{q}} \right)$ \quad (5.23)

### Explanation 5.9:
Darko and Liang (2020) established an operator called the weighted q-rung orthopair fuzzy Hamacher average (Wq-ROFHA) as presented in Eqs. (5.24) and (5.25). Let $\tilde{Q}_i = (\mathcal{U}_{\tilde{Q}_i}, \vartheta_{\tilde{Q}_i})$ (i=1, 2, ..., n) be set of q-ROFNs and $\omega = (\omega_1, \omega_2, ..., \omega_n)^T$ be weight vector of $\tilde{Q}_i$ with $\sum_{i=1}^n \omega_i = 1$ and $\omega_i \in [0,1]$.

Wq-ROFHA($\tilde{Q}_1, \tilde{Q}_2, ..., \tilde{Q}_n$) = $\omega_1(\tilde{Q}_1) \oplus \omega_2(\tilde{Q}_2) \oplus \cdots \oplus \omega_n(\tilde{Q}_n)$ \quad (5.24)
= $\bigoplus_{i=1}^n \omega_i (\tilde{Q}_i)$

Wq-ROFHA($\tilde{Q}_1, \tilde{Q}_2, ..., \tilde{Q}_n$)
$= \sqrt[q]{\frac{\prod_{i=1}^n\left(1+(\gamma-1)(\mathcal{U}_{\tilde{Q}_i})^q\right)^{\omega_i} - \prod_{i=1}^n\left(1-(\mathcal{U}_{\tilde{Q}_i})^q\right)^{\omega_i}}{\prod_{i=1}^n\left(1+(\gamma-1)(\mathcal{U}_{\tilde{Q}_i})^q\right)^{\omega_i} + (\gamma-1)\prod_{i=1}^n\left(1-(\mathcal{U}_{\tilde{Q}_i})^q\right)^{\omega_i}}}$, 
$\frac{\sqrt[q]{\gamma}\prod_{i=1}^n(\vartheta_{\tilde{Q}_i})^{\omega_i}}{\sqrt[q]{\prod_{i=1}^n\left(1+(\gamma-1)(1-(\vartheta_{\tilde{Q}_i})^q)\right)^{\omega_i} + (\gamma-1)\prod_{i=1}^n(\vartheta_{\tilde{Q}_i})^{q\omega_i}}}$ (5.25)

where $\gamma>0$, $q\ge0$.

### Explanation 5.10:
Darko and Liang (2020) developed an operator called the weighted q-rung orthopair fuzzy Hamacher geometric mean (Wq-ROFHGM) as presented in Eqs. (5.26) and (5.27). Let $\tilde{Q}_i = (\mathcal{U}_{\tilde{Q}_i}, \vartheta_{\tilde{Q}_i})$ (i=1, 2... n) be set of q-ROFNs and $\omega = (\omega_1, \omega_2, ..., \omega_n)^T$ be weight vector of $\tilde{Q}_i$ with $\sum_{i=1}^n \omega_i = 1$ and $\omega_i \in [0,1]$.

Wq-ROFHGM($\tilde{Q}_1, \tilde{Q}_2, ..., \tilde{Q}_n$) = $\omega_1(\tilde{Q}_1) \oplus \omega_2(\tilde{Q}_2) \oplus \cdots \oplus \omega_n(\tilde{Q}_n)$
$= \bigoplus_{i=1}^n \omega_i(\tilde{Q}_i)$ (5.26)

Wq-ROFHGM($\tilde{Q}_1, \tilde{Q}_2, ..., \tilde{Q}_n$) =
$\frac{\sqrt[q]{\gamma}\prod_{i=1}^n(\mathcal{U}_{\tilde{Q}_i})^{\omega_i}}{\sqrt[q]{\prod_{i=1}^n\left(1+(\gamma-1)(1-(\mathcal{U}_{\tilde{Q}_i})^q)\right)^{\omega_i} + (\gamma-1)\prod_{i=1}^n(\mathcal{U}_{\tilde{Q}_i})^{q\omega_i}}}$, 
$\frac{\sqrt[q]{\prod_{i=1}^n\left(1+(\gamma-1)(\vartheta_{\tilde{Q}_i})^q\right)^{\omega_i} - \prod_{i=1}^n\left(1-(\vartheta_{\tilde{Q}_i})^q\right)^{\omega_i}}}{\sqrt[q]{\prod_{i=1}^n\left(1+(\gamma-1)(\vartheta_{\tilde{Q}_i})^q\right)^{\omega_i} + (\gamma-1)\prod_{i=1}^n\left(1-(\vartheta_{\tilde{Q}_i})^q\right)^{\omega_i}}}$ (5.27)

where $\gamma>0$, $q\ge0$.
