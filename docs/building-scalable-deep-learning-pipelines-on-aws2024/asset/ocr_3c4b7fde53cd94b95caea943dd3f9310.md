# CHAPTER 3  DATA PREPARATION WITH PYSRARK FOR DEEP LEARNING

```
[In]: class DataProcessor:
          def __init__(self, spark_session):
              self.spark = spark_session

          def load_data(self, file_path: str):
              try:
                  df = self.spark.read.csv(
                        file_path,
                        header=True,
                        inferSchema=True
                   )
                  return df
              except Exception as e:
                  print(f"Error loading data: {str(e)}")
                  return None

          def print_first_n_rows(self, df, n=10):
              print(f"First {n} rows of the DataFrame:")
              df.show(n)

          def print_partition_info(self, df):
              num_partitions = df.rdd.getNumPartitions()
              print(f"Number of partitions: {num_partitions}")
```

```
[In]: def copy_file_from_s3(
            bucket_name: str,
            file_key: str,
            local_file_path: str
        ):
            try:
                s3 = boto3.client('s3')
                s3.download_file(bucket_name, file_key, local_file_path)
```