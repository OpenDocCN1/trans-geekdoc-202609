Still, it is worth observing more closely which combinations of features have surpassed the single feature of tokens. Tags + tokens, mean frequency in chapters, and the PoS differentiated version of tokens and multiwords generally have slightly higher results than tokens alike, but this difference is only significant in one case: the PoS differentiated multiwords (p-value =0.004). This confirms that many other researchers have found, i.e how difficult it is to outperform tokens. A great number of models and annotations do not offer any advantages in this setup, the division of the tokens depending on whether they are narrative or direct speech passages, the mean or standard deviation of the frequencies over chapters, or the isolation of the lexical (lemmata) and grammatical data (linguistic annotation) of the tokens. And yet, tokens are not always the very best features, which means that some features are useful for specific subgenres.

# 6.1.3 Knowledge Extraction about Features

In this section, I analyze more closely some statistical patterns of the linguistic features that are the best predictors of subgenres. First, I look at those features that are stronger cues for differentiating several subgenres. Second, I run a series of experiments concerning hypotheses about which characteristics these features show:

+   - Are the most important features also the most frequent in the text? In other words, does the importance of these features for the classification correlate with their original frequency?
- Can a set of good predictors be established to achieve high results for not only one category, but for all categories?
- Are some Parts of Speech (PoS) more important in the classification than others? Are verbs or nouns more necessary for the classification than pronouns and prepositions? Does punctuation play an important role?

In addition, I look more closely at the results of the several layers of the linguistic and textual annotation, particularly in comparison with the more simple tokens.

The question about how important specific words are for groups of texts has been answered through different traditions. Corpus linguistics has im-