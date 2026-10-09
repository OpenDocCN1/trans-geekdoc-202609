
# Define the names of the files to be included in the zip file
```python
[In]: files_to_zip = [
        'data_processing.py',
        'model_training.py',
        'model_evaluation.py',
        'utils.py',
        'tesla_stock_prediction.py',
        'requirements.txt'
    ]

# Define the name of the zip file
[In]: zip_file_name = 'tesla_stock_prediction.zip'

# Create a zip file containing the specified files
[In]: with zipfile.ZipFile(zip_file_name, 'w') as zip_file:
        for file_name in files_to_zip:
            file_path = os.path.join(dags_directory,
                                     file_name)
            zip_file.write(file_path, arcname=file_name)

# Upload the zip file to the S3 bucket
[In]: bucket_name = 'instance1bucket'
[In]: s3_client = boto3.client('s3')
[In]: s3_client.upload_file(
        zip_file_name,
        bucket_name,
        f'dags/{zip_file_name}')

# Clean up: remove the zip file
[In]: os.remove(zip_file_name)
[In]: print("Files zipped and uploaded successfully.")
```

This code prepares and uploads the DAG files to Amazon S3. First, the necessary libraries are imported. These include `os` for interacting with the operating system, `zipfile` for handling zip file operations, and `boto3` for interacting with Amazon Web Services (AWS) services like S3. The directory containing the DAG files is specified as `dags_directory`, set to `/home/ubuntu/airflow/dags`. This directory holds the Python files constituting the DAG and other associated files needed for its execution. A list named `files_to_zip` is defined, containing the names of the files that will be included in the zip file. These comprise the Python scripts defining the DAG logic:

- data_processing.py
- model_training.py
- model_evaluation.py
- utils.py
- tesla_stock_prediction.py
- requirements.txt

The name of the zip file is specified as `zip_file_name`, set to `tesla_stock_prediction.zip`. This file will serve as the packaged collection of DAG files ready for deployment. A `zipfile.ZipFile` context manager is initiated to create the zip file specified by `zip_file_name`. Within this context, each file listed in `files_to_zip` is added to the zip file. The `arcname` parameter ensures that the files are stored within the zip file with the same directory structure as in `dags_directory`.

Once the zip file is created and populated with the necessary files, it's time to upload it to an S3 bucket. The bucket name is specified as `instance1bucket`, and the `boto3` client for S3 is initialized. The `upload_file` method is then called on the client, specifying the local zip file, the destination bucket, and the path within the bucket where the file should be stored.

After the upload is successful, the local zip file is removed to clean up the workspace using `os.remove(zip_file_name)`. Finally, a success message is printed to indicate that the files were zipped and uploaded successfully.

Packaging DAGs along with their dependencies in this way simplifies deployment processes, ensures all necessary components are included, and facilitates consistency in versioning and dependency management across different environments.

## Step 4: Configuring the MWAA Environment

The next step in the deployment process after uploading the DAG files to the designated S3 bucket is to configure the MWAA environment to include the uploaded DAG and specify any additional settings such as environment variables, connections, and plugins. This step is crucial for ensuring that the MWAA environment can effectively manage and execute the DAG according to your requirements.

To configure the MWAA environment:

- Start by accessing the Amazon MWAA console and navigating to the environment settings for the target MWAA environment where you intend to deploy the DAG.
- Within the environment configuration, locate the section dedicated to DAGs and specify the S3 path to the uploaded DAG file. This informs MWAA about the location of the DAG file in the S3 bucket and allows it to retrieve the file for execution.

In addition to specifying the DAG file:

- Set environment variables to provide configuration parameters or secrets required by the DAG during runtime.

- Environment variables can include settings such as database connection strings, API keys, or any other sensitive information needed by the DAG for its operation.

- By configuring environment variables within the MWAA environment, you ensure that the DAG has access to the necessary resources without exposing sensitive information directly in the DAG code.

Additionally, plugins containing additional Airflow operators, hooks, or sensors may be required to support specific functionalities within the DAG:

- Ensure that the necessary plugins are installed and configured in the MWAA environment to provide the required functionality for executing the DAG.

- This includes installing any custom or third-party plugins and specifying their configurations within the MWAA environment.

## Step 5: Triggering DAG Execution

After the DAG has been successfully deployed and configured in the Amazon MWAA environment, you can trigger its execution manually or based on a predefined schedule within the MWAA environment:

- Manual Execution: You can manually trigger the execution of the DAG from the MWAA console. Navigate to the DAGs view in the MWAA console, locate the DAG, and initiate its execution by clicking the “Trigger DAG” button. This will immediately start the execution of the DAG, and you can monitor its progress and view logs from the MWAA console.
- Scheduled Execution: Alternatively, you can schedule the DAG to run automatically based on a predefined schedule. In the MWAA environment configuration, specify the desired schedule interval for the DAG execution using the `schedule_interval` parameter. For example, to trigger the DAG execution daily, you can set `schedule_interval=timedelta(days=1)` in the DAG definition. Amazon MWAA will then automatically trigger the execution of the DAG according to the specified schedule.

## Step 6: Monitoring Execution

Once triggered, Amazon MWAA will start executing the DAG tasks according to their defined dependencies and the schedule interval. The tasks will run in the specified sequence (e.g., in simple_mwaa_dag.py DAG, print_date executes first followed by print_message). You can monitor the progress of the DAG execution, view task logs, and troubleshoot any issues that may arise from the MWAA console.

Monitoring deep learning models is crucial for several reasons, particularly in production environments managed by services like Amazon MWAA. One reason is ensuring the performance and accuracy of the models over time. Models can experience performance degradation due to changes in data distribution (data drift) or shifts in the relationship between input features and target variables (concept drift). Continuous monitoring helps detect such issues early, allowing for timely retraining or adjustments to maintain accuracy.

Operational efficiency is another key reason for monitoring deep learning models. By keeping track of resource utilization—such as CPU, GPU, and memory usage—you can ensure that the model runs efficiently and identify any bottlenecks that may arise. Monitoring latency is also critical, particularly for real-time applications where meeting response time requirements is essential. Ensuring that models operate reliably and are available when needed is fundamental to maintaining system integrity. Monitoring can detect failures or errors in the model's operation, facilitating quick troubleshooting and minimizing downtime. Additionally, it helps in understanding and managing the scalability of the model under varying loads.

More importantly, compliance and governance are increasingly important in many industries, especially those dealing with sensitive data such as finance and healthcare. Monitoring models ensures that audit trails are maintained, which is crucial for regulatory compliance. Finally, security is another critical aspect that benefits from diligent monitoring. By detecting unusual patterns or anomalies, monitoring can alert you to potential security breaches.

You can monitor your deep learning models in two ways:

- Through the MWAA console and Apache Airflow UI for direct DAG monitoring
- Using Amazon CloudWatch for comprehensive metrics and logs tracking

The MWAA console and the Apache Airflow UI allow you to set up, manage, and monitor workflows that include tasks such as data preprocessing, model training, evaluation, and deployment. This enables you to automate and schedule these tasks while keeping an eye on their execution and performance.

To monitor DAGs running in Amazon MWAA using the MWAA console, follow the below steps:

- Log into the AWS Management Console and navigate to the Amazon MWAA service.
- Choose the MWAA environment where your DAGs are running. This will bring up the environment details page.
