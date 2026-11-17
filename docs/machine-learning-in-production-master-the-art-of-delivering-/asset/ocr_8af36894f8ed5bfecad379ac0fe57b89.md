Hereafter, the repository should be accessible from the local terminal. Now, create a new directory and clone the Cloud Source Repository to your local machine, include the code files in it, and push it to the Cloud Source Repository from the local machine.

Let's consider the scenario of loan prediction, where the problem statement is to predict whether a customer's loan will be approved. Feel free to implement hyperparameter tuning and optimize the model.

First, create a package of ML code, and build a web app using FastAPI. Then, create the test cases and dependencies file, Dockerfile, and docker-compose file. Finally, create configuration files for GCP deployment, namely, cloudbuild.yaml, deployment.yaml, service.yaml.

Note: For code files in the src directory, refer to the ML model package developed in Chapter 4: Packaging ML Models, and for the rest of the code files, refer to Chapter 11: Deploying ML Models on Microsoft Azure. New code files added are cloudbuild.yaml, deployment.yaml, and service.yaml. Remove workflow directory .github. Also, the tox.ini file is updated for this scenario.

The code repository is also available on GitHub at https://github.com/suhas-ds/GCP.

The following directory structure shows the CI/CD pipeline files:

```
.\n|-- k8s\n|   |-- deployment.yaml\n|   |-- service.yaml\n|-- src\n|   |-- build\n|   |   |-- bdist.linux-x86_64\n|   |   |-- lib\n|   |-- prediction_model\n|   |   |-- config\n|   |   |-- datasets\n|   |   |-- processing\n|   |   |-- __pycache__\n|   |   |-- trained_models\n|   |   |-- __init__.py\n|   |   |-- pipeline.py\n|   |   |-- predict.py
```