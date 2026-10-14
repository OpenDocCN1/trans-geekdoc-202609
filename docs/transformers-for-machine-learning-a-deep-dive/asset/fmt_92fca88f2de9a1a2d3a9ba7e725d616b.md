
# Scaling

The time complexity of Funnel-Transformer is `O(d) ⋅ T² + T ⋅ d²`. Since `T` decreases by half at successive encoder layers, the complexity decreases by a factor of four for each layer. Since `O(T ⋅ d²)` has the large constant `d²`, it tends to dominate, providing a linear speedup, instead of a quadratic one.

Due to the complexity reduction afforded by the pooling between layers, it is possible to add additional encoder layers or make existing layers wider without increasing the computational load in any significant manner.

# Performance

Three sizes of the standard transformer were compared to several configurations of Funnel-Transformer, each with fewer or similar numbers of expected floating-point operations to the transformer to which it was being compared:

- **large**: 24 layers, `d` = 1024  
- **base**: 12 layers, `d` = 768  
- **small**: 6 layers, `d` = 768  

Quality comparisons are made for GLUE and when Funnel-Transformer decreases the sequence length and adds more layers, it performs better than the standard transformer on text classification and all GLUE datasets except for STS-B. When the sequence length is decreased but the depth is not increased, performance decreases on GLUE text classification datasets.

## 5.1.1.2 DeLighT

DeLighT \[[180](#refbib.xhtml#refbib_180)\] is a modified Transformer architecture that performs as well as the standard transformer on machine translation and language modeling; all while using far fewer parameters and FLOPs. It introduces a transformation on the input to a Transformer block that comes before the projections into query, key, value spaces.

**DeLighT block** The DeLighT block uses N layers of the grouped linear transformation (GLT) \[[181](#refbib.xhtml#refbib_181)\] to first transform a *d*-dimensional vector into a higher-dimensional space of *d*[*m**a**x*] = *w*[*m*] *d*[*i**n*] in the first ⌈*N*/2⌉ layers, and then transform the *d*[*m**a**x*] vector into a lower-dimensional space, *d*[*o*], using the other *N* − ⌈*N*/2⌉ layers. The *d*[*o*] vector is what is then projected in the query, key, and value spaces. DeLighT blocks closer to the output of the model are made wider and deeper than those closer to the model input. DeLightT used *d*[*o*] = *d*/2 and also shuffles the features between the groups in the GLT, using a mixer connection \[[182](#refbib.xhtml#refbib_182)\] to combine the shuffled features with the input, similar to a residual connection. The expansion phase of the DeLighT block is shown in [Fig. 5.3](#ch5.xhtml#fig5_3).

``` 
[Figure 5.3 The expansion phase of the DeLight transformation, showing the three grouped linear transformations (GLT).](images/fig5_3.jpg)
```

[Figure 5.3](#ch5.xhtml#b5fig5_3) The expansion phase of the DeLight transformation, showing the three grouped linear transformations (GLT).

Mehta et al. proposed that by increasing the depth of the DeLighT block and the width of its intermediate GLT layers, the transformer will have an increased representational capacity and that one can then replace multi-head attention with single-head attention. Similarly, they propose that the DeLighT block's wide linear layers let one decrease the size of the feedforward layer by up to 16x.

**Performance** DeLighT performed as well as or better than the standard transformer on machine translation, despite having considerably fewer parameters. But, when DeLighT is given more parameters, it outperforms the standard transformer. It also obtains similar or better quality to SOTA models on machine translation. Also, performance increases with the number of network parameters in the DeLighT block.

## 5.1.2 Connections between Transformer Blocks

### 5.1.2.1 RealFormer

RealFormer, the Residual Attention Layer Transformer \[[107](#refbib.xhtml#refbib_107)\], adds residual scores to the raw attention logits (query-key dot product) of all attention heads from the previous layer of a transformer. The attention weights are then the softmax of the summed attention logits. This is shown schematically in [Fig. 5.4](#ch5.xhtml#fig5_4) and mathematically in (5.7)–(5.9).

``` 
$$\\begin{array}{l} {ResidualMultiHead(\\mathbf{Q},\\mathbf{K},\\mathbf{V},\\mathbf{Prev}) = \\text{concat}(head\_{1},\\ldots,head\_{h})\\mathbf{W}\_{o}} \\\\ \\end{array}$$  

(5.7)
```

``` 
$$\\begin{array}{l} {head\_{i} = ResidualAttn(\\mathbf{Q}\_{i},\\mathbf{K}\_{i},\\mathbf{V}\_{i},\\mathbf{Pre}\\mathbf{v}\_{i})} \\\\ \\end{array}$$  

(5.8)
```

``` 
$$\\begin{array}{l} {ResidualAttn(\\mathbf{Q}^{\\prime},\\mathbf{K}^{\\prime},\\mathbf{V}^{\\prime},\\mathbf{Pre}\\mathbf{v}^{\\prime}) = \\text{softmax}\\left( {\\frac{\\mathbf{Q}^{\\prime}\\mathbf{K}^{\\prime}\\ ^{\\text{T}}}{\\sqrt{\\text{d}\\_\\text{k}}}\\text{+}\\mathbf{Pre}\\mathbf{v}^{\\prime}} \\right)\\mathbf{V}^{\\prime}} \\\\ \\end{array}$$  

(5.9)
```

where **P****r****e****v** ∈ ℝ^(*h* × *d*[*i**n**] × *d*[*o**u**t*]) are the attention logits from the previous transformer layer. *d*[*i**n**] is the layer's input sequence dimension and *d*[*o**u**t*] is the layer's output sequence dimension. The argument of the softmax, the attention logits or attention scores, is passed to the next RealFormer layer.

![Figure 5.4 RealFormer's residual attention connection.](images/fig5_4.jpg)

[Figure 5.4](#ch5.xhtml#b5fig5_4) RealFormer's residual attention connection.

This method can be applied to other transformer architectures, including to decoder layers. When there are multiple types of attention modules in a transformer, one can skip edges to support one residual connection for each type of attention.

**Performance** RealFormer generally performs better than the standard transformer architecture, including its use in BERT, all without increasing the number of model parameters.

## 5.1.3 Adaptive Computation Time

### 5.1.3.1 Universal transformers (UT)

As seen in the previous chapters, transformers overcome the issues associated with RNNs, namely the bottlenecks of sequential computation and the vanishing gradient problems amongst the many. Furthermore, self-attention, the critical innovation in the transformers, helps in parallelizing the computation of per-symbol context-based vectors and creates a global receptive field where the symbol gets information from all the symbols. On the other hand, the absence of recurrent inductive bias of RNNs becomes an issue when solving tasks with inherent hierarchical structures or when the lengths vary significantly between the training and the unseen data the model predicts. Also, the number of sequential computations in transformers is independent of the input size but only dependent on the number of layers, making it computationally non-universal or Turing incomplete. Transformers apply the same amount of computation to all the inputs leading to inefficiencies in many cases where computations can be conditioned on the complexity.

Universal transformers (UT) by Dehghani et al. \[[69](#refbib.xhtml#refbib_69)\] is an extension of transformers where the parallelizability and global receptive field benefits get supplemented by the recurrent inductive bias of RNNs while being computationally universal. Instead of a fixed number of layers in the transformers, Universal transformers have a Universal transformer block, i.e., a self-attention mechanism followed by a recurrent transformation that provides a recurrent inductive bias for each input symbol in parallel. As shown in [Fig. 5.5](#ch5.xhtml#fig5_5), the Universal Transformer is a recurrent function not in time but in depth that evolves the hidden states corresponding to every input in parallel, based at each step on the sequence of previous hidden states.

![Figure 5.5 Universal Transformer with information from different positions using self-attention and applying a recurrent transition function.](images/fig5_5.jpg)
