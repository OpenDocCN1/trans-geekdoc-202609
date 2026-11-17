# Configure CI pipeline

At this stage, you will configure the CI pipeline. This pipeline will execute the following tasks:

+   - Set up Python version 3.6.
+   - Install required dependencies.
+   - Create or get Azure Machine Learning (AML) workspace.
+   - Build and train the ML model.
+   - Evaluate newly trained model performance against the existing model to decide whether the model is to be promoted to production.
+   - Register model in Azure Machine Learning (AML) service.
+   - Create a scoring Docker image with the required dependencies.
+   - Publish the artifacts (all files) to the repo.

The following figure shows the steps of the CI pipeline:

![](bbox=[0.195, 0.48, 0.795, 0.915])

Figure 11.25: CI pipeline for ML