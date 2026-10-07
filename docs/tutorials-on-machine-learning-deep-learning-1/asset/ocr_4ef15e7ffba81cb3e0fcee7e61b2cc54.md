Also remember, we did it already in CNN, when we used the predict function to predict if the image contains a cat or a dog. we added one dimension and that additional dimension for the batch: we put our input image of a cat into a batch and that added one dimension that would make the whole thing accept by the predict method.

+   - So we'll create a batch which will contain one vector, and we will be into a new dimension corresponding to the batches.

+   - We have to use the Variable module that we imported at the beginning of torch.autograd. It's just a PyTorch technique.

+   i. We create train_tensor[id_user] inside Variable().

+   ii. To create this dimension, we use the squeeze() on Variable(), like this this.

+   iii. To specify the index of this new dimension. we use squeeze(0) because we are gonna put this new dimension in first position (as we did in Keras) and so we will have index zero.

This will create a batch of single vector.

```
# --- Training the SAE model ---
b_epoch = 200
for epoch in range(1, nb_epoch+1):
train_loss = 0
t = 0.0
for id_user in range(nb_users):
    input = Variable(train_tensor[id_user]).squeeze(0)
```

NOTE: The batch can have several vectors. Remember this called Batch Learning.

But here we're gonna do Online Learning. That means that we are going to update the weights after each observation going to the network. and we are creating a batch of one input vector. But we have to create this batch, otherwise it won't work.

# 15.3-6 Train the SAE model : target-vector

Target-vector: As we did in RBM we need a target vector, which is a copy of the input vector. Since we're going to modify the input and remain the same, so that we can compare the modified input and the original data in target.

Filter us: In this step we're gonna introduce an condition to find the users who rated at least one movie. So if an observation contains only zeros, which means the user didn't rate any movies, then we won't count this observation.

```
# --- Training the SAE model ---
b_epoch = 200
for epoch in range(1, nb_epoch+1):
train_loss = 0
t = 0.0
for id_user in range(nb_users):
    input = Variable(train_tensor[id_user]).squeeze(0)
target = Variable(target.data > 0):
    if torch.sum(target.data > 0):
        output = -vae(input)
```

Here target.data will take all the values of target.data, target.data will be the ratings of the user here at loop root, it's all of them.

target_data > 0, consider all the ratings that are greater than zero. We check if torch.sum(target.data > 0) is larger than zero.

And if that's case, torch.sum(target.data > 0) means that the observation contains at least one rating is not zero. In that way we use the users that rated at least one movie.