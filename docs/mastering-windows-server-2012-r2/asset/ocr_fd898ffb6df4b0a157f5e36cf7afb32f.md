# Account Policies Specified password restriction, lockout policies, and Kerberos policy.

Local Policies Configures auditing and assigns user rights and miscellaneous security settings.

Event Log Centralizes configuration options for the event log.

Restricted Groups Enforces and controls group memberships for certain groups, such as the Administrators group.

System Services Standardizes services, configurations, and protects against changes.

Registry Creates templates for registry key permissions to control who can change what keys and to control access to parts of the registry.

File System Creates templates for permissions on folders and files to ensure that files and directories keep the permissions you want them to.

Public Key Policies Manages settings for organizations using a public key infrastructure.

Software Restrictions Places restrictions on what software runs on a system. This new feature is designed to prevent viruses and untrusted software from running on a system.

# Leveraging Security Templates

To accomplish your "mass" security rollout from the previous example, you will need some way to get the settings "entered" and then "deployed." The deployment is easy, since you have AD and Group Policy. The question then becomes how you "enter" the security information or to stomp out the latest web server on all of computers if it can be tracked, refused, and quickly modified? The answer is security templates. We suggest that if you're overthinking it, just start using them. In this section, you'll see how.

Let's say you've decided you want to ensure the Power Groups on your workstations are empty—don't want anyone in them. You are also afraid of stomping out the latest web server on all of computers that have IIS, so you're going around and disabling Web Publishing Service on all servers that don't need it.

But, man, that's a lot of work. So, you plan B: the security requirements document. In this document, you outline what must be done for any updates or services approved at Acme Corporation. You distribute the document. And who has time to read? There is no easy way to check on systems to see whether they meet the requirements. Or so it seems.

Wouldn't it be great to just click a button and make these changes on every system? You can with a few tools: sedit.exe, which is an MMC snap-in named Security Configuration and Analysis, and security templates.

# What Templates Can Do

Basically, a security template is an ASCII file that you feed into a program named sedit.exe. That template is a set of instructions—a script—that lets you make many kinds of changes in your system.

Templates don't modify anything that you couldn't modify otherwise; they provide a nice, reproducible way to make modifications and easily audit systems to ensure that they meet the template's requirements. You could make any of these changes with the GUI, but it's time-consuming. With templates, you can change the following:

NTFS Permissions If you want the directory C: \STUFF to have NTFS permissions of System/Full Control and Administrators/Full Control and deny access to everyone else, then a template can make that happen. And because you can apply templates not only to one machine but also to many (you're using group policies), you could enforce that set of NTFS permissions on the whole domain.