# Google Cloud Identity Access Management

+   - Do not grant OWNER permission to anyone in the organization. Typically, you want the IaC service account to have ownership of the buckets.

+   - Be aware of how you grant permissions to anonymous users. The allUsers and allAuthenticatedUsers provide access to everyone on the internet - be they anonymous users or logged in with a Google account. You may not want this behavior.

+   - Avoid setting ACLs in inaccessible objects. An inaccessible object is an that cannot be downloaded (read) and can only be deleted. This can happen when the owner of an object leaves a project without granting anyone else OWNER or READER permission on the object.

+   - Make sure to delegate administrative control of your buckets. By default, project owners have OWNER permissions. Make sure not to assign this role to individuals.

+   - Make sure you understand Cloud Storage's interoperable behavior before using it.

# Uniform bucket-level access

Cloud Storage has uniform bucket-level access to support the system's uniform permissions. When you use this feature on a bucket, all ACLs for Cloud Storage resources in the bucket are disabled, and access to Cloud Storage resources is allowed solely through IAM. You have 90 days after enabling consistent bucket-level access to revoke your decision.

Keep in mind that enabling uniform bucket-level access revokes access for users who get access purely through object ACLs and prevents users from managing rights through bucket ACLs. Before enabling consistent bucket-level access, read the Google Cloud product documentation when moving an existing bucket and consider whether it's the right thing to do in your situation.

# Using uniform bucket-level access in practice

When you use uniform bucket-level access? Uniform bucket-level access streamlines how you offer access to Cloud Storage resources. Using consistent bucket-level access also enables you to use features such as Domain Restricted Sharing and IAM Conditions.

You might not want to use uniform bucket-level access and instead keep fine-grained ACLs in the following situations:

+   - You legacy ACLs to control bucket object access

+   - You want an object's uploader to have full control over that object but to have less access to the objects

+   - You want to use the XML API to view or set bucket permissions