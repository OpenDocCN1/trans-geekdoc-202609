
# 注册 SAP HANA 资源

Click the Register Resource button to launch the five-step Register Resources wizard. In the first step, `1\. Resource`, provide the connection details for your SAP HANA database. Click the Step 2 button to continue. In the second step, `2\. Connection`, select the desired communication encryption options when connecting to the SAP HANA database. Click the Step 3 button to continue. In the third step, `3\. Technical User`, enter the credentials that will be used to gather runtime and health information from the database. This step also provides an additional option for creating a technical user within the target database. Click the Step 4 button to continue. In the fourth step, `4\. Resource Groups`, assign the registration to one or more existing resource groups. Click the Step 5 button to continue. In the fifth step, `5\. Contact`, enter the contact information for the administrator of the database. Click the Review button to view a summary of the registration. If the information looks correct, click the Register button to activate the connection.

A basic understanding of the SAP HANA cockpit manager will be required when creating SAP HANA cockpit users and when managing access to the overall SAP HANA cockpit functionality. In this section, we provided a high-level overview of the components and steps necessary to set up access to the SAP HANA cockpit and SAP HANA cockpit manager. In the next section, we’ll provide a few tips on navigating the SAP HANA cockpit Home page, connecting to a registered database, and locating security-specific options on the System Overview page.

## 1.1.3 Navigating SAP HANA Cockpit

Navigating the SAP HANA cockpit requires a basic understanding of the interface layout and the workflow used to connect to a registered database and then interact with security and administration tools on the System Overview interface. We discussed how to obtain the SAP HANA cockpit URL in [Section 1.1.2](#01_001.html#h1.1.2) and how to set up user access to the SAP HANA cockpit. Once you’ve logged onto the SAP HANA cockpit, you’ll start with the SAP HANA cockpit Home page.

[Figure 1.8](#01_001.html#f1.8) shows an example layout of the SAP HANA cockpit Home page. The tabs near the top of the interface (Monitor Landscape, Manage Landscape, and SAP One Support) will each navigate you to a different section and tile set on the homepage. Let’s look at each of these tabs in more detail.

The first tab and tile set is the Monitor Landscape tab. Under this tab, you can view the entire resource directory by clicking the Resource Directory tile. You can also see registered systems organized into Production, Development, and Test resource groups based on the database’s configured profile. When installing SAP HANA, the installer will establish the intended use of the system, and that information is used by the SAP HANA cockpit to automatically organize registered systems into the Production, Development, and Test resource groups. Any resource groups assigned to your user account will also display as tiles in this section. Finally, the Administration Help tile enables you to navigate to documentation relevant to administering the SAP HANA cockpit.

[![SAP HANA Cockpit Homepage](bilderklein/klein01_008.png)](img-f1.8.html)

**Figure 1.8** SAP HANA Cockpit Homepage

To navigate to an SAP HANA database, locate the connection based on the tile groups found on your homepage. In most cases, you’ll find a system in one or more of the tile groupings. Each tile is not exclusive to a registered SAP HANA system. For example, to see all registered systems that your account has access to, click the Resource Directory tile to see a complete list. Within the resource directory, you can use the filter bar to locate a specific SAP HANA database. This feature makes locating a specific SAP HANA database easy even in large landscapes that might have several registered systems.

Once you’ve located a registered SAP HANA database, click the resource name, typically following the format `<database tenant>@<SID>`. For example, if the tenant database is H4E, and the SID of the database is HDB, the registered name would be H4E@HDB. [Figure 1.9](#01_001.html#f1.9) shows a list of registered SAP HANA systems and the filter bar. Once you’ve located your target system, click the system name to access that system’s System Overview page.

[![List of SAP HANA Systems within the SAP HANA Cockpit Resource Directory](bilderklein/klein01_009.png)](img-f1.9.html)

**Figure 1.9** List of SAP HANA Systems within the SAP HANA Cockpit Resource Directory

The System Overview page is also divided into tiles and sections. A smaller filter bar exists at the top of the page. You can use this filter bar to limit the administration tiles that are displayed. In the Filter by Area dropdown list, choose Security to limit the interface to tiles that contain SAP HANA security functions.

[Figure 1.10](#01_001.html#f1.10) shows an example of the tile layout and the various options available for managing security. The tiles in the security area are the Data Encryption, Auditing, Authentication, Security Related Links, User & Role Management, and Anonymization Report tiles.

In the next section, we’ll explore each of these tiles in more detail. For now, understanding how to access a registered resource, how to access the System Overview page, and how to filter for security-related areas or tiles are the most important processes for you to understand.

[![Security-Related Tiles and Configuration Options within the SAP HANA Cockpit When Connected to a Registered System](bilderklein/klein01_010.png)](img-f1.10.html)

**Figure 1.10** Security-Related Tiles and Configuration Options within the SAP HANA Cockpit When Connected to a Registered System

## 1.2 Security Areas in SAP HANA Cockpit

Up to this point in the chapter, we’ve discussed the architecture of the SAP HANA cockpit, including deployment options. We’ve explored the SAP HANA cockpit manager and described the high-level steps required to set up users, resource groups, and registered systems. Finally, we provided high-level information about how you can access a registered system in the SAP HANA cockpit and then access a registered system’s System Overview page. On the System Overview page, you can filter the various options available using the Filter by Area dropdown list. For the purposes of managing security, we’ll find most options in this area.

The security area provides tiles and links to the Data Encryption, Auditing, Authentication, Security Related Links, User & Role Management, and Anonymization Report areas. In the next section, we’ll provide a high-level overview of each area and describe how you’ll use these areas to manage an SAP HANA security model.

### 1.2.1 User & Role Management Area

The User & Role Management area provides several links, such as the Manage Users, Assign roles to users, Assign privileges to users, Manage roles, Manage user groups, and View database object dependencies links, as shown in [Figure 1.11](#01_002.html#f1.11).

[![The User & Role Management Tile in SAP HANA Cockpit](bilderklein/klein01_011.png)](img-f1.11.html)

**Figure 1.11** The User & Role Management Tile in SAP HANA Cockpit

The following list outlines what each link in this tile is used for. In subsequent chapters, we’ll demonstrate these items in more detail. However, in this chapter, we’ll only provide a basic overview of each link. Let’s briefly look at each link:

*   Manage users
