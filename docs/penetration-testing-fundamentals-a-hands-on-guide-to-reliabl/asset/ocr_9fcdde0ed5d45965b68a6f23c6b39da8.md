If you click the Statistics drop-down menu, there are a number of interesting options, shown in Figure 8-7.

![](bbox=[0.115, 0.175, 0.42, 0.62])

FIGURE 8-7 Wireshark Statistics.

As you can see, if there is DNS or DHCP traffic that has been captured, you can select that option to gather statistics related to that protocol. Selecting conversations will let you see statistics for IPv4, IPv6, TCP, and UDP conversations. HTTP can provide you with a great deal of information on HTTP traffic. Obviously there are many other choices. This chapter is not meant to be a Wireshark tutorial, but rather hopes to provide you a basic working knowledge of Wireshark.

Wireshark is a very versatile tool. It is worth taking the time to learn completely all the features of this tool. Fortunately, there are a number of resources on the Wireshark page at https://www.wireshark.org/#learnWS to help you learn.

The reason you use a tool like Wireshark is to get a very granular view of what is being transmitted over the network. You may actually see data, including credentials, sent in cleartext. Or you will be able to see TLS being established and used. You may also see error codes sent back from a web server. There is a wealth of data that can be derived from mapping network traffic.