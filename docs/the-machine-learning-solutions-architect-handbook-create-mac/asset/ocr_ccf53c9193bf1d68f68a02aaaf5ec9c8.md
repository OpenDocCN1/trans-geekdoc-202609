# Adopting MLOps for ML workflows 277

![](bbox=[0.142, 0.095, 0.857, 0.415])

Figure 9.3 – MLOps architecture using AWS services

As we mentioned earlier, the shared service environment hosts common tools for pipeline management and execution, as well as common repositories such as code repositories and model registries.

Here, we use AWS CodePipeline to orchestrate the overall CI/CD pipeline. AWS CodePipeline is a continuous delivery service that integrates natively with different code repositories as AWS CodeCommit and Bitbucket. It can source files from the code repository and make them available to downstream tasks such as building containers using the AWS Build service, training models in the model training environment. You can create different pipelines to meet different needs. A pipeline can be triggered on-demand via an API or the CodePipeline management console, or by changes in a code repository. Depending on your requirements, you can create different pipelines. In the proceeding diagram, we can see four example pipelines:

+   * A container build pipeline for building different container images.

+   * A model training pipeline for training a model for release.

+   * A model deployment pipeline for deploying trained models to production.

+   * A development, training, and testing pipeline for model training and deployment testing in a data science environment.