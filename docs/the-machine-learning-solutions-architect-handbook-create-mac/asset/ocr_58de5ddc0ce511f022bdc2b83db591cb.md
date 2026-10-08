# ML pipeline monitoring

The ML pipeline's execution needs to be monitored for statuses and errors, so corrective actions can be taken as needed. During a pipeline execution, there are pipeline-level statuses/events as stage-level and action-level statuses/events. You can use these events and statuses to understand the progress of each pipeline and stage and get alerted when something is wrong. The following diagram shows how AWS CodePipeline, CodeBuild, and CodeCommit can work with CloudWatch, CloudWatch Logs, and EventBridge for general status monitoring and reporting, as well as problem troubleshooting:

![](bbox=[0.163, 0.313, 0.801, 0.786])

CodeBuild can send metrics, such as SucceededBuilds, FailedBuilds, and Duration metrics. These CodeBuild metrics can be accessed through both the CodeBuild console and the CloudWatch dashboard.