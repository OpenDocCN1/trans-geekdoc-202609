
Another wireless attack is the WPS attack. Wi-Fi Protected Setup (WPS) requires a PIN to connect to the WAP. The WPS attack attempts to intercept that PIN in transmission, connect to the WAP, and then steal the WPA2 password.

#### Cell Phone Attacks

There are many ways to attack cell phones; the more common attacks are briefly described here.

*   **Bluesnarfing:** `Unauthorized access of information from a Bluetooth device`.

*   **Blue jacking:** The process of using another Bluetooth device that is within range (depending on the version of Bluetooth it could be 10 to 240 meters) and sending unsolicited messages to the target.

*   **Bluebugging:** Similar to bluesnarfing, `bluebugging accesses and uses all phone features`.

*   **Pod slurping:** Using a device such as an iPod to illicitly confidential data by directly plugging it into a computer where the data are held.

#### Password Cracking

Doing password cracking is easiest when one can actually get physical access to a machine. This is not as difficult as it sounds. Many organizations (such as universities) have kiosk machines where someone can use the system with minimal/guest privileges. A skilled hacker can use this access to gain further access.

##### OphCrack

A very popular tool for cracking Windows passwords is `OphCrack`. `OphCrack` can be downloaded from [`http://ophcrack.sourceforge.net`](http://ophcrack.sourceforge.net). It is based on an understanding of how Windows passwords work. Windows passwords are stored in a hash file in one of the system directories, usually `C:\WINDOWS\system32\config\` in a SAM file. SAM is an acronym for Security Accounts Manager. The passwords are stored as a hash. (Hashes will be discussed in detail in [`Chapter 8`](#ch08.xhtml#ch08), “[Encryption](#ch08.xhtml#ch08).”) What Windows does is hash the password you type in and compare it to the hash found in the SAM file. If there is a match, then you are logged in. To prevent someone from copying the SAM file and taking it off to try to brute force it, as soon as Windows begins the boot process, the operating system locks the SAM file. What `OphCrack` does is boot to Linux and then get the SAM file and look up the hashed passwords in a large table of hashed values it has, searching for a match. If it finds one, then the matching text in that table of hashed values is the password. You can see `OphCrack` in [`Figure 6.8`](#ch06.xhtml#ch06fig08).

![Figure 6.8 OphCrack. ¶  ¶ Screenshot for Ophcrack is shown. The options available at the top of the window are, load, delete, save, tables, crack, help, and exit. The option "Save" is selected. Three options are present below these options. They are Progress (selected), statistics, Preferences. The details of the user, LM hash, NT hash, LM pwd1, LM pwd2, NT pwd are given. The second half of the window displays table, directory, status, and progress. ¶ ](Images/06fig08.jpg)

**Figure 6.8** `OphCrack`. ¶ 

This tool is remarkably easy to use. Just put the `OphCrack` CD into the machine and reboot. During the boot process you can press F12 for a boot menu and tell the system to boot from CD. You will then start `OphCrack`. It should be noted that longer passwords (as of this writing, longer than 10 characters) are usually not crackable by `OphCrack`.

Assuming `OphCrack` is successful (it isn’t always), what can the attacker do with this? At best she simply got the local machine admin account, and not a domain account. Well, this can be used to then gain domain access. One simple technique is to create a script that will in turn create a domain admin account. The script is simple:

[Click here to view code image](Images/ch06_images.xhtml#p168pro01)

```
net user /domain /add localaccountname password
net group /domain "Domain Admins" /add localaccount
```

Obviously, if the attacker executes this script, it will not work. One must be a domain admin for it to work. So the attacker saves this script to the All Users startup folder. The next time a domain admin logs on to this system, the script will successfully execute. But the attacker may not want to wait until that happens. In order to speed up the process, the attacker causes some minor problem in the system (changes settings, alters configuration, and so on). In many organizations, the tech support personnel are in the domain admins group. When a tech support person logs on to the system to correct the problem, the script will successfully run.

### Malware Creation

In this section we will briefly discuss how easy it is to create malware. In [Chapter 5](#ch05.xhtml#ch05), “[Malware](#ch05.xhtml#ch05),” you saw the tool eLiTeWrap. In this section you will see the methods used to actually create viruses. This is not in any way an encouragement for you to create such viruses. It is meant to educate you on why such malware is so common.

For many years, one needed significant programming skills in order to create a virus. However, in recent years there have been a number of tools developed to create viruses. These tools allow the end user to click a few buttons and create a virus. This is one reason viruses are becoming so prevalent. One such tool is the `TeraBIT Virus Maker`, shown in [`Figure 6.9`](#ch06.xhtml#ch06fig09).

![Figure 6.9 TeraBIT Virus Maker. ¶  ¶ Screenshot for TeraBIT virus maker is shown. Several options with checkboxes are displayed in the window. Of those options, the selected options are, Avoid opening notepad, disable task manager, and spread with folders. ¶ ](Images/06fig09.jpg)

**Figure 6.9** `TeraBIT Virus Maker`. ¶ 

Tools like this make it very easy for even a novice to create a virus. When tools like this become prevalent, tools that automate some specific computer attack, then one can expect a great many more such attacks.

You can easily see from the options that `TeraBIT Virus Maker` can create some rather damaging malware. It is important to realize that this is only one option that a malware creator has. There are a number of tools on the Internet that help create viruses. There are even ransomware development kits.

In addition to these tools, there are websites that contain catalogs of malware code. Anyone with only moderate programming skills can download the code for a virus and modify that malware for his specific needs. You can think of this as a sort of cyber weapons proliferation.

This proliferation of cyber weapons is the primary reason for this section in this chapter. It is critical that security professionals, or aspiring security professionals, be aware of just how easy it is to create a virus. This means we should reasonably expect to see more viruses as time goes on. Of course, there are still custom written viruses, and these are in fact the most effective form of malware. But the proliferation of tools and source code means that even those with only minimal technical skills can create viruses.

#### Windows Hacking Techniques

Given the ubiquitous nature of Microsoft Windows, it should be no surprise that there are a wide range of attacks specifically aimed at that operating system. In this section, we will briefly look at some of these.

##### Pass the Hash

We will examine cryptographic hashes at some length in [`Chapter 8`](#ch08.xhtml#ch08). For now just accept that many systems store passwords as a cryptographic hash. This is done because it is impossible to “unhash” something.

The pass the hash attack essentially realizes that the hash cannot be reversed; rather than trying to find out what the password is, the attacker just sends over the hash. If the attacker can obtain a valid username and user password hashes values (just the hash—the attacker does not know the actual password), then the hacker can use that hash, without ever knowing the actual password.
