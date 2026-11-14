```
for field in ["uid", "mid", "gender", "age", "occupation"]:
    # For each categorical feature, if the value in df_test is not
    # in df_train, then we move the entries contain that new value
    # to trainig.
    # This will ensure that we won't have out of vocabulary cases
    # to be handled during evaluation. However, in real production,
    # we need to address the so-called "out-of-vocabulary" issue.
    test_set = set(df_test[field].values())
    train_set = set(df_train[field])
    diff_id = list(test_set.difference(train_set))
    index = df_test[field].isin(diff_id)
    df_train = pd.concat([df_train, df_test.loc[index, :]]).reset_index(
        drop=True
    )

    df_test = df_test.loc["index", :]
    # Checking again
    assert set(df_test[field]).issubset(set(df_train[field])), field

df_train.to_pickle("./ml-1m/train.pkl", compression="gzip")
df_test.to_pickle("./ml-1m/test.pkl", compression="gzip")
```

To load the data in batches from the above created.pickle files, we make our own data loader using keras.utils.Sequence.

```
import numpy as np
from keras.utils import Sequence


class DFMData(Sequence):
    def __init__(self, x_set, y_set, batch_size, shuffle=True):
        self.x, self.y = x_set, y_set
        self.batch_size = batch_size
        self.shuffle = True
        self.index = np.arange(len(self.y))
        self.on_epoch_end()

    def __len__(self):
        return int(np.ceil(len(self.y) / float(self.batch_size)))

    def __getitem__(self, index):
        start_index = index * self.batch_size
        end_index = (index + 1) * self.batch_size
        if end_index > len(self.y):
            end_index = None

        batch_x = [x[start_index:end_index] for x in self.x]
        batch_y = self.y[start_index:end_index]

        return batch_x, batch_y

    def on_epoch_end(self):
        if self.shuffle:
            np.random.shuffle(self.index)
```