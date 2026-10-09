```
```
Calculates the correlation between each
feature and the
target variable ('Outcome').
"""
if self.data is not None:
    print("Feature-Target Correlation "
    "(excluding 'SkinThickness', 'Insulin'):")
    for column in self.data.columns:
        if column not in ['Outcome',
                          'SkinThickness',
                          'Insulin']:
            correlation = self.data.filter(
                (col(column) != 0)
                & (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            ).stat.corr(column, 'Outcome')
            print(f"{column}: {correlation}")
    else:
        print("Data not loaded.")
```
```

```
```
[In]: def copy_file_from_s3(bucket_name, file_key, local_path):
    """
    Copies a file from an AWS S3 bucket to a local path.

    Args:
        bucket_name (str): The name of the S3 bucket.
        file_key (str): The key of the file in the S3 bucket.
        local_path (str):
            The local path where the file will be copied.
    """
```
```