```
self.x = [
    x[self.index] if x.ndim < 2 else x[self.index, :]
    for x in self.x
]

self.y = self.y[self.index]

# Prepare data loader
df_train = pd.read_pickle("./ml-1m/train.pkl", compression="gzip")
df_test = pd.read_pickle("./ml-1m/test.pkl", compression="gzip")

# Make the dataset provider
batch_size = 128
train_dataset = DFMDataset(
    [
        df_train["uid"].values,
        df_train["mid"].values,
        df_train["gender"].values,
        df_train["age"].values,
        df_train["occupation"].values,
        np.vstack(df_train["movie_genre"].values),
    ],
    df_train["rating"].values,
    batch_size=batch_size,
    shuffle=True,
)

test_dataset = DFMDataset(
    [
        df_test["uid"].values,
        df_test["mid"].values,
        df_test["gender"].values,
        df_test["age"].values,
        df_test["occupation"].values,
        np.vstack(df_test["movie_genre"].values),
    ],
    df_test["rating"].values,
    batch_size=batch_size,
    shuffle=True,
)
```

Finally, let's train the model.

```
import json
from keras.callbacks import EarlyStopping

def compute_steps(num_examples, batch_size):
    return num_examples // batch_size + int(
        num_examples % batch_size > 0
    )
```