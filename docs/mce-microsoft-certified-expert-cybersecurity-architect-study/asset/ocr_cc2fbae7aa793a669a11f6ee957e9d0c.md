One example of a nonregional service is Azure Active Directory (Azure AD). In other words, Azure AD may store identity data globally, except for Azure AD deployments in the United States, Europe, Australia, and New Zealand.

When a disaster occurs, Azure Backup keeps your data safe and recoverable. Using the Microsoft Azure Recovery Services (MARS) agent, you can back up files, folders, and desired system state and backups of entire Windows/Linux VMs (using backup extensions). Azure Files shares, SQL Server VMs running on Azure VMs, and SAP HANA databases running on Azure VMs can also be backed up.

Azure Backup, Azure Data Factory, Azure Site Recovery, Azure Stream Analytics, and locally redundant storage (LRS) are among the Azure services, tiers, and plans that can store customer data only in one region.

# Protecting Organizational Data

A Microsoft Cybersecurity Architect can protect organizational data from unauthorized access. A key component of ensuring the confidentiality of cloud workloads is encryption. Multiple encryption methods, protocols, and algorithms are used across Microsoft's products and services to deliver a secure path for data to travel via the Azure infrastructure and to ensure the confidentiality of data stored within it. To protect its customers' data, Microsoft uses some of the strongest encryption protocols in the industry.

As part of Azure, customers can also manage and control the security of their data, including encryption data at rest, in transit, and during processing. Managing encryption keys properly is essential to best encryption practices, and Azure Key Vault helps secure encryption keys. Azure, the customer in Key Vault, or the customer on-premises can manage and store encryption keys.

A key management strategy can include server-side keys managed by Azure services or client-side encryption where Azure does not have access to encryption keys.

# Encryption of Data at Rest

Whenever customer data is written to Azure Storage, including azure managed disks, azure blobs, queues, and table storage, it is automatically encrypted. As well as being compliant with FIPS 140-2, Azure storage data is encrypted with 256-bit AES encryption.

Azure offers several options for encrypting OS and data disks for Windows Server and Linux instances (VMSSs).

For infrastructure as a service (IaaS) virtual machine disks, Azure Disk Encryption provides full-volume encryption based on BitLocker on Windows and DM-Crypt on Linux. An Azure Key Vault is required to manage and control disk encryption keys and secrets.

As part of BitLocker, Windows Server 2016 Shielded VMs are encrypted to prevent restricted administrators from accessing information inside the virtual machine. The key vault and VMs must be located in the same region and subscription. As part of the Shielded VMs solution, the Host Guardian Service certifies virtualization hosts and releases encryption keys.