
# You can also run MLFlow using a Google Cloud plug‐in without needing to install the Docker image provided by MLFlow. Refer to this link for plug‐in details:

`https://pypi.org/project/google-cloud-mlflow`

## Testing for Target Performance

Some of the things you need to consider while testing your model for performance in production are as follows:

*   You need to check for training‐serving skew in the model and test the quality of the model in production with the real‐time data.
*   You can monitor the model age and performance throughout an ML pipeline.
*   You can test that model weights and outputs are numerically stable. For example, during model training, your weights and layer outputs should not be `NaN` or `null`. You need to write tests to check for `NaN` and `null` values of model weights and layer outputs. Moreover, you need to test that more than half of the outputs of a layer are not zero.

Vertex AI has services such as `Vertex AI Model Monitoring` and `Vertex AI Feature Store` that can help solve some of the testing issues for your deployed model in production, such as detecting skew and monitoring model performance over time.

For more information, see `https://developers.google.com/machine-learning/testing-debugging/pipeline/production`.

## Configuring Triggers and Pipeline Schedules

For this section, you need to know how to trigger a training or prediction job on the Vertex AI platform based on the use case.

For example, to trigger a real‐time prediction job, you can set up the prediction endpoint on the Google Cloud App Engine to create a serverless ML gateway. We covered the architecture pattern in the section “Serving (Online, Batch, and Caching)” earlier in this chapter.

The following are some of the services that will help create a trigger and schedule the training or prediction jobs on Vertex AI:

*   `Cloud Scheduler` can help you set up a cron job schedule to schedule your Vertex AI training or prediction jobs.
*   With `Vertex AI managed notebooks`, you can execute and schedule a Vertex training and prediction job using the Jupyter Notebook. Refer to this link to learn more: `https://cloud.google.com/vertex-ai/docs/workbench/managed/schedule-managed-notebooks-run-quickstart`.
*   `Cloud Build` is the CI/CD offering on GCP. If you want to retrain a model or build a `Dockerfile` and push it for custom training, use `Cloud Build` to kick it off. `Cloud Run` is a managed offering to deploy containers. Imagine that the container you're deploying is a Flask or FastAPI app that has your model. You can use `Cloud Build` to deploy your application to `Cloud Run`.
*   You can also use event‐driven serverless `Cloud Functions` and `Cloud Pub/Sub`. `Cloud Functions` are serverless and stateless functions as a service (FaaS), and `Pub/Sub` implements the publisher‐subscriber pattern. You can use an event‐based `Cloud Storage` trigger for a `Cloud Function` so that if a new version of a model is added to a bucket, you can activate a `Cloud Function` to start the deployment.

It's a challenge to use `Cloud Function` and `Pub/Sub` when there are multiple `Cloud Functions` doing multiple things. For example, `Cloud Function A` triggers data transform, then `cloud function B` triggers model training, and finally, `Cloud Function C` deploys the model. In this case, you would need an orchestrator to orchestrate these events in a pipeline. To orchestrate data cleaning, data transformation, model deployment, and model training using `Cloud Functions`, you can use `Cloud Workflows`.

**Cloud Workflows** orchestrate multiple HTTP‐based services into a durable and stateful workflow. Workflows are great for chaining microservices together, automating infrastructure tasks like starting or stopping a VM, and integrating with external systems. Workflow connectors also support simple sequences of operations in Google Cloud services such as `Cloud Storage` and `BigQuery`.

If you do not want to orchestrate using a `Cloud Function`, use `Cloud Scheduler` and `Workflows`.

Vertex AI provides the orchestration choices such as Vertex AI pipelines listed in [Table 10.3](#c10.xhtml#c10-tbl-0003), which we will cover in detail in the next chapter ([Chapter 11](#c11.xhtml), “Designing ML Training Pipelines”).

### TABLE 10.3 ML orchestration options

| Option | Description |
| --- | --- |
| Vertex AI Pipelines | Vertex AI Pipelines helps you to automate, monitor, and govern your ML systems by orchestrating your ML workflow in a serverless manner and storing your workflow's artifacts using Vertex ML Metadata. By storing the artifacts of your ML workflow in Vertex ML Metadata, you can analyze the lineage of your workflow's artifact. |
| Cloud Composer | Cloud Composer is designed to orchestrate data‐driven workflows (particularly ETL/ELT). It's built on the Apache Airflow project, but Cloud Composer is fully managed. Cloud Composer supports your pipelines wherever they are, including on‐premises or across multiple cloud platforms. All logic in Cloud Composer, including tasks and scheduling, is expressed in Python as directed acyclic graph (DAG) definition files. |

Read this blog for more information: `https://cloud.google.com/blog/topics/developers-practitioners/choosing-right-orchestrator-google-cloud`.

## Summary

In this chapter, we covered the details of TF Serving in scaling prediction service.

We discussed the `predict` function in TF Serving and how to know the output based on the `SignatureDef` of the saved TF model.

Then we discussed architecture for online serving. We dove deep into static and dynamic reference architectures. Then we discussed the architecture to use pre‐computing and caching while serving predictions.

We also covered how to deploy models using online and batch mode with Vertex AI Prediction and Google Cloud serving options. We covered the reasons for performance degradation in production when testing for target performance such as training‐serving skew, change in data quality, and so on. You learned about tools such as `Vertex AI Model Monitoring` that can help in testing for models in production.

Last, you learned about ways to configure triggers and schedules to automate a model pipeline, such as `Cloud Run`, `Cloud Build`, `Cloud Scheduler`, `Vertex AI managed notebooks`, and `Cloud Composer`.

## Exam Essentials

*   **Understand TensorFlow Serving.** Understand what TensorFlow Serving is and how to deploy a trained TensorFlow model using TF Serving. Know the different ways to set up TF Serving with Docker. Understand the TF Serving prediction response based on a saved model's `SignatureDef` tensors.
*   **Understand the scaling prediction services (online, batch, and caching).** Understand the difference between online batch and caching. For online serving, understand the differences in architecture and use cases with respect to input features that are fetched in real time to invoke the model for prediction (static reference features and dynamic reference features). Also, understand the caching strategies to improve serving latency.
*   **Understand the Google Cloud serving options.** Understand how to set up real‐time endpoints using Google Cloud Vertex AI Prediction for custom models or models trained outside Vertex AI; understand how to set up predictions using both APIs and the GCP console setup. Also, understand how to set up a batch job for any model using Vertex AI batch prediction.
*   **Test for target performance.** Understand why model performance in production degrades. Also understand at a high level how Vertex AI services such as `Vertex AI Model Monitoring` can help with performance degradation issues.
