We can compute an empirical approximation to the cross entropy as follows. Suppose we approximate the true distribution with an empirical distribution based on data sampled from \(p\):

\(p_{\mathcal{D}}(x|\mathcal{D}) = \frac{1}{N} \sum_{n=1}^N \mathbb{I}(x = x_n)\) (5.105)

In this case, the cross entropy is given by

\(H = -\frac{1}{N} \sum_{n=1}^N \log p(x_n) = -\frac{1}{N} \log \prod_{n=1}^N p(x_n)\) (5.106)

The corresponding perplexity is given by

\(\text{perplexity}(p_{\mathcal{D}}, p) = 2^{-\frac{1}{N} \log (\prod_{n=1}^N p(x_n))} = 2 \log (\prod_{n=1}^N p(x_n))^{-\frac{1}{N}}\) (5.107)

\(= (\prod_{n=1}^N p(x_n))^{-1/N} = \sqrt[N]{\prod_{n=1}^N \frac{1}{p(x_n)}}\) (5.108)

In the case of language models, we usually condition on previous words when predicting the next word. For example, in a bigram model, we use a second order Markov model of the form \(p(x_n|x_{n-1})\). We define the **branching factor** of a language model as the number of possible words that can follow any given word. For example, suppose the model predicts that each word is equally likely, regardless of context, so \(p(x_n|x_{n-1}) = 1/K\), where \(K\) is the number of words in the vocabulary. Then the perplexity is \(((1/K)^N)^{-1/N} = K\). If some symbols are more likely than others, and the model correctly reflects this, its perplexity will be lower than \(K\). However, we have \(\mathbb{H}(p^*) \le \mathbb{H}_{ce}(p^*, p)\), so we can never reduce the perplexity below \(2^{-\mathbb{H}(p^*)}\).

# ## 5.3 Mutual information

The KL divergence gave us a way to measure how similar two distributions were. How should we measure how dependent two random variables are? One thing we could do is turn the question of measuring the dependence of two random variables into a question about the similarity of their distributions. This gives rise to the notion of **mutual information** (MI) between two random variables, which we define below.

# ### 5.3.1 Definition

The mutual information between rv's \(X\) and \(Y\) is defined as follows:

\(\mathbb{I}(X;Y) \triangleq D_{KL}(p(x,y) \parallel p(x)p(y)) = \sum_{y \in Y} \sum_{x \in X} p(x,y) \log \frac{p(x,y)}{p(x)p(y)}\) (5.109)

(We write \(\mathbb{I}(X;Y)\) instead of \(\mathbb{I}(X, Y)\), in case \(X\) and/or \(Y\) represent sets of variables; for example, we can write \(\mathbb{I}(X; Y, Z)\) to represent the MI between \(X\) and \((Y, Z)\).) For continuous random variables, we just replace sums with integrals.