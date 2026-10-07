# PERFORMANCE EVALUATION OF ML AND DL TECHNIQUES 41

![](bbox=[0.215, 0.114, 0.786, 0.342])

**Figure 2.12** Structure of random forest classification. (Source: medium.com [47]).

hence some of the criteria like Gini Index, Gain Ratio, or Chi Square can be used for deciding the Root node.

# 2.3.5.3 Random Forest Classifier

Random forest classification task is already described in section 2.3.4.2, the model described in 2.3.4.2 was a regression algorithm which takes the average of the score and predict the values [46]. In the case of classification task and voting is done for all the trees, which have the highest vote is chosen as the final output of the model as shown in Figure 2.12.

# 2.3.5.4 Naive Bayes Classifier

Naive bay classifier is one of the Bayes theorem-based classification algorithm, which makes prediction on the base of probabilities, and is applied in most of the classification applications including, sentiment analysis, spam detection in mails, etc [48]. Bayes theorem is mathematically described as shown in Equation 2.7

```
$P(A | B) = \frac{P(B|A)P(A)}{P(B)} \quad (2.7)$
```

where P(A|B) chance of A occurring in event B; P(B|A) change of B being true; P(A) chances of A occurring; P(B) chances of B occurring.