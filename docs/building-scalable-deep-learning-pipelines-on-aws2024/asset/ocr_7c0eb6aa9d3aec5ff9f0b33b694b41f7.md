```
```python
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)
```
```

```
```python
[In]: class CustomCallback(Callback):
    """Custom Keras callback for printing epoch
    information."""
    def on_epoch_end(self, epoch, logs=None):
        """Prints epoch information every 10 epochs."""
        if (epoch + 1) % 10 == 0:
            logger.info(
                f"Epoch [{epoch + 1}/{self.
                    params['epochs']},"
                f"Loss: {logs['loss']:.4f}"
            )
```
```

```
```python
[In]: class DiabetesProcessor:
    """Class for preprocessing diabetes data."""
    @staticmethod
    def preprocess_data(spark, data_file_path,
                        train_parquet_path, test_parquet_path):
        """Preprocesses the diabetes data using
        PySpark."""
        try:
            diabetes_df = spark.read.csv(
                data_file_path,
                header=True,
                inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            )
```
```