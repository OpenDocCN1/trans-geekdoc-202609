# Classification with Logistic Regression

The betas from gradient descent are

[-20.75395723, 1.1041736, 0.22893847]

Rounding to four decimal places, the result matches. Figure 14.2 plots the log-likelihood versus the number of iterations. The curve increases to a stable value relatively quickly. Hopefully, this illustration provided a greater understanding of how the parameter estimates can be computed. There is a wide range of models in machine learning, and the parameters are often estimated using some form of gradient descent.

![](bbox=[0.288, 0.335, 0.712, 0.525])

Figure 14.2: Convergence of Gradient Descent

# 14.2.3 Model Performance Evaluation

In this section, we compare predictions on the test set to the actual labels. When producing predicted labels from predicted probabilities, a threshold needs to be applied. The threshold in sklearn is 0.50 by default. A different threshold can sometimes give better results, and we will consider this next. The metrics we use are accuracy, recall, precision, and F1 score. These were introduced in Chapter 11. There are several ways to calculate the metrics: according to the definition, with an individual function from sklearn such as recall(), or with the function classification_report() which computes metrics in batch. Let's first run classification_report() and review the output. The function takes actual labels and predicted labels, in this order.

```
print(classification_report(y_te, model.predict(x_te))
      precision recall f-score support
```