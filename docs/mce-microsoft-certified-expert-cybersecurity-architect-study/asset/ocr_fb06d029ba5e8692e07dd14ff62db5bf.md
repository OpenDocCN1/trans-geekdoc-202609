data and storage resources and services with Microsoft Defender for Cloud, including the following:

+   - Azure Storage
+   - Azure Cosmos DB
+   - Azure Key Vault
+   - SQL Database

Each resource or service is protected differently by Microsoft Defender for Cloud. Microsoft Defender protects Azure Storage resources for the cloud with advanced threat protection, including the following:

+   - Blob containers
+   - File shares
+   - Data lakes

You will receive alerts based on events across your Azure Storage accounts. For example, Microsoft Defender for Cloud monitors activity across your Azure Storage accounts.

+   - **Suspicious activity**: For instance, someone might have accessed one of your storage accounts using an IP address that is an active Tor exit node.
+   - **Anomalous behavior**: You are alerted when Microsoft Defender for Cloud detects abnormal behavior. Usually, your storage accounts are accessed from the United States, but now access might be attempted from another continent.

Your cloud security posture must be robust to achieve this. You will be able to identify and address any components and systems that don't comply with your security and compliance standards.

Defender for Cloud's Secure Score in Figure 5.9 displays the scores for one or more subscriptions (based on the number of subscriptions selected in the Azure Portal).

You can improve your security by reviewing Defender for Cloud's recommendations page and following the remediation instructions for each recommendation. The recommendations are organized into security controls, and each control represents your vulnerable attack surfaces and groups-related security recommendations logically. A single resource within a control can be remediated only if all recommendations are addressed. Find out how well your organization protects each attack surface by reviewing each security control score.

Figure 5.10 depicts an example of the recommendations dashboard with all security controls arranged in a top-down list, with the controls at the top having the greatest impact on the Secure Score.

As you continuously remediate security recommendations to improve your Secure Score, you can track progress as your key performance indicator (KPI).

The recommended choice is to use the Secure Score to track your progress and remediate security recommendations triggered by Microsoft Defender for Cloud. However, you can still do much more to keep progressing positively toward a better security posture. A company's Secure Score will likely fluctuate up and down if its Azure Governance is not very mature, and a new resource provisioned without security settings can contribute to this problem.