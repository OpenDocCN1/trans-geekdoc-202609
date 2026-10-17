# 14.2.3 Training Codebook Vectors

The first step in training a set of codebook vectors is to initialize the set. We can initialize it with patterns constructed from random features in the training dataset. Below is a function named random_codebook() that implements this. Random input and output features are selected from the training data.

```
# Create a random codebook vector
def random_codebook(train):
    n_records = len(train)
    n_features = len(train[0])
    codebook = [train[randrange(n_records)][i] for i in range(n_features)]
    return codebook
```

Listing 14.8: Function To Create a Random Codebook Vector.

After the codebook vectors are initialized to a random set, they must be adapted to best summarize the training data. This is done iteratively.

+   - **Epochs**: At the top level, the process is repeated for a fixed number of epochs or exposures of the training data.
+   - **Training Dataset**: Within an epoch, each training pattern is used one at a time to update the set of codebook vectors.
+   - **Pattern Features**: For a given training pattern, each feature of a best matching codebook vector is updated to move it closer or further away.

The best matching unit is found for each training pattern and only this best matching unit is updated. The difference between the training pattern and the BMU is calculated as the error. The class values (assumed to be the last value in the list) are compared. If they match, the error is added to the BMU to bring it closer to the training pattern, otherwise it is subtracted to push it further away.

The amount that the BMU is adjusted is controlled by a learning rate. This is a weighting on the amount of change made to all BMUs. For example, a learning rate of 0.3 means that BMUs are only moved by 30% of the error or difference between training patterns and BMUs.

Further, the learning rate is adjusted so that it has maximum effect in the first epoch and less effect as training continues until it has a minimal effect in the final epoch. This is called a linear decay learning rate schedule and can also be used in artificial neural networks. We can summarize this decay in learning rate by epoch number as follows:

$rate = learning\_rate \times (1.0 - \frac{epoch}{total\_epochs})$ (14.2)

We can test this equation by assuming a learning rate of 0.3 and 10 epochs. The learning rate of each epoch would be as follows: