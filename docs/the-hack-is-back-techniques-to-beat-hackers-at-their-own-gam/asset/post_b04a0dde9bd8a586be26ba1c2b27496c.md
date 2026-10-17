
have DNS records with very low time-to-live values. If we mistakenly take down the availability of resources, users should only need to wait five minutes or reboot their machines to have access restored. However, we need to make sure that we reduce this chance as much as possible.

### Preventing Multicast DNS Attacks

To prevent and reduce the risk of multicast DNS attacks, we can enforce a GPO at the domain level to prevent the use of LLMNR. This is an effective control, as modern enterprise networks do not need fallback DNS resolution mechanisms outside of configured DNS servers.

## NTLM RELAYS

Named after the NT LAN Manager authentication protocol, NTLM relays exploit the very foundation of Windows authentication to attempt to gain unauthorized access to areas of the domain. By sitting in between two victims, an attacker can dictate and control the activity occurring.

To exploit this, we can use the NetExec tool to identify which machines on the domain do not enforce SMB signing. Locating these machines allows us to keep track of which machines can attempt to be exploited when relaying inbound connections. To complete this, we can run the command below:

```
nxc smb 192.168.56.0/24 --gen-relay-list relayable.txt
```

![](img/181571ad74cba0e6a2f38fcd2658651e_230_0.png)

**FIGURE 7.23** Running NetExec to get a list of machines that do not enforce SMB signing.

Now with the list of vulnerable machines saved as **relayable.txt**, we can use Impacket’s **ntlmrelayx.py** script to target the detected machines. What this script does is take incoming NTLM connections and attempt to relay them to other machines to establish a connection. When using the **-tf** switch, we can provide a target file to the program to attempt to create connections with. The **-socks** switch will establish a SOCKS proxy with any successful connections, allowing us to continue to leverage the connection as we see fit.

```
ntlmrelayx.py -tf relayable.txt -smb2 -socks
```

To practice this and get even more in-depth, there are several excellent workshops and resources available. One of the best to learn is from Jean-François Maes and is titled NTLM Relaying 101, this is available as a GitBook at https://jfmaes-1.gitbook.io/ntlm-relaying-like-a-boss-get-da-before-lunch/.

To fix this, enforcing SMB signing is crucial. This prevents the unauthorized manipulation of resources to protect the integrity of the domain.

## AUTHENTICATED ACCESS

Gaining authenticated access to AD can reveal a significant amount of information on how to attack the target. Not only do we have access to some potential SMB shares, but we can also gather information within LDAP for potential privilege escalation.

### SMB Shares

Access to an authenticated account may give more access to file shares using SMB across the computers in the domain. Users tend to save items within file shares such as passwords which can make escalation easier. Even worse, some administrators will store PowerShell and batch scripts that have credentials within them on the shares. Gaining access to SMB shares to search for sensitive files is not only effective, but it has ATT&CK ID assigned as T1135¹².

There are several tools to help us achieve this objective, such as the NetExec tool,¹³ the most recent replacement for the CrackMapExec tool. This tool can be used for several different functions, such as password spraying, but in this author’s experience, the tool shines in how it can systematically access SMB shares across a network. Instead of attempting SMB logins and enumeration at an individual and manual pace, NetExec allows us to supply a list of IPs or a CIDR to enumerate the shares. This increases our effectiveness in the testing we complete.

```
root@t470:~# nxc smb 192.168.56.0/24 -u robb.stark -p sexywolfy --shares
SMB 192.168.56.12 445 MEEREEN [*] Windows Server 2016 Standard Evaluation 14393 x64 (name:MEEREEN) (domain...
SMB 192.168.56.1 445 server_name [*] UNIX (name:server_name) (domain:WORKGROUP) (signing:False) (SMBv1:True)
SMB 192.168.56.10 445 KINGSLANDING [*] Windows 10.0 Build 17763 x64 (name:KINGSLANDING) (domain:sevenkingdoms...)
SMB 192.168.56.11 445 WINTERFELL [*] Windows 10.0 Build 17763 x64 (name:WINTERFELL) (domain:north.sevenkingdc
SMB 192.168.56.12 445 MEEREEN [*] essos.local\robb.stark:sexywolfy STATUS_LOGON_FAILURE
SMB 192.168.56.23 445 BRAAVOS [*] Windows Server 2016 Standard Evaluation 14393 x64 (name:BRAAVOS) (domain...
SMB 192.168.56.22 445 CASTELBLACK [*] Windows 10.0 Build 17763 x64 (name:CASTELBLACK) (domain:north.sevenkingt
SMB 192.168.56.1 445 server_name [*] WORKGROUP\robb.stark:sexywolfy STATUS_ACCESS_DENIED
SMB 192.168.56.1 445 server_name [*] Error enumerating shares: STATUS_ACCESS_DENIED
SMB 192.168.56.10 445 KINGSLANDING [-] sevenkingdoms.local\robb.stark:sexywolfy STATUS_LOGON_FAILURE
SMB 192.168.56.11 445 WINTERFELL [*] north.sevenkingdoms.local\robb.stark:sexywolfy (Pwn3d!)
SMB 192.168.56.23 445 BRAAVOS [*] essos.local\robb.stark:sexywolfy
SMB 192.168.56.22 445 CASTELBLACK [*] north.sevenkingdoms.local\robb.stark:sexywolfy
SMB 192.168.56.23 445 BRAAVOS [*] Enumerated shares
```

| Share | Permissions | Remark |
|---|---|---|
| ADMIN$ | READ,WRITE | Remote Admin |
| C$ | READ,WRITE | Default share |
| CertEnroll | | Active Directory Certificate Services share |
| IPC$ | | Remote IPC |
| public | Basic | Read share for all domain users |

```
SMB 192.168.56.22 445 CASTELBLACK [*] Enumerated shares ...
```

FIGURE 7.24 Running NetExec to enumerate shares across a CIDR with a known set of credentials.

In the case of the Uber breach in September of 2022, the attacker leveraged open SMB shares that contained plaintext administrator credentials in PowerShell scripts. This shows a clear and present impact of this threat and how difficult it can be to find it properly without regular penetration testing and threat emulation. Uber, a 318 billion dollar company struggled with this – how can we learn from their mistake to protect other environments?

### SYSVOL Share

The SYSVOL is a specific share within the Domain Controllers which is used to support domain functions. This folder exists to support AD functions within a domain and must be domain public for users and computers to access. Generally, there are a lot of Group Policy Objects and references in this folder. It is less common to find local admin passwords via Group Policy stored in these folders, but it is still very possible.

This GPO stores an encrypted local admin password within the public folder, however, Microsoft has published the encryption password online.¹⁴ This means that anyone who can find a local admin password within the SYSVOL folder can decrypt it to try and gain access to the local machines.

Along with this, many administrators will store domain scripts within the scripts folder on the SYSVOL. This is a common technique for admins to ensure that users and machines run a specific script on boot or logon. Some of these scripts will attempt to perform actions such as mapping drives or running additional programs, pay attention to these as they can reveal sensitive information.

In this author’s professional experience, one internal test revealed that a domain script on the SYSVOL\scripts folder leveraged an encrypted password for an administrator account. This password was used to run functions and processes as the elevated account when a domain user logged on. Simple reverse engineering of the binary and encrypted password revealed the plaintext password used by the account, which was one of several avenues used to compromise the domain.

### LOCAL ADMIN ACCESS

In many instances, we will gain administrative access to a local machine on the domain with the intent to escalate through to Domain Admin. There are several ways where this can be achieved, such as gathering the password or the NTLM hash for the local administrator account. It is important for sysadmins to have the ability to log into a machine as a local administrator to fix issues if the machine can’t reach the network. However, if machines all use the same local administrator password, it’s possible to use this authentication material to pivot around to other machines on the domain.

In order to remediate this, use the Microsoft Local Administrator Password Solution (LAPS). This uses Active Directory to manage the local administrator authentication material for unique passwords per machine. Implementing LAPS is simple and easy to ensure that it can be used inside as many environments as possible.

## BLOODHOUND

BloodHound is a tool developed by SpecterOps and is used to enumerate and uncover attack paths within AD permissions. BloodHound can uncover many difficult to identify or understand escalation paths and provides a convenient graph-based visualization. The tool can help effectively show who and how an escalation path can be leveraged within the environment.

BloodHound operates by using a collection agent to gather all of the information available within AD, then import it into a Neo4j database for storage. The BloodHound GUI connects to this database to perform analysis in a visual format. This visual analysis not only helps us as attackers to see escalation paths but helps sysadmins and business decision-makers understand and visually comprehend the level of risk. This author has consistently utilized screenshots from BloodHound in reports to customers to help display information in a digestible manner.

BloodHound is also a tool listed on the MITRE ATT&CK framework as tool ID S0521.¹⁵ There are at least four known and named threat actors who leverage BloodHound to exploit an AD domain for personal gain. Becoming familiar with this software will help us understand and display risk to customers to ultimately reduce operating risk.

Note that as of August 2023, the BloodHound Community Edition was released. This offers several benefits over the BloodHound Legacy version, such as an entirely containerized architecture. Beyond this, the Cypher queries are faster and the CE supports an API. For this section, we’ll explore BloodHound CE as BloodHound Legacy is no longer supported.

### Sniffing out the Data

To analyze an AD environment for potential escalation paths, the network must be enumerated with a collection tool to gain the list of all objects and their relationships. This is done with a BloodHound collection agent, which can be run via a C# executable, PowerShell script, or even Python from a Linux-based machine. Generally, this will require user-level permissions to bind to the Domain Controller.

This author prefers the Python version of the ingestor, also known as **bloodhound.py**. This tool is a part of the Kali repository and can be installed with **sudo apt install bloodhound.py**. Once installed via **apt**, it can be run with the **bloodhound-python** command. To collect data from AD to import into the BloodHound GUI, we must provide credentials to gather information. There are various collection methods, but generally we should choose **all** to ensure we have the most amount of data to search through the domain.
