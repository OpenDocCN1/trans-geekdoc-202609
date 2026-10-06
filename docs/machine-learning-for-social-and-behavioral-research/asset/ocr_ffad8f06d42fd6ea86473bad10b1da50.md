288 Machine Learning for Social and Behavioral Research

to suggest potential replacement words for the misspelled ones. Finally, we replace the misspelled words with the suggested correct words.

# Word Stemming

Sometimes, different forms of a word that mean the same thing might be used. For example, "loves," "loving," and "loved" are all tenses of the word "love." "Better" and "best" are the comparative and superlative adjectives of "good." In such situations, it is often useful to reduce the related words to their word stem, base, or root form, e.g., "love" and "good" in the above examples. Many algorithms are available to conduct word stemming dating back to the work by Lovins (1968). Programs such as Hunspell can be used word stemming.

# 11.4.2 Text Tokenization

In analysis, tokenization is the process of breaking text into pieces such as keywords, phrases, symbols, and other elements called tokens. Tokens are often in the form of individual words, but they can also be sentences, paragraphs, or even chapters. They do not necessarily consist only of words. For example, they can be special characters such as punctuation marks and emojis, depending on the purpose of the analysis. The tokens from tokenization are machine readable and can then be analyzed.

We use the text in the listing below as an example. One way is to tokenize the text into individual sentences as tokens (see below). This is typically by dividing the text by punctuation marks. Such tokenization can be useful in natural language processing where we are interested in the size of a paragraph and the length of a sentence. For this example, there are five sentences in the text. Note that it does not check whether a sentence is grammatically correct or not.

+   [1] "My favorite Professor by far."
[2] "He is very helpful and willing to give you out the best he can."
[3] "He will not just give you answers however, but help guide you so that you can learn it on your own."
[4] "I definitely recommend taking him for whatever math courses you can."
[5] "He requires a lot of work, but it pays off in the run!"