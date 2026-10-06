# CHAPTER 18 CONNECTING WINDOWS AND MAC CLIENTS

+   - You can create a mapped drive to network folder shares.

+   - You can use Windows Explorer to connect to uniform naming convention (UNC) paths that describe the network location in the form of \computename\sharename.

The following examples will access resources located on the bigform.com domain. Table 18.1 lists those resources and their locations on the network.

# TABLE 18.1: Network Resources Used in This Section's Examples

| NETWORK RESOURCE TYPE | NETWORK RESOURCE PATH | NETWORK RESOURCE LOCATION |
| --- | --- | --- |
| Marketing file share | \bf1\BF_Marketing | bf1.bigform.com |
| Black-and-white printer | \bf1\BF_Main_Printer | bf1.bigform.com |

# Publishing Resources with Group Policy Objects

Starting with Windows 2008's version of Active Directory, you are able to publish all the most common resources to client (and server) devices in a centralized way. The new feature discussed in Chapter 9 is Group Policy: Preferences. These policies allow you to perform such operations as setting up drive mappings, creating shortcuts, and configuring environment settings, as shown in Figure 18.23. You can do this for both users and computers that are located in specific organizational units (OUs) or of them.

![](bbox=[0.095, 0.532, 0.903, 0.893])