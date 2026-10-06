# 70 MATHEMATICS FOR MACHINE LEARNING

Now we can find the entropy of the whole dataset using the entropy formula

$H(S) = \sum_{i=1}^{N} p_i \log_2 p_i$

So total values or N is 10 and propbability of Avg. Sales and Max Sales are 3/10 and 7/10 resepectively

$H(S) = \sum_{i=1}^{N} p_i \log_2 p_i$

$H(S) = \frac{3}{10} \log_2 \frac{3}{10} - \frac{7}{10} \log_2 \frac{7}{10}$

$H(S) \approx 0.82$

After obtaining the entropy we can substitute the values in the information gain formula to find the information gain from Discount feature

| Discount | Sales | Gain(A, S) = H(S) - H(A,S) |
|---|---|---|
| 10% | Average | |
| 25% | Maximum | $0.82 - \frac{4}{10}(-\log_2\frac{4}{10} - \frac{2}{4} - \frac{2}{4} - \log_2\frac{2}{4}) +$
| 20% | Maximum | $+\frac{4}{10}(-\log_2\frac{4}{10} - \frac{4}{4} - \frac{1}{4} - \log_2\frac{4}{4}) +$
| 10% | Maximum | $+\frac{2}{1}(-\log_2\frac{1}{2} - \frac{1}{2} - \log_2\frac{1}{2})$ |
| 25% | Average | $=0.82 - 0.4 - 0.0 - 0.2$
| 10% | Maximum | $=0.82 - 0.6$
| 20% | Maximum | $=0.22$ |

The information gain from the Discount feature is 0.22, the feature with highest information gain values is used in models to predict values to get better results. So if Advertisement is the feature then information gain is

![](bbox=[0.137, 0.846, 0.862, 0.953])