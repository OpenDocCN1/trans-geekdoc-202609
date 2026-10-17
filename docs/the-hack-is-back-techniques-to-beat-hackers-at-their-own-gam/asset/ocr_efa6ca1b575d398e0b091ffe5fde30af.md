In some cases, the hacker might be on a Workstation and need to get the important proprietary data from the file server. Fortunately for the hackers (and end users), there are some cases where the drives to important shares are pre-mapped and the command net use will display a list of the Workstation’s mapped shared. Network Shares are important resources where end users can access, store, and backup files and collaborate with other users within their organization. In the case if these shares have data worth stealing, the attackers can exfiltrate the data right out of the network using Invoke-RestMethod.

![](bbox=[0.1, 0.18, 0.89, 0.28])

# FIGURE 8.29 Net use.

If the attacker is not lucky enough to have any shared drives on their compromised workstation, then they can use the ipconfig command to find the Domain Controller or Domain Name System (DNS) Servers (sometimes one in the same) on the network which may have one or more file shares. These servers can often be found by viewing the Workstation’s DNS address. And, if the hacker gains local administrator access, they can connect to any other system they can reach on the network with the same username and password. Unfortunately, I have seen too many networks where the local administrator username and password are the same and the hacker can have a field day moving from box to box in the network. If the network is configured this way, the following native Windows commands will allow the attacker to connect to the IPC$ share of the server and then copy any files from any of the drives present on the system to the workstation In order for this to work, an administrative account with the same password (and username) needs to be on another machine on the network.

![](bbox=[0.1, 0.51, 0.89, 0.83])

# FIGURE 8.30 The IPC$ share.