As a special case of Equation 3.18 for the graphical model in Figure 3.3, the corresponding probability may be written as P(A₁, A₂, A₃, A₄) = P(A₁ | A₂)P(A₂)P(A₃ | A₁, A₂)P(A₄). Valid probability distributions lead to directed acyclic graphs. Graphs are acyclic if you follow a path of arrows and can never return to nodes you started from. An ancestor of a node is any node that is its parent, parent of its parent, parent of its parent of its parent, and so on recursively.

From the small and simple graph structure in Figure 3.3, it is clear that the loan approval depends on both income and employment status. Income depends on employment status. Gender is independent of everything else. Making independence statements is more difficult in larger and more complicated graphs, however. Determining all of the different independence relationships among all the events or random variables is done through the concept of d-separation: a subset of nodes S₁ is independent of another subset of nodes S₂ conditioned on a third subset of nodes S₃ if S₃ d-separates S₁ and S₂. One way to explain d-separation is through the three different motifs of three nodes each shown in Figure 3.4, known as a causal chain, common cause, and common effect. The differences among the motifs are in the directions of the arrows. The configurations on the left have no node that is being conditioned upon, i.e. no node’s value is observed. In the configurations on the right, node A₃ is being conditioned upon and is thus shaded. The causal chain and common cause motifs without conditioning are connected. The causal chain and common cause with conditioning are separated: the path from A₁ to A₂ is blocked by the knowledge of A₃. The common effect motif without conditioning is separated; in this case, A₃ is known as a collider. Common effect with conditioning is connected; moreover, conditioning on any descendant of A₃ yields a connected path between A₁ and A₂. Finally, a set of nodes S₁ and S₂ is d-separated conditioned on a set of nodes S₃ if and only if each node in S₁ is separated from each node in S₂.¹⁰

causal chain

common cause

common effect

![](bbox=[0.3, 0.58, 0.92, 0.86])

Figure 3.4. Configurations of nodes and edges that are connected and separated. Nodes colored gray have been observed. Accessible caption. The causal chain is A₁ → A₃ → A₂; it is connected when A₃ is unobserved and separated when A₃ is observed. The common cause is A₁ ← A₃ → A₂; it is connected when A₃ is unobserved and separated when A₃ is observed. The common effect is A₁ → A₃ ← A₂; it is separated when A₃ is unobserved and connected when A₃ or any of its descendants are observed.

¹⁰There may be dependence not captured in the structure if one random variable is a deterministic function of another.