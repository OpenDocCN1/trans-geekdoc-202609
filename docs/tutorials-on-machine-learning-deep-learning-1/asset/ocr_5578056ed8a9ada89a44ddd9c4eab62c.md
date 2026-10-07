# 15.5 Train the SAE model: Nested-for-loop and input

Our code will help you optimize our code so you can use it on high dimensional datasets. Here we'll use a dataset with 200,000 ratings. If you want to use this code for the 1 million ratings dataset or a larger dataset, an optimized code that saves memory as much as possible.

+   - We won't go into some detail about the technique and besides is this topic related to PyTorch. The most important thing that matters is that you understand
  - How the architecture of the Neural Network works.
  - How to populate our StackedAutoEncoders architecture by changing the number of layers and the number of neurons in the hidden layers in the StackedAutoEncoders class.
  - You can try different combinations of the activation functions by manipulating the objects related to the activation functions.

+   - We're gonna use pretty advanced techniques in PyTorch.
  - No. Epochs: The first step is to define a number of EPOCH, it is based on experimenting. We're gonna train our StackedAutoEncoders for 200 EPOCHS.

+   - Outer-loop, train_loss: Second step is to make a nested-for-loop. outer loop over epochs and the inner-loop will loop over all observations in each EPOCH. ie all users will use each observation correlation to the ratings of a user.
  - Before we start the second loop, we need to initialize train_loss and counter s. As we do in RBM. We will make test for the loss of the test set.
  - Counter s: Counter will count the number of users rated at least one movie. The purpose is to optimize the memory, we won't compute for the users who didn't rate any movies.
  - To do this we need to keep track of the number of users who rated at least one movie. Here, we use s = 0. to make it floating-point-type.
  - Since we're gonna use the RMSE in the end, floating-point is used to make sure that int-type and floating-point do not cause any issue.
  - Since the root-mean-squared-error is a float, then all the elements to compute the root-mean-squared error should be a float. It's not compulsory, but that's just to avoid.

The next step is to start the second loop: It will loop over all the observations, ie all the users. The Inner-loop will introduce all the actions that will take place in a single EPOCH.
Inside 2nd for loops: We're gonna get our predicted rating using our StackedAutoEncoders class withe object that we created earlier.

> We're gonna compute the error on each EPOCH. To observe how the training evolving. Because we want to optimize this, so keep track if it's decreasing over the EPOCHS.

We will apply our optimizer. optim.Msprop to Stochastic Gradient Descent to update the weights and lead to the convergence.

+   - The variable we call id_User is the range(nb_users), without upper/lower bound, it loop for each user.
  - Because it needs to be the indexes of the observations of our training set and the indexes of our observations training don't go from 0 to 193. From 0 to 942, range(nb_users) will make this range from 0 to 942.

```
for id_user in range(nb_users):
```

Now we apply the input vector, which is the input vector of features that contains the ratings of all movies given by this particular user inside the loop.

```
input = Variable(train_tensor(id_user)).unsqueeze()
```

+   - train_tensor[id_user] will get the ratings for all movies that are given by id_user. id_user is the user with which we are dealing in the loop.
  - But train_tensor[id_user] is a vector and the network in PyTorch or even on Keras can not accept a single vector of one dimension which is Batch of input.

For our example, forward() function will not take a simple vectors of one dimension as input. So we need to add an extra dimension which will convert to a batch(which is it in RBM, but in different way).