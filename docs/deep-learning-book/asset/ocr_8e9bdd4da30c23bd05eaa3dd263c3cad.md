and learned biases **b**, then the affine-softmax output layer performs the following computations:

a_i = b_i + Σ_j W_{ij} h_j   ∀i ∈ {1, …, |V|},   (12.8)

\hat{y}_i = e^{a_i} / Σ_{i'=1}^{|V|} e^{a_{i'}}.   (12.9)

If **h** contains n_h elements, then the above operation is O(|V| n_h). With n_h in the thousands and |V| in the hundreds of thousands, this operation dominates the computation of most neural language models.

# 12.4.3.1 Use of a Short List

The first neural language models (Bengio et al., 2001, 2003) dealt with the high cost of using a softmax over a large number of output words by limiting the vocabulary size to 10,000 or 20,000 words. Schwenk and Gauvain (2002) and Schwenk (2007) built upon this approach by splitting the vocabulary V into a **shortlist** L of most frequent words (handled by the neural net) and a tail T = V\L of more rare words (handled by an n-gram model). To be able to combine the two predictions, the neural net also has to predict the probability that a word appearing after context C belongs to the tail list. This may be achieved by adding an extra sigmoid output unit to provide an estimate of P(i ∈ T | C). The extra output can then be used to achieve an estimate of the probability distribution over all words in V as follows:

P(y = i | C) = 1_{i∈L} P(y = i | C, i ∈ L) (1 − P(i ∈ T | C))
+ 1_{i∈T} P(y = i | C, i ∈ T) P(i ∈ T | C),   (12.10)

where P(y = i | C, i ∈ L) is provided by the neural language model and P(y = i | C, i ∈ T) is provided by the n-gram model. With slight modification, this approach can also work using an extra output value in the neural language model's softmax layer, rather than a separate sigmoid unit.

An obvious disadvantage of the short list approach is that the potential generalization advantage of the neural language models is limited to the most frequent words, where, arguably, it is the least useful. This disadvantage has stimulated the exploration of alternative methods to deal with high-dimensional outputs, described below.