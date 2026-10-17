

以下是一个 ARM 模板示例，用于创建 Azure SQL 数据库。模板定义包含以下元素：

*   逻辑服务器名称。
*   服务器管理员帐户的用户名和密码。
*   Azure SQL 数据库、其初始服务层级及其性能 SKU。

```
{
  "$schema": "https://schema.management.azure.com/schemas/2019–04–01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "serverName": {
      "type": "string",
      "defaultValue": "dp900sql001sv",
      "metadata": {
        "description": "The name of the SQL logical server."
      }
    },
    "sqlDBName": {
      "type": "string",
      "defaultValue": "dp900sql001db",
      "metadata": {
        "description": "The name of the SQL Database."
      }
    },
    "location": {
      "type": "string",
      "defaultValue": "eastus2",
      "metadata": {
        "description": "Location for all resources."
      }
    },
    "administratorLogin": {
      "type": "string",
      "metadata": {
        "description": "The administrator username of the SQL logical server."
      }
    },
    "administratorLoginPassword": {
      "type": "securestring",
      "metadata": {
        "description": "The administrator password of the SQL logical server."
      }
    }
  },
  "variables": {},
  "resources": [
    {
      "type": "Microsoft.Sql/servers",
      "apiVersion": "2020–02–02-preview",
      "name": "[parameters('serverName')]",
      "location": "[parameters('location')]",
      "properties": {
        "administratorLogin": "[parameters('administratorLogin')]",
        "administratorLoginPassword": "[parameters('administratorLoginPassword')]"
      },
      "resources": [
        {
          "type": "databases",
          "apiVersion": "2020–08–01-preview",
          "name": "[parameters('sqlDBName')]",
          "location": "[parameters('location')]",
          "sku": {
            "name": "GP_Gen5_2",
            "tier": "GeneralPurpose",
          },
          "dependsOn": [
            "[resourceId('Microsoft.Sql/servers', concat(parameters('serverName')))]"
          ]
        }
      ]
    }
  ]
}
```

然后可以通过 Azure 门户、Azure PowerShell 或 Azure CLI 部署此模板。以下是一个 Azure PowerShell 脚本示例，该脚本将前面的 ARM 模板部署到新资源组。它还定义逻辑服务器的管理员用户名和密码，并在部署模板时将信息传递给模板。此脚本还假设模板与 Azure PowerShell 脚本位于同一文件夹中，文件名为 `azuredeploy.json`。

```
Connect-AzAccount

# Set an admin login and password for your server
$adminSqlLogin = "dp900admin"
$password = "<Admin Password>"

New-AzResourceGroup -Name sql001 -Location eastus
New-AzResourceGroupDeployment -ResourceGroupName `
arm-vscode -TemplateFile ./azuredeploy.json `
-administratorLogin $adminSqlLogin `
-administratorLoginPassword $password
```

### 迁移到 Azure SQL

有多种方法可用于将数据库从本地 SQL Server 实例迁移到 Azure SQL。除非您正在从较旧版本的 SQL Server 升级并需要更新任何已弃用的功能，否则将数据库迁移到 Azure VM 上的 SQL Server 相对简单。以下迁移选项通常包括：

*   备份本地数据库并将其存储在 Azure Blob 存储中。使用 `RESTORE DATABASE FROM URL` 将数据库备份从 Azure Blob 存储还原到 Azure VM 上的 SQL Server。
*   如果本地实例是 Always On AG 中的主实例，请将 Azure VM 上的 SQL Server 添加为辅助实例。数据同步到 Azure VM 上的 SQL Server 后，执行故障转移，使 Azure VM 上的 SQL Server 成为新的主实例。
*   配置事务复制，使本地 SQL Server 实例为发布服务器，Azure VM 上的 SQL Server 为订阅服务器。数据复制到 Azure VM 上的 SQL Server 后，更新应用程序连接字符串并将用户指向 Azure 中的数据库。

由于本地 SQL Server 与 PaaS Azure SQL 之间存在兼容性差异，迁移到 Azure SQL 数据库或 Azure SQL MI 需要更多规划和考虑。尽管 Azure SQL MI 与本地 SQL Server 几乎 100% 兼容，但两者之间仍存在一些功能差异，可能会导致迁移问题。本地 MySQL 和 PostgreSQL 实例与 Azure Database for MySQL 和 Azure Database for PostgreSQL 之间的差异也是如此。这就是 Azure 数据库迁移服务等服务可以提供数据，使迁移规划过程更加容易的地方。

`Azure 数据库迁移服务 (DMS)` 是一项完全托管的服务，可用于发现任何潜在的兼容性问题，并在解决这些问题后迁移数据库。它使用 `数据迁移助手 (DMA)` 来检测兼容性问题，并提出如何解决这些问题的建议。DMA 也可用于迁移到 Azure VM 上的 SQL Server，方法是发现旧版 SQL Server 与 Azure VM 上较新版本之间的兼容性问题。DMA 可用于评估从 SQL Server 2005 到最新版本的各种 SQL Server 版本。解决任何兼容性问题后，可以使用 DMA 迁移数据库架构，以便使用 DMS 简化数据迁移。

DMS 可用于脱机和在线迁移。`脱机`迁移是指应用程序停机时间从迁移开始时即开始。应用程序切换是手动过程，必须由用户执行。脱机迁移适用于迁移到 Azure SQL 数据库、Azure SQL MI、Azure VM 上的 SQL Server、Azure Cosmos DB、Azure Database for MySQL 和 Azure Database for PostgreSQL。DMS 还可以通过 `在线`迁移处理应用程序切换过程来限制停机时间。在线迁移仅适用于迁移到 Azure SQL MI、Azure Cosmos DB 和 Azure Database for PostgreSQL。

### 数据库安全

数据库安全对任何 RDBMS 都至关重要。出于此原因，Azure 中的关系数据库通过以下方法强制实施数据库安全：

*   网络隔离
*   访问管理
*   数据加密和混淆
*   安全管理

这些方法中的每一种都代表了保护数据免受未经授权访问的不同安全级别。虽然与不同安全层相关的许多任务在 Azure 中的不同关系数据库产品上以相同的方式应用，但有些任务在不同数据库平台之间处理方式不同。例如，网络隔离在 Azure VM 上的 SQL Server 上的实现方式与在 Azure SQL 数据库上的实现方式非常不同。

由于网络隔离是详细介绍 Azure 中不同关系数据库产品的章节中的核心主题，以下部分将重点介绍访问管理、数据加密和混淆以及安全管理功能。

#### 访问管理

