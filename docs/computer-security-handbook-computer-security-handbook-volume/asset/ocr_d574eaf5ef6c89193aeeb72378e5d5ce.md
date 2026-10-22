will display the user IDs and passwords in the local system cache. These can then be cracked using rainbow tables or cracking software back at the attacker’s location.

The second step is to look at the host network connections to determine what computers the host is communicating with. The logic behind this is simple—any credentials in the local computer will very likely work on other hosts the system is interacting with. Remember that the purpose of user IDs is to provide authentication to other systems for the purpose of using them. Using the cracked password for the locally cached user IDs, the attacker connects to the subsequent systems and proceeds to extract the user IDs and password hashes from that host. The process of moving from host to host like this is termed lateral movement. It is especially important to note that the attackers are not using malware to accomplish this access. They are using legitimate user IDs and passwords. Ultimately, the attacker will continue this process until they find a system with an administrative account that will give them access across the entire environment. It is rare for them to have to traverse more than six to ten systems in order to find one with a network or domain administrator account cached. Once they have an administrative account they are free to use it to move throughout the network.

In addition to obtaining local user IDs and passwords from system caches, the attackers also map the target environment at this stage. Mapping the network is done through simple querying of Active Directory. The simplest way for the attackers to gain information about the environment is with a series of simple commands:

```
net group "domain computers" /domain
net group "domain users" /domain
net group "domain controllers" /domain
net group "domain admins" /domain
```

If you aren’t familiar with those commands, you should try them. The only requirement is to do them from a computer that is a member of the local domain. No administrative credentials are necessary. The result is a list of all computers, users, domain controllers, and domain admin accounts in the environment. This information is returned immediately and is far more useful for attackers’ purposes than running a tool like nmap. A further benefit is that the use of these commands is very, very difficult to detect as compared to nmap or similar tools that are very noisy. When the attackers want to gain more thorough information about an environment they will typically use dsquery and dsget. These are two command line tools provided by Microsoft to query active directory. Here are the contents of a batch script that was recovered from a recent incursion showing the use of these tools.

```
dsquery user -limit 0 | dsget user -samid -display -title -email -dept -office -company -c >1
dsquery user -limit 0 | dsget user -samid -pwdneverexpires -accexpir es -loscr -profile -hmdir -hmdrv -c >2
dsquery user -limit 0 | dsget user -c > 3
dsquery group -limit 0 |dsget group -c >g
dsquery subnet -limit 0 |dsget subnet -c >sn
dsquery site -limit 0 |dsget site -c >s
dsquery computer -limit 0 |dsget computer -c>c
dsquery ou -limit 0 | dsget ou -c>o
```

Attackers understand that users leave organizations and change roles. To ensure they have plenty of user IDs at their disposal it is a high priority for them to dump the entire domain credentials. This usually occurs within minutes of them achieving an administrative account with sufficient credentials. Their tool of choice for this is the