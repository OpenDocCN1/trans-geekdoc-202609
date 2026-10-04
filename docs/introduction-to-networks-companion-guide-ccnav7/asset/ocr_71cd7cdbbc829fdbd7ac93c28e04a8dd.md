![](bbox=[0.25, 0.1, 0.92, 0.5])

Figure 14-31 UDP: Connectionless and Unreliable

# UDP Server Processes and Requests (14.7.3)

Like TCP-based applications, UDP-based server applications are assigned well-known or registered port numbers, as shown in Figure 14-32. When these applications or processes are running on a server, they accept the data matched with the assigned port number. When UDP receives a datagram destined for one of these ports, it forwards the application data to the appropriate application, based on its port number.

**Note**

The Remote Authentication Dial-in User Service (RADIUS) server shown in Figure 14-32 provides authentication, authorization, and accounting services to manage user access. The operation of RADIUS is beyond the scope of this book.

# UDP Client Processes (14.7.4)

As with TCP, with UDP, client/server communication is initiated by a client application that requests data from a server process. The UDP client process dynamically selects a port number from the range of port numbers and uses it as the source port for the conversation. The destination port is usually the well-known or registered port number assigned to the server process.