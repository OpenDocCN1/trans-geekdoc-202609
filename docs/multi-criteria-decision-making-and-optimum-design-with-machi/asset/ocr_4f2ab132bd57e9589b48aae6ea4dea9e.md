(iii) The proof is obvious.

(iv) Since $\mathcal{M}_{\gamma}(p) \ge \mathcal{Q}_{\gamma}(p) \le \mathcal{L}_{\gamma}(p), \mathcal{M}_{\gamma}(p) \le \mathcal{Q}_{\gamma}(p)$ and
$\mathcal{M}_{\gamma}(p) \ge \mathcal{Q}_{\gamma}(p) \ge \mathcal{L}_{\gamma}(p)$,
Rightarrow |\mathcal{M}_{\gamma}(p) - \mathcal{L}_{\gamma}(p)| \le |\mathcal{M}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)|$
$|\mathcal{M}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)| \ge |\mathcal{M}_{\gamma}(p) - \mathcal{L}_{\gamma}(p)|$ and
$mathcal{M}_{\gamma}(p) - \mathcal{L}_{\gamma}(p)| \ge |\mathcal{M}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)|$. Hence
$|\mathcal{L}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)| \le |\mathcal{M}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)|, |\mathcal{L}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)| \le |\mathcal{M}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)|$

Therefore, $	ext{TAN\_S}(\mathcal{M}, \mathcal{Q}) \le 	ext{TAN\_S}(\mathcal{M}, \mathcal{L})$ and
$	ext{TAN\_S}(\mathcal{M}, \mathcal{Q}) \ge 	ext{TAN\_S}(\mathcal{L}, \mathcal{Q})$.

Let $\mathcal{M}$ and $\mathcal{L}$ be any two $	ext{SPH}_N, 	ext{S}_s$ on $\mathbb{X}$. Then

# **Theorem 2.5.2** $0 \le 	ext{COS\_S}(\mathcal{M}, \mathcal{L}) \le 1$

+   (i) $0 \le 	ext{COS\_S}(\mathcal{M}, \mathcal{L}) \le 1$
(ii) $	ext{COS\_S}(\mathcal{M}, \mathcal{L}) = 1$ if and only if $\mathcal{M} = \mathcal{L}$
(iii) $	ext{COS\_S}(\mathcal{M}, \mathcal{L}) = 	ext{COS\_S}(\mathcal{L}, \mathcal{M})$
(iv) If $\mathcal{Q}$ is a $	ext{SPH}_N$ in $\mathbb{X}$ and $\mathcal{M} \subseteq \mathcal{Q} \subseteq \mathcal{L}$, then $	ext{COS\_S}(\mathcal{M}, \mathcal{Q}) \le 	ext{COS\_S}(\mathcal{M}, \mathcal{L})$ and $	ext{COS\_S}(\mathcal{M}, \mathcal{Q}) \le 	ext{COS\_S}(\mathcal{L}, \mathcal{Q})$

Let $\mathcal{M}$ and $\mathcal{L}$ be any two $	ext{SPH}_N, 	ext{S}_s$ on $\mathbb{X}$. Then

# **Theorem 2.5.3** $0 \le 	ext{COT\_S}(\mathcal{M}, \mathcal{L}) \le 1$

+   (i) $	ext{COT\_S}(\mathcal{M}, \mathcal{L}) \le 1$
(ii) $	ext{COT\_S}(\mathcal{M}, \mathcal{L}) = 1$ if and only if $\mathcal{M} = \mathcal{L}$
(iii) $	ext{COT\_S}(\mathcal{M}, \mathcal{L}) = 	ext{COT\_S}(\mathcal{L}, \mathcal{M})$
(iv) If $\mathcal{Q}$ is a $	ext{SPH}_N$ in $\mathbb{X}$ and $\mathcal{M} \subseteq \mathcal{Q} \subseteq \mathcal{L}$, then $	ext{COT\_S}(\mathcal{M}, \mathcal{Q}) \le 	ext{COT\_S}(\mathcal{M}, \mathcal{L})$ and $	ext{COT\_S}(\mathcal{M}, \mathcal{Q}) \le 	ext{COT\_S}(\mathcal{L}, \mathcal{Q})$.

# 15.3 THE DECISION-MAKING ALGORITHM

Let $\mathcal{A} = \{\mathcal{A}_1, \mathcal{A}_2, \dots, \mathcal{A}_n\}$ be the collection of persons, $\mathcal{C} = \{\mathcal{C}_1, \mathcal{C}_2, \dots, \mathcal{C}_m\}$ be the set of criteria for each person, and $\mathcal{B} = \{\mathcal{B}_1, \mathcal{B}_2, \dots, \mathcal{B}_l\}$ be the family of alternatives of persons.

**Step 1**: Estimate the connection between persons and attributes ($\mathfrak{R}_1$)

The connections between person $\mathcal{A}_j$ ($j=1, 2, \dots$) and attribute $\mathcal{C}_k$ ($k=1, 2, \dots, n$) are given in Table 15.1 in terms of SNSs.

**Step 2**: Find the association between attributes and alternatives ($\mathfrak{R}_2$)

$\mathfrak{R}_2$ can be represented in the form of decision Table 15.2 based on the SNSs.

**Step 3**: Calculate the trigonometric similarity measures

Use the code in Python to calculate the different trigonometric similarity measures between $\mathfrak{R}_1$ and $\mathfrak{R}_2$ based on Section 15.2.4; the measures are presented in Table 15.3.