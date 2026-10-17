
1. Click the `Replicate Data Globally` button under `Settings` in the left-side panel of the Azure Cosmos DB blade.

2. From this page, you can add regions by either clicking on them in the world map or clicking `Add Region` and selecting one in the drop-down list. You can also choose to add a new write region using the `Add Region` button. [Figure 3.13](#c03.xhtml#c03-fig-0013) illustrates how to add a new write region replica.

![FIGURE 3.13 Adding a new write region replica](images/c03f013.png)

[FIGURE 3.13](#c03.xhtml#R_c03-fig-0013) Adding a new write region replica

### Configuring Consistency

The Azure Portal allows you to change the consistency level from the default session consistency to another. Simply click the `Default Consistency` button under `Settings` in the left-side panel and choose a new default consistency level.

If you choose the bounded staleness consistency level, you will be given the option to configure the maximum lag time and maximum lag operations. [Figure 3.14](#c03.xhtml#c03-fig-0014) illustrates how you can change the default consistency to bounded staleness through the `Default Consistency` page.

![FIGURE 3.14 Updating the default consistency to bounded staleness](images/c03f014.png)

[FIGURE 3.14](#c03.xhtml#R_c03-fig-0014) Updating the default consistency to bounded staleness

#### Azure PowerShell

Just as with relational databases in Azure, you can use Azure PowerShell to create and manage all components of Azure Cosmos DB. The following PowerShell script can be run on the Azure Cloud Shell or a PowerShell window to create a new Azure Cosmos DB account:

```
<# 
Sign into your Azure environment. Not required 
if running this script in the Azure Cloud Shell
#>
Connect-AzAccount
 
<#
Set the parameters needed to create the account 
such as the resource group name, account name, 
API type, consistency level, and replica locations
#>
$resourceGroupName = "dp900cosmos001"
$accountName = "dp900cosmos001"
$apiKind = "Sql"
$consistencyLevel = "Session"
$locations = @()
$locations += New-AzCosmosDBLocationObject `
-LocationName "East US" -FailoverPriority 0 -IsZoneRedundant 0
$locations += New-AzCosmosDBLocationObject `
-LocationName "West US" -FailoverPriority 1 -IsZoneRedundant 0
 
#Create the account
New-AzCosmosDBAccount `
    -ResourceGroupName $resourceGroupName `
    -LocationObject $locations `
    -Name $accountName `
    -ApiKind $apiKind `
    -EnableAutomaticFailover: $true `
    -DefaultConsistencyLevel $consistencyLevel
```

This script includes a few key parameters that are used to define the account:

*   `$resourceGroupName`—The resource group that the Azure Cosmos DB account is going to be deployed to. The resource group must already exist.

*   `$accountName`—The name for the account.

*   `$apiKind`—The Azure Cosmos DB API that will be used for the account.

*   `$consistencyLevel`—The default consistency level for the account.

*   `$locations`—The replica regions for the account. The region with `FailoverPriority` set to 0 is the write region.

Azure PowerShell can also be used to create an Azure Cosmos DB database and container. The following script is used to create a new database in the newly created account with 4000 RU/s, as well as a container with 400 RU/s:

```
$resourceGroupName = "dp900cosmos001"
$accountName = "dp900cosmos001"
$databaseName = "dp900cosmosdb01"
$containerName = "dp900cosmoscontainer01"
$partitionKey = "/Id"
$databaseThroughput = 4000
$containerThroughput = 400
 
New-AzCosmosDBSqlDatabase `
    -ResourceGroupName $resourceGroupName `
    -AccountName $accountName `
    -Name $databaseName `
    -Throughput $databaseThroughput
 
New-AzCosmosDBSqlContainer `
    -ResourceGroupName $resourceGroupName `
    -AccountName $accountName `
    -DatabaseName $databaseName `
    -Name $containerName `
    -PartitionKeyKind Hash `
    -PartitionKeyPath $partitionKeyPath `
    -Throughput $containerThroughput
```

More information about creating and managing Azure Cosmos DB objects with Azure PowerShell can be found at `https://docs.microsoft.com/en-us/azure/cosmos-db/sql/manage-with-powershell`.

#### Azure CLI

Azure CLI is an alternative to Azure PowerShell for creating and managing Azure Cosmos DB components via a scripting language. The following Azure CLI script can be run on the Azure Cloud Shell, in a PowerShell window, or in a command prompt to create a new Azure Cosmos DB account, database, and container. This script uses the same parameters as the Azure PowerShell script in the previous section:

```
resourceGroupName='dp900cosmos001'
accountName='dp900cosmos001'
databaseName='dp900cosmosdb01'
containerName='dp900cosmoscontainer01'
partitionKey='/Id'
dbThroughput=4000
containerThroughput=400
 
az cosmosdb create \
    -n $accountName \
    -g $resourceGroupName \
    --default-consistency-level Session \
    --locations regionName='West US 2' \
        failoverPriority=0 isZoneRedundant=False \
    --locations regionName='East US 2' 
        failoverPriority=1 isZoneRedundant=False \
 
az cosmosdb sql database create \
    -a $accountName \
    -g $resourceGroupName \
    -n $databaseName \
    --throughput $dbThroughput
 
az cosmosdb sql container create \
    -a $accountName -g $resourceGroupName \
    -d $databaseName -n $containerName \
    -p $partitionKey --throughput $containerThroughput
```

More information about creating and managing Azure Cosmos DB objects with Azure CLI can be found at `https://docs.microsoft.com/en-us/azure/cosmos-db/sql/manage-with-cli`.

#### ARM Template

As mentioned in [Chapter 2](#c02.xhtml), ARM templates can be used to define the resources and configuration requirements for Azure deployments. These templates can be used to automate new deployments of Azure Cosmos DB as well as configuration changes for Azure Cosmos DB in different development environments.

One example of an ARM template that creates an Azure Cosmos DB account, database, and container can be found at `https://docs.microsoft.com/en-us/azure/cosmos-db/sql/quick-create-template?tabs=CLI`. The script can be deployed by clicking the `Deploy To Azure` button in the link and entering the required parameters or by running the following Azure PowerShell script:

```
Connect-AzAccount
$resourceGroupName = "dp900cosmos001"
$location = "East US"
 
New-AzResourceGroup 
    -Name $resourceGroupName
    -Location $location
 
New-AzResourceGroupDeployment 
    -ResourceGroupName $resourceGroupName `
    -TemplateUri https://raw.githubusercontent.com/Azure
/azure-quickstart-templates/master/quickstarts
/microsoft.documentdb/cosmosdb-sql/azuredeploy.json
```

### Azure Cosmos DB Security

Data security for Azure Cosmos DB is implemented at multiple levels in Azure. Just as with data stored in a relational database in Azure, unauthorized access to Azure Cosmos DB is prevented using network isolation and identity management. Data stored in Azure Cosmos DB is also encrypted at rest and in transit to protect data from malicious activity. The following sections examine the methods Azure uses to secure data stored in Azure Cosmos DB in further detail.

#### Network Isolation

We briefly examined the two network isolation options for Azure Cosmos DB while going over how to deploy an account using the Azure Portal. These options include the following:

*   Using the Azure Cosmos DB firewall to set IP-based access controls that restrict communication to an approved set of IP addresses. This can be taken a step further by allowing access for entire subnets by enabling the Azure Cosmos DB service endpoint on them.

*   Assigning a private IP address from a VNet Azure Cosmos DB account with a private endpoint. This will restrict access to only applications that can communicate with the VNet that the private endpoint is associated with.
