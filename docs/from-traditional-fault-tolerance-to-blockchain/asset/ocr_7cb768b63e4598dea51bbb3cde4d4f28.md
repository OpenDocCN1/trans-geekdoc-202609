of 100KB, the oneway transfer latency over the network is estimated to be around 2600μs (half of the end-to-end latency without logging). This implies that the network manages to offer slightly under 40MB per second transfer rate.

# 2.3.2 Sender-Based Message Logging

For distributed applications that do not wish to log messages synchronously in stable storage, the sender-based message logging protocol [13] can be used to achieve limited degree of robustness against process failures. The basic idea of the sender-based message logging protocol is to log the message at the sending side in volatile memory. Should the receiving process fail, it could obtain the messages logged at the sending processes for recovery. To avoid restarting from the initial state after a failure, a process can periodically checkpoint its local state and write the message log in stable storage (as part of the checkpoint) asynchronously.

Unlike the receiver-based message logging protocol introduced in section 2.3.1, where the relative ordering of the messages received can be implicitly logged, such ordering information (i.e., the determinant for the messages) must be explicitly supplied by the receiver of a message to the sender. Furthermore, after sending the ordering information, the receiver needs to wait for an explicit acknowledgment for the ordering message. Prior to receiving of the acknowledgment, the receiver must not send any message to other processes (however, it can execute the message received immediately without delay, similar to the optimization for pessimistic logging discussed in section 2.3.1.2. This restriction is put in place to prevent the formation of orphan messages and orphan processes [7], which would force the orphan processes to roll back their state during the recovery of another process.

An orphan message is one that was sent by a process prior to a failure, but cannot be guaranteed to be regenerated upon the recovery of the process [7]. An orphan process is a process that receives an orphan message. If a process sends out a message and subsequently fails before the determinants of the messages it has received are properly logged, the message sent becomes an orphan message.

# 2.3.2.1 Data Structures

In the sender-based message logging protocol, each process must maintain the following data structures: