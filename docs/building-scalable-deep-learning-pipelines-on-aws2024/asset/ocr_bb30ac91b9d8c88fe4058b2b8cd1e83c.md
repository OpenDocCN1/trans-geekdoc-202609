# CHAPTER 8 SCALABLE DEEP LEARNING PIPELINES WITH APACHE AIRFLOW

```
[In]: def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using
    SparkSession.
    """
    spark = SparkSession.builder \
        .appName("StockPricePrediction") \
        .getOrCreate()
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df
```

```
[In]: def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature
    vectors using
    VectorAssembler and scaling them using
    StandardScaler.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)

    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
```