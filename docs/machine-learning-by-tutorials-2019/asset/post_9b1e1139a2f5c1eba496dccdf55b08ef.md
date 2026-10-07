
## Machine Learning Chapter 5: Digging Deeper into Turi Create

Increasing the number of iterations did help little, so apparently the initial guess of 100 iterations was too low. Tip: For the best results, first train the model with too many iterations, and see at which iteration the validation accuracy starts to become worse. That's your sweet spot. Now train again for exactly that many iterations and save the model.

## Confusing apples with oranges?

![](img/5720be5c3cca252e12448e68d25607b5_179_0.png)

A picture says more than a thousand numbers, and a really useful visualization of how well the model does is the confusion matrix. This matrix plots the predicted classes versus the images' real class labels, so you can see where the model tends to make its mistakes.

In the previous chapter, you ran this command:

```
print("Confusion Matrix:\n", metrics(["confusion_matrix"]))
```

This displayed a table:

| target_label | predicted_label | count |
|---|---|---|
| cookie | juice | 1 |
| carrot | watermelon | 1 |
| pretzel | pretzel | 14 |
| cake | ice cream | 2 |
| pineapple | carrot | 1 |
| doughnut | muffin | 1 |
| muffin | doughnut | 7 |

The target_label column shows the real class, while predicted_label has the class that was predicted, and count how many of this particular mistake made.

The table shows the model predicted "muffin" 7 times when the image was really "doughnut," predicted "cake" when the image was really "ice cream," and so on.

However, presented this, the confusion matrix doesn't look much like a matrix, and we promised to show how to get a better visualization.

Start by entering and running the following code:

```python
import numpy as np
import seaborn as sns

def compute_confusion_matrix(metrics, labels):
    num_labels = len(labels)
    label_to_index = {label: i for i, label in enumerate(labels)}
    conf = np.zeros((num_labels, num_labels), dtype=np.int)
    for row in metrics["confusion_matrix"]:
        true_label = label_to_index[row["target_label"]]
        pred_label = label_to_index[row["predicted_label"]]
        conf[true_label, pred_label] = row["count"]

    return conf

def plot_confusion_matrix(conf, labels, figsize=(8, 8)):
    fig = plt.figure(figsize=figsize)
    heatmap = sns.heatmap(conf, annot=True, fmt="d", rotation=45)
    heatmap.xaxis.set_ticklabels(labels, ha="right", fontsize=12)
    heatmap.yaxis.set_ticklabels(labels, rotation=0, ha="right", fontsize=12)
    plt.xlabel("Predicted label", fontsize=12)
    plt.ylabel("True label", fontsize=12)
    plt.show()
```

You define two functions: one to compute the confusion matrix and one to draw it.

compute_confusion_matrix() looks at all the rows in the metrics["confusion_matrix"] table, and fills up a 2D-array with the counts of each pair of labels. It uses the NumPy package for this.

![](img/5720be5c3cca252e12448e68d25607b5_180_0.png)

Then, `plot_confusion_matrix()` takes this NumPy array, and plots it as a heatmap using Seaborn, a plotting package that adds useful plot types to Matplotlib. You installed Seaborn when you created the turien environment in the previous chapter.

Now, enter and running the following commands to call these functions:

```python
conf = compute_confusion_matrix(metrics, labels)
plot_confusion_matrix(conf, labels, figsize=(16, 16))
```

And enjoy the display!

![](img/5720be5c3cca252e12448e68d25607b5_181_0.png)

## The confusion matrix

A heatmap shows shows small values as "cool" colors — black and dark purple — and large values as "hot" colors — red to pink to white. The larger the value, the brighter it is in the confusion matrix, you expect to see a lot of high values on the diagonal, since these are the correct matches.

For example, the row for the "pretzel" class has 14 matches and 11 wrong one. The wrong predictions are one "apple," two "cookie," one "doughnut," and seven "hotdog." Note that apple often gets mistaken for orange, cookie, doughnut, and muffin also get mixed up.

The confusion matrix is very useful because it shows potential problem areas for the model. From this particular confusion matrix, it's clear the model has learned a great deal already, since the diagonal stands out, but it is still far perfect. Ideally, you want everything to be zero except the diagonal. It might be a little misleading from the picture since at glance it appears that there aren't many mistakes. But all the small numbers in the dark squares up to 40 total, or 36% wrong.

Keep in mind that some categories have more images than others. For example, pretzel has only 25 images in the test set, while most of the other classes have 50, so it will never have as many correct matches. Still, it only scores 14 of 25 correct (56%), so overall the model actually does poorly on pretzels.

## Computing recall for each class

Turi's evaluate() function gives you the overall dataset accuracy, but as mentioned in the section of the first chapter, accuracy might be much lower or higher for specific subsets of the dataset. With a bit of code, you can get the recall for individual classes from the confusion matrix:

For each row of the confusion matrix, the number on the diagonal is how many images in this class the model predicted correctly. You're dividing this number by the sum over that row, which is the total number of images. This gives you the percentage of each class that the model classified correctly:

| class | recall |
|---|---|
| apple | 64.0% |
| banana | 68.0% |
| cake | 54.0% |
| carrot | 66.0% |
| cookie | 56.0% |
| doughnut | 62.0% |
| grape | 84.0% |
| hot dog | 76.0% |
| ice cream | 44.0% |
| juice | 74.0% |
| muffin | 50.0% |
| orange | 74.0% |
| pineapple | 67.5% |
| popcorn | 62.5% |
| pretzel | 56.0% |
| salad | 72.0% |
| strawberry | 67.3% |
| waffle | 62.0% |
| watermelon | 64.0% |

The best classes are grape (84% correct) and hot dog (76%). Juice (74%) and orange are also good. The worst performing classes are ice cream (44%), muffin (50%), cake (54%), and pretzel (56%). These be the classes to pay attention to, in order to improve the model — the numbers you'll get for your own version of this model might be slightly different. This is due to the choice of hyperparameters, such as the number of iterations. Also because models are initialized with random numbers, therefore trained models are never exactly the same (unless you set the random seed to a fixed number).

## Training classifier with regularization

A typical hyperparameter that machine learning practitioners like to play with is the amount of regularization that is being used by the model. Regularization helps to prevent overfitting. Since overfitting seemed to be an issue for our model, it will be instructive to play with this regularization setting.

## Machine Learning Chapter 5: Digging Deeper into Turi

Enter and run this statement:

```python
model = tc.image_classifier.create(train_data, target="label",
model="squeezenet_v1.1",
test=True,
max_iterations=200,
validation_set=val_data,
l1_penalty=0.0,
convergence_threshold=1e-8)
```

You've added three additional arguments: l2_penalty, l1_penalty and convergence_threshold. Setting the convergence_threshold to a very small value means that the training won't stop until it has done 200 iterations. l2_penalty and l1_penalty are hyperparameters that add regularization to reduce overfitting.

What is regularization? Recall that the model learns parameters — also called weights or coefficients — using feature values, to maximize how many training data items it classifies correctly. Overfitting can happen when the model gives too much weight to some features, giving them very large coefficients. Setting l2_penalty greater than 0 penalizes large coefficients, encouraging the model to learn smaller coefficients. Higher values of l2_penalty reduce the size of coefficients, but can also reduce the training accuracy.

Setting l1_penalty greater than 0 also penalizes large coefficients. In addition, it discards features that have very small coefficients, by setting these to 0. Typically, you'd use either l2_penalty or l1_penalty, but not both in the same session.

In the author's training session, the model has stopped overfitting:

| Iteration | Passes | Step size | Elapsed Time | Training Accuracy | Validation Accuracy |
|---|---|---|---|---|---|
| 124 | 183 | 2.755461 | 33.123541 | 0.780281 | 0.643979 |
| 149 | 221 | 1.000000 | 39.888881 | 0.785449 | 0.646073 |
| 178 | 258 | 0.965987 | 41.115951 | 0.786415 | 0.647120 |
| 199 | 305 | 1.326954 | 53.436095 | 0.788995 | 0.649215 |

![](img/5720be5c3cca252e12448e68d25607b5_184_0.png)
