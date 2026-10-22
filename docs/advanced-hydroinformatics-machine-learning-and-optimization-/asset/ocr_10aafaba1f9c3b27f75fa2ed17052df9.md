![](bbox=[0.26, 0.16, 0.66, 0.43])

Unique newspaper articles

Figure 10.5 News-filtering process.

these are words that do not add much meaning value to a sentence or a document. The bag of stop words can be obtained from the GitHub collective repository at https://github.com/Alir3z4/stop-words. Other stop words were added to the bag, following a trial-and-error procedure on the article text, regarding the dialect.

# 10.3.5. Step 5 (Text Vectorization–Tokenization)

Subsequently, the feature text identification or tokenization started with the word embedding, applying the Word2Vec function, which provides concepts for the word embedding (Goldberg & Levy, 2014). The Word2Vec method identifies text mapping and then creates a model for reproducing such mappings to generate “word embedding” (given a text corpus), which is the process of mapping words to a vector space to realize statistical and probabilistic operations. The most important objective of this method is to preserve the relation between words, this is minimizing the distance between vectors within a similar context. In example, while through a tokenization, it is possible to represent the word flood in a text corpus X as [0,0,0,0,0,0,1,0,0,0,0,0] and the word drought as [0,0,1,0,0,0,0,0,0,0,0,0], where the vector size is equal to the vocabulary in the text corpus, these vectors do not show any relation between the meaning of the words flood and drought, both extreme event opposites within the hydrological cycle.