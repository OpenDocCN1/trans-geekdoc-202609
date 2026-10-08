
**Theorem 5.4.7.** If \( \text{T}' \in \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \) and for each \( u \in U \), \( \text{T}'(\mathbb{H}_\mathbb{G}) \in \mathcal{F}(\mathbb{H}_\mathbb{G}) \), then \( \mathcal{F}\mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \subseteq \mathcal{F}(\mathbb{H}_\mathbb{G}) \).

**Theorem 5.4.8.** \( \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \) is sectionally elementary.

*Proof:* Let \( \mathcal{F}(\mathcal{T}\sigma(\mathbb{H}_\mathbb{G})) = \{y_1, y_2, \dots, y_p; z_1, z_2, \dots, z_k\} \). Assume that \( \text{T}' \in \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \) and some \( \alpha, \beta \in (y_p, z_i) \) such that \( \text{T}^{(y_i, z_i)} \subset \text{T}^{(\alpha, \beta)} \). Since \( \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}^{(y_i, z_i)}) = \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}^{(\alpha, \beta)}) \) \(\ni\) some \( \mathcal{A} \in \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \supseteq \mathcal{A}^{(y_i, z_i)} = \text{T}^{(\alpha, \beta)} \). Then \( \text{T}^{(\alpha, \beta)} \subset \mathcal{A}^{(y_i, z_i)} \) implies the IFS \( U(u_i) \) defined by

\[ U(u_i) = \begin{cases} (\alpha, \beta) \text{ if } u_i \in \mathcal{A}^{(y_i, z_i)} \setminus \text{T}^{(y_i, z_i)} \\ \mathcal{A} \text{ otherwise} \end{cases} \]

is an IFT of IFTHG. Here \( \text{U} < \mathcal{A} \), \(\Leftrightarrow\) minimality of \( \mathcal{A} \), which is a contradiction.

**Theorem 5.4.9.** For each \( \mathcal{A} \in \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \), \( \mathcal{A}^{(y_1, z_2)} \) is a minimal IFT of \( \mathbb{H}_\mathbb{G}^{(y_1, z_2)} \).

*Proof:* For every IFTHG \( \mathbb{H}_\mathbb{G} = (U, \varepsilon; s_1, s_2) \), consider a minimal IFT \( \text{T} \) of \( \mathbb{H}_\mathbb{G}^{(y_1, z_2)} \) such that \( \text{T} \subset \mathcal{A}^{(y_1, z_2)} \). Define the intuitionistic fuzzy set \( U(u_i) \) where

\[ U(u_i) = \begin{cases} (y_2, z_2) \text{ if } u_i \in \mathcal{A}^{(y_1, z_1)} \setminus \text{T} \\ \mathcal{A} \text{ otherwise} \end{cases} \]

By the above theorem, \( U \) is an IFT of IFTHG, contradicting the minimality of \( \mathcal{A} \).

**Definition 5.4.10.** Let IFTHG be \( \mathbb{H}_\mathbb{G} = (U, \varepsilon; s_1, s_2) \). The intuitionistic fuzzy transversal core (IFTC) of \( \mathbb{H}_\mathbb{G} \) is an IFTHG \( \mathbb{H}'_\mathbb{G} = (U', \varepsilon'; s_1, s_2) \) then

1. \( \bigwedge \mathcal{T}\sigma(\mathbb{H}'_\mathbb{G}) = \bigwedge \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \),
2. \( U \cup \mathcal{T}\sigma(\mathbb{H}'_\mathbb{G}) = \mathbb{H}'_\mathbb{G} \),
3. \( \varepsilon/\varepsilon' \) is completely the set containing vertices of \( \mathbb{H}_\mathbb{G} \notin \mathcal{T}\sigma(\mathbb{H}_\mathbb{G}) \), and
4. an independent set \( V \subseteq U \) has a set of all different combinations of a nonadjacent vertices in \( \mathbb{H}_\mathbb{G} \) \(\Leftrightarrow\) \(\exists\) a threshold values \( s_1 \) & \( s_2 > 0 \) such that \( \sum_{u_i \in V} \mu_{y_i}(u_i) \leq s_1 \) and \( \sum_{u_i \in V} (1 - \nu_y(u_i)) \leq s_2 \).

**Definition 5.4.11.** Consider an IFTHG with \( U = \{u_1, u_2, u_3, u_4, u_5, u_6\} \), \( \varepsilon = \{\varepsilon_1, \varepsilon_2, \varepsilon_3, \varepsilon_4, \varepsilon_5\} \), where, \( \varepsilon_1 = \{u_1 \langle 0.3, 0.4 \rangle, u_6 \langle 0.4, 0.6 \rangle\} \), \( \varepsilon_2 = \{u_1 \langle 0.3, 0.4 \rangle, u_2 \langle 0.4, 0.5 \rangle, u_4 \langle 0.3, 0.6 \rangle, u_6 \langle 0.4, 0.6 \rangle\} \), \( \varepsilon_3 = \{u_1 \langle 0.3, 0.4 \rangle, u_3 \langle 0.2, 0.6 \rangle, u_4 \langle 0.3, 0.6 \rangle, u_5 \langle 0.2, 0.7 \rangle, u_6 \langle 0.4, 0.5 \rangle\} \), \( \varepsilon_4 = \{u_3 \langle 0.2, 0.6 \rangle, u_5 \langle 0.2, 0.7 \rangle, u_7 \langle 0.4, 0.6 \rangle\} \), and \( \varepsilon_5 = \{u_2 \langle 0.4, 0.5 \rangle, u_6 \langle 0.4, 0.6 \rangle\} \), as shown in Figure 5.3.

![](img/e9de70cd491e84262133af63cb33d500_84_0.png)

**FIGURE 5.3** IFT HG ( $\mathbb{H}_{\mathbb{G}}$ , $\eth$ )

The associated incidence matrix for $\mathbb{H}_{\mathbb{G}}$ is given as

| | $\mathcal{E}_1$ | $\mathcal{E}_2$ | $\mathcal{E}_3$ | $\mathcal{E}_4$ | $\mathcal{E}_5$ |
|---|---|---|---|---|---|
| $u_1$ | $\langle0.3,0.4\rangle$ | $\langle0.3,0.4\rangle$ | $\langle0.3,0.4\rangle$ | $\langle0,1\rangle$ | $\langle0,1\rangle$ |
| $u_2$ | $\langle0,1\rangle$ | $\langle0.4,0.5\rangle$ | $\langle0,1\rangle$ | $\langle0,1\rangle$ | $\langle0.4,0.5\rangle$ |
| $u_3$ | $\langle0,1\rangle$ | $\langle0,1\rangle$ | $\langle0.2,0.6\rangle$ | $\langle0.2,0.6\rangle$ | $\langle0,1\rangle$ |
| $u_4$ | $\langle0,1\rangle$ | $\langle0.3,0.6\rangle$ | $\langle0.3,0.6\rangle$ | $\langle0,1\rangle$ | $\langle0,1\rangle$ |
| $u_5$ | $\langle0,1\rangle$ | $\langle0,1\rangle$ | $\langle0.2,0.7\rangle$ | $\langle0,1\rangle$ | $\langle0,1\rangle$ |
| $u_6$ | $\langle0.4,0.6\rangle$ | $\langle0.4,0.6\rangle$ | $\langle0.4,0.6\rangle$ | $\langle0.4,0.6\rangle$ | $\langle0.4,0.6\rangle$ |

The incidence matrix of IFTC $\mathbb{H}_{\mathbb{G}}'$ is given as

| | $\mathcal{E}_1$ | $\mathcal{E}_2$ |
|---|---|---|
| $u_1$ | $(0.3,0.4)$ | $(0.3,0.4)$ |
| $u_2$ | $(0.4,0.5)$ | $(0,1)$ |
| $u_3$ | $(0,1)$ | $(0.2,0.6)$ |
| $u_4$ | $(0.3,0.6)$ | $(0.3,0.6)$ |
| $u_5$ | $(0,1)$ | $(0.2,0.7)$ |
| $u_6$ | $(0.4,0.6)$ | $(0.4,0.6)$ |

The transversal core of IFTGH is given in Figure 5.4.

![](img/e9de70cd491e84262133af63cb33d500_85_0.png)

**Result:**

1. The transversal core exists and is unique for any IFTGH no spike hyperedges.
2. This definition also holds for IFTGHs among spike (a hyperedge including one vertex) hyperedges.

**Definition 5.4.12.** *The open neighborhood* for the minimal transversal on IFTGH of the vertex $u_i$ is the set containing nearest vertices of $u_i$ except itself in a hyperedge and is represented as $\mathcal{N}_{h}(u_i)$.

**Example 5.4.13.** Consider an IFTGH with $U = \{u_1, u_2, u_3, u_4, u_5, u_6, u_7\}$, $\mathcal{E} = \{\mathcal{E}_1, \mathcal{E}_2, \mathcal{E}_3, \mathcal{E}_4, \mathcal{E}_5\}$ where $\mathcal{E}_1 = \{u_1\langle 0.3, 0.4\rangle, u_7\langle 0.4, 0.6\rangle\}$, $\mathcal{E}_2 = \{u_2\langle 0.2, 0.6\rangle, u_7\langle 0.4, 0.6\rangle\}$, $\mathcal{E}_3 = \{u_2\langle 0.2, 0.6\rangle, u_4\langle 0.5, 0.3\rangle\}$, $\mathcal{E}_4 = \{u_2\langle 0.4, 0.3\rangle, u_4\langle 0.5, 0.3\rangle, u_7\langle 0.4, 0.6\rangle\}$, $\mathcal{E}_5 = \{u_3\langle 0.2, 0.5\rangle, u_6\langle 0.3, 0.6\rangle, u_7\langle 0.4, 0.6\rangle\}$.

Here, $u_2$ and $u_7$ are the open neighborhood of the vertex $u_1$ in $\top_1$.

**Definition 5.4.14.** The *closed neighborhood* for the minimal transversal on IFTHG of the vertex $u_i$ is the set containing nearest vertices of $u_i$ including the vertex in a hyperedge and is represented as $\mathcal{N}'_h(u_i)$.

**Example 5.4.15.** From the above example, it is shown that the closed neighborhood of the vertex $u_1$ is $u_1$, $u_2$ and $u_7$, in $T_1$.

**Theorem 5.4.16.** If $\mathbb{H}_{\G} = \langle U, \varepsilon, s_1, s_2\rangle$ be an IFTHG, then the given conditions are similar

1. T is an IFT of IFTHG.
2. $\operatorname{T}^{(v_{i}z_{j})} \cap \mathcal{A}^{(v_{i}z_{j})} \neq \varnothing$, for each IF hyperedge $\mathcal{A} \in \varepsilon$ and each $\langle y_{i}z_{j}\rangle$ with $0 < y_{i} \leq \underline{h}_{\mu}\left(\mathbb{H}_{\G}\right)$, $0 < z_{j} \leq \underline{h}_{\nu}\left(\mathbb{H}_{\G}\right)$.
3. $\operatorname{T}^{(v_{i}z_{j})}$ is an IFT of $\mathbb{H}_{\G}^{(v_{i}z_{j})}$, for each $\langle y_{i}z_{j}\rangle$ with $0 < y_{i} \leq \alpha$, $0 < z_{j} \leq \beta$.

*Proof:* By definition, “A minimal IFT T for IFTHG is a transversal of $\mathbb{H}_{\G}$ which satisfies the property that if $T_1 \subset T$, then $T_1$ is not an IFT of $\mathbb{H}_{\G}$” the proof is trivial.

**Theorem 5.4.17.** For a simple IFTHG $\mathbb{H}_{\G}$, $T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G})) = \mathbb{H}_{\G}$.

**Theorem 5.4.18.** For any IFTHG $\mathbb{H}_{\G}$, $T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G})) \subseteq \mathbb{H}_{\G}$.

*Proof:* From Definition 5.4.10, $\exists$ a partial IFTHG $\mathbb{H}_{\G}^{'}$ of a simple IFTHG $\mathbb{H}_{\G}$, $\exists T\mathfrak{H}(\mathbb{H}_{\G}^{'}) = T\mathfrak{H}(\mathbb{H}_{\G})$. By Theorem 5.4.17, $T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G})) = T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G}^{'}) = \mathbb{H}_{\G}^{'} \subseteq \mathbb{H}_{\G}$.

**Theorem 5.4.19.** Let $\mathbb{H}_{\G} = \langle U, \varepsilon, s_1, s_2\rangle$ be an IFTHG and assume

T $\in T\mathfrak{H}(\mathbb{H}_{\G})$. If $\mathbb{H}_{\G}^{'} \subseteq supp(T) \subseteq \mathbb{H}_{\G}$, then $\exists$ an IF threshold hyperedge $\mathcal{A}$, $\langle y_{i}z_{j}\rangle \in \mathcal{A}$ represent the membership and nonmembership values of $\mathcal{A} \supseteq$

1. $\langle y_{p}z_{q}\rangle = \underline{h}_{t}(\mathcal{A}) = \underline{h}_{t}\left(T^{(v_{i}z_{j})}\right) > 0$.
2. $\mathrm{T}_{\underline{h}_{t}(\mathcal{A})} \cap \mathcal{A}_{\underline{h}_{t}(\mathcal{A})} = \mathbb{H}_{\G}$.

*Proof:* Assume $0 < \underline{h}_{t}\left(T^{(v_{i}z_{j})}\right) \leq 1$ & suppose $\varepsilon^{'}$ be the set of IF threshold hyperedges where $\underline{h}_{t}(\mathcal{A}^{(v_{i}z_{j})}) \geq \underline{h}_{t}\left(T^{(v_{i}z_{j})}\right)$ for each $\tau \in \varepsilon^{'}$ for which $\sum_{u_{i} \in U} \mu_{ij}\left(u_{i}\right) \leq s_{1}$ and $\sum_{u_{i} \in U}\left(1 - \nu_{ij}\left(u_{i}\right)\right) \leq s_{2}$, $\forall 1 \leq i \leq m$, $1 \leq j \leq n$.

Since $\mathrm{T}^{(v_{i}z_{j})}$ is an IFT of $\mathbb{H}_{\G}^{(v_{i}z_{j})}$ and $\mathbb{H}_{\G}^{'} \subseteq \mathrm{T}^{(v_{i}z_{j})}$ is nonempty. Further, for each $\tau \in \varepsilon^{'}$, $\underline{h}_{t}(\tau) \geq \left(T^{(v_{i}z_{j})}\right)$ is true. In addition, suppose that $\mathrm{T}^{(v_{i}z_{j})}$ is the minimal IFT, then for each $\tau \in \varepsilon^{'}$, $\underline{h}_{t}(\tau) \geq \left(T^{(v_{i}z_{j})}\right)$ and there exists $\mathbb{H}_{\G^{'}t} \neq \mathbb{H}_{\G}$ with $\mathbb{H}_{\G^{'}t} \in \tau_{\underline{h}_{t}(\tau)} \cap T_{\underline{h}_{t}(\tau)}$.

Define an IFTHG $\mathbb{H}_{\G^{1}} \supseteq$
