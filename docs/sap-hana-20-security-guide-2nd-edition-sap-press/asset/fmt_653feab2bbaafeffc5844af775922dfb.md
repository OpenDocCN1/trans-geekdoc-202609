
Developers will need to be assigned access to an organization or a space within an organization allowing them to create a container and deploy design-time content within an HDI container. To create and manage organizations and spaces, click the `Organizations` menu option from the SAP HANA XSA cockpit Home screen, as shown in [Figure 18.8](#18_002.html#f18.8). Locate an existing organization on the page. A separate tile will be created for each organization, with the title of each tile being the organization. Click the organization tile to drill into the configuration options and spaces associated with it.

[![Managing Organizations and Spaces in SAP HANA XSA Cockpit](bilderklein/klein18_008.png)](img-f18.8.html)

**Figure 18.8** Managing Organizations and Spaces in SAP HANA XSA Cockpit

When you click into the organization, the accordion menu changes on the right and includes new menu options for the organization. Click the `Members` menu option. A list of organization members will appear. To add a new member, click the `Add Members` button. When adding a member, you can grant one of two privileges. The first privilege is the organization manager, which grants full access to the organization and all spaces within the organization. Select the checkbox beside the `Organization Manager` role to grant it to the member. Grant the organization auditor role for members that only need read access to the organization and all spaces within the organization. Modify the assignments by using the pencil icon to the right of each listed member. You can also delete a member by clicking the trashcan icon to the right of each member.

To access the spaces within the selected organization, click the spaces button in the accordion menu to the right. Spaces within a selected organization will be displayed as tiles on the right side of the interface. Click the name of a space to drill down into the space options. Again, the accordion menu will change to show options specific to the management of spaces. Once again, click the `Members` menu item in the space-specific accordion menu. A list of existing members will appear on the right, as shown in [Figure 18.9](#18_002.html#f18.9).

[![Managing Members within a Space Using the SAP HANA XSA Cockpit](bilderklein/klein18_009.png)](img-f18.9.html)

**Figure 18.9** Managing Members within a Space Using the SAP HANA XSA Cockpit

Use this interface, shown in [Figure 18.9](#18_002.html#f18.9), to add members and space-specific role assignments. Three space roles are available. A space manager will have the ability to change various options for a given space using the SAP HANA XSA cockpit or other available interfaces. The space developers role grants a member the ability to manage applications and services deployed to the space. For example, a developer needs this access to use this space within SAP Web IDE for SAP HANA to build a project or deploy it to its runtime HDI container. The space auditors role allows a member to view the configuration of the space without the ability to make changes. Developers cannot deploy runtime content with this role. Again, be sure you understand that SAP HANA XSA users will often need access to an organization or space within to deploy applications based on that space. Also, organization and space access is managed independently of application access granted with role collections.

You should now understand how users, organizations, spaces, and role collections are managed within the SAP HANA XSA platform using the SAP HANA XSA cockpit. Note that SAP HANA XSA role collections and SAP HANA XSA application roles are decoupled from the SAP HANA database. Thus, developers cannot deploy applications that are runtime without to proper access to a space. Next, we’ll review another important tool that developers use in the SAP HANA XSA platform from a security standpoint, SAP Web IDE for SAP HANA.

## 18.3 Working with SAP Web IDE for SAP HANA

SAP Web IDE for SAP HANA, a web-based application hosted within the SAP HANA XSA platform, is used by developers to create applications for the SAP HANA XSA platform. SAP Web IDE for SAP HANA can also be used by developers to create SAP HANA database catalog objects, SAP HANA calculation views, SAP HANA core data services (CDS) artifacts, and SAP HANA XSA-based repository roles. From a security perspective, you can use SAP Web IDE for SAP HANA to manage roles deployed within a specific HDI container. As an SAP HANA and SAP HANA XSA security administrator, you must understand the role of this tool and the steps required to grant developers access to it. In the next section, we’ll provide an overview of the tool and the components that govern its security.

### 18.3.1 SAP Web IDE for SAP HANA Overview

SAP Web IDE for SAP HANA is deployed within the SAP HANA XSA platform. Before you can access SAP Web IDE for SAP HANA, you’ll need to verify a few items. First, when SAP Web IDE for SAP HANA 2.0 is installed to the SAP HANA XSA platform, the deployment does not create role collections in the SAP HANA XSA cockpit. You must log on to the SAP HANA XSA cockpit and create two new role collections. You only need to do this once in most cases. For example, you can create the role collections shown in [Table 18.1](#18_003.html#t18.1).

| Role Collection Name || Application Identifier || Included Role/Role Template |
| --- | --- | --- |
| `ZXS_WEBIDE_ADMIN` || `webide!i1` || `WebIDE_Administrator` |
| `ZSX_WEBIDE_DEVELOPER` || `webide!i1` || `WebIDE_Developer` |

**Table 18.1** Example Roles Collections to Create before Accessing SAP Web IDE for SAP HANA

With the two role collections created, SAP Web IDE for SAP HANA user must be granted at a minimum the `ZSX_WEBIDE_DEVELOPER` role collection example shown in [Table 18.1](#18_003.html#t18.1). The application role `WebIDE_Developer` allows a user to access SAP Web IDE for SAP HANA and the SAP HANA database explorer. The `WebIDE_Administrator` role grants access to additional tools within SAP Web IDE for SAP HANA such as the space enablement tool.

In addition to these custom role collections, a user might also need the following SAP HANA XSA privileges depending on their function:

*   At a minimum, the user needs the role collection `XS_CONTROLLER_USER` granted to work with spaces and organizations when building projects or deploying them to the runtime.
*   For a given space, they’ll need the space role `space developers` to build or deploy projects to the runtime.

If you have an SAP HANA XSA user and have the correct access to the space, organization, and SAP HANA XSA platform, you should be able to log on to the SAP Web IDE for SAP HANA application. Before you can log on, you must identify the URL used to access the SAP Web IDE for SAP HANA application. If you’re unsure of the URL, you can access the SAP HANA XSA command line and run the following commands to list each deployed application and its URL:

```
xs login
xs a
```

Once you have the URL, access SAP Web IDE for SAP HANA and provide your credentials. You’ll then land on the application’s homepage, as shown in [Figure 18.10](#18_003.html#f18.10).

[![SAP Web IDE for SAP HANASAP Web IDE for SAP HANAhomepage Homepage](bilderklein/klein18_010.png)](img-f18.10.html)

**Figure 18.10** SAP Web IDE for SAP HANA Homepage

The interface is divided into menu icon options on the left, a file menu bar on the top a workspace area containing your code, and then a working area on the right. As you open objects in the workspace, they will open in the working area on the right.

In this section, we won’t go into detail about how to use SAP Web IDE for SAP HANA to develop content. That topic is beyond the scope of this book. The goal of this section is to make sure administrators understand how to set up security for SAP Web IDE for SAP HANA and how users access the application.

###### More Information on Development within SAP Web IDE for SAP HANA
