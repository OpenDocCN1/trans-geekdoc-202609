![](bbox=[0.15, 0.07, 0.85, 0.5])

Figure 12.2 The k-NN algorithm for classification: identifying k-nearest neighbors and taking the majority vote. Lines connect the unlabeled data with their one, three, and five-nearest neighbors. The majority vote in each scenario is indicated by the shape drawn under each black cross.

The voting process when using k-NN for regression is very similar, except that we take the mean of these k votes as the predicted value for the new data.

This process is illustrated for our commuting example in figure 12.3. The crosses on the x axis represent new data: times we left the house and want to predict journey length for. If we train a 1-nearest neighbor model, the model finds the single case from the training set that is closest to the departure time of each of the new data, and uses that value as the predicted journey length. If we train a 3-nearest neighbor model, the model finds the three training cases with departure times most similar to each of the new data, takes the mean journey length of those nearest cases, and outputs this as the predicted value for the new data. The same applies to any number of k we use to train the model.