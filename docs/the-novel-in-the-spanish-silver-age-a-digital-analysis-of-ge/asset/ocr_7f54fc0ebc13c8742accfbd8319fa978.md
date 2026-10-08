For example, Bazón wrote many naturalist novels; in a subgenre task, the classifier might use her lexical frequency distribution (her authorial cue or signal) to classify naturalist novels. In previous research, I have attempted to penalize the authorial similarity between texts after calculating the Delta distances (Calvo Tello et al. 2017). This transformation has a similar goal, but works with the original frequency of features before adding them into the Delta matrix.

The goal of this transformation is to standardize the frequencies of each text using all the works of the same author. The word *of* has a relative frequency of 0.045 in *Los pazos de Ulloa*, considering that this text was written by Bazán, how expect is this value? This frequency high or low in her novels? To calculate this *authorial-zscores*, the frequency of each text is standardized by a subset of novels written by the author:

# Formula 7

![](bbox=[0.366, 0.517, 0.633, 0.549])

The bar plot of Sub-figure A of Figure 51 shows that the *z*-score of *de* ('of') in *Los pazos de Ulloa* is 0.25 z-scores, meaning it is slightly higher than expected for Bazán. On the other hand, the word *el* ('the') almost reaches a 0.75 z-score, meaning that this word occurs very frequently in this text, considering the author's style. The distribution is skewed to the left, although not as much as the corpus-zscores. The data points are distributed below -0.5 and a few cases over 1.5., and in general it resembles a Gaussian distribution.

To make the calculation of authorial-zscores possible, every writer must be represented by more than one text in the data set. But, as seen in Section 3.1.9, many authors have written only one novel, making this requirement unrealistic for literary works. For this reason, I have decided to work with