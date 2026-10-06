# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

FIGURE 7.67 Active Directory Migration Tool Agent Dialog window

![](bbox=[0.32, 0.1, 0.74, 0.46])

The Agent Summary field displays the progress. For further information, you can view the migration log and agent detail. The agent detail provides another window detailing the agent's installation and run events.

The users need to be logged off for the workstation where this operation occurs. A locked workstation will also lock access to the profile. This causes the agent to perform an add operation, but it could still produce an error or unexpected reactions. From our experience, some users may not understand the difference between logged off and locked. We recommend asking users to restart their workstations when knocking off work. Then run the operation in off-hours.

After the operation is completed, the user can be logged on with the new user account. Your old desktop will be presented, and all the other profile-specific settings are available. In this case, their mapped drives to their home folder will be available. Their access to the home folder will verify whether the SID history is working as well.

In additional runs of the Security Translation Wizard, permissions on the home folder can be re-ACled.

# Migrating Computer Accounts

The process of migrating Directory Tool Agent looks similar to the Security Translation Wizard and the Active Directory Migration Tool Agent (see Figure 7.68). The Agent Summary includes a Post-check column. The operation performs the domain membership change, which will require a reboot. The verification of change is performed in the post-check. The reboot reboots the post-check retry settings. This sets the number of retries and the interval between each attempt. With little patience on your part, the operation completes.