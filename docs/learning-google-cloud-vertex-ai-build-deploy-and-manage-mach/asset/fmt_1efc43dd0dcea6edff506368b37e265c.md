
### Function `fetch_eval_info`

Function `fetch_eval_info` will fetch the evaluation data from the trained model artifacts, which will be passed to the `metrics_log_check` function to check if the model performance is above the threshold and returns the value to be `true` (if the model performance is better than the threshold) or `false` (otherwise).

```python
DISPLAY_NAME = 'image_boat_classification'

@kfp.dsl.pipeline(name="image-classification", pipeline_root=pipeline_folder)
def pipeline(
    gcs_source: str = "gs://pipeline_automl/class_labels.csv",
    display_name: str = DISPLAY_NAME,
    project: str = PROJECT_ID,
    gcp_region: str = "us-central1",
    api_endpoint: str = "us-central1-aiplatform.googleapis.com",
    thresholds_dict_str: str = '{"auPrc": 0.60}',
):
    # First component
    dataset_create_op = gcc_aip.ImageDatasetCreateOp(
        project=project,
        display_name=display_name,
        gcs_source=gcs_source,
        import_schema_uri=aiplatform.schema.dataset.ioformat.image.single_label_classification
    )

    # Second component
    training_op = gcc_aip.AutoMLImageTrainingJobRunOp(
        project=project,
        display_name=display_name,
        prediction_type="classification",
        budget_milli_node_hours=8000,
        dataset=dataset_create_op.outputs["dataset"],
    )

    # Third component
    model_eval_task = image_classification_model_eval_metrics(
        project,
        gcp_region,
        api_endpoint,
        thresholds_dict_str,
        training_op.outputs["model"],
    )

    with dsl.Condition(
        model_eval_task.outputs["dep_decision"] == "true",
        name="deploy_decision",
    ):
        # Fourth component is end point creation only if the condition is met
        endpoint_op = gcc_aip.EndpointCreateOp(
            project=project,
            location=gcp_region,
            display_name="train-automl-vision",
        )

        # Fifth component of the pipeline is deploying model on the endpoint created.
        gcc_aip.ModelDeployOp(
            model=training_op.outputs["model"],
            endpoint=endpoint_op.outputs["endpoint"],
            automatic_resources_min_replica_count=1,
            automatic_resources_max_replica_count=1
        )
```

### Step 7: Compile using Kubeflow

Run the following code to compile the pipeline code. The correct data type usage in pipelines is verified by the Kubeflow Pipelines SDK v2 compiler, as is the avoidance of inputs from parameters being used as outputs from artifacts and vice versa:

```python
compiler.Compiler().compile(pipeline_func=pipeline, package_path="image_classif_pipeline.json")
```

Once the code is executed, a JSON file named `image_classif_pipeline` will be created as shown in [Figure 6.10](#ch06.xhtml#fig6-10):

![](images/Figure_6.10.png)

**Figure 6.10:** JSON file created for the custom model evaluation component

1.  Open the JSON file:

    ![](images/Figure_6.11.png)

    **Figure 6.11:** JSON file contents

The JSON will have all the details regarding components of the pipeline, parameters of each component, run time configuration, parameters, and so on.

Except the model evaluation component, all other components will be executed on the ML-pipeline component. Only the model evaluation component will be executed on the deep-learning packages (which is mentioned in the code).

### Step 8: Pipeline creation

Run the following code to create the pipeline:

```python
ml_pipeline_job = aiplatform.PipelineJob(
    display_name="automl-image-training",
    template_path="image_classif_pipeline.json",
    pipeline_root=pipeline_folder,
    parameter_values={"project": PROJECT_ID, "display_name": DISPLAY_NAME},
    enable_caching=True
)
```

### Step 9: Submitting the Pipeline job

Run the following code to submit the pipeline job. The link will be provided once the code is executed for the pipeline as shown in [Figure 6.12](#ch06.xhtml#fig6-12):

```python
ml_pipeline_job.submit()
```

![](images/Figure_6.12.png)

**Figure 6.12:** Pipeline link in the notebook file

1.  Once the pipeline job is submitted, a link will be provided to check the status of the pipeline. Click on it.

### Execution of Pipeline

Once the job is submitted for execution, the pipeline will be visible under the pipeline section of Vertex AI. The status of each component will be displayed (yet to start, success, failure). Follow the below steps to check the status of the submitted pipeline.

#### Step 1: Pipeline of image classification

Open the link as shown in [Figure 6.13](#ch06.xhtml#fig6-13) to navigate to pipelines of Vertex AI. The pipeline will start executing and this exercise will take about 90 to 120 mins. All the five tasks in the exercise will be executed sequentially. Once the complete pipeline is executed, you will see a green colored tick mark on all the components as shown in [Figure 6.13](#ch06.xhtml#fig6-13):

![](images/Figure_6.13.png)

**Figure 6.13:** Pipeline created

1.  Indicating all the steps in the pipelines are executed successfully.
2.  Click on **Summary** section of the pipeline.
3.  **Basic info** provides the information of pipeline run, region, link to view the logs, and so on.
4.  **Run parameter** provides information regarding the parameters that are used for the pipeline. Scroll down to get the run metrics in the **Summary** section.
5.  Click the toggle button to expand the artifacts.

#### Step 2: Expand artifacts

Artifacts will be expanded in the pipeline as shown in [Figure 6.14](#ch06.xhtml#fig6-14):

![](images/Figure_6.14.png)

**Figure 6.14:** Components and artifacts of the pipeline

1.  The first component in the pipeline is to create a dataset from the csv and image files from the cloud storage.
2.  Click on **Node Info** to get the basic info, input parameters and output parameters for first component.
3.  **View logs** populates the log for this component at the bottom section.
4.  Artifacts of the dataset created. Click on the artifact component in the node info; a link will be provided to the dataset created. Refer to [Figure 6.15](#ch06.xhtml#fig6-15).
5.  Artifacts of the trained model. Click on the artifact component in the node info; a link will be provided to the trained model is saved. Refer [Figure 6.16](#ch06.xhtml#fig6-16).
6.  Click on **metrics** to get the confusion matrix in the JSON format, and other model evaluation metrics.
7.  Click on **metrics** to get the confusion matrix in the image format.

> **Note:** If the pipeline fails due to errors in any components, users can troubleshoot the component and re-run the pipeline. In this scenario the successfully executed components will not be executed again and the results will be picked from the cache.

The created dataset available under the dataset module of Vertex AI is shown in [Figure 6.15](#ch06.xhtml#fig6-15):

![](images/Figure_6.15.png)

**Figure 6.15:** Dataset section of Vertex AI

Trained model will be available under the model section of Vertex AI as shown in [Figure 6.16](#ch06.xhtml#fig6-16):

![](images/Figure_6.16.png)

**Figure 6.16:** AutoML classification model listed under model registry of Vertex AI

#### Step 3: Model deployment

In this exercise, since the model performance was above the threshold, an endpoint is created, and the model is deployed to the endpoint as shown in [Figure 6.17](#ch06.xhtml#fig6-17):

![](images/Figure_6.17.png)

**Figure 6.17:** Model deployed to endpoint

#### Step 4: Pipeline artifacts stored in cloud storage

Pipeline artifacts are stored in the cloud storage as shown in [Figure 6.18](#ch06.xhtml#fig6-18):

![](images/Figure_6.18.png)

**Figure 6.18:** Pipeline artifacts stored in the cloud storage

### Deleting resources

We have utilized Workbench, Cloud Storage to store the images, the model has been trained and deployed to the endpoint. You need to ensure to delete the Workbench, clear the data stored in the Cloud Storage, delete the dataset created, remove the model from the endpoint, and delete the endpoint.

### Conclusion
