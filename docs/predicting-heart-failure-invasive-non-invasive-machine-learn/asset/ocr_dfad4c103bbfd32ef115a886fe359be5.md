incorrect disease prediction [40]. Two common techniques could be applied for handling the data sets: deletion and imputation. Removing missing instances is the most used way for treating missing values, whereby cases that cannot be processed are removed. Despite the simple implementation of this method, it can remove useful information. On the other hand, the imputation method is used where missing values are replaced with estimated values. In our research, the second approach was used. Specifically, we used the nearest neighbor algorithm with k = 5 to impute missing values where a case is imputed using values from the majority of the complete five nearest cases.

# 7.4.3 Performance Measures

Five common evaluation measures were used to assess the efficiency of the prediction models. These evaluation measures were selected as they are widely used to evaluate the efficiency of prediction models. The first measure is Recall, as shown in Equation 7.1, which measures how well a binary classification predicts positive labels. The second measure is precision, as shown in Equation 7.2, which measures the probability that a positive prediction is correct. The third measure is accuracy, as shown in Equation 7.3, which measures the performance of classification. The fourth measure is specificity, as shown in Equation 7.4, which measures how well a binary classification test correctly identifies the negative cases. The last measure is the F-measure, as shown in Equation 7.5, which measures the probability that a positive prediction is correct [32].

```
Recall = 
t_p / (t_p + f_n)
(7.1)
```

```
Precision = 
t_p / (t_p + f_p)
(7.2)
```

```
Accuracy = 
(t_p + t_n) / (t_p + t_n + f_p + f_n)
(7.3)
```

```
specificity = 
t_n / (t_n + f_p)
(7.4)
```

```
F - measure = 
2 x precision x recall / (precision + recall)
(7.5)
```

+   Where:
+   - t_p is true positive.
+   - t_n is true negative.
+   - f_p is false positive.
+   - f_n is false negative.