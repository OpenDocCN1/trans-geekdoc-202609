# 17 Appendix

# 17.1 Topological group

**Definition 17.1.** A topological group is a set $G$ with the following properties:

(1) $G$ is a group;

(2) $G$ is a Hausdorff space;

(3) the mapping $(x, y) \to xy^{-1}$ of $G \times G$ to $G$ is connected;

Property (3) represents the group structure compatible with the topological structure of $G$. It can be written as follows:

(4) $(x, y) \to xy^{-1}, x \to x^{-1}$ are the continuous mappings of $G \times G$ to $G, G$ to $G$, respectively.

**Definition 17.2.** Let $G$ be a topological group. For any $g \in G$, called the mapping of $G$ to $G$,

$$L_g: x \to gx, \quad \forall x \in G \,,$

$$R_g: x \to xg, \quad \forall x \in G \,,$

respectively, are the left transformation and right transformation of $G$.

Obviously, the following four properties are established.

$$(L_g)^{-1} = L_{g^{-1}} \,, \quad (R_g)^{-1} = R_{g^{-1}} \,,$

$L_g, R_g$, and mapping $x \to x^{-1}$ are all homeomorphic mappings of $G$.

$adg = L_g R_g:$ is the self-homeomorphic mapping of $G$, and $\forall x \in G, adg(x) = gxg^{-1}$.

For any natural number $n$, the mapping $(x_1, x_2, \dots, x_n) \to x_1x_2 \dots x_n$ is the continuous mapping of $\underset{n}{\underbrace{G \times G \times \dots \times G}}$.

**Theorem 17.1.** Let $e$ be the unit of topological group $G$. Then, there is the basic neighbourhood group $U$ of $e$, which fits the following conditions:

(1) $V_1, V_2 \in U$, then $V_1 \cap V_2 \in U$;

(2) $V \in U$, while $W \supset V$, then $W \in U$;

(3) $\underset{V \in U}{\cap} V = \{e\}$;

(4) $\forall V \in U, \exists V_1 \in U$, making $V_1 V_1^{-1} \le V$;

(5) $\forall V \in U, a \in G$, then $aVa^{-1} \in U$.

By contrast, given a group $G$ and a set of $U$ containing $e$ satisfying the above five conditions, $G$ can be uniquely defined as a topological group. Let $U$ be the basic neighbourhood group of $e$.

Let $G$ be a topological group, $H$ be a subgroup, and $o$ be the open family of $G$. Then, the subset family $O_H = \{O \cap H | O \in o\}$ of $H$ satisfies the open set theorem. Thus, introduce the topology in $H$, becoming the induced topology of topological group $G$ in $H$. It is easy to prove, with the topology on it, that $H$ is a topological group.