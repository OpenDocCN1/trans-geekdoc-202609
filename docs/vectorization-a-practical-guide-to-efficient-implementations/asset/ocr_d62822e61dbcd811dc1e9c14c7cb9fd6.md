```
```python
Returns:
----------------
* attention: attention score (..., l_q, depth_out)
* weights: weights of the value when summing the value (..., l_q, l_k)
"""
# Cosine/dot product similarity
# Q K.T, (..., l_q, l_k)
logit_score = tf.matmul(query, key, transpose_b=True)

# scale by dimension of key
d_k = tf.cast(tf.shape(key)[-1], tf.float32)
scaled_logit_score = logit_score / tf.sqrt(d_k)  # (..., l_q, l_k)

# Masking the region by a large negative number (est. -inf)
if mask is not None:
    scaled_logit_score += mask * -1e9  # (..., l_q, l_k)

if causal:
    l_q = tf.shape(query)[-2]
    l_k = tf.shape(key)[-2]
    # creates an upper triangular mask to retain lower triangular
    # matrix
    causal_mask = 1 - tf.linalg.band_part(
        tf.ones((l_q, l_k), tf.float32), -1, 0
    )
    scaled_logit_score += causal_mask * -1e9

# weights: softmax normalization
weights = softmax(scaled_logit_score, axis=-1)
# Add dropout
weights = tf.nn.dropout(weights, dropout)

# attention (..., l_q, depth_out)
attention = tf.matmul(weights, value)

return attention, weights
```
```

+   * Lines 13 and 14: Key and value must have the same length, i.e. l_k == l_v.
+   * Line 33 implements the dot product part of the attention, between Key and Query QK^T. The logit_score has shape (batch_size, [num_heads,] l_q, l_k), where optionally, num_heads is the number of heads in the case of multi-headed attention.
+   * Line 36 gets the embedding size of the key d_k from the input key.
+   * Line 37 computes the scaled dot product QK^T / sqrt(d_k).
+   * Lines 40 and 41: This handles a case where an additional binary mask is applied on top of the dot product attention. We apply the masking by adding the masked region with a large negative number. This is because, after applying the softmax activation the logit score of large negative numbers will become near 0. For example, softmax([1, -3, 2, -1e9, 5]) = 1.7142441e-02, 3.1397477e-04, 4.6597987e-02,