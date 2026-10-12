
Model is deployed on to the GCP endpoint. Users can get the predictions from the deployed model using python on local machine.

Install `google-cloud-aiplatform` python package through the following command:

```
pip install google-cloud-aiplatform
```

More information on the package can be obtained from the following link:

<https://pypi.org/project/google-cloud-aiplatform/>

## Python Code for predictions

```
# Install google-cloud-aiplatform

from google.cloud import aiplatform

from google.protobuf import json_format

from google.protobuf.struct_pb2 import Value

import os

def online_pred_tabular(project, model_id, instance_dict, location, api_endpoint):

    client_options = {"api_endpoint": api_endpoint}

    client = aiplatform.gapic.PredictionServiceClient(client_options=client_options)

    instance = json_format.ParseDict(instance_dict, Value())

    instances = [instance]

    parameters_dict = {}

    parameters = json_format.ParseDict(parameters_dict, Value())

    endpoint = client.endpoint_path(project=project, location=location, endpoint_id=model_id)

    response = client.predict(endpoint=endpoint, instances=instances, parameters=parameters)

    predictions = response.predictions

    for prediction in predictions:
        print(" prediction:", dict(prediction))

# For GCP authentication. Provide full path of the json file

os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = ""

project_id = "vertex-ai-gcp"  # project_ID can be obtained from GCP dashboard (refer Figure 2.35)

model_id = "2047967950081622016"  # Model_ID refer Figure 2.29

location = "us-central1"  # Location refer to Figure 2.25

api_endpoint = "us-central1-aiplatform.googleapis.com"

# Inputs in Json format

inputs = {"BMI": "16.6", "Smoking": "Yes", "AlcoholDrinking": "No", "Stroke": "No", "PhysicalHealth": "3", "MentalHealth": "30", "DiffWalking": "No", "Sex": "Female", "AgeCategory": "55-59", "Race": "White", "Diabetic": "Yes", "PhysicalActivity": "Yes", "GenHealth": "Very good", "SleepTime": "5", "Asthma": "Yes", "KidneyDisease": "No", "SkinCancer": "Yes"}

# Calling the function

online_pred_tabular(project_id, model_id, inputs, location, api_endpoint)
```

## Output of the python code

The output of the python code can be seen in Figure 2.36:

![](images/Figure_2.36.png)

Figure 2.36: Python code output

Output contains probability scores for each of the classes.

Note: There are multiple ways of authentication, method used in the code is the simplest.

`Project_ID` can be obtained from the dashboard of the GCP (landing page of the platform) as seen in the following screenshot:

![](images/Figure_2.37.png)

Figure 2.37: Project_ID from dashboard

## Model un-deployment and deleting end point

Endpoint cannot be deleted until the all the models are removed from deployment.

### Step 1: Selecting the endpoint

Deployed model will be listed under endpoints as shown the Figure 2.38:

![](images/Figure_2.38.png)

Figure 2.38: Endpoint where model is deployed

1.  Navigate to endpoints.
2.  Click on the endpoint that needs to be deleted.

### Step 2: Removing model from deployment

![](images/Figure_2.39.png)

Figure 2.39: Removing model from deployment

1.  Select the model for removing and click on un-deploy model from endpoint.
2.  A Popup will ask for confirmation.

### Step 3: Endpoint deletion

![](images/Figure_2.40.png)

Figure 2.40: Endpoint deletion

1.  Select the endpoint to be deleted and click Remove endpoint.

Note: Deploying model is cost incurring, ensure to delete the model from deployment.

## Model deletion

In the entire process of working on the AutoML with tabular data we have created dataset and models.

Please follow steps mentioned in Figure 2.41 to delete the trained model:

![](images/Figure_2.41.png)

Figure 2.41: Deletion of trained model

1.  Navigate to models.
2.  Select the trained model for deletion.

## Dataset deletion

Please follow steps described in Figure 2.42 to delete the dataset created:

![](images/Figure_2.42.png)

Figure 2.42: Dataset deletion

1.  Navigate to datasets.
2.  Select the dataset and click on Delete dataset.

Note: batch predictions output are stored in the cloud storage, delete those files to complete clean up activity.

## Conclusion

In this chapter we learnt about Vertex AI and key their features. We worked on the AutoML tabular, created dataset, trained the model and put it for deployment for predictions. In the next chapter we will work on AutoML for images and text data.

## Questions

1.  Can user train AutoML model without creating managed datasets?
2.  Can multiple models be put into same endpoint for deployment?
3.  Why is service account needed for getting online predictions?
4.  What are the different tasks AutoML can handle for the tabular data?

## Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

<https://discord.bpbonline.com>

![](images/fm1.png)

# CHAPTER 3 AutoML Image, Text, and Pre-built Models

## Introduction

In the last chapter, we started working on AutoML for tabular data. This chapter continues with the AutoML section for images and text data, followed by step-by-step instructions for images and text data. GCP also provides pre-built models, and this chapter covers them in brief. This chapter also talks about the benefits and limitations of AutoML, in brief.

## Structure

In this chapter, we will discuss the following topics:

*   Vertex AI AutoML for image data
*   Image dataset creation
*   Image model training
*   Image model evaluation
*   Batch prediction for image
*   Model deployment for online predictions for image
*   Serving online predictions image
*   Vertex AI AutoML for text data
*   Text dataset creation
*   Text model training
*   Text model evaluation
*   Batch prediction for text
*   Model deployment for online predictions for text
*   Serving online predictions text
*   Pre-built models in GCP
*   Benefits of AutoML
*   Limitations of AutoML

## Objectives

By the end of this chapter, you will be able to create datasets, train the AutoML model, obtain batch predictions, and deploy the models for online predictions for images and text data. Also, get introduced to pre-built models of GCP.

## Vertex AI AutoML for image data

AutoML for images can handle tasks of single-label, multi-label classification, object detection, and image segmentation. For the practical exercise of the AutoML for image single-label classification we are using boat classification image data which can be downloaded from below mentioned link:

<https://www.kaggle.com/datasets/imsparsh/dockship-boat-type-classification>

The dataset is listed under CC0: Public domain license and contains images belonging to nine categories. For our exercise, we are considering images belonging to cruise ships, ferry boats, and kayaks (50 images are chosen randomly from each category).

`AutoML_image_data` bucket is created under `us-centra1` (single region) and three folders containing images belonging to three categories are uploaded. An additional folder is created in the bucket by the name `Data_for_batch_pred` which contains a randomly chosen image for batch prediction. A snapshot of the cloud storage is shown in Figure 3.1:

![](images/Figure_3.1.png)

Figure 3.1: Image data uploaded to cloud storage
