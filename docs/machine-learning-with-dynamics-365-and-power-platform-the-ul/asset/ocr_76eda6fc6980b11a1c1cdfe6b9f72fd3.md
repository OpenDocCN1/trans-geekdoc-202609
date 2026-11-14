+   - YAML. A machine-readable alternative to JSON.
+   - Table. ASCII table with keys as column headings.
+   - TSV. Tab-separated values with no keys.
+   - None. No output other than errors and warnings.

+   - Querying with JMESPath. JSON has a query language called JMESPath that enables you to select and modify data from CLI output. All commands in the Azure CLI supports query argument to execute a JMESPath query.

+   - Cross-platform. Azure CLI is written in Python language, which means it is cross-platform and works on Windows, macOS, and Linux.

Some common commands that are used in CLI include:

+   - az – CLI starting point.
+     - az login – login to your Azure account
+     - az account – manage the account
+     - az groups – manage resource groups
+     - az VM – virtual machines
+     - az storage account – storage accounts
+     - az Keyvault – key vault
+     - az webapp – web applications
+     - az sql server – SQL databases
+     - az cosmosdb – CosmosDB

+   - Globally available commands.

**Help.** This command displays reference information about the commands you display it with. It also displays related arguments and lists available subgroups and commands. For example, az group -h or az group -help will display all the groups, subgroups, and commands that might help you to write next command and get what you need.