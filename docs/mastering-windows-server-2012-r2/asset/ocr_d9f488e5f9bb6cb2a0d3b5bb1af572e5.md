# METADATA CLEANUP

Something else to consider is if you lose a domain controller because of hardware failure or OS corruption, sometimes it's faster to use the ndsutil metadata clean command to remove the DC and then just install a fresh one with the same name and let Active Directory do its thing.

This link has some additional information on cleaning up server metadata in Active Directory: http://tinyurl.com/ws2012ntdsutil.

# Performing an Authoritative Restore

The purpose of an authoritative restore is to recover AD objects by marking the restored objects or by marking the new copy that should be replicated to the other domain controllers. Every time a change is made to AD DS, the version number of the restored object is incremented. Making an authoritative restore of deleted objects setting the version higher than the currently replicated version of the AD database.

Wherever possible, authoritative restores should be on the global catalog server so that group information can be fully recovered. If you isolate the global catalog server before it receives replication of the deletion you are trying to recover, you can restore the objects without first performing a non-authoritative restore. In other words, if you are quick enough, you can unplug the network cable from the global catalog server and avoid having to recover from a backup.

To perform an authoritative restore before the change has replicated, do the following:

+   1. Isolate the server by disconnecting the network cables or by typing the repadmin / options <servername> +DISABLE_INBOUND_REPL command.

+   2. Stop AD ds using Services Services Tools menu in Server Manager, as described earlier in this chapter, or by typing the net stop ntds command at an elevated command prompt.

+   3. At an elevated command prompt, type ndsutil, type authoritative restore, and press Enter.

+   4. Use the appropriate command for the type of object being restored:

+   * To restore a subtree, such as an entire OU, type restore subtree <DN>, where <DN> is the full distinguished name of the object being restored. For example, restore the HR OU in Bigfirm.com, type restore object "OU=HR,DC=bigfirm,DC=com".

+   * To restore a single object, such as a user account, type restore object <DN>, where <DN> is the full distinguished name of the object.

+   6. Make a note of any .txt or .ldi files that are generated and can be used to create any back links for the objects being restored:

+   * Back links contain the information for group memberships.

+   * The .txt files can be used to re-group memberships in other domains for the restored user accounts using the create ldi file command in Ndsutil in the other domains.