# Deploying a model in Vertex AI

+   1 Upload the model we trained in chapter 9 to Google Cloud storage.
2 Import the model to the Vertex AI Model Registry.

The following sections describe each of these steps.

# 10.4.1 Uploading the model to a Cloud Storage bucket

The simplest way to get your trained model into Google Cloud Storage is to upload a folder containing the trained model. If you want to upload a version of the model that has already been trained, clone the repo https://github.com/lmassaron/Advanced_Analytics_for_Business. The directory you want to upload is chapter_10/models/kl_real_estimate_keras_preprocessing_model.

To upload your model from chapter 9, select the Cloud Bucket you created in the Cloud Storage page, as shown in figure 10.16. In the Bucket Details page, select Upload Folder, as shown in figure 10.17.

![](bbox=[0.19, 0.385, 0.809, 0.483])

Figure 10.16 Selecting your bucket in the Cloud Storage page

Bucket details

# first-project-mi-tabular-bucket

| Location Storage class Public access Protection |
| us (multiple regions in United States) Standard Not public None |

| OBJECTS CONFIGURATION PERMISSIONS PROTECTION

+   Buckets first-project-mi-tabular-bucket
UPLOAD FILES UPLOAD FOLDER CREATE FOLDER TRANSFER DATA

Filter by name prefix only Filter objects and folders

| Name Size Type Created? Storage class Last modified |

No rows to display

![](bbox=[0.626, 0.758, 0.746, 0.825])

Select the folder from your local system to contain the trained model from chapter 9. When the upload is complete, the folder will appear on the Bucket details page, as shown in figure 10.18.