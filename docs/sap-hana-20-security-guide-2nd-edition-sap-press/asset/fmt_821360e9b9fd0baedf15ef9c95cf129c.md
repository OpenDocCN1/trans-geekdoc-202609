
Unlike the SAP HANA Web-Based Development Workbench and the older SAP HANA Studio, the SAP HANA cockpit GUI does not support SAP HANA XS repository-based catalog objects and schemas. Therefore, you cannot grant privileges to design-time objects nor their runtime objects in the catalog. In short, the SAP HANA cockpit is not designed to work with SAP HANA XS repository objects that are owned by the `_SYS_REPO` account. Why SAP chose not to support this functionality is not clear, but the most likely explanation is that future versions of SAP HANA will not support the SAP HANA XS development architecture.

To revoke an object privilege, click an assigned object and its assigned privilege from the list and then click the `Remove Object` button to revoke the privilege. To make the changes active, click the `Save` button or continue making other changes if necessary. Note that, once the `Save` button is clicked, you’ll be returned to the list of privileges and will need to click the `Edit` button again to make further changes.

To change assigned object privileges, while in edit mode, click an assigned object and its assigned privilege from the list and then click the `Change Privileges` button to open a new popup window with the title `Change Privileges of` concatenated with the name of the object. A list of assigned and unassigned privileges for the object will appear. Select the checkboxes to grant the privilege or deselect the checkbox to revoke the privilege. Use the `Yes/No` slider to manage the grantable to others privilege. Click the `OK` button at the bottom right to apply your changes. Again, to make the changes active, click the `Save` button or continue making other changes as necessary until you’re ready to activate all changes.

#### Analytic Privileges

The third tab in the user management interface is the `Analytic Privileges` tab. The process for granting or revoking analytic privileges is like the process used for system privileges discussed earlier in this section.

The analytic privileges listed in this interface have already been granted to the user. If the list is blank, nothing is currently granted. To grant an analytic privilege, click the `Edit` button located on the far-right near the `Search` field to enable edit mode. Once you click the `Edit` button, new buttons labeled `Cancel`, `Add`, and `Remove` will appear. Click the `Add` button to open the `Select Analytic Privileges` popup window. Within this window, you’ll see a search bar and a list of runtime analytic privileges with checkboxes. Use the search bar to filter the list based on the entered text. Then, scroll through the list and select the checkbox next to the analytic privilege you want to grant. With one or more analytic privileges selected, click the `OK` button to add the desired items to the user. Your selected analytic privileges should now appear in the list.

To assign the `Grantable to Others` privilege, while in edit mode, locate an analytic privilege in the list. To the right, you’ll see a `Yes/No` slider. Move the slider to `Yes` to allow the user to grant the same privilege to another user or role. Note that the slider will not be enabled if your current logged in user account does not have the privileges necessary to grant `Grantable to Others`. Repeat this process for each analytic privilege in the list. Once you’ve added all the desired analytic privileges to the list, click the `Save` button to grant the privileges.

To revoke an analytic privilege, start by clicking the `Edit` button again to enable edit mode, then select the checkbox beside each analytic privilege you want to revoke, and click the `Remove` button to revoke the privileges. Repeat the process for each analytic privilege you want to revoke. Once you’ve removed all the desired analytic privileges, click the `Save` button. The removed privileges will be revoked, and the user object will be updated.

During the process of adding or removing privileges, you can click the `Cancel` button to discard any unsaved changes. Clicking the `Cancel` button will deactivate the `Add`, `Cancel`, and `Remove` buttons and return you to a read-only list of currently granted analytic privileges.

#### Package Privileges

The fifth tab in the `Assign Privileges` window is named `Package Privileges`. The process for granting or revoking package privileges like the process used for object privileges. The packages and privileges listed in this interface have already been granted to the user. If the list is blank, nothing is currently granted. To grant a package privilege, click the `Edit` button located on the far-right side of the interface near the `Search` field. Once you click the `Edit` button to enable the edit mode, new buttons labeled `Cancel`, `Add Package`, `Change Privileges`, and `Remove Package` will appear. Click the `Add Package` button to open the `Select Objects` popup window. Within this window, you’ll see a search bar and a list of packages. Use the search bar to filter the list based on the entered text. Scroll through the list and highlight the package you want to assign privileges to.

Once you click the desired package, the `Add Package with Privileges` window will appear. In this window, you’ll see a list of possible package privileges that can be assigned. Select the checkbox beside each privilege you want to grant. In addition, for each privilege, you can use the `Yes/No` slider under `Grantable to Others` to allow the privilege to be granted to other users. Click the `OK` button located at the bottom right side of the interface to continue.

You should now see the selected packages and the privileges you assigned listed in the `Package Privileges` tab.

To revoke a package privilege, click an assigned package and its assigned privilege from the list and then click the `Remove Package` button to revoke the privilege. To make the changes active, click the `Save` button or continue making other changes if necessary. Note that once the `Save` button is clicked, you’ll be returned to the list of privileges and be required to click the `Edit` button again to make further changes.

To change assigned package privileges, while in edit mode, click an assigned package and its assigned privilege from the list and then click the `Change Privileges` button to open a new popup window with the title `Change Privileges of` concatenated with the name of the package. A list of assigned and unassigned privileges for the package will appear. Select the checkbox to grant the privilege or deselect the checkbox to revoke the privilege. Use the `Yes/No` slider to manage the grantable to others privilege. Click the `OK` button at the bottom right of the window to apply your changes. Again, to make the changes active, click the `Save` button or continue making other changes if necessary until you’re ready to activate all changes.

#### Privileges on Users

The sixth tab in `Assign Privileges` window is named `Privileges on Users`. You’ll use this interface to grant the `Attach Debugger` privilege to the grantee for the current authenticated user. This GUI is limited to just one action. Clicking the `Add` button will automatically add the `Attach Debugger` privilege, and the grantor will give the user account access the registered systems within the SAP HANA cockpit. Click the `Save` button to grant the privilege or click the `Cancel` button to discard the change. If the privilege is already granted, click the `Remove` button to revoke the privilege.

### 4.3.3 Granting and Revoking Privileges with the SAP HANA Web-Based Development Workbench

The SAP HANA Web-Based Development Workbench security manager, hosted within the XS engine, provides a GUI you can use to create users, create roles, or manage security. You can access the SAP HANA Web-Based Development Workbench via a supported Internet browser. The following two URLs can be customized to match the details of your environment:

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/security`
*   `http://<sap_hana_host>: 80<instance_number>/sap/hana/ide/security`
