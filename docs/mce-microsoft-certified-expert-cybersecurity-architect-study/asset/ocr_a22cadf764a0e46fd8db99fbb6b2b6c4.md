# Use a Site-to-Site VPN

Best practice: On-premises workstations must have secure access to Azure virtual networks. To provide secure communication between the end user or admin workstation to Azure secure virtual network need to be designed and deployed, aligning with organization requirements and standards.

# Use a Point-to-Site VPN

These are the best practices:

+   Best practice: Use high-speed WAN links for larger datasets. To provide additional protection, you can use ExpressRoute with SSL/TLS or another protocol to encrypt data at the application level.

+   Best practice: Use the Azure Portal to interact with Azure Storage. To interact with Azure Storage, use the Storage REST API over HTTPS. All transactions occur over HTTPS.

# Key Management with Key Vault

A cloud service can function effectively only if its encryption keys are adequately protected and managed. Key Vault is Microsoft's recommended way of working and controlling access to encryption keys. Azure Active Directory accounts can be used to assign permissions to services or users to access keys. HSMs and key management software no longer need to be configured, patched, and maintained with Key Vault.

Azure Key Vault helps solve the following problems:

+   Secrets Management: Azure Key Vault allows token storage, password storage, certificate storage, and API keys management in a secure and tightly controlled way.

+   Key Management: Key Management can be accomplished using Azure Key Vault. With Azure Key Vault, you can easily manage and create encryption keys.

+   Certificate Management: Azure Key Vault makes it easy to provision, manage, and deploy TLS/SSL certificates for Azure and your internal connected resources.

![](bbox=[0.136, 0.712, 0.22, 0.775])

Azure supports a variety of encryption models, including server-side encryption using service-managed keys, customer-managed keys in Key Vault, and customer-managed keys on customer-controlled hardware. Client-side encryption is performed outside of Azure.

From the SC-100 exam standpoint, remember that to prevent out-of-band attacks (such as accessing underlying storage), Microsoft Defender for Cloud Apps encrypts data at rest.