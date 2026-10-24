the ordering message to a process and another regular message to a different process, and node on which the process runs subsequently crashes, the ordering message might not be delivered to its intended target successfully while the regular message might.

Furthermore, in the original sender-based message logging protocol [13] , the regular message and the ordering message must be retransmitted after a timeout before the expected acknowledgment message is received. With the use of reliable channels, such proactive retransmission becomes unnecessary because the only scenario in which a retransmission is necessary is when a process fails, in which case, the retransmission will be triggered by the recovery mechanism (more in section 2.3.2.3).

The use of a mature reliable communication protocol such as TCP in distributed applications is more desirable because the application developers can focus on the application logic and application-level messaging reliability without worrying about issues such as achieving high throughput and doing congestion control.

# EXAMPLE 2.6

In the example shown in Figure 2.18, the distributed system consists of three processes. Both the seq counter and rsn counter are initialized to be 0, and the message log is empty at each process. Process P0 first sends a regular message, <REGULAR,0,?,m0>, to P1. Upon sending the message, P0 increments its seq counter to 1 and log the message in its volatile buffer. At this point, the rsn value for the message is unknown, hence it is denoted as a question mark.

On receiving the regular message <REGULAR,0,?,m0>, P1 assigns the current rsn counter value, which is 0, to this message indicating its receiving order, increments its rsn counter to 1, and sends P0 an ORDER message <ORDER,[m0],0>. When P0 receives this ORDER message, it updates the entry in its message log to reflect the ordering number for message m0, and sends an sc ack message, <ACK,[m0]>, to P1.

Once receiving the ACK message, P1 is permitted to send a regular message, <REGULAR,0,?,m1>, to P2. The handling of the message and the corresponding ORDER and ACK messages are similar to the previous ones.