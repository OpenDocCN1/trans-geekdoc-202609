
[Figure 5.11](#ch5.xhtml#b5fig5_11) Global attention adjacency matrix for the internal transformer construction, for *L* = 12 and *G* = 3, 4, 7. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

The external transformer construction adds *g* additional tokens to the existing *L* tokens. The additional tokens are global. Examples include special tokens used in transformers, like \[CLS\]\[CLS\]. This essentially creates a new adjacency matrix, *B*, that includes the special tokens by prepending *g* rows and columns onto *A*. Here, *B*(*i*,  : ) = *B*(:,*i*) = 1, where *i* = 1, …, *g*, and *B*(*g* + *i*, *g* + *j*) = *A*(*i*, *j*), where *i* and *j* = 1, …, *L*. The expanded adjacency matrix *B* is shown in [Fig. 5.12](#ch5.xhtml#fig5_12).

![Figure 5.12 Global attention adjacency matrix for the external transformer construction, for L = 9 and g = 3. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_12.jpg)

[Figure 5.12](#ch5.xhtml#b5fig5_12) Global attention adjacency matrix for the external transformer construction, for *L* = 9 and *g* = 3. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

Finally, an example adjacency matrix for the combination of random, sliding window, and global attention (external construction) is shown in [Fig. 5.13](#ch5.xhtml#fig5_13).

![Figure 5.13 Big Bird attention adjacency matrix for the external transformer construction, for L = 12,g = 2,w = 4, and r = 4. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_13.jpg)

[Figure 5.13](#ch5.xhtml#b5fig5_13) Big Bird attention adjacency matrix for the external transformer construction, for *L* = 12, *g* = 2, *w* = 4, and *r* = 4. Row *i* corresponds to query *i*. Columns with a • are keys that query *i* attends to and ⋅ represents a lack of attention (a missing edge).

**Efficient sparse matrix multiplication** By making the adjacency matrix (and the corresponding attention matrix) sparse, the speedups provided by GPUs are removed. This is because multiplication of matrices with arbitrary sparsity is not efficient on GPUs. However, matrices whose sparsity is grouped into blocks can be efficiently multiplied on GPUs \[[100](#refbib.xhtml#refbib_100)\].

To address this, Big Bird groups blocks of queries and keys together and then adds sparsity by block rather than by individual sequence position \[[292](#refbib.xhtml#refbib_292)\]. Select a block size, *b*, and then divide the sequence length *L* into *L*/*b* blocks. So, instead of *L* queries and keys, there will be *L*/*b* queries and keys. This modifies each attention pattern discussed above in relatively simple ways:

1.  **Random attention** The random number of keys for a query to attend to, *r*, becomes the random number of key blocks that a query block attends to.

2.  **Sliding window attention** The query block *i* attends to key blocks *i* − (*w* − 1)/2 through *i* + (*w* − 1)/2.

3.  **Global attention** The definition of global attention is unchanged, except it is defined in terms of blocks rather than sequence position.

### 5.2.3 Improving Multi-Head-Attention

Now we focus on some of the ways the attention mechanism has been changed to improve performance of the transformer.

#### 5.2.3.1 Talking-heads attention

Vaswani et al \[[254](#refbib.xhtml#refbib_254)\] showed that multi-head attention allows the transformer to perform *h* (number of attention heads) separate attention calculations. Talking-Heads Attention \[[227](#refbib.xhtml#refbib_227)\] instead allows the attention heads to share information. It works by adding two linear layers that project the product of the query and key matrices, **QK**^(*T*) (attention logits), into a new space and projects the attention weights, *S**o**f**t**m**a**x*(**Q****K**^(*T*)), into a new space.

Talking-Heads Attention (THA) also partitions the attention heads into three types: heads for the queries and keys, heads for the value, and heads for the attention logits and attention weights. Let's look at this in detail.

Recall from [section 5.2.1.1](#ch5.xhtml#sec5_2_1_1) that the multi-head attention between two sequences **X**[1], **X**[2], with lengths *L*[1] and *L*[2] is:

$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\_{1}\\mathbf{W}\_{q},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{k} \\times h}} \\\\ \\mathbf{K} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{k} \\times h}} \\\\ \\mathbf{V} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{v},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{v} \\times h}} \\\\ \\end{array}$$  

(5.56)

where **X**[1] ∈ ℝ^(*L*[1] × *d*), **X**[2] ∈ ℝ^(*L*[2] × *d*), **W**[*q*], **W**[*k*] ∈ ℝ^(*d* × *d*[*k*] × *h*), and **W**[*v*] ∈ ℝ^(*d* × *d*[*v*] × *h*), with

$$\\begin{array}{ll} \\mathbf{\\alpha} & {= \\mathbf{Q}\\mathbf{K}^{T}, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h}} \\\\ \\end{array}$$  

(5.57)

$$\\begin{array}{ll} {\\mathbf{A}(\\mathbf{Q},\\mathbf{K})} & {= \\text{softmax}\\left( \\frac{\\mathbf{\\alpha}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right),\\, \\in {\\mathbb{R}}^{\\text{L}\_{\\text{1}} \\times \\text{L}\_{\\text{2}} \\times \\text{h}}} \\\\ \\end{array}$$  

(5.58)

$$\\begin{array}{ll} {\\mathbf{C}(\\mathbf{Q},\\mathbf{K},\\mathbf{V})} & {= {\\sum\\limits\_{L\_{2}}\\mathbf{A}}(\\mathbf{Q},\\mathbf{K})\\mathbf{V},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{v} \\times h}} \\\\ \\end{array}$$  

(5.59)

where *α* is the attention logits, **A**(**Q**, **K**) are the attention weights, and **C**(**Q**, **K**, **V**) is the “context” vector representing the output of the *h* attention heads prior to concatenation of the attention heads and the final projection layer.

**Partitioning the attention heads** THA modifies the attention mechanism in a few ways from that shown in (5.56)–(5.59). First, it changes the attention head dimension of **Q** and **K** to be the number of query-key attention head *h*[*k*], and changes the attention head dimension of **V** to be the number of value attention heads *h*[*v*]. This happens by changing the dimension of the projection matrices that generate the query, key, and value matrices from the input sequences. In other words, (5.56) becomes

$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\_{1}\\mathbf{W}\_{q},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{k} \\times h\_{k}}} \\\\ \\mathbf{K} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{k} \\times h\_{k}}} \\\\ \\mathbf{V} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{v},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{v} \\times h\_{v}}} \\\\ \\end{array}$$  

(5.60)

where **W**[*q*], **W**[*k*] ∈ ℝ^(*d* × *d*[*k*] × *h*[*k*]), and **W**[*v*] ∈ ℝ^(*d* × *d*[*v*] × *h*[*v*]).

**Projecting the attention logits** Next, the attention logits*α* are projected with a linear layer that mixes the query-key attention heads with the attention logit/weight heads, **W**[*α*] ∈ ℝ^(*h*[*k*] × *h*), and the attention weights are projected with a linear layer that mixes the value attention heads with the attention logit/weight heads, **W**[*A*] ∈ ℝ^(*h* × *h*[*v*]). In other words, (5.57)–(5.59) becomes

$$\\begin{array}{l} {\\mathbf{\\alpha} = \\mathbf{Q}\\mathbf{K}^{T}, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h\_{k}}} \\\\ \\end{array}$$  

(5.61)

$$\\begin{array}{l} {\\mathbf{P}\_{\\alpha} = \\mathbf{\\alpha}\\mathbf{W}\_{\\alpha},\\, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h}} \\\\ \\end{array}$$  

(5.62)
