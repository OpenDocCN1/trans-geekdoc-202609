
There are several management activities that administrators and developers must consider when working with Azure Storage. For one, users will need to decide how they will design their Azure Storage deployments to be reusable across multiple environments. Administrators will also need to decide how to secure their storage accounts, as well as how they will provide/restrict access to the different storage services that are created in the account. The following sections will discuss common methods used to perform these tasks as well as the tools users can utilize to manage their storage accounts.

## Deployment Scripting and Automation

Automated resource deployments are standard for any multi-environment workload that uses cloud resources. As with any Azure resource, Azure Storage deployments can be scripted using a variety of methods including Azure PowerShell, Azure CLI, and Infrastructure as Code templates. Azure PowerShell and Azure CLI are also common tools that can be used to manage data stored in Azure Storage. The following sections examine how to use Azure PowerShell, Azure CLI, and ARM templates to deploy Azure Storage resources.

### Azure PowerShell

Users can easily write Azure PowerShell scripts that will deploy and manage Azure Storage resources. The following is an example of a script that will create a standard general-purpose v2 storage account:

```
<# Sign into your Azure environment. Not required 
if running this script in the Azure Cloud Shell #>
Connect-AzAccount

$resourceGroupName = "dp900storageacct001"
$storageAccountName = "dp900stracct001"
$location = "East US"

New-AzStorageAccount -ResourceGroupName $resourceGroup `
  -Name $storageAccountName `
  -Location $location `
  -SkuName Standard_RAGRS `
  -Kind StorageV2
```

The next step after creating the storage account and setting security postures is to begin creating file shares and/or blob containers. The following script creates a new blob container in the previously created storage account:

```
$resourceGroupName = "dp900storageacct001"
$storageAccountName = "dp900stracct001"
$containerName = "dp900container01"


# Retrieve an existing Storage Account reference
$storageContext = Get-AzStorageAccount -ResourceGroupName $resourceGroupName `
    -Name $storageAccountName

# Create the container
New-AzStorageContainer -Name $containerName `
    -Context $storageContext `
```

Once the container is created, you can start uploading data to it using the `Set-AzStorageBlobContent` Azure PowerShell command. The following script demonstrates how to use this command to upload an image stored on a local directory to the container. It also configures the blob to use the hot access tier for quick access.

```
$resourceGroupName = "dp900storageacct001"
$storageAccountName = "dp900stracct001"
$containerName = "dp900container01"


# Retrieve an existing Storage Account reference
$storageAccount = Get-AzStorageAccount -ResourceGroupName $resourceGroupName `
    -Name $storageAccountName

# Get the Storage Account context
$storageContext = $storageAccount.Context

# Upload a file to the Hot access tier
Set-AzStorageBlobContent -File "D:\Images\Image001.jpg" `
  -Container $containerName `
  -Blob "Image001.jpg" `
  -Context $storageContext `
  -StandardBlobTier Hot
```

The script can be modified to upload several files by looping through the local directory. More information about creating and managing Azure Blob storage resources with Azure PowerShell can be found at `https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-powershell`.

### Azure CLI

Azure CLI is another scripting environment that administrators can use to create and manage Azure Storage resources. The following Azure CLI script uses the same parameters as the Azure PowerShell script in the previous section to create a storage account and a blob container:

```
resourceGroupName='dp900storageacct001'
storageAccountName='dp900stracct001'
containerName='dp900container01'
location='eastus'

az storage account create \
  --name $storageAccountName \
  --resource-group $resourceGroupName \
  --location $location \
  --sku Standard_RAGRS \
  --kind StorageV2

az storage container create \
    --account-name $storageAccountName \
    --name $containerName \
```

More information about creating and managing Azure Blob storage resources with Azure CLI can be found at `https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-cli`.

### ARM Template

Like other Azure services, Infrastructure as Code templates such as Azure Resource Manager (ARM) templates are the most optimal way to define resources for Azure Storage deployments. These templates can be used to quickly build Azure Storage services in multiple development environments, allowing developers to easily build and test new functionality.

One example of an ARM template that creates a standard storage account can be found at `https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.storage/storage-account-create`. The template can be deployed using the following Azure PowerShell:

```
Connect-AzAccount
 $resourceGroupName = "dp900storageacct001"
 $location = "East US"
  
 New-AzResourceGroup 
     -Name $resourceGroupName
     -Location $location
  
 New-AzResourceGroupDeployment 
     -ResourceGroupName $resourceGroupName `
     -TemplateUri https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/quickstarts/microsoft.storage/storage-account-create
 /azuredeploy.json
 
```

## Azure Storage Security

Microsoft provides several layers of security to ensure that data stored in one of the Azure Storage services is protected from unauthorized access. As with any other data service in Azure, there are several network isolation and identity management options that can be used to limit who can access data in a storage account. The following sections examine the methods available for securing data in Azure Storage as well as some of the default security standards such as data encryption and protection from accidental deletes.

### Network Isolation

Storage accounts have a public endpoint that provides access over the Internet. Azure allows users to isolate this endpoint by limiting access to certain IP addresses through a firewall, trusted Azure services, or specific Azure subnets. Azure also allows users to attach a private IP address from a VNet to a storage account, restricting communication to traffic that can access the VNet. This is the Microsoft recommended approach for securing storage accounts that store sensitive data such as personally identifiable information (PII).

All these options can be configured through the Azure Portal, or an Azure PowerShell or Azure CLI script after a storage account is created. Let's walk through how to configure one of the network isolation options in the Azure Portal:

1. Navigate to the storage accounts page in the Azure Portal and click on the storage account that was previously created.

2. In the left-side panel of the storage account blade, click `Networking`. [Figure 4.16](#c04.xhtml#c04-fig-0016) shows where this button is located.

    ![FIGURE 4.16 Networking button](images/c04f016.png)

    [FIGURE 4.16](#c04.xhtml#R_c04-fig-0016) Networking button

3. There are three tabs listed at the top of the networking page: Firewalls And Virtual Networks, Private Endpoint Connections, and Custom Domain. We will cover the Firewalls And Virtual Networks and Private Endpoint Connections tabs for the purpose of configuring network isolation on a storage account. Just know that the Custom Domain tab allows you to map a custom domain to a blob or static website endpoint.

4. The Firewalls And Virtual Networks tab enables users to allow access from specific VNets and subnets as well as specific IP addresses. [Figure 4.17](#c04.xhtml#c04-fig-0017) illustrates these settings.
