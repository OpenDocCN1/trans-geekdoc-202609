
# Chapter Summary

In this chapter, we learnt about pipelines, what Kubeflow is and its components. We covered how to construct a pipeline using the Kubeflow SDK and using the AutoML component of GCP for model training. We also covered how to submit the pipeline for a run and visually understand the pipeline and check the results.

In the next chapter, we will construct the pipeline using the Kubeflow SDK for custom model training.

## Questions

1.  Pipelines built on what can be executed on Vertex AI?
2.  Why in the code is the base image information mentioned only in the custom model evaluation function?
3.  Why do we need to compile the pipeline before submitting it?
4.  Will all the components be executed from the beginning if the pipeline gets executed after troubleshooting of errors?

## Join our book's Discord space

Join the book's Discord Workspace for latest updates, offers, tech happenings around the world, new releases, and sessions with the authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![Discord](images/fm1.png)

# CHAPTER 7: Pipelines using Kubeflow for Custom Models

## Introduction

In the previous chapter, we worked on the pipelines of GCP using Kubeflow. We built the first pipeline using AutoML of the platform for model training. In this chapter, we will see how to build pipelines for custom models and compare the results of different pipelines. We will also understand a few differences between Vertex AI pipelines and Kubeflow pipelines.

## Structure

In this chapter, we will cover the following topics:

*   Data for model training
*   Additional permissions
*   Creation of workbench using cloud shell
*   Pipeline code walk through
*   Pipeline
*   Pipeline comparison
*   Deletion of resources

## Objectives

By the end of this chapter, users will be able to build pipelines using Kubeflow for custom model building and compare the results of different pipelines.

## Data for model training

For this exercise, data is downloaded from Kaggle (link provided below), and the dataset is listed under CC0: Public Domain licenses. In previous chapters we have used Cloud Storage to upload the data to train the model; in this chapter, data is being uploaded to BigQuery of GCP on which the machine learning model is trained.

[https://www.kaggle.com/datasets/arashnic/hr-ana](https://www.kaggle.com/datasets/arashnic/hr-ana)

Refer to the BigQuery section from [Chapter 1](#ch01.xhtml), *Basics of Google Cloud Platform* to upload the data. [Figure 1.43](#ch01.xhtml#fig1-43) to [1.47](#ch01.xhtml#fig1-47) will help you upload the data to BigQuery. Refer to [Figure 1.48](#ch01.xhtml#fig1-48) to run a small query to check if the data upload is successful.

To upload data to BigQuery, create a dataset by the name `employee_data`. Under the dataset, create a table called `employee_promotion_data`. In the query section, use the query `select * from 'vertex-ai-gcp-1.employee_data.employee_promotion_data' limit 10` to check the data upload. [Figure 7.1](#ch07.xhtml#fig7-1) shows data that is uploaded to BigQuery:

![Figure 7.1: Data loaded into BigQuery table](images/Figure_7.1.png)

In this chapter we will create a pipeline on the Vertex AI component of GCP using the Kubeflow SDK. In the pipeline we will use the AutoML component of GCP for model training.

## Additional permissions

We also need to grant additional permissions to the service account associated with the Compute Engine of GCP since we are fetching data from BigQuery. Follow these steps to grant the required permissions.

### Step 1: Open IAM and admin section

Follow the steps mentioned in [Figure 7.2](#ch07.xhtml#fig7-2) to add roles to the service account associated with Compute Engine of GCP:

![Figure 7.2: IAM of GCP](images/Figure_7.2.png)

1.  Click **IAM**.
2.  Choose the service account associated with the project.
3.  Click **Edit Principal**.

### Step 2: Additional role

Follow the steps mentioned in [Figure 7.3](#ch07.xhtml#fig7-3), [7.4](#ch07.xhtml#fig7-4) and [7.5](#ch07.xhtml#fig7-5) to edit the roles of the service account of Compute Engine:

![Figure 7.3: Edit roles of service account](images/Figure_7.3.png)

1.  Click **+ Add Another Role** and follow the steps mentioned in [Figure 7.4](#ch07.xhtml#fig7-4):

    ![Figure 7.4: Adding BigQuery admin role](images/Figure_7.4.png)

2.  Select **BigQuery Admin** role under the BigQuery product/service.
3.  Click **SAVE**. A new role will be added to the service account as shown in the following figure:

    ![Figure 7.5: New role added to service account is visible in the IAM](images/Figure_7.5.png)

4.  New role will be visible for the service account associated with the Compute Engine.

## Creation of Workbench

In all the previous chapters we have worked on the workbench. Vertex AI Workbench and custom model training guides on creating a workbench using the GUI approach. Follow these steps to create a Vertex AI workbench from the Cloud Shell:

### Step 1: Activate Cloud Shell

Follow the steps shown in [Figure 7.6](#ch07.xhtml#fig7-6) to activate the Cloud Shell and type the following commands:

![Figure 7.6: Activate Cloud Shell](images/Figure_7.6.png)

1.  Click **Cloud Shell** to activate it.
2.  Type in the following commands in the Cloud Shell to create the workbench:

```
gcloud notebooks instances create kubeflow-custom-ml \
  --vm-image-project=deeplearning-platform-release \
  --vm-image-family=common-cpu-notebooks \
  --machine-type=n1-standard-4 \
  --location=us-central1-a
```

### Step 2: Created workbench

The created workbench will be listed under the workbench section of Vertex AI as shown in [Figure 7.7](#ch07.xhtml#fig7-7):

![Figure 7.7: Workbench creation complete](images/Figure_7.7.png)

1.  Newly created workbench.
2.  Click on **OPEN JUPYTERLAB**.

## Pipeline code walk through

We will be using a Python 3 notebook file to type commands, create a pipeline, compile and run it. Follow the steps mentioned below to create a Python file and type the Python codes given in this section.

### Step 1: Create Python notebook file

Once the workbench is created, open JupyterLab and follow the steps mentioned in [Figure 7.8](#ch07.xhtml#fig7-8) to create a Python notebook file:

![Figure 7.8: New launcher window](images/Figure_7.8.png)

1.  Click **New Launcher**.
2.  Double-click the **Python 3** notebook file to create one.

Step 2 onwards, run the given codes in separate cells.

### Step 2: Package installation

Run the following commands to install the Kubeflow, Google Cloud Pipeline, and Google Cloud AI Platform packages. (It will take a few minutes to install the packages):

```
USER_FLAG = "--user"

!pip3 install {USER_FLAG} google-cloud-aiplatform==1.3.0 --upgrade
!pip3 install {USER_FLAG} kfp --upgrade
!pip install google_cloud_pipeline_components
```

### Step 3: Kernel restart

Type the following commands in the next cell to restart the kernel. (Users can restart the kernel from the GUI as well):

```
import os

if not os.getenv("IS_TESTING"):
    import IPython
    app = IPython.Application.instance()
    app.kernel.do_shutdown(True)
```

### Step 4: Enabling APIs

Run the following lines of code to enable the APIs. We used to enable APIs from Cloud Shell. This is another way of enabling the APIs from the Python notebook (except Cloud Resource Manager, all other APIs are enabled in previous chapters):

```
!gcloud services enable compute.googleapis.com \
  containerregistry.googleapis.com \
  aiplatform.googleapis.com \
  cloudbuild.googleapis.com \
  cloudfunctions.googleapis.com \
  cloudresourcemanager.googleapis.com
```

If all the APIs are enabled successfully, the success message will be printed as shown in [Figure 7.9](#ch07.xhtml#fig7-9):

![Figure 7.9: APIs enabled successfully](images/Figure_7.9.png)
