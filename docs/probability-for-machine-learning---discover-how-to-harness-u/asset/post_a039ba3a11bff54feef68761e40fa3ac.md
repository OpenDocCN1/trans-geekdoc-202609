
![](img/6ef657cfead7281442f755181c4f6e50_262_0.png)

Figure 26.1: Line Plot of Evaluating Predictions with Log Loss.

Model skill is reported as the average log loss across the predictions in a test dataset. As an average, we can expect that the score will be suitable with a balanced dataset and misleading when there is a large imbalance between the two classes in the test set. This is because predicting 0 or small probabilities will result in a small loss. We can demonstrate this by comparing the distribution of loss values when predicting different constant probabilities for a balanced and an imbalanced dataset. First, the example below predicts values from 0.0 to 1.0 in 0.1 increments for a balanced dataset of 50 examples of class 0 and 1.

```python
# plot impact of log loss with balanced datasets
from sklearn.metrics import log_loss
from matplotlib import pyplot
# define an imbalanced dataset
testy = [0 for x in range(50)] + [1 for x in range(50)]
# loss for predicting different fixed probability values
predictions = [0.0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
losses = [log_loss(testy, [y for x in range(len(testy))]) for y in predictions]
# plot predictions vs loss
pyplot.plot(predictions, losses)
pyplot.show()
```

Listing 26.2: Example of plotting the change in log loss for a balanced dataset.

Running the example, we can see that a model is better-off predicting probability values that are not sharp (close to the edge) and are back towards the middle of the distribution. The penalty of being wrong with a sharp probability is very large.

![](img/6ef657cfead7281442f755181c4f6e50_263_0.png)

Figure 26.2: Line Plot of Predicting Log Loss for Balanced Dataset.

We can repeat this experiment with an imbalanced dataset with a 10:1 ratio of class 0 to class 1.

```python
# plot impact of log loss with imbalanced datasets
from sklearn.metrics import log_loss
from matplotlib import pyplot
# define an imbalanced dataset
testy = [0 for x in range(100)] + [1 for x in range(10)]
# loss for predicting different fixed probability values
predictions = [0.0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
losses = [log_loss(testy, [y for x in range(len(testy))]) for y in predictions]
# plot predictions vs loss
pyplot.plot(predictions, losses)
pyplot.show()
```

Listing 26.3: Example of plotting the change in log loss for an imbalanced dataset.

Here, we can see that a model that is skewed towards predicting very small probabilities will perform well, optimistically so. The naive model that predicts a constant probability of 0.1 will be the baseline model to beat. The result suggests that model skill evaluated with log loss should be interpreted carefully in the case of an imbalanced dataset, perhaps adjusted relative to the base rate for class 1 in the dataset.

![](img/6ef657cfead7281442f755181c4f6e50_264_0.png)

Figure 26.3: Line Plot of Predicting Log Loss for Imbalanced Dataset.

## 26.3 Brier Score

The Brier score, named for Glenn Brier, calculates the mean squared error between predicted probabilities and the expected values. The score summarizes the magnitude of the error in the probability predictions. The error score is always between 0.0 and 1.0, where a model with perfect skill has a score of 0.0. Predictions that are further away from the expected probability are penalized, but less severely as in the case of log loss. The skill of a model can be summarized as the average Brier score across all probabilities predicted for a test dataset.

The Brier score can be calculated in Python using the `brier_score_loss()` function in scikit-learn. It takes the true class values (0, 1) and the predicted probabilities for all examples in a test dataset as arguments and returns the average Brier score. We can evaluate the impact of prediction errors by comparing the Brier score for single probability predictions in increasing error from 0.0 to 1.0. The complete example is listed below.

```python
# plot impact of brier for single forecasts
from sklearn.metrics import brier_score_loss
from matplotlib import pyplot
# define an imbalanced dataset
testy = [0 for x in range(50)] + [1 for x in range(50)]
# brier score for predicting different fixed probability values
predictions = [0.0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
losses = [brier_score_loss(testy, [y for x in range(len(testy))]) for y in predictions]
# plot predictions vs loss
pyplot.plot(predictions, losses)
pyplot.show()
```

Listing 26.5: Example of plotting the change in brier score for a balanced dataset.

Running the example, we can see that a model is better-off predicting middle of the road probabilities values like 0.5. Unlike log loss that is quite flat for close probabilities, the parabolic shape shows the clear quadratic increase in the score penalty as the error is increased.

![](img/6ef657cfead7281442f755181c4f6e50_266_0.png)

Figure 26.5: Line Plot of Predicting Brier Score for Balanced Dataset.

We can repeat this experiment with an imbalanced dataset with a 10:1 ratio of class 0 to class 1.

```python
# plot impact of brier score with imbalanced datasets
from sklearn.metrics import brier_score_loss
from matplotlib import pyplot
# define an imbalanced dataset
testy = [0 for x in range(100)] + [1 for x in range(10)]
# brier score for predicting different fixed probability values
predictions = [0.0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
losses = [brier_score_loss(testy, [y for x in range(len(testy))]) for y in predictions]
# plot predictions vs loss
pyplot.plot(predictions, losses)
pyplot.show()
```

Listing 26.6: Example of plotting the change in brier score for an imbalanced dataset.

Running the example, we see a very different picture for the imbalanced dataset. Like the average log loss, the average Brier score will present optimistic scores on an imbalanced dataset, rewarding small prediction values that reduce error on the majority class. In these cases, the Brier score should be compared relative to the naive prediction (e.g. the base rate of the minority class or 0.1 in the above example) or normalized by the naive score. This latter example is common and is called the Brier Skill Score (BSS).

$$BSS = 1 - \left(\frac{BS}{BS_{ref}}\right)\qquad (26.1)$$

Where $BS$ is the Brier skill of model, and $BS_{ref}$ is the Brier skill of the naive prediction. The Brier Skill Score reports the relative skill of the probability prediction over the naive forecast. A good update to the scikit-learn API would be to add a parameter to the `brier_score_loss()` to support the calculation of the Brier Skill Score.

```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import roc_curve
from matplotlib import pyplot
# generate 2 class dataset
X, y = make_classification(n_samples=1000, n_classes=2, random_state=1)
# split into train/test sets
trainX, testX, trainy, testy = train_test_split(X, y, test_size=0.5, random_state=2)
# fit a model
model = LogisticRegression(solver='lbfgs')
model.fit(trainX, trainy)
# predict probabilities
probs = model.predict_proba(testX)
# keep probabilities for the positive outcome only
probs = probs[:, 1]
# calculate roc curve
fpr, tpr, thresholds = roc_curve(testy, probs)
# plot no skill
pyplot.plot([0, 1], [0, 1], linestyle='--')
# plot the roc curve for the model
pyplot.plot(fpr, tpr)
# show the plot
pyplot.show()
```

Listing 26.7: Example of plotting a ROC curve for predictions.

Running the example creates an example of a ROC curve that can be compared to the no skill line on the main diagonal. ROC curves are covered in more detail in Chapter 27.

![](img/6ef657cfead7281442f755181c4f6e50_270_0.png)

Figure 26.7: Example ROC Curve Plot for Binary Classification Predictions.

The integrated area under the ROC curve, called AUC or ROC AUC, provides a measure of the skill of the model across all evaluated thresholds. An AUC score of 0.5 suggests no skill, e.g. a curve along the diagonal, whereas an AUC of 1.0 suggests perfect skill, all points along the left y-axis and top x-axis toward the top left corner. An AUC of 0.0 suggests perfectly incorrect predictions. Predictions by models that have a larger area have better skill across the thresholds, although the specific shape of the curves between models will vary, potentially offering opportunity to optimize models by a pre-chosen threshold. Typically, the threshold is chosen by the operator after the model has been prepared.

The AUC can be calculated in Python using the `roc_auc_score()` function in scikit-learn. This function takes a list of true output values and predicted probabilities as arguments and returns the ROC AUC. An AUC score is a measure of the likelihood that the model that produced the predictions will rank a randomly chosen positive example above a randomly chosen negative example. Specifically, that the probability will be higher for a real event (*class = 1*) than a real non-event (*class = 0*). This is an instructive definition that offers two important intuitions:

- **Naive Prediction.** A naive prediction under ROC AUC is any constant probability. If the same probability is predicted for every example, there is no discrimination between positive and negative cases, therefore the model has no skill (AUC=0.5).
