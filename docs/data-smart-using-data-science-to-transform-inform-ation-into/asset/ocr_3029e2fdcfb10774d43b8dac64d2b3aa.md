```
Birth.Control  "0"
Feminine.Hygiene "0"
Folic.Acid "0"
Prenatal.Vitamins "0"
Prenatal.Yoga "0"
Body.Pillow "0"
Ginger.Ale "0"
Sea.Bands "1"
Stopped.buying.ciggies "0"
Cigarettes "0"
Smoking.Cessation "0"
Stopped.buying.wine "1"
Wine "1"
Maternity.Clothes "0"
PREGNANT "1"
> t(PregnancyData.Test.lm.Preds[1])
1
[1,] 0.6735358
> PregnancyData.Test.rf.Preds[1,2]
[1] 0.504
```

Note that in printing the input row, I leave the column index blank in the square brackets [1,] so that all columns' data is printed. This particular customer has an unknown gender, lives in an apartment, and has bought sea bands and wine, but then stopped buying wine. The logistic regression gives them a score of 0.67 while the random forest is right around 0.5. The truth is that she is pregnant—chalk one up for the logistic regression!

Now that you have the two vectors of class probabilities, one for each mode, you can compare the models in terms of true positive rate (tpr in the following code) and false positive rate (fpr in the following code) just as you did earlier in the book. Luckily for you, though, in R the ROCR package can compute and plot the ROC curves so you don't have to. Since you've already loaded the ROCR package, the first thing you need to do is create two ROCR prediction objects (using the ROCR prediction() function), which simply count up the positive and negative class predictions at various cutoff levels in the class probabilities.

```
pred.lm <-
prediction(PregnancyData.Test.lm.Preds, PregnancyData.Test$PREGNANT)
```

```
pred.rf <-
prediction(PregnancyData.Test.rf.Preds[,2],
PregnancyData.Test$PREGNANT)
```

Note in the second call that you hit the second column of class probabilities from the random forest object just as discussed earlier. You can then turn these prediction objects into ROCR performance objects by running them through the performance() function. A performance object takes the classifications given by the model on the test set for