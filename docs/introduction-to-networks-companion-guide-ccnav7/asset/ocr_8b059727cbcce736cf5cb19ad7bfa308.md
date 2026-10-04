stream into segments, providing reliability, controlling data flow, and reordering segments. TCP frees the application from having to manage any of these tasks. Applications, like those shown in Figure 14-10, can simply send the data stream to the transport layer and use the services of TCP.

![](bbox=[0.22, 0.2, 0.73, 0.45])

Figure 14-10 Applications That Use TCP

# Check Your Understanding—TCP Overview (14.2.5)

Refer to the online course to complete this activity.

Interactive Graphic

# UDP Overview (14.3)

The reliability and flow control features provided by TCP come with additional overhead related to connection establishment and tracking whether or not segments were received. When such overhead creates unnecessary delay, it is time to use UDP, which is a simpler transport layer protocol than TCP. UDP is used by many applications and protocols, including delay-sensitive VoIP applications and simple reply and request protocols (that is, DNS and DHCP).

# UDP Features (14.3.1)

This section covers UDP, including what it does and when it is a good idea to use it instead of TCP. UDP is a best-effort transport protocol. It is a lightweight transport protocol that offers the same data segmentation and reassembly as TCP, but without TCP’s reliability and flow control. UDP is such a simple protocol that it is usually described in terms of what it does not do compared to TCP.

UDP’s features include the following:

+   - Data is reconstructed in the order in which it is received.
- Any segments that are lost are not re-sent.