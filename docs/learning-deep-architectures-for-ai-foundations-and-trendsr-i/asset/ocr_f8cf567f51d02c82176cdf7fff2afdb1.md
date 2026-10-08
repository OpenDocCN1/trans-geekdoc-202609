# 6.1 Layer-Wise Training of Deep Belief Networks 69

```
**Algorithm 2**
TrainUnsupervisedDBN($\hat{P}, \epsilon, \ell, W, b, c, \text{mean\_field\_computation}$)
```

Train a DBN in a purely unsupervised way, with the greedy layer-wise procedure in which each added layer is trained as an RBM (e.g., by Contrastive Divergence).

+   $\hat{P}$ is the input training distribution for the network
$\epsilon$ is a learning rate for the RBM training
$\ell$ is the number of layers to train
$W^k$ is the weight matrix for level $k$, for $k$ from 1 to $\ell$

+   $\mathbf{b}^k$ is the visible units offset vector for RBM at level $k$, for $k$ from 1 to $\ell$
$\mathbf{c}^k$ is the hidden units offset vector for RBM at level $k$, for $k$ from 1 to $\ell$

mean_field_computation is a Boolean that is true training data at each additional level is obtained by a mean-field approximation instead of stochastic sampling

+   for $k = 1$ to $\ell$ do
  initialize $W^k = 0, \mathbf{b}^k = 0, \mathbf{c}^k = 0$
  while
    sample $\mathbf{h}^l$ from $\hat{P}$
    for $i = 1$ to $k-1$ do
      if mean_field_computation then
        assign $\mathbf{h}^j$ to $Q(\mathbf{h}^j|\mathbf{h}^{i-1})$, for all elements $j$
        $\\mathbf{h}^i$
      else
        sample $\mathbf{h}^j$ from $Q(\mathbf{h}^j|\mathbf{h}^{i-1})$, for all elements $j$
        $\\mathbf{h}^i$
      end
  RMBupdate({\mathbf{h}^{k-1}, \epsilon, W^k, \mathbf{b}^k, \mathbf{c}^k$) {this providing $Q(\mathbf{h}^k|\mathbf{h}^{k-1})$ for future use}
end while
end for