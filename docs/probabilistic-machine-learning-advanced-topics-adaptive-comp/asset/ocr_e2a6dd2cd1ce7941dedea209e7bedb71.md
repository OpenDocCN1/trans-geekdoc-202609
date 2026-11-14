(The scaling by \(\sqrt{d_k}\) is to reduce the dependence of the output on the dimensionality of the vectors.)

Given the scores, we can compute the attention weights using the softmax function:

\(\alpha_i(\boldsymbol{q}, \boldsymbol{k}_{1:n}) = \text{softmax}_i([a(\boldsymbol{q}, \boldsymbol{k}_1), \dots, a(\boldsymbol{q}, \boldsymbol{k}_n)]) = \frac{\exp(a(\boldsymbol{q}, \boldsymbol{k}_i))}{\sum_{j=1}^n \exp(a(\boldsymbol{q}, \boldsymbol{k}_j))}\) (16.10)

See Figure 16.6 for an illustration.

In some cases, we want to restrict attention to a subset of the dictionary, corresponding to valid entries. For example, we might want to pad sequences to a fixed length (for efficient minibatching), in which case we should "mask out" the padded locations. This is called **masked attention**. We can implement this efficiently by setting the attention score for the masked entries to a large negative number, such as \(-10^6\), so that the corresponding softmax weights will be 0.

For efficiently, we usually compute all \(n\) vectors in parallel. Let the corresponding matrices of queries, keys and values be denoted by \(\mathbf{Q} \in \mathbb{R}^{n \times d_k}\), \(\mathbf{K} \in \mathbb{R}^{n \times d_k}\), \(\mathbf{V} \in \mathbb{R}^{n \times d_v}\). Let

\(\boldsymbol{z}_j = \sum_{i=1}^n \alpha_i(\boldsymbol{q}_j, \mathbf{K}) \boldsymbol{v}_i\) (16.11)

be the \(j\)’th output corresponding to the \(j\)’th query. We can compute all outputs \(\mathbf{Z} \in \mathbb{R}^{n \times d_v}\) in parallel using
\(\mathbf{Z} = \text{Attn}(\mathbf{Q}, \mathbf{K}, \mathbf{V}) = \text{softmax}(\frac{\mathbf{Q}\mathbf{K}^\top}{\sqrt{d_k}})\mathbf{V}\) (16.12)

where the softmax function softmax is applied row-wise. See Figure 16.7 (left) for an illustration.

To increase the flexibility of the model, we often use a **multi-head attention** layer, as illustrated in Figure 16.7 (right). Let the \(i\)’th head be

\(\boldsymbol{h}_i = \text{Attn}(\mathbf{Q}\mathbf{W}_i^Q, \mathbf{K}\mathbf{W}_i^K, \mathbf{V}\mathbf{W}_i^V)\) (16.13)

where \(\mathbf{W}_i^Q \in \mathbb{R}^{d \times d_k}\), \(\mathbf{W}_i^K \in \mathbb{R}^{d \times d_k}\) and \(\mathbf{W}_i^V \in \mathbb{R}^{d \times d_v}\) are linear projection matrices. We define the output of the MHA layer to be

\(\mathbf{Z} = \text{MHA}(\mathbf{Q}, \mathbf{K}, \mathbf{V}) = \text{Concat}(\boldsymbol{h}_1, \dots, \boldsymbol{h}_h)\mathbf{W}^O\) (16.14)

where \(h\) is the number of heads, and \(\mathbf{W}^O \in \mathbb{R}^{hd_v \times d}\). Having multiple heads can increase performance of the layer, in the event that some of the weight matrices are poorly initialized; after training, we can often remove all but one of the heads [MLN19].

When the output of one attention layer is used as input to another, the method is called **self-attention**. This is the basis of the transformer model, which we discuss in Section 16.3.5.

# 16.2.8 Recurrent layers

We can make the model be **stateful** by augmenting the input \(\boldsymbol{x}\) with the current state \(\boldsymbol{s}_t\), and then computing the output and the new state using some kind of function:

\((\boldsymbol{y}, \boldsymbol{s}_{t+1}) = f(\boldsymbol{x}, \boldsymbol{s}_t)\) (16.15)

This is called a **recurrent layer**, as shown in Figure 16.8. This forms the basis of **recurrent neural networks**, discussed in Section 16.3.4. In a vanilla RNN, the function \(f\) is a simple MLP, but it may also use attention (Section 16.2.7).