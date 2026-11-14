
where \( f(\cdot) \) is the encoder function which takes input \( x \) and produces the hidden layer \( y \), and \( g(\cdot) \) is the decoder function which takes the hidden layer representation and produces the output \( z \). The hidden layer of the autoencoder can be represented as

```
y = \sigma(xW + b)
```

where

- \( x \) is the input vector. If \( x \) is a set of categorical values, then it is a binary vector, e.g. \( x = [0, 1, 1, 0, 0] \). \( x \) is of size \( \text{(batch\_size, vocab\_size)} \).
- \( W \) is the weight matrix, of size \( \text{(vocab\_size, hidden\_size)} \).
- \( b \) is the bias column vector, of size \( \text{(vocab\_size, 1)} \).
- \( \sigma \) is the activation function, e.g. sigmoid or ReLU activation.

### 8.5.1 Embedding Lookup on Sparse Inputs

\( xW + b \) is the linear model, or the dense layer of a feedforward neural network before activation. The linear multiplication term \( xW \) results a \( \text{[batch\_size, vocab\_size]} \times \text{[vocab\_size, hidden\_size]} = \text{[batch\_size, hidden\_size]} \) matrix. For example, let

```
W = 
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \\
1 & 3 & 5 \\
2 & 4 & 6
\end{bmatrix}

Then

\tilde{y} = xW = [0 \ 1 \ 1 \ 0 \ 0] \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \\ 1 & 3 & 5 \\ 2 & 4 & 6 \end{bmatrix}
= [4+7 \ 5+8 \ 5+8 \ 6+9]
= [11 \ 13 \ 15]
```

Notice that this is a sparse (\( x \)) to dense matrix (\( W \)) multiplication. In addition to using dense binary representation of \( x \), we can also use a sparse tensor to represent the binary indicator. Therefore, this operation can be achieved by tf.sparse.sparse_dense_matmul in Tensorflow or torch.sparse.mm in PyTorch, i.e.

```
import tensorflow as tf
x = tf.sparse.from_dense([[0, 1, 1, 0, 0]])
W = tf.constant([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [1, 3, 5],
    [2, 4, 6],
])
y_tilde = tf.sparse.sparse_dense_matmul(x, W)
# <tf.Tensor: shape=(1, 3), dtype=int32, numpy=array([[11, 13, 15]], dtype=int32)>
```

and in PyTorch,

```
import torch
x = torch.tensor([[0, 1, 1, 0, 0]]).to_sparse()
W = torch.tensor([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [1, 3, 5],
    [2, 4, 6],
])
y_tilde = torch.sparse.mm(x, W)
# tensor([[11, 13, 15]])
```

If we make W the embedding matrix We, and let x -> s where s is the set of indices where the binary vector xi = 1, e.g. x = [0, 1, 1, 0, 0] -> s = [1, 2]. Then, the lookup operation on the embedding matrix will return each row of the embedding vector stacked vertically, e.g.

$E = [W_e] \cdot lookup(s) = \begin{bmatrix} 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix}$

Then, to get xW, we simply sum across the rows of the resulting matrix,

$\bar{y}_k = \sum_i E_{i,k}$

Or

$\bar{y} = [4 + 7 + 5 + 8 + 6 + 9] = [11 \ 13 \ 15]$

Embedding lookups are usually implemented with a hash map which has a time complexity of (O(1)). An advantage of using the embedding lookup is that, we no longer need to compute the multiplication with 0 terms. This is especially helpful when the data is very sparse (containing predominantly 0s). Both Tensorflow and PyTorch implement a version of the above embedding lookup and summation operation. In Tensorflow, i.e.

```
import tensorflow as tf

s = tf.ragged.constant([([1, 2], [3, 0, 4])]).to_sparse()
W = tf.constant([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [1, 3, 5],
    [2, 4, 6],
])
weights = s.values_with_values(tf.ones_like(s.values)) # equal weights
y_tilde = tf.nn.embedding_lookup_sparse(
    W,
    s,
    weights,
    combiner="sum",
)
# <tf.Tensor: shape=(2, 3), dtype=int32, numpy=
# array([[11, 13, 15],
#        [ 4,  9, 14]], dtype=int32)>
```

In PyTorch, i.e.

```
import torch

# 1-based indexing; 0 is used as padding index
s = torch.tensor([[2, 3, 0, 0, 0], [4, 1, 5, 0, 0]])
W = torch.tensor([
    [0, 0, 0], # padding entry
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [1, 3, 5],
    [2, 4, 6],
])
y_tilde = torch.nn.functional.embedding(
    s,
    W,
    padding_idx=0,
).sum(dim=1)
# tensor([[11, 13, 15],
#         [ 4,  9, 14]])
```

Notice that in Tensorflow's implementations, we need to specify `combiner="sum"` to sum together each embedding along the row. In contrast, `torch.nn.functional.embedding` returns a `(batch_size, seq_len, hidden_size)` tensor, where the padding entries are part of the output. We then need to sum along `dim=1` to combine the embeddings together.

To complete the dense layer with the bias term, we can further initialize a single vector $b$ whose length is equal to the embedding size. Then, $\bar{y} = xW + b$ is hence represented as

\(\bar{y}_k = b_k + \sum_{i \in s} E_{i,k}\) (8.2)

where $i$ is the index of the item along each row (where a row may contain a variable number of items), and $k$ is the index of the embedding vector.

### 8.5.2 Inputs with Weights

If each item in the input vector is also weighted by a weight $w$, then we can modify the above dense layer implementation as

\(y_k = b_k + \sum_{i \in s} w_i \cdot E_{i,k}\) (8.3)

Following the above example, suppose items 1 and 2 are weighted by 1.3 and 2.7, respectively, then the input $x$ is modified to become

$x = [0 \quad 1.3 \quad 2.7 \quad 0.0 \quad 0.0]$

instead of a simple binary vector that contains only 0s and 1s. When converting to the indicator notations, we need two tensors created, one that stores the indices of the items, and one that stores the weights at the corresponding entry, i.e.

$s = [1, 2]$

$v = [1.3, 2.7]$

Let us realize Equation 8.3 in Tensorflow,

```
import tensorflow as tf
s = tf.ragged.constant([[1, 2], [3, 0, 4]]).to_sparse()
v = tf.ragged.constant([[1.3, 2.7], [2.1, 4.6, 0.8]]).to_sparse()
W = tf.constant([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [1, 3, 5],
    [2, 4, 6],
], dtype=tf.float32)
y_tilde = tf.nn.embedding_lookup_sparse(
    W,
    s,
    v,
    combiner="sum",
)
# <tf.Tensor: shape=(2, 3), dtype=float32, numpy=
# array([[24.099998, 28.1, 32.100002],
#        [ 8.3, 18.7, 29.099998]], dtype=float32)>
```

And in PyTorch,

```
import torch
# 1-based indexing; 0 is used as padding index
s = torch.tensor([[2, 3, 0, 0, 0], [4, 1, 5, 0, 0]])
# using dense representations with paddings
v = torch.tensor([[[1.3, 2.7, 0.0, 0.0, 0.0], [2.1, 4.6, 0.8, 0.0, 0.0]]])
W = torch.tensor([
    [0, 0, 0], # padding entry
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [1, 3, 5],
    [2, 4, 6],
], dtype=torch.float32)
# look up embeddings
y_tilde = torch.nn.functional.embedding(
    s,
    W,
    padding_idx=0,
)
# apply weights
y_tilde = v * v[:, :, None]
# Combine
y_tilde = y_tilde.sum(dim=1)
# tensor([[24.1000, 28.1000, 32.1000],
#         [ 8.3000, 18.7000, 29.1000]])
```

In practice, the embedding lookup table is learned during a certain training task or can also be reloaded from a pre-trained model. Let us implement the autoencoder model which takes sparse inputs using Tensorflow/Keras and PyTorch. Tensorflow/Keras implementation is below

```
import tensorflow as tf
from keras import Model, Input
from keras.layers import Dense, Activation

class Autoencoder(Model):
    """Autoencoder with sparse inputs."""

    def __init__(
        self,
        num_items,
        emb_size,
        hidden_activation="relu",
        output_activation="sigmoid",
    ):
        super(Autoencoder, self).__init__()
        self.num_items = num_items
        self.emb_size = emb_size
        self.hidden_activation = Activation(
            hidden_activation, name="hidden_activation"
        )
        self.output_layer = Dense(num_items, name="output_layer")
        self.output_activation = Activation(
            output_activation, name="output_activation"
        )

    def build(self, input_shape):
        self.embedding = self.add_weight(
            name="embedding",
            shape=(self.num_items, self.emb_size),
            trainable=True,
        )
        self.bias = self.add_weight(
            name="bias",
            shape=(1, self.emb_size),
            trainable=True,
        )

    def call(self, inputs, training=False):
        items = inputs["items"]
        weights = inputs.get("weights", None)
        if weights is None:
            # equal weights
            weights = items.with_value(tf.ones_like(items, tf.float32))
        # Implement the sparse dense layer (batch_size, emb_size)
        embed = tf.nn.embedding_lookup_sparse(
            self.embedding, items, weights, combiner="sum",
            name="hidden_embed"
        )

        # Add bias
        y = embed + self.bias
```
