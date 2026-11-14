messages may circulate indefinitely around the loops and the process may not converge to a stable equilibrium ... Such oscillations do not normally occur in probabilistic networks ... which tend to bring all messages to some stable equilibrium as time goes on. However, this asymptotic equilibrium is not coherent, in the sense that it does not represent the posterior probabilities of all nodes of the network. — [Pea88, p.195]

Despite these reservations, Pearl advocated the use of belief propagation in loopy networks as an approximation scheme (J. Pearl, personal communication). [MWJ99] found empirically that it works on various graphical models, and it is now used in many real world applications, some of which we discuss below. In addition, there is now some theory justifying its use in certain cases, as we discuss below. (For more details, see e.g., [Yed11.])

# 9.4.1 Loopy BP for pairwise undirected graphs

In this section, we assume (for notational simplicity) that our model is an undirected pairwise PGM, as in Equation (9.50). However, unlike Section 9.3.2, we do not assume the graph is a tree. We can apply the same message passing equations as before. However, since there is no natural node ordering, we will do this in a parallel, asynchronous way. The basic idea is that all nodes receive messages from their neighbors in parallel, they then update their belief states, and finally they send new messages back out to their neighbors. This message passing process repeats until convergence. This kind of computing architecture is called a systolic array, due to its resemblance to a beating heart.

More precisely, we initialize all messages to the all 1's vector. Then, in parallel, each node absorbs messages from all its neighbors using

```
bel_s(z_s) \propto \psi_s(z_s) \prod_{t \in nbr_s} m_{t \to s}(z_s) \qquad (9.66)
```

Then, in parallel, each node sends messages to each of its neighbors:

```
m_{s \to t}(z_t) = \sum_{z_s} \left( \psi_s(z_s)\psi_{st}(z_s, z_t) \prod_{u \in nbr_s \backslash t} m_{u \to s}(z_s) \right) \qquad (9.67)
```

The \(m_{s \to t}\) message is computed by multiplying together all incoming messages, except the one sent by the recipient, and then passing through the \(\psi_{st}\) potential. We continue this process until convergence. If the graph is a tree, the method is guaranteed to converge after \(D(G)\) iterations, where \(D(G)\) is the diameter of the graph, that is, the largest distance between any two nodes.

# 9.4.2 Loopy BP for factor graphs

To implement loopy BP for general graphs, including those with higher-order clique potentials (beyond pairwise), it is useful to use a factor graph representation described in Section 4.6.1. In this section, we summarize the BP equations for the bipartite version of factor graphs, as derived in [KFL01]. For a version that works for Forney factor graphs, see [Loe+07].

3. For an efficient JAX implementation of these equations for discrete factor graphs, see https://github.com/vicariousinc/PGMax. For the Gaussian case, see https://github.com/probml/pgml-jax.