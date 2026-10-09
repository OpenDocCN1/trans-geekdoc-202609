```
[In]: from pyspark.sql.functions import broadcast
```

```
[In]: small_df = spark.createDataFrame([
        ("2023-08-25", 5.5),
        ("2023-08-26", 6.0), ],
    ["Date", "AdditionalData"])
```

```
# Broadcast join
[In]: joined_df = repartitioned_df.join(
        broadcast(small_df),
        on="Date",
        how="left"
    )
```

Broadcasting the smaller DataFrame allows Spark to distribute it to all worker nodes, thus avoiding the shuffle operation that would be required for a regular join. This can significantly improve performance for joins involving large and small datasets.

Saving large datasets in Parquet format is another method to improve performance when processing large datasets in PySpark as Parquet supports compression and optimized read operations. Saving the DataFrame in Parquet format helps in reducing storage space and improving the speed of read operations due to its optimized layout.

The code below saves the repartitioned Tesla stock price dataset as Parquet:

```
[In]: repartitioned_df.write.parquet(
        "/home/ubuntu/airflow/dags/tesla_stock.parquet")
```

Finally, enabling Adaptive Query Execution (AQE) optimizes query execution based on runtime statistics. It can adjust query plans to improve performance by making decisions like optimizing join strategies or adjusting the number of shuffle partitions based on the actual data processed: