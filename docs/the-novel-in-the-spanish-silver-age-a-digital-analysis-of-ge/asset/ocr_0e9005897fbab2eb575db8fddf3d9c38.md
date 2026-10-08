**Figure 47:** Plots showing relative tf-idf z-scores in two novels

# Visualization of Rel-tfidf-z-scores Frequency

Sub-figure A:
Bar Plot with Frequency of 20 MFW in Two Novels

![](bbox=[0.183, 0.263, 0.513, 0.417])

Sub-figure B:
Histor of 2000 MFWs
mean = -0.01
standard deviation = 0.65

![](bbox=[0.535, 0.263, 0.835, 0.417])

Sub-figure C:
Box Plot of 2000 MFWs
Median = -0.14
IQR = 0.0

![](bbox=[0.183, 0.477, 0.513, 0.624])

Sub-figure D:
Scatter Plot of Frequencies
Correlation (Pearson's r) = 0.0
p-value = 1.0

![](bbox=[0.535, 0.477, 0.835, 0.624])

tive frequency. A possible variation of this would be to transpose the tf-
el-zscore. However that would be harder to defend because the tf-idf
is specifically proposed for the frequencies of words. In contrast, a z-score
tformation is independent of the type of data, and therefore it is legiti-
m to apply it after the tf-idf weighting.



Until now all variants are based on the Bag of Words document model in
which the frequency expresses the number of times the feature appears in
t document. In a way, the BoW model can be understood as the sum of