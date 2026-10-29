# Checking the Filtering Systems of Target Networks

The ACK flag probe scanning technique also helps in checking the filtering systems of target networks. The attacker sends an ACK probe packet to check the filtering mechanism (firewalls) of packets employed by the target network.

Sending an ACK probe packet with a random sequence number and getting no response from the target means that the port is filtered (stateful firewall is present); an RST response from the target means that the port is not filtered (no firewall is present).

![](bbox=[0.25, 0.245, 0.735, 0.33])

Figure 3.55: Stateful Firewall is present

![](bbox=[0.255, 0.367, 0.735, 0.45])

Figure 3.56: No Firewall

# ACK Flag Probe Scanning using Nmap

In Zenmap, the -sA option is used to perform an ACK flag probe scan.

![](bbox=[0.255, 0.538, 0.75, 0.882])

Figure 3.57: ACK Flag Probe scanning using Zenmap