
This tab also allows you to configure access from trusted Azure services and read access to storage logging and metrics from any network. There is also an option to determine whether traffic is routed over the Microsoft network or the Internet as it travels from the source application to the storage account's public endpoint. These settings are illustrated in [Figure 4.18](#c04.xhtml#c04-fig-0018).

![FIGURE 4.17 Virtual Network and Firewall Access](images/c04f017.png)

[FIGURE 4.17](#c04.xhtml#R_c04-fig-0017) Virtual Network and Firewall Access

![FIGURE 4.18 Exceptions and Networking Routing](images/c04f018.png)

[FIGURE 4.18](#c04.xhtml#R_c04-fig-0018) Exceptions and Networking Routing

1. If you click the `Private Endpoint Connections` tab, you will be able create a new private endpoint that will have its very own private IP address from a VNet. This will restrict storage account access to traffic that can communicate with that VNet.

## Access Management

Azure Storage requires that every application interacting with a storage account has the appropriate authorization permissions. The only exception to this rule is when anonymous read access for containers or blobs is configured. Azure allows organizations to use either one of or a combination of the following authorization methods to provide storage account access:

* `Storage account access keys`

* `Shared access signatures (SAS)`

* `Azure AD Integration`

* `AD Domain Services (AD DS) for Azure Files`

* `Access control lists (ACLs) for ADLS`

The following sections examine each of these options in further detail.

### Storage Account Access Keys

Storage accounts natively include two access keys that can be used to authorize access to blob, file, queue, and table storage services. These keys can be regenerated at any point in time and can be kept in a secure location like Azure Key Vault. They can be found by clicking on the `Access keys` button on the left side of the storage account blade for a storage account.

Access keys can be used in the authorization header for any REST API call to provide storage access. Instead of assigning an access key to an authorization header, users can choose to use one of the predefined connection strings that are available in the access keys page to authorize their application requests.

While access keys are an available authorization option for storage accounts, it is recommended to use Azure AD credentials instead. Access keys provide shared authorization to multiple storage services, which can provide more access than what is needed. Azure AD can be used to provide more granular permissions to specific storage services such as blob containers and file shares. For this reason, Azure provides administrators with the option to block storage account requests that use an access key. This can be done by clicking the `Configuration` button (under Settings) on the left side of the storage account blade for your storage account and clicking `Disabled` under the Allow Storage Account Key Access setting.

### Shared Access Signature (SAS)

A shared access signature (SAS) delegates access permissions to specific storage account resources over a predetermined period of time. A SAS provides more granular access than an account key, as they allow administrators to restrict what resources a client application can access and what permissions it has on those resources.

Administrators can create a SAS using the Azure Portal, Azure PowerShell, Azure CLI, or the Azure Storage client library for .NET. Creating a SAS results in one or more signed URLs that point to each storage service that the SAS was provided access to. The URL includes a token that indicates what permissions client applications are authorized to use with the SAS.

To create a SAS in the Azure Portal, click on the `Shared Access Signature` button on the left side of the storage account blade for your storage account. [Figure 4.19](#c04.xhtml#c04-fig-0019) illustrates the configuration options on the shared access signature page.

![FIGURE 4.19 Shared access signature configuration options](images/c04f019.png)

[FIGURE 4.19](#c04.xhtml#R_c04-fig-0019) Shared access signature configuration options

The following list describes each configuration option on this page:

* `Allowed services` defines which storage services the SAS can access. Options include blob, file, queue, and table storage.

* `Allowed resource types` sets the access granularity for the SAS. For example, setting the allowed resource type scope to Service will enable access to the entire blob, file, queue, or table service. Setting the Object resource type scope will limit access to data objects stored in a storage service. Options include service, container, and object types.

* `Allowed permissions` defines what permissions the SAS is authorized to perform. Options include read, write, delete, list, add, create, update, process, and immutable storage.

* `Blob versioning permissions` sets whether the SAS can delete blob versions if versioning is enabled.

* `Allowed blob index permissions` defines what permissions the SAS is authorized to perform on blob indexes. Options include read/write and filter.

* `Start and expiry date/time` defines how long the SAS is valid.

* `Allowed IP addresses` restricts access to one IP address or a range of IP address. Leaving this option empty will allow any IP address to communicate with the storage account via the SAS.

* `Allowed protocols` sets the protocols permitted for a request using the SAS. By default, this option is set to HTTPS only, but it can be changed to allow HTTPS and HTTP connections. It is recommended to only allow HTTPS connections.

Click the `Generate SAS And Connection String` button at the bottom of the page to generate the SAS token as well as the connection strings and SAS URLs for each of the selected storage services.

As with access keys, it is recommended to use Azure AD credentials instead of a SAS. The same process that blocks requests made with an access key also blocks requests that use a SAS.

### Azure AD Integration

Azure AD is a supported identity management service for Azure Storage services. Administrators can assign storage access permissions to Azure AD users, groups, and applications with Azure RBAC roles. These roles can be used to grant access permissions to Azure AD identities at the following storage levels:

* `The storage account level`—Azure AD identities that are scoped to a storage account are propagated with their delegated permissions to all resource objects hosted in the storage account.

* The resource level—This includes any resource that may be hosted by a storage account, such as a blob container or a file share. An Azure AD identity scoped to a resource can interact with that resource's data, granted the action the identity is trying to perform is allowed by the permissions assigned to it.

Identities can be set using a variety of methods such as through the Azure Portal, Azure PowerShell, and Azure CLI. To add identities through the Azure Portal, click the `Access Control (IAM)` button in the left-side panel of the resource you want to add the identity to. Click the `Add` button on the Access Control (IAM) page and start adding role assignments to identities. Along with generic RBAC roles such as `Owner`, `Contributor`, and `Reader` that will grant administrative access to the object, Azure Storage services have built-in roles that grant resource-specific permissions. The following is a list of roles specific to Azure Storage that are relevant to the DP-900 exam:

* `Storage Blob Data Owner`—Identities assigned this role have full access to blob containers and data. It can also be used to assign ACLs to ADLS folders. This role applies to Azure Blob Storage and ADLS.
