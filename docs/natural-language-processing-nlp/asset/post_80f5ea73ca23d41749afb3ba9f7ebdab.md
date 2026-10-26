
**Algorithm 7** Bootstrap sampling for classifier evaluation. The original test set is \(\{x^{(1:N)}, y^{(1:N)}\}\), the metric is \(\delta(\cdot)\), and the number of samples is \(M\).

**procedure** BOOTSTRAP-SAMPLE(\(x^{(1:N)}, y^{(1:N)}, \delta(\cdot), M\))

    **for** \(t \in \{1,2,\ldots,M\}\) **do**
        **for** \(i \in \{1,2,\ldots,N\}\) **do**
            \(j \sim \operatorname{UniformInteger}(1,N)\)
            \(\tilde{x}^{(i)} \leftarrow x^{(j)}\)
            \(\tilde{y}^{(i)} \leftarrow y^{(j)}\)
        \(d^{(t)} \leftarrow \delta(\tilde{x}^{(1:N)}, \tilde{y}^{(1:N)})\)
    **return** \(\{d^{(t)}\}_{t=1}^{M}\)

As the number of bootstrap samples goes to infinity, \(M \to \infty\), the bootstrap estimate is increasingly accurate. A typical choice for \(M\) is \(10^4\) or \(10^5\); larger numbers of samples are necessary for smaller \(p\)-values. One way to validate your choice of \(M\) is to run the test multiple times, and ensure that the \(p\)-values are similar; if not, increase \(M\) by an order of magnitude. This is a heuristic measure of the **variance** of the test, which can decrease with the square root \(\sqrt{M}\) (Robert and Casella, 2013).

## 4.4.4 Multiple comparisons

Sometimes it is necessary to perform multiple hypothesis tests, such as when comparing the performance of several classifiers on multiple datasets. Suppose you have five datasets, and you compare four versions of your classifier against a baseline system, for a total of 20 comparisons. Even if none of your classifiers is better than the baseline, there will be some chance variation in the results, and in expectation you will get one statistically significant improvement at \(p = 0.05 = \frac{1}{20}\). It is therefore necessary to adjust the \(p\)-values when reporting the results of multiple comparisons.

One approach is to require a threshold of \(\frac{\alpha}{m}\) to report a \(p\) value of \(p < \alpha\) when performing \(m\) tests. This is known as the **Bonferroni correction**, and it limits the overall probability of incorrectly rejecting the null hypothesis at \(\alpha\). Another approach is to bound the **false discovery rate** (FDR), which is the fraction of null hypothesis rejections that are incorrect. Benjamini and Hochberg (1995) propose a \(p\)-value correction that bounds the fraction of false discoveries at \(\alpha\): sort the \(p\)-values of each individual test in ascending order, and set the significance threshold equal to largest \(k\) such that \(p_k \leq \frac{k}{m}\alpha\). If \(k > 1\), the FDR adjustment is more permissive than the Bonferroni correction.

Privacy. In these cases, one solution is to publicly release **stand-off annotations**, which contain links to document identifiers. The documents themselves can be released under the terms of a licensing agreement, which can impose conditions on how the data is used. It is important to think through the potential consequences of releasing data: people may make personal data publicly available without realizing that it could be redistributed in a dataset and publicized far beyond their expectations (boyd and Crawford, 2012).

## Measuring inter-annotator agreement

To measure the replicability of annotations, a standard practice is to compute the extent to which annotators agree with each other. If the annotators frequently disagree, this casts doubt on either their reliability or on the annotation system itself. For classification, one can compute the frequency with which the annotators agree; for rating scales, one can compute the average distance between ratings. These raw agreement statistics must then be compared with the rate of agreement by chance — the expected level of agreement that would be obtained between two annotators who ignored the data.

**Cohen’s Kappa** is widely used for quantifying the agreement on discrete labeling tasks (Cohen, 1960; Carletta, 1996),¹¹

$$\kappa = \frac{\text{agreement} - E[\text{agreement}]}{1 - E[\text{agreement}]}.$$ [4.11]

The numerator is the difference between the observed agreement and the chance agreement, and the denominator is the difference between perfect agreement and chance agreement. Thus, $\kappa = 1$ when the annotators agree in every case, and $\kappa = 0$ when the annotators agree only as often as would happen by chance. Various heuristic scales have been proposed for determining when $\kappa$ indicates “moderate”, “good”, or “substantial” agreement; for reference, Lee and Narayanan (2005) report $\kappa \approx 0.45 - 0.47$ for annotations of emotions in spoken dialogues, which they describe as “moderate agreement”; Stolcke et al. (2000) report $\kappa = 0.8$ for annotations of **dialogue acts**, which are labels for the purpose of each turn in a conversation.

When there are two annotators, the expected chance agreement is computed as,

$$E[\text{agreement}] = \sum_k \hat{\Pr}(Y = k)^2,$$ [4.12]

where $k$ is a sum over labels, and $\hat{\Pr}(Y = k)$ is the empirical probability of label $k$ across all annotations. The formula is derived from the expected number of agreements if the annotations were randomly shuffled. Thus, in a binary labeling task, if one label is applied to 90% of instances, chance agreement is $.9^2 + .1^2 = .82$.

¹¹ For other types of annotations, Krippendorff’s alpha is a popular choice (Hayes and Krippendorff, 2007; Artstein and Poesio, 2008).

The remaining problems will require you to build a classifier and test its properties. Pick a multi-class text classification dataset that is not already tokenized. One example is a dataset of New York Times headlines and topics (Boydstun, 2013).14 Divide your data into training (60%), development (20%), and test sets (20%), if no such division already exists. If your dataset is very large, you may want to focus on a few thousand instances at first.

7. Compare various vocabulary sizes of 10², 10³, 10⁴, 10⁵, using the most frequent words in each case (you may use any reasonable tokenizer). Train logistic regression classifiers for each vocabulary size, and apply them to the development set. Plot the accuracy and Macro-F-MEASURE with the increasing vocabulary size. For each vocabulary size, tune the regularizer to maximize accuracy on a subset of data that is held out from the training set.

8. Compare the following tokenization algorithms:
- Whitespace, using a regular expression;
- The Penn Treebank tokenizer from NLTK;
- Splitting the input into non-overlapping five-character units, regardless of whitespace or punctuation.

Compute the token/type ratio for each tokenizer on the training data, and explain what you find. Train your classifier on each tokenized dataset, tuning the regularizer on a subset of data that is held out from the training data. Tokenize the development set, and report accuracy and Macro-F-MEASURE.

9. Apply the Porter and Lancaster stemmers to the training set, using any reasonable tokenizer, and compute the token/type ratios. Train your classifier on the stemmed data, and compute the accuracy and Macro-F-MEASURE on stemmed development data, again using a held-out portion of the training data to tune the regularizer.

10. Identify the best combination of vocabulary filtering, tokenization, and stemming from the previous three problems. Apply this preprocessing to the test set, and compute the test set accuracy and Macro-F-MEASURE. Compare against a baseline system that applies no vocabulary filtering, whitespace tokenization, and no stemming.

Use the binomial test to determine whether your best-performing system is significantly more accurate than the baseline.

14 Available as a CSV file at http://www.amber-boydstun.com/supplementary-information-for-making-the-news.html. Use the field TOPIC_2DIGIT for this problem.
