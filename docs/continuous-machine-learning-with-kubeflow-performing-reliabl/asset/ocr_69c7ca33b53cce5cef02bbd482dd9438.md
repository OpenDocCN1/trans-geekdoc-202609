**Kubernetes** The Pipeline Service calls the Kubernetes API server to create the necessary Kubernetes resources (CRDs) to run the pipeline.

**Python** You create the components or specify a pipeline using the Kubeflow Pipelines **domain-specific language**

**DSL** The DSL compiler transforms your pipeline’s Python code into a static configuration (YAML).

**Pipeline** You call the Pipeline Service to create a pipeline run from the static configuration.

**Orchestration** A set of orchestration controllers execute the containers needed to complete the pipeline. The containers execute within the Kubernetes Pods on virtual machines. An example controller is the **Argo Workflow** controller, which orchestrates the task-driven workflows.

**Pipeline web** The Pipeline web server gathers data from various services to display relevant views – the list of pipelines currently running, the history of pipeline execution, the list of data artifacts, debugging information about individual pipeline runs, and execution status about individual pipeline runs.

**Pipeline** You call the Pipeline Service to create a pipeline run from the static configuration.