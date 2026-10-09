```
        .rdd.flatMap(lambda x: x)
        .collect()
    )

test_diabetes_df = spark.read.parquet(
    test_parquet_path
)
X_test = np.array(
    test_diabetes_df
    .select("scaled_features")
    .rdd.flatMap(lambda x: x)
    .collect()
)
y_test = np.array(
    test_diabetes_df
    .select("Outcome")
    .rdd.flatMap(lambda x: x)
    .collect()
)

best_model = DiabetesModelTrainer.train_tensorflow_model(
    X_train,
    y_train,
    X_test,
    y_test
)

DiabetesModelEvaluator.evaluate_model(
    best_model,
    X_test,
    y_test
)
```