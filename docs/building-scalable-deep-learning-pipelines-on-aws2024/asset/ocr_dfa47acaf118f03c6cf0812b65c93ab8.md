learning_rate (float): The learning rate for the optimizer. Defaults to 0.001.

num_workers (int): The number of subprocesses to use for data loading. Defaults to 4.

Raises: FileNotFoundError: If the specified data file is not found.

```
"""
try:
    subprocess.run([
        "aws", "s3", "cp",
        "s3://instance1bucket/TSLA_stock.csv",
        "/home/ubuntu/airflow/dags/"
    ])
    
    df = load_data(data_file_path)
    df = preprocess_data(df)
    
    train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
    
    train_features, train_labels = \\
        spark_df_to_tensor(train_df)
    test_features, test_labels = spark_df_to_tensor(test_df)
    
    train_loader = create_data_loader(
        train_features,
        train_labels,
        batch_size=batch_size,
        num_workers=num_workers
    )
```