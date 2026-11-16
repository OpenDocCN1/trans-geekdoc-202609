# # Change and Configuration Management

Organizations put a lot of effort into securing assets and hardening systems. To manage required system changes, controls must be put in place to make sure all changes are documented and approved. This is accomplished through the change management process. Any time a change is to be made, it is important to verify what is being requested, how it will affect the systems, and what unexpected actions might occur. Most organizations do not directly deploy a patch without first testing it to see what changes will occur after the patch has been installed. It is important to ensure that changes do not somehow diminish or reduce the security of a system. Configuration management should also provide a means to roll back or undo any applied changes in the event that negative effects occur because of the change. Although change management processes can be implemented slightly differently in various organizations, the following is a generic process:

+   1. Request a change.
+   2. Approve the change.
+   3. Catalog the change.
+   4. Schedule the change.
+   5. Prepare a means to roll back the change, if needed.
+   6. Implement the change.
+   7. Test or confirm the change.
+   8. Report the completion of the change to the appropriate individuals/groups.

> **Tip**
> 
> While some might question the need to have a rollback plan, things can go wrong. For example, in December 2020, Microsoft’s Windows 10 update conflicted with CORSAIR Utility Engine software and caused Windows to crash.