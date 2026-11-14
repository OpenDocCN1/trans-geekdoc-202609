combining the incoming messages from all its children with its own local evidence:

\(bel_s(z_s) \propto \psi_s(z_s) \prod_{t \in ch_s} m_{t \to s}(z_s)\) (9.58)

To compute the outgoing message that s should send to its parent t, we pass the local belief through the pairwise potential linking s and t, and then marginalize out s to get

\(m_{s \to t}(z_t) = \sum_{z_s} \psi_{st}(z_s, z_t) bel_s(z_s)\) (9.59)

At the root of the tree, bel_t(z_t) = p(z_t | y) will have seen all the evidence. It can then send messages back down to the leaves. The message that s sends to its child t should be the product of all the messages that s received from all its other children u, passed through the pairwise potential, and then marginalized:

\(m_{s \to t}(z_t) = \sum_{z_t} \left( \psi_s(z_s) \psi_{st}(z_s, z_t) \prod_{u \in ch_s \setminus t} m_{u \to s}(z_s) \right)\) (9.60)

See Figure 9.9. Instead of multiplying all-but-one of the messages that s has received, we can multiply all of them and then divide out by the t → s message from child t. The advantage of this is that the product of all the messages has already been computed in Equation (9.58), so we don't need to recompute that term. Thus we get

\(m_{s \to t}(z_t) = \sum_{z_s} \psi_{st}(z_s, z_t) \frac{bel_s(z_s)}{m_{t \to s}(z_s)}\) (9.61)

We can think of bel_s(z_s) as the new updated posterior p(z_s | y) given all the evidence, and m_{t → s}(z_s) as the prior predictive p(z_s | y_t^-), where y_t^- is all the evidence in the subtree rooted at t. Thus the ratio contains the new evidence that t did not already know about from its own subtree. We use this to update the belief state at node t to get:

\(bel_t(z_t) \propto bel_t(z_t) m_{s \to t}(z_t)\) (9.62)

(Note that Equation (9.58) is a special case of this where we don't divide out by m_{s → t}, since in the upwards pass, there is no incoming message from the parent.) This is analogous to the backwards smoothing equation in Equation (9.37), with \alpha_t(i) replaced by bel_t(z_t = i), A(i,j) replaced by \psi_{st}(z_s = i, z_t = j), \gamma_{t+1}(j) replaced by bel_s(z_s = j), and \alpha_{t+1|t}(j) replaced by m_{t \to s}(z_s = j).

See Figure 9.8 for the overall pseudocode. This can be generalized to directed trees with multiple root nodes (known as polytrees) as described in Supplementary Section 9.1.1.

# 9.3.3 Max-product algorithm

In Section 9.3.2 we described the sum-product algorithm, that computes the posterior marginals:

\(bel_i(k) = \gamma_i(k) = p(z_i = k | y) = \sum_{z_{-i}} p(z_i = k, z_{-i} | y)\) (9.63)