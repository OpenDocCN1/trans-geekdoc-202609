```
num_epochs (int):
The number of epochs for training the model.
Defaults to 100.
batch_size (int):
The batch size for data loading during
training.
Defaults to 32.
learning_rate (float):
The learning rate for the optimizer.
Defaults to
0.001.

Raises:
FileNotFoundError: If the specified data
file is not
found.

'''
try:
df = load_data(data_file_path)
df = preprocess_data(df)
train_df, test_df = df.randomSplit([0.8, 0.2],
seed=42)
train_features, train_labels = utils.spark_df_
to_tensor(
train_df
)
test_features, test_labels = utils.spark_df_
to_tensor(
test_df
)
```