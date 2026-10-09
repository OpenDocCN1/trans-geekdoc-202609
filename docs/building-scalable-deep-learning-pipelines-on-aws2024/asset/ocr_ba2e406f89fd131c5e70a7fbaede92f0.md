```
```
[In]: def print_first_5_observations(df: DataFrame,
        heading: str):
       """

       Print the first 5 observations of the DataFrame with
       a custom heading.
       """
       logger.info(heading)
       df.show(5, truncate=False)
```

```
[In]: def create_data_loader(features, labels, batch_size):
       """

       Create a TensorFlow Dataset for batch processing.
       """
       dataset = tf.data.Dataset.from_tensor_slices(
            (features, labels)
        )
       dataset = dataset.shuffle(buffer_size=10000)
       dataset = batch(batch_size)
       return dataset
```

```
[In]: def copy_file_from_s3(bucket_name: str, file_key: str,
           local_file_path: str):
       """

       Copy file from S3 bucket to local file path.
       """

       s3 = boto3.client('s3')
       s3.download_file(bucket_name, file_key, local_
       file_path)
       logger.info(
           f"File downloaded from S3 bucket {bucket_name}"
           f"to local file path: {local_file_path}"
       )
```
```