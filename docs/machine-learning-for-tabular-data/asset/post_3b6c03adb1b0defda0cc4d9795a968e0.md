
## Defining the deep learning model

## Listing 9.10 Lowercase column names and replacing spaces

The code shown in 9.10 replaces the column names in the input DataFrame and the list of categorical and continuous column names. For example, the variable name Car becomes Car_Parks.

The following listing presents the definition of the df_to_dataset function, which creates an input pipeline for the model that Keras preprocessing layers.

## Listing 9.11 Function to create an input pipeline

```python
# function from https:
//tensorflow.org/tutorials/structured_data/preprocessing_layers
def df_to_dataset(dataframe, shuffle=True, batch_size=32):
    df = dataframe.copy()
    labels = df.get('target')
    df = {key: value(tf, tf.newaxis) for key,
          value, _ in dataframe.items()}
    df = tf.Dataset.from_slices(dict(df,
    labels))
    if shuffle:
        df = df.shuffle(buffer_size=len(dataframe))
    df = df.batch(batch_size)
    return df.prefetch(1)
```

| Gets the target column from the local copy of the dataframe | Creates a new dictionary with the same keys and values but a new axis added to it |
| :--- | :--- |
| Creates a TensorFlow Dataset using the from_tensor_slices method | Applies prefetch(1) the dataset |
| Shuffles the elements of the dataset to avoid overfitting if the data has intrinsic sorting | Groups the elements of the dataset to batches of size batch_size |

The df_to_dataset function shown in 9.11, is taken directly from https://tensorflow.org/tutorials/structured_data/preprocessing_layers, will be applied to the training, validation, and test datasets to convert them into tf.data Dataset objects, shuffle and batch the datasets. Note that the definition of the dataset takes two (df, a dictionary version of the input dataframe, and labels, the target values from the input dataframe). Also, note that applying prefetch(1) to the dataset allows the dataset to be processed more efficiently by overlaying the preprocessing and model execution of one batch while the next batch is being loaded.

The following list defines the get_normalization_layer() function, which defines a normalization layer for a given feature.

## List 9.12 Creating normalization layers for continuous columns

```python
# function from
https://www.tensorflow.org/tutorials/structured_data/preprocessing_layers
def get_normalization_layer(name, dataset):
    normalizer = layers.Normalization(axis=None)
    feature_ds = dataset.map(lambda x, y: x[name])
    normalizer.adapt(feature_ds)
    return normalizer
```

![](img/def89cc476fa39f4c54bd34e78d91674_368_0.png)

The get_normalization_layer() function defined in list 9.12, which is taken directly from https://www.tensorflow.org/tutorials/structured_data/preprocessing_layers, which will be applied to all the continuous columns that we want to train the model. This function scales input values to a distribution centered around 0 with a standard deviation of 1. For details about the normalization object defined in this function, see https://mgz.bz/YDDx. Note that for gradient boosting solutions, normalization would not be needed.

The following list presents the definition of the get_category_encoding_layer() which specifies an encoding layer for a given categorical column.

## List 9.13 Creating encoding layers for categorical columns

```python
# function from
https://www.tensorflow.org/tutorials/structured_data/preprocessing_layers
def get_category_encoding_layer(name, dtype, max_tokens=None):
    if dtype == 'string':
        index = layers.Lookup(max_tokens=max_tokens)
    else:
        index = layers.IntegerLookup(max_tokens=max_tokens)
    feature_ds = dataset.map(lambda x, y: x[name])
    index.adapt(feature_ds)
    encoder = layers.CategoryEncoding(num_tokens=
```

![](img/def89cc476fa39f4c54bd34e78d91674_368_1.png)

![](img/def89cc476fa39f4c54bd34e78d91674_368_2.png)

![](img/def89cc476fa39f4c54bd34e78d91674_368_3.png)

```python
    index.vocabulary_size()
return lambda feature: encoder(index(feature))
```

Applies multi-hot encoding to the indices

The get_category_encoding_layer() function defined in 9.13, which is taken directly from https://www.tensorflow.org/tutorials/structured_data/preprocessing_layers, will be applied to all the categorical columns that we use to train the model. In function, if a column is a string column, a layer is generated that turns strings into numeric indices; otherwise, a layer is created that turns integer values into numeric indices.

The following list shows the code to apply the df_to_dataset() function to the training, validation, and datasets.

## List 9.14 Applying of df_to_dataset() to train, validate, and test datasets

```python
# function from
# https://www.tensorflow.org/tutorials/structured_data/preprocessing_layers
train_ds = df_to_dataset(train, batch_size=batch_size)
val_ds = df_to_dataset(val, shuffle=False)
batch_size=batch_size
test_ds = df_to_dataset(test, shuffle=False)
batch_size=batch_size
```

| Generates training dataset | Generates validation dataset | Generates test dataset |
| :--- | :--- | :--- |

Once the code in 9.14 is applied, we will obtain the datasets and be ready to start the training process.

The following list shows the code to apply the df_to_dataset() function to the training, validation, and test datasets.

## List 9.15 Defining layers for continuous and categorical columns

```python
all_inputs = []
encoded_features = []

for header in config['continuous']:
  numeric_col = tf.keras.Input(shape=(1,), name=header)
  normalization_layer = get_normalization_layer(header, train_ds)
  encoded_numeric_col = normalization_layer(numeric_col)
  all_inputs.append(numeric_col)
  encoded_features.append(encoded_numeric_col)
```

Creates a normalization layer for continuous column

List for encoded features

Creates an encoding layer for categorical column

```python
for header in config['categorical']:
  categorical_col = tf.keras.Input(shape=(1,), name=header)
  encoding_layer = get_category_encoding_layer(header, train_ds)
  encoded_categorical_col = encoding_layer(categorical_col)
  all_inputs.append(categorical_col)
  encoded_features.append(encoded_categorical_col)
```

## CHAPTER 9 Deep learning best practices

In the code in 9.15, for each continuous column, get_normalization_layer() defines a normalization layer for the column. The new layer is added to the encoded_features list, and the column name is appended to the all_inputs list. For each categorical column, get_category_encoding_layer() defines an encoder for the column. The new layer is added to the encoded_features list, and the column name is appended to the all_inputs list. Once the code in 9.15 is run, the encoded_features list contains the following values:

| <KerasTensor: shape=(None, 1), dtype=float32 (created by layer 'Bathrooms')> | <KerasTensor: shape=(None, 1), dtype=float32 (created by layer 'Car Parks')> |
| :--- | :--- |
| <KerasTensor: shape=(None, 1), dtype=float32 (created by layer 'Rooms')> | <KerasTensor: shape=(None, 1), dtype=float32 (created by layer 'Size')> |
| <KerasTensor: shape=(None, 1), dtype=string (created by layer 'Location')> | <KerasTensor: shape=(None, 1), dtype=string (created by layer 'Property_Type')> |
| <KerasTensor: shape=(None, 1), dtype=string (created by layer 'Furnishing')> | <KerasTensor: shape=(None, 1), dtype=string (created by layer 'Size_type_bin')> |

If we look at the settings in the config file that specify the continuous and categorical columns used to train the model, we see that the matches matches in the _features list:

- categorical: # categorical columns
- Location
- Property Type
- Furnishing
- Size_type_bin
- continuous: # continuous columns
- Bathrooms
- Car Parks
- Rooms
- Size

Now we have defined the layers that correspond with the columns of the input dataset, we can define the model. The following shows the code that defines the model.

## Listing 9.16 Code to define the model

```python
all_features = tf.keras.layers.concatenate(encoded_features)
x = tf.keras.layers.Dense(32,
```

> Concatenates the features from the encoded_features list created in the code in listing 9.15
