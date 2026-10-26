```
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

![](bbox=[0.15, 0.4, 0.8, 0.74])

Figure 26.5: Line Plot of Predicting Brier Score for Balanced Dataset.

We can repeat this experiment with an imbalanced dataset with a 10:1 ratio of class 0 to class 1.

```
# plot impact of brier score with imbalanced datasets
from sklearn.metrics import brier_score_loss
from matplotlib import pyplot
```