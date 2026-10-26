```
# define an imbalanced dataset
testy = [0 for x in range(100)] + [1 for x in range(10)]
# brier score for predicting different fixed probability values
predictions = [0.0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
losses = [brier_score_loss(testy, [y for x in range(len(testy))]) for y in predictions]
# plot predictions vs loss
pyplot.plot(predictions, losses)
pyplot.show()
```

Listing 26.6: Example of plotting the change in brier score for a imbalanced dataset.

Running the example, we see a very different picture for the imbalanced dataset. Like the average log loss, the average Brier score will present optimistic scores on an imbalanced dataset, rewarding small prediction values that reduce error on the majority class. In these cases, the Brier score should be compared relative to the naive prediction (e.g. the base rate of the minority class or 0.1 in the above example) or normalized by the naive score. This latter example is common and is called the Brier Skill Score (BSS).

$$BSS = 1 - \left(\frac{BS}{BS_{ref}}\right)\qquad (26.1)$$

Where $BS$ is the Brier skill of model, and $BS_{ref}$ is the Brier skill of the naive prediction. The Brier Skill Score reports the relative skill of the probability prediction over the naive forecast. A good update to the scikit-learn API would be to add a parameter to the `brier_score_loss()` to support the calculation of the Brier Skill Score.