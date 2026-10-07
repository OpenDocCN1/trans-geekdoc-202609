IAM Conditions can only be used on buckets with uniform bucket-level access to prevent conflicts between policies and ACLs. So, note the following points when using it:

+   * Set IAM conditions on a bucket after enabling uniform bucket-level access
* Remove all IAM conditions from a bucket's policy to deactivate uniform bucket-level access
* Uniform bucket-level access cannot be disabled after 90 days of use

This concludes the section on IAM policies and storage bucket ACLs. Let us look at IAM APIs.

# IAM APIs

IAM uses the following API endpoints (regular OAuth access tokens either for a user or service account can be used to access these APIs:

+   * Policies (v2)
* Roles (query and get/list)
* Organizations roles
* Permissions
* Projects
    * IAM policies (linting and querying)
    * Workload identity pools, operations, and providers
    * Permissions
    * Roles
    * Service accounts
    * Service account keys
* Service account credentials
* Security token services

Finally, let us look at various log files for IAM APIs. You will often start with these logs to troubleshoot an issue.

# IAM logging

Google Cloud IAM writes audit logs and admin logs to help with questions such as “Who did what, where, and when?” These logs are vitally important for audit and forensic capabilities.