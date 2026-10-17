What is interesting here is that I was not positive if that DefaultAccount was something I created or was actually supposed to be there. A simple Google search did tell me that The DefaultAccount or Default System Managed Account (DSMA), is a built-in account introduced in Windows 10 version 1607 and Windows Server 2016. So that account is supposed to be on this version of the Windows OS but not all of the different versions on Windows. It can vary so it can be quite tricky, as you will see in the next example, and even experienced administrators might have to research to find the list of accounts.

On this older version of Windows, there were a bunch of default accounts that were supposed to be on there. You might see some similar accounts on the modern versions of Windows depending on what is installed and configured. The HelpAssistant and Support accounts are legitimate accounts included with this version of Windows. The IWAM and IUSR accounts are created when the user installs Internet Information Services, so those are also supposed to be there. On newer versions of Windows, I have also seen a WDAUtilityAccount which is related to Windows Defender. The fake account I created is HelperAssistant. Notice that I tried to keep the capitalization similar to the HelpAssistant account.

![](bbox=[0.107, 0.316, 0.893, 0.454])

**FIGURE 9.21** Which accounts are legitimate?

The administrator and guest accounts can also be enabled and used by the attacker if it is not in use. Starting with Windows Vista, the client OS Versions (Windows NT client list includes NT Workstation, 2000 Pro, XP, Vista, 8.1, 10, and 11) the Administrator and Guest accounts would be disabled by default. In the Windows Server versions (NT Server, 2000 Server, 2003, 2008, 2012, 2016, 2019, and 2022), the Administrator Account is enabled, and the guest account is disabled. And, speaking of Windows Server, on a Domain Controller, which can have dozens, hundreds, or thousands of accounts, making tracking user accounts a much more complex situation, as it is even more difficult to find unauthorized accounts. One suggestion to help find unauthorized accounts is to view the accounts with Administrative privileges on the system. When I do this on the Windows server, I only find two accounts. Standard accounts and accounts that are members of group like backup operators can still do damage to the system, but most of the time the attacker is going to need administrative rights for their tasks.

The command I used to view the administrator accounts was: **net localgroup administrators**

![](bbox=[0.107, 0.715, 0.893, 0.919])

**FIGURE 9.22** May I speak with an Administrator?