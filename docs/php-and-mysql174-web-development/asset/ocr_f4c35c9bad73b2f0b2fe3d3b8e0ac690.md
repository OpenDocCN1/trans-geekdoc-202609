# Protecting the Network

There are a few ways in which we can protect the network in which our web application resides. Although the exact details of these are beyond the scope of this book, they are reasonably easy to learn about and will protect more than just your web applications.

# Firewalls

Just as we need to filter all the input that comes into our web application written in PHP, we also need to filter all the traffic that comes to our network, whether it be into our corporate offices or a data center in which we are hosting our servers and applications.

You do this with a firewall, which can be software running on a known operating system such as FreeBSD, Linux, or Windows, or it can be a dedicated appliance you purchase from a networking equipment vendor. A firewall's job is to filter out unwanted traffic and block access to those parts of our network that we left alone.

The TCP/IP protocol, on which the Internet is based, operates on ports, with different ports being dedicated to different types of traffic (for example, HTTP is port 80). A large number of ports are used strictly for internal network traffic and have little use for interaction with the outside world. If we prohibit traffic from entering or leaving our network on these ports, we reduce the risk that our computers or servers (and therefore we our web applications) will be compromised.

# Use a DMZ

As mentioned earlier in this chapter, our servers and web applications are not only at risk of attack from external customers, but also from internal malicious users. Although these latter attackers will be fewer and farther between, they often have the potential to do more damage via intimate knowledge of how the company works.

One of the ways to mitigate this risk is to implement what is known as a demilitarized zone, or DMZ. In this, we isolate the servers running our web applications (and other servers, such as corporate email servers) from both the external Internet and internal corporate networks, as shown in Figure 15.3.

![](bbox=[0.118, 0.703, 0.728, 0.92])

Figure 15.3 Setting up a demilitarized zone (DMZ)