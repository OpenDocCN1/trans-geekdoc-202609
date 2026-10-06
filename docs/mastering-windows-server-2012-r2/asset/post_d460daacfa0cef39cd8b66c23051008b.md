
## Chapter 9

## Group Policy: AD’s Gauntlet and Active Directory Delegation

When you talk about Active Directory, you must also talk about Group Policy. Group Policy is not a new technology for Active Directory, but it has grown and improved with every iteration of the operating system and service pack since it was first introduced in Windows 2000. The Group Policy technology and features that are delivered with Windows Server 2012 R2 are such drastic improvements from the original version that they almost seem like new technology. Changes and enhancements have come for managing Group Policy (the Group Policy Management Console and the Group Policy Management Editor), managing available settings (with more than 5,000 settings), controlling targeting objects, and troubleshooting your Group Policy infrastructure. If you are a veteran of Group Policy, you will certainly want to focus on the Group Policy preferences, GPMC, and troubleshooting sections in this chapter. In this chapter, you will learn to:

- Understand local policies and Group Policy objects
- Create GPOs
- Troubleshoot group policies
- Delegate control using organizational units
- Use advanced delegation to manually set individual permissions
- Find out which delegations have been set

## Group Policy Concepts

Let’s start with some important concepts, terms, and rules you need to know to master Group Policy. In the process of explaining the functionality of Group Policy, we will mention several settings without actually showing how to turn them on in Group Policy snap-in. Just focus on the concepts for now. Later in this section, we'll take you on a full tour of the Group Policy Management console (GPMC); we will cover the Group Policy application (including settings such as Enforce and Block Inheritance) and the expanded settings.

Administrators configure and deploy Group Policy objects (GPOs). GPOs are containers for groups of settings (policy settings) that can be applied to user and computer accounts throughout Active Directory. Policy objects are created using the Group Policy Management Editor (GPME), which is invoked by editing a GPO from the GPMC. The same GPO could specify a set of applications to be installed on all users' desktops, implement a strict policy of disk quotas and restrictions on the Explorer shell, and define domain-wide password and account lockout policies. It is possible to create one-encompassing GPO or several different GPOs, one for each type of function.

A GPO is made of two parts:

- **Computer Configuration**: Computer configuration policies manage machine-specific settings such as disk quotas, security auditing, and Event Log management.
- **User Configuration**: User policies apply user-specific settings such as application configuration, start menu management, and folder redirection.

However, there is a deal of overlap between the two, especially that Group Policy preferences have been introduced (on Group Policy preferences later in this chapter). It is not unusual to find the same policy in both User Configuration and Computer Configuration. Be prepared for the fact that you can apply settings to the domain, a site, or an OU. You can create multiple GPOs that apply to the same OU, and the order in which they are applied determines which settings "win." This is known as precedence.

## Policies Inherited and Cumulative

## or or

Group Policy settings are cumulative and inherited from parent directories. For example, the domain has several GPOs. So, some policy settings can be applied to the entire domain, while others target accounts or OUs upon which they are linked.

## Group Policy Power! Refresh Intervals

Policies apply in the background every 90 minutes, or with a 30-minute "randomization" to keep the domain controller from getting hit by hundreds or even thousands of computers at once. DCs differ from normal computers and refresh group policies every five minutes. There is, however, a policy to configure all of this, as you'll see later in this chapter. The refresh interval include folder redirection, software installation, script application, Group Policy preference preferences, and Group Policy preference drive maps. These are applied only at logon (for user accounts) or startup (for computer accounts); otherwise, you might end up uninstalling an application while someone is trying to use it. Or a user might be working in a folder as it is redirected to a new location. In, for data integrity these policies apply only in the "foreground" refresh of Group Policy.

## Group Policy Basics

To understand how Group Policy technology works in your Active Directory environment, it is best to understand how some of the Group Policy technology works "under the hood." If you are just becoming familiar with Group Policy, you will quickly see that many of the features that Group Policy possesses benefits over older technologies, such as system policies.
