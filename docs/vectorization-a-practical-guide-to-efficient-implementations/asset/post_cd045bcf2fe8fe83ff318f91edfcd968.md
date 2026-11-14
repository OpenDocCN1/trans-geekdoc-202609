
```value_index=tf.lookup.TextFileIndex.LINE_NUMBER,
key_dtype=tf.string,
value_dtype=tf.int64,
value_index_offset=1, # index starts at 1
),
default_value=0, # oov
)
# Apply the lookup
index = table.lookup(values)
# <tf.Tensor: shape=(6,), dtype=int64, numpy=array([26, 1, 3, 4, 8, 0])>
# Clean up the temp file
os.remove(file_path)
```

When using Keras with Tensorflow, keras.layers.StringLookup, building on top of tf.lookup, offers additional ways to incorporate string to integer indices lookup tables inside a Keras model. It also provides further post-processing to transform the integer indices into common labeling schemes such as one-hot encoding or Term Frequency-Inverse Document Frequency (TF-IDF).

## 6.4.5 TorchText torchtext.vocab

Since PyTorch torch.Tensor does not handle strings and bytes, the library itself does not provide a way to handle the transformation from string values to integer indices and relies on custom preprocessing. TorchText is a library currently in pre-release (at the time of writing, the most recent version is 0.16) that implements text pre-processing utilities for NLP tasks. torchtext.vocab.vocab is the method to convert string values to integer indices based on a lookup table from a predefined dictionary which maps between the string value and the frequency of occurrence of the value. It sorts the order of the index based on the frequency, with the lowest frequency as the starting index.

```
# !pip install torchtext==0.16.0
import torchtext
# A dictionary that maps between vocabulary and frequency of
# occurrence
# This creates a->0, b->1, c->2
vocab = {"a":1, "b": 2, "c":10}
# Special tokens to insert at the beginning of the
# vocabulary
```

```
7 # The mapping now becomes <pad>->0, a->1, b->2, c->3
8 vocab_lookup = torchtext.vocab.vocab(
9     vocab, specials=["<pad>"], special_first=True
10 )
11 # handle oov, anything else, use -1
12 vocab_lookup.set_default_index(-1)
13 # look up values: "d" is oov, "<pad>" is special which maps
14 # to index 0
15 values = ["a", "c", "b", "d", "<pad>"]
16 # Look up a single value
17 index = vocab_lookup["a"] # 1
18 # Look up an array of values
19 indices = vocab_lookup.lookup_indices(values)
20 # [1, 3, 2, -1, 0]
```

A nice feature that torch.vocab has is the ability to build the vocabulary iteratively, instead of predefined the vocabulary by summarizing the data (cf. tensorflow_transform.compute_and_apply_vocabulary, a Tensorflow extension library that allows iterative vocabulary building but requires the mastery of Tensorflow Extended [TFX]). For instance,

```
1 from torchtext.vocab import build_vocab_from_iterator
2
3 def get_feature(feature_batch):
4     for feature in feature_batch:
5         yield feature
6
7 feature_batch = [["a", "b", "c"], ["a", "d", "c"], ["f", "g"]]
8 vocab_lookup = build_vocab_from_iterator(
9     get_feature(feature_batch), specials=["<pad>"]
10 )
11 vocab_lookup.set_default_index(-1) # oov
12
13 # look up values
14 values = ["a", "g", "2", "<pad>"]
15 index = vocab_lookup.lookup_indices(values)
16 # [1, 6, -1, 0]
```

## 6.5 Case Study: Factorization Machine

Factorization Machine (FM), proposed by Steffen Rendle in 2010 [Rendle, 2010], is a supervised machine learning algorithm that can be used for classification, regression, and ranking tasks. It is a combination of linear regression and matrix factorization. It also uses a polynomial kernel. Thus, FM is an extension of basic matrix factorization, since it can model not only user and item ids as inputs but also contextual features such as item attributes, user characteristics, and user behavior contexts. FM is used as a strong baseline model in building recommendation engines in e-commerce, media streaming, and advertising industries. The strengths of FM are:

- 1. It can model d-way feature interaction, where d is the order of polynomial, i.e. typically set to d = 2.
- 2. A fast optimization algorithm for FM can reduce polynomial computation time to linear complexity.

Let's first examine the mathematical formulation of FM.

### 6.5.1 Factorization Machine Model

Let x ∈ R^n denote a d-dimensional feature vector of a sample, and y denote the label data, which can be real values (in regression models) or class labels. The model for a Factorization Machine of degree 2 is

```
ŷ(x) = w₀ + Σ(wᵢxᵢ) + ΣΣ⟨vᵢ, vⱼ⟩xᵢxⱼ
```

where

- • w₀ ∈ R is the global mean
- • wᵢ ∈ Rⁿ is the weights of the ith feature
- • V ∈ Rⁿˣᵏ represents the feature embeddings
- • vᵢ represents the ith row of V
- • k is the number of latent factors
- • ⟨·, ·⟩ is the dot product between two vectors. Thus, ⟨vᵢ, vⱼ⟩ models feature interactions

The third term is the feature interaction term. Notice that we are modeling interactions for j > i. Although FM can be generalized to higher orders than order 2, the numerical stability is not great. The generalization to d-way FM is

```
ŷ(x) = w₀ + Σwᵢxᵢ + ΣΣ...Σ(Πxᵢⱼ)(ΠΠv⁽ˡ⁾ᵢⱼ,𝒇)
```

with time complexity O(knᵈ), where

- • l is the index of the interactions, from 2 to d
- • f is the index of latent factors, from 1 to kₗ

### 6.5.2 More Efficient Optimization Criterion

The third term adds a nonlinearity to the model, but it is the difficult part for optimization (O(kn²), n² since all pair-wise interactions of features have to be computed, and the length of the latent factors is \( k \)). Rearrangement of the third term can reduce the time complexity to \( O(kn) \), which is linear.

\(\sum_{i=1}^n \sum_{j=i+1}^n \langle \mathbf{v}_i, \mathbf{v}_j \rangle x_i x_j\)
\(= \frac{1}{2} \sum_{i=1}^n \sum_{j=i+1}^n \langle \mathbf{v}_i, \mathbf{v}_j \rangle x_i x_j - \frac{1}{2} \sum_{i=1}^n \langle \mathbf{v}_i, \mathbf{v}_i \rangle x_i x_i \text{ (upper triangle – diagonal entry)}\)
\(= \frac{1}{2} \left( \sum_{i=1}^n \sum_{j=1}^n \sum_{f=1}^k v_{i,f} v_{j,f} x_i x_j - \sum_{i=1}^n \sum_{f=1}^k v_{i,f} v_{i,f} x_i x_i \right) \text{ (expanding the dot product)}\)
\(= \frac{1}{2} \sum_{f=1}^k \left( \left( \sum_{i=1}^n v_{i,f} x_i \right) \left( \sum_{j=1}^n v_{j,f} x_j \right) - \sum_{i=1}^n v_{i,f}^2 x_i^2 \right) \text{ (factor out the feature summation)}\)
\(= \frac{1}{2} \sum_{f=1}^k \left( \left( \sum_{i=1}^n v_{i,f} x_i \right)^2 - \sum_{i=1}^n v_{i,f}^2 x_i^2 \right)\)

For sparse features, only nonzero elements need to be computed so that the overall complexity is linear to the number of nonzero features.

The final model can be written as

\(\hat{y}(x) = w_0 + \sum_{i=1}^n w_i x_i + \frac{1}{2} \sum_{f=1}^k \left( \left( \sum_{i=1}^n v_{i,f} x_i \right)^2 - \sum_{i=1}^n v_{i,f}^2 x_i^2 \right) \quad (6.1)\)

### 6.5.3 Implementation of Deep Factorization Machine in Tensorflow

### Warning

I used the following versions of the Python packages on M1 MacBook Pro 2021 to build the exercise on DeepFM. Specifically, older versions of `pandas` may throw errors when loading the data or may handle the unicode characters incorrectly.

```
python==3.10.6
numpy==1.24.3
pandas==2.1.1
tensorflow==2.13.0
keras==2.13.1
```

We use Keras API in Tensorflow to implement the Deep Factorization Machine (DeepFM) [Guo et al., 2017] algorithm. This is a simple modification of the FM algorithm by adding a deep neural network component to help predict the final output. Recall that a dense feedforward neural network is implementing the following equation:

$z = \sigma(xw + b)$

where $\sigma$ is some activation function such as the sigmoid function. $x$ typically represents a vector input in batches, while $w$ and $b$ are weight matrices and bias vectors, respectively.

The class `KerasDeepFactorizationMachine` contains a set of methods to implement the mathematical formulations of DeepFM and returns a Keras Model object in the `build_model` method via Keras’ functional API. Of course, one can also choose to subclass the `keras.Model` class for its implementation and create another build function separately in order to take advantage of the `model.fit` and `model.evaluate` APIs later on.

```
from typing import List

from keras import Model, Input
import keras.backend as K
from keras.layers import (
    Concatenate,
    Flatten,
    Lambda,
    Embedding,
    Reshape,
    Dense,
    Dropout,
    Add,
    Activation,
)

from keras.regularizers import l2

class KerasDeepFactorizationMachine:
    """
    Parameters:
    --------
    * feature_name: name of the features. For the purpose of
    distinguishing between feature names in each keras steps
    * feature_size: a list of size of each features, in the correct
    order. This is the number of unique categories of the feature.
    If the feature is continuous, use 0.
    * num_label: a list of integers, in the correct order of the
    features, that indicates the number of labels applied to a
    multilabel categorical feature.
    - For non-multilabel categorical features, use 1;
    - For continuous features, use 1;
    - Otherwise, specify the maximum number of multi-labels
    * emb_size: embedding size
    * hidden_layer_dim: list of hidden layer dimensions for
    Multilayer perceptron part of the Deep Factorization Machine.
    If None or empty [], DPM becomes FM.
```
