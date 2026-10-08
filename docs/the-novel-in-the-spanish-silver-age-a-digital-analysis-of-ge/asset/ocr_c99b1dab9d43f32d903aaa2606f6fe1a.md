there is some linguistic annotation that is ignored, such as the morphological information about gender and number of articles, the number of the different PoS per test, the discursive particles, or the pro.

This list of the 1,000 top linguistic features will be used to enrich what has already been proved to work best, i.e. PoS differentiated multiwords, in an attempt to engineer the best possible features.

A surprising result is that the division between direct speech features and narrative features does not bring any advantage, and can even give worse results. To observe this question more closely, I use the narrative differentiated tokens as features, calculating the coefficients for each one. A pattern is observed in the features ranked by their coefficients. The first token would be the ellipsis in direct speech, followed by the ellipsis in narrative passages. The ellipsis feature was split into two, but the coefficients in the different genres have a very strong correlation (r=0.96). This means that the classifier these two different features with very similar values. This pattern is observed in the entire data frame. The correlation of the coefficients between the direct speech (for example *buscar_ds*) and its counterpart in narrative passages (*buscar_nr*) tends to be very strong or even perfect. In summary, the split of the features by their position in passages has mainly brought redundancy to the table of features, which explains that the results were not improved. The information about direct speech seems to be important for the classification, but apparently the classifiers are able to access it only through the typographical information of the em dashes.

# 6.1.4 Parameters Evaluation

After analyzing the features in their combinations and linguistic categories, it is necessary to optimize the rest of the parameters. For this, I run a grid search of five different parameters to determine which one show a better performance. In a binary task. Since the previous section did not show a feature combination that worked better in every case, I used five different combinations which had already achieved good results:

+   - Tokens
- Semantic annotation
- Lemmata + linguistic annotation
- TEI-tags + tokens