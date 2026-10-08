Seldon Core provides packaged model servers for some of the ML libraries, including the SKLearn server for scikit-learn models, the XGBoost models, TensorFlow Serving for TensorFlow models, and MLflow server-based model serving. You can also build your own custom serving container for specific model serving needs and host it using Seldon Core.

The following template shows how to deploy a model using the SKLearn server using Seldon Core. You simply need to change the modelUri path to point to a saved model on a cloud object storage provider such as Google Cloud Storage, Amazon S3 storage, or Azure Blob storage. To test with an example, you can change the following modelUri value to an example provided by Seldon Core - gs://seldon-models/sklearn/iris:

```
apiVersion: machinelearning.seldon.io/v1alpha
kind: SeldonDeployment
metadata:
  name: sklearn
spec:
  name: sklearn-model
  predictors:
    - graph:
      children: []
        implementation: SKLEARN SERVER
        modelUri: <uri to model artifacts on the cloud storage>
  name: classifier
  name: default
  replicas: 1
```

Seldon Core also supports an advanced workflow (also known as an inference graph) for serving models. The inference graph feature allows you to have a graph with different models and other components in a single inference pipeline. An inference graph can consist of several components:

+   - One or more ML models for the different prediction tasks
- Traffic routing management for usage patterns, such as traffic splitting to different models for A/B testing
- A component for combining results from multiple models, such as a model ensemble component