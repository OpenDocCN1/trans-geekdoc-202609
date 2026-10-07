
# 14.4 Dataprocessing 2 : user & max Movies

Now we're going the total number of users and movies. We are then going to convert our training set and test set, into a matrix where the lines/rows are going to be users, the columns are going to be movies, and the cells are going to be the ratings.

- We are going to create a match for the training set, and another one for the test set, and in each of these two matrices, we want to include all the users and all the movies from the original data set.
- In the training-set, if a user didn't rate a movie, we'll put a 0, to the corresponding cell of the matrix.

- These matrices will have the same number of users and the same number of movies, so they will have the same number of rows and the same number of columns.
- In these matrices, each of indexed I, where U is the user and I is the movie. Each cell U I will get the rating of movie I, the user U. And if this user didn't rate the movie I, we put a 0.
- We're make a function to do this.
- Since these two matrices will contain the total number of users and the total number of movies, we need to find those numbers.

**Finding-max user and max-movies:** We could scroll the dataset and find out those numbers, and manually implement these movies. But to make more flexible, we use max() function, which will enable us to find any-test set and finds the corresponding max-user and max-movies automatically.

- Manually using maximum number can cause different-train split may different amounts of users and movies.
- So we use the code to find the maximum from both train set and test set.

```python
# Getting the number of Users and Movies
n_users = int(max(max(train_set[:], 0), max(test_set[:], 0)))
n_movies = int(max(max(train_set[:], 1), max(test_set[:], 1)))
```

| nb_movies | int | 1 | 1682 |
|---|---|---|---|
| nb_users | int | 1 | 943 |

> NOTICE:
( (train_set[:], 0) finds the maximum from the first column (user-id) of training-set max(train_set[:], 0) similarly finds the maximum from the test-set. We then pick the maximum of these 2 maximum numbers. We convert those to integers.
- For movies, int(max(max(train_set[:], 1), max(test_set[:], 1))) finds the maximum of maximum from the columns (Movie No) from train-set and test-set.
- Also notice we changed the index. 0 or 1 to select the corresponding columns for Users ID and Movie No.

Next we create our training set and test set into two matrices where the lines are the users, the columns are the movies, and the timestamps will be removed.

# 14.4.5 Dataprocessing 3 : Creating Metrics

Now we're going to convert our training set and test set into an array with users in lines and movies in columns.

- We need to make a specific structure of data RBM expects as inputs. We will have the observations in lines and the features in columns.
- We're just using the structural data for neural networks or for machine learning in general that is with the observations in lines and the features in columns.

- Since we gonna do this for both the training set and the test set, we're create a function that we will apply on both training set and test set.
- We're call this function convert, we need to give an arguments to the function, which will be our dataset.

We could use 2-dimensional NumPy array. We're gonna use Torch afterwards, we won't create a two-dimensional NumPy array, we create a list of lists.

Since we have 943 users, we will have 943 lists, these will be horizontal lists each corresponds one User each is a list of observations in lines. the first list will correspond to the first user, the second list will correspond to the second user.

Each list contains the ratings of the 1,082 movies by the user corresponding to the list.

If the user didn't rate the movie, then set and test set will have the same size basically for both the training set and test set, we are considering all the users and movies, and we just put 0 when the user didn't rate the movie.

So, this list will be a list of 943 lists because we have 943 users, and each of these 943 lists will be a list of 1,082 elements because we have 1,082 movies.

```python
# converting the data into an array with lines and movies in column
new_data = []
for id_user in range(1, nb_users + 1):
    # data[id_user, 0] = id_user as condition over movie column "data:, 1"
    id_movies = data[:, 1] == id_user # returns a list
    # data[id_user, 0] = id_user as condition over ratings column "data:, 2"
    id_ratings = data[:, 2][data[:, 0] == id_user
    # vector of zeros
    ratings = np.zeros(nb_movies)
    ratings[id_movies - 1] = id_ratings
    new_data.append(list(ratings))
train_set_conv = convert(train_set)
test_set_conv = convert(test_set)
```

Notice we get the list of movies that a user rated:
id_movies = data[:, 1][data[:, 0] == id_user # returns a list
Here, data[:, 1] selects the movie column (2nd column), then we apply the condition: "data[:, 0]==id_user", it gets the list of movies that are rated by the id_user.

Similarly we get the corresponding ratings, that are given by id_user
id_ratings = data[:, 2][data[:, 0] == id_user
Here, data[:, 0] selects the ratings column (3rd column), then we apply the condition: "data[:, 0]==id_user", it gets the list of movies that are rated by the id_user.

data[:, 0] == id_user means the user_id column (first column) select the items the id_user.

Following creates a list of lists named ratings of size nb_movies.
ratings = np.zeros(nb_movies)
In the lists we put the value of "id" at the index "n-1", since the id of movies starts from 1.

Also noticing the list operation, it runs the id_ratings given by id_user to the corresponding movie id_movies. In Python at start, and our user's IDs at end.
ratings[id_movies - 1] = id_ratings

| Index | Type | Value |
|---|---|---|
| 0 | list | (8.0, 3.0, 4.0, 3.0, 0.0, 1.0, ...) |
| 1 | list | (4.0, 0.0, 0.0, 0.0, ...) |
| 2 | list | (8.0, 0.0, 0.0, 0.0, ...) |
| 3 | list | (8.0, 0.0, 0.0, 0.0, ...) |
| 4 | list | (8.0, 0.0, 0.0, 0.0, ...) |
| 5 | list | (4.0, 0.0, 0.0, 2.0, ...) |
| 6 | list | (8.0, 0.0, 0.0, 0.0, ...) |
| 7 | list | (8.0, 0.0, 0.0, 0.0, ...) |
| 8 | list | (8.0, 0.0, 0.0, 0.0, ...) |
| 9 | list | (8.0, 0.0, 0.0, 0.0, ...) |

![](img/0aa92657a6eb1b9f2dd65bbb79055a3_490_0.png)

Notice each line has different ratings now. Since we use rated ratings 1, 6, 10, and 12, many there could be less, 0 for those.

Also used list(), to make sure that ratings are a list.

```python
new_data.append(list(ratings))
```

Note in following, range is there because no user0 in our dataset, and the loop excludes nb_users + 1, so our users will be nb_users.

```python
for id in range(1, nb_users + 1):
```

# 14.4.6 Data Preprocessing 4: Convert Matrices to torch.Tensor

We've converted our training set and our test set into arrays of users in lines and movies in columns.

- The columns are the features that are going to be the input nodes in the network.
- For each we will have its ratings of all the movies, zeros, and these are going to be the input nodes for this observation going into the network.
- Then PyTorch comes into place, we will build the architecture with PyTorch tensors.
- A tensor is a multi-dimensional array but instead of a NumPy array, this is a PyTorch array.
- In fact, we could build it with NumPy array, but that would be less efficient and we're using tensors using the torch tensors.

**NOTE**: With TensorFlow exactly the same. With TensorFlow we work with tensors.

- Those are another kind of tensor, another of multi-dimensional matrix, and so we could implement our AE/RM from scratch with TensorFlow.
- But for AE/RM, PyTorch gives better results, and also this is much simpler.

```python
# Converting the data into Torch Tensors
train_set = torch.FloatTensor(train_set_cnt)
test_set = torch.FloatTensor(test_set_cnt)
```

Now training set and test set are torch tensors. two are multi-dimensional matrices by PyTorch.
