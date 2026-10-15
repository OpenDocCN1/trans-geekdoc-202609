contributing to the final model, then the model_weight_ensemble() function is called to create the final model that is then evaluated on the test dataset.

```
# evaluate a specific number of members in an ensemble
def evaluate_n_members(members, n_members, testX, testy):
    # reverse loaded models so we build the ensemble with the last models first
    members = list(reversed(members))
    # select a subset of members
    subset = members[:n_members]
    # prepare an array of equal weights
    weights = [1.0/n_members for i in range(1, n_members+1)]
    # create a new model with the weighted average of all model weights
    model = model_weight_ensemble(subset, weights)
    # make predictions and evaluate accuracy
    _, test_acc = model.evaluate(testX, testy, verbose=0)
    return test_acc
```

Listing 26.19: Example of evaluating a model created from a given number of members.

Importantly, the list of loaded models is reversed first to ensure that the last n models in the training run are used, which we would assume might have better performance on average.

```
# reverse loaded models so we build the ensemble with the last models first
members = list(reversed(members))
```

Listing 26.20: Example of reversing the list of loaded ensemble members.

We can then evaluate models created from different numbers of the last n models saved from the training run from the last 1-model to the last 10 models. In addition to evaluating the combined final model, we can also evaluate each saved standalone model on the test dataset to compare performance.

```
# evaluate different numbers of ensembles on hold out set
single_scores, ensemble_scores = list(), list()
for i in range(1, len(members)+1):
    # evaluate model with i members
    ensemble_score = evaluate_n_members(members, i, testX, testy)
    # evaluate the i'th model standalone
    _, single_score = members[i-1].evaluate(testX, testy, verbose=0)
    # summarize this step
    print('> %d: single=%.3f, ensemble=%.3f' % (i, single_score, ensemble_score))
    ensemble_scores.append(ensemble_score)
    single_scores.append(single_score)
```

Listing 26.21: Example of evaluating a suite of different average model weight models.

The collected scores can be plotted, with blue dots for the accuracy of the single saved models and the orange line for the test accuracy for the model that combines the weights the last n models.

```
# plot score vs number of ensemble members
x_axis = [i for i in range(1, len(members)+1)]
pyplot.plot(x_axis, single_scores, marker='o', linestyle='None')
pyplot.plot(x_axis, ensemble_scores, marker='o')
pyplot.show()
```

Listing 26.22: Example of plotting model performance vs the number of contributing members.