The EKM creation flow is as follows:

+   Establish an account with the partner. They have their own portal where you manage the keys.
Create a key or use an existing key. This has a unique URI or key path. Copy this path to use in Step 4.
Next, grant your Google Cloud project workload service account access to the key in the external key management partner system.
In your Google Cloud project, you create a Cloud EKM key, using the URI or key path for the externally managed key.

While Cloud EKM seems like a great option to use, there are some considerations you should be aware of:

+   Cloud EKM can be used with Hosted Private HSM to create a single-tenant HSM solution integrated with Cloud KMS. Choose a Cloud EKM partner that supports single-tenant HSMs.
When you use a Cloud EKM key, Google has no control over the availability of your externally managed key in the partner system. Google cannot recover your data if you lose your keys outside of Google Cloud.
Review the guidelines about external key management partners and regions when choosing the locations for your Cloud EKM keys.
Review the Cloud EKM service-level agreement (SLA).
Communicating with an external service over the internet can lead to problems with reliability, availability, and latency. For applications with a low tolerance for these types of risks, consider using Cloud HSM or Cloud KMS to store your key material.
You will need a support contract with the external key management partner. Google Cloud support can only provide support for issues in Google Cloud services and cannot directly assist with issues on external systems. You may need to work with support on both sides to troubleshoot interoperability issues.

# Restrictions

Here are some general restrictions you should be aware of while using Cloud EKM:

+   Automatic rotation is not supported.
When you create a Cloud EKM key using the API or the Google Cloud CLI, it must not have an initial key version. This does not apply to Cloud EKM keys created using the Cloud console.
Cloud EKM operations are subject to specific quotas in addition to the quotas on Cloud KMS operations.