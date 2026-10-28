# Question 3: What are n-grams, and how are they used in language modeling and feature extraction?

**Answer:** An N-gram is a contiguous subsequence of n words, characters, symbols, or any items taken from a certain text or speech.

Some examples of n-grams are:

+   - **Unigrams (1-grams):** I, love, AI.
+   - **Bigrams (2-grams):** I love, love AI.
+   - **Trigrams (3-grams):** I love AI.

It plays an important role in the probabilistic language models where n-grams are used to predict the word given n-1 previous words. This is beneficial in determining the succeeding element in a series. For instance, using the bigram model of probability, the chance of love following I would be calculated using the frequency of the bigram I love.

N-grams are used for generating sequences and in speech recognition, where the n-grams maybe used in estimating the probability of sequences of phonemes or acoustic features to enhance transcription. We can also obtain feature vectors from n-gram representations. Each of the features is related to the presence or frequency within the document of certain n-grams.

Documents are indexed and retrieved using n-grams since they hold information on phrases or just terms that would be useful in document relevance, **named entity recognition (NER)** identifies general patterns of words that make up named entities. This helps in the process of extracting other entities such as the name, place, or even an organization among others. N-grams can be used in part of speech tag which is the process of analyzing sequences