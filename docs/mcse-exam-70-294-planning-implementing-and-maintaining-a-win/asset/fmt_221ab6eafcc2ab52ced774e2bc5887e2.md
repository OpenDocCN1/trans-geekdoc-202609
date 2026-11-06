
## Active Directory Sites and Services

As shown in [Figure 1.22](#B9781931836944500076.xhtml#f0115), the `Active Directory Sites and Services` console has a number of containers that provide information and functions on creating and maintaining sites. When a domain is first installed on a DC, a site object named `Default-First-Site-Name` is created. This container can (and should) be renamed to something that is meaningful to the business. As mentioned earlier, additional sites can be created to improve replication between sites, or domains can be added to this existing site.

![Figure 1.22 Active Directory Sites and Services](images/B9781931836944500076/f01-22-9781931836944.jpg)

Figure 1.22 Active Directory Sites and Services

The `Inter-Site Transports` container is used to create and store site links. A site link is a connection between sites. Links created under the `IP` container use the Internet Protocol (`IP`) as their transport protocol, while those created under `SMTP` use the Simple Mail Transfer Protocol (`SMTP`).

The `Subnets` container is used to create and store objects containing information about subnets on your network. Subnets are collections of neighboring computers that are subdivided within the network, using a common network ID. Using the `Subnets` container, you can group different subnets together to build a site.

Now that we’ve looked at the `MMC`, and the snap-ins used to manage Active Directory, let’s get a little hands-on experience. In [Exercise 1.02](#B9781931836944500076.xhtml#b0095), we’ll see how the `MMC` is used to load the snap-ins we’ll use in future exercises.

## Exercise 1.02 Adding Snap-Ins to the Microsoft Management Console

1. From the `Run` command in the Windows Start menu, type `MMC`, and click `OK`.
2. When the `MMC` opens, click the `Add/Remove Snap-in` command on the `File` menu.
3. When the `Add/Remove Snap-in` dialog box appears, dick the `Standalone` tab to select it. Click the `Add` button.
4. When the `Add Standalone Snap-in` appears, select `Active Directory Domains and Trusts` from the listing and then click the `Add` button. An entry for this snap-in should appear in the listing in the `Add/Remove Snap-in` dialog box.
5. Select `Active Directory Sites and Services` from the listing and then click the `Add` button. An entry for this snap-in should appear in the listing in the `Add/Remove Snap-in` dialog box.
6. Select `Active Directory Users and Computers` from the listing and then click the `Add` button. An entry for this snap-in should appear in the listing in the `Add/Remove Snap-in` dialog box.
7. Click `Close` to return to the previous screen. At this point, three entries should appear in the `Add/Remove snap-in` dialog box. Click `OK` to close the dialog.
8. The console tree in the `MMC` should now contain nodes for each snap-in. Expand each snap-in and notice that they contain objects and information relating to the aspects each snap-in deals with.

## Command-Line Tools

Windows Server 2003 provides a number of command-line tools that you can use for managing Active Directory. These tools use commands typed in at the prompt, and can provide a number of services that are useful in administering the directory. The command-line tools for Active Directory include:

![Squareb](images/Squareb.png) `Cacls` Used to view and modify discretionary access control lists (DACLs) on files.

![Squareb](images/Squareb.png) `Cmdkey` Used to create, list, and delete usernames, passwords, and credentials.

![Squareb](images/Squareb.png) `Csvde` Used to import and export data from the directory.

![Squareb](images/Squareb.png) `Dcgpofix` Restores Group Policy Objects (GPOs) to the state they where in when initially installed.

![Squareb](images/Squareb.png) `Dsadd` Used to add users, groups, computers, contacts, and OUs.

![Squareb](images/Squareb.png) `Dsget` Displays the properties of an object in Active Directory.

![Squareb](images/Squareb.png) `Dsmod` Used to modify users, groups, computers, servers, contacts, and OUs.

![Squareb](images/Squareb.png) `Dsmove` Renames an object without moving it, or moves an object to a new location.

![Squareb](images/Squareb.png) `Ldifde` Used to create, modify, and delete objects from Active Directory.

![Squareb](images/Squareb.png) `Ntdsutil` Used for general management of Active Directory.

![Squareb](images/Squareb.png) `Whoami` Provides information on the user who’s currently logged on.

In the sections that follow, we will briefly discuss each of these tools, and show you how they can assist you in performing certain tasks when administering Active Directory.

### Cacls

`Cacls` is used to view and modify the permissions a user or group has to a particular resource. `Cacls` provides this ability by allowing you to view and change DACLs on files. A DACL is a listing of access control entries (ACEs) for users and groups, and includes permissions the user has to a file. The syntax for using this tool is:

`Cacls filename`

`Cacls` also has a number of switches, which are parameters you can enter on the command line to use a specific functionality. [Table 1.1](#B9781931836944500076.xhtml#t0010) lists the switches for `Cacls`.

Table 1.1

Switches for the `Cacls` Tool

| Parameter | Description |
| --- | --- |
| `/t` | Change the DACLs of files in the current directory and all subdirectories. |
| `/e` | Edit the DACL. |
| `/r username` | Revokes the users’ rights. |
| `/c` | Ignore any errors that might occur when changing the DACL. |
| `/g username permission` | Grants rights to a specified user. Rights that can be granted are: n (None), r (Read), w (Write), c (Change), and f (Full Control). |
| `/p username permission` | Replaces the rights of a specified user. The rights that can be replaced are: n (None), r (Read), w (Write), c (Change), and f (Full Control). |
| `/d username` | Denies access to a specified user. |

### Cmdkey

`Cmdkey` is used to create, view, edit, and delete the stored usernames, passwords, and credentials. This allows you to log on using one account, and view and modify the credentials of another user. As with other command-line tools we’ll discuss, `cmdkey` has a number of switches that provided needed parameters for the tool to function. [Table 1.2](#B9781931836944500076.xhtml#t0015) lists these parameters.

Table 1.2

Switches for the `Cmdkey` Tool

| Parameter | Description |
| --- | --- |
| `/add:targetname` | Adds a username and password to the list, and specifies the computer or domain (using the targetname parameter) with which the entry will be associated. |
| `/generic` | Adds generic credentials to the list. |
| `/smartcard` | Instructs `cmdkey` to retrieve credentials from a smart card. |
| `/user: username` | Provides the username with which this entry is to be associated. If the username parameter isn’t provided, you will be prompted for it. |
| `/pass: password` | Provides the password to store with this entry. If the password parameter isn’t provided, you will be prompted for it. |
| `/delete: {targetname | /ras}` | Deletes the username and password from the list. If the targetname parameter is provided, the specified entry will be deleted. If `/ras` is included, the stored remote access entry is deleted. |
| `/list: targetname` | Lists the stored usernames and credentials. If the targetname parameter isn’t provided, all of the stored usernames and credentials will be listed. |

### Csvde

`Csvde` is used to import and export data from Active Directory. This data is comma delimitated, so that a comma separates each value. Exporting data in this way allows you to then import it into other applications (for example, Microsoft Office tools such as Access and Excel). [Table 1.3](#B9781931836944500076.xhtml#t0020) lists the parameters for this command.

Table 1.3

Switches for the `Csvde` Tool

| Parameter | Description |
| --- | --- |
| `-i` | Used to specify the import mode. |
| `-f filename` | Specifies the filename to import or export data to. |
