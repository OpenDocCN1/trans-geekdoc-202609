Lastly, apply the **predict** method to the **target_user** using the model developed in Step 5 and assign it as a new variable. Then **print** the new variable on a new line.

```
pred_target_user = model.predict([target_user])
print("Prediction:", pred_target_user)
```

Let’s run the model by right-clicking and selecting “Run” or by navigating from the Jupyter Notebook menu to Cell > Run All. Wait one or two seconds for the computer to process the model. The results, as shown below, will then appear at the bottom of the cell.

**Prediction:** [1]

The outcome of this exercise for the y variable “Clicked on Ad” is **[1]**, which means that the target user is expected to click on the advertisement and the ad should therefore be recommended to this user. Conversely, an outcome of **[0]** signifies that the user is *not* expected to click on the advertisement based on the behavior of similar users.

A more advanced version of this exercise examining both discrete and continuous variables (using logistic regression) is available at: http://www.scatterplotpress.com/bonus-chapters/recommender-systems-for-absolute-beginners-chapter-7/