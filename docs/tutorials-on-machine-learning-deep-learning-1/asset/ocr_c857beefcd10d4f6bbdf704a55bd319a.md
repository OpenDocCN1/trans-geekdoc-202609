# # Chapter 15 : Part 3
# Deep Learning
AutoEncoder : project

# ## 15.3.1 Data Preprocessing

+   - We train our auto-encoders-AE on this training set, and so it will try to identify patterns to find groups of movies that are liked by similar segments of users

+   - AE will find these patterns, it will find some specific features of the movies which will be the hidden nodes in the auto-encoders, and these specific features can be some genres, some actors that are in the movies, or some directors.

+   - For example, one hidden node can be a specific director, like Tarantino, or it can identify some movies with a great actor that is liked by the same group of people because they give the same high rating.

+   - So basically it will identify patterns, it will identify some features, based on which, in the future, the AE-recommender model will be able to predict the rating of a movie that one user has never seen, and it will be able to predict rating based on the features that the auto-encoder detected, and based on the history of this user.

+   - AE will take the features that it detected, and it will take the ratings of that one user to predict the rating of the new movie that same user has never seen, and has not rated yet.

+   - There is no common rating of the same user between the training sets and the test set, however we have the same users, for example in-test we start with one user, as in the training set. But for this one user, we will not have the same movies because the ratings are in different-sets

+   - It is a supervised technique: Test set is just to get the real results on one user's data, so what will happen that we will make our predictions using our auto-encoder's model to predict the rating, for example, AE could predict rating 4 of movie 14 by user-1, but in test set it is 5.

+   - Then, we will measure the error between the real rating, 5, and the prediction, 4, and that will allow us to measure the MSE by Mean Squared Error.

+   - We are converting our training set into 2 matrices, where the lines/rows are going to be the users, the columns are going to be the movies, and the cells are going to be the ratings.

+   - In each of these two matrices, we want to include all the users and all the movies from the original data set

+   - And in the training set, a user didn't rate a movie we will put a zero into the cell of the matrix that corresponds to this user and that movie.

+   - These matrices will have the same number of users and the same number of movies so they will have the same number of lines/rows and the same number of columns.

+   - And in these two matrices, each cell of index U, I, where U is the user and I is the movie, each cell UI will get the rating of movie I by user U. If this user U not rate the movie I, we will put a 0.

For this reason we get first number of users and total number of movies.

+   - We need these matrices for a specific structure of data that will fit to the structure of the AE and the AEs are like neural networks, where we use some input nodes that are the features and we have some observations going by one into the NN starting with input nodes.

+   - So we created list of 943 lists which have 943 users and each of these 943 lists will be a list of 1682 elements we have 1682 movies (exactly same as RBM-model).

+   - We use tensor instead of NumPy. A tensor is a multidimensional matrix but instead of being a NumPy, this is a PyTorch. And in fact, we will build a neural network with NumPy arrays, but that will be more efficient and that is why we're using tensors.

+   - So, the training_set is going to be one torch.tensor and the test_set is going to be another torch.tensor. Two

![](bbox=[0.495, 0.972, 0.505, 0.988])