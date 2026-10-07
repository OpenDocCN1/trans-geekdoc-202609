Test Accuracy of the result: We can find the accuracy of the result by interpreting the confusion matrix. By above output, we can interpret 66+24=90 (Correct Output) and 8+3=11 (Incorrect Output).

Visualizing the training set: Finally, we will visualize the training set. To visualize, we will use the ListedColormap of matplotlib library. We divide the region into pixels with 0.01.

```
# Visualizing the training results
from matplotlib import ListedColormap
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max()+1, 0.01), 
                     np.arange(X_set[:,1].min(), X_set[:,1].max()+1, 0.01))
plt.contourf(X1, X2, classifier.predict(np.c_[X1.ravel(), X2.ravel()]).reshape(X1.shape), cmap=ListedColormap('red','green'))
plt.xlim(X1.min(), X1.max())\plt.ylim(X2.min(), X2.max())\for i, j in enumerate(unique): plt.scatter(X_set[:,0], X_set[:,1], c=j, label=j)
plt.title('Logistic Regression Training')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

In the code we have used the ListedColormap Matplotlib library to use the colormap to visualizing the result.

+   We created two variables x_set and y_set to raise x_train and y_train.

After that, we used the np.meshgrid command to create a Rectangular Grid, which has a range of -1(minimum) to 1 (maximum). The pixel points we have taken are 0.01.

To create a Filled Contour, we have used plt.contour command, it will create regions of provided colors (yellow and blue). In this function, we have passed the classifier.predict to show the predicted data points predicted by the classifier.

Output: By examining the result we will get the following

![](bbox=[0.158, 0.483, 0.833, 0.768])

+   In the graph below-n, we can see that there are some Blue points within the green region and Yellow points within the red region.

+   All these data are the observation points from the training set, which shows the result for purchased variables.

+   This graph is made using two independent variables i.e., Age on the x-axis and Estimated Salary on the y-axis.

+   The Yellow point observations are for which purchased (dependent variable) is probably 1 means user who purchased the SUV car.

+   The Blue point observations are for which purchased (dependent variable) is probably 1 means user who purchased the SUV car.

+   We can also estimate from the graph that the users who are younger with low salary, did not purchase the car, whereas research shows high estimated purchased the car.