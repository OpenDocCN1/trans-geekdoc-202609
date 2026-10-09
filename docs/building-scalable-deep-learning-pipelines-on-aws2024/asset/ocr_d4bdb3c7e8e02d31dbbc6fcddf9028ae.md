# CHAPTER 3    DATA PREPARATION WITH PYSPARK FOR DEEP LEARNING

```
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
         s3.download_file(bucket_name, file_key, local_
         file_path)
         print(f"File downloaded from S3 bucket
         {bucket_name} "
                f"to local file path: {local_file_path}"
         )
     except Exception as e:
         print(f"Error copying file from S3: {str(e)}")
```

```
[In]: def main(
         s3_bucket_name: str,
         s3_file_key: str,
         local_file_path: str
     ):
     spark = SparkSession.builder \\
         .appName("StockPriceOptimization") \\
         .config("spark.sql.adaptive.enabled", "true") \\
         .config("spark.sql.shuffle.partitions", "20") \\
         .getOrCreate()
```

147