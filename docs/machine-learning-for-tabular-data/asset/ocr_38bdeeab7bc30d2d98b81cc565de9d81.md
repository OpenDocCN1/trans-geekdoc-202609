# Getting started with Google Cloud

have a project name that is shared with any other project in Google Cloud, the project ID for that project will be automatically updated to unique.

# 10.3.3 Creating a Google Cloud Storage bucket

The primary way to store data in Google Cloud is to use Cloud Storage buckets. In this section, we will go through what you need to know about Cloud Storage buckets for the purposes of deploying a model. If you are interested in more details on Cloud Storage buckets, see the documentation: https://cloud.google.com/storage/docs/buckets. We will be using a bucket to store the model we trained in chapter 9. To create a Cloud Storage bucket, enter “cloud storage” in the search bar in the Google Console and select Cloud Storage, as shown in figure 10.11.

![](bbox=[0.186, 0.313, 0.89, 0.447])

Figure 10.11 Searching for Cloud Storage

The Cloud Storage Buckets page appears. Select Create to create a new Cloud Storage bucket, as shown in figure 10.12.

![](bbox=[0.186, 0.591, 0.89, 0.725])

Figure 10.12 Cloud Storage bucket view

In a bucket page, enter a unique name for your bucket (figure 10.13), click Continue, and select Region in Location Type, and select a region, as shown in figure 10.14. To work with the machine learning pipeline script that we will explore in chapter 11, the bucket needs to be created in a region. For the purposes of this example, you can pick any region that you like. Click Create. Note that your bucket name has to be universally unique.