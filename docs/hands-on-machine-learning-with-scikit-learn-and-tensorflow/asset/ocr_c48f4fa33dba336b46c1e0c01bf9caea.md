```
plt.plot(X_new, y_proba[:], 0], b="b-", label="Not Iris-Virginica")
# + more Matplotlib code to make the image look pretty
```

![](bbox=[0.149, 0.122, 0.85, 0.311])

Figure 4-23. Estimated probabilities and decision boundary

The petal width of Iris-Virginica flowers (represented by triangles) ranges from 1.4 cm to 2.5 cm, while the other iris flowers (represented by squares) generally have a smaller petal width, ranging from 0.1 cm to 1.8 cm. Notice that there is a bit of overlap. Above 2 cm the classifier is highly confident that the flower is an Iris-Virginica (it outputs a high probability to class), while below 1 cm it is highly confident that it is not an Iris-Virginica (high probability for the "Not Iris-Virginica" class). In these extremes, the classifier is unsure. However, if you ask it to predict using the predict() method rather than the predict_proba(), it will return whichever class is the most likely. Therefore, there is a decision boundary around 1.6 cm where both probabilities are equal to 50%; if the petal width is higher than 1.6 cm, the classifier will predict that the flower is an Iris-Virginica, or it will predict that it is not (even if it is not very confident)

```
>>> log_reg.predict([[1.7], [1.5]])
array([[1], [0]])
```

Figure 4-24 shows the same dataset but displaying two features: petal width and length. Once, the Logistic Regression classifier can estimate the probability that a new flower is an Iris-Virginica based on these two features. The dashed line represents the points where the model estimates a 50% probability: this is the model's decision boundary. Note that it is a linear boundary. Each parallel line represents the points where the model outputs a specific probability, from 15% (bottom left) to 90% (top right). All the flowers beyond the top-right line have an over 90% chance of being Iris-Virginica according to the model.

18 is the set of points x such that $\theta_0 + \theta_1x_1 + \theta_2x_2=0$, which defines a straight line.