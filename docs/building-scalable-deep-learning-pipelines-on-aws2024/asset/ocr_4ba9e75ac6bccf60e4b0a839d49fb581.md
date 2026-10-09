Parameters:

+   - file_path (str): Path to the CSV file.
- feature_cols (list): List of feature columns.
- train_ratio (float): Ratio of training data.
- seed (int): Random seed for splitting data.

Returns:

+   - tuple: Tuple containing train and test DataFrames.

```
"""
df = self.spark.read.csv(
    file_path,
    header=True,
    inferSchema=True
)
\ assembler = VectorAssembler(
    inputCols=feature_cols, outputCol='features')

df = assembler.transform(df)

scaler = StandardScaler(
    inputCol='features',
    outputCol='scaled_features',
    withMean=True,
    withStd=True
)

scaler_model = scaler.fit(df)

df = scaler_model.transform(df)

train_df, test_df = df.randomSplit(
    [train_ratio, 1-train_ratio],
    seed=seed
)

return train_df, test_df
```

589