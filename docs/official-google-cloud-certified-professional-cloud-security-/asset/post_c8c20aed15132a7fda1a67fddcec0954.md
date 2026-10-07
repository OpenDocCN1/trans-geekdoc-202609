
[content]
## Accessing a secret

Accessing a secret version returns the secret contents as well as additional metadata about the secret version. When you access a secret version, you specify its version-id. You can also access the latest version of a secret by specifying latest as the version.

Accessing a secret version requires the secretmanager.secretAccessor IAM role. Typically, this role is granted to the service account used by your application.

The following is a gcloud command that can be used to access a particular version of the secret. However, a common method is to use application libraries for it, as you will see later in the section:

```
gcloud secrets versions access version-id --secret="secret-id"
```

You can also use the latest keyword to get the current version, but this is not a recommended best practice.

## Accessing a binary secret version

You can access binary secrets directly but not Cloud SDK formats the output as UTF-8, which can corrupt binary secrets. To get the raw bytes, Cloud SDK prints the output as base64-encoded, which you can decode:

```
gcloud secrets versions access version-id --secret="secret-id" --format='get(payload.data)' | tr '_' '/' | base64 -d
```

## Accessing secrets from your application

You can access secrets from Google Cloud services as Compute Engine, Application Engine, GKE, and Cloud Run.

Secret Manager has a REST and gRPC API for accessing and managing secrets. However, a convenient way to get to secrets is by using client libraries bundled with your application to access secrets. You do not need to embed service account keys within your application to Secret Manager APIs. All you need is the right IAM role for the service account used by Google Cloud service of your choice, such as GCE, GAE, or Cloud Functions:

- In Cloud Build

- Mount the secret as a volume, which will make the secret available to the container as files. Reading the volume will read the secret from Secret Manager. You can use the latest keyword to fetch the secret using this method.

- Access the secret using a traditional environment variable. Environment variables are resolved by Cloud Run at the start of the container. When you use this method, do not use the latest keyword, use a particular version.

- For GKE, you can use Workload Identity in conjunction with Secret client libraries to access secrets. You can also use the Secret Store CSI driver in conjunction with the Google Secret Manager provider for this. This driver allows you to access secrets as files mounted in Kubernetes pods. The provider is an open source project supported by Google that uses the workload identity of the pod as secret when authenticating to the Google Secret Manager API. For this work, the workload identity of the pod must be configured and appropriate IAM bindings must be applied. This plugin is built to ensure compatibility between Secret Manager and Kubernetes workloads that need to load secrets from the filesystem. The plugin also enables syncing secrets to Kubernetes-native secrets for consumption as environment variables. When evaluating this, consider the following threats:

- When a secret is accessible on the filesystem, application vulnerabilities such as directory traversal (https://pack.link/wYWwm) attacks can become higher severity as the attacker may gain the ability to read the secret material.

- When a secret is consumed through environment variables, misconfigurations such as binding debug endpoint or including dependencies that log process environment details may leak secrets.

- When syncing secret material to another data store (such as Kubernetes Secrets), consider whether the access controls on data store are sufficiently narrow in scope.

- For multi-cloud application deployments, consider using workload identity federation on other platforms, such as Amazon Web Services or Microsoft Azure, that use current identity protocols to authenticate to Google Cloud APIs. Typically, you would want to use the native offering of the cloud providers for where your application is deployed.

Let us look at how to achieve multi-region redundancy of secrets by using a secret rotation policy. This strategy supports the application redundancy you would need for high availability and failover.

## Secret replication policy

Secrets are a global resource entity; however, secret payloads (the underlying secret material) are stored locally within a region. Some regulated customers such as financial and healthcare institutions may have strict residency requirements, while other customers may want to store the secret near the data. A replication policy allows control over where secret payloads are stored.

There are two replication policy types: automatic and user-managed.

## Automatic

With the automatic policy type, the replication of the secret is managed by Google. This policy provides the highest level of availability:

- When a secret has an automatic replication policy, its payload data is copied as many times as needed. This is the easiest way to set things up, and most users choose it. This is the policy that used by default when a secret is created using the Google Cloud CLI or the web UI.
- A secret that is automatically replicated is stored in a single place for billing purposes.
- For a resource location organization policy evaluation, you can only make a secret with an automatic replication policy if you can make resources global.

## User-managed (user-selected)

With the user-managed replication policy type, the secret is replicated to only locations selected by users:

> Note
The secret version addition will be impacted if one of the regions you select is unavailable.

- The payload data of a secret with a user-managed replication policy is duplicated to a user-configured list of locations. The secret can be duplicated to as many supported locations as you choose. If there are regulations on where the secret payload data can be stored, this could be useful.
- Each location in the user-managed replication policy is treated as a separate location for billing reasons.
- A secret with a user-managed replication policy can only be created if the organization policy allows the creation of resources in all selected locations.
- As a rule, choose between two and five locations for replication. Having a large number of locations results in longer replication delays as well as increased latency.

Let us look at some of the encryption options, namely Google default encryption and customer-managed encryption, for Secret Manager.

## CMEKs for Secret Manager

By default, secrets are encrypted with Google default encryption. However, some regulated customers require control of keys, so Secret Manager supports customer-managed encryption keys (CMEKs) (within Cloud KMS) for encrypting:

> Note
However, if you disable or permanently destroy the CMEK, the secret encrypted with that key cannot be decrypted.

- Secret payloads are encrypted by Google-managed keys before being written to persistent storage with no additional configuration required.
- Secret Manager encrypts data with a unique data encryption key (DEK) before writing it to persistent storage in a specific location. The Secret Manager service owns a replica-specific called a key encryption key (KEK), which is used to encrypt the DEK. This is commonly referred to as envelope encryption.
- The CMEK is a symmetric key that you control within Cloud KMS when using CMEKs with Secret Manager. The CMEK must be stored in the GCP region as the secret. This makes sure that Secret Manager has access to the key in the event of a zone or region failure.
- Customers who desire control over encryption keys can use the Cloud External Key Manager (EKM) in the CMEK policy for encryption and decryption. This removes Google's management of the encryption key for your secrets as the encryption key is controlled outside of Google Cloud.
- CMEKs are also supported using user-managed replication. When you create a CMEK in Cloud KMS, make sure the location of the key matches the location of the secret if you are using a user-managed replication policy.

So far, we know how to set up secrets in Google Cloud. Let us now go over some of the best practices for managing secrets in production and development environments.

# Best practices for secret management

Here are some general practices that Google recommends when it comes to managing secrets:

- As with much all services in Google Cloud, access to the Secret Manager API is protected by IAM. Follow the principle of least privilege when granting permissions to secrets to your applications.
