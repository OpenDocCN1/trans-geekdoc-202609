score,” which is a modified way of computing their average, and works better than simply taking the mean.⁴

| Classifier | Precision | Recall | F1 score |
|------------|-----------|--------|----------|
| A | 95% | 90% | 92.4% |
| B | 98% | 85% | 91.0% |

Having a single-number evaluation metric speeds up your ability to make a decision when you are selecting among a large number of classifiers. It gives a clear preference ranking among all of them, and therefore a clear direction for progress.

As a final example, suppose you are separately tracking the accuracy of your cat classifier in four key markets: (i) US, (ii) China, (iii) India, and (iv) Other. This gives four metrics. By taking an average or weighted average of these four numbers, you end up with a single number metric. Taking an average or weighted average is one of the most common ways to combine multiple metrics into one.

⁴ If you want to learn more about the F1 score, see https://en.wikipedia.org/wiki/F1_score. It is the “harmonic mean” between Precision and Recall, and is calculated as 2/((1/Precision)+(1/Recall)).