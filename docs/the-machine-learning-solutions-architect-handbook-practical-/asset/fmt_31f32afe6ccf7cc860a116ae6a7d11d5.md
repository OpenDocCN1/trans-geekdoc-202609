
In a Kubernetes-based environment, there are two main approaches for model training you can choose from depending on your training needs:

*   Model training using `Kubernetes` `Jobs`

*   Model training using `Kubeflow` `training operators`

Let’s take a closer look at each one of these approaches in detail:

*   **Model training using Kubernetes Jobs**: As we discussed in `Chapter 6`, `Kubernetes Container Orchestration Infrastructure Management`, a Kubernetes Job creates one or more containers and runs them through to completion. This pattern is well suited for running certain types of ML model training jobs, as an ML job runs a training loop to completion and does not run forever. For example, you can package a container with a Python training script and all the dependencies that train a model and use the Kubernetes Job to load the container and kick off the training script. When the script completes and exits, the Kubernetes Job also ends. The following sample YAML file kicks off a model training job if submitted with the `kubectl apply` command: 

```
apiVersion: batch/v1
kind: Job
metadata:
name: train-churn-job
spec:
template:
spec:
containers:
- name: train-container
imagePullPolicy: Always
image: <model training uri>
command: ["python", "train.py"]
restartPolicy: Never
backoffLimit: 4
```

    To query the status of the job and see the detailed training logs, you can run the `kubectl get jobs` command and the `kubectl logs <pod name>` command, respectively.

*   **Model training using Kubeflow training operators**: A Kubernetes Job can launch a model training container and run a training script inside the container to completion. Since the controller for a Kubernetes Job does not have application-specific knowledge about the training job, it can only handle generic Pod deployment and management for the running jobs, such as running the container in a Pod, monitoring the Pod, and handling generic Pod failure. However, some model training jobs, such as distributed training jobs in a cluster, require the special deployment, monitoring, and maintenance of stateful communications among various Pods. This is where the Kubernetes training operator pattern can be applied.

Kubeflow offers a list of pre-built training operators (such as the `TensorFlow`, `PyTorch`, and `XGBoost` operators) for complex model training jobs. Each Kubeflow training operator has a `custom resource` (`CR`) (for example, `TFJob CR` for TensorFlow jobs) that defines the training job’s specific configurations, such as the type of Pod in the training job (for example, `master`, `worker`, or `parameter server`), or runs policies on how to clean up resources and for how long a job should run. The controller for the CR is responsible for configuring the training environment, monitoring the training job’s specific status, and maintaining the desired training job’s specific state. For instance, the controller can set environment variables to make the training cluster specifications (for example, types of Pods and indices) available to the training code running inside the containers. Additionally, the controller can inspect the exit code of a training process and fail the training job if the exit code indicates a permanent failure. The following YAML file sample template represents a specification for running training jobs using the TensorFlow operator (`tf-operator`):

```
apiVersion: "kubeflow.org/v1"
kind: "TFJob"
metadata:
name: "distributed-tensorflow-job"
spec:
tfReplicaSpecs:
PS:
replicas: 1
restartPolicy: Never
template:
spec:
containers:
- name: tensorflow
image: <model training image uri>
command:
Worker:
replicas: 2
restartPolicy: Never
template:
spec:
containers:
- name: tensorflow
image: <model training image uri>
command:
```

In this example template, the specification will create one copy of the parameter servers (which aggregate model parameters across different containers) and two copies of the workers (which run model training loops and communicate with the parameter servers). The operator will process the `TFJob` object according to the specification, keep the `TFJob` object stored in the system with the actual running services and Pods, and replace the actual state with the desired state. You can submit the training job using `kubectl apply -f <TFJob specs template>` and can get the status of the `TFJob` with the `kubectl get tfjob` command.

As a data scientist, you can submit Kubernetes training jobs or Kubeflow training jobs using the `kubectl` utility, or from your Jupyter Notebook environment using the `Python SDK`. For example, the `TFJob` object has a Python SDK called `kubernet.tfjob`, and Kubernetes has a client SDK called `kubernetes.client` for interacting with the Kubernetes and Kubeflow environments from your Python code. You can also invoke training jobs using the `Kubeflow Pipeline` component, which we will cover later, in the `Kubeflow pipeline` section.

Using Kubernetes Jobs for ML training requires the installation and configuration of the necessary ML software components for training different models using different frameworks. You will also need to build logging and monitoring capabilities to monitor the training progress.

The adoption of Kubeflow training operators also presents its own set of challenges. Several operators, including the MPI training operator, are still in the maturing phase and are not yet suitable for production adoption. While operators provide certain logs and metrics, obtaining a comprehensive view of extensive training runs across Pods remains challenging and necessitates the integration of multiple dashboards. The existence of separate operators for various ML frameworks with fragmented capabilities and statuses complicates achieving a unified experience. 

The learning curve for running training operators can be high, as it involves understanding many components, such as the development of training YAML files, distributed training job configuration, and training job monitoring.

## Registering models with a model registry

A `model registry` is an important component in model management and governance, and it is a key link between the model training stage and the model deployment stage, as models need to be properly stored in a managed repository for a governed model deployment. There are several open-source options for implementing a model registry in an ML platform. In this section, we will explore MLflow Model Registry for model management. 

MLflow Model Registry is one of the leading model registry solutions with strong support in model artifacts lifecycle management, versioning support, and a range of deployment targets like Docker, Amazon SageMaker, and Azure ML. It is designed for managing all stages of the ML lifecycle, including experiment management, model management, reproducibility, and model deployment. It has the following four main components:

*   **Experiment tracking**: During model development, data scientists run many training jobs as experiments using different datasets, algorithms, and configurations to find the best working model. Tracking the inputs and outputs of these experiments is critical to ensure efficient progress. Experiment tracking logs the parameters, code versions, metrics, and artifacts when running your ML code and for later visualizing of the results.

*   **ML projects**: Projects package data science code in a format to reproduce runs on any platform.

*   **Models:** Models provide a standard unit for packaging and deploying ML models.

*   **Model Registry:** Model Registry stores, annotates, discovers, and manages models in a central repository.
