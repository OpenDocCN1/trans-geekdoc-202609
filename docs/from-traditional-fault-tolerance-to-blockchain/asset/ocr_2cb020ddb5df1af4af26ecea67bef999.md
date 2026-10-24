not reach their the destination processes due to the process failure, the recovering process retransmit the regular messages or the ack messages based on the following rule:

+   - If the entry in the log for a message contains no rsn value, then a REGULAR message is retransmitted because the intended receiving process might not have received this message.

+   - If the entry in the log for a message contains a valid rsn value, then an ACK message is sent so that the receiving process can send regular messages.

When a process receives a regular message, it always sends a corresponding ORDER message in response. There are three scenarios:

+   - The message is not a duplicate, in which case, the current rsn counter value is assigned to the message as its receiving order, and the corresponding ORDER message is sent. The process must then wait for the ACK message before it sends any regular message.

+   - The message is a duplicate, and the corresponding rsn value is found in its history list, in which case, an ORDER message is sent and the duplicate message itself is discarded. The process must then wait for the ACK message before it sends any regular message. Note that it is impossible for the process to have received the corresponding ACK message before because otherwise the recovering process must have logged the rsn value for the regular message.

+   - The message is a duplicate, and there is no corresponding entry in the history list. In this case, the process must have checkpointed its state after receiving the message and it is no longer needed for recovery. As a result, the process sends an ORDER message with a special constant indicating that the message is no longer needed and the sending processing can safely purge the entry from its message log.

The recovering process may receive two types of retransmitted regular messages: (1) those with a valid rsn value, and (2) those without. Because the rsn counter is part of the state checkpointed, the recovering process knows which message is to be executed next. During the recovery, the process executes the retransmitted regular messages with valid rsn values according to the ascending rsn