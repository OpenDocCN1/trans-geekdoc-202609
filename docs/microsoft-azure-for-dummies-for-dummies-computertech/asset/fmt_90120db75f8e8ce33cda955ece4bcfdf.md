
*   The **Redeploy** button (C) is useful if a deployment fails; you can fix the errors in the ARM template and pick up the deployment where it left off. This important ARM characteristic is called *idempotence*.

*   You can open the resource group associated with the deployment (D) and navigate to the **Deployments** setting to review this and other deployments, download template definitions, and so forth.

*   This list of granular deployment operations (E) is tremendously useful for troubleshooting failed deployments.

### Using the blob service

Although general-purpose storage accounts have four discrete services intended for different data and object types, most of this chapter focuses on the blob service.

The reason for my choice is twofold:

*   This is a beginner’s book, and the other three services are intended for a more advanced audience.

*   The blob service is the most frequently used Azure storage account service.

#### Installing Azure Storage Explorer

Azure Storage Explorer is a free, closed-source, cross-platform desktop application that enables you to interact with your Azure storage accounts.

Go to [`https://azure.microsoft.com/en-us/features/storage-explorer`](https://azure.microsoft.com/en-us/features/storage-explorer/) (or search for *Azure Storage Explorer* in your favorite search engine), download the program, and install it on your computer. Follow these steps to configure Storage Explorer:

1.  **In the Connect to Azure Storage dialog box, select Add an Azure Account, set the Azure environment to Azure, and then click Next.**

    If the dialog box doesn’t appear the first time you start Storage Explorer, click the **Add Account** button on the Storage Explorer sidebar. (The button’s icon looks like an electrical plug.)

2.  **Authenticate to Azure, using your administrative account.**

3.  **In the Show Resources from These Subscriptions filter, ensure your target Azure subscription is selected, and click Apply.**

    I manage multiple subscriptions, so I like to focus only on the one(s) I’m working with.

[Figure 3-4](#c03.xhtml#c03-fig-0004) shows Storage Explorer and the following features:

*   Click the **Explorer** button (A) to browse your storage account(s).

*   Click the **Manage Accounts** button (B) to filter the subscriptions that Storage Explorer shows in Explorer view.

*   Click the **Add Account** button (C) to sign in with more than one Azure AD account simultaneously.

*   Expand general-purpose storage accounts to see their services (D). The navigation works like a File Transfer Protocol client application.

*   View the properties of the current selection (E). By default, storage accounts use the following public endpoints for each service:

    *   Blob service: `https://<storage-acct-name>.blob.core.windows.net/`

    *   File service: `https://<storage-acct-name>.file.core.windows.net/`

    *   Queue service: `https://<storage-acct-name>.queue.core.windows.net/`

    *   Table service: `https://<storage-acct-name>.table.core.windows.net/`

*   Each service has its own toolbar (F). The blob service toolbar shown in [Figure 3-4](#c03.xhtml#c03-fig-0004) is used for containers and file uploads/downloads, whereas the table service toolbar is used for data import/export and queries.

*   This pane (G) gives you granular interaction with your storage account.

*   The **Activities** pane (H) shows error, warning, and information messages from Storage Explorer.

![FIGURE 3-4: Azure Storage Explorer.](images/9781119612148-fg0304.png)

[FIGURE 3-4:](#c03.xhtml#rc03-fig-0004) Azure Storage Explorer.

![Tip](images/tip.png)Storage Explorer is also available in the Azure portal. Browse to your storage account, and select the **Storage Explorer** setting.

#### Uploading blobs

Now it's time to create a blob container and upload some files to Azure. Follow these steps:

1.  **Expand your storage account, right-click the Blob Container node, and choose Create Blob Container from the shortcut menu.**

    An intuitive name for the container is `files`. A container functions like a directory in a computer’s file system.

2.  **Select the `files` container, and click **Upload** on the Storage Account toolbar.**

    You could drag and drop files into the container, but I’m intentionally being more … er, intentional in my instruction.

3.  **Add one or more files to your new container.**

    You can perform a file upload directly in the Azure portal. Navigate to the **Containers** blade, click into your new container, and then click **Upload** from the toolbar. You can then browse your computer for files and add them to Azure blob storage.

It’s a good habit to right-click blobs in Storage Explorer to access handy administrative options from the shortcut menu, including downloading the object and changing its access tier. [Figure 3-5](#c03.xhtml#c03-fig-0005) shows the shortcut menu you see when you right-click a blob.

![FIGURE 3-5: Try right-clicking everything in Azure Storage Explorer to see what options are available.](images/9781119612148-fg0305.png)

[FIGURE 3-5:](#c03.xhtml#rc03-fig-0005) Try right-clicking everything in Azure Storage Explorer to see what options are available.

![Tip](images/tip.png)Practice working with blob upload, download, and deletion by using keyboard shortcuts (which you can find at [`https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-accessibility#shortcut-keys`](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-accessibility#shortcut-keys)) as well as Storage Explorer’s menu and toolbar system. Make sure that you practice with test files and not production resources, however.

#### Changing blob access tiers

This section returns to the Azure portal so that you can modify a blob object’s access tier. First, it’s instructive to understand how Microsoft prices standard-tier storage accounts. You’re charged for

*   **Storage volume:** Storage volume represents the amount of data in your blob service.

*   **REST API transactions:** Every time you interact with the blob service, that interaction translates into a read, write, update, or delete REST API call, and Microsoft charges you for each call.

*   **Data egress network traffic:** There’s no charge for ingress (upload or inbound) traffic into the storage account, but you pay for egress (download or outbound) data transfer.

Depending on the pricing scheme, it may make sense for you to change the access tier for blobs that have different use scenarios. You have three tier options:

*   **Hot tier:** Optimized for frequently accessed data. You get a discount on transaction pricing.

*   **Cool tier:** Optimized for infrequently accessed data to be stored for at least 30 days. You get a discount on storage footprint.

*   **Archive tier:** Optimized for rarely accessed data (180 days or more). You get a discount on both storage footprint and transaction costs.

To modify the access tier for one of the blobs you uploaded into your `files` blob container, follow these steps:

1.  **In the Azure portal, locate your storage account, and select the **Containers** setting.**

    You’ll find some inconsistencies in the Azure portal and Azure documentation. The storage account **Blobs** service is also called **Containers**; if Microsoft changed the service name to **Containers** by the time you’re reading this, you'll know why.

2.  **Browse to the `files` container, select one of your blobs, and click **Change Tier** from the toolbar.**

    When you select a blob, Azure shows you all the blob’s metadata.

3.  **From the **Access Tier** drop-down menu, choose **Archive**, and then click **Save** to confirm your changes.**

    I show you the interface in [Figure 3-6](#c03.xhtml#c03-fig-0006). The Azure portal should display a message informing you that marking the blob as **Archive** makes it inaccessible until you explicitly return it to the **Hot** or **Cool** tier.
