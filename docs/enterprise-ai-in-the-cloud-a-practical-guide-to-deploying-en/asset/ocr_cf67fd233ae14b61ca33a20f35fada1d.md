| | ARTIFACT TRACKING DESCRIPTION TOOLS |
| :--- | :--- |
| Code Versioning | Git, Google Cloud Source Repositories | Supports integrating Git and Google Cloud source repositories to help track code versions. |

+   **Code Repository**
+   **Experiments**
+   * Python notebooks
+   * and code
+   **ML Training & Deployment**
+   * Python code
+   * Docker files
+   * BuildSpec files
+   * CloudFormation templates
+   **Model Registry**
+   **Images**
+   * Data processing
+   * Model training
+   * Model deployment
+   **Model Binaries**
+   * model.tar.gz

![](bbox=[0.305, 0.205, 0.695, 0.495])

+   **Data Repository**
+   **Data Files**
+   * Raw data
+   * Processed data
+   * Labeled data
+   * Training data
+   * Validation data
+   * Inference data
+   * Inference feedback
+   **Manifest Repository**
+   **Release**
+   * Container IDs
+   * Model name
+   * Model binary path
+   * Instance type and count
+   * Monitoring config
+   **Build**
+   * Container IDs
+   * Input data
+   * Data processing
+   * Compute
+   * Training
+   * Artifact registry
+   * Execution outputs

# **FIGURE 14.7:** Data and artifacts lineage tracking

Google Cloud also provides services such as Kubeflow, Data Catalog, and Dataflow to track artifacts throughout the machine learning lifecycle.

# # Container Image Management

Container image management is a vital step to enable MLOps, because it ensures that the models are deployed in consistent environments. Container orchestration tools such as Kubernetes play a critical role in automating the deployment of ML models and platforms like AWS, Azure, and Google Cloud support this.

The following table lists several types of images that need to be managed:

| TYPE OF IMAGE | STORAGE LOCATION/OWNERSHIP | DESCRIPTION |
|---|---|---|
| Public images | Docker Hub, GitHub, ECR Public Gallery | Publicly available images stored in public repositories. |