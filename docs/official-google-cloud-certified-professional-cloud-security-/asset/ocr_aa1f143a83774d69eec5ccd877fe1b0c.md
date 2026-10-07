# GKE security features 411

Audit records begin their lifecycle inside the kube-apiserver component. Each record on each stage of its execution generates an audit event, which is then pre-processed according to a certain policy and written to a backend. The policy determines what's recorded and the backends persist the records. The current backend implementations include log files and webhooks.

The Kubernetes documentation goes on to say that each request can be recorded with an associated stage. The defined stages are as follows:

+   * RequestReceived: The stage for events generated as soon as the audit handler receives the request, and before it is delegated down the handler chain.
* ResponseStarted: Once the response headers are sent, but before the response body is sent. This stage is only generated for long-running requests (for example, watch).
* ResponseComplete: The response has been completed and no more bytes will be sent.
* Panic: Events generated when a panic occurred.

The GKE audit policy defines rules about how events should be recorded and what data they should. GKE receives the log entries from the Kubernetes API server, and applies its policy to determine which entries get to the project's logs. For the most part, GKE applies the following rules to log entries that come from the Kubernetes API server:

+   * Entries that represent create, delete, and update requests go to the Admin Activity log
* Entries that represent get, list, and updateStatus requests go to the Data Access log

Admin Activity logs are turned on by default in your Google Cloud project. They can't be turned off; however, you must turn on Data Access logs. Let us move on to understanding the features of GKE logging.

# Logging

By default, GKE clusters are natively integrated with Cloud Logging (Monitoring). When you create a GKE cluster, both Monitoring and Cloud Logging are enabled by default. This means you get a monitoring dashboard specifically tailored for Kubernetes and your logs are sent to Cloud Logging's dedicated, persistent datastore and indexed for both searches and visualization in the Cloud Logs Viewer.

There are several ways to access your logs in Cloud Logging depending on your use case.

You can access your logs using the following:

+   * Cloud Logging console: You can see your logs directly from the Cloud Logging console by using the appropriate logging filters to select Kubernetes resources such as cluster, node, pod, or container logs. Here are some sample Kubernetes-related queries to help you get started.