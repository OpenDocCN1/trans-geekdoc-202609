
Using the SAP HANA Web-Based Development Workbench editor, you can create packages within the hierarchy. To create a top-level package, right-click the Content folder and choose New • Package. To create a subpackage within a top-level package, right-click an existing package and choose New • Package. You can also use the keyboard shortcut `(Ctrl)+(Alt)+(Shift)+(N)` as an alternative to the right-click menu to launch the package creation process. Once you start the process, the Create Package popup window will appear. [Figure 9.2](#09_001.html#f9.2) shows an example of the window that will appear where you can define the package.

[![Naming Your Package in the Create Package Popup Window](bilderklein/klein09_002.png)](img-f9.2.html)

**Figure 9.2** Naming Your Package in the Create Package Popup Window

Enter the Package Name in the provided field. Enter a text description to help others identify the purpose of the package in the Description field. The remaining Responsible and Original Language fields are additional, optional metadata fields. Click the Create button, and a new package will appear in the hierarchy below the node where you started the creation process. You can repeat this process for each new top-level node or subpackage that is required to secure and organize your development artifacts.

### 9.1.3 Overview of Delivery Units

Delivery units play a role in the lifecycle management of packages. Before you can export content to a file or transport development content from one SAP HANA system to another, you must first assign a package or package hierarchy to a delivery unit. A delivery unit should contain package and development artifacts that are associated with each other. For example, a web-based application developed in the XS engine and its associated package hierarchy can be assigned to a single delivery unit. Using a delivery unit allows the content to be transported in an organized and consistent manner.

Once content is organized into a delivery unit, you can export the delivery unit to a compressed file, which then can be imported into another SAP HANA system for the purposes of transporting the code. Using SAP HANA application lifecycle management, you can also transport delivery units between systems. A delivery unit can also serve as an external code backup and can be imported back into the originating SAP HANA system if content needs to be restored.

Note that an administrator must define the vendor ID or content vendor within the system configuration before content can be assigned to a delivery unit. This vendor definition is configured in the `indexserver.ini` file under the repository option and `content_vendor` key. Specify a value that will identify your organization’s name; for example, you could enter a domain name, such as “e-corp.com.”

The user creating the delivery unit must have privileges similar to those assigned to the default role `sap.hana.xs.lm.roles::Administrator`. Note that the INIFILE admin system privilege, found in this default role, is only necessary for defining the content vendor. A custom role should be created for developers that create delivery units to avoid granting them access to make configuration changes to the SAP HANA system.

###### Additional Information about Delivery Units

For additional information pertaining to the creation and management of delivery units, refer to the SAP HANA Application Lifecycle Management Guide, available at [http://s-prs.co/v498206](http://s-prs.co/v498206).

## 9.2 What Are Package Privileges?

Package privileges are organized into two broad categories: native package privileges and imported package privileges. Native package privileges refer to packages and their child development artifacts developed from scratch in an SAP HANA system. You should expect to create and edit native content in a development system. Imported package privileges represent packages and their child development artifacts that are imported into a system. These objects are created in a remote system, exported, and then imported into a different system.

As noted earlier, packages are nodes organized in a parent-child relationship. Together, these nodes make up the SAP HANA repository. Each package contains a subpackage or one or more development artifacts. Package privileges are assigned for a package node; development artifacts can’t be granted privileges individually or explicitly. However, development artifacts do inherit the privileges assigned to their parent and grandparent package nodes.

Inheritance can simplify the design of a security model. For example, you can establish privileges for a top-level package and assume that all child objects will inherit the same privileges. You won’t need to explicitly configure privileges for each child package or subpackage within the repository. Inheritance simplifies the design of repository roles because you won’t need to address package privileges each time a new package or development artifact is created.

In addition to its benefits, inheritance also introduces some risks, depending on the placement of critical development artifacts such as repository roles. For example, repository roles must be stored in an isolated location to prevent privilege elevation by users that don’t manage roles or the assignment of privileges. Stored procedures used to provision users must also be stored in an isolated location for the same reasons. Therefore, inheritance can also present challenges to a security model that leverages development artifacts.

When the system validates access to a development artifact, it first checks the privileges assigned to the direct parent package. If no privileges have been assigned to the direct parent, the system will continue to traverse up the hierarchy, checking each grandparent node until it can validate the requested action. If no parent or grandparent node has assigned privileges for that user, the user fails authorization and is considered not authorized to perform the requested action.

Development artifacts use a bottom-up approach to authorization validation. Therefore, you don’t have to explicitly assign privileges to each parent and grandparent package node; you only need to grant privileges to its closest desired parent or grandparent package, and no privileges need to be established specifically for a given user at each level of the package hierarchy. Be sure you understand this point because experienced security professionals might assume that development artifacts use a top-down approach based on inheritance and might then overengineer the security model.

Native package privileges apply to objects that are directly created, maintained, and activated within a particular originating environment. For example, if you create a repository role within a development system, that role will always remain a native object within that system. The native package privileges are as follows:

*   `REPO.READ`

    This package privilege grants read access to a package and its child objects. This privilege applies to both native and imported objects.

*   `REPO.EDIT_NATIVE_OBJECTS`

    This package privilege grants edit privileges to design-time objects within a package. This privilege only applies to native objects or those created within an originating system.

*   `REPO.ACTIVATE_NATIVE_OBJECTS`

    This package privilege grants the ability to create, activate, or reactivate design-time objects within a package. This privilege only applies to native objects or those created within an originating system.

*   `REPO.MAINTAIN_NATIVE_PACKAGES`

    This package privilege grants the ability to edit and create packages and subpackages. This privilege only applies to native packages or those created within an originating system.

Imported package privileges are as follows:

*   `REPO.EDIT_IMPORTED_OBJECTS`
