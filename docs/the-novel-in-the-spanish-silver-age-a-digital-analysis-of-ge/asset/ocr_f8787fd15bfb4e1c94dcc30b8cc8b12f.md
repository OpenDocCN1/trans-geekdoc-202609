# 4.2 Transformations of Lexical Data and Linguistic Annotation

Figure 45: Plots showing relative z-score frequency in two novels

# Visualization of Rel-zscores Frequency

![](bbox=[0.135, 0.206, 0.439, 0.412])

![](bbox=[0.498, 0.206, 0.796, 0.412])

![](bbox=[0.135, 0.442, 0.439, 0.603])

![](bbox=[0.498, 0.442, 0.796, 0.613])

Why these transformations deviate and what causes this? These features appear in the Los pazos de Ulloa and are very infrequent in the rest of the corpus. The difference is that a feature can have a high t-idf if its frequency was high, such as the names of the protagonists *Nucha, Julián*. As already pointed out, the t-idf still correlates with the original frequency. On the contrary, the z-score transformation does not correlate with the original, and therefore it is able to assign high values, when the feature occurs only once in the text (such as zahumadas or ahúmas, which are extremely rare words in Spanish). The specific names of the protagonist are expected to be so informative for genre classification, and therefore I expect z-scores to be a better transformation than t-idf for this task.