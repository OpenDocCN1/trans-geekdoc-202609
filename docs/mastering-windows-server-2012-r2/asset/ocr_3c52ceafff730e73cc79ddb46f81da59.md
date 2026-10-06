# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

+   1. Run adprep on the schema master role by typing adprep /forestprep, and press Enter.

A warning will appear verifying that all servers are running Windows Server 2003 or higher.

+   2. Confirm by typing C and then pressing Enter.

+   3. Next, on the infrastructure master role in your domain that you want to prepare, run adprep /domainadprep /gpprep and press Enter.

+   4. Finally, run adprep /rodprep on the infrastructure master role.

In step 1, when you extended the forest, you might have noticed while running the command that a lot of text appears and runs in a matrix style through your domain prompt. This step imports all the necessary schema changes. If you have Exchange or Lyric or any other application that needed a schema extension in the past, step 1 did not change or interfere with these schema changes.

Step 4 prepared the domain for Windows Server 2012 and changed the permission for Group Policy objects for replication with Windows Server 2012. As a last, you added the opportunity to add a Read-only Domain Controller. It is a good idea to run adprep /rodprep now or at a later time when you are back in production, it might require more effort to do this.

To summarize, before you upgrade a Windows 2008–based AD domain to a Server 2012-based AD domain, you must do the following:

+   2. Upgrade the forest by running adprep /forestprep on the schema FSMO computer for your forest, even if that machine is not in the domain that you are going to upgrade.

+   3. Upgrade the domain structure by running adprep /domainadprep /gpprep on the infrastructure FSMO for the domain that you are going to upgrade.

+   4. Optionally, run /rodprep to prepare for read-only domain controllers.

# Running Setup

Now you're ready to run Setup. In the DVD, double-click in My Computer if it doesn't autostart, and select the Upgrade option. When you are asked about the latest updates, select this option so that you will have the latest updates available. The wizard will warn you about anything that will change in this upgrade. It will also check that you've forest-prepped and domain-prepped properly. If you click Start, you will get a dialog showing any application or driver compatibility issues. If you accept the results, Setup runs hands-off, and there's nothing for you to do until it's done and you log into your newly upgraded Server 2012 DC for the first time. At this point, you're upgraded!