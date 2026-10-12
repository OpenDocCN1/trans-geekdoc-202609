
![Figure 13.11 Graph partitioning. a) Input graph. b) The input graph is partitioned into smaller subgraphs using a principled method that removes the fewest edges. c-d) We can now use these subgraphs as batches to train in a transductive setting, so here, there are four possible batches. e) Alternatively, we can use combinations of the subgraphs as batches, reinstating the edges between them. If we use pairs of subgraphs, there would be six possible batches here.](images/c13-fig-0011.jpg)

[Figure 13.11](#c013.xhtml#c13-fig-0011a) Graph partitioning. a) Input graph. b) The input graph is partitioned into smaller subgraphs using a principled method that removes the fewest edges. c-d) We can now use these subgraphs as batches to train in a transductive setting, so here, there are four possible batches. e) Alternatively, we can use combinations of the subgraphs as batches, reinstating the edges between them. If we use pairs of subgraphs, there would be six possible batches here.

Given one of the above methods to form batches, we can now train the network parameters in the same way as for the inductive setting, dividing the labeled nodes into train, test, and validation sets as desired; we have effectively converted a transductive problem to an inductive one. To perform inference, we compute predictions for the unknown nodes based on their k-hop neighborhood. Unlike training, this does not require storing the intermediate representations, so it is much more memory efficient.

## 13.8 Layers for graph convolutional networks

In the previous examples, we combined messages from adjacent nodes by summing them together with the transformed current node. This was accomplished by post-multiplying the node embedding matrix `H` by the adjacency matrix plus the identity `A + I`. We now consider different approaches to both (i) the combination of the current embedding with the aggregated neighbors and (ii) the aggregation process itself.

### 13.8.1 Combining current node and aggregated neighbors

In the example GCN layer above, we combined the aggregated neighbors `HA` with the current nodes `H` by just summing them:

![c13-fig-5015.jpg](images/c13-fig-5015.jpg)

(13.13)

In another variation, the current node is multiplied by a factor of `(1 + ε[k])` before contributing to the sum, where `ε[k]` is a learned scalar that is different for each layer:

![c13-fig-5016.jpg](images/c13-fig-5016.jpg)

(13.14)

This is known as *diagonal enhancement*. A related variation applies a different linear transform `Ψ[k]` to the current node:

![c13-fig-5017.jpg](images/c13-fig-5017.jpg)

(13.15)

where we have defined ![c13-fig-5018.jpg](images/c13-fig-5018.jpg) in the third line.

### 13.8.2 Residual connections

With residual connections, the aggregated representation from the neighbors is transformed and passed through the activation function before summation or concatenation with the current node. For the latter case, the associated network equations are:

![c13-fig-5019.jpg](images/c13-fig-5019.jpg)

(13.16)

***

Problem 13.8

***

### 13.8.3 Mean aggregation

The above methods aggregate the neighbors by summing the node embeddings. However, it's possible to combine the embeddings in different ways. Sometimes it's better to take the average of the neighbors rather than the sum; this can be superior if the embedding information is more important and the structural information less so since the magnitude of the neighborhood contributions will not depend on the number of neighbors:

![c13-fig-5020.jpg](images/c13-fig-5020.jpg)

(13.17)

where as before, `ne[n]` denotes a set containing the indices of the neighbors of the `n-th` node. Equation 13.17 can be computed neatly in matrix form by introducing the diagonal `N × N` degree matrix `D`. Each non-zero element of this matrix contains the number of neighbors for the associated node. It follows that each diagonal element in the inverse matrix `D^−¹` contains the denominator that we need to compute the average. The new GCN layer can be written as:

![c13-fig-5021.jpg](images/c13-fig-5021.jpg)

(13.18)

### 13.8.4 Kipf normalization

There are many variations of graph neural networks based on mean aggregation. Sometimes the current node is included with its neighbors in the mean computation rather than treated separately. In Kipf normalization, the sum of the node representations is normalized as:

![c13-fig-5022.jpg](images/c13-fig-5022.jpg)

(13.19)

with the logic that information coming from nodes with a very large number of neighbors should be down-weighted since there are many connections and they provide less unique information. This can also be expressed in matrix form using the degree matrix:

![c13-fig-5023.jpg](images/c13-fig-5023.jpg)

(13.20)

***

Problem 13.9

***

### 13.8.5 Max pooling aggregation

An alternative operation that is also invariant to permutation is computing the maximum of a set of objects. The *max pooling* aggregation operator is:

![c13-fig-5024.jpg](images/c13-fig-5024.jpg)

(13.21)

where the operator `max[•]` returns the element-wise maximum of the vectors `h[m]` that are neighbors to the current node `n`.

### 13.8.6 Aggregation by attention

The aggregation methods discussed so far either weight the contribution of the neighbors equally or in a way that depends on the graph topology. Conversely, in *graph attention layers*, the weights depend on the data at the nodes. A linear transform is applied to the current node embeddings so that:

![c13-fig-5025.jpg](images/c13-fig-5025.jpg)

(13.22)

Then the similarity `s[mn]` of each transformed node embedding ![c13-fig-5026.jpg](images/c13-fig-5026.jpg) to the transformed node embedding ![c13-fig-5027.jpg](images/c13-fig-5027.jpg) is computed by concatenating the pairs, taking a dot product with a column vector `ϕ[k]` of learned parameters, and applying an activation function:

![c13-fig-5028.jpg](images/c13-fig-5028.jpg)

(13.23)

These variables are stored in an `N × N` matrix `S`, where each element represents the similarity of every node to every other. As in dot-product self-attention, the attention weights contributing to each output embedding are normalized to be positive and sum to one using the softmax operation. However, only those values corresponding to the current node and its neighbors should contribute. The attention weights are applied to the transformed embeddings:

![c13-fig-5029.jpg](images/c13-fig-5029.jpg)

(13.24)

where `a[•]` is a second activation function. The function `Softmask[•, •]` computes the attention values by applying softmax operation separately to each column of its first argument `S`, but only after setting values where the second argument `A + I` is zero to negative infinity, so they do not contribute. This ensures that the attention to non-neighboring nodes is zero.

This is very similar to the self-attention computation in transformers (see [figure 13.12](#c013.xhtml#c13-fig-0012)), except that (i) The keys, queries, and values are all the same, (ii) The measure of similarity is different, and (iii) The attentions are masked so that each node only attends to itself and its neighbors. As in transformers, this system can be extended to use multiple heads that are run in parallel and recombined.

***

Notebook 13.4

Graph attention

***

***

Problem 13.10

***
