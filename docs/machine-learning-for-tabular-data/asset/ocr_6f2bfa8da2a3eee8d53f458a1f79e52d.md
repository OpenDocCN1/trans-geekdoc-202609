# Defining the deep learning model

# Listing 9.10 Lowercase column names and replacing spaces

The code shown in 9.10 replaces the column names in the input Data-Frame and the list of categorical and continuous column names. For example, the variable name Car becomes Car\_Parks.

The following listing presents the definition of the df\_to\_dataset function, which creates an input pipeline for the model that Keras preprocessing layers.

# Listing 9.11 Function to create an input pipeline

```
# function from https:
//tensorflow.org/tutorials/structured_data/preprocessing_layers
def df_to_dataset(dataframe, shuffle=True, batch_size=32):
df = dataframe.copy()
labels = df.get(\'target')
df = {key: value(tf, tf.newaxis) for key,
value, _ in dataframe.items()}
df = df.Dataset.from_slices(dict(df,
labels))
if shuffle:
df = df.shuffle(buffer_size=len(dataframe))
df = df.batch(batch_size)
return df.prefetch(1)
```

| Gets the target column from the
local copy of the dataframe | Creates a new dictionary
with the same keys\and values but a
new axis added to it |
| Creates a TensorFlow
Dataset using the
from\_tensor\_slices method |
| Applies prefetch(1)
the dataset | Shuffles the elements of the
daset to avoid overfitting if the
data has intrinsic sorting
Groups the elements of the dataset
to batches of size batch_size

The df\_to\_dataset function shown in 9.11, is taken directly from https://tensorflow.org/tutorials/structured_data/preprocessing_layers, will be