and context word co-occurring. This “maximization” is measured using either hierarchical softmax or negative sampling. While both have strengths, by far the most common setup is Skip-Gram with Negative Sampling (SGNS).42

> 42 See word2vec (Wijffels 2021).

An important extension of SGNS is **fastText**, which incorporates “subword” character _n_-grams—for example, “fluffy” is the co-occurrence of “fl”, “lu”, “uf”, “ff”, “fy”. The model averages these _n_-gram vectors to get word vectors, and can even create vectors for out-of-vocabulary words.43

> 43 See fastText (Mouseli­mis 2022) and fastTextR (Schwendinger and Hvitfeldt 2020).

While SGNS has comparable performance to GloVe—depending on the task and tuning parameters, such as window size—one reason SGNS is preferred is that it builds on an intuitive model of language learning (Arseniev-Koehler and Foster 2020). Similar to how LDA topic modeling builds on an understanding of the writing process, the idea that people learn the meaning of words through exposure to sequences of words is built into the sliding window architecture. Humans don’t have the benefit of the “global” co-occurrence statistics like GloVe. So, it is not a “plausible” learning process.

There are technical reasons to prefer GloVe, though. First, it is computationally simpler. Second, the average cosine between all words in GloVe is much larger than SGNS; SGNS distributes words in narrower corridors of the embedding space.44 This can be partially solved with post-processing techniques, such as subtracting the overall mean from SGNS embeddings (Mu et al. 2017).

> 44 “Spreading out” words in the space (isotropy) generally improves embeddings on various tasks (Arora et al. 2016; Mu et al. 2017).

# Contextualized Embeddings: ELMo and BERT

Recall that a _token_ is an instance of a word (or _n_-gram) in a text, while a word _type_ is a unique word (or _n_-gram). The previous methods could be said to produce _type embeddings_: each unique word has a single vector. The obvious benefit of this is efficiency. These are also sometimes called “static” embeddings because they do not change with a word’s specific context. However, we know that the same words can evoke various senses in different contexts, which may be semantically related or unrelated (i.e., homonyms). A common example is a _financial_ bank versus a _river_ bank.

The tricky question is: How many senses does a word have and how do we define the boundary between senses? Type embeddings overcome this question by trying to summarize all possible senses. So-called contextual models solve this by going in the opposite direction: creating _token embeddings_, which assign a vector to a word in a single context. This