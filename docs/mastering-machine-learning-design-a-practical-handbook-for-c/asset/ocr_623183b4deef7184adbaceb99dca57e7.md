```
EndpointConfigName=endpoint_config_name,
ModelImageUrl=model_image,
)
# Create an endpoint
endpoint_name = "my-endpoint"
sagemaker_client.create_endpoint(
    EndpointName=endpoint_name,
    EndpointConfigName=endpoint_config_name,
)
```

# 2. Google AI Platform:

+   - **AI Platform Pipelines:** A service for building and deploying machine learning pipelines, including model training, deployment, and monitoring.
+   - **AI Platform Prediction:** Allows deploying models as web services for real-time predictions. You can configure them to accept specific input formats and return predictions.

# Code Example (using Google Cloud Python Client Library):

Python

```
# Import libraries
from googleapiclient import discovery
# Create a prediction service object
service = discovery.build("ml","v1")
# Define project ID and model name
project_id = "your-project-id"
model_name = "projects/{}/models/{}".format(project_id,"your-model-name")
# Deploy the model for online prediction
```