# IP Address Decoy

+   - IP address decoy technique refers to generating or manually specifying the IP addresses of decoys in order to evade an IDS or firewall
+   - It appears to the target that the decoys as well as the host(s) are scanning the network
+   - This technique makes it difficult for the IDS or firewall to determine which IP address was actually scanning the network and which IP addresses were decoys

# Decoy Scanning using Nmap

Nmap has two options for decoy scanning:

+   - `nmap -D RND:10 [target]`
+     (Generates a random number of decoys)
+   - `nmap -D decoy1,decoy2,decoy3,.. etc.`
+     (Manually specify the IP addresses of the decoys)

![](bbox=[0.56, 0.25, 0.84, 0.4])

# IP Address Decoy

The IP address decoy technique refers to generating or manually specifying IP addresses of the decoys to evade IDS/firewalls. It appears to the target that the decoys as well as the host(s) are scanning the network. This technique makes it difficult for the IDS/firewall to determine which IP address is actually scanning the network and which IP addresses are decoys.

The Nmap scanning tool comes with a built-in scan function called a decoy scan, which cloaks a scan with decoys. This technique generates multiple IP addresses to perform a scan, thus making it difficult for the target security mechanisms such as IDS, firewalls, etc., to identify the original source from the registered logs. The target IDS might report scanning from 5– 0 IP addresses; however, it cannot differentiate between the actual scanning IP address and the innocuous decoy IPs.

You can perform two types of decoy scans using Nmap:

**nmap -D RND:10 [target]**

Using this command, Nmap automatically generates a random number of decoys for the scan and randomly positions the real IP address between the decoy IPs.

Ex. Assume that 10.10.10.10 is the target IP address to be scanned. Thus, the Nmap decoy scan command will be:

```
# nmap -D RND: 10 10.10.10.10
```