# Determine the Security Requirements for Storage Workloads

Azure Storage accounts are ideal for workloads that require fast and consistent response times or involve many input-output operations (IOPs). Storage accounts contain all your Azure Storage data objects, such as the following:

+   - Blobs
+   - File shares
+   - Queues
+   - Tables
+   - Disks

Optimize your Azure Storage account's security by following these recommendations:

+   - Enable soft deletion for blobs.
+   - To authorize access to blob data, use Azure AD.
+   - Consider the principle of least privilege when assigning permissions to an Azure AD security principal using Azure RBAC.
+   - To store business-critical data, use blob versioning or immutable blobs.
+   - Storage accounts should be restricted from accessing the Internet by default.
+   - Limit access to your storage account by configuring firewall rules.
+   - Network access should be limited to specific networks.
+   - Access the storage account only with trusted Microsoft services.
+   - Make sure all your storage accounts have the Secure Transfer required option enabled.
+   - SAS tokens should be used only with HTTPS connections.
+   - Avoid and prevent storage accounts with Shared Key authorization.
+   - Make sure you regenerate your account keys regularly.
+   - If you issue SAS to clients, create a revocation plan.

# Security Posture Management for Storage

To improve the overall security posture of web workloads, they need to undergo an ongoing security assessment, just like any other cloud workload. Azure Defender for Storage detects distinctive and potentially destructive attempts to access and exploit your storage account using Azure-native security intelligence. Security alerts are provided contextually based on Microsoft Threat Intelligence data and advanced threat detection capabilities. As part of those alerts, steps are also outlined for mitigating the threats and preventing future attacks.