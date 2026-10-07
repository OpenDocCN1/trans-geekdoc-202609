
And that's not too bad: because we predict when a user is going to like a movie, on average we will make an error of 1 out of 9.

We were hoping to get a loss that is less than one star that the average difference between the real rating and the predicted rating is less than 1. Therefore, we will make better predictions of whether a user is going to like a movie.

We are expecting to get a loss of less than 1 (loss < 1 star).

Second thing we are now calculating the loss on the training sets, we also need to calculate the test_loss on the test set. When we can see there is a high-overfitting or not.

Result: at the last epoch, we expect a final loss of 0.91.

So that it's not too bad. Besides, we are training on 100K ratings and you will definitely get a better loss error if you train on these ratings. Our dataset is optimized so that the training doesn't take too much time.

Now let's hope we get the same error on the test set.

Increasing epochs may lead to Overfitting: Of course, by having many epochs you can get a lower loss on the training set, but then you might end up with a larger difference of the loss between the training set and the test set which leads to high-overfitting, and to avoid that, 20 epochs is enough for our current dataset.

> ImplementedError: Module [StackedAutoEncoders] is missing the required forward function.
This error is shown if we missing forward() function in our SAE-architecture, the StackedAutoEncoders class.

# All code at once here (train only)

```python
# AE : Recommender, SAE Stacked-Auto-Encoder

# Importing the Libraries
from turtle import clone
import pandas as pd
import numpy as np
import torch
import torch.nn as nn
import torch.nn.parallel
import torch.optim as optim
import torch.utils.data
from torch.autograd import Variable

# importing the dataset

# preparing the training set and test set
training_set = pd.read_csv("/movie_lens_100k/u.base", delimiter="\t")
test_set = np.array(training_set, dtype="int")

ts_test = pd.read_csv("/movie_lens_100k/u.base", delimiter="\t")
test_set = np.array(ts_test, dtype="int")

# Getting the number of Users and Movies
nb_users = int(max(training_set[:, 0]), max(test_set[:, 0]))
nb_movies = int(max(training_set[:, 1]), max(test_set[:, 1]))

# converting the data into an array with users in lines and movies in column.
def convertdata(data):
    new_data = []
    for user_id in range(1, nb_users + 1):
        # use "user_id, == user_id" as condition over movie column "data[:,,1]"
        movie_ids = data[:, 1][data[:, 0] == user_id] # returns a list

# use data[:, 0] = id_user as condition over ratings column data[:, 2]
id_ratings = data[:, 2][data[:, 0]==id_user]
# # of vectors
ratings = np.zeros(nb_movies)
ratings[id_movies - 1] = id_ratings

new_data.append(list(ratings))

return
new_data

train_set_cvnt = convert(train_set)
test_set_cvnt = convert(test_set)

# Converting the data to Torch Tensor. Following are the Tensors of ratings
train_set_tensor = torch.FloatTensor(train_set_cvnt)
test_set_tensor = torch.FloatTensor(test_set_cvnt)

# --- Creating the architecture of the Neural Network for SAE
class StackedAutoEncoders(nn.Module):
    def __init__(self):
        super(StackedAutoEncoders, self).__init__()
        self.fc1 = nn.Linear(nb_movies, 20)
        self.fc2 = nn.Linear(20, 10)
        self.fc3 = nn.Linear(10, 20)
        self.fc4 = nn.Linear(20, nb_movies)
        self.activation = nn.Sigmoid()

    def forward(self, x):
        x = self.activation(self.fc1(x))
        x = self.activation(self.fc2(x))
        x = self.activation(self.fc3(x))
        x = self.fc4(x)
        return x

sae = StackedAutoEncoders()
criterion = nn.MSELoss()
optimizer = optim.RMSprop(sae.parameters(), lr=0.01, weight_decay=0.5)

# --- Training the SAE ---
nb_epoch = 20
for epoch in range(1, nb_epoch + 1):
    train_loss = 0
    s = 0
    for id_user in Variable(train_set_tensor.unsqueeze(0)):
        target = id_user.clone()
        non_zero_ratings = torch.sum(target > 0)
        if non_zero_ratings > 0:
            output = sae(id_user)
            output[target == 0] = 0
            loss = criterion(output, target)
            mean_corrector = nb_movies/float(non_zero_ratings + 1e-10)

            loss.backward()
            train_loss += torch.sqrt(loss.data) * mean_corrector
            s += 1
        optimizer.step()
    train_loss_normalized = train_loss/s
    print(f'Epoch: {epoch}, loss = {train_loss_normalized}')
```

# Test model: use test-set to calculate "test_loss"
Here we compute the test-set loss and hope we can make it better than the ratings.

- Similar to the RBM model, we don't need loop because we are not training the model.
- We don't need epochs to measure the test-set performance to measure the test-loss. Of course only one epoch because we're gonna measure global loss, we only need inner loop because the code loops over all users of the data.
- For the target-vector, we don't choose test-set for the input-vector, we use the train-set. Because `test_loss` computes the loss on test-set. We initialized it to 0.

```python
test_loss = 0
cnt = 0.0
for uid in range(nb_users):
    v = Variable(train_set[uid]).squeeze(0) # input vector from training-set
    vt = Variable(test_set[uid]).squeeze(0) # target vector from test-set
```

The input to our model is all the ratings of the movies we watched. We are training the test-set in input-vector:

- We put this input vector into the AE-network, the AE will look at the ratings of the movies and predict positive ratings and based on these, it will predict the ratings of the movies that the user hasn't watched (ratings that are not present in test-set). That's the prediction.
- Here is the point of using test-set as target-vector: it contains the real-ratings of the movies that were not present in training-set (we used AE to generate them), so we can compare predicted and real ratings and measure the test_loss.
- `test_loss` will indicate how our model performs on new data.

For example, if we use our input vector we give ratings to all the movies we watched, then when we feed this input vector into the network, the neurons of the specific features related to action movies will be activated with a large weight: high ratings for the other movies that the user hasn't watched.

And then, we will compare the predicted ratings to the ratings of the test-set because the test set contains these ratings that were not part of the training set. That is, these movies that the user hasn't watched yet in the training set.

```python
test_loss = 0
cnt = 0.0
for uid in range(nb_users):
    v = Variable(train_set[uid]).squeeze(0)
    vt = Variable(test_set[uid]).squeeze(0)
    non_zero_ratings_t = torch.sum(vt.data)
    if non_zero_ratings_t > 0:
        t_output = sae(v)
        vt.require_grad = False
        loss_t = criterion(t_output[vt == 0], vt)
        mean_corrector_t = nb_movies/float(non_zero_ratings_t + 1e-10)
        cnt += np.sqrt(loss_t.data) * mean_corrector_t
    cnt += 1.0
```

eval_loss = test_loss/cnt
print(f"Evaluation Loss = {eval_loss}")

- The predictions happen here: test_output = sae(v). The AE model is just making one step forward after training.
- Our forward function returns the vector of predicted ratings and therefore by calling our object on the input here, we will get our predicted ratings for the movies that the user hasn't watched yet, and this will go into test_output.
- We use `vt.require_grad = False` because we don't need the gradient with respect to the target.

To calculate loss, between real-ratings in test-set and predicted-ratings from train-set.

We also need the mean_corrector for test-set.

```python
mean_corrector = nb_movies/float(non_zero_ratings + 1e-10)
```

Finally we compute the test_loss and increment our counter cnt.

```python
test_loss += torch.sqrt(loss_t.data) * mean_corrector
```

After the loop, we calculate the normalized-loss and print the result:

```python
eval_lossSS = test_loss/cnt
print(f"Evaluation or Test = {eval_lossSS}")
```

built a robust recommended system. The test-loss is 0.05 stars, which is less than one star. So for example if you're using the recommended system for the movie you're watch tonight, and let's say after we give the movie four stars, that this recommended system would predict you between three and five stars to this movie.
