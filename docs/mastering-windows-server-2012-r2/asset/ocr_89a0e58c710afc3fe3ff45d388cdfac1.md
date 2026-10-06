# Chapter 20

# # Advanced IP: Routing with Windows

Why route from Windows? The short answer is that you can, and it will open your eyes to a world previously unseen.

Over a decade routers were expensive and it was common for network-savvy companies to use cast-off PCs as cheap routers. For example, by putting a couple of network cards in the PC and installing a copy of Linux, a network engineer could save the company a lot of money on buying a huge chunk of metal from a major network vendor. Even now you can find these distributions lurking on the Internet and still in use in some ISPs.

Routing is a vital part of maintaining a network infrastructure (think about how VLANs are in your network and how the traffic is routed among them!). It is important to understand how routing works inside the hosts on it. Normally, this is beyond the control of a server administrator, knowing a little about routing will also help you troubleshoot connection issues on your hosts and network.

In this chapter, we will take you through the life of an IP packet as it is routed across your network, and we will explore the differences between class-based and classless routing (although these are relatively old concepts, looking at the differences still provides some insight). We will explain how address translator (NAT) devices allow you to route TCP traffic, and in a brief history, we will see how the arrival of Winsock shaped the Internet.

We will walk you through the processes of installing the Remote Access role and how to configure a router with NAT (we will revisit the Remote Access role in the next chapter). We will cover how to configure a Windows Server 2012 R2 computer to route IP, and discuss tunneling. Finally, you will learn how to use the knowledge gained from this chapter, and a few common tools, to troubleshoot network communication difficulties.

In this chapter, you will learn to:

+   * Document the life of an IP packet routed through your network
* Explain the class-based and classless views of IP routing
* Use NAT devices to route TCP traffic

# # The Life of an IP Packet

The designers of the original Internet Protocol achieved something that goes beyond merely clever: they made something that is just as simple as it is to achieve its purpose. As a result, you will not be going to tell you how to route UDP or TCP,