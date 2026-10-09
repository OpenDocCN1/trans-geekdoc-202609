```
try:
    s3 = boto3.client('s3')
    s3.download_file(bucket_name, file_key, local_path)
    print(f"File {file_key} downloaded to {local_path}")
except Exception as e:
    print(f"An error occurred while downloading file",
          f"{file_key}:", str(e))

[In]: if __name__ == "__main__":
    spark = (SparkSession.builder
             .appName("PimaDatasetExplorer")
             .getOrCreate())
    local_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
    s3_bucket_name = "instance1bucket"
    s3_file_key = "diabetes.csv"
    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )
    
    explorer = PimaDatasetExplorer(local_file_path)
    explorer.preprocess_data()
    explorer.handle_missing_values()
    explorer.count_zeros()
    explorer.data_summary()
    explorer.count_outcome()
    explorer.explore_feature_distributions()
    explorer.calculate_feature_target_correlation()
```