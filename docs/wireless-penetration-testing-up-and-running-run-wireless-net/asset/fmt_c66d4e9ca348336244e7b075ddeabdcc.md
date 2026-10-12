
Essentially, it is the practice of leveraging compromised computers to gain access to networks that we would not otherwise have access to. If a computer with access to the network is compromised, network isolation will be worthless. This approach allows an attacker to get access to secret networks by routing to compromised systems. The pivot is used to transfer all requests to the newly found network. It is like a kind of tunnel. Refer to [Figure 9.2](#c09.xhtml#fig9_2):

![](images/Figure-9.2.jpg)

**Figure 9.2:** Pivoting

The device with two NICs has access to both the `192.168.1.0/24` and `192.168.10.0/24` networks, as shown in the topology. Unless a routing rule is defined, there is no access between these two networks under normal circumstances. The authorized user, who is using a computer with two NIC cards, must access some services in the DMZ, according to this topology.

# Compromise first pivot and port forwarding

The meterpreter shell obtained in the system named as RD is likewise connected to the DMZ network, according to our attack scenario. With the information-gathering procedure, it is later discovered that the target has two NICs.

**The environment's router does not route between networks.**

[Figure 9.3](#c09.xhtml#fig9_3) illustrates the first pivot:

![](images/Figure-9.3.jpg)

**Figure 9.3:** First pivot

[Figure 9.4](#c09.xhtml#fig9_4) illustrates the `Meterpreter_1`:

![](images/Figure-9.4.jpg)

**Figure 9.4:** Meterpreter\_1

[Figure 9.5](#c09.xhtml#fig9_5) illustrates the `Meterpreter_2`:

![](images/Figure-9.5.jpg)

**Figure 9.5:** Meterpreter\_2

According to our scenario, an attacker who gains access to the RD system will wish to use the second NIC (7.7.7.0/24) to access the network. To do this activity, the attacker needs first to define the routing rule on RD.

With Metasploit, this is simple. To build the routing rule using the current meterpreter session, do the following command. Refer to [Figure 9.6](#c09.xhtml#fig9_6):

![](images/Figure-9.6.jpg)

**Figure 9.6:** Meterpreter\_3

The 7.7.7.0/24 network can be accessed in the Metasploit framework if the meterpreter session with ID value 2 operates, according to the established rule, as shown in [Figure 9.7](#c09.xhtml#fig9_7).

The IP addresses of the JC system are then discovered using post modules like ARP scanners. Another computer discovered in the hidden network –7.7.7.20– is JC.

Refer to [Figure 9.7](#c09.xhtml#fig9_7):

![](images/Figure-9.7.jpg)

**Figure 9.7:** Meterpreter\_4

The IP addresses of live systems in the 7.7.7.0/24 network have been determined, including the JC-named system. Refer to [Figure 9.8](#c09.xhtml#fig9_8):

![](images/Figure-9.8.jpg)

**Figure 9.8:** Hidden network

Naturally, the following question will arise: will nmap-style scanning tools be used instead of post modules like `arp_scanner` for such scanning work?

# Nmap via pivoting

To accomplish this, Metasploit's routing configuration must be active and capable of being sent via socks4 proxy. Another Metasploit module can be used to fulfill this requirement.

The use of the socks4 proxy as a Metasploit module can be seen in [Figure 9.9](#c09.xhtml#fig9_9):

![](images/Figure-9.9.jpg)

**Figure 9.9:** socks4 proxy

Using the ProxyChains utility built for GNU/Linux operating systems, any TCP connection can be routed to destinations via TOR or SOCKS4, SOCKS5, or HTTP/HTTPS. Many proxy servers can be used in this tunneling approach. In addition to offering anonymity, applications like pivoting can be used to shift traffic to new networks found. Refer to [Figure 9.10](#c09.xhtml#fig9_10):

![](images/Figure-9.10.jpg)

**Figure 9.10:** ProxyChains

The information for the newly built socks4 proxy server is added to the last line of the `/etc/proxychains.conf` file, which is opened in a text editor. Refer to [Figure 9.11](#c09.xhtml#fig9_11):

![](images/Figure-9.11.jpg)

**Figure 9.11:** Proxychains.conf file

It is an easy way to use ProxyChains to execute a nmap scan. The network packages will be sent to the destination via the defined proxy. Refer to [Figure 9.12](#c09.xhtml#fig9_12):

![](images/Figure-9.12.jpg)

**Figure 9.12:** Nmap output\_1

Also, refer to [Figure 9.13](#c09.xhtml#fig9_13):

![](images/Figure-9.13.jpg)

**Figure 9.13:** Nmap output\_2

According to the scan results, SSH and HTTP services will function on the target machine. We will look at a distinct sort of traffic routing called port forwarding before moving on to exploitation.

# Port forwarding

Port forwarding is one of the first steps in pivoting. Certain services on the secret network's specified systems may not be directly accessible (Web servers, and so on). Due to the lack of double-sided routing, this is the case. We know how to travel to the target system and submit a request, but because the target is unaware of our location, our requests will be refused. Refer to [Figure 9.14](#c09.xhtml#fig9_14):

![](images/Figure-9.14.jpg)

**Figure 9.14:** Port forwarding

As a result, we route a port on our own system to the destination using the present meterpreter session. The routing will work if this process is alive.

One thing to keep in mind at this point: the run `autoroute` command allows us to work freely within the Metasploit framework thanks to the routing we provide. However, we will need tools like port forwarding and ProxyChains to access the target using Kali tools.

Port forwarding can be done with `portfwd` module, which is one of the post modules of Metasploit. Refer to [Figure 9.15](#c09.xhtml#fig9_15):

![](images/Figure-9.15.jpg)

**Figure 9.15:** Port forward using Metasploit

The connection request is forwarded to port 80 of the computer with the IP address 7.7.7.20 when we use our internet browser to submit a link request to our local `2323` port.

ProxyChains and Nmap have previously identified a Web service running on 7.7.7.20's 80th TCP port. To use this service, forward port `2323` on the local system to the 7.7.7.20 port `80` that we want to use. Refer to [Figure 9.16](#c09.xhtml#fig9_16):

![](images/Figure-9.16.jpg)

**Figure 9.16:** Port forward command

Active rules can be viewed with the `portfwd list` command. Refer to [Figure 9.17](#c09.xhtml#fig9_17):

![](images/Figure-9.17.jpg)

**Figure 9.17:** Portfwd list command

Easy file sharing Web Server will be detected when the program executing on port `80` of the target system with IP address 7.7.7.20 is verified. Refer to [Figure 9.18](#c09.xhtml#fig9_18):

![](images/Figure-9.18.jpg)

**Figure 9.18:** Easy file sharing Web server

# SSH brute-force over pivoting

As you are aware, an SSH service was identified on 7.7.7.20. A brute-force attack on this service is simple to carry out. The `SSH_enumusers` auxiliary module allows user detection, as shown in [Figure 9.19](#c09.xhtml#fig9_19):

![](images/Figure-9.19.jpg)

**Figure 9.19:** SSH\_enumusers Module output\_1

Also, refer to [Figure 9.20](#c09.xhtml#fig9_20):

![](images/Figure-9.20.jpg)

**Figure 9.20:** SSH\_enumusers Module output\_2

In addition to the auxiliary modules on the Metasploit Framework, Kali tools like Hydra can be used for the attack. If Hydra is deployed in ProxyChains, all traffic will be redirected to the target system via the compromised system. Refer to [Figure 9.21](#c09.xhtml#fig9_21):

![](images/Figure-9.21.jpg)

**Figure 9.21:** Hydra tool in Kali Linux

SSH connection via a proxy server to the target system with admin username and password 123456 obtained during Hydra brute-force attack. Refer to [Figure 9.22](#c09.xhtml#fig9_22):

![](images/Figure-9.22.jpg)

**Figure 9.22:** SSH connection

# Gaining access to the second pivot
