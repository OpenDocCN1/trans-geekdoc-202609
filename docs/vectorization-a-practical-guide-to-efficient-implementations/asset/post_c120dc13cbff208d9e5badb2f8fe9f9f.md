
```python
# e.g. (1, ..., batch_size, ..., seq_size, ..., 1, ...)
shape = [1] * sequence.ndim
shape[batch_axis] = indices.shape[0]
shape[seq_axis] = indices.shape[1]
indices = indices.reshape(shape)

# reindexing
reversed_sequence = np.take_along_axis(sequence, indices, seq_axis)
return reversed_sequence
```

![](img/e891acaacd4fb5b80dab2ed824618203_376_0.png)

![](img/e891acaacd4fb5b80dab2ed824618203_376_1.png)

Figure 10.4 Illustration of the implementation logic to reverse a padded sequence. (a) Illustration of creating the reverse index mask within the specified sequence lengths. (b) Illustration of the step-by-step process of reordering the sequence.

- Lines 14–17 get the lengths of the sequences within the batch. It performs a check using `assert` to make sure there is one sequence length specified for each sequence in the batch.

- Lines 20–25 create an index reversing mask. We first start with a forward sequence index, [0, 1, 2, ..., seq_len]. Then, use np.where to replace the values via broadcasting: if the forward index is less than the specified sequence length, then compute the reverse sequence index as seq_lengths - 1 - indices; otherwise, retain the current forward index. See Figure 10.4a for an illustration (bottom matrix labeled as “index mask”).

- Lines 29–32 reshape the index masking in order to handle higher-dimensional cases. The batch and sequence dimensions make up the two dimensions of the index masking matrix. To handle the rest of the dimensions, we rely on broadcasting to slice the higher-dimensional sequences using np.take_along_axis.

- Line 35 uses np.take_along_axis to reorder the sequence. See Figure 10.4b for an illustration of the underlying iterative process.

A PyTorch version can also be implemented by simply changing the NumPy function to the corresponding PyTorch functions

```python
import torch

def torch_reverse_sequence(
    sequence: torch.Tensor,
    seq_lengths: list,
    seq_axis: int = 1,
    batch_axis: int = 0,
):
    seq_lengths = torch.asarray(seq_lengths, dtype=int)[:, None]
    assert sequence.shape[batch_axis] == len(
        seq_lengths
    ), "length of seq_lengths must be equal to sequence.shape[batch_axis]"

    # creating reversing indices via masking (batch_size, seq_len)
    indices = torch.arange(sequence.shape[seq_axis])
    # if within specified sequence length, create the reverse index
    # otherwise, retain the forward index
    indices = torch.where(
        indices < seq_lengths, seq_lengths - 1 - indices, indices
    )

    # Add additional singleton dimensions for broadcasting
    # e.g. (1, ..., batch_size, ..., seq_size, ..., 1, ...)
    shape = [1] * sequence.ndim
    shape[batch_axis] = indices.shape[0]
    shape[seq_axis] = indices.shape[1]
    indices = indices.reshape(shape)

# reindexing
reversed_sequence = torch.take_along_dim(sequence, indices, seq_axis)
return reversed_sequence
```

We can verify the implementation by testing a couple of examples against Tensorflow's implementation.

```python
import numpy as np
import tensorflow as tf
# Create a 2D example
sequence = np.array([
    [3, 4, 7, 8, 0, 0, 0, 0],
    [2, 3, 5, 0, 0, 0, 0, 0],
    [8, 7, 6, 5, 4, 0, 0, 0],
])
batch_axis = 0
seq_axis = 1
seq_lengths = [4, 6, 5]
reversed_sequence_np = reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
reversed_sequence_tf = tf.reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
assert np.allclose(reversed_sequence_np, reversed_sequence_tf)
# Create a 3D example. The batch and sequence axes are not defaults.
# batch_axis = 1, seq_axis = 2
sequence = torch.asarray(
    np.array([
        [
            [3, 4, 7, 8, 0, 0, 0, 0],
            [2, 3, 5, 0, 0, 0, 0, 0],
            [8, 7, 6, 5, 4, 0, 0, 0],
        ],
        [
            [2, 4, 6, 8, 0, 0, 0, 0],
            [4, 6, 10, 0, 0, 0, 0, 0],
            [16, 14, 12, 10, 8, 0, 0, 0],
        ],
    ])
)
batch_axis = 1
seq_axis = 2
# Here padding is also not always 0 and valid sequence value is not
# always > 0
seq_lengths = [4, 6, 3]

reversed_sequence_np = reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
reversed_sequence_tf = tf.reverse_sequence(
    sequence, seq_lengths, seq_axis=seq_axis, batch_axis=batch_axis
)
assert np.allclose(reversed_sequence_np, reversed_sequence_tf)
```

## 10.5 Case Study: Gumbel-Max Sampling with Weights

When training a multi-class classification algorithm, we activate the final layer, whose output we denote as \(\theta\), with a softmax function to obtain the probabilities of each class,

\(p_i = \text{softmax}(\theta_i) = \frac{e^{\theta_i}}{\sum_j^N e^{\theta_j}}\)

where we denote \(p_i\) as the probability of the class \(i\); \(N\) is the number of classes; \(\theta_i\) as the unactivated final layer output for class \(i\), which is often referred to as the logit value of the class. By inverting the softmax function, we can compute the logit value from the probability as

\(\theta_i = \log \left( p_i \sum_j^N e^{\theta_j} \right) = \log(p_i) + \log(C) = \log(p_i) + C\)

where \(C\) denotes some constants which we can ignore later on.

In certain areas like recommendation systems and object detection in which the problems are often formulated as multi-class or multi-label classifications, it is common to see negative classes outnumbering the positive ones. The overwhelming number of negative classes can also reduce training efficiency. A way to tackle this is by selecting a set number of negative classes via random sampling. On the other hand, the distribution of positive labels may skew toward those more popular classes. These factors can lead to class imbalance and a model bias toward the more generic classes. To mitigate class imbalance, a viable solution could be reducing the number of negative label classes in the training data by sampling. The sampling can favor more generic classes, making them appear more frequently as negative labels whenever appropriate. This strategy, in turn, would make the tail-end classes show up as negative labels less frequently, thus, motivating the model to learn to predict these less generic classes more effectively. To achieve these goals, we need to implement a sampling without replacement strategy; to achieve these goals efficiently with vectorization, we need to rely on one-pass rather than iterative algorithms for sampling. Hence, our discussion on the Gumbel-Max trick [Huijben et al., 2022] in this section.

Gumbel distribution has the probability density function (PDF) and cumulative density function (CDF) as

\(\text{PDF}_{\text{Gumbel}}(x; \mu, \beta) = \frac{1}{\beta} e^{-\frac{x-\mu}{\beta}} e^{-\frac{x-\mu}{\beta}}\)

\(\text{CDF}_{\text{Gumbel}}(x; \mu, \beta) = e^{-e^{-\frac{x-\mu}{\beta}}}\)

The standard Gumbel distribution is obtained by setting \(\mu = 0, \beta = 1\), and the PDF and CDF become

\(\text{PDF}_{\text{Gumbel}}(x; 0; 1) = e^{-x-e^{-x}}\)

\(\text{CDF}_{\text{Gumbel}}(x; 0; 1) = e^{-e^{-x}}\)

Let \(G\) denotes a sample obtained from the standard Gumbel distribution. The Gumbel-Max trick suggests that to sample from the softmax distribution whose unactivated logits are denoted by \(\theta_i\), we can first obtain the index \(I\) of the sample among the \(N\) classes using

\(I = \text{argmax}_{i \in \{1, ..., N\}} (\theta_i + G^{(i)})\) (10.1)

where the term inside the parentheses is often called perturbed logits. Since we can predetermine how we want to sample (e.g. popularity based or simply random uniform), we can designate the probability of each class \(p_i\). Therefore, we can rewrite Equation 10.1 in terms of \(p_i\),

\(I = \text{argmax}_{i \in \{1, ..., N\}} (\theta_i + G^{(i)}) = \text{argmax}_{i \in \{1, ..., N\}} (\log(p_i) + C + G^{(i)})\) (10.2)

where \(C\) is the normalizing constant. However, \(C\) does not impact the order of the perturbed logits term since it simply shifts the values for all classes by the same value. We can, therefore, drop the term, and obtain

\(I = \text{argmax}_{i \in \{1, ..., N\}} (\log(p_i) + G^{(i)})\) (10.3)

To sample \(G^{(i)}\) for each class \(i\), we use the inverse transform sampling technique. This is done by first sampling from the uniform distribution \(y \sim U(0, 1)\), and then using the inverse cumulative distribution function (ICDF) to compute the sample value. The ICDF of the standard Gumbel distribution is

\(\text{CDF}_{\text{Gumbel}}^{-1}(y) = -\log(-\log y)\) (10.4)
