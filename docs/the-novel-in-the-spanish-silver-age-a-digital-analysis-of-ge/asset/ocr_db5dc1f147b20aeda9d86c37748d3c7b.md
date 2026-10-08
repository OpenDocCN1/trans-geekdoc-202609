# The Novel in the Spanish Silver Age

the data set? To answer this, the mean in the corpus is subtracted from each value, and then divided by the standard deviation in the corpus (Formula 4).

Formula 4

![](bbox=[0.437, 0.303, 0.555, 0.348])

The z-scores of lexical information are usually calculated from the relative frequency (rel-zscores).

The features can now have positive and negative values, as it can be seen in Sub-figure A of Figure 45 with values from minus to six. These scores are standard deviations of the mean of the corpus. For example, the el in the text Tirano Banderas has a z-score of three, meaning that its frequency is three standard deviations higher than expected in this corpus. The shape of the histogram (Sub-figure B) is close to a Poisson distribution, with the peak very close to the mean (-0.02). This moderate skewness is also observed in the box plots (Sub-figure C), which have many positive outliers. These are words with a very high frequency in comparison to the rest of the corpus, such as tenebrosisima (very gloomy), yahumadas (uncertain meaning) or ahúmes ('you smoke') for Los pazos de Ulloa, which are all words that appear only in the specific text in the entire corpus. In the fourth plot it can be observed that this transformation has no correlation² with the total frequency.

Among the six transformations already discussed, only two have managed to assign the highest scores to tokens which were not the most frequent: tfidf and z-scores. In tfidf, the highest values were words such as Nucha or Julián, while the highest z-scores are tokens such as tenebrosisima or ahúmes.