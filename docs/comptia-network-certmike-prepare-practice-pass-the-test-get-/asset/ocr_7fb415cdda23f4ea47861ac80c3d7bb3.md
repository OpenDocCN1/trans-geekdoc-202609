# Load Balancers

Load balancers are devices that distribute enterprise use when they have multiple servers running the same application or service. Balancing the load means that the incoming traffic for those servers is distributed among them so that no one is serving over- or overwhelmed. For example, highly trafficked websites typically have multiple servers functioning as a cluster. Load balancing ensures that each of the servers in the cluster handles approximately the same amount of incoming traffic.

# Proxy Servers

A proxy server is a networking device that functions as an intermediary between client computers and the Internet. The browser on the clients is configured with the address of the proxy server so that any attempts it may make to access the Internet are redirected to the proxy. The proxy server then accesses the Internet server, receives its responses, and relays them back to the clients. This way, only the proxy server accesses the Internet; clients remain hidden on a private network.

# Firewall

A firewall is a hardware or software device that functions as a barrier between a private network and the Internet outside. Its primary objective is to protect the resources on the internal network from unauthorized access—whether accidental or deliberate—by external systems. A firewall is essentially a filter that examines the incoming traffic and allows or denies access to the private network based on content. The most basic packet filtering technique that most firewall use is to examine the IP addresses and port numbers in packet headers to determine where the traffic is going. Administrators can configure firewall with rules that include or exclude types of traffic based on these criteria. More advanced firewall techniques examine packets—including their data—in much greater detail.

# Intrusion Prevention and Detection

An intrusion detection system (IDS) is a hardware or software device that examines network traffic, looking for anomalous patterns that might indicate the presence of an intruder or an actual attack. Some IDS products base their detection routines on signatures provided by the product manufacturer, usually on a subscription basis, much like an antivirus product. Others use a more behavioral approach by watching for deviations from baseline traffic patterns and other anomalies.

Unlike a firewall, which is located at the border of the private and public networks, an IDS is located inside the private network, enabling it to monitor for both internal and external threats. When an IDS detects a potential intrusion, it gathers information about it in the form of logs and reports; captures pertinent traffic samples, if necessary; and notifies the administrators responsible.

IDS products detect, document, and notify, but they can do nothing to mitigate any trouble that they find. An intrusion prevention system (IPS) can intervene, however, using