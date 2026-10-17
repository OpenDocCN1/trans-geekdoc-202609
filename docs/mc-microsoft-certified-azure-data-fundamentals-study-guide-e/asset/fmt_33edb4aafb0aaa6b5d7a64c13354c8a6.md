
6.  The `Data Protection` tab allows you to protect data from accidental deletes or modifications, enable version management, and set time-based retention policies for blob versions. [Figure 4.5](#c04.xhtml#c04-fig-0005) illustrates an example of the data protection settings with the default options.

    ![FIGURE 4.5 Create a Storage Account: Data Protection tab.](images/c04f005.png)

    [FIGURE 4.5](#c04.xhtml#R_c04-fig-0005) Create a Storage Account: Data Protection tab.

7.  The `Tags` tab allows you to place a tag on the storage account for cost management.

8.  Finally, the `Review + Create` tab allows you to review the configuration choices made during the design process. If you are satisfied with the choices made for the instance, click the `Create` button to begin provisioning the storage account.

### Azure Storage Services

The DP-900 exam covers Azure Files, Azure Blob storage, ADLS, and Azure Table storage. Because Azure Table storage was covered in [Chapter 3](#c03.xhtml), the following sections will focus on Azure Files, Azure Blob storage, and ADLS.

#### Azure Files

Azure Files is a storage service that allows organizations to build fully managed file shares in Azure. File shares deployed through Azure Files can be accessed using the SMB protocol on standard and premium storage accounts or the NFS protocol on premium storage accounts. The service organizes data in a hierarchical folder structure and is typically used to replace or complement on-premises file shares. Along with the benefits that are native to Azure storage accounts such as offloading hardware management and global redundancy, data stored in an Azure file share can be accessed from anywhere in the world.

File shares created in Azure Files can be mounted concurrently to a VM in the cloud or on a user's local machine for access. SMB file shares can be mounted to Windows, Linux, or macOS devices. NFS file shares are limited to Linux and macOS devices. In addition to being accessible as a mounted drive, SMB file shares can be synchronized between Azure Files and a local share on a Windows Server device using `Azure File Sync`. This service allows organizations to cache frequently accessed data on the local file share while leaving the least accessed data in Azure.

##### Access Tiers

Azure Files offers four storage tiers to meet the performance and price requirements of different workloads:

*   `Premium` file shares use SSDs for storage, providing high performance and low latency for IO-intensive workloads. This tier is only available in premium storage accounts.

*   `Transaction optimized` file shares use standard HDDs for storage, enabling transaction-heavy workloads that do not need the low latency that premium file shares provide. This tier is available in standard storage accounts.

*   `Hot` file shares use standard HDDs for storage and are optimized for general-purpose file-sharing scenarios. This tier is available in standard storage accounts.

*   `Cool` file shares use standard HDDs for storage and offer cost-efficient storage that is optimized for archive storage scenarios. This tier is available in standard storage accounts.

The premium storage tier is the only tier that users can access via SMB and NFS protocols. Transaction optimized, hot, and cool tiers are only offered in standard storage accounts and do not support the NFS protocol as of this writing.

File shares created on a standard storage account switch between the transaction optimized, hot, and cool tiers without needing to move to a different storage account. Moving from one of the standard storage account tiers to the premium tier will require you to create a new premium storage account and copy the data from the old file share to the new one. The data can be copied from the old share to the new one using the `AzCopy` utility that is described later in this chapter.

More information about the different storage tiers available for Azure Files can be found at `https://docs.microsoft.com/en-us/azure/storage/files/storage-files-planning#storage-tiers`.

##### Creating a File Share

File shares in Azure can be created through the Azure Portal, a REST API call, an Azure PowerShell or Azure CLI script, or as a part of an Infrastructure as Code template. The Azure Files client library can be used in custom .NET, Java, C++, or Python applications to manipulate file shares. The following steps describe how to create a file share in the Azure Portal.

1.  Navigate to the storage accounts page in the Azure Portal and click on the storage account that was previously created.

2.  In the left-side panel of the storage account blade, click `File shares`. [Figure 4.6](#c04.xhtml#c04-fig-0006) shows where this button is located.

    ![FIGURE 4.6 File shares button](images/c04f006.png)

    [FIGURE 4.6](#c04.xhtml#R_c04-fig-0006) File shares button

3.  Click the `+ File Share` button at the top of the file shares blade to configure a new file share. [Figure 4.7](#c04.xhtml#c04-fig-0007) shows what this button looks like and where at the top of the page it is located.

    ![FIGURE 4.7 Create a New File Share button.](images/c04f007.png)

    [FIGURE 4.7](#c04.xhtml#R_c04-fig-0007) Create a New File Share button.

4.  Enter a name and select an access tier for the new file share. [Figure 4.8](#c04.xhtml#c04-fig-0008) illustrates a completed example of this page.

    ![FIGURE 4.8 New file share](images/c04f008.png)

    [FIGURE 4.8](#c04.xhtml#R_c04-fig-0008) New file share

5.  Click `Create` to create the file share.

##### Mounting a File Share

One of the biggest advantages of using an Azure file share is that they can be mounted to any computer in the world. However, there are some considerations that need to be made:

*   If you are connecting via SMB, then the OS of the computer that the file share is being mounted to must support SMB 3.0 and higher.

*   Ensure that TCP port 445 is open if you are connecting via SMB and using the file share's public endpoint. This is the port that the SMB protocol uses for communication.

*   As of this writing, mounting an NFS file share using its public endpoint is restricted to VMs inside of Azure.

Many organizations do not allow public endpoint access and block TCP port 445 for security reasons. In these scenarios, organizations can establish a secure network tunnel between an Azure VNet and their on-premises network using a VPN or ExpressRoute connection. This allows them to attach a private IP address, or private endpoint, from the VNet to the storage account hosting the file share. Using the private endpoint allows users to access the file share using a secure network connection without needing to open TCP port 445. More information about securely accessing an Azure file share can be found at `https://docs.microsoft.com/en-us/azure/storage/files/storage-files-networking-overview#accessing-your-azure-file-shares`.

The Azure Portal provides scripts that will mount a file share to a machine using a compatible OS. The following steps describe how to access these scripts:

1.  Navigate to the storage accounts page in the Azure Portal and click on the storage account that was previously created.

2.  In the left-side panel of the storage account blade, click `File Shares`.

3.  Click on the file share that was previously created.

4.  Click the `Connect` button at the top of the page. [Figure 4.9](#c04.xhtml#c04-fig-0009) shows what this button looks like and where at the top of the page it is located.

    ![FIGURE 4.9 Connect button](images/c04f009.png)

    [FIGURE 4.9](#c04.xhtml#R_c04-fig-0009) Connect button

5.  In the Connect pop-up page, choose the OS you will be mounting the file share to. This example will use the Windows option.

6.  Choose the drive letter that the mounted file share will use and the authentication method. The example will use `Z` as the drive letter and `Storage account key` for the authentication method.
