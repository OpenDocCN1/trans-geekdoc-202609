
## Account Policies
Specified password restriction, lockout policies, and Kerberos policy.

- Local Policies Configures auditing and assigns user rights and miscellaneous security settings.

- Event Log Centralizes configuration options for the event log.

- Restricted Groups Enforces and controls group memberships for certain groups, such as the Administrators group.

- System Services Standardizes services, configurations, and protects against changes.

- Registry Creates templates for registry key permissions to control who can change what keys and to control access to parts of the registry.

- File System Creates templates for permissions on folders and files to ensure that files and directories keep the permissions you want them to.

- Public Key Policies Manages settings for organizations using a public key infrastructure.

- Software Restrictions Places restrictions on what software runs on a system. This new feature is designed to prevent viruses and untrusted software from running on a system.

## Leveraging Security Templates

To accomplish your "mass" security rollout from the previous example, you will need some way to get the settings "entered" and then "deployed." The deployment is easy, since you have AD and Group Policy. The question then becomes how you "enter" the security information or to stomp out the latest web server on all of computers if it can be tracked, refused, and quickly modified? The answer is security templates. We suggest that if you're overthinking it, just start using them. In this section, you'll see how.

Let's say you've decided you want to ensure the Power Groups on your workstations are empty—don't want anyone in them. You are also afraid of stomping out the latest web server on all of computers that have IIS, so you're going around and disabling Web Publishing Service on all servers that don't need it.

But, man, that's a lot of work. So, you plan B: the security requirements document. In this document, you outline what must be done for any updates or services approved at Acme Corporation. You distribute the document. And who has time to read? There is no easy way to check on systems to see whether they meet the requirements. Or so it seems.

Wouldn't it be great to just click a button and make these changes on every system? You can with a few tools: sedit.exe, which is an MMC snap-in named Security Configuration and Analysis, and security templates.

## What Templates Can Do

Basically, a security template is an ASCII file that you feed into a program named sedit.exe. That template is a set of instructions—a script—that lets you make many kinds of changes in your system.

Templates don't modify anything that you couldn't modify otherwise; they provide a nice, reproducible way to make modifications and easily audit systems to ensure that they meet the template's requirements. You could make any of these changes with the GUI, but it's time-consuming. With templates, you can change the following:

- NTFS Permissions If you want the directory C:\STUFF to have NTFS permissions of System/Full Control and Administrators/Full Control and deny access to everyone else, then a template can make that happen. And because you can apply templates not only to one machine but also to many (you're using group policies), you could enforce that set of NTFS permissions on the whole domain.

- Local Group Membership Perhaps you have a policy that workstations are set up so that the only accounts in the local administrators group are Domain Admins from the domain. But now and then, someone temporarily elevates a user account to the Administrators group with the intention of undoing the action as soon as the need is over. And, because someone is busy as all folks are, undoing never gets done. By applying a security template that says "only Administrator and Domain Admins can be in local,” reapplying the template kicks out who's not supposed to be.

- Local Security Policy Settings Every machine has dozens of local security settings, things like "Who can log in?", "How often should locally stored accounts be changed?", and "Who should be allowed to change the time?"

## Enforcing Security Settings

Templates automate the process of setting security information just as you had sat down and done it from the GUI. There is no magic guardian that constantly monitors a system to ensure that your desired settings are always enforced. The only way is to either reapply the template on some regular basis or create a GPO to apply the template, because security settings in GPO are updated.

## Working with Templates

It's easy to show how to work with templates with an example, let's build a template to do three things:
- We'll ensure that no one is in the Power Users group.
- We'll set NTFS permissions so that the directory C:\SECRET is accessible only to the local Administrators group.
- Finally, we'll shut down Internet Services, that pesky web server that seems to install itself on every operating system that Microsoft makes.

First, you'll need some tools. Let's build one custom tool using the MMC. Set it up like so:
1. Click Start, type mmc /a in the field, and then press Enter to bring up the empty MMC.
2. In the empty MMC, choose Add/Remove Snap-in from the File menu.
3. In the Add or Remove Snap-in dialog box, click Security Configuration and Analysis and then the Add button. Then Security Templates and Add again.
4. Click OK.
5. Save your new tool for future use.

Your tool should look like the one in Figure 9.24. Expand the Security Templates node, and add a new path. The path you want to add is C:\Windows\Security\Templates. Expand that, and you'll see the security.inf template.

![](img/41a3208e6906a3732620203b86cea7_530_0.png)

## Expanding the security.inf template

Expand the security.inf template, and you'll see, in the right pane, folders corresponding to everything you can control:
- Account Policies: Sets password, account lockout, and Kerberos policies
- Local Policies: Controls audit settings, user rights, and security options
- Event Log Settings: Controls parameters of how events are stored
- Restricted Groups: Controls what goes into and stays out of various local groups
- System Services: Turns services on and off and who has the rights to change any of that
- Registry: Sets permissions to change or view any given registry key (and which keys will be audited)
- File System: Controls NTFS permissions on folders and files

You're interested in building a new template from scratch. To do that, right-click the template path, and choose New Template from the context menu. Type in a name for the template and a description you want. The new template will appear as a folder in the left pane, along with the prebuilt templates. We've named ours Simple. First, let's clean up the Power Users group:
1. Open Simple.
2. Inside Simple, you'll see a folder named Restricted Groups. Click so that it appears in the left pane.
3. Right-click Restricted Groups, and choose AD Group.
4. Type in Power Users in the Add Group dialog box, or choose the Browse function to select the Power Users group.

Note if you are working from a domain controller, then you won't, of course, have a Power Users group.

By default, including a group in a security template tells the template to remove everyone from the group, you're finished. If you wanted to use the security template to put someone in the group, then just right-click the group and choose Properties, which lets you specify members of the group.

Next, let's set up the security template so that any system with a folder C:\SECRET will be accessible only to the local administrators.
1. Back in the left pane, right-click File System, and choose Add File.
2. In the dialog box that appears, you can either choose a particular directory or specify it in the name. Yes, the item was Add File, but you can choose directories as well.
3. Type C:\SECRET, and click OK.
Now you'll see the standard Windows NTFS dialog box.
4. Delete permissions for all users and groups except for Administrators. Grant Full Control to Administrators.
The program will ask whether you want to move these permissions to apply only to this folder or to all children.
5. Set it as you like, and click OK.

Finally, let's shut down IIS:
1. Click System Services.
2. In the right pane, right-click World Web Publishing Services, and choose Properties.
3. Select the Define This Policy Setting in the Template check box, and click the Disabled radio button.
4. Click OK.
