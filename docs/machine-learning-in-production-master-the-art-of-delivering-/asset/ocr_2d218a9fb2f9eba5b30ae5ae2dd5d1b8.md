Note: You need to select Azure service connection from the Azure subscription dropdown wherever necessary.

Next, in the **Triggers** tab, select **Enable continuous integration** checkbox. This enables the CI pipeline to run as soon as any changes are pushed to the code repository.

You can trigger the CI pipeline by pushing any changes to the repository. The Azure CI pipeline detects the changes in the repo and starts building the pipeline. To see the progress of the CI pipeline, switch to the **Summary** tab.

The following figure displays the **Summary** tab. You can see the commit message on the top, followed by the summary and the jobs. The job status and progress of steps can be seen by clicking on **Phase 1**.

![](bbox=[0.225, 0.345, 0.772, 0.731])

Figure 11.26: CI pipeline for ML-Jobs summary