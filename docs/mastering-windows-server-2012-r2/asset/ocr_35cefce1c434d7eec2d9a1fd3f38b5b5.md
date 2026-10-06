# 342 CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

dnscmd /EnlistDirectoryPartition <QDN of partition>

+   4. As a last step, examine the DNS server settings and configure them to your company standard.

# POST-MIGRATION PROCEDURES

You should verify the domain services. You can perform tool-based tests with the Event Viewer, DCDiag, and NetDiag to see if there are initial problems. You should perform user acceptance tests well, such as attempting to log on and accessing network resources with the new domain controller as the available authentication service.
Given the plans for the migration process, you should perform the following:

+   * FSMO role transfers and GC assignment.
* IP address reassignment.
* Network name reassignment. The domain controller can be renamed using the System applet (sysdm.cpl) in Control Panel or the rename command.
* DNS, reassignment of the standard primary zones may be required.

> GOOD TO KNOW...
After adding a Windows Server 2012 domain controller to an existing domain, you should transfer the FSMO roles to the newest domain controller.

# REPURPOSING HARDWARE

The swing migration provides the opportunity to redeploy an existing domain controller as a Windows Server 2012 domain controller, although it may not have the correct upgrade path available. For example, you may have a domain controller capable of running both 64- and 32-bit versions of Windows Server. Remember, Windows Server 2012 comes in 64-bit only, so upgrading the original server would be possible.
This procedure requires an available virtual machine or hardware that can support Windows Server 2012. This spare machine provides an intermediate phase between the two Active Directory states. Follow these steps:

+   1. Prep the forest/schema and design.
2. Build a Windows Server 2012 member server on the spare machine.
3. Verify that DNS is supporting Active Directory adequately.
4. Prep the source server.
5. Promote the spare member server.
* Similar to the post-migration procedures, you will want to ensure everything is stable within the network and that users can access resources.