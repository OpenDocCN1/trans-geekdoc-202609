```
dag = DAG('test', default_args=default_args, schedule_
interval=timedelta(days=1))
```

```
t1 = BashOperator(
task_id='print_date',
bash_command='date',
dag=dag)
```

```
t2 = BashOperator(
task_id='sleep',
bash_command='sleep 5',
retries=3,
dag=dag)
```

```
t2.set_upstream(t1)
```

Airflow can connect to many different sources and has built-in operators for many external services, such as AWS EMR and Amazon SageMaker. It has been widely adopted by many enterprises in production environments.

# Kubeflow Pipelines

Kubeflow Pipelines is a Kubeflow component, and it is purpose-built for authenticating and orchestrating end-to-end ML workflows on Kubernetes. First, let's review some core concepts of Kubeflow Pipelines:

+   -Pipeline**: A pipeline describes an ML workflow, all the components in the workflow, and how the components are related to each other in the pipeline.
- **Pipeline components**: A pipeline component performs a task in the pipeline. An example of a pipeline component could be a data processing component or model training component.
- **Experiment**: An experiment organizes different trial runs (model training) for an ML project so you can easily inspect and compare the different runs and results.
- **Step**: The execution of one component in a pipeline is called a step.