# Key management options 227

For the exact steps to enable CMEKs, see the documentation for the relevant Google Cloud service.
You can expect to follow steps like these:

+   1. You create or import a Cloud KMS key, selecting a location as is geographically near as possible to the location of the service's resources. The service and the key can be in the same project or different projects. This is the CMEK.
2. You grant the CryptoKey Encrypter/Decpter IAM role (roles/cloudkms.cryptoKeyEncrypterDecrypter) on the CMEK to the service account for that service.
3. You configure the service to use a CMEK to protect your data. For example, you can configure a GKE cluster to use a CMEK to protect data at rest on the boot disks of nodes.

+   * If an account has a cryptoKeyEncrypterDecrypter role, it can encrypt and decrypt its data. If you disable or revoke the CMEK, then data cannot be accessed.

> Note The rotation of the CMEK will not impact data availability since the service keeps track of which CMEK version was used to encrypt the data and will use that version to decrypt it.

# CMEK compliance

Some services do not directly store data, or store data for only a brief period as an intermediate step in a long-running operation. For this type of workload, it is not practical to encrypt each separately. These services do not offer CMEK integrations, but can offer CMEK compliance, with no configuration on your part.

A CMEK-compliant service encrypts temporary data by using an ephemeral key that only exists in memory and is never written to disk. When the temporary data is no longer needed, the ephemeral key is flushed from memory, and the encrypted data cannot be accessed, even if the storage resource still exists.

A CMEK-compliant service might offer the ability to send its output to a service with a CMEK integration, such as Cloud Storage.

# Customer-supplied encryption key

You can provide your own AES-256 key, encoded in standard Base64, as an additional layer on top of Google-managed encryption keys. This key is known as a customer-supplied encryption key (CSEK).

The CSEK is currently supported by only two services: Cloud Storage and Compute Engine.