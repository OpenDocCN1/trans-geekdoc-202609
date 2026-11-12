
## TABLE 3.3 Co-occurrence vectors for four words in the UN corpus

| | ... | biodiversity | sustainable | global | ... |
|---|---|---|---|---|---|
| conservation | ... | 4 | 8 | 0 | ... |
| restoration | ... | 4 | 4 | 0 | ... |
| development | ... | 1 | 16 | 3 | ... |
| transboundary | ... | 1 | 0 | 0 | ... |

given context in the training corpus. As shown in the table, there are 0 instances of *sustainable* and *transboundary* co-occur in the context in the training corpus, whereas 16 instances of the word *sustainable* co-occurring with the word *development*. This is not surprising, as intuitively *sustainable* co-occurs with *development* more often than with *transboundary*.

Three of the dimensions, the three words in the row, are hand-picked for pedagogical purposes: *biodiversity*, *sustainable*, and *global*. These three dimensions of the vector for *conservation* – [4, 8, 0] – are the number of instances that *conservation* co-occurs in context with the three hand-picked words.

This example indicates that there is a correlation between distributional similarity and meaning similarity. We can also see from Table 3.3 that the two words *conservation* and *restoration* are more similar to each other than they are to other target words like *development*, because *biodiversity* tends to occur more often in their window (4 times vs. 1 time).

Figure 3.1 is a spatial visualization of word vectors for *development*, *transboundary*, *conservation*, and *restoration* in a three-dimensional space. From the figure, we can see the distance of the word *development* is farther than *transboundary*, *conservation*, and *restoration*, and the distance between *conservation* and *restoration* is much closer, as the meanings of these two words are very close. Though the training corpus includes only one document with roughly 2,000 words, it demonstrates some alignments between the model prediction and human intuitions. The accuracy of the model may improve when we increase vector dimensionality and the amount of the training data (Mikolov et al., 2013, pp. 6–7).

In a real-life corpus, the vocabulary size is much larger than three hand-picked context words. A real vector would have vastly more dimensions and thus be much less dense, as many words may actually appear in the four-word context window to both the left and the right in the training corpus. The length of the vector is generally the size of the vocabulary, often between 10,000 and 50,000 words. Since most of these numbers are zero, the vector representations are sparse. This is a fundamental problem that makes language modeling and other ML challenges difficult to resolve. As Bengio et al. (2003) point out, “if one wants to model the joint distribution of 10 consecutive words in a natural language excerpt with a vocabulary of size 100,000, there are potentially 100000^10 – 1 = 10^50 – 1 free parameters” (p. 1137). One way to solve this issue is to use the shared patterns of the words to describe them, through which the dimensions of the vector are greatly reduced.

![](img/ec5cbdd0549c7a4e25c06fc472c12208_75_0.png)
FIGURE 3.1 Spatial visualization of word vectors

The co-occurrence matrix in Table 3.3 shows frequencies of words with other words in each cell. But in most cases, raw frequency is not the best measure of association between words. Raw frequency is very skewed and not very discriminative. For example, words like *the*, *a*, and *I* occur frequently with all sorts of words and do not provide much information about any particular word. Simply by examining co-occurrences with these words, one cannot tell what kinds of contexts are shared by *conservation* and *restoration* in contrast to *development* and *transboundary*. Thus, we need to weight words in the vector. A weighting function can be provided using models such as the PPMI (positive pointwise mutual information) model or the tf-idf (term frequency – inverse document frequency) model, with the former being used for term-term matrices (see Table 3.3) and the latter for term-document matrices. Both algorithms are widely employed to compute word similarity, for tasks like finding word paraphrases, tracking changes in word meaning, and automatically discovering meanings of words in different corpora (Jurafsky & Martin, 2020, pp. 106–112). In translation, the tf-idf model is widely used for automated terminology extraction.

To summarize, in the above approach, a word can be represented as a sparse, long vector with dimensions corresponding to words in the corpus vocabulary or documents in a collection. In the next section, we will introduce a more powerful word representation: short dense vectors. Unlike the vectors produced by the PPMI model or the tf-idf model, these embeddings are short, with the number of dimensions d ranging from 50–1,000, rather than the much larger vocabulary size |V| or number of documents.

## 3.3.2.2 Feature vectors

Dense vectors entail feature creation, in which the features may or may not have any obvious relation to the original input but do have comparative value in that similar inputs have similar features. In Section 2.3.1 of Chapter 2, we gave an example of paradigmatic relationships in a sequence. As shown in Figure 3.2, specific features can be extracted based on characteristics of each word category.

As discussed in Section 3.2, statistical language models such as n-gram models are based on conditional probability. The generalization is obtained from sequences of words seen in the training corpus to new sequences of words. When a new combination of n words appears that was not seen in the training corpus, n-gram models look at the probability predicted using a smaller context size. In contrast, feature vectors achieve a higher level of generalization that is not possible with classical n-gram language models. For example, if the phrase the cat is walking in the bedroom is in the training corpus, the generalization a dog was running in a room should be almost as likely, because dog and cat, as with the and a, room and bedroom, etc., have similar semantic and grammatical roles (Bengio et al., 2003, pp. 1137–1140).

Figure 3.2 is a visualization of the generalization obtained when a sequence of words that has not yet occurred has high probability due to the fact that it consists of words that are similar to words in an occurring sequence because they have semantic and grammatical similarity.

If we assign a numeric value to a feature related to ‘animal’, the values for words cat and dog must be greater than those for bedroom and room. Conversely, if the feature is ‘space that can be occupied’, the values for words bedroom and room will be greater than those for cat and dog. These relationships show that the assigned numbers represent meaningful values. They are real value numbers and can be used in mathematical operations. In this sense, feature vectors are in effect distributed representations, as we discussed in Chapter 1. Bengio et al. (2003) state that the feature vectors associated with each word can be “initialized using prior knowledge of semantic features” (pp. 1139–1140). In the case of prior knowledge of semantic features, like parts of speech or name entities, the information can also be passed to the computer program through sequential labeling tasks. The example shown in Figure 3.2 is based on prior human knowledge of semantic features.

Features can also be learned from training data. For example, if dog and cat are found with similar co-occurrences in a particular corpus, e.g., dog and cat both appear with a and the on the left and is and was on the right side of the word, the
![](img/ec5cbdd0549c7a4e25c06fc472c12208_77_0.png)
FIGURE 3.2 Generalization based on semantic and grammatical similarity

computer program can learn that they play similar roles syntactically and semantically. Matrices can be applied to extract features from the distributional structure, such as the term-to-term matrices and term-to-document matrices discussed in Section 3.3.2.1. However, in these models, the length of the vector is generally the size of the vocabulary, often between 10,000 and 50,000 words. This is a fundamental problem that makes language modeling and other learning problems difficult.

This problem can be addressed using neural network language models. In these models, input and output data are fed to the neural network in order for the neural language model to work out fixed-sized feature vectors on its own. Dimensions are learned based on the algorithm and do not have an intuitive interpretation like ‘animal’ or ‘space that can be occupied’ as in earlier examples of manually extracted features.

## 3.3.2.3 Word2vec

Word2vec is a technique to learn word embeddings using shallow neural networks. In this approach, the vector-space word representations are implicitly learned through the input-layer weights, and it has been found that these representations are surprisingly good at capturing syntactic and semantic regularities in language (Mikolov, Yih, & Zweig, 2013, pp. 746–751). Instead of counting how often each
