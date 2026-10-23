![](bbox=[0.05, 0.05, 0.95, 0.35])



A = S(S) = exp ( S / diag(S1_N) ) (15.29)

(The expression S1_N is a vector that sums along the columns of S, as explained in Eq. (C.76), and the division is performed elementwise.)

Once we have computed the attention weights, we can perform the dictionary lookup for a batch of queries as follows:

attention(Q, K, V) = A V = exp ( QK^T / diag((QK^T)1_n) ) V (15.30)



If we force the attention heatmap to be sparse, so that each output can only attend to one input location instead of a weighted combination of all of them, the method is called hard attention. This results in a nondifferentiable training objective. However, we can use reinforcement learning methods to fit such models We compare these two approaches for an image captioning problem, as shown in Fig. 15.16b. See [Xu+15] for the details.

It seems from the above examples that these attention heatmaps can “explain” why the model generates a given output. However, the interpretability of attention is controversial (see e.g., [JW19; WP19; SS19; Bru+19] for discussion).



The transformer model [Vas+17] is a seq2seq model which uses attention in the encoder as well as the decoder, thus eliminating the need for RNNs, as we explain below. Transformers have been used for many (conditional) sequence generation tasks, such as machine translation [Vas+17], constituency parsing [Vas+17], music generation [Hua+18], protein sequence generation [Mad+20; Cho+20],