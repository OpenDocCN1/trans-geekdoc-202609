
Note: Those last two problems occur with more than just sequences. Many data types are affected by their sources. For example, sensors from different phones will report different values in the same situations, camera lenses have slightly different distortions, and so on. All physical devices are produced with some variance, so data collected from different devices can be slightly different when measuring the same thing. In these cases, the same rules apply: try to train with as many sources as possible, and try to test on data from multiple sources. Unless of course the model is meant to work with a specific source — as correcting tense distortion for images from a specific camera. By all means test on data collected from the source to ensure your model works correctly in its intended production environment.

## But sometimes...

And now, in a shocking plot twist, you're about to be told to sometimes do what you were just told not to do — train and validate on the same people! What?!

Real talk: There are going to be — maybe most of the time — when you won't have as much data as you want. In those cases, you can stretch your dataset out by starting with just two datasets — training and then grabbing a chunk of your training set to use for validation.

Depending on how many different sources are present in your training set, you might not be able to follow the recommended procedure of separating based on source. For example, the one provided with the chapter contains data from just two people. You'd lose too much training data if you separated these users, so you'd need to accept training and validating on both of them.

It's not ideal — your validation accuracy will be artificially closer to your training accuracy because the two datasets are more similar, making it harder to tell if your model overfits. But if there's enough variety in your training set to start, then this works fairly well.

To help split your training data, Turi Create provides a nice utility function that splits an SFrame into two smaller SFrames, while maintaining proper sequence groupings. The following code demonstrates how to use it:

```python
train, valid =
tc.activity_classifier.util.random_split_by_session(
train_sf, session_id='sessionId', fraction=0.9)
```

# Machine Learning
## Chapter 12: Training a Model for Sequence Classification

This uses Turi Create's activity_classifier.util.random_split_by_session function with a training set, telling it which column identifies the sessions, and what percentage of the data should be used in the split. It returns two SFrames, the first will contain the given percentage of the original SFrame's sessions, and the second will contain the remaining sessions.

After running this code, train would contain about 90% of the sessions and valid would contain the other 10%. You would use these two SFrames for your training and validation sets.

The most important thing about this function is that it splits data based on session IDs, which keeps sequences organized together. Any samples with the same session ID are kept together and in order, but any particular session ID could end up in the training or the validation set.

The results of this are not necessarily going to give you a perfectly balanced split. For example, here are the results of calling utils.count_activities on train and valid from one run:

| activity | userId | Count | activity | userId | Count |
|---|---|---|---|---|---|
| chop_it | u_01 | 33 | chop_it | u_01 | 3 |
| chop_it | u_02 | 34 | chop_it | u_02 | 2 |
| drive_it | u_01 | 30 | drive_it | u_01 | 5 |
| drive_it | u_02 | 31 | drive_it | u_02 | 6 |
| rest_it | u_01 | 95 | rest_it | u_01 | 13 |
| rest_it | u_02 | 97 | rest_it | u_02 | 11 |
| shake_it | u_01 | 31 | shake_it | u_01 | 5 |
| shake_it | u_02 | 33 | shake_it | u_02 | 3 |
| # rows x 3 columns | | | # rows x 3 columns | | |

Random train/validation split counts

Probably fine, but if you see a particularly bad split — when you know the original data was well balanced — then you try splitting it again.

If you want to experiment try combining the training and validation data and then use this function to randomly split it. You'll end up with more variety in your training data in exchange for a less trustworthy validation set. For now, you'll use the separate datasets you've already built.

# Training the model

Now it's time to build and train your model. Almost.

Whenever you are with a new model or dataset, it's good to first take a small portion of your training data and see if you can get the model to overfit. Overfitting

![](img/5720be5c3cca252e12448e68d25607b5_405_0.png)

raywenderlich.com

# Machine Learning Chapter 12: Training a Model for Sequence Classification

is usually a bad thing — it means your model is memorizing the training data instead of learning a more general solution — but it also shows the model is actually capable of learning something from your data. If your model is going to work on a real dataset, then it should easily be able to overfit on a tiny version of it. And if it can't, you've got several problems you need to address:

- A bug in the model. This is especially common when implementing neural nets from scratch using frameworks as Keras.
- A model too simple to solve the problem. You might need more layers, or more nodes per layer.
- A model architecture incapable of solving the problem. Different architectures work better for different problems, so pick something appropriate.
- Poorly tuned hyperparameters. Sometimes all it takes is a change to the learning rate, other times you might need different activation functions, optimization algorithms or loss functions.

Maybe the problem is the problem itself. Machine learning isn't the right solution to every problem, so don't try to force it.
The point of this is to prove that your dataset is applicable to the problem, your model is built correctly and it's tuned enough to learn. You'll usually have to do more tuning later with your full dataset, but those training sessions take longer. This step is critical to keep yourself from wasting time trying to tune a model that isn't ever going to work.

To save we don't show the results of the overfitting step, but you can find them in the Model_Complete.ipynb. Now it's time to build and train your model. Turi Create's activity_classifier.create makes this easy — Add the following code to a cell:

```python
model = tc.activity_classifier.create(
  dataset=train_sf, session_id='sessionId', target='activity',
  features=["rotX", "rotY", "rotZ", "accelX", "accelY", "accelZ"],
  prediction_window=20, validation_set=val_sf,
  max_iterations=20)
```

This one line of coding is doing a lot, but it warrants a bit of explanation. It goes:

- dataset: Your training dataset, stored as SFrame.

![](img/5720be5c3cca252e12448e68d25607b5_406_0.png)

- session_id: The name of the column in dataset that stores the session ID associated with each row, create keeps data with the same session ID grouped together, and trains over in chunks of the size of prediction_window.
- target: The name of the column that contains the labels you want to predict. In this case, it's activity.
- features: This is an optional list of columns to use for training. If you don't supply it, then create all the columns as features except the ones specified for session_id and target. More on this in a bit.
- prediction_window: How many samples (i.e. rows of data) the model looks at to make a prediction. More on this later.
- validation_set: Your validation dataset, stored as SFrame — if you don't supply it, and dataset contains more than 100 sessions, create will automatically make a validation set by randomly selecting sessions from dataset. But if it contains fewer sessions than that, create trains the model without a validation set. It's best not to rely on this logic, and supply your own data instead.
- max_iterations: The maximum number of epochs will train over. That is, the number of times it will go through the training set. Note: the parameter name and documentation claim this is a “maximum”, as create could stop training sooner. However, to is no evidence that training ever stops before this value is reached, so think of it as the actual number instead of a maximum.

Notice how the features parameter is a list including six of the 12 motion features available in your dataset.

These were chosen a bit arbitrarily, mostly to show that you don't need to use all columns in your dataset. In the previous section you saw how each activity appeared with a distinct pattern. Take a look at the following plots, which show just rotation values for samples of each activity:

![](img/5720be5c3cca252e12448e68d25607b5_407_0.png)

Rotations for 100 samples of 'shake_it', 'chop_it', and 'drive_it' activities from training dataset
