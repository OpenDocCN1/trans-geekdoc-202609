network time is wasted. The primary disadvantages are complexity and hardware capacity (i.e. buffer space).

# Error Control

Error control includes both error detection and error correction. Error detection at data-link layer can be accomplished with VRC, LRC or CRC and error correction is generally accomplished with automatic repeat (ARQ). With ARQ, any time a transmission error is detected, the destination station sends a negative acknowledgment (NAK) back to the source station requesting retransmission of the last frame or frames. ARQ also allows for retransmission of mission or lost frames.

Two types of ARQ exist:

+   - stop-and-wait
- Sliding window.

Stop-and-wait frame control implements stop-and-wait ARQ and sliding window flow control usually implements ARQ in one of two variants: go-back-n frames or selective reject (SRE.1).

With go-back-n frames, the destination station tells the source station to go back n frames and retransmit all of them, even though all of them do not contain errors. With selective reject, the destination station tells the source station to retransmit only the frame or frames received in error.

# Character and Bit-Oriented Protocols

Control information is transmitted by the protocols in separate control frames or as overhead and included in the frame. Data-link protocols are generally classified as either character or bit oriented.

# Character-Oriented Protocols

Character-oriented protocols interpret a frame of data as a group of successive bits combined into predefined frames of length, usually eight bits each. Each group of bits represents a unique character. Control information is included in the frame form of standard characters from an existing character set, such as ASCII. With COP, unique link control characters as start of text (STX) and end of text (ETX) perform the same action no matter where they occur in the transmission. These are also known as byte-oriented

Transmission is the process of sending and propagating analogue or digital information signal over a physical point-to-point or multipoint transmission medium, either wired, optical fiber or wireless.