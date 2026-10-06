# PowerShell History Viewer

You just saw in Figure 7:22 how tasks previously executed in Active Directory Administrative Center are translated into PowerShell and displayed in Windows PowerShell History. Because ADAC is on top of PowerShell, everything will be shown in the PowerShell History as commands. Windows Server 2012 Active Directory has more than 140 PowerShell cmdlets, and it would take a lot of time to learn the commands and the specific syntax. Therefore we recommend that you keep an eye on this window it will help you in learning these commands.

At the top of the PowerShell History window are several fields:

+   **Copy** You can use Copy to copy one or multiple commands. For copying multiple commands you can hold Ctrl and click each of the commands you would like to:

+   **Search** With the Search field you can search any cmdlet within PowerShell History. Just type the few letters, and the panel will narrow down your search results.

+   **Start and End Task** If you want to group your commands, you can click Start Task before executing any action in ADAC and give it a name, and click End Task as soon as you have finished the execution. For the next group of commands, you would repeat these steps.

+   **Clear All** This will clear your history commands.

+   **Show All** If you select Show All, every task you perform in the ADAC will be shown in the History window. If you deselect this, only tasks that manipulate Active Directory will show up. The default is for the checkbox to be selected.

# Delegating Control Using Organizational Units

Earlier in this chapter, I mentioned that one of the reasons for creating an OU was to delegate control, and certainly one of AD's strengths is that it can let you grant partial or complete administrative powers to a group of users. This means that would be possible for a one-domain network to be subdivided into parts, like Uptown and Downtown, Marketing, Engineering, and Management. Whether the most common requirement or reason to delegate control to an OU is to help people reset user passwords. Another quite requested permission is to be able to modify certain attributes of users or group objects. There are many other requirements you will be facing during your Active Directory administration center. Even if you're not interested in delegation, Chapter 9 gives you a very good start on delegating control in Active Directory.

# Domain Maintenance Tasks

After you have established your domain, you will need to do some domain maintenance. Although this section doesn't cover everything you will need to do, it does cover basic tasks:

+   - Joining a domain
- Decommissioning a DC
- Troubleshooting AD DNS
- Raising the domain and forest functional levels