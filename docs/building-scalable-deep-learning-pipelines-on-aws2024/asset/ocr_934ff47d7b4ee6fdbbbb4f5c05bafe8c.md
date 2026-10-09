+   * schedule_interval=None: Sets the schedule interval for the DAG's execution. Here, None indicates
that the DAG is not scheduled to run on a regular
interval. Instead, it can be triggered manually or by
external events.

# Step 4: Define Tasks

In this step, we define three tasks corresponding to the three modules
of the previous subsection: preprocessing data, training the TensorFlow
model, and evaluating the trained model.

We begin by defining the preprocess_task that will execute the
preprocess_data function with the specified arguments as part of the
Airflow DAG:

```
```python
[In]: preprocess_task = PythonOperator(
    task_id='preprocess_data',
    python_callable=preprocess_data,
    op_kwargs={
        'data_file_path': ("/home/ubuntu/airflow/dags"
                            "/diabetes.csv"),
        'train_parquet_file_path': ("/home/ubuntu/
            airflow/dags"
                            "/diabetes_train.
                            parquet"),
        'test_parquet_file_path': ("/home/ubuntu/
            airflow/dags"
                            "/diabetes_test.
                            parquet")
    },
    dag=dag,
)
```
```