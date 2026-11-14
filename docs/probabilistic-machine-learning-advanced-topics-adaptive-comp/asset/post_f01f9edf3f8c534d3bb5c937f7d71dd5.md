
combining the incoming messages from all its children with its own local evidence:

\(bel_s(z_s) \propto \psi_s(z_s) \prod_{t \in ch_s} m_{t \to s}(z_s)\) (9.58)

To compute the outgoing message that s should send to its parent t, we pass the local belief through the pairwise potential linking s and t, and then marginalize out s to get

\(m_{s \to t}(z_t) = \sum_{z_s} \psi_{st}(z_s, z_t) bel_s(z_s)\) (9.59)

At the root of the tree, bel_t(z_t) = p(z_t | y) will have seen all the evidence. It can then send messages back down to the leaves. The message that s sends to its child t should be the product of all the messages that s received from all its other children u, passed through the pairwise potential, and then marginalized:

\(m_{s \to t}(z_t) = \sum_{z_s} \left( \psi_s(z_s) \psi_{st}(z_s, z_t) \prod_{u \in ch_s \setminus t} m_{u \to s}(z_s) \right)\) (9.60)

See Figure 9.9. Instead of multiplying all-but-one of the messages that s has received, we can multiply all of them and then divide out by the t → s message from child t. The advantage of this is that the product of all the messages has already been computed in Equation (9.58), so we don't need to recompute that term. Thus we get

\(m_{s \to t}(z_t) = \sum_{z_s} \psi_{st}(z_s, z_t) \frac{bel_s(z_s)}{m_{t \to s}(z_s)}\) (9.61)

We can think of bel_s(z_s) as the new updated posterior p(z_s | y) given all the evidence, and m_{t → s}(z_s) as the prior predictive p(z_s | y_t^-), where y_t^- is all the evidence in the subtree rooted at t. Thus the ratio contains the new evidence that t did not already know about from its own subtree. We use this to update the belief state at node t to get:

\(bel_t(z_t) \propto bel_t(z_t) m_{s \to t}(z_t)\) (9.62)

(Note that Equation (9.58) is a special case of this where we don't divide out by m_{s → t}, since in the upwards pass, there is no incoming message from the parent.) This is analogous to the backwards smoothing equation in Equation (9.37), with \alpha_t(i) replaced by bel_t(z_t = i), A(i,j) replaced by \psi_{st}(z_s = i, z_t = j), \gamma_{t+1}(j) replaced by bel_s(z_s = j), and \alpha_{t+1|t}(j) replaced by m_{t \to s}(z_s = j).

See Figure 9.8 for the overall pseudocode. This can be generalized to directed trees with multiple root nodes (known as polytrees) as described in Supplementary Section 9.1.1.

## 9.3.3 Max-product algorithm

In Section 9.3.2 we described the sum-product algorithm, that computes the posterior marginals:

\(bel_i(k) = \gamma_i(k) = p(z_i = k | y) = \sum_{z_{-i}} p(z_i = k, z_{-i} | y)\) (9.63)

We can replace the sum operation with the max operation to get **max-product belief propagation**. The result of this computation are a set of **max marginals** for each node:

```
\zeta_i(k) = \max_{\mathbf{z}_{\neg i}} p(z_i = k, \mathbf{z}_{\neg i} | \mathbf{y}) \quad (9.64)
```

### 9.3.3.1 Connection between MMM and MAP

In [YW04], they showed that, if the max marginals are unique and computed exactly (e.g., if the graph is a tree), then \(\tilde{\mathbf{z}} = \mathbf{z}^*\). This means we can recover the global MAP estimate by running max product BP and then setting each node to its local max (i.e., using the MMM estimate). However, if there are ties in the max marginals (corresponding to the case where there is more than one globally optimal solution), this “local stitching” process may result in global inconsistencies. If we have a tree-structured model, we can use a **traceback** procedure, analogous to the Viterbi algorithm (Section 9.2.6), in which we clamp nodes to their optimal values while working backwards from the root. For details, see e.g., [KF09a, p569]. Unfortunately, backtrace does not work on general graphs. An alternative, iterative approach, proposed in [YW04], is follows. First we run max product BP, and clamp all nodes which have unique max marginals to their optimal values; we then clamp a single ambiguous node to an optimal value, and condition on all these clamped values as extra evidence, and perform more rounds of message passing, until all ties are broken. This may require many rounds of inference, although the number of non-clamped (hidden) variables gets reduced at each round.

### 9.3.3.2 Connection between MPM and MAP

In this section, we discuss the MPM estimate, \(\hat{\mathbf{z}}\), which computes the maximum of the posterior marginals. In general, this does not correspond to the MAP estimate, even if the posterior marginals are exact. To see why, note that MPM just looks at the belief state for each node given all the visible evidence, but ignores any dependencies or constraints that might exist in the prior. To illustrate why this could be a problem, consider the error correcting code example from Section 5.5, where we defined \(p(\mathbf{z}, \mathbf{y}) = p(z_1)p(z_2)p(z_3|z_1, z_2) \prod_{i=1}^3 p(y_i|z_i)\), where all variables are binary. The priors \(p(z_1)\) and \(p(z_2)\) are uniform. The conditional term \(p(z_3|z_1, z_2)\) is deterministic, and computes the parity of \((z_1, z_2)\). In particular, we have \(p(z_3 = 1|z_1, z_2) = \mathbb{I}(\text{odd}(z_1, z_2))\), so that the total number of 1s in the block \(\mathbf{z}_{1:3}\) is even. The likelihood terms \(p(y_i|z_i)\) represent a bit flipping noisy channel model, with noise level \(\alpha = 0.2\). Suppose we observe \(\mathbf{y} = (1, 0, 0)\). In this case, the exact posterior marginals are as follows:$^2 \gamma_1 = [0.3469, 0.6531], \gamma_2 = [0.6531, 0.3469], \gamma_3 = [0.6531, 0.3469]$. The exact max marginals are all the same,

2. See error_correcting_code_demo.ipynb for the code.

namely \(\zeta_i = [0.3265, 0.3265]\). Finally, the 3 global MAP estimates are \(\boldsymbol{z}^* \in \{[0, 0, 0], [1, 1, 0], [1, 0, 1]\}\), each of which corresponds to a single bit flip from the observed vector. The MAP estimates are all valid code words (they have an even number of 1s), and hence are sensible hypotheses about the value of \(\boldsymbol{z}\). By contrast, the MPM estimate is \(\hat{\boldsymbol{z}} = [1, 0, 0]\), which is not a legal codeword. (And in this example, the MMM estimate is not well defined, since the max marginals are not unique.)

So, which method is better? This depends on our loss function, as we discuss in Section 34.1. If we want to minimize the prediction error of each \(z_i\), also called bit error, we should compute the MPM. If we want to minimize the prediction error for the entire sequence \(\boldsymbol{z}\), also called word error, we should use MAP, since we can take global constraints into account.

For example, suppose we are performing speech recognition and someone says "recognize speech". MPM decoding may return "wreck a nice beach", since locally it may be that "beach" is the most probable interpretation of "speech" when viewed in isolation (see Figure 34.3). However, MAP decoding would infer that "recognize speech" is the more likely overall interpretation, by taking into account the language model prior, \(p(\boldsymbol{z})\).

On the other hand, if we don't have strong constraints, the MPM estimate can be more robust [MMP87; SM12], since it marginalizes out the other nodes, rather than maxing them out. For example, in the casino HMM example in Figure 9.3, we see that the MPM method makes 49 bit errors (out of a total possible of \(T = 300\)), and the MAP path makes 60 errors.

### 9.3.3.3 Connection between MPE and MAP

In the graphical models literature, computing the jointly most likely setting of all the latent variables, \(\boldsymbol{z}^* = \arg \max_{\boldsymbol{z}} p(\boldsymbol{z}|\boldsymbol{y})\), is known as the most probable explanation or MPE [Pea88]. In that literature, the term "MAP" is used to refer to the case where we maximize some of the hidden variables, and marginalize (sum out) the rest. For example, if we maximize a single node, \(z_i\), but sum out all the others, \(\boldsymbol{z}_{-i}\), we get the MPM \(\hat{z}_i = \arg \max_{z_i} \sum_{\boldsymbol{z}_{-i}} p(\boldsymbol{z}|\boldsymbol{y})\).

We can generalize the MPM estimate to compute the best guess for a set of query variables \(Q\), given evidence on a set of visible variables \(V\), marginalizing out the remaining variables \(R\), to get

```
\(\boldsymbol{z}_Q^* = \arg \max_{\boldsymbol{z}_Q} \sum_{\boldsymbol{z}_R} p(\boldsymbol{z}_Q, \boldsymbol{z}_R | \boldsymbol{z}_V)\) (9.65)
```

(Here \(\boldsymbol{z}_R\) are called nuisance variables, since they are not of interest, and are not observed.) In [Pea88], this is called a MAP estimate, but we will call it an MPM estimate, to avoid confusion with the ML usage of the term "MAP" (where we maximize everything jointly).

## 9.4 Loopy belief propagation

In this section, we extend belief propagation to work on graphs with cycles or loops; this is called loopy belief propagation or LBP. Unfortunately, this method may not converge, and even if it does, it is not clear if the resulting estimates are valid. Indeed, Judea Pearl, who invented belief propagation for trees, wrote the following about loopy BP in 1988:

> When loops are present, the network is no longer singly connected and local propagation schemes will invariably run into trouble ... If we ignore the existence of loops and permit the nodes to continue communicating with each other as if the network were singly connected,
