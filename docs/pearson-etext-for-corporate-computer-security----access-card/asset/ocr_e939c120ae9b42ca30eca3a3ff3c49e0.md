# Figure 6-6 Connection and Socket

![](bbox=[0.3, 0.095, 0.89, 0.305])

For the few packets that do attempt to open connections, the processing of stateful packet inspection firewalls is more complex. Fortunately, because few packets attempt to open connections, connection-opening packets do not place a heavy burden on SPI firewalls.

# REPRESENTING CONNECTIONS

SPI focuses on connections between programs on different hosts. In networking, a connection is represented by its socket, which designates a specific program (designated by a port number) on a specific computer (IP address). A socket is written as an IP address, a colon, and a port number—for example, 10.3.47.16:4400. As Figure 6-6 shows, a connection is a link between programs on different machines. It consists of two sockets—an internal socket and an external socket.

# Test Your Understanding

+   5. a. What is a state?
+      b. Are most packets part of the connection-opening state or the ongoing communication state?
+      c. Why is the answer to Question 5b important for stateful packet inspection’s efficiency?
+      d. What is a connection?
+      e. How is a connection between two programs on different computers represented?

# Packets That Do Not Attempt to Open Connections

In stateful packet inspection, as Figure 6-5 shows, when a packet arrives that does not attempt to open a connection, an SPI firewall checks if it is part of a previously approved connection.

+   - If it is part of an existing connection in the connection table, the packet is passed, usually without further filtering.
+   - If it is not part of an existing connection in the connection table, it is dropped and logged.

# TCP CONNECTIONS

For example, suppose that a packet arriving from the outside does not attempt to open a connection (Step 1 in Figure 6-7). The packet has IP source address 123.80.5.34, TCP source port number 80, IP destination address 60.55.33.12,