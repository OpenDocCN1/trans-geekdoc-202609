processing services, so networks had to be established via privately leased lines. A user would lease a line from the telephone company and then set up his computer hardware to network through that dedicated line. With such a reliable connection, the synchronous data link control protocol of SNA was able to manage each line and provide a data communication network between the users' computer systems. A proprietary protocol, SDLC was added to the modern and computer systems developed by IBM that made up an SNA environment. Later, IBM shared the synchronous data link control with standards organizations that then developed the high-level data link control (HDLC) protocol that other hardware vendors began using.

The synchronous data link control protocol was the first of kind to provide transmissions based on bytes that are responsible for identifying each frame of data sent. In SDLC, the transmission of data is broken into frames that are streamed over the connection. Each frame contains not only the data being sent, but also a series of bytes that carry information on the address the frame is being sent to, how to arrange all of the frames in proper order, and the ability for the system to double check the frame for any errors that may have occurred during its journey.

The first and last bytes of the SDLC frame are called flags, which are essentially the frame's wrapper, indicating its beginning and end. The next byte or two make up the address. The control bytes, which can have multiple purposes depending on the type of frame being transmitted, follow the address and handle sequencing of frames, termination of transmissions, status checking, polling, and so forth. The data payload follows the control bytes, and after the data, but before the closing flag, are a couple bytes used for redundant sequence checking.

An SNA environment using synchronous data link control is fairly straightforward, where each node on the network is identified as either the primary or secondary. The primary nodes are most likely a mainframe computer, while secondary are terminals communicating with the mainframe. Still, a network running under SDLC is capable of several different types of topologies.

In a point-to-point setup, there are only computers communicating with one another: a single primary mainframe and a single secondary terminal. With multipoint, the mainframe is responsible for any number of secondary terminals. Another topology is the loop configuration, where the mainframe acts as something of a primary point in a circle where it passes frames through the loop via only the first or last terminal in the circle. There is then something the hub go-ahead method that allocates an outbound channel to the mainframe and an inbound channel to the terminals.

The main features of synchronous data link protocols are as follows:

+   - Character-oriented protocol
- Based on one byte (8-bit)
- Use ASCII for character character
- Not efficient \00AE used
- Bit-oriented protocol