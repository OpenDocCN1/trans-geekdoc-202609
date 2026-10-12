
# Newly Created Feature Store

1. Click on **Create Entity Type** for its creation.

## Step 5: Creation of Entity Type

Follow the steps shown in [Figure 9.7](#ch09.xhtml#fig9-7) to create an entity type:

![](images/Figure_9.7.png)

**Figure 9.7: Creation of entity type**

1. Select the **Region** under which the feature store is created.
2. All the feature stores under the region will be listed; select the newly created **Featurestore**.
3. Provide **Entity type name**.
4. Write the **Description** for the entity type.
5. **Feature monitoring** (enable if the features need to be monitored).
   1. It enables the monitoring of feature stores and features. Feature store monitors CPU utilization, storage, and latency. Feature monitoring helps in monitoring changes in feature value distribution.
6. Click **CREATE**.

## Step 6: Entity Type Created Successfully

The entity type is created successfully as shown in [Figure 9.8](#ch09.xhtml#fig9-8) under the selected feature store:

![](images/Figure_9.8.png)

**Figure 9.8: Entity type created and listed on the landing page**

1. Click the newly created **Entity type**.

## Step 7: Creation of Features

Once the entity type is created, features need to be created before ingesting the values. Follow the steps mentioned in [Figure 9.9](#ch09.xhtml#fig9-9) to create features:

![](images/Figure_9.9.png)

**Figure 9.9: Creation of features**

1. Click **ADD FEATURES**.
   A new side tab will pop out to enter the features as shown in [Figure 9.10](#ch09.xhtml#fig9-10); follow the below steps to create the features:

   ![](images/Figure_9.10.png)

   **Figure 9.10: Adding user input for feature creation**

2. Enter the **Feature name**.
3. Enter the **Value type** stored in that feature.
4. Enter the **Description** for the feature.
5. Click **Add Another Feature** to add new features.
6. Click **SAVE**, once all the features are added.

## Step 8: Features Created Successfully

Once the features are created successfully, they are displayed on the entity type page as shown in [Figure 9.11](#ch09.xhtml#fig9-11):

![](images/Figure_9.11.png)

**Figure 9.11: Features listed under the entity type**

1. Newly created features are displayed in tabular format.
2. Click on **Ingest Values** to add the feature values.

## Step 9: Ingesting Feature Values

Follow the steps mentioned in [Figure 9.12](#ch09.xhtml#fig9-12) to initiate the ingestion of feature values:

![](images/Figure_9.12.png)

**Figure 9.12: Importing data to features**

1. Data can be ingested from cloud storage or BigQuery. Select **Cloud Storage CSV file**.
2. Select the CSV file from the cloud storage by clicking **BROWSE**.
3. Click **CONTINUE** and follow the steps mentioned in [Figure 9.13](#ch09.xhtml#fig9-13):

After selecting the data source, we need to map the columns of the data source to the features. Follow the steps mentioned in [Figure 9.13](#ch09.xhtml#fig9-13) to map the features:

![](images/Figure_9.13.png)

**Figure 9.13: Mapping of columns to features**

1. Add **employee ID**, since that is the column which is containing unique values.
2. Select to enter the **Timestamp** manually. If data contains the timestamp values, the same column can be used here.
3. Select the date and time.
4. Map the column names in the CSV file to the features.
5. Click **INGEST** to initiate the ingestion job.

## Step 10: Ingestion Job Successful

Once the feature values are ingested successfully, the ingestion job status will be updated as shown in [Figure 9.14](#ch09.xhtml#fig9-14):

![](images/Figure_9.14.png)

**Figure 9.14: Ingestion jobs of feature store**

1. The ingestion job is completed successfully.

## Step 11: Landing Page of Feature Store After Creation

The landing page of the feature store is shown in [Figure 9.15](#ch09.xhtml#fig9-15); all the features under entity type and feature store are listed and displayed in tabular format:

![](images/Figure_9.15.png)

**Figure 9.15: Landing page of feature store after the creation of features**

1. Click the **age** feature. The window will navigate to the properties of the feature as shown in [Figure 9.16](#ch09.xhtml#fig9-16):

![](images/Figure_9.16.png)

**Figure 9.16: Properties of feature**

1. For all the features, **Feature Properties** consisting of basic information and statistics are displayed.
2. Metrics are populated if the monitoring feature is enabled for the feature store and for that particular feature.

# Working on Feature Store Using Python

In the previous section, we worked on a feature store for the creation and uploading of feature values using the GUI approach. In this section, we shall create another feature store, ingest values, and also fetch the values from the feature store.

We will be using the Python 3 notebook file to type commands for working on the feature store. Follow the following-mentioned steps to create a Python file and type the Python codes given in this section.

## Step 1: Create a Python Notebook File

Once the workbench is created, open JupyterLab and follow the steps mentioned in [Figure 9.17](#ch09.xhtml#fig9-17) to create a Python notebook file:

![](images/Figure_9.17.png)

**Figure 9.17: New launcher window of notebook**

1. Click the new launcher.
2. Double-click the **Python 3** notebook file to create one.

## Step 2: Package Installation

Run the following commands to install the google cloud AI platform package. (It will take a few minutes to install the packages):

```bash
USER="--user"
!pip install {USER} google-cloud-aiplatform
```

## Step 3: Kernel Restart

Type the following commands in the next cell to restart the kernel (users can restart the kernel from the GUI as well):

```python
import os
import IPython

if not os.getenv(""):
    IPython.Application.instance().kernel.do_shutdown(True)
```

## Step 4: Importing the Installed Packages

Run the following-mentioned codes in a new cell to import the required packages:

```python
import google.cloud.aiplatform_v1
from google.cloud.aiplatform_v1.types import featurestore_service as fs_s
from google.cloud.aiplatform_v1.types import featurestore as fs
from google.cloud.aiplatform_v1.types import feature
from google.cloud.aiplatform_v1.types import entity_type
from google.cloud.aiplatform_v1.types import io
from google.protobuf.timestamp_pb2 import Timestamp
from google.cloud.aiplatform_v1.types.featurestore_service import ImportFeatureValuesRequest
from google.cloud.aiplatform_v1.types import FeatureSelector, IdMatcher
from google.cloud.aiplatform_v1.types import featurestore_online_service
import datetime
```

## Step 5: Setting Up the Project and Other Variables

Run the following-mentioned line of codes in a new cell to set the project to the current one and also define variables to store the path for multiple purposes:

```python
Project_id = "vertex-ai-gcp-1"
featurestore_name = "employee_fs_pysdk"
Entity_name = "emp_entity_pysdk"
location = "us-central1"
endpoint = "us-central1-aiplatform.googleapis.com"
```

## Step 6: Connecting to the Feature Store

Connection to the feature store is the first step to work on the feature store. We create a connection to the feature store through the service client to create and ingest values to it using `FeaturestoreServiceClient`.

`FeaturestoreOnlineServingServiceClient` is used to fetch the feature values from the feature store. Run the below-mentioned line of codes to complete the connection:

```python
client_admin = google.cloud.aiplatform_v1.FeaturestoreServiceClient(client_options={"api_endpoint": endpoint})
client_data = google.cloud.aiplatform_v1.FeaturestoreOnlineServingServiceClient(client_options={"api_endpoint": endpoint})
fs_resource_path = client_admin.common_location_path(Project_id, location)
```

## Step 7: Creation of Feature Store
