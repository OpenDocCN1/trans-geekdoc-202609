

## Probability Factorization and Decoder Output Estimation

The joint probability distribution is expressed as:

$$P(\mathbf{y}_1^{oh}, \mathbf{y}_2^{oh}, \ldots, \mathbf{y}_{N'+1}^{oh} \mid \mathbf{y}_0, \mathcal{X}_{0:N+1})$$

where the superscript $oh$ denotes the corresponding one-hot representation. To simplify notation, the $oh$ superscript will be omitted in this section, and the symbol $\mathbf{y}$ will directly refer to the one-hot representation. Note that we always assume the first token $\mathbf{y}_0$ in the target output sequence is the sequence start embedding.

Following the previous notational convention and applying the probability product rule (Chapter 2), we obtain:

$$
P(\mathbf{y}_1, \mathbf{y}_2, \ldots, \mathbf{y}_{N'+1} \mid \mathbf{y}_0, \mathcal{X}_{0:N+1})
= P(\mathbf{y}_1 \mid \mathbf{y}_0, \mathcal{X}_{0:N+1})
\prod_{n=2}^{N'+1} P(\mathbf{y}_n \mid \mathbf{y}_{n-1}, \ldots, \mathbf{y}_0, \mathcal{X}_{0:N+1})
\tag{19.44}
$$

Now replace the conditional probabilities in the above equation with the corresponding estimates from the decoder output. Recall that all elements of $\mathbf{y}_n$ (the one-hot vector) are zero, except for the $i$-th element (corresponding to the target word ID) which satisfies $y_{ni} = 1$. This yields the following equation:

