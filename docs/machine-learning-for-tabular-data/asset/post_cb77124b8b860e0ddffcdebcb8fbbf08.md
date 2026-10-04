
On the Model settings tab of the Import model page, follow these steps:

- 1. In Model Framework, select TensorFlow. Recall from chapter 8 TensorFlow is the low-level framework for Keras, the framework we used to train the model.

- 2. In Model Framework Version, select the TensorFlow level used to train the model. You can find this from the output of tf.__version__ in the notebook used to train the model:

```
tf.__version__
2.9.2
```

- 3. In Model Artifact Location, click Browse and select the folder where you uploaded the model.

- 4. Click Continue and Import, as shown in figure 10.23.

## Import model

- Name and region
- Model settings
- Explainability (optional)

![](img/def89cc476fa39f4c54bd34e78d91674_402_0.png)

Import model artifacts into a pre-built container
View the list of supported runtimes including TensorFlow, scikit-learn and XGBoost

Import an existing custom container
Build a custom container. Must be stored in Container Registry or Artifact Registry

## Pre-built container settings

Figure 10.23 Selecting model settings

The model import process may take several minutes to complete. When the import is complete, you will see the new model name on the Model Registry page, as shown in figure 10.24.

## Deploying a model in Vertex AI

## Model Registry

Models are built from your datasets or unmanaged data sources. There are many different types of machine learning models available on Vertex AI, depending on your case and level of experience with machine learning. Learn more

Region
us-central1 (iowa)

| Name | Deployment status | Description | Default version | Type | Source |
|---|---|---|---|---|---|
| first-model-ml-tabular | | | 1 | Imported | Custom training |

**Figure 10.24** Model Registry showing the imported model

Congratulations! You have imported a model into Vertex AI. In the next section, we will go through the steps to make this model available through an endpoint.

## 10.4.3 Deploying the model to an endpoint

Now that we have imported the trained model into Vertex AI, we can deploy it to an endpoint. By deploying the model to an endpoint, we get a URL that we can use to invoke the model. In effect, the endpoint deployment can take the place of the model in the local file system that the Flask server served in the simple web deployment that we created earlier in this chapter.

To deploy the model to an endpoint, on the Model Registry page, select the model we created in the previous section. In the Model details page, select the version of the model (by default, 1), as shown in figure 10.25. In the version page for the model, click Deploy to Endpoint, as shown in figure 10.26. In the Deploy to Endpoint page, enter a name in Endpoint name and click Continue, as shown in figure 10.27.

![](img/def89cc476fa39f4c54bd34e78d91674_403_0.png)

Model description Region
- us-central1 (iowa)

| Version ID | Alias | Status | Description | Endpoints |
|---|---|---|---|---|
| 1 | default | Ready | | - |

**Figure 10.25** Model details page

## Deploy your model

Endpoints are machine learning models deployed for online prediction requests. Endpoints are useful for serving predictions to many users (for example, in response to an application request). You can also run batch predictions if you don't need immediate results.

```
DEPLOY TO ENDPOINT
```

| Name | ID | Status | Models | Region | Monitoring | Most recent monitoring job | Most recent alerts | Last updated |
|---|---|---|---|---|---|---|---|---|
| No active endpoints containing this model | | | | | | | | |

**Figure 10.26** Deploying your model

![](img/def89cc476fa39f4c54bd34e78d91674_404_0.png)

- Define your endpoint
- Model settings
- Model monitoring

**Figure 10.27** Deploying to endpoint page

In the Model Settings tab, under Advanced Scaling Options, select a minimal machine type, such as n1-standard-2, as shown in figure 10.28, and click Continue.

## Deploying a model in Vertex AI

## ADVANCED SCALING OPTIONS

| Machine type * | n1-standard-2, 2 vCPUs, 7.5 GB memory |

Figure 10.28 Setting the machine type for the deployment

Because this is a test deployment of a simple model, we only need a minimal machine type. If we were deploying a more demanding model, or making a production deployment, we could choose a machine type with more memory or compute resources, depending on the requirements of our model. A minimal machine type is good enough for our test deployment, and it will cost less than a more advanced machine type. When you are using a cloud environment, it's a best practice to use the resources that are sufficient for your application and not more. Doing this will save you money.

TIP For more details about machine types for Vertex AI endpoint deployment, see the documentation at https://mng.bz/vK14.

Click Deploy, as shown in Figure 10.29.

## Deploy to endpoint

- Define your endpoint
- Model settings
- Model monitoring

![](img/def89cc476fa39f4c54bd34e78d91674_405_0.png)

Deployment can take several minutes to complete. When deployment is complete, the status of the deployment on the Model version details page changes to Active, as shown in figure 10.30.

| Name | ID | Status | Region | Monitoring | Most recent monitoring job | Most recent alerts |
|---|---|---|---|---|---|---|---|
| first-model-tabular-endpoint | 389644930651258880 | Active | 1 | us-central1 | Disabled | -- | -- |

Figure 10.30 Confirmation that the model has been deployed

## 384 CHAPTER 10 Model deployment

Congratulations! You have completed the deployment of a model in Vertex AI. In the next section, we will go through the steps to quickly test the deployment.

## 10.4.4 Initial test of the deployment

Now that we have deployed the model, we can do an initial test of the model directly in the console. Recall the test we did in chapter 9, we defined a dictionary with all the features:

```
sample = {
  'location': 'Sentul, Lumpur',
  'rooms': 3.0,
  'property_type': 'Condominium For Sale',
  'furnishing': 'Partially Furnished',
  'size_type_bin': 'built-up 1',
  'bathrooms': 2.0,
  'car_parks': 0.0,
  'size': 950.0
}
```

We can use this sample to test the model in Vertex AI. In the Model details page, go to the Test section, as shown in figure 10.31.

## Test your model

Your JSON request must contain instances field and an optional parameters field if you're using a custom model. No other fields can be present.![](img/def89cc476fa39f4c54bd34e78d91674_406_0.png)

Figure 10.31 Test Your Model section of the Deploy and Test tab

## JSON request

```json
{
  "instances":[
    {
      "location": ["Sentul, Lumpur"],
      "rooms": [3.0],
      "property_type": ["Condominium For Sale"],
      "furnishing": ["Partly Furnished"],
      "size_type_bin": ["built-up 1"],
      "bathrooms": [2.0],
      "car_parks": [0.0],
      "size": [950.0]
    }
  ]
}
```

Figure 10.32 Test sample in JSON format

Note three differences between the format of the sample in the JSON request and the original sample from the chapter 9 Notebook:
- Values in the key-value pairs are all arrays rather than single values. You will get an error if you have single values.
- Double quotes ("") are used throughout rather than single quotes.
- There is no comma after the last key-value pair.

Once the JSON Request field contains valid JSON, the frame turns blue. Click Predict to see the output of the endpoint in the Response field, as shown in figure 10.33.

## Response

```json
{
  "predictions": [
    [
      -1.52191401
    ]
  ],
  "deployedModelId": "3381917447132020736",
  "model": "projects/102833200603/locations/us-central1/models/4355669133940",
  "modelDisplayName": "first-model-tabular",
  "modelVersionId": "1"
}
```

Figure 10.33 Response from the endpoint for the test sample
