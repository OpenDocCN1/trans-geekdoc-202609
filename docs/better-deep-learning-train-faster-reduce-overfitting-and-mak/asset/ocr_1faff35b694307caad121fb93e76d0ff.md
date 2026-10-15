![](bbox=[0.2, 0.14, 0.81, 0.46])

Figure 20.4: Box and Whisker Plot of Model Test Accuracy Over 30 Repeats.

The analysis of the sample of test scores clearly demonstrates a variance in the performance of the same model trained on the same dataset. A spread of likely scores of about 8 percentage points (81% to 73%) on the test set could reasonably be considered large, e.g. a high variance result.

# 20.3.4 Model Averaging Ensemble

We can use model averaging to both reduce the variance of the model and possibly reduce the generalization error of the model. Specifically, this would result in a smaller standard deviation on the holdout test set and a better performance on the training set. We can check both of these assumptions. First, we must develop a function to prepare and return a fit model on the training dataset.

```
# fit model on dataset
def fit_model(trainX, trainy):
    # define model
    model = Sequential()
    model.add(Dense(15, input_dim=2, activation='relu'))
    model.add(Dense(3, activation='softmax'))
    model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
    # fit model
    model.fit(trainX, trainy, epochs=200, verbose=0)
```