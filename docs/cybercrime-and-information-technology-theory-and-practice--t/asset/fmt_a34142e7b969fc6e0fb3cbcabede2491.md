
# 计算机网络简介

*But what happens behind the scenes?*

*   Domain Name System (DNS) Search
*   Network communication using Transmission Control Protocol (TCP)
    *   Browser sends a Hypertext Transfer Protocol Secure (HTTPS) request
    *   Server sends back HTTPS response
    *   Server acknowledges and sends back the requested Hypertext Markup Language (HTML) file
*   Browser renders HTML
*   Browser sends additional requests (GET request) for additional components
*   Matthew receives requested information

First, the browser checks for a Domain Name System (DNS) record to find the corresponding IP address of `www.linkedin.com`. Every Web page on the Internet has a unique IP address assigned to it. While the Uniform Resource Locator (URL) is a reference to a specific website, the DNS is the “phonebook” of the Internet and contains a list of every URL and its IP addresses. To find `www.linkedin.com`, the browser checks four caches, the Browser cache, Computer Operating System (OS) cache, Router cache, and Internet service provider (ISP) DNS cache. A cache can be hardware or software. It stores data so that future requests for that data can be found more quickly.

If the IP address is not found, the DNS server starts a new DNS query to find the IP address of `www.linkedin.com`. As soon as the browser locates the right IP address, it tells the server that has found the IP address for `www.linkedin.com` and wants to transfer the information.

How does it do that? There are several types of network protocols, but the TCP is the most common protocol used to establish and maintain network communication. The browser sends a Hypertext Transfer Protocol (HTTP) request. HTTP is a protocol that runs on top of TCP. TCP transfers data packets between Matthew’s computer, the client, and the server. This connection is known as a three-way handshake: 1-SYN or a request from the server is sent to synchronize devices; 2-SYN/ACK or the client (Matthew) hears the request; and 3-ACK or the request is acknowledged. This establishes the connection between the network and the devices. After the TCP/IP connection is established, the data can be delivered to Matthew’s computer.

The browser receives a HTML file that needs to be understood and displayed. First, it renders the HTML, and then it checks the HTML tags and sends out a GET method request for additional components on the Web page, like an image or a graph. Now Matthew can see the result of “Jobs in Computer Security” appearing on his browser.

All these events take place while Matthew blinks. In this chapter you will learn to understand each of these steps and appreciate the network devices and processes that make them possible.

The term “computer network” refers to two or more interconnected computing devices or machines that can communicate with each other. The fundamental goal of `computer networking` is simple—to securely share information and resources. It is the execution that is not simple at all.

## 5.1 Introduction to Computer Networking

Over the centuries, some human inventions have provided transformative changes in our lives. Inventions such as the wheel, compass, concrete, steel, gunpowder, and nails have extended the boundaries of civilization and human knowledge and have moved innovation forward.

The end of the 18th century brought the age of the steam engine.

The 20th century brought us automation, information gathering and processing, the Internet, and mobile phones.

The Internet is an enormous global network of networks that can connect every computing device to its vast resources and to every other computer on the planet. In the 1960s, the Advanced Research Projects Agency (ARPA), part of the Department of Defense, funded a proposed network project called the Advanced Research Projects Agency Network (ARPANET), through the Association for Computing Machinery (ACM).

In 1969, the experimental ARPANET was constructed. Only universities with ties to the Department of Defense were considered for this project. The new network connected the Universities of California Los Angeles (UCLA) and California at Santa Barbara (UCSB), the Stanford Research Institute (SRI), and the University of Utah (UTAH) through the Internet Message Processor (IMP).

![FIGURE 5.1 A map of the ARPANET in December 1970. Courtesy of DARPA.](images/fig5.1.jpg)

**FIGURE 5.1** A map of the ARPANET in December 1970. Courtesy of DARPA.

![FIGURE 5.2 The first routers, known as Interface Message Processors or IMPs. Courtesy of DARPA.](images/fig5.2.jpg)

**FIGURE 5.2** The first routers, known as Interface Message Processors or IMPs. Courtesy of DARPA.

![FIGURE 5.3 The first rough conceptual design of ARPANET in 1969 with four nodes. Adopted from DARPA.](images/fig5.3.jpg)

**FIGURE 5.3** The first rough conceptual design of ARPANET in 1969 with four nodes. Adopted from DARPA.

However, it is worth noting that Bolt Beranek and Newman (BBN) Inc. was awarded the contract to build the ARPANET. Consequently, BBN created Telenet Communications Corp. to commercialize the packet switching technology. Telenet received a Federal Communications Commission (FCC) license in 1974. In 1975, Telenet launched the first commercial packet switching with network service that cost $0.60 per kilo packet with no distance restrictions and $0.90–2.40 per hour for computer terminals dialing into the local Telenet node. The company expanded its network globally and played a vital role in generating the standard for commercial packet networks.

Most institutions with computer science programs were part of CSNET. In 1983, TCP/IP became the official protocol for ARPANET. The term “protocol” will be explained shortly.

In 1983, the ARPANET split into two separate networks, the MILNET for military installations and the ARPANET for civilian use (mainly dedicated to research). In 1986, the National Science Foundation (NSF) sponsored the development of the National Science Foundation Network (NSFNET), which promoted advanced research in networking.

In 1989, while working for the European Organization for Nuclear Research (CERN), Tim Berners-Lee invented the World Wide Web (WWW). The idea was the creation of a service that merged HTML, URL, and HTTP so that all computers could understand each other in an easy-to-use global information system.

In 1990, the ARPANET was replaced by NSFNET. In 1995, the network became largely commercial and grew exponentially.

### 5.1.1 Protocols

A protocol is a digital language and set of specifications and procedures followed throughout the network so that computers in different locations can share information and resources, making the network viable. Networks can connect many different types of computers and share resources that reside on widely different types of servers. Without a viable protocol, no network can function.
