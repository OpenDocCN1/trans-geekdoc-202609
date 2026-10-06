+   3. From within the MMC console, select the File menu from the toolbar.

+   4. Select Add/Remove Snap-in in the drop-down menu.

+   5. Select Group Policy Object Editor from the list of snap-ins.

+   6. Leave Local Computer as the entry under Group Policy Object.

+   7. Click the Browse button.

+   8. Select the Users tab in a Group Policy Object dialog box.

+   9. Select the desired user account from the list, and then click the OK button.

+   10. Click Finish in the Select Group Policy Object dialog box.

+   11. Click OK in the Add or Remove Snap-ins dialog box.

+   12. Expand the Local Computer\username> Policy node in the console.

# Creating GPOs

Now that you understand the major concepts with Group Policy and know the difference between local GPOs and domain-based GPOs, let's go through the steps of creating and editing a domain-based GPO. In this section, we'll show you all the settings we discussed in the preceding "theory" section.

# DOMAIN-BASED GPOs

From this point forward, we will be focusing on only domain-based GPOs, because they are the preferred, local and secure way to deploy the settings that exist in a GPO.

You will be using the GPMC to manage all domain-based GPOs. With Windows Server 2012 R2, you will need to install the GPMC using Server Manager, as you saw in Chapter 2, "Installing and Upgrading to Windows Server 2012 R2."

After the GPMC is installed, it shows up under the Start > Administrative Tools menu. Once you select it from this list, the GPMC tool opens and displays the domain in your management computer has membership, as shown in Figure 9.4.

To create a new GPO in the domain, you will need to expand the GPMC structure such that you can see all the nodes that exist under the domain, as shown in Figure 9.5.

+   1. Right-click the Group Policy Objects node, and select New.

+   2. In the New GPO dialog box, type the name for the GPO (in this case Desktop Security), and then click the OK button.

This will create a blank GPO called Desktop Security, which is not linked to any container in the domain yet. At this point, you will want to configure the GPO settings and link it to the site, the domain, or an OU. To link a GPO to a node in Active Directory, follow these steps: