```
local_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
s3_cli ent.upload_file(local_path, bucket_name, key)
print("File uploaded successfully.")
except Exception as e:
    print(f"An error occured: {e}")

[Out]: File uploaded successfully.
```

In this code, we reversed the order of the parameters compared with the code for downloading from S3. In other words, for downloading, the parameters were

s3_client.download_file(bucket_name, key, local_path)

For uploading, the parameters are

s3_client.upload_file(local_path, bucket_name, key)

It is worth noting that, if the file already exists in the destination location (S3 bucket in this case) and we attempt to upload a file with the same key (filename), it will typically overwrite the existing file with the new one.

# # Data Preprocessing (PySpark)

Once data is retrieved from S3, as explained in the preceding step, it undergoes preprocessing using PySpark, a distributed data processing framework that enables efficient data cleaning, transformation, and feature engineering on large datasets.

Leveraging PySpark for preprocessing tasks offers distinct advantages over traditional libraries like Pandas and Scikit-Learn. Firstly, its distributed nature allows PySpark to handle big data processing tasks with superior scalability and performance compared with single-node