# 8.7 Defining and fitting the fastai model

> Defines the model as a tabular learner object using the tabularDataLoaders object dls and using accuracy as the performance measurement for training

```
learn = tabular(dls, metrics=accuracy)
learn.fit_one_cycle(3)
```

Note that the statements in listing 8.7 define and fit the model are much simpler than the model definition and fit statements that we saw for the Keras model in chapter 3. In this sense, the fastai solution resolves the code for the XGBoost solution that we saw in chapter 3.

Figure 8.8 shows the output of the fit statement. For each epoch, the training loss, validation loss, and accuracy are listed. If we compare the training results shown in figure 8.4 (when the target column was not explicitly converted to string values) with the training results shown in figure 8.8 (when the target column was converted to string values), it's clear that we get better results when fastai treats the problem as a classification problem rather than a regression.

| epoch train_loss valid_loss accuracy time |
|---|---|---|---|--|
| 0 | 0.434672 | 0.407458 | 0.817900 | 00:17 |
| 1 | 0.424458 | 0.406396 | 0.814900 | 00:11 |
| 2 | 0.385092 | 0.405317 | 0.817100 | 00:10 |

![](bbox=[0.615, 0.605, 0.782, 0.642])

Before continuing with the rest of the fastai solution, let's take a moment to discuss the relationship between training loss, validation loss, and test loss. Figure 8.8 shows the training and validation loss at each epoch. Training loss indicates that the model could be underfit or regularization techniques that only apply to training (such as dropout) are having an outsize effect. Figure 8.8 shows subsequent epochs, training loss drops faster than the validation loss until it is lower than the validation loss by the final epoch.

The following listing confirms that fastai treats the problem as a classification problem because the loss function is CrossEntropyLoss(), a loss function that is appropriate for a classification problem.