
**Note:** Continue to read the full first chapter before attempting this because you might want to ....

When you boot to the installation media, you are able to access the command prompt without any type of authentication. You will know that you are in the right place, when you see an `X:\Sources>` prompt. At that prompt, you will type the following command to keep a copy of the legitimate file so you can replace it later if needed.

`copy C:\Windows\System32\Utilman.exe C:\Windows\System32\Utilman.1`

Then, type:

`copy C:\Windows\System32\cmd.exe C:\Windows\System32\Utilman.exe`

Click Y to replace the file. After that, close your command prompt by clicking the red X in the top right corner and then click Continue to Windows. At the Windows logon screen, click the Ease of Access button (`Utilman.exe`) to get a command prompt. I will now review how I got to this point. (I am a teacher, so I like to review ☺).

![](img/181571ad74cba0e6a2f38fcd2658651e_17_0.png)

FIGURE 1.3 Renaming Utilman.exe cmd.exe.

## BREAKING INTO THE WINDOWS OPERATING SYSTEM – STEP-BY-STEP WITH SCREENSHOTS

*All of the Steps to break into the Windows Operating System without a password:*

1. Get a copy of the installation media for Windows on a USB drive or legacy media like DVD.
   Note: With a DVD, you select that choice in step 2 and press the space bar immediately.
2. Enter the boot menu of the computer to ensure you can boot to installation media (if needed).
   Note that if you have secure boot enabled, that will need to be disabled in the BIOS (Figure 1.4).

![](img/181571ad74cba0e6a2f38fcd2658651e_17_1.png)

FIGURE 1.4 BIOS Boot Menu options.

3. You should get to a Windows installation screen where you can select the Language. Click Next.
4. At this point, **DO NOT CLICK** the Install button. Instead, click Repair your Computer.
   **Note:** Going through the installation process can wipe out all of your data (Figure 1.5).

![](img/181571ad74cba0e6a2f38fcd2658651e_18_0.png)

**FIGURE 1.5** Don’t install now, instead repair your computer.

5. Select Troubleshoot from the list of options (Figure 1.6).

![](img/181571ad74cba0e6a2f38fcd2658651e_18_1.png)

**FIGURE 1.6** Troubleshoot.

6. Select Command Prompt from the list of Advanced options (Figure 1.7).

![](img/181571ad74cba0e6a2f38fcd2658651e_18_2.png)

**FIGURE 1.7** Command prompt.

Once you have a command prompt, you can:

- Create a user and add the user to the administrators group.
- Reset a password for a user.
- Enable the administrator account and set a password for the account.
- Open the User Manager on certain versions of Windows.

Note: This “back door” can be implanted on a targeted system to provide quick and continued access.

In this case, I am using Windows 10 Professional, and I can just reset the password by opening the User Manager program from the command prompt by typing `lusrmgr.msc` (as seen below). From there, you have your choice of what you can do. One option is to reset the password for the default account on the system. If you are using a version of Windows like Home that does not support the local user manager, then you can just type:

`net user jesse P@ssw0rd`

replacing Jesse with your username and P@ssw0rd with the password you want to use for the system. It is important to note that if your name has a space in it, you need quotes:

`net user "Jesse Varsalone" P@ssw0rd`

It is important to note that this will not allow you to log in as that user and access all of their websites and logins, which could include various sites many people use frequently, including Gmail, Office 365, banking sites, Coinbase, etc. Resetting a user’s password will result in limiting the hacker’s ability to further exploit the web logins and passwords (or l00t) that go along with the user’s accounts. If you want to hack well and get the “Golden Nugget” (great place to stay for Defcon btw), you will have to work a little harder. We will examine the more devious methods for post-exploitation capabilities in the next section of this chapter.

If you are resetting your own password, then just go into the Users folder, and then right click on your name and then select set password (as seen below). If you are completing the task, you can change your password here, so you are able to log into the system if you forgot it. If you are an attacker, and you reset the password for the account, the person who uses the computer will almost certainly know that something has changed on their system if they cannot log in with the password they have been using.

![](img/181571ad74cba0e6a2f38fcd2658651e_20_0.png)

FIGURE 1.10 The Local User Manager of Windows Pro versions.

This attack should work on every version of Windows back to Windows 2000, as Windows NT did not have any accessibility options. For the older operating systems, you can use Kali or BackTrack to perform similar steps. This is described in Defense Against the Black Arts, which is now a freely accessible eBook. Unbelievably, for Windows 95, 98, and ME (and Windows 3.11), you can click cancel at login and get into the system.

## POST-EXPLOITATION

After resetting the main user account for the Windows system, I was able to log in to that account. After that, I have unfettered administrative access to the machine. This is a great way to reset a password for a machine when a user who has given you permission to help them get into their system when they forgot the password. It also would be a viable option for an attacker who is trying to break into a system that they do not have the password to. Here is the good news and bad news, depending on what the purpose for getting into the machine is. If a hacker changes that password, based on my testing, they will not be able to access the websites and logins stored in Chrome or Microsoft Edge once they change the password. Now, you can still access all of their documents, pictures, and other critical files. However, the “keys to the kingdom” may actually lie in getting those website logins, especially if they are tied to bank/crypto accounts, personal email, or work email accounts. We will explore this next.

![](img/181571ad74cba0e6a2f38fcd2658651e_21_0.png)

FIGURE 1.11 Typical PDFs that can be found on a computer system.

Most people store a treasure trove of critical and personal information in documents, PDFs, Excel Spreadsheets, text files (with passwords), and other files. On systems I had permission to access, I have even seen things like tax return documents as well as credit card numbers with expiration dates and CVV numbers stored into text files on systems (likely so the user can copy and paste them when they order things online). I store some of my credit cards in Chrome as well as on some of the websites where I make frequent purchases. People who are more paranoid about storing their bank or credit card information on various websites they make purchases from might tend to put them in local files on their computers so they can copy and paste the information when needed. They could be less willing to store this type of information remotely because they are trying to avoid their credit card being used to make unauthorized purchases if that company or their account gets breached. However, storing credentials or credit card information on a local machine is not a more secure strategy because files like this are at risk if someone gets physical access to the machine or if an attacker compromises the workstation remotely using an exploit, and can download files. Like in a Capture the Flag event, your ability to search through the noise can be critical to finding the “l00t” within a system. The Windows search feature and the quick access to recently opened documents will be helpful, but keep in mind that an average Windows system might have well over 500,000 to over a million files. Using a common phrase like PASS may lead you somewhere. Having some forensic know-how would be helpful as you can sort items by date modified.
