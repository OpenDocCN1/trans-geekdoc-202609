```
Epoch 7/100
=====================================
is 904us/step - loss: 0.3412 - accuracy: 0.8576
Epoch 8/100
=====================================
is 791us/step - loss: 0.3409 - accuracy: 0.8589
Epoch 9/100
=====================================
is 845us/step - loss: 0.3405 - accuracy: 0.8601
Epoch 10/100
=====================================
is 836us/step - loss: 0.3406 - accuracy: 0.8614
\D\Development_2.0-ML_phase_3_ML_Intro\ml_p3_cho_dp_1_ANN
```

# 4.8.5 Prediction and evaluation of trained ANN model

We just trained ANN on the train-set and now time to make the predictions and the test-set. We can execute follow as our classification model.

```
y_pred = ann_classifier-predict(x_test)
```

After we have got the predicted probabilities. These are the probabilities of leaving the bank of the 2000 customers of the test-set.

Now we can get the accuracy of the model using Confusion-matrix. We get accuracy 86% on training-set, now we going to use test-set.

If we get a good accuracy on all the customers of the test set, then the Bank can use this model by ranking the probabilities of their customers to the lowest of customers most likely leave the Bank. So for example we have to look at the 10 percent highest probabilities of their customers leave and make it a SEGMENT and then analyzed in more depth using Data Mining Techniques to understand why the customers of this segment are most likely to leave the bank. Then the Bank can also take this method to measure these predictions of their customers from leaving.

| | | |
|---|---|---|n| 0 | 0.204 | False |
| 1 | 0.308 | False |
| 2 | 0.100 | False |
| 3 | 0.033 | False |
| 4 | 0.052 | True |
| 5 | 0.918 | False |
| 6 | 0.020 | False |
| 7 | 0.084 | False |
| 8 | 0.122 | True |
| 9 | 0.937 | False |
| 10 | False | |
| 11 | False |

However, predict method returns the probabilities in range [0, 1]. But in confusion matrix we just need 0 or 1 'false' or 'true'. So need to convert these predicted probabilities into 'false' or 'true'.

We have set a threshold value to decide when the predicted result is 1(true) and when the predicted result is 0(false). And the threshold value set is 0.5 or 50%.

The code is simple, just need to apply a condition over the y_pred value.

```
y_pred = (y_pred > 0.5)
```

y_pred > 0.5 is used because 1 means a customer will leave the Bank. So all values of y_pred greater than 0.5 will become one

Now we can proceed to the confusion-matrix.

In medicine we can take a higher threshold if we have to predict is sensitive information like for example if we have to predict if tumor is malignant.

But here we just predicting if a customer is leaving or staying in the Bank. So 50 percent threshold is fine.

| | | |
|---|---|---|n| 1 | 1550 | 45 |
| 2 | 230 | 175 |

| | | |
|---|---|---|n| 1 | 1523 | 72 |
| 2 | 215 | 190 |

Instructor-version:

Practical-version: