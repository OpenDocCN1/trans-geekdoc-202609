
## 5. Batch Predictions

Since we have chosen cloud storage, select the file from the bucket.

## 6. Output Format

Select the Output format. Outputs can be directly dumped into a BigQuery table or stored in cloud storage in `csv`/`jsonl`/`TFrecord` format.

## 7. Output Location

Provide the output location.

## 8. Create

Click on **Create**.

Batch predictions may take a few minutes to a few hours depending on the number of records. Importantly, users do not need to deploy the model for batch predictions.

## Step 2: Output of Batch Predictions

After batch predictions, output will be stored to cloud storage as shown in [Figure 2.23](#ch02.xhtml#fig2-23):

![](images/Figure_2.23.png)

**Figure 2.23: Batch prediction output**

One CSV file will be created for each record (`prediction_results.csv`). `Prediction.csv` contains the information of the input record along with the probability of scores for different classes. `Error_stats.csv` will provide information for the users if any errors are encountered during the prediction.

## Model Deployment for Online Predictions

The model package, which we will bundle into a Docker image to deploy, comprises all the parts required to execute a model, including the run environment, ML framework, stored model file, and supported backend microservice. On the other hand, the endpoint is the place where the computer resources are located where your model is really processing prediction queries. For auto-scaling, users may choose the machine type and other factors.

The model must be deployed on an Endpoint before predictions based on it may be accepted. Follow the steps below to deploy the model.

### Step 1: Model Deployment

Model deployment can be initiated under **Deploy and Test** as shown in [Figure 2.24](#ch02.xhtml#fig2-24):

![](images/Figure_2.24.png)

**Figure 2.24: Model deployment**

1.  Go to **Deploy and Test** tab.
2.  Select **Deploy to endpoint**.

### Step 2: Endpoint Definition

The steps involved in Endpoint definition can be seen in [Figure 2.25](#ch02.xhtml#fig2-25):

![](images/Figure_2.25.png)

**Figure 2.25: Endpoint creation**

1.  Select **CREATE NEW ENDPOINT**. If the model needs to be deployed to an existing endpoint, users are provided with an option of **Add to existing endpoints**.
2.  Provide the name for the endpoint.
3.  Access can be standard unless it is for private access.
4.  Click on **Continue**.

### Step 3: Model Settings

Traffic split and hardware needed for prediction can be chosen as shown in [Figure 2.26](#ch02.xhtml#fig2-26):

![](images/Figure_2.26.png)

**Figure 2.26: Model settings for deployment**

1.  If the model is deployed in multiple endpoints, traffic split can be done between them. If the model is deployed in only one endpoint then it has to be set to 100%.
2.  Number of nodes required for prediction.
3.  Select the machine type (if the model is very complicated then it is recommended to select machines with good configuration).

Scroll down to choose the options of logging and click **Continue**.

### Step 4: Model Monitoring

Follow the steps below as shown in [Figure 2.27](#ch02.xhtml#fig2-27) to enable model monitoring in production:

![](images/Figure_2.27.png)

**Figure 2.27: Model monitoring**

1.  Users can enable model monitoring for the deployed model (the model can be deployed without enabling the monitoring).
2.  Provide a name for the monitoring job.
3.  Monitoring will be done by multiple jobs. The time length of the job needs to be provided. If the expected load is high then a low number is recommended and vice versa.
4.  Mail ID for the alerts.
5.  Percentage of requests can be chosen within a monitoring window for sampling.

Input schema is optional for AutoML models and can be ignored. Scroll down and click **Continue**.

### Step 5: Monitoring Objectives

Model performance deteriorates over time. Follow the steps shown in [Figure 2.28](#ch02.xhtml#fig2-28) to choose the model monitoring objectives:

![](images/Figure_2.28.png)

**Figure 2.28: Monitoring objective**

1.  Prediction requests are logged in a BigQuery table in the same project. The input feature values contained in the logged requests are then analyzed for skew or drift (it requires training data for the comparison).
2.  Model monitoring tracks changes in a feature's contributions to a model's predictions over time (no training data is required).
3.  Since we have chosen skew detection, the user needs to provide the training data options.
4.  Choose the dataset which is used for training the AutoML model.
5.  Provide the target column name.
6.  Click **DEPLOY**.

It will take a few minutes to deploy the model to the endpoints.

### Step 6: Testing Deployed Model

Follow the steps shown in [Figure 2.29](#ch02.xhtml#fig2-29) to test the deployed model on the platform before proceeding for online predictions:

![](images/Figure_2.29.png)

**Figure 2.29: Online prediction testing**

1.  Model is deployed successfully.
2.  ID is the model ID that is deployed. (One endpoint can deploy multiple models). The same ID is used for online predictions.
3.  Even before users get the online predictions, users can test the model output on the platform by populating column values and clicking on **predict** at the bottom of the screen.
4.  Output prediction will be populated with the probability scores.

## Service Account Creation

The deployed model is ready to serve requests for predictions. While sending data and model details for predictions, users should also be authenticated. In these scenarios, user GCP account details cannot be used for authentication; a service account is needed. Follow the steps below for service account creation. Open **IAM and admin** and follow steps as shown in [Figure 2.30](#ch02.xhtml#fig2-30):

### Step 1: Service Account Creation

![](images/Figure_2.30.png)

**Figure 2.30: Service account**

1.  Select **Service accounts** under **IAM and admin** section.
2.  Click on **Create service account**.

### Step 2: Service Account Details

Follow steps shown in [Figure 2.31](#ch02.xhtml#fig2-31) to add account details:

![](images/Figure_2.31.png)

**Figure 2.31: Service account details**

1.  Provide a name for the service account.
2.  Provide a service account ID.
3.  Provide a description for the service account.
4.  Click on **Create and continue**.

Changing the access to the service account is not required for this exercise.

### Step 3: Assigning Roles for the Service Account

During the process of service account creation, let us also grant access to certain roles needed for this service account. Granting these roles is important since we will use the same service account for custom model building, pipelines, and so on. Follow steps shown in [Figure 2.32](#ch02.xhtml#fig2-32) to grant roles. (It is an optional step and can be done as and when needed as well).

![](images/Figure_2.32.png)

**Figure 2.32: Grant AI platform access to service account**

1.  Click on **Select a role**.
2.  Select **AI Platform** under actions.
3.  Select **AI Platform Admin**.

Similarly, add a few other roles belonging to Cloud Storage and Vertex AI as displayed in [Figure 2.33](#ch02.xhtml#fig2-33):

![](images/Figure_2.33.png)

**Figure 2.33: Grant other access to service account**

### Step 4: Service Account Manage Keys

Once the service account is created, users need to create keys. Follow steps shown in [Figure 2.34](#ch02.xhtml#fig2-34) and [Figure 2.35](#ch02.xhtml#fig2-35) to create keys:

![](images/Figure_2.34.png)

**Figure 2.34: Service account manage keys**

1.  Service account is now created.
2.  Click on the actions of the created service account and click on **Manage keys**.

### Step 5: Service Account Add Keys

![](images/Figure_2.35.png)

**Figure 2.35: Service account key creation**

1.  Click on **ADD KEY** and choose **Create new key**.

A pop-up will provide options to create a key in `json`/`P12` format. Choose `json` format and a `.json` file will be downloaded.

> **Note:** Users need to provide the full path of the `json` file for authentication in the Python code. We can use the same key for the next chapter also.

## Serving Online Predictions
