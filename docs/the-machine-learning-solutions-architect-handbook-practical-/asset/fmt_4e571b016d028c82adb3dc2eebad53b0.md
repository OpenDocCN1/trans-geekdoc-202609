
It is important to note that running pipelines using Kubeflow Pipelines requires a high degree of competency with Kubernetes, which could be challenging for people without deep Kubernetes skills. Building the workflow in Python can be a complex task that involves writing a `Dockerfile` or `YAML` file for each component, and Python scripts for the workflow and execution. Kubeflow Pipelines mainly works within the Kubeflow environment, with very limited integration with external tools and services. It also lacks native pipeline versioning capability. Despite these challenges, Kubeflow Pipelines is still widely adopted due to its support for end-to-end ML management, workflow visualization, portability, and reproducibility.

Now that we have explored various open-source tools for building ML platforms, let’s delve into end-to-end architecture using these open-source frameworks and components.

# Designing an end-to-end ML platform

After discussing several open-source technologies individually, let’s now delve into their integration and see how these components come together. The architecture patterns and technology stack selection may vary based on specific needs and requirements. The following diagram presents the conceptual building blocks of an ML platform architecture:

![](OEBPS/Images/B20836_07_12.png)

Figure 7.12: ML platform architecture

Next, let’s delve into different strategies to implement this architecture concept with different combinations of open-source technologies.

## ML platform-based strategy

When designing an ML platform using open-source technologies, one effective strategy is to utilize an ML platform framework as a base platform and then integrate additional open-source components to address specific requirements. One such ML platform framework is Kubeflow, which provides a robust foundation with its built-in building blocks for an ML platform. By leveraging Kubeflow, you can benefit from its core components while extending the platform’s capabilities through the integration of complementary open-source tools.

This strategy allows for flexibility and customization by seamlessly integrating a range of open-source ML components into the platform. You would choose this approach if the base ML platform framework meets most of your requirements, or if you can work within the limitations of the framework. The following table outlines key ML platform components and their corresponding open-source frameworks and tools:

| ML Platform Component | Open-Source Framework |
| --- | --- |
| Code repository | GitHub |
| Experimentation and model development | Kubeflow Jupyter Notebook |
| Experiment tracking | MLflow experiment tracker |
| Feature store | Feast feature store |
| Data annotation | Computer Vision Annotation Tool (CVAT) |
| Training | Kubeflow training operators |
| Data and model testing | Deepchecks |
| Model repository | MLflow Model Repository |
| ML pipeline development | Kubeflow Pipelines |
| Model inference | Kubeflow KFServing (Seldon Core, TFServing, Triton) |
| Docker image repository | Docker Hub |
| CI/CD | GitHub Actions |
| Drift monitoring | Deepchecks |

Table 7.1: ML platform components and their corresponding open-source frameworks

By incorporating these frameworks and tools into the architectural conceptual diagram, we can visualize the resulting diagram as follows:

![](OEBPS/Images/B20836_07_13.png)

Figure 7.13: Kubeflow-based ML platform

Using this architecture, data scientists utilize Kubeflow Jupyter Notebook for conducting experiments and building models. Experiment runs and relevant details, such as data statistics, hyperparameters, and model metrics, are tracked and saved in the MLflow experiment tracking component.

Common ML features are stored in the Feast feature store. When there is a need for data annotation, data annotators can employ open-source data annotation tools like `Computer Vision Annotation Tool` (`CVAT`) and Label Studio to label data for model training. Data scientists can utilize features from the feature store and the labeled dataset as part of their experimentation and model building.

GitHub serves as the code repository for data scientists. They save all source code, including training scripts, algorithm code, and data transformation scripts, in the code repository. Model training and inference Docker images are stored in Docker Hub. A Docker image build process can be deployed to create new Docker images for training and inference purposes.

For formal model training, the training script is pulled from the GitHub repository, and the training Docker image is pulled from Docker Hub into the Kubeflow training operator to initiate the model training, along with the training dataset. Deepchecks can be utilized to perform data validation and model performance checks. Once the model is trained, the model artifacts, along with any metadata such as model metrics and evaluation graphs, are stored in MLflow Model Registry.

When it is time to deploy the model, models are fetched from MLflow Model Registry and loaded into KFServing for model inference, along with the model inference Docker image and inference script. KFServing offers the flexibility to choose different inference servers, including Seldon Core, TFServing, and Triton.

Prediction logs can be sent to the model monitoring component for detecting data drift and model drift. Open-source software tools like Evidently AI can be employed for data drift and model drift detection.

To orchestrate various tasks such as data processing, feature engineering, model training, and model validation, Kubeflow Pipelines can be developed. For `CI/CD` (`Continuous Integration/Continuous Deployment`), GitHub Actions can be used as a triggering mechanism to initiate different pipelines.

Overall, this approach allows you to combine the benefits of a base ML platform framework with the flexibility provided by a wide range of open-source components.

## ML component-based strategy

An alternative approach is to build the ML platform using individual components rather than relying on a base ML platform framework. This strategy offers the advantage of selecting the best-in-class components for each aspect of the platform, allowing organizations to adhere to their existing open-source standards for core components like pipeline development or notebook IDEs. The following architectural pattern illustrates this approach.

![](OEBPS/Images/B20836_07_14.png)

Figure 7.14: Component-based architecture

In this architecture pattern, alternative technologies and tools are utilized for pipeline development, notebook environments, and training infrastructure management. Additionally, Kubernetes serves as the infrastructure management framework. This approach allows organizations to leverage specific technologies and tools that align with their unique requirements and preferences.

One notable aspect is the use of Airflow as the standard orchestration and pipeline tool across various technical disciplines, including ML and data management. Airflow’s widespread adoption within organizations enables it to serve as a unifying pipeline management tool, facilitating seamless integration between different components and workflows.

Moreover, this architecture pattern emphasizes the building of custom training and inference infrastructure on top of Kubernetes. By leveraging Kubernetes, organizations gain the flexibility to create customized training and inference environments tailored to their specific needs.

In addition to the availability of free open-source tools that meet ML platform requirements, it is important to consider the integration of commercial components into the open-source architecture. These commercial offerings can enhance specific aspects of the ML platform and provide additional capabilities.
