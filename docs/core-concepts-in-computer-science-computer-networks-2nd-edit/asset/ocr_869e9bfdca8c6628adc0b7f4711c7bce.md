protocols and some of the examples of character-oriented protocols are XMODEM YMODEM, ZMODEM, KERMIT, BLAST, IBM's 83B asynchronous data-link protocol, IBM's binary synchronous communications.

Character oriented protocols are classified according to the following

+   - Simplex
- Half Duplex
- Full duplex

# Simplex

This is the simplest form of protocol used in the transfer of data. With this protocol, the transmission takes place in one direction at a time. Transmission and Reception on the same line is NOT possible. When simplex is used, the system is set up to first send data, while the other is set up to receive data and vice versa. This does not mean that there is no communication in the reverse direction. Idle RQ system will stop and wait for an acknowledgment after each block, but no data can be sent in the reverse direction. This is what makes it simplex.

Kermit is an example of this system of data transfer. With this system, each user initiates the Kermit program and then enters the connect. This results in a link between the sending device and the receiving device. At the receiving device enters the receive command and the user in the sending system uses the command followed by the file(s) name(s). The Kermit in the sending system transmits the entire file(s). This system is used when users wish to transfer files from one DTE to another (e.g. one PC to another PC) using a point-to-point link.

Kermit is an asynchronous data link protocol. This means that it does use start and stop bits and packages the characters into frames/blocks/packets for convenience.

If manual modes are used then one must be set in the originate mode and the other in the answer mode, but both must be set to operate at the same baud rate. As each file is transferred, a message is sent to both screens, indicating that a segment is sent and received. After all segments are transferred, both the sending and receiving DTEs exit Kermit and return to the operating system, giving an exit command. Frames are identified by sending a character which specifies the length of the frame which is about to be sent. An additional character is also sent after each frame called the carriage return character to indicate that the frame is finished.

> The half-duplex mode is used in cases where there is no need for communication in both directions at the same time. The entire capacity of the channel can be utilized for each direction.

# Half Duplex

Most character oriented protocols operate in half-duplex, stop and wait mode. These provide data transfer facilities in both directions but not at the same time. A well-known protocol of this type is IBM's binary synchronous control or Bisync (or