Wait! Before you start typing, you can save time with clicking! For instance, rather than typing 'P(Mandrill | Other)', simply double-click the corresponding name in the Fields list box. This will insert that field into the formula next to your cursor. When you are ready and have constructed the formula correctly, click OK.

If all goes according to plan, your new field will appear in the Field list of your PivotTable. Drag this new field into the Values field to use it (see Figure 3.21).

![](bbox=[0.136, 0.25, 0.45, 0.72])

Figure 3.21: Place the field Model Prediction into the Values field to use the next calculated field you just created.

Now, let's take a look at our results! If the model predicts a 1, then it's predicting (based on the training data provided) that a given tweet refers to the Mandrill app. A 0 means our model is predicting that a given tweet refers to something else. In Figure 3.22, we see that tweets 7 and 19 were misclassified. But still, the model gets 18 out of 20 correct! Not bad, eh?