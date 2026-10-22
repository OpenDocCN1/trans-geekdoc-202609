![](bbox=[0.28, 0.1, 0.8, 0.28])

# Exhibit 5.16 Multitasking Server Host and Port Numbers

# 5.6.8 Port Numbers.

We have now looked at most fields in the TCP header. The first two fields warrant special mention.

# 5.6.8.1 Port Numbers on Servers.

Port number fields mean different things for clients and servers. For a server, it represents a specific application running on that server, as Exhibit 5.16 shows. Servers are multitasking computers, which means that they can run multiple applications at the same time. Each application is specified by a different port number.

For instance, on a server, a Web server application program may run on TCP Port 80. Incoming TCP segments that have 80 as their destination port number are passed to the Web server application. Actually, TCP Port 80 is the well-known port for Web server programs, meaning that it is the usual port number for the application. Although Web servers can be given other TCP port numbers, this makes it impossible for users to establish connections unless they know or can guess the nonstandard TCP port number.

The TCP port range from 0 to 1023 is reserved for the well-known port numbers of major applications, such as HTTP and email. For instance, Simple Mail Transfer Protocol (SMTP) mail server programs usually are run on TCP Port 25, while File Transfer Protocol (FTP) requires two well-known port numbers—TCP Port 21 for supervisory control and TCP Port 20 for the actual transfer of files.

# 5.6.8.2 Port Numbers on Clients.

Client hosts use TCP port numbers differently. Whenever a client connects to an application program on a server, it generates a random ephemeral port number that it uses only for that connection. On Windows machines, the ephemeral TCP port numbers range from 1024 to 4999.

The Microsoft port number range for ephemeral port numbers may differ from the official IETF range, with values of 5000–65534. The use of nonstandard ephemeral port numbers by Windows and some other operating systems causes problems for firewall filtering.

# 5.6.8.3 Sockets.

Exhibit 5.17 shows that the goal of internetworking is to deliver application messages from one application on one machine to another application on another machine. On each machine, there is a TCP port number that specifies the application (or connection) and an IP address to specify a computer. A socket is a combination of an IP address and a TCP port number. It is written as the IP address,