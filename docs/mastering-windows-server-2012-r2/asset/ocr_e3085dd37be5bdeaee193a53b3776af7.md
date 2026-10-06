# CHAPTER 9- GROUP POLICY: AD'S GAUNTLET AND ACTIVE DIRECTORY DELEGATION

If you have a Windows Server 2012 Active Directory and you deleted the BKvanagh account, then you should reanimate it from the Active Directory Recycle Bin.

If you deleted the user account and don't have a Windows Server 2012 Active Directory, then you will have to re-create it and add the user to all the groups that she was before. This is a time-consuming process.

You should disable the BCvanagh account to comply with the security officer and the personnel department. You can delete the account after a predetermined time has passed and the user has not returned to the organization.

# Chapter 9: Group Policy: AD's Gauntlet and Active Directory Delegation

Understand local policies and Group Policy objects. Every Windows computer from Windows 2000 Professional and up has a local group policies, which can accommodate for various situations where the computer might be located. There are Group Policy objects stored in Active Directory too, which can allow for administration of computers and users who are associated with the domain.

Master It Which of the following is not a local group policy?

+   - Local Computer Policy

+   - Administrator

+   - Non-Administrator

+   - All Users

Solution All Users is not a local group policy.

Create GPOs. Group Policy objects can and should be created within your Active Directory domain. These additional GPOs will allow you to control settings, software, and security on the different users and computers that you have within the domain. GPOs are typically linked to O but can be linked to the domain node and AD sites as well. GPOs are created within AD by using the Group Policy Management console.

Master It Create a new GPO and link it to the HRUsers OU.

Solution Create the GPO and link it to HRUsers OU:

+   1. Create the HRUsers OU under the domain.

+   2. Within the GPMC, right-click the HRUsers OU, and select the option to create and link a GPO.

+   3. Give the new GPO a name of HRUserSecurity.

Troubleshoot group policies. At times a GPO setting or group policy fails to apply. There can be many reasons for this, and you can use many tools to investigate the issue. Some tools,