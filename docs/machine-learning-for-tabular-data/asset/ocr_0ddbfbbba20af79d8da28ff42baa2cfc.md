# Defining the ML pipeline

+   - The pipeline script is a new component in the ML pipeline. This script sets up the input necessary for the model training script, uses the Vertex AI SDK to create a container for the model training script, and invokes the script to do the training.

+   - The pipeline config file is a new component in the ML pipeline. This config file contains parameters for the pipeline script, including the built-in Vertex AI containers; the proportion of the cleaned-dataset for each of the training, validation, and testing sets; the dataset ID; and the location of the code for the training script.

+   - The trained model is automatically put in the model registry in the ML pipeline implementation and deployed to a Vertex AI endpoint. In the local system, we manually uploaded the model to Cloud Storage and deployed it to an endpoint.

The endpoint that is result of both the local system implementation and the ML pipeline implementation can be plugged into our web deployment by updating the `endpoint_id` parameter in the Flask server config, as shown in figure 11.29.

![](bbox=[0.19, 0.452, 0.809, 0.873])

Figure 11.29 Web deployment with endpoint from local or ML pipeline