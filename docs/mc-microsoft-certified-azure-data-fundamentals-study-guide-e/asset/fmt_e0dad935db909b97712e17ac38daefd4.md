
## 4. The Explorer page will list all of the storage accounts and storage resources in the selected subscription(s)

[Figure 4.24](#c04.xhtml#c04-fig-0024) illustrates how the previously created blob container and file share is listed in Azure Storage Explorer.

![FIGURE 4.24 Storage account display](images/c04f024.png)

[FIGURE 4.24](#c04.xhtml#R_c04-fig-0024) Storage account display

When you click on a blob container or a file share, the main pane will display all of its contents as well as options to upload new items and create a new subfolder. Click on the previously created blob container and click the `Upload` button in the top ribbon. Click `Upload Files` to upload one or more data files. The Upload Files pop-up page allows you to select the files you want to upload, the blob type, and the access tier for the blob. [Figure 4.25](#c04.xhtml#c04-fig-0025) shows an example of this page uploading a block blob with the hot access tier.

Once it's uploaded, you will be able to manipulate the data with several options in the top ribbon and by right-clicking the blob.

### Azure Data Factory

Azure Data Factory is a PaaS ETL technology that can be used to orchestrate data movement and data transformation activities. With the Azure Data Factory's native data store connectors, users can quickly build connections to on-premises and cloud data stores. Developers can then use those established connections, called `Linked Services`, to build datasets that are used in Azure Data Factory pipelines. Pipelines consist of activities that process datasets, storing them in formats that can be used by data science and reporting applications.

One of the core components of Azure Data Factory is its `Copy Data` activity. Developers can use this activity to move large amounts of data from on-premises and cloud data stores to a central data repository in Azure Storage. The Copy activity is typically the first step used in an Azure Data Factory ETL pipeline, consolidating raw, source data in a single ADLS account. This activity is also used to migrate binary objects such as videos, images, and audio files to Azure Blob Storage.

![FIGURE 4.25 Upload Files pop-up page](images/c04f025.png)

[FIGURE 4.25](#c04.xhtml#R_c04-fig-0025) Upload Files pop-up page

Creating Azure Data Factory resources such as linked services, datasets, pipelines, and pipeline activities is covered in further detail in [Chapter 5](#c05.xhtml), “Modern Data Warehouses in Azure.”

### Azure Data Box

For some organizations, using a programmatic approach to migrating data from an on-premises appliance to Azure can take longer than what is acceptable. Microsoft can support organizations facing this issue with Azure Data Box. `Azure Data Box` is a physical device that lets organizations send large amounts of data to Azure very quickly. It is typically used to migrate datasets that are larger than 40 TBs in scenarios with limited or no network connectivity. Azure Data Box is used in the following scenarios:

*   Moving large amounts of media data such as videos, images, and audio files to Azure
*   Migrating several VMs to Azure at once
*   Migrating large amounts of historical data that is used by distributed analytics solutions

Azure Data Box can also be used to export data from Azure Storage to an on-premises datacenter.

The following steps describe the workflow used to migrate data to Azure with Azure Data Box:

1. Order the device through the Azure Portal. Provide shipping information and the destination Azure storage account for the data.
2. Once the device is delivered, connect the device to your network using a wired connection. Make sure the computer from which you will be copying the data has access to the data.
3. Copy the data to the device.
4. Once the data has finished copying, turn off the device and ship it back to the Azure datacenter that you are migrating the data to.
5. The data is moved to the designated Azure storage account once the device is returned.

More information about procuring and managing an Azure Data Box device can be found at `https://docs.microsoft.com/en-us/azure/databox/data-box-overview`.

## Summary

This chapter covered file and object storage concepts and when to use one over the other. In a nutshell, file storage is used to organize data on a file share and is typically used for network-wide collaboration. File storage is optimized for small amounts of data that can be organized using a hierarchy of directories and subdirectories. Object storage is used to store large volumes of data in binary and text format. This includes images, videos, audio, and data used in distributed analytics solutions.

Azure Storage is a multi-purpose PaaS storage platform that allows users to create object, file, key-value, and queue data stores. A storage account is the highest level of management for Azure Storage and can host one or more storage services. The storage services include Azure Blob storage, Azure Data Lake Storage Gen2, Azure Files, Azure Table storage, and Azure Queue storage.

Depending on the performance requirements for the use case, storage accounts can be configured to one of two account types: standard or premium. Both standard and premium storage accounts replicate their data three times locally for high availability. Standard storage accounts also allow users to configure a secondary region that will replicate the data three more times in a different Azure region for disaster recovery benefits.

Azure Files is a fully managed file share solution in Azure with support for SMB and NFS access protocols. File shares can be easily mounted to network drives or synchronized to a local machine using Azure File Sync. Azure offers the following four storage tiers for file shares to meet the performance and price requirements of different workloads: premium, transaction optimized, hot, and cool.

Azure Blob Storage is Azure's object storage solution. Typical Azure Blob Storage use cases include storing binary data such as images and videos and storing large amounts of textual data for big data processing solutions and as a data archive. Data in Azure Blob Storage is represented as blob objects. Blobs can be stored in one of three access tiers that allow users to store blob data in the most cost-effective manner depending on latency requirements and how frequently they are accessed.

Azure Data Lake Storage Gen2 (ADLS) is an object storage solution that is built on top of Azure Blob Storage. With its hierarchical namespace implementation and native HDFS support, ADLS is an ideal storage solution for big data analytics solutions.

As with any service in Azure, Azure Storage services can be deployed manually in the Azure Portal or automated with a script or an Infrastructure as Code template. Azure Storage provides multiple methods to secure data, including several network isolation and access management techniques. Data is natively encrypted at rest and in transit and is protected from being accidentally deleted or modified.

This chapter ends by describing some of the tools that can be used to manage and move data to Azure Storage. Data movement can be managed through a command line with AzCopy, graphically with Azure Storage Explorer, or as a part of an ETL pipeline with Azure Data Factory. Microsoft also offers Azure Data Box, a physical device that organizations can procure to migrate large amounts of data. Once it's ordered and received, organizations can connect an Azure Data Box device to their local network and upload data to it. The Azure Data Box device can then be shipped back to an Azure datacenter where Microsoft will upload the data to a storage account of the organization's choosing.

## Exam Essentials
