# Machine Learning Chapter 16: Natural Language Transformation, Part 2

consider lemmatizing or stemming it and checking for instead. Sometimes, vocabularies only contain other variations of a word, but that may give you better results than using an <UNK> token.

+   - Similar words have similar embeddings. That means you may get reasonable results for words in your vocabulary even if they weren't present in your training data, as long as they are in usage to use more data that fully covers your vocabulary is still preferred.
- There have been attempts to create vectors for OOV tokens on the fly, or to use hybrid models that treat OOV tokens at the character level instead of as words. You should research ideas like if you have a project that needs to handle rare or unknown words.

# Key points

+   - Bidirectional recurrent networks produce better encodings in cases wherein context appears before and after an item in a sequence.
- Use beam search with your decoder to produce better translations.
- Seq2Seq models that include attention mechanisms generally out perform those that do not, because they learn to focus on the most relevant parts of sequences.
- Word embeddings encode information about the contexts in which words are used, capturing relationships between words in an unsupervised manner. Using them improves performance on most NLP tasks.
- OOV tokens are more difficult to handle when using word tokens, but you will need a plan for dealing with them because it's much less likely that you'll be fully support your source or target languages at the word level.

# Where to go from here?

These past three chapters have only scratched the surface of the field of NLP. Hopefully, they've shown you how to accomplish useful things in your apps, while sparking your interest to research other topics. What's next?

The past year has brought an important advance in the field of NLP that we didn't cover: language models. While word embeddings are essentially a type of transfer

![](bbox=[0.156, 0.922, 0.843, 0.956])