F1-scores of this double loop with the aim of obtaining robust results that are not dependent on the specific texts selected. This setup means a total of more than 30,000 combinations, with almost 3 million iterations.

Which of these combinations of features achieves the highest results in each of the 23 subgenres? Ideally one combination of features performs clearly than the rest. The bar of Figure 65 shows the amount of times that each combination yields the best results for each subgenre.

Figure 65: Best results for each subgenre by feature combinations

![](bbox=[0.203, 0.347, 0.796, 0.568])

No combination is a clear winner and some features perform better with a specific subgenre. There are four combinations of features with higher results than the rest: linguistic annotation +lemmata, tokens, tags + tokens and semantic annotation. This data is ordered using tokens as the baseline, therefore it can happen that some of these three cases of the tokens are actually not better than the rest, only merely as the others. In any case, it is surprising that the apparent difference between linguistic and textual annotation is not greater.

A single value for each subgenre erases much information: In general, a combination of features can have high results when it does not perform the best in any subgenre. In contrast, some features can be lucky with three or four subgenres, but insufficient for the majority of the rest. The box plots of Figure 66 show the results for all classifications, grouping them by feature combinations.