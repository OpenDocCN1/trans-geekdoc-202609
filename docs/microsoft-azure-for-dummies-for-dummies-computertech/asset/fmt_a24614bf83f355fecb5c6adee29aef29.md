
![Tip](images/tip.png)When I refer to a resource’s *context menu* in the Azure portal, I typically mean the ellipsis (…) icon that appears at the right end of the item row.

### Backing up storage blobs in bulk

The question we consider now is how to take backups of entire blob containers. Sadly, the Azure platform doesn’t have any native features to assist you; I don’t have any definitive answer for why this is, but Microsoft may consider that as a feature request in the future. But you can write a shell script that calls `AzCopy` (see the nearby sidebar) to copy blobs between two storage accounts, preferably in different regions.

First, install `AzCopy` (see the “[AzCopy](#c10.xhtml#c10-fea-0001)” sidebar later in this chapter), and then open an elevated command prompt and run the following PowerShell command to set a new environment variable that points to your `AzCopy` installation directory (in this example, `AzCopy` is in my `C:\azcopy` directory). You do this so you can call the `AzCopy` command from any directory in a command-prompt session or script file:

```
[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\bin", "Machine")
```

Then restart your computer to enable the new system environment variable.

Here's the `AzCopy` command I used to copy my scripts container from my `wileyprimstorage` storage account to my `scripts-backup` container in my `wileysecstorage` storage account:

```
AzCopy /Source:https://wileyprimstorage.blob.core.windows.net/scripts /Dest:https://wileysecstorage.blob.core.windows.net/scripts-backup /SourceKey:4SXSCKBA== /DestKey:ZpuwuCLQ== /S
```

You authenticate to the storage accounts by passing in an access key. If you’ve been studying this book in chapter sequence, you know what access keys are and how to find them. If not, then I suggest you read [Chapter 3](#c03.xhtml) for a formal treatment of Azure storage accounts.

## Protecting Your Virtual Machines

That's enough about storage accounts. This section discusses protecting your precious Azure VM operating system and data disks that currently reside in Managed Disk storage.

### Getting to know the Recovery Services vault

The Azure Recovery Services vault has two purposes:

*   **Backup and recovery:** Backing up and restoring individual VMs or VMs in bulk
*   **Disaster recovery:** Configuring warm standby instances of your Azure VMs and switching to them quickly if the primary instance(s) go offline

![Technical stuff](images/technicalstuff.png)Both the Managed Disk service and the Recovery Services vault are abstraction layers on top of the Azure storage account. Much of Azure Resource Manager deals with abstracting higher levels of administrative overhead for more-manageable levels.

#### Deploying a Recovery Services vault

Follow these steps to deploy a Recovery Services vault in the Azure portal:

1.  **Browse to the Recovery Services vaults blade, and click Add.**
2.  **Complete the Create Recovery Services vault form.**
    The vault name needs to be unique at the Azure subscription level. Keep in mind that your VMs to be backed up need to be in the same region as your Recovery Services vault.
3.  **Click Review + Create and then click Create to submit the deployment.**
    The deployment is fast because the Recovery Services vault is essentially a container.

Azure Recovery Services vaults can automate the backups of SQL Server running in Azure VMs as well as storage account file shares, but you need to drill into VM backup.

![Warning](images/warning.png)You can back up Azure VMs only to a Recovery Services vault in the same Azure region. If your VMs span regions, you need multiple Recovery Services vaults that do the same.

#### Creating a backup policy

A *backup policy* determines your backup schedule — that is, how often Azure makes backups and how long it retains them.

Follow these steps to create a simple backup policy to use for your VM backups:

1.  **In your Recovery Services Vault settings, click Backup Policies.**
2.  **On the Backup Policies page, click Add.**
    The Add blade appears.
3.  **In the Add blade under Policy Type, select Azure Virtual Machine.**
    Notice that you can also create policies for SQL Server in an Azure VM and Azure File Share backups.
4.  **Complete the Create Policy blade.**
    Here are the major policy options:
    *   **Policy Name:** Use a descriptive name. (I chose `wiley-windows-policy`, for example.)
    *   **Backup Schedule:** Select Daily or Weekly.
    *   **Instant Restore:** Specify a value between 1 and 5 days to keep your latest backup snapshot in the Recovery Service vault staging area. This feature makes restores much faster because the vault doesn’t have to unpack the snapshot from the archives to place it in the staging area.
    *   **Retention Range:** Specify how long Azure archives weekly, monthly, and yearly backup points.
5.  **Click Create to commit your changes.**

### Backing up VMs

You can configure VM backup from the perspective of the Recovery Services vault or the perspective of an individual VM. In this section, I show you both methods.

> **Note:** To follow along with the exercises in this section, you need two VMs; it doesn’t matter whether they run Windows Server or Linux. It’s important that the VMs be in a running state so that the Azure VM Snapshot extension can back up files in use and provide for application-consistent backups.

I cover Azure VM creation in [Chapter 5](#c05.xhtml).

#### Backing up a single VM

Follow these steps to back up a running VM in the Azure portal:

1.  **In the VM’s Settings list, select Backup.**
2.  **Complete the Welcome to Azure Backup blade.**
    All you need to do is choose your newly created Recovery Services vault and your new backup policy from the provided drop-down menus.
3.  **Click Enable Backup.**
4.  **When deployment is complete, return to the VM’s Backup blade.**
5.  **On the toolbar, click Backup Now.**
    This step initiates a manual backup rather than waiting for the next backup window specified in your policy.
6.  **Confirm the backup retention date.**
7.  **Click OK to start the backup.**

#### Backing up multiple VMs

Follow these steps to back up one or more VMs from your Recovery Services vault:

1.  **In your Recovery Services vault’s settings list, select Backup.**
2.  **Complete the following fields as shown here:**
    *   **Where Is Your Workload Running?:** Azure
    *   **What Do You Want to Back Up?:** Virtual machine
3.  **Click Backup to continue.**
4.  **On the Backup Policy blade, select your VM policy, and click OK to continue.**
    The Select Virtual Machines blade appears.
5.  **On the Select Virtual Machines blade, select the VMs you want to include in the batch backup job configuration.**
    [Figure 10-3](#c10.xhtml#c10-fig-0003) shows my environment.
    ![FIGURE 10-3: You can back up multiple VMs simultaneously from your Recovery Services vault.](images/9781119612148-fg1003.png)
    [FIGURE 10-3:](#c10.xhtml#rc10-fig-0003) You can back up multiple VMs simultaneously from your Recovery Services vault.
6.  **Click OK.**
    The Backup blade appears.
7.  **In the Backup blade, click Enable Backup to complete the configuration.**

![Tip](images/tip.png)You can check on the backup job status by clicking the Backup Jobs setting in your vault.

### Restoring VMs

Before I explain the “clicky-clicky” procedure, I want to explain the VM restore options.

#### VM backup consistency levels

Azure offers three guarantees for VM restore, depending on the consistency level of the backup snapshots:

*   **Application-consistent:** This level is the most preferred snapshot consistency level. The guarantee is that the VM will boot up and that you won’t suffer data corruption or loss.
*   **File-system-consistent:** The SLA stipulates that the VM will boot up and that you’ll suffer no data corruption. You may need to implement manual or automated fixups, however, to ensure that your data is current.
