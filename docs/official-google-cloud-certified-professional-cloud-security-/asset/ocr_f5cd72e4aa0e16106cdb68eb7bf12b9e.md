# Key management options

In this section, we will cover several aspects of key management that are either Google-managed or customer-managed. It is important to know which option is best suited to which scenario so that you can make the right decision for a given use case.

# Google Cloud's default encryption

Google Cloud stores all data encrypted at rest using a Google-managed default encryption key. The key is the AES-256 symmetric encryption key. There is no setup of keys or configuration required to turn on this; by default all users use this type of encryption. Google manages the keys and the rotation period of these keys. Google Cloud's default encryption is best suited for customers who do not have specific requirements related to compliance or regional requirements for cryptographic key material. It is simple to use and does not require additional configuration to create keys, hence there is no cost to use it.

# Customer-managed encryption keys (CMEKs)

Some customers of Google Cloud have stringent regulatory and compliance requirements to have control over the keys used to encrypt data at rest. To help with these requirements, Google Cloud offers the ability to encrypt data related to those services using an encryption key managed by the customer within Cloud KMS. CMEKs mean that the customer decides the key type (software versus hardware), algorithm strength, and key rotation period when creating a key in Cloud KMS.

CMEKs give you control over aspects of the key lifecycle, including (not limited to) the following:

+   * Customers can disable the keys used to safeguard data at rest, limiting Google's ability to decode
* Customers can protect their data by utilizing a key that is personal to their location
* Customers can rotate the keys used to protect the data either automatically or manually
* Customers can use a Cloud HSM, a Cloud External Key Manager (EKM), or an existing key that they import into Cloud KMS to protect their data

Customer-Managed Encryption Keys (CMEKs) are a supported feature in certain Google Cloud services. Let's explore what it entails for services for CMEK support.

# CMEK integrations

When a service supports CMEKs, it is said to have a CMEK integration. Some services, such as GKE, have multiple CMEK integrations for protecting several types of data related to the service.