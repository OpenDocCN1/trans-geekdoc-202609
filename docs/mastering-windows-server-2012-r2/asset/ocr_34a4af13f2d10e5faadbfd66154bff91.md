# AVOID REPEAT PASSWORD PROMPTS AFTER A PASSWORD CHANGE

If a user has more than one computer and is logged into both (for example, if they have both a laptop and a desktop computer), then they should log out and log back in both computers after changing the password. The session will still work, but because their domain password will have changed, this can lead to repeated password prompts for network resources such as Exchange servers, SharePoint sites, and other applications requiring authentication. You can keep typing in passwords when prompted, but it's simplest to log in with the new password to avoid the prompts.

# Connecting to Network Resources

One of the main reasons to join a domain is to access resources on the domain, such as the printer down the hall or some documents that you need to work on. You could access company photos, slide shows, and other media to make a marketing campaign. Whatever your need, you don't need to have these items and devices hooked or stored directly on your client machine. In fact, having stored on the network is ideal because they are more secure than (access is centrally controlled, and ideally the are backed up regularly). Examples of network resources include the following:

+   * Printers
* Shared folders and files
* Wireless devices (such as wireless printers)
* Services (such as Web Services)
* Company applications

Connecting to shared resources is easy for users, thanks to many of the changes in Active Directory and Group Policy. You can still use features like Network Discovery as a way for your computer to find resources on the network easily, although in most enterprises this is not recommended. With the introduction to Group Policy: Preferences it can now publish resources more easily for employees or departments through Group Policy objects and membership in domain groups. Users can continue to search Active Directory for resources they may need. This means that the user doesn't need to know where the device is installed or connected. The user might not know the exact name of a shared folder or printer or the server where it's stored. As long as the resource is published to Active Directory, with a little searching the shared resource will most likely be able to find and utilize the resource.

There are several ways to access shared resources. This section will expand on these more common ways for each of the client operating systems addressed in this chapter:

+   * Resources are published to you through Group Policy objects.
* You can search for and access resources that are published in Active Directory.
* You can attach to shared network resources (for example, shared folders and printers) by the command line.