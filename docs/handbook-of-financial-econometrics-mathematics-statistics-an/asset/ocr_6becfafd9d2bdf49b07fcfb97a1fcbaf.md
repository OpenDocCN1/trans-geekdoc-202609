# 18.4.2.3 Sentence2vec

The word2vec model (Mikolov et al. (2013a) is used for learning vector representations of words, called “word embeddings”. One of the word2vec models is the continuous bag-of-words (CBOW) model, which predicts target words (e.g., “mat”) from source context words (“the cat sits on the”). Inspired by this idea, sentence2vec is proposed to learn the representation for a sentence. Compared to the word2vec CBOW model, the differences lie in

+   (1) The sentence id will be added during the training process so that each sentence in the training corpus can have a unique id. The sentence id will also be mapped into a vector, called sentence vector, which would be the final vector that we want. In each sentence, the dimension of the sentence vector is the same as the word vector.
+   (2) In the training process, the sentence vector and the word vectors of context will be concatenated as the input to softmax. We show the structure of sentence2vec in Figure 18.14. The sentence vector represents the missing information from the current context and can act as a memory of the topic of the sentence. Therefore, every time we predict the probability of a word (i.e., w(t) in Figure 18.14), we will use the semantic information of the entire sentence.
+   (3) After training, the sentence vector will be obtained and used as the features for the proposed model.

![](bbox=[0.25, 0.7, 0.75, 0.9])

Figure 18.14: The framework of sentence2vec.