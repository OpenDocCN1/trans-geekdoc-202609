+   Choose the IAM user for which you want to create an access key and secret key pair.
In the “Security credentials” tab, scroll down to the “Access keys” section.
Click the “Create access key” button.
Select “Application running on an AWS compute service” under “Use case” and confirm the message “I understand the above recommendation and want to proceed to create an access key” at the bottom of the screen.
Once the access key is created, you’ll see the access key ID and the secret access key. Take note of these credentials as they will be displayed only once. If you lose them, you’ll need to create a new access key.
Ensure that the IAM user or role associated with the access key pair has the necessary permissions for S3 actions. This can be achieved by attaching the appropriate policies such as AmazonS3FullAccess.

One issue with this method is the security risk arising from hardcoding credentials in your code, which can lead to accidental exposure. Another issue relates to maintenance: updating credentials requires code changes, which can be cumbersome.

A better solution is to use IAM roles, which AWS manages securely without needing to specify the credentials required to access S3 in your code. This approach is more secure and scalable, especially in production environments.

An IAM role is an AWS identity that you can create and assign specific permissions to, allowing trusted entities (such as EC2 instances running Databricks) to assume the role and perform actions in AWS. When an IAM role is attached to the EC2 instances hosting your Databricks cluster,