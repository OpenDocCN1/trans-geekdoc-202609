+   1. Calculate the requirements for each step:
+      a. Hardware compute resources
+      b. OS resources (like Docker image(s))
+      c. Software resources (like Conda/virtual env dependencies)
+      d. Data inputs
+   
+   2. It determines the dependencies between various steps, which results in a dynamic execution graph.
+   
+   3. The following things happen when each node in the execution graph runs:
+      a. The service conceivably reuses existing resources to configure the necessary hardware and software environment.
+      b. The step runs and provides logging and monitoring information to its containing experiment object.
+      c. The output of every step is treated as inputs to the next step and/or written to storage.
+      d. Resources that are of no use are concluded and disconnected.

# The benefits of using pipelines in ML workflow are:

+   - It enables you to run steps, either parallel or sequentially in a reliable and unattended manner.
+   - You can create multiple pipelines and reliably coordinate heterogeneous compute. This means you can make effective use of available compute resources by running individual pipeline steps on various compute targets, such as HDInsight, GPU Data Science VMs, and Databricks.
+   - Pipelines can be reused by creating pipeline templates for explicit scenarios, like retraining and batch-scoring. You can trigger published pipelines from external systems through simple REST calls.