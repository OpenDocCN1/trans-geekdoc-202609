
Many routers provide network address translation (NAT). NAT hides the internal IP addresses and port numbers used by internal hosts. Consequently, sniffers cannot learn these IP addresses and port numbers. NAT does no actual filtering, but networks with NAT protection tend to be very difficult to attack.

Application proxy firewalls provide protection at the application layer. They relay packets between an internal host and an external host, examining the application content as they do so. Application proxy firewalls provide extremely strong security, but a separate proxy program is needed for each application to be protected, and only a few types of application programs are suitable for application proxy protection. Worst of all, application proxy firewalls are very slow. It is most common to see an application proxy firewall placed between a single server and the clients that attempt to reach it or between internal clients and external webservers.

Firms have long used intrusion detection systems (IDSs), which provide deep packet inspection and examine streams of packets instead of just individual packets. The goal of an IDS is to look for suspicious packets and report them—but not stop them. New firewalls that use IDS methods to actually drop packets are called intrusion prevention systems (IPSs). IPSs use ASIC hardware to provide the speed needed to analyze traffic in real time (which is necessary to drop packets). In addition, IPSs only drop packets if they are highly certain that they are seeing an actual attack instead of just suspicious activities. If IPSs are less sure that a stream of packets is an attack, they may limit that traffic to a certain percent of total bandwidth in order to minimize damage.

Firewalls rarely do antivirus filtering directly. However, there usually are strong connections between firewalls and antivirus servers. When information requiring antivirus checking arrives at a firewall, the firewall will pass it to an antivirus server. If the antivirus server does not drop the information, it either delivers the information to the destination host or returns it to the firewall for delivery (and probably additional filtering). A few firewalls, called unified threat management (UTM) firewalls, do antivirus filtering as well as traditional filtering, but these are not common today.

Most main border firewalls also can detect and stop denial-of-service (DoS) attacks. DoS attacks are difficult to stop because DoS packets have the same form as legitimate packets. Border firewalls often address DoS attacks by limiting the rate of suspected DoS traffic and by protecting internal servers against half-open DoS attacks with false opens. However, if the volume of attack traffic is high, the firm’s link to the Internet will be saturated, and there will be nothing the firm can do. ISPs need to help prevent DoS attacks, and companies that own infected computers must stop these computers from sending out DoS attack packets.

Typically, a border router is multihomed, which means that it connects to multiple subnets. One could be the subnet leading to the Internet. A second could be the subnet leading to the firm’s internal network. A third subnet could be called the demilitarized zone (DMZ). The firm puts all servers that must be accessible from the Internet in the DMZ subnet. Hosts found in DMZs include public webservers, application proxy servers, and a DNS server that only knows the host names and IP addresses of hosts within the DMZ. Firms must harden hosts in the DMZ aggressively because these hosts will face constant attacks from attackers on the Internet.

Firewall technology is useless without strong management. Firms must define policies for firewalls very carefully, and these policies must drive both configuration and vulnerability testing to ensure that the firewall is operating properly. The firm must update firewall policies and ACLs constantly, and they must read the firewall log files very frequently. Many firms use central firewall management systems, which actively manage firewalls from a single computer. This reduces management costs.

The chapter closed with two difficult problems that will face firewall administrators in the future. The first is the death of the perimeter. Border firewalls are only useful if attackers must come in through the Internet border router. However, not all attackers have to do so today. Internal attackers and attackers coming in through access points are already inside the site, as are employees who bring in malware on

These are examples of the inherent tensions between privacy and security. The use of new apps, IoT devices, and systems often introduces privacy risks and security vulnerabilities that are difficult to identify and mitigate. The biggest risk of all is that the designated watchers (i.e., IT security staff) often lack the proper oversight to ensure that they are not abusing their power. So, the next time you think about buying a lottery ticket, keep your fingers crossed that the watchers are being watched!

## Discussion Questions

- 1. The article discusses the use of security audits to ensure that employees are not doing anything that they should not be doing on their employer's systems. In what other contexts are audits conducted?
- 2. Define what a rootkit is and conduct a search online for examples of how rootkits have been used.
- 3. One strategy for preventing IT employees from violating their extensive system access is “separation of duties.” Can you think of any other examples of how a function or task is split into multiple pieces or assigned to multiple individuals to prevent abuse of that function?
- 4. Take a moment to think about all of the different types of devices that you use on a daily basis. How could these devices be compromised to invade your privacy? Is this risk of privacy invasion enough to make you stop using these devices?

## Security Technology

### Tor—Onion Routing

In July 2019, a hacking group named “0v1ru$” revealed that it had breached a system run by the Russian federal security service named the FSB (Federalnaya sluzhba bezopasnosti) and stolen 7.5 TB of secret information.⁶ One of the most interesting things found in this massive theft was the operation of the system named Nautilus-S. This system was built to deanonymize Tor traffic and, ultimately, identify users. But why would one of the world’s largest intelligence agencies spend so much time and effort on Tor networks? It did it because Tor provides users with the one thing that is nearly impossible on the Internet—anonymity.

### Tor for Anonymity

An effective way for whistleblowers and journalists to send and receive data over the Internet is to use onion routing. A popular implementation of onion routing is the Tor network (TorProject.org). The Tor network provides almost completely anonymous access to the Internet. It uses a series of encrypted relay nodes to forward packets from senders to receivers.

Tor is also useful if you live in or are visiting a country that prohibits access to specific websites or services such as chat or instant messaging.⁷ It can be used by political dissidents to communicate sensitive material.

Corporations can benefit from using a Tor network by hiding all information that may be gained from analyzing the traffic patterns into and out of a company. Competitors could monitor traffic for search terms, visits to the U.S. Patent and Trademark Office, communication between certain manufacturers, and so on. All of these could yield clues to a confidential corporate strategy or new product development. Using a Tor network could prevent this type of corporate espionage.

### How Tor Works

### Step 1

After installing the Tor client, a user would request a listing of all the Tor nodes from a directory server.⁸ Tor nodes will be used to relay data between senders and receivers. The user’s computer can also act as a relay node for someone else’s data transfer.

### Step 2

The Tor client would then randomly select a path from the local host to the destination computer. In this case the destination computer is a webserver. The Tor client builds a series of encrypted links between each Tor node. Each Tor node can only see the next hop in the path. It cannot see the originating user, the destination webserver, or any Tor nodes beyond a single hop. All traffic is fully encrypted when being passed from node to node.

### Step 3

The Tor node that ends up being the last hop before reaching the destination webserver is known as the exit node. The connection between the exit node and the destination webserver
