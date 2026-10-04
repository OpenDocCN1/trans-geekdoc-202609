+   - There is no session establishment.
- The sender is not informed about resource availability.

For more information on UDP, search the internet for UDP RFCs.

# UDP Header (14.3.2)

UDP is a stateless protocol, which means neither the client nor the server tracks the state of a communication session. If reliability is required when using UDP as the transport protocol, it must be handled by the application.

One of the most important requirements for delivering live video and voice over a network is that the data must continue to flow quickly. Live video and voice applications can tolerate some data loss with minimal or no noticeable effect; they are perfectly suited to UDP.

The blocks of communication in UDP are called datagrams, or segments. The transport layer protocol sends datagrams in a best-effort manner.

The UDP header is far simpler than the TCP header because it has only four fields and requires 8 bytes (that is, 64 bits). Figure 14-11 shows the fields in a UDP header.

![](bbox=[0.22, 0.6, 0.85, 0.7])

Figure 14-11 Fields of the UDP Header

# UDP Header Fields (14.3.3)

Table 14-2 describes the fields in the UDP header.

Table 14-2 Details of the UDP Header Fields

| UDP Header Field | Description |
|---|---|
| Source Port | A 16-bit field used to identify the source application by port number |
| Destination Port | A 16-bit field used to identify the destination application by port number |
| Length | A 16-bit field that indicates the length of the UDP datagram header |
| Checksum | A 16-bit field used for error checking of the datagram header and data |