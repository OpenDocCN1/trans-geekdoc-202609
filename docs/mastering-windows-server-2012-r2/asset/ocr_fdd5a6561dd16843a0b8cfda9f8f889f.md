# Replication of Group Policy Is Built In

GPOs replicate themselves automatically, with no work on your part. Active Directory is replicated using AD Replication (controlled by the Knowledge Consistency Checker and the Insite Site Topology Generator) and is controlled by the File Replication Service or Distributed File Service

# GPOs Undo Themselves When Removed

All the administrative template GPO settings write their information to contain parts of the registry and clean up themselves when the policy is removed or the GPO is deleted.
This fixes the dreaded "tattooing" that has plagued "policy management" since it was first introduced. For example, if you had created a system policy on a legacy system that everyone's background color was so nauseating and set up a policy to keep them from changing the color. These changes were written into the system's registry. If you deleted it, the policies in the registry would not be removed, and therefore the ugly background would remain intact on the system. This is called "tattooing". You'd actually have to write a new policy to undo the registry entries. With GPOs, that's necessary. Just removing the policy will undo its effects.

# You Need't Log On to Apply Group Settings

The true story of Group Policy is related to the "background refresh.\ Since all domain-based computers check in to see there are any changes every 90 minutes or so, policy settings are constantly being applied. This means that a setting that you make at 6 A.M. on a Monday morning to control some security setting on every desktop won't require the computers to be up and running. Rather, the background refresh will apply to the computer before the user arrives at 8 A.M.

On Windows 2000 and later with Active Directory, machines get their policy settings from the domain when they power up (recall machines log on also), and users get policies from their domain when they log on.

# Local Policies and Group Policy Objects

When you open the Group Policy tool (gpedit.msc), it automatically focuses on the local machine GPO, as shown in Figure 9.1. Administrators can use the tool to configure account settings (such as the minimum password length and number of logon attempts before locking the account), to set up auditing, and to specify other miscellaneous settings. However, the domain-based policy editor, the Group Policy Management Editor, includes a number of settings (including software installation and folder redirection) that are not available for local policies.

# GP Folder Structure

The local Group Policy folder structure is similar to that of other domain-based GPOs and is found in \Windows\system32\GroupPolicy.