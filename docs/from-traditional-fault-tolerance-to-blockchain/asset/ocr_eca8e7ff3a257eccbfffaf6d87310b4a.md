![](bbox=[0.265, 0.105, 0.735, 0.355])

Figure 2.12 Transport level (a) and application level (b) reliable messaging.

the message in stable storage, the sending side would receive no notification and the message sent is no longer available.

To ensure application level reliable messaging, the sending process must store a copy of the message sent (in the application level) for possible retransmission until it receives an explicit acknowledgment message from the receiving process in the application level, as shown in Figure 2.12(b). Such an application level reliable messaging protocol does exist in some distributed computing paradigm, such as Web services [6]. Incidentally, the sender-based message logging protocol [13], to be introduced in a later subsection, incorporates a similar mechanism, albeit for a slightly different purpose.

We should note that the use of such an application level reliable messaging protocol is essential not only to ensure the atomicity of message receiving and logging, but also to facilitate the distributed system to recover from process failures (for example, the failure of the process at one end point of a transport level connection, which would cause the breakage of the connection, would have no negative impact on the process at the other end of the connection, and a process is always ready to reconnect if the current connection breaks).

Furthermore, the use of an application level reliable messaging protocol also enables the following optimization: a message received can be executed immediately and the logging of the