
# Build what's next. Better Faster.

**Figure 10.6** Entering the Google Cloud console

![](img/def89cc476fa39f4c54bd34e78d91674_395_0.png)

**Figure 10.7** Google Cloud console

The console is the user interface for Google Cloud. This is one of the interface choices for working with Google Cloud features, and it is what we will use for most of the actions we will take in Google Cloud in this chapter. In addition to the Cloud console, you can interact with Google Cloud features using

- Command-line interface
- Client libraries

NOTE See https://cloud.google.com/docs/overview for more details on the interfaces for Google Cloud.

## 10.3.2 Creating a Google Cloud project

You can create a project once you have successfully logged into Google Cloud and accessed the Google Cloud Console. In this section, we will go through the steps to create a project.

In the Google Cloud console, click the Project Selection field, as shown in figure 10.8. In the Select Project screen, select New Project, as shown in figure 10.9. Then, enter `first-project-ml-tabular` in the Project Name field and click on Create, as shown in figure 10.10.

![](img/def89cc476fa39f4c54bd34e78d91674_396_0.png)

Selecting a project

![](img/def89cc476fa39f4c54bd34e78d91674_396_1.png)

Figure 10.9 Selecting a project

![](img/def89cc476fa39f4c54bd34e78d91674_396_2.png)

Congratulations! You have created your first Google Cloud project.
Note that the project name needs to be unique for your set of projects. The project ID, which appears below the Project Name field, must be universally unique, so if you

Figure 10.10 Entering a project name

# Getting started with Google Cloud

have a project name that is shared with any other project in Google Cloud, the project ID for that project will be automatically updated to unique.

## 10.3.3 Creating a Cloud Storage bucket

The primary way to store data in Google Cloud is to use Cloud Storage buckets. In this section, we will go through what you need to know about Cloud Storage buckets for the purposes of deploying a model. If you are interested in more details on Cloud Storage buckets, see the documentation: https://cloud.google.com/storage/docs/buckets. We will be using a bucket to store the model we trained in chapter 9. To create a Cloud Storage bucket, enter “cloud storage” in the search bar in the Google Console and select Cloud Storage, as shown in figure 10.11.

![](img/def89cc476fa39f4c54bd34e78d91674_397_0.png)

Figure 10.11 Searching for Cloud Storage

The Cloud Storage Buckets page appears. Select Create to create a new Cloud Storage bucket, as shown in figure 10.12.

![](img/def89cc476fa39f4c54bd34e78d91674_397_1.png)

Figure 10.12 Cloud Storage bucket

In a bucket page, enter a unique name for your bucket (figure 10.13), click Continue, and select Region in Location Type, and select a region, as shown in figure 10.14. To work with the machine learning pipeline script we will explore in chapter 11, the bucket needs to be created in a region. For the purposes of this example, you can pick any region you like. Click Create. Note that your bucket name has to be universally unique.

## Name your bucket

Pick a globally unique, permanent name. Naming guidelines:

- Multi-region: Highest availability across largest area
- Dual-region: High availability and low latency across 2 regions
- Region: Lowest latency within a single region

Tip: Don't include any sensitive information

The Bucket details page appears, showing your new bucket, as shown in figure 10.15.

| first-project-tabular-bucket | Location | Storage class | Public access | Protection |
| :--- | :--- | :--- | :--- | :--- |
| us (multiple regions) | Standard | Not public | None |
| OBJECTS | CONFIGURATION | PERMISSIONS | LIFECYCLE | OBSERVABILITY |

Congratulations! You have created your first Cloud Storage bucket.

## 10.4 Deploying a model in Vertex AI

Earlier in this chapter, we deployed a real estate prediction model using a Flask-based web application. In this section, we are going to deploy the model using Google Vertex AI environment. Now that we have created a project in Google Cloud and created a Cloud Storage bucket in our new project, we are ready to deploy a model in Google Cloud. The following are the steps we will follow for this deployment (described in more detail in the Vertex AI documentation):

1. Upload the model we trained in chapter 9 to Cloud storage.
2. Import the model to Vertex AI Model Registry.

### 10.4 Uploading the model to a Cloud Storage bucket

The simplest way to get your trained model into Cloud Storage is to upload a folder containing the trained model. If you want to upload a version of the model that has already been trained, clone the repo https://github.com/googlecloudplatform/vertex-ai-docs. The directory you want to upload is `models/real_estate_keras_preprocessing_model`. To upload your model from chapter 9, select the bucket you created in the Cloud Storage page, as shown in figure 10.16. In the Bucket Details page, select Upload Folder, as shown in figure 10.17.

![](img/def89cc476fa39f4c54bd34e78d91674_399_0.png)

Figure 10.16 Selecting your bucket in the Cloud Storage page

| first-project-tabular-bucket | Location | Storage class | Public access | Protection |
| :--- | :--- | :--- | :--- | :--- |
| us (multiple regions) | Standard | Not public | None |
| OBJECTS | CONFIGURATION | PERMISSIONS |

Select the folder from your local system to contain the trained model from chapter 9. When the upload is complete, the folder will appear on the Bucket details page, as shown in figure 10.18.

img/def89cc476fa39f4c54bd34e78d91674_399_1.png

Figure 10.18 Your uploaded bucket in the Bucket details page

| first-project-tabular-bucket | Location | Storage class | Public access | Protection |
| :--- | :--- | :--- | :--- | :--- |
| us (multiple regions) | Standard | Not public | None |
| OBJECTS | CONFIGURATION | PERMISSIONS |
| UPLOAD FILES | UPLOAD FOLDER | CREATE FOLDER | TRANSFER DATA |
| Name | Size | Type | Created |
| :--- | :--- | :--- | :--- |
| real_estate_keras_preprocessing_model | | Folder | |

Congratulations! You have uploaded your model to Google Cloud.

## 10.4.2 Importing the model to Vertex AI

Now that we have uploaded the model to a Cloud Storage bucket, we can import it to the Vertex AI Model Registry. Enter "vertex ai" in the Google Cloud console search bar to get to the Vertex AI page. If this is the first time you have used Vertex AI, you will see All Recommended APIs. If you see this button, click on it to enable the APIs that are required to use Vertex AI, as shown in figure 10.19.

![](img/def89cc476fa39f4c54bd34e78d91674_400_0.png)

Figure 10.19 Enabling Vertex AI APIs

### Deploying a model in Vertex AI

Then select Model Registry in the left navigation panel, as shown in 10.20, and on the Model Registry page, click Import, as shown in 10.21.

![](img/def89cc476fa39f4c54bd34e78d91674_401_0.png)

Figure 10.20 Model Registry in the Vertex AI page navigation panel

In the Import model page, select Import as New Model, enter “first-model-ml-tabular” in the Name field, and click Continue, as shown in 10.22.

## Import model

- Name and region
- Model settings
- Explainability (optional)

![](img/def89cc476fa39f4c54bd34e78d91674_401_1.png)

Figure 10.22 Specifying the name of the imported model in Model Registry
