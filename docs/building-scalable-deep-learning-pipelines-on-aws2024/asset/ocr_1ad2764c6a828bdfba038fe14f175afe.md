```
```python
X_train = np.array(train_diabetes_df.select(
    "scaled_features")
    .rdd.flatMap(lambda x: x).collect()
)
y_train = np.array(
    train_diabetes_df.select("Outcome")
    .rdd.flatMap(lambda x: x).collect())

trained_model =
    DiabetesModelTrainer.train_tensorflow_model(
        X_train,
        y_train
)

test_diabetes_df = spark.read.parquet(test_
    parquet_path)
X_test = np.array(
    test_diabetes_df.select("scaled_features")
    .rdd.flatMap(lambda x: x).collect())
y_test = np.array(
    test_diabetes_df.select("Outcome")
    .rdd.flatMap(lambda x: x).collect()
)

DiabetesModelEvaluator.evaluate_model(
    trained_model,
    X_test,
    y_test
)

except Exception as e:
    logger.error(f"An error occurred: {str(e)}")
```
```