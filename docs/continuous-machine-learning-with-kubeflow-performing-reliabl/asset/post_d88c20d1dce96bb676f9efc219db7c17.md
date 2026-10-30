
```
config = kubeflow_dag_runner.KubeflowDagRunnerConfig(
 kubeflow_metadata_config=metadata_config, tfx_image='gcr.io/tfx-oss-public/tfx:0.22.0')
 kfp_runner =
 kubeflow_dag_runner.KubeflowDagRunner(output_filename='pipe9' +
 '.yaml', config=config)
 kfp_runner.run(pipeline)
```

After running the preceding code, it will dump a yaml, as shown in the following screenshot. Before running the file, replace the bucket name here in step1/2.

![](img/8f8a671916d96b455297952d0f37b96c_302_0.png)

Figure 4.32: Kubeflow Pipeline yaml

Once we dump the yaml, complete the following steps to run the pipeline in Kubeflow:

Upload the pipeline.yaml file in the Kubeflow pipeline, and click on

![](img/8f8a671916d96b455297952d0f37b96c_303_0.png)

Figure 4.33: Upload pipeline.yaml

Next, create an experiment if you haven’t yet; we have done so already in our previous chapters. After that, click on Run and choose that pipeline.

![](img/8f8a671916d96b455297952d0f37b96c_303_1.png)

Figure 4.34: Create Run

Before starting the pipeline, run ‘choose an experiment’ and then change the following parameters, like replacing your Bucket name; for example: tfx-pipeline is my bucket name and tfx is my experiment name.

Click on

![](img/8f8a671916d96b455297952d0f37b96c_304_0.png)

Figure 4.35: Pipeline parameters

After that, the pipeline will be ready, as shown in the following screenshot:

![](img/8f8a671916d96b455297952d0f37b96c_305_0.png)

Figure 4.36: Pipeline of TFX

Each pipeline component, represented as a block, is a self-contained piece of code, packaged as a Docker image. It contains the inputs (arguments) and outputs and performs one step in the pipeline. In the example pipeline, shown earlier, the transform_data step requires the arguments that are produced as an output of the extract_data and of the generate_schema steps, and its outputs are the dependencies for

Your ML code is wrapped into components, where you can do the following:

Specify **parameters** – which become available to edit in the dashboard and configurable for every run.

Attach **persistent volumes** – without adding persistent volumes, we would lose all the data if our notebook was terminated for any reason.

Specify **artifacts** to be generated – graphs, tables, selected images, models – which end up conveniently stored on the Artifact Store, inside the Kubeflow dashboard.

Finally, when you run the pipeline, each container will now be executed throughout the cluster, according to the Kubernetes scheduling, taking the dependencies into consideration. This containerized architecture makes it simple to reuse, share, or swap out the components as your workflow changes, which tends to happen.

![](img/8f8a671916d96b455297952d0f37b96c_307_0.png)

Figure 4.37: Kubeflow pipeline visualization

After running the pipeline, you will be able to explore the results on the **pipelines** debug, tweak parameters, and run experiments by executing the pipeline with the different parameters or data sources.

Now, after the completion of the pipeline, run the model artifacts dumped inside the GCS bucket. In the following screenshot, we can see the serving model directory:

Bucket details

tfx-pipeline

Buckets > [redacted] > tfx_taxi_simple > 6d011835-562c-49d0-bea2-a06048a601ce

OBJECTS  CONFIGURATION  PERMISSIONS  RETENTION  LIFECYCLE

UPLOAD FILES  UPLOAD FOLDER  CREATE FOLDER  MANAGE HOLDS  DELETE

Filter  Filter by object or folder name prefix

| Name | Size | Type | Created time | Storage class | Last modified | Public access |
|---|---|---|---|---|---|---|
| CsvExampleG | - | Folder | - | - | - | - |
| Evaluator/ | - | Folder | - | - | - | - |
| ExampleValidi | - | Folder | - | - | - | - |
| Pusher/ | - | Folder | - | - | - | - |
| SchemaGen/ | - | Folder | - | - | - | - |
| StatisticsGen/ | - | Folder | - | - | - | - |
| Trainer/ | - | Folder | - | - | - | - |
| Transform/ | - | Folder | - | - | - | - |
| model_servin | - | Folder | - | - | - | - |

Figure 4.38: Kubeflow pipeline Artifacts & Model in GCS

## 4.7 Conclusion

In this chapter, we learned how to build the TFX pipeline for the BERT Model for production ready with the integration of Visualization Tools like Fairness, Tensorboard, TFMA.

We also learned how to load the BERT Model from TF-HUB and how to use it. Then, we learned about the transformation pipeline prior to training the Model. We have also learned how to train our BERT Model with the distributed GPU Node strategy. Then, we created a pipeline with the TFX Components and visualized and evaluated the blessed model with the Fairness Indicators and metrics. Then, we loaded the server model and tested with a sample movie review and checked its sentiment probability.

## 4.8 Reference

https://www.tensorflow.org/tfx/tutorials

https://www.tensorflow.org/responsible_ai/fairness_indicators/tutorials/Fairness_Indicators_Example_Colab

## CHAPTER 5

### ML Model Explainability & Interpretability

In this chapter, we will work for a classification model with the hotel booking dataset, train the TensorFlow and boosting models, and visualize the advanced explanation of our model results with Tensorboard, Shap, and What-if products.

### Structure

In this chapter, we will cover the following topics:

- Problem statement
- Getting started with Python library installation and data loading in Colab
- Feature transformation for Training Model
- LightGBM Model training
- Model Analysis with advance visualization along Shap tool
- TensorFlow Estimator Model Building Framework
- Advance Visualization for TensorFlow Model with Tensorboard, What-IF Tool and Fairness

### Objectives

After studying this chapter, we will be able to understand the following:

The implementation of Shapely Additive explanations and how to use it's different approach on model evaluation.

How to build LightGBM model building from scratch.

The different Advance Shap plots for model analysis.

How to build the TensorFlow Estimator Framework end to end.

How to evaluate the Model performance with the What-if Tool alongside the Fairness indicator.

### 5.1 Problem

The problem statement for this data set contains the booking information for a city hotel and a resort hotel, which includes some information, such as when the booking was made, length of stay, and the number of adults, children, or babies, and the number of available parking spaces, among other things.

Have you ever wondered when the best time is in a year to book a hotel room? Or wondered about the optimal length of stay in order to get the best daily rate? Or, what if you wanted to predict whether or not a hotel is familiar to receive a disproportionately high amount of special requests?

requests? requests? requests? requests? requests? requests?
requests? requests? requests? requests? requests? requests?
requests? requests? requests? requests? requests? requests?
requests? requests? requests? requests? requests? requests?
requests? requests? requests? requests? requests? requests?
requests?

requests?

### 5.2 General idea and concept behind Shap

The goal of SHAP is to explain the prediction of an instance x by computing the contribution of each feature to the prediction. From the coalitional game theory, the shapely values were computed from the SHAP explanation methods. Each feature value instance acts as players in a coalition. How to fairly distribute the prediction among the features, Shapley values tells us that. A player is an individual feature value, for example, from a tabular data. A group of feature values can also be a player.

For example, the prediction distribution among the image pixels can also be grouped to super pixels. One of the innovation that SHAP brought to the table is an additive feature attribution method, a linear model that explain the Shapley value.

SHAP specifies the explanation as follows:

g(z') = ∅ₒ + ∑_{j=0}^{M} ∅_j Z'_j

SHAP describes the following three desirable properties:

### Local accuracy
