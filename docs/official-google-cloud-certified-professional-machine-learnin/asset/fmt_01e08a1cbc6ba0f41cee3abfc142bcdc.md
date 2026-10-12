
# What-If Tool (WIT) for Model Inspection

You can use the What-If Tool (WIT) within notebook environments to inspect AI Platform Prediction models through an interactive dashboard. The What-If Tool integrates with TensorBoard, Jupyter Notebooks, Colab notebooks, and JupyterHub. It is also preinstalled on Vertex AI Workbench user-managed notebooks and TensorFlow instances.

To use WIT, you need to install the `witwidget` library, which is already installed in Vertex AI Workbench. Then configure `WitConfigBuilder` to either inspect a model or compare two models. The following is some example code to inspect a model:

```
PROJECT_ID = 'YOUR_PROJECT_ID'
MODEL_NAME = 'YOUR_MODEL_NAME'
VERSION_NAME = 'YOUR_VERSION_NAME'
TARGET_FEATURE = 'mortgage_status'
LABEL_VOCAB = ['denied', 'approved']
config_builder = (WitConfigBuilder(test_examples.tolist(), features.columns.tolist() + ['mortgage_status'])
  .set_ai_platform_model(PROJECT_ID, MODEL_NAME, VERSION_NAME, adjust_prediction=adjust_prediction)
  .set_target_feature(TARGET_FEATURE)
  .set_label_vocab(LABEL_VOCAB)
```

Then pass the config builder to `WitWidget`, and set a display height.

```
WitWidget(config_builder, height=800)
```

The What-If Tool displays an interactive visualization within your notebook. Try this Colab notebook to explore how the What-If Tool works:

`https://colab.research.google.com/github/pair-code/what-if-tool/blob/master/What_If_Tool_Notebook_Usage.ipynb`

## Retraining/Redeployment Evaluation

After the model is trained and deployed in the real world, over time model performance changes; your model is sensitive to change as user behavior and training data keeps changing with time. Although all machine learning models decay, the speed of decay varies with time. Data drift, concept drift, or both mostly cause this. Let us understand these terms.

### Data Drift

**Data drift** is a change in the statistical distribution of production data from the baseline data used to train or build the model. You can detect data drift if the feature attribution of your model changes or the data itself changes. For example, suppose you built a model with temperature data collected from an IoT sensor in Fahrenheit degrees but the unit changed to Celsius. This means there has been a change in your input data, so the data has drifted. You can detect data drift by examining the feature distribution or correlation between features or checking the data schema over baseline using a monitoring system.

### Concept Drift

**Concept drift** is a phenomenon where the statistical properties of the target variable you're trying to predict change over time. For example, say you build a model to classify positive and negative sentiment of Reddit feed around certain topics. Over time, people's sentiments about these topics change. Tweets belonging to a positive sentiment may evolve over time to be negative.

In order to detect drift, you need to monitor your deployed model, which can be done by Vertex AI Model Monitoring. We will cover this topic in detail in [Chapter 12](#c12.xhtml), "Model Monitoring, Tracking and Auditing Metadata."

### When Should a Model Be Retrained?

Decide on a retraining strategy based on [Table 8.7](#c08.xhtml#c08-tbl-0006). We will discuss how you can use Vertex AI pipelines and Vertex AI Model Monitoring to set up retraining in [Chapter 12.](#c12.xhtml)

**TABLE 8.7** Retraining strategies

| Strategy | Description |
| :--- | :--- |
| Periodic training | You can choose an interval such as weekly, monthly, or yearly for retraining your model. It depends on how frequently your training data gets updated. Retraining your model based on an interval only makes sense if it aligns with your business use case. The selection of a random period for model retraining can give you a worse model than the previous model. |
| Performance-based trigger | If your model performance falls below your set threshold, which is the ground truth or baseline data, this automatically triggers the retraining pipeline. This approach assumes that you have implemented a sophisticated monitoring system in production. |
| Data changes trigger | If data drift happens, that should trigger a build for model retraining. Usually model performance changes in production, which can lead to data drift. |
| Retraining on demand | This is a manual and traditional way of retraining your models that employs traditional techniques. |

## Unit Testing for Model Training and Serving

Testing machine learning systems is hard because the code, model, and data all control the behavior of the system. Testing ML models means testing the model code as well as testing the data and the model. Unit tests allow us to test whether a unit of code is functioning as we expect it to.

Model testing involves explicit checks for behaviors that we expect our model to follow. Testing allows us to identify some bugs early. We can run some tests without needing trained parameters. These tests include the following:

*   Checking the shape of your model output and ensuring it aligns with the labels in your dataset.
*   Checking the output ranges and ensuring it aligns with your expectations (e.g., the output of a classification model should be a distribution with class probabilities that sum to 1).
*   Making sure a single gradient step on a batch of data yields a decrease in your loss.
*   Making assertions about your datasets.
*   Checking for label leakage between your training and validation datasets.

### Testing for Updates in API Calls

You can test updates to an API call by retraining your model, but that would be resource intensive. Rather, you can write a unit test to generate random input data and run a single step of gradient descent to complete without runtime errors.

### Testing for Algorithmic Correctness

To check your model for algorithmic correctness, follow these steps:

1.  Train your model for a few iterations and verify that the loss decreases.
2.  Train your algorithm without regularization. If your model is complex enough, it will memorize the training data and your training loss will be close to 0.
3.  Test specific subcomputations of your algorithm. For example, you can test that a part of CNN runs once per element of the input data.

## Summary

In this chapter, we discussed various file types such as structured, unstructured, and semi-structured and how they can be stored and ingested for AI/ML workloads in GCP. We divided the file ingestion into Google Cloud Platform into stages such as collect, process, store, and analyze and discussed services that can help at each stage. We covered Pub/Sub and Pub/Sub Lite to collect real-time data and BigQuery Data Transfer Service and Datastream to migrate data from third-party sources and databases to Google Cloud. In the process phase, we covered how we can transform the data using services such as Cloud Dataflow, Cloud Data Fusion, Cloud Dataproc, Cloud Composer, and Cloud Dataprep.

Then we talked about how you can train your model using Vertex AI training. Vertex AI training supports frameworks such as scikit-learn, TensorFlow, PyTorch, and XGBoost. We talked about how you can train a model using prebuilt containers and custom containers.

We also covered why and how you can unit test the data and model for machine learning.

Then we covered hyperparameter tuning and various search algorithms for hyperparameter tuning available in Google Cloud, as well as Vertex AI Vizier and how it's different than hyperparameter tuning.

You learned how you can track and debug your training model in Vertex AI metrics using Vertex AI interactive shell, TensorFlow Profiler, and the What-If Tool.

You also learned about data drift and concept drift and when you should retrain your model to avoid drift.

## Exam Essentials
