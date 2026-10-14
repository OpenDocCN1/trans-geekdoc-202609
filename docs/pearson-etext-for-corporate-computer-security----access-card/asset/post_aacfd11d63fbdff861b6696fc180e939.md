
**Figure 6-5** States in a Connection

![](img/073342643701cc54eb7875c41ab92ef2_305_0.png)

Instead of talking about time periods, phases, or stages, computer scientists use the term **state** to describe a particular temporal period during a connection. In human conversations there is an opening state, an ongoing communication state, and an ending state.

The concept of states is central to SPI filtering. Figure 6-5 illustrates a simple connection in which there are only two states.

> A state is a distinct phase in a connection between two applications.

- First, there is an *opening* state, when the two applications agree to open a connection.
- Afterward, the two applications enter the *ongoing communication* state. For most connections, traffic is dominated by exchanges during the ongoing communication state. The two applications communicate back and forth using the same port numbers and other conditions.

## STATEFUL PACKET INSPECTION WITH TWO STATES

The concept of states is important because it is appropriate to check for different things during different states. Stateful inspection does precisely that: It changes its specific examination method depending on the state.

> Stateful packet inspection uses specific examination methods depending on the state of the connection.

Figure 6-5 shows that when a packet arrives, the firewall first determines whether the packet is part of a connection-opening attempt. For example, if the packet contains a TCP segment, it is only attempting to open a connection if the SYN bit is set.

The figure shows that different rules apply to packets that are part of connection-opening attempts and those that are not.

The vast majority of packets are *not* part of connection-opening attempts. Note in the figure that stateful packet inspection is simple for packets that do not attempt to open a connection. Consequently, nearly all packets are handled quickly, simply, and therefore inexpensively.

**Figure 6-6** Connection and Socket

![](img/073342643701cc54eb7875c41ab92ef2_306_0.png)

For the few packets that do attempt to open connections, the processing of stateful packet inspection firewalls is more complex. Fortunately, because few packets attempt to open connections, connection-opening packets do not place a heavy burden on SPI firewalls.

## REPRESENTING CONNECTIONS

SPI focuses on connections between programs on different hosts. In networking, a connection is represented by its socket, which designates a specific program (designated by a port number) on a specific computer (IP address). A socket is written as an IP address, a colon, and a port number—for example, 10.3.47.16:4400. As Figure 6-6 shows, a connection is a link between programs on different machines. It consists of two sockets—an internal socket and an external socket.

### Test Your Understanding

- 5. a. What is a state?
- b. Are most packets part of the connection-opening state or the ongoing communication state?
- c. Why is the answer to Question 5b important for stateful packet inspection’s efficiency?
- d. What is a connection?
- e. How is a connection between two programs on different computers represented?

## Packets That Do Not Attempt to Open Connections

In stateful packet inspection, as Figure 6-5 shows, when a packet arrives that does not attempt to open a connection, an SPI firewall checks if it is part of a previously approved connection.

- If it is part of an existing connection in the connection table, the packet is passed, usually without further filtering.
- If it is not part of an existing connection in the connection table, it is dropped and logged.

### TCP CONNECTIONS

For example, suppose that a packet arriving from the outside does not attempt to open a connection (Step 1 in Figure 6-7). The packet has IP source address 123.80.5.34, TCP source port number 80, IP destination address 60.55.33.12,

**Figure 6-7** Stateful Packet Inspection for a Packet That Does Not Attempt to Open a Connection I

![](img/073342643701cc54eb7875c41ab92ef2_307_0.png)

| Type | Internal IP | Internal Port | External IP | External Port | Status |
|------|-------------|---------------|-------------|---------------|--------|
| TCP | 60.55.33.12 | 4400 | 123.80.5.34 | 80 | OK |
| UDP | 60.55.33.5 | 3660 | 1.8.33.4 | 161 | OK |

and TCP destination port number 4400. This matches the connection in the first row. Therefore, the packet is part of an approved connection. The firewall passes the packet.

### UDP AND ICMP CONNECTIONS

Although ICMP and UDP (User Datagram Protocol) are connectionless, SPI firewalls can handle ICMP and UDP. For ICMP, for instance, there are echo and echo-reply interactions. If an ICMP echo message arrives, this is viewed as a connection-opening attempt. An echo reply message would not. Some UDP interactions can also be handled in a similar way. Figure 6-7 shows a row that represents a UDP connection. It will pass subsequent packets matching this connection.

### ATTACK ATTEMPTS

Suppose that an attacker’s host sends a packet with the IP source address 10.5.2.4 (a spoofed IP address) and the TCP destination port 80. This is not a connection-opening attempt. (The SYN flag is not set in the TCP segment.) In Figure 6-8, we see that this packet does not match any row in the connection table. The firewall drops and logs the packet.

**Figure 6-8** Stateful Packet Inspection for a Packet That Does Not Attempt to Open a Connection II

![](img/073342643701cc54eb7875c41ab92ef2_307_1.png)

| Type | Internal IP | Internal Port | External IP | External Port | Status |
|------|-------------|---------------|-------------|---------------|--------|
| TCP | 60.55.33.12 | 4400 | 123.80.5.34 | 80 | OK |
| UDP | 60.55.33.12 | 3660 | 1.8.33.4 | 161 | OK |

**PERSPECTIVE** We have seen that for packets that do not attempt to open a connection and therefore appear to be part of the ongoing communication state, SPI processing is very simple. If the connection is in the connection table, pass the packet; if not, drop the packet.

Although basic SPI processing for ongoing communication is this simple, it is also possible to build additional filtering into the processing. Additional filtering increases the work and therefore the cost of the SPI firewall. However, it is justified for some applications.

### Test Your Understanding

- 6. **a.** Give the simple stateful packet inspection firewall rule for packets that do not attempt to open connections.
- **b.** Is SPI filtering for packets that are part of ongoing communications usually simple and inexpensive? Explain.
- **c.** UDP is connectionless. How is it possible for an SPI firewall to handle UDP connections?

## Packets That Do Attempt to Open a Connection

So far, we have looked at how SPI firewalls handle packets that *do not* attempt to open a connection. Figure 6-5 shows that stateful inspection firewalls also have a simple default behavior for deciding whether to pass packets that *do* try to open connections. (In general, the **default** is what you get if you do not specify something else explicitly.)

- By default, SPI firewalls permit all attempts to open a connection from an *internal* host to an external host. This makes sense because it generally is acceptable for internal clients to open connections to external servers. When an internal host tries to open a connection to an external host, the firewall by default adds an appropriate row to the state table.
- By default, the SPI firewall stops all *external* hosts from opening connections to internal hosts. This makes sense because few external clients should be able to reach internal servers. This default stops attackers from connecting to internal servers (or clients).

### Test Your Understanding

- 7. Give the two simple default SPI firewall rules for packets that attempt to open connections.

### Access Control Lists (ACLs) for Connection-Opening Attempts

Although the default behavior of stateful packet inspection firewalls works most of the time for connection-opening attempts, organizations need to have exceptions. For exceptions, the default behavior will need to be superseded.

- For example, firms may need to permit some externally initiated connections. For example, external clients will need access to the firm’s internal e-commerce server.
- To give another example, firms may need to prevent some internally initiated connections to the outside world. For instance, the firewall may need to prevent internal clients from connecting to known phishing sites. It may also need to prevent malware on internal compromised hosts from attacking external hosts or from sending sensitive information out of the site.
