# # Self-attention

![](bbox=[0.343, 0.035, 0.883, 0.573])

For each word, we compute an attention weight between that word and all other words

+   - The raw attention of the i-th word to the j-th word is a function of query $q_i$ and key $k_j$
- The raw attention values are put through a softmax to get the final attention weights