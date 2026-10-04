# Defining the ML pipeline

This is the value that needs to be set for dataset_id in the pipeline config file pipeline_config.yml, as shown in 11.27.

```
ENDPOINT_NAME = 'klrealestate'
# from cloud.google.com/vertex-ai/docs/training/pre-built-containers
train_image = 'us-docker.pkg.dev/vertex-ai/training/tf-cpu.2-9-latest'
# from cloud.google.com/vertex-ai/docs/pre-built-containers
deploy_image = 'us-docker.pkg.dev/vertex-ai/prediction/tf2-2-9-latest'
config_path = "model_training_config.yml"
# Google Storage file containing the config settings for the training script
```

```
script_path = 'model_training_keras_preprocessing.py'
machine_type = 'n1-standard-4'
# project details
project_id = 'first-project-ml-tabular'
region = 'us-central1'
dataset_id = '290141542631119872'
11.27 dataset_id in the pipeline config file
```

Congratulations! You have set a Vertex AI managed dataset for the dataset that the model training portion of the ML pipeline will use to train the model.

# 11.3 Defining the ML pipeline

So far in this chapter, we have completed the following preparation steps for the pipeline:

+   1 Created a service account and a service account key
2 Uploaded the service account key to the directory where we will run the pipeline script
3 Uploaded the cleaned-up dataset to Cloud Storage
4 Created a Vertex AI-managed dataset from the cleaned-up dataset

In this section, we will implement the elements we prepared in the preceding section and use to create an ML pipeline that takes a preprocessed dataset at one end and produces a trained model deployed with a Vertex AI endpoint at the other end.

# 11.3.1 Local implementation vs. with ML pipeline

Before we define with the ML pipeline, let's contrast the ML pipeline with the local setup to train the Kuala Lumpur real estate prediction model that we implemented in chapter 10. Figure 11.28 shows this contrast and highlights some of the differences between the two implementations.