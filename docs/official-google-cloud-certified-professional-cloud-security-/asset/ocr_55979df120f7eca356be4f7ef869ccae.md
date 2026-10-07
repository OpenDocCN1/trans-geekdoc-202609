# Security logs

Cloud Logging offers two forms of security logs: Cloud Audit Logs and Access Transparency Logs. Cloud Audit Logs generates the following types of audit logs for each cloud project, folder, and organization:

+   - Admin Activity audit logs include information on API calls and actions that potentially alter cloud resource settings. Activities such as creating a virtual machine or altering Cloud IAM permissions are examples of changes that are captured by Admin Activity audit logs. You can't configure, exclude, or disable these types of logs. They're always recorded for security reasons. Admin Activity audit logs are created even if the Cloud Logging API is disabled. The retention period for administrator activity records is 400 days.
- Data Access audit logs show who accessed what data, the access time, and what actions were performed. Data Access audit logs are retained for 30 days. All Google Cloud services are supported. Data access audit logs are disabled by default.
- System Event audit logs: Events that alert resource configurations are recorded in System Event audit logs. These logs are generated automatically by Google's systems, not by users. System Event audit logs cannot be configured, excluded, or they are always written.
- Policy Denied audit logs: Policy Denied audit logs are created when a Google Cloud service rejects a user or service account access for a security policy violation. VPC Service Controls determines policies and sends Cloud Logging Policy Denied audit logs. Your Cloud project gets charged for Policy Denied audit log storage. You can't disable Policy Denied audit logs, but you can exclude them from Cloud Logging.

The next type of security log is Access Transparency. Access Transparency provides logs based on the actions taken by Google staff when accessing your Google Cloud content. Access Transparency logs can help you track the compliance posture of your organization with regard to your legal and regulatory requirements. We recommend Access Transparency in depth in Chapter 3, Trust and Compliance.

# User logs

As mentioned earlier, user logs, sometimes referred to as user-written logs, are written to Cloud Logging using an agent, the Cloud Logging API, or client libraries. Let's take a look at the user-agent log type:

+   - Cloud Logging agent: An agent can be installed to stream logs from instances to Cloud Logging. The Cloud Logging agent is based on Fluentd and is preconfigured by default to syslog logs and common third-party tools' logs (for example, MySQL, PostgreSQL, MongoDB, Cassandra, and Apache). It is possible to customize the pre-configured Fluentd agent configurations as required.